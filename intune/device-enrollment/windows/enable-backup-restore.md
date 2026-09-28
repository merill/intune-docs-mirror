---
layout: Conceptual
title: Enable Windows Backup for Organizations - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/windows/enable-backup-restore
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: maholdaa
ms.subservice: enrollment
description: Enable Windows backup and restore in Intune for employees or students.
ms.date: 2025-11-21T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 6d189e1a-9445-9f93-3f47-79adf4364b8c
document_version_independent_id: 6d189e1a-9445-9f93-3f47-79adf4364b8c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/windows/enable-backup-restore.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/windows/enable-backup-restore
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/windows/enable-backup-restore.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: 3e46a61b-dacd-52ba-4e4c-7791bb7e362d
---

# Enable Windows Backup for Organizations - Microsoft Intune | Microsoft Learn

Enable users to securely sync their settings to the cloud and restore them on new or reimaged devices. Together, Microsoft Intune and Windows Backup for Organizations lets users back up your organization's Windows settings and restore them on a Microsoft Entra joined device during enrollment.

Windows Backup for Organizations is a feature that's made up of the [Windows backup and restore settings](/en-us/windows/configuration/windows-backup/catalog) and is an option that can:

- Reduce migration overhead
- Minimize user disruption
- Strengthen device resilience against incidents
- Simplify your organization's transition to Windows 11

You can enable Windows backup and restore for devices in the Microsoft Intune admin center within the settings catalog, and under **Devices** &gt; **Enrollment**. The restore setting is a tenant-wide setting that applies to all users. After you turn on the restore option, users turning on their devices for the first time see the corresponding restore page during device enrollment.

## Benefits

Windows Backup for Organizations ensures that users have a consistent and personalized experience across different devices. Benefits include:

- Reduced troubleshooting: Confidently reset devices knowing that users can recover and return to previous settings.
- Seamless experience: Smoothly transition from devices running Windows 10 to devices running Windows 11 using saved backups.
- Enhanced productivity: Minimize downtime and maximize user productivity, whether resetting the device or reimaging, by restoring user settings to their preferred and familiar PC preferences.

## Requirements

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> **Backup** - Devices must be Microsoft Entra hybrid joined or Microsoft Entra joined and running one of the following versions:
> 
> - Windows 10, version 22H2 (build 19044.6216 or later)
> - Windows 11, version 22H2 (build 22621.5768 or later)
> - Windows 11, version 23H2 (build 22631.5768 or later)
> - Windows 11, version 24H2 (build 26100.4946 or later)
> 
> 
> **Restore** - Devices must be [Microsoft Entra joined](/en-us/entra/identity/devices/concept-directory-join). Restore is available on devices that are either on the August 2025 cumulative update, or running one of the following versions:
> 
> - Windows 11, version 22H2 (build 22621.3958 or later)
> - Windows 11, version 23H2 (build 22631.3958 or later)
> - Windows 11, version 24H2 (build 26100.1301 or later)
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To configure the restore setting, you must have Intune Service Administrator permissions.

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> Configure the **Install Windows quality updates** setting in the [enrollment status page profile](setup-status-page). If you're on a build older than July 2025, verify this setting is enabled on your devices.

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

The restore feature also requires:

- The device user must have at least one backup profile.
- If Autopilot is used, the Autopilot profile must be configured to use [user-driven mode](/en-us/autopilot/user-driven), not self-deploying mode.

## RBAC and tenant wide targeting

The restore setting for Windows Backup for Organizations is a tenant-wide setting. This means the restore setting is either turned on or off for all Windows devices in a tenant. The default configuration is **Not configured**, which turns off the restore setting for all devices.

## Enrollment

To enable Windows Backup for Organizations during enrollment, configure your backup and restore settings in the Microsoft Intune admin center. There are two areas where you need to configure settings: in the settings catalog, and under enrollment.

# [Backup](#tab/backup)
Complete these steps to configure the backup settings in the settings catalog.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) as an [Intune service administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator).
2. Go to **Devices** &gt; **Managed devices** &gt; **Configuration**.
3. Create a new policy.
    1. For **Platform**, select **Windows 10 and later**.
    2. For **Profile type**, select **Settings Catalog**.
4. Under the **Sync your settings** category, find the **Enable Windows backup** setting. Select the setting to enable it.
5. Finish the remaining steps to create your policy. Then select **Save**.

# [Restore](#tab/restore)
Complete these steps to configure the restore setting for enrollment.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) as an [Intune service administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator).
2. Go to **Devices** &gt; **Enrollment**.
3. Select the **Windows** tab.
4. Under **Enrollment options**, select **Windows Backup and Restore**.
5. For **Show restore page**, select **On**.

    Tip

    Before a user can restore a backup, you have to set up the backup settings in the settings catalog. To go to the settings catalog, select **Go to Settings Catalog to configure backup settings**.
6. Select **Save**.

The **Last modified** date updates to account for recent changes. Return to **Windows Backup and Restore** anytime to view and edit the setting again.

---

## Reporting

Per device reporting is available in the Microsoft Intune admin center.

1. Go to **Devices**.
2. Select the **Windows** tab.
3. Under the **Device name** column in the table, select a device.
4. Go to **Enrollment**.
5. In the table, under **Profile type**, look for **Windows Backup and Restore profile**. From here, you can check the state of the backup profile on the device, and see whether or not the device went through a restore. Possible statuses include:
    - Not Applicable
    - No policy assigned
    - Succeeded
    - Failed
    - No Backup Profiles
    - Setup as New PC Selected

For more information about the reporting available on the enrollment page, see [View enrollment reports](../monitor-reports).

## Known issues

Known issues with Windows Backup for Organizations include:

- This feature isn't supported in Government cloud or 21Vianet.
- This feature doesn't work for shared or userless devices.
- The restore feature isn't supported for versions earlier than Windows 11, version 22H2.
- When corporate accounts are used on Hyper-V virtual machines (VM) with phishing-resistant multifactor authentication (MFA) enforced, users are prompted to authenticate using a security key or smart card. However, due to Hyper-V VM limitations, these authentication methods can't pass through, resulting in an undesirable UI experience and preventing users from completing the authentication process.

    Note

    This issue is specific to VMs, particularly when users initially sign in with weaker authentication methods (such as a password or authenticator app) and phishing-resistant MFA is subsequently enforced.
- The restore feature isn't supported with the following provisioning methods:

    - Hybrid Azure AD Join
    - Workplace Join
    - Self-deployment mode
    - Technician flow of Windows Autopilot for pre-provisioned devices
    - Windows Autopilot reset flow
    - Manual enrollment through the Windows Settings app
    - Enrollment via Group Policy
    - Enrollment via Configuration Manager co-management
- This feature isn't supported on the following SKUs.

    | Edition | SKU |
    | --- | --- |
    | CloudEdition | CloudEdition, Windows 11 SE (203) |
    | CloudEditionN | CloudEditionN, Windows 11 SE N (202) |
    | Holographic | Windows 10 Holographic (136) |
    | IoTUAP | Windows 10 IoT Core (123) |
    | IoTUAPCommercial | Windows 10 IoT Core Commercial (131) |
    | PPIPro | Windows 10 TeamOS (119) |