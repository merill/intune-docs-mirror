---
layout: Conceptual
title: Restrict USB Devices Using Settings Catalog in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/restrict-usb
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Use the settings catalog in Microsoft Intune to restrict USB devices, including thumb drives, flash drives, USB cameras, and more. Use other settings to allow specific USB devices on Windows 10/11 devices.
ms.date: 2026-04-30T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mayurjadhav, kufang
locale: en-us
document_id: 7e291b73-da5d-5232-6a22-239a99c3be31
document_version_independent_id: 7e291b73-da5d-5232-6a22-239a99c3be31
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/settings-catalog/restrict-usb.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/settings-catalog/restrict-usb
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/settings-catalog/restrict-usb.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: b9fd8481-e6a9-6a51-ab0d-9d25572d7e79
---

# Restrict USB Devices Using Settings Catalog in Microsoft Intune - Microsoft Intune | Microsoft Learn

Many organizations want to block specific types of USB devices, such as USB flash drives or cameras. You might also want to allow specific USB devices, such as a keyboard or mouse.

Use the settings catalog in Microsoft Intune to configure these settings in a policy, and then deploy this policy to your Windows devices. For more information on the settings catalog, see [Use the settings catalog to configure device settings in Microsoft Intune](./).

This article shows you:

- How to create a settings catalog policy with USB settings in the Intune admin center
- How to use a log file to troubleshoot devices that shouldn't be blocked

This article applies to:

- Windows

## Prerequisites

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To configure the settings catalog policy, at a minimum, sign in to the Intune admin center with the **Policy and Profile Manager** role. For more information about the built-in roles in Intune, see [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview).

## Create the profile

This policy provides an example of how to block (or allow) features that affect USB devices. Use this policy as a starting point, and then add or remove settings as needed for your organization.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Settings catalog**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. For example, enter **Restrict USB devices**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, select **Add settings**. In the settings picker, go to **Administrative templates** &gt; **System** &gt; **Device installation** &gt; **Device Installation Restrictions**. Select the following settings:

    - **Allow installation of devices that match any of these Device IDs**
    - **Allow installation of devices using drivers that match these device setup classes**
    - **Prevent installation of devices not described by other policy settings**

    [![Screenshot of the Device Installation Restrictions settings in the settings catalog in Microsoft Intune.](media/restrict-usb/settings-catalog-select-device-installation-restrictions.png)](media/restrict-usb/settings-catalog-select-device-installation-restrictions.png#lightbox)
8. Close the settings picker. Configure the settings you selected:

    - **Allow installation of devices that match any of these Device IDs**: Select **Enabled**. Add the device or hardware IDs for devices you want to allow.

        To get the device or hardware ID, use Device Manager, find the device, and look at the properties. For the specific steps, see [find the hardware ID on a Windows device](/en-us/windows-hardware/drivers/install/hardware-ids).

        There's also some helpful device ID information at [Deploy and manage device control in Microsoft Defender for Endpoint with Microsoft Intune](/en-us/defender-endpoint/device-control-deploy-manage-intune).
    - **Allow installation of devices using drivers that match these device setup classes**: Select **Enabled**. Add the [System-defined device setup classes available to vendors](/en-us/windows-hardware/drivers/install/system-defined-device-setup-classes-available-to-vendors) you want to allow.

        In the following image, the **Keyboard**, **Mouse**, and **Multimedia** classes are allowed.
    - **Prevent installation of devices not described by other policy settings**: Select **Enabled**.

    When you enable and configure these settings, your policy looks similar to the following policy settings:

    [![Screenshot of the restrict USB settings configured in the settings catalog in Microsoft Intune.](media/restrict-usb/settings-catalog-restrict-usb-settings-enabled.png)](media/restrict-usb/settings-catalog-restrict-usb-settings-enabled.png#lightbox)
9. Select **Next**.
10. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, see [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
11. In **Assignments**, select the device groups that receive the profile. Select **Next**.
12. In **Review + create**, review your settings. When you select **Create**, your changes are saved and the profile is assigned.

## Verify USB device restrictions on Windows devices

After you deploy the device configuration profile to your targeted devices, confirm that it works correctly.

If a USB device is blocked from installing, you see a message similar to the following message:

`The installation of this device is forbidden by system policy. Contact your system administrator.`

In the following example, the iPad is blocked because its device ID isn't in the allowed device ID list:

[![Screenshot that shows a device blocked by an Intune policy.](media/restrict-usb/device-status.png)](media/restrict-usb/device-status.png#lightbox)

## A device is blocked but should be allowed

Some USB devices have multiple GUIDs, and it's common to miss some GUIDs in your policy settings. As a result, a USB device that you allow in your settings might be blocked on the device.

In the following example, in the **Allow installation of devices using drivers that match these device setup classes** setting, the Multimedia class GUID is entered, and the camera is blocked:

[![Screenshot that shows the Windows can't find your camera message on a Windows device.](media/restrict-usb/camera-blocked.png)](media/restrict-usb/camera-blocked.png#lightbox)

[![Screenshot that shows the camera is blocked by group policy message on a Windows device.](media/restrict-usb/cam-blocked.png)](media/restrict-usb/cam-blocked.png#lightbox)

**Resolution**:

To find the GUID of your device, use the following steps:

1. On the device, open the `%windir%\inf\setupapi.dev.log` file.
2. In the file:

    1. Search for **Restricted installation of devices not described by policy**.
    2. In this section, find the `Class GUID of device changed to: {GUID}` text. Add this `{GUID}` to your policy.

        In the following example, you see the `Class GUID of device changed to: {36fc9e60-c465-11cf-8056-444553540000}` text:

        ```log
        >>>  [Device Install (Hardware initiated) - USB\VID_046D&PID_C534\5&bd89ed7&0&2]
        >>>  Section start 2020/01/20 17:26:03.547
        dvi: {Build Driver List} 17:26:03.597
        …
        dvi: {Build Driver List - exit(0x00000000)} 17:26:03.645
        dvi: {DIF_SELECTBESTCOMPATDRV} 17:26:03.647
        dvi:      Default installer: Enter 17:26:03.647
        dvi:           {Select Best Driver}
        dvi:                Class GUID of device changed to: {36fc9e60-c465-11cf-8056-444553540000}.
        dvi:                Selected Driver:
        dvi:                     Description - USB Composite Device
        dvi:                     InfFile     - c:\windows\system32\driverstore\filerepository\usb.inf_amd64_9646056539e4be37\usb.inf
        dvi:                     Section     - Composite.Dev
        dvi:           {Select Best Driver - exit(0x00000000)}
        dvi:      Default installer: Exit
        dvi: {DIF_SELECTBESTCOMPATDRV - exit(0x00000000)} 17:26:03.664
        dvi: {Core Device Install} 17:26:03.666
        dvi:      {Install Device - USB\VID_046D&PID_C534\5&BD89ED7&0&2} 17:26:03.667
        dvi:           Device Status: 0x01806400, Problem: 0x1 (0xc0000361)
        dvi:           Parent device: USB\ROOT_HUB30\4&278ca476&0&0
        !!! pol:           The device is explicitly restricted by the following policy settings:
        !!! pol:           [-] Restricted installation of devices not described by policy
        !!! pol:      {Device installation policy check [USB\VID_046D&PID_C534\5&BD89ED7&0&2] exit(0xe0000248)}
        !!! dvi:      Installation of device is blocked by policy!
        !   dvi:      Queueing up error report for device install failure.
        dvi: {Install Device - exit(0xe0000248)} 17:26:03.692
        dvi: {Core Device Install - exit(0xe0000248)} 17:26:03.694
        <<<  Section end 2020/01/20 17:26:03.697
        <<<  [Exit status: FAILURE(0xe0000248)]
        ```
3. In the device configuration profile, go to the **Allow installation of devices using drivers that match these device setup classes** setting, and add the class GUID from the log file.
4. If the issue continues, repeat these steps to add the other class GUIDs until the device is successfully installed.

    In our example, the following class GUIDs are added to the device profile:

    - USB Bus devices (hubs and host controllers): `{36fc9e60-c465-11cf-8056-444553540000}`
    - Human Interface Devices (HID): `{745a17a0-74d3-11d0-b6fe-00a0c90f57da}`
    - Camera devices: `{ca3e7ab9-b4c3-4ae6-8251-579ef933890f}`
    - Imaging devices: `{6bdd1fc6-810f-11d0-bec7-08002be2092f}`

## Common class GUIDs to allow USB devices

- **Keyboard and mouse**: Add the following GUIDs to the device profile:

    - Keyboard: `{4d36e96b-e325-11ce-bfc1-08002be10318}`
    - Mouse: `{4d36e96f-e325-11ce-bfc1-08002be10318}`
- **Cameras, headphones and microphones**: Add the following GUIDs to the device profile:

    - USB Bus devices (hubs and host controllers): `{36fc9e60-c465-11cf-8056-444553540000}`
    - Human Interface Devices (HID): `{745a17a0-74d3-11d0-b6fe-00a0c90f57da}`
    - Multimedia devices: `{4d36e96c-e325-11ce-bfc1-08002be10318}`
    - Camera devices: `{ca3e7ab9-b4c3-4ae6-8251-579ef933890f}`
    - Imaging devices: `{6bdd1fc6-810f-11d0-bec7-08002be2092f}`
    - System devices: `{4D36E97D-E325-11CE-BFC1-08002BE10318}`
    - Biometric devices: `{53d29ef7-377c-4d14-864b-eb3a85769359}`
    - Generic software devices: `{62f9c741-b25a-46ce-b54c-9bccce08b6f2}`
- **3.5 mm headphones**: Add the following GUIDs to the device profile:

    - Multimedia devices: `{4d36e96c-e325-11ce-bfc1-08002be10318}`
    - Audio endpoint: `{c166523c-fe0c-4a94-a586-f1a80cfbbf3e}`

Note

The actual GUIDs might be different for your specific devices.