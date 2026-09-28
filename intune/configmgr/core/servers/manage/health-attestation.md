---
layout: Conceptual
title: Health attestation - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/health-attestation
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
description: Learn about the device health attestation functionality in Configuration Manager.
ms.date: 2021-04-14T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 424907c6-2079-754b-4c70-1e041bf5e50e
document_version_independent_id: 7d544033-2504-d5a0-de3c-ce6896cde9d1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/health-attestation.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/health-attestation
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/health-attestation.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 648e6ef1-0339-3c8c-8144-f638120d0e19
---

# Health attestation - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can view the status of [Windows 10 Device Health Attestation](/en-us/windows/security/threat-protection/protect-high-value-assets-by-controlling-the-health-of-windows-10-based-devices) in the Configuration Manager console. Device health attestation lets you make sure that client computers have the following trustworthy BIOS, TPM, and boot software configurations enabled:

- *Early-launch antimalware (ELAM)* protects your computer when it starts up and before third-party drivers initialize. For more information, see the[Overview of Early Launch AntiMalware](/en-us/windows-hardware/drivers/install/early-launch-antimalware).
- *Windows BitLocker Drive Encryption* encrypts all data stored on the OS and data volumes, including removable disks. For more information, see [Plan for BitLocker management](../../../protect/plan-design/bitlocker-management).
- *Secure Boot* is a security standard to help make sure that a device boots using only software that's trusted by the PC manufacturer. For more information, see [Secure Boot](/en-us/windows-hardware/design/device-experiences/oem-secure-boot).
- *Code Integrity* improves OS security by validating the integrity of a driver or system file each time it's loaded into memory. For more information, see [Enable virtualization-based protection of code integrity](/en-us/windows/security/threat-protection/device-guard/enable-virtualization-based-protection-of-code-integrity).

This functionality is available for on-premises resources managed by Configuration Manager and [mobile devices managed with Microsoft Intune](../../../../device-security/compliance/ref-windows-settings#device-health). You can specify whether reporting is done via the cloud or on-premises infrastructure. On-premises device health attestation monitoring enables you to monitor client PCs without internet access.

## Enable health attestation

### Requirements

- Client devices running a supported version of Windows 10 or Windows Server 2016 or later, with [Device health attestation enabled](/en-us/windows-server/security/device-health-attestation).
- TPM 1.2 or TPM 2 enabled devices.
- When using cloud management, communication between the Configuration Manager client agent and the management point with `has.spserv.microsoft.com` (port 443) health attestation service. When on-premises, the client needs to communicate with the device health attestation-enabled management point.

### How to enable health attestation service communication on Configuration Manager client computers

Use this procedure to enable device health attestation monitoring for devices that connect to the internet.

1. In the Configuration Manager console, choose **Administration** &gt; **Overview** &gt; **Client Settings**. Select the tab for **Computer Agent** settings.
2. In the **Default Settings** dialog box, select **Computer Agent** and then scroll down to **Enable communication with Health Attestation Service**.
3. Set **Enable communication with Health Attestation Service** to **Yes**, and then select **OK**.
4. Target the collections of devices that should report device health.

### How to enable on-premises health attestation service communication on Configuration Manager client computers

Use this procedure to enable device health attestation monitoring for on-premises devices that don't connect to the internet.

You can configure the on-premises device health attestation service URL on the management point to support client devices without internet access.

1. In the Configuration Manager console, navigate **Administration** &gt; **Overview** &gt; **Site Configuration** &gt; **Sites**.
2. Right-click the primary or secondary site with the management point that support on-premises device health attestation clients, and select **Configure site components** &gt; **Management Point**. The **Management Point Component Properties** page opens.
3. On the **Advanced Options** tab, select **Add** and specify a valid on-premises device health attestation service URL. You can add multiple URLs. If multiple on-premises URLs are specified, clients receive the full set and randomly choose which to use.
4. In the Configuration Manager console, choose **Administration** &gt; **Overview** &gt; **Client Settings**. Select the tab for **Computer Agent** settings.
5. Scroll down to **Enable communication with Health Attestation Service**, and set to **Yes**.
6. Select the **Use on-premises Health Attestation Service** option, and set to **Yes**.
7. Target the collections of devices that should report device health with the client agent settings to enable device health attestation reporting.

You can also **Edit** or **Remove** device health attestation service URLs.

## Monitor device health attestation

To view the device health attestation status, in the Configuration Manager console go to the **Monitoring** workspace, expand the **Security** node, and then select **Health Attestation**.

Configuration Manager device health attestation displays the following information:

- **Health Attestation Status** - Shows the share of devices in compliant, noncompliant, error, and unknown states
- **Devices Reporting Health Attestation** - Shows the percentage of devices reporting Health Attestation status
- **Noncompliant Devices by Client Type** - Shows share of mobile devices and computers that are noncompliant
- **Top Missing Health Attestation Settings** - Shows the number of devices missing the health attestation setting, listed per setting