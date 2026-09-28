---
layout: Conceptual
title: Update Windows BIOS using configuration MDM policy - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-bios-windows
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
description: Learn more about the BIOS configuration profile that can manage traditional BIOS settings in Microsoft Intune. You use an OEM tool to create a configuration file with the settings. You deploy an OEM Win32 app to the devices to read the configuration file and BIOS passwords. Then, you create a BIOS configuration policy in Intune to add the configuration file and assign the policy to your devices.
ms.date: 2024-06-06T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: madakeva
locale: en-us
document_id: d8e43763-4a8b-e3b9-5924-39386d737446
document_version_independent_id: d8e43763-4a8b-e3b9-5924-39386d737446
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-bios-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-bios-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-bios-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/caec7b7f-4941-4578-b79f-c63b1c1f5af4
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/754dea88-f800-4835-b6b5-280cb5d81e88
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 820b94a5-11f5-0a62-3db2-6679e6e0fe42
---

# Update Windows BIOS using configuration MDM policy - Microsoft Intune | Microsoft Learn

In Intune, you can use a **BIOS configuration and other settings** device configuration policy to enable or disable BIOS features and settings.

Using an OEM tool, you create a BIOS configuration file that configures the BIOS features. On the devices, you install the OEM Win32 app that reads the configuration. Then, in the Intune BIOS policy, you add the BIOS configuration file, and assign the policy to your devices.

The configuration file typically includes settings that secure the device and secure its built-in hardware.

For example, you want to prevent end users from reimaging the device and getting out of Intune management. For this task, you create a BIOS configuration file that disables booting from USB. Then, you add this file to the Intune policy and enable a BIOS password. These steps make sure the configuration isn't overwritten.

This feature applies to:

- Windows
- Dell devices

This article includes more information on the configuration file and Win32 app, and shows you how to create the **BIOS configuration and other settings** policy in Intune.

Warning

BIOS configuration changes can impact device functionality and operability, including the ability to boot or access Bitlocker encrypted drives. This feature allows Intune administrators to easily update BIOS configurations on their devices. When you make changes, test and deploy in phases to minimize the impact of any unexpected configurations.

## Prerequisites

- To configure the Intune policies, at a minimum, sign in to the Intune admin center with the **Policy and Profile manager** role. For information on the built-in roles in Intune, and what they can do, go to:

    - [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview)
    - [Built-in role permissions for Microsoft Intune](../../fundamentals/role-based-access-control/ref-built-in-roles)
- This feature supports organization-owned devices that are MDM enrolled in Intune. Personal devices and devices not enrolled in Intune aren't supported.
- Make sure the devices don't have an existing BIOS password configured. This feature requires that Intune have the BIOS password. If Intune doesn't have the BIOS password of the device, then it can't update the BIOS configuration.

## Step 1 - Create the configuration file and deploy the app

This section focuses on using the OEM tool to create the configuration file, and deploying the OEM Win32 app to the devices.

1. Create the configuration file using an OEM tool. In the file, add and configure the features you want to configure. You can add any configuration settings that the OEM supports.

    - For Dell, you can use the [Dell Command](https://www.dell.com/support/kbdoc/000214308/dell-command-endpoint-configure-for-microsoft-intune) (opens Dell's website) tool to create the BIOS configuration file.
2. When you create the configuration file, there's a coordinating Win32 app provided by the OEM. Deploy the OEM Win32 app to the devices. This app:

    - Acts as an agent that reads the configuration file you create, and reads the BIOS passwords of the devices.
    - Must be installed on all devices before you assign the Intune BIOS configuration policy.

    For Dell, you can download the [Dell Command](https://www.dell.com/support/kbdoc/000214308/dell-command-endpoint-configure-for-microsoft-intune) (opens Dell's web site) app.

    To install this app on the devices, you can use Intune:

    - Add the app to Intune and make it a required app.
    - Assign the app to the group or assignment filter you create in the next step (in this article).

    For information on Win32 apps in Intune, go to [Add, assign, and monitor a Win32 app in Microsoft Intune](../../app-management/deployment/add-win32).

## Step 2 - Create a group or use an assignment filter

It's recommended to focus this policy on a specific set of devices. Your options:

- **Option 1** - Create a group that includes the devices. When you create the app policy and the BIOS configuration policy, you assign the policies to this group.
- **Option 2** - Use an assignment filter based on the device manufacturer. When you create the filter, target the OEM devices. When you assign the app and BIOS configuration policies, add this filter.

For information on these features, go to:

- [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups)
- [Use filters when assigning your apps, policies, and profiles in Microsoft Intune](../../fundamentals/filters/overview)

## Step 3 - Create the BIOS configuration policy in Intune

This policy is where you add the configuration file you created in Step 1 with the OEM tool.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Templates** &gt; **BIOS configuration and other settings**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your policies so you can easily identify them later. For example, a good profile name is **BIOS config password**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.

    Select **Next**.
6. In **Configuration settings**, configure the following settings:

    - **Hardware**: Select your hardware OEM vendor from a list of supported OEMs. Currently, only Dell is supported.
    - **Disable per-device BIOS password protection**: This setting manages the password that protects the BIOS configuration on the device. Your options:

        - **No**: Intune generates a unique device password for each device. To access and update the BIOS configuration on the device, users must enter this password.
        - **Yes**: There isn't a password protecting the BIOS. Any previous passwords are removed. End users can access the BIOS and change the BIOS settings on the device.
    - **Configuration file**: Upload the configuration file generated with your OEM tool.

        For Dell, upload the Dell Client Configuration Tool Kit file (`.cctk`). The file size limit is 2 MB.

    Select **Next**.
7. In **Assignments**, select the new device group you created. This group receives your profile. For information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
8. In **Review + create**, review your settings, and select **Create**. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

The next time each device checks in, the policy applies.

## Monitor your policy with built-in reports

In the Intune admin center, after you create a policy, you can monitor its status, and see any errors.

1. In the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Policies** tab.
2. Select the policy you want to monitor. The **Device status** report shows the status of the policy, and shows any error details for troubleshooting.

For more information, go to:

- [Monitor device configuration policies in Microsoft Intune](../monitor-device-profile)
- [Intune reports](../../device-management/reports/overview)

## Retrieve the BIOS passwords

Intune stores the BIOS passwords for each device. You can get the BIOS passwords using Microsoft Graph. To test the Graph APIs, you can use [Microsoft Graph Explorer](/en-us/graph/graph-explorer/graph-explorer-overview).

Important

Make sure you back up all passwords outside of Intune. If you don't backup the passwords outside of Intune, then be aware of the following scenarios:

- If a device is removed from Intune management, then admins can still read BIOS passwords using the [Microsoft Graph hardwarePasswordDetails API](/en-us/graph/api/intune-deviceconfig-hardwarepassworddetail-get).
- If the Intune subscription for your tenant ends, then there's no way to read or retrieve BIOS passwords. In this situation, your only option is to contact your OEM.

### Option 1 - Read the BIOS password one device at a time

This option gets the BIOS passwords, one device at a time.

1. Create a custom Intune RBAC role with the **Read Bios Password** permission:

    1. At a minimum, sign in to the [Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) as a member of the **Intune Role Administrator** built-in Intune role.

        For information on the Intune built-in roles, go to:

        - [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview)
        - [Built-in role permissions for Microsoft Intune](../../fundamentals/role-based-access-control/ref-built-in-roles)
    2. Select **Tenant administration** &gt; **Roles** &gt; **Create a new role**.
    3. **Name** your role and select **Next**.
    4. In **Permissions**, expand **Managed devices** &gt; Set **Read Bios Password** to **Yes**.
    5. Select **Next** &gt; **Next** &gt; **Create**.
2. Sign in to your Graph tool with this custom RBAC role, and use the [Microsoft Graph hardwarePasswordDetails API](/en-us/graph/api/intune-deviceconfig-hardwarepassworddetail-get):

    - `https://graph.microsoft.com/beta/deviceManagement/hardwarePasswordDetails('<deviceID>')`

### Option 2 - Read the BIOS password of all devices

This option gets a list of all the BIOS passwords of all devices.

1. At a minimum, you need the **Intune Administrator** role in Microsoft Entra ID.
2. Sign in to your Graph tool with this role, and use the [Microsoft Graph hardwarePasswordDetails API](/en-us/graph/api/intune-deviceconfig-hardwarepassworddetail-get):

    - `https://graph.microsoft.com/beta/deviceManagement/hardwarePasswordDetails`

For information on the built-in roles, go to [Microsoft Entra built-in roles](/en-us/entra/identity/role-based-access-control/permissions-reference).

## Remove BIOS configuration password

If you're planning to stop managing the BIOS of your devices or remove devices permanently from your tenant, then you must remove the BIOS password.

To remove the BIOS password, in your Intune BIOS configuration policy, set the **Disable per-device BIOS password protection** setting to **Yes**. Then, assign the policy. When the device [checks in with Intune](../troubleshoot-device-profiles#policy-refresh-intervals), the policy applies. On the device, you can also manually sync the device with Intune to apply the policy.

After the policy applies, reboot the device.

Unenrolling the device from Intune doesn't remove the BIOS password. If you unenroll the device before you disable the password, then you need to update the password manually on the device.

## BIOS configuration vs DFCI

Intune has two features that can manage the BIOS settings on Windows devices: **BIOS configuration and other settings** and **Device Firmware Configuration Interface (DFCI)**.

The following table compares these options.

| **Feature** | **BIOS configuration and other settings** | **DFCI** |
| --- | --- | --- |
| **Supported OEMs** | Dell Possibly more in the future | Surface, Acer, Asus, Dynabook, Fujitsu, Panasonic For more information, go to [Microsoft DFCI Scenarios](https://microsoft.github.io/mu/dyn/mu_feature_dfci/DfciPkg/Docs/Scenarios/DfciScenarios/). |
| **Supported configurations** | Any configurations available in your OEM tool | A set of settings to control security features, some hardware features, boot options, ports, and more |
| **How settings are applied** | Intune delivers the configuration file when the policy is assigned. The OEM agent on the device applies the configuration. | Through UEFI CSP using the DFCI layer, which is isolated from the OS |
| **Blocks access to BIOS menu** | Yes, via BIOS passwords | Yes, via certificates |
| **Configuration during Windows Autopilot** | In the Enrollment Status Page (ESP) settings, select the OEM Win32 app. | Intune automatically enrolls the device in DFCI mgmt. |
| **Reporting** | Reports if the configuration file applied. | Granular report for each setting you configure. |
| **Intune policy type** | **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Templates** &gt; **BIOS configuration and other settings** | **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Templates** &gt; **Device Firmware Configuration Interface** |

For information on DFCI, go to:

- [Device Firmware Configuration Interface (DFCI) profiles on Windows devices in Microsoft Intune](configure-dfci-windows)
- [Microsoft DFCI Scenarios](https://microsoft.github.io/mu/dyn/mu_feature_dfci/DfciPkg/Docs/Scenarios/DfciScenarios/)
- [DFCI on Surface devices](/en-us/surface/surface-manage-dfci-guide)