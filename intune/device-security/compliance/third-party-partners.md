---
layout: Conceptual
title: Third-party device compliance partners support in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/compliance/third-party-partners
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- compliance
- sub-device-compliance
ms.subservice: protect
description: Use a third-party device compliance partner as a source of compliance data for devices you manage with Intune.
ms.date: 2026-06-24T00:00:00.0000000Z
ms.topic: overview
ms.reviewer: ilwu-microsoft
locale: en-us
document_id: 7e191009-82be-326f-8436-89399f5f96a0
document_version_independent_id: 7e191009-82be-326f-8436-89399f5f96a0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/compliance/third-party-partners.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/compliance/third-party-partners
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/compliance/third-party-partners.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 5fa89b20-ef63-5ec2-cdd9-76d1b1afd374
---

# Third-party device compliance partners support in Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune supports integration with several third-party device compliance partners. When you use a third-party device compliance partner, the partner adds the compliance state data it collects to Microsoft Entra ID. You can use device compliance data from the partner alongside the compliance results you collect with Intune. Together, these signals power [Conditional Access policies](overview#integrate-with-conditional-access) that help to protect your organization and data.

By default, Intune is the mobile device management (MDM) authority for your devices. When you add a compliance partner to Microsoft Entra ID and Intune, that partner becomes the MDM authority for devices assigned to it through a Microsoft Entra user group.

To enable user data from device compliance partners, complete the following tasks:

1. **Configure Intune to work with the device compliance partner**, and then configure groups of users whose devices are managed by that compliance partner.
2. **Configure your compliance partner to send data to Intune**.
3. **Enroll your devices to your device compliance partner**.

With these tasks complete, the device compliance partner sends device state details to Intune. Intune adds this information to Microsoft Entra ID. For example, devices in a noncompliant state have a *not compliant* status added to their device record in Microsoft Entra ID.

## Supported device compliance partners

The following compliance partners are supported as generally available:

- 42Gears SureMDM
- 7P
- Addigy
- BlackBerry UEM
- Citrix Workspace device compliance
- CLOMO MDM
- Fleet
- IBM MaaS360
- Jamf Pro
- Iru
- Ivanti Neurons for MDM
- Ivanti EPMM
- mobiconnect
- Mosyle Fuse
- Mosyle Onek12
- Omnissa Workspace ONE UEM
- Scalefusion
- SOTI MobiControl

Note

Microsoft Intune is currently revamping our device compliance partner process, which will be available for prospective partners in 2026 Q3.

## Self-service onboarding for compliance partners

Microsoft Intune supports self-service onboarding for compliance partners. Partners can onboard and publish their own compliance connectors for use with Intune. After a partner makes a connector available, you can configure it from within the Intune admin center when adding a compliance partner, as described later in this article.

Note

The availability of specific partners depends on whether the partner has completed the onboarding process and published their connector for use with Intune.

## Requirements

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - Microsoft Intune subscription with access to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
> - Intune licenses assigned to device users.
> 

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> - Android
> - iOS/iPadOS
> - macOS
> 
> 
> Not all partners support all platforms. Check your partner's documentation for supported platforms.

You also need:

- A subscription to the device compliance partner.
- Check your compliance partner's documentation for prerequisites.

For self-service onboarded compliance partners, obtain the Microsoft Entra application ID from the compliance partner before you begin configuration.

## Configure Intune to work with a device compliance partner

Enable support for a device compliance partner to use compliance state data from that partner with your Conditional Access policies.

### Add a compliance partner to Intune

1. Sign in to [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Tenant Administration** &gt; **Connectors and Tokens** &gt; **Partner Compliance management** &gt; **Add Compliance Partner**.

    [![Add a device compliance partner](media/third-party-partners/add-compliance-partner.png)](media/third-party-partners/add-compliance-partner.png#lightbox)
3. On **Basics**, expand the **Compliance partner** dropdown and select the partner you want to add. To configure a self-service onboarded partner that does not appear in the dropdown, select **Custom MDM Compliance Partner**. Then enter the **Custom MDM Compliance Partner Entra Application ID** provided by your compliance partner. If the application ID isn't associated with a valid onboarded compliance partner, the configuration can't be completed.

    Next, select the dropdown for **Platform**, and select the platform.

    You can use only one partner per platform, even if you add multiple compliance partners to Microsoft Entra ID.
4. On **Assignments**, select the user groups that contain devices managed by this partner. With this assignment, you change the MDM authority for applicable devices to use this partner. Users who have devices managed by the partner must also be assigned a license for Intune.
5. On **Review + create**, review your selections, and then select **Create** to complete this configuration.

Your configuration now appears on the **Partner compliance management** page.

### Modify the configuration for a compliance partner

1. Sign in to [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Tenant Administration** &gt; **Connectors and Tokens** &gt; **Partner Compliance management**, and then select the partner configuration you want to modify. Configurations appear by platform type.
3. On the partner configuration **Overview** page, select **Properties** to edit the assignments.
4. On the **Properties** page, select **Edit** to change the assigned groups.
5. Select **Review + save** and then **Save** to save your edits.
6. *This step only applies when you use Omnissa Workspace ONE*:

    From within the Workspace ONE UEM console, you must manually synchronize the changes you saved in the Microsoft Intune admin center. Until you manually sync changes, Workspace ONE UEM isn't aware of configuration changes, and users in newly assigned groups don't successfully report compliance.

    To manually sync from Azure Services:

    1. Sign in to your Omnissa Workspace ONE UEM console.
    2. Go to **Settings** &gt; **System** &gt; **Enterprise Integration** &gt; **Directory Services**.
    3. For *Sync Azure Services*, select **SYNC**.

        Azure services synchronize all changes made after the initial configuration or the last manual synchronization to UEM.

## Configure your compliance partner to work with Intune

To enable a device compliance partner to work with Intune, you must complete configurations specific to that partner. For information on this task, see the documentation made available by your chosen compliance partner:

## Enroll your devices to your device compliance partner

See your device compliance partner's documentation to enroll devices. After devices enroll and submit compliance data to the partner, that compliance data is forwarded to Intune and added to Microsoft Entra ID.

## Monitor devices managed by third-party device compliance partners

After you configure a third-party compliance partner and enroll devices, the partner forwards compliance data to Intune. You can then view device details in the Microsoft Entra admin center.

Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) and go to **Devices** &gt; [**All devices**](https://entra.microsoft.com/#view/Microsoft_AAD_Devices/DevicesMenuBlade/%7E/Devices).

## Best practices for migrating devices from third-party MDM to Intune MDM

When you migrate devices from third-party MDM providers to a full Intune stack, follow these cleanup steps:

1. Initiate a retirement action from the third-party MDM service before enrolling the device with Intune MDM. This retirement action notifies Intune to perform the necessary cleanup tasks in its third-party integration services.

    Note

    Removing the third-party MDM profile locally on a device doesn't sufficiently trigger the Intune cleanup tasks.
2. Confirm that devices retired from the third-party MDM appear in Microsoft Entra ID with **None** listed in the **MDM** column. At this point, your devices can now be enrolled with Intune MDM.
3. After all devices migrate to Intune through steps 1 and 2, disable the Intune connection in your third-party MDM provider's admin console. If that isn't an option, you can also disable the connection console in the Microsoft Intune admin center.

    1. Go to **Tenant administration** &gt; **Connectors and tokens** &gt; **Device compliance partner**.
    2. Select the device compliance partner you want to disable.
    3. Toggle the connection to **Off**.

Note

If devices don't complete the cleanup tasks and still appear enrolled in Intune, Intune applies its own compliance policies and ignores third‑party policies.