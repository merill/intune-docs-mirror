---
layout: Conceptual
title: Configure definition updates - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-definition-updates
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
description: Learn how to select and configure methods with Endpoint Protection in Configuration Manager to keep antimalware definitions up to date on client computers.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 7af33c58-a6c7-2955-b379-827d43d21dec
document_version_independent_id: 346e5de5-745e-d070-d4a0-3c6aa04d0572
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/endpoint-definition-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/endpoint-definition-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/endpoint-definition-updates.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 04045c1f-371c-55f4-7e14-6663e0cee865
---

# Configure definition updates - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

With Endpoint Protection in Configuration Manager, you can use any of several available methods to keep antimalware definitions up to date on client computers in your hierarchy. The information in this topic can help you to select and configure these methods.

To update antimalware definitions, you can use one or more of the following methods:

- [Updates distributed from Configuration Manager](endpoint-definitions-configmgr) - This method uses Configuration Manager software updates to deliver definition and engine updates to computers in your hierarchy.
- [Updates distributed from Windows Server Update Services (WSUS)](endpoint-definitions-wsus) - This method uses your WSUS infrastructure to deliver definition and engine updates to computers.
- [Updates distributed from Microsoft Update](endpoint-definitions-microsoft-updates) - This method allows computers to connect directly to Microsoft Update in order to download definition and engine updates. This method can be useful for computers that are not often connected to the business network.
- [Updates distributed from Microsoft Malware Protection Center](endpoint-definitions-protection-center) - This method will download definition updates from the Microsoft Malware Protection Center.
- [Updates from UNC file shares](endpoint-definitions-network) - With this method, you can save the latest definition and engine updates to a share on the network. Clients can then access the network to install the updates.

    You can configure multiple definition update sources and control the order in which they are assessed and applied. This is done in the **Configure Definition Update Sources** dialog box when you create an antimalware policy.

Important

For Windows 10 or later PCs, you must configure Endpoint Protection to update malware definitions for Windows Defender.

## How to Configure Definition Update Sources

Use the following procedure to configure the definition update sources to use for each antimalware policy.

1. In the Configuration Manager console, click **Assets and Compliance**.
2. In the **Assets and Compliance** workspace, expand **Endpoint Protection**, and then click **Antimalware Policies**.
3. Open the properties page of the **Default Antimalware Policy** or create a new antimalware policy. For more information about how to create antimalware policies, see [How to create and deploy antimalware policies for Endpoint Protection](endpoint-antimalware-policies).
4. In the **Security Intelligence updates** section of the antimalware properties dialog box, click **Set Source**.

    - The **Definition updates** section was renamed to **Security Intelligence updates** starting in Configuration Manager version 1902.
5. In the **Configure Definition Update Sources** dialog box, select the sources to use for definition updates. You can click **Up** or **Down** to modify the order in which these sources are used.
6. Click **OK** to close the **Configure Definition Update Sources** dialog box.

## Configure Endpoint Protection definitions

- [Updates distributed from Configuration Manager](endpoint-definitions-configmgr) - This method uses Configuration Manager software updates to deliver definition and engine updates to computers in your hierarchy.
- [Updates distributed from Windows Server Update Services (WSUS)](endpoint-definitions-wsus) - This method uses your WSUS infrastructure to deliver definition and engine updates to computers.
- [Updates distributed from Microsoft Update](endpoint-definitions-microsoft-updates) - This method allows computers to connect directly to Microsoft Update in order to download definition and engine updates. This method can be useful for computers that are not often connected to the business network.
- Updates distributed from Microsoft Malware Protection Center - This method will download definition updates from the Microsoft Malware Protection Center.
- [Updates from UNC file shares](endpoint-definitions-network) - With this method, you can save the latest definition and engine updates to a share on the network. Clients can then access the network to install the updates.