---
layout: Conceptual
title: Configure clients for CMG - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/configure-clients
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Understand how to configure clients to use the cloud management gateway (CMG).
ms.date: 2022-02-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 233e999e-4316-08ba-d14f-e04814a70fe8
document_version_independent_id: b8c760e4-fb95-420f-f5c0-520c8aea02b5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/cmg/configure-clients.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/cmg/configure-clients
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/cmg/configure-clients.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 065319ac-1ac6-60fa-b42d-2476e55c878e
---

# Configure clients for CMG - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Once the cloud management gateway (CMG) and the supporting site system roles are operational, you may need to make configuration changes on Configuration Manager clients.

Clients that can communicate with the management point automatically get the location of the CMG service on the next location request. The polling cycle for location requests is every 24 hours. If you don't want to wait for the normally scheduled location request, you can force the request. To force the request, restart the SMS Agent Host service (ccmexec.exe) on the computer.

For devices that aren't connected to the internal network, there are several options to configure them with a CMG location. For more information, see Install off-premises clients using a CMG.

Note

By default all clients receive CMG policy. Control this behavior with the client setting, **Enable clients to use a cloud management gateway**. For more information, see [About client settings](../../deploy/about-client-settings#enable-clients-to-use-a-cloud-management-gateway).

## Client location

The Configuration Manager client automatically determines whether it's on the intranet or the internet. If the client can contact a domain controller or an on-premises management point, it sets its connection type to **Currently intranet**. Otherwise, it switches to **Currently Internet**, and uses the location of the CMG service to communicate with the site.

Note

You can force the client to always use the CMG regardless of whether it's on the intranet or internet. This configuration is useful for testing purposes, or for clients that you want to force to always use the CMG. Set the following registry key on the client:

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\Security, ClientAlwaysOnInternet = 1`

You can also specify this setting during client installation using the [CCMALWAYSINF](../../deploy/about-client-installation-properties#ccmalwaysinf) property.

This setting will always apply, even if the client roams into a location where boundary group configurations would otherwise leverage local resources.

To verify that clients have the policy specifying the CMG, open a Windows PowerShell command prompt as an administrator on the client computer, and run the following command:

```powershell
Get-WmiObject -Namespace Root\Ccm\LocationServices -Class SMS_ActiveMPCandidate | Where-Object {$_.Type -eq "Internet"}
```

This command displays any internet-based management points the client knows about. While the CMG isn't technically an internet-based management point, clients view it as one.

Note

To troubleshoot CMG client traffic, use **CMGService.log** and **SMS\_Cloud\_ProxyConnector.log**. For more information, see [Log files](../../../plan-design/hierarchy/log-files#cloud-management-gateway).

## Install off-premises clients using a CMG

There are two methods to install the Configuration Manager client on devices that aren't currently connected to your intranet. Both require a local administrator account on the target system.

- The first method is to use a bulk registration token to install the client on a device. For more information on this method, see [Create a bulk registration token](../../deploy/deploy-clients-cmg-token#bulk-registration-token).
- For the second method, when you run **ccmsetup.exe**, use the `/mp` parameter to specify the CMG's URL. For more information, see [About client installation parameters and properties](../../deploy/about-client-installation-properties#mp). This method requires one of the following conditions:

    - The Configuration Manager site is properly configured to use PKI certificates for client authentication. Additionally, the client systems each have a valid, unique, and trusted client authentication certificate previously issued to them.
    - The systems are Microsoft Entra domain-joined or hybrid Microsoft Entra domain-joined.

## Configure off-premises clients for CMG

You can connect devices to a recently configured CMG where the following conditions are true:

- They already have the Configuration Manager client installed.
- They aren't connected and can't be connected to your intranet.
- They meet one of the following conditions:

    - A valid, unique, and trusted client authentication certificate previously issued to it.
    - Microsoft Entra domain-joined
    - Hybrid Microsoft Entra domain-joined
- You don't want to or can't completely reinstall the existing client.
- You have a method to change a machine registry value and restart the **SMS Agent Host** service using a local administrator account.

To force the connection on these devices, create the **REG\_SZ** registry entry `CMGFQDNs` in the key `HKLM\Software\Microsoft\CCM`. Set its value to the URL of the CMG, for example, `https://GraniteFalls.contoso.com`. Then restart the **SMS Agent Host** Windows service on the device.

If the Configuration Manager client doesn't have a current CMG or internet-facing management point set in the registry, it automatically checks the `CMGFQDNs` registry value. This check occurs every 25 hours, when the **SMS Agent Host** service starts, or when it detects a network change. When the client connects to the site and learns of a CMG, it automatically updates this value.