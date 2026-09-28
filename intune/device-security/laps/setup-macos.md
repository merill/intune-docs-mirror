---
layout: Conceptual
title: Set up local admin account creation and password management for macOS devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/laps/setup-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: protect
description: Set up macOS account configuration with LAPS through automatic device enrollment for macOS devices in Intune.
ms.date: 2026-04-01T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: annovich
locale: en-us
document_id: 8d1162cf-1708-8b5c-0157-dd117cec544c
document_version_independent_id: 8d1162cf-1708-8b5c-0157-dd117cec544c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/laps/setup-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/laps/setup-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/laps/setup-macos.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/837687b0-8846-4eb2-adb6-2b853e8c70c4
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c797fa2-4419-46e7-a4e3-4c97d0a1f2a0
platformId: 9d80db93-3f15-01f0-e55f-467a6826ee90
---

# Set up local admin account creation and password management for macOS devices - Microsoft Intune | Microsoft Learn

You can use a macOS automated device enrollment (ADE) profile to configure a newly enrolled macOS device for both admin and user account configuration alongside Microsoft local admin password solution (LAPS). **macOS account configuration with LAPS** is an optional set of configurations you can use in new and existing macOS ADE profiles with and without user device affinity. These configurations for account management only apply to new enrollments.

With *macOS local account configuration with LAPS*, devices are provisioned with a local administrator account that has a strong, encrypted, and randomized admin password, which is stored and encrypted by Intune. Similarly, a local standard user account can also be provisioned within the enrollment profile. After enrollment, Intune automatically rotates the LAPS-managed administrator password every six months. To supplement autorotation, Intune admins with sufficient permissions can use the Intune admin center to view a devices local administrator account password and can manually rotate that password at need with remote device actions.

The Intune generated password for the admin account is 15 characters with a mixture of lowercase and uppercase letters, numbers, and special symbols.

Because *macOS local account configuration with LAPS* is enabled only during automated device enrollment (ADE) after a factory reset, a previously enrolled device must reenroll with Intune using a LAPS enabled ADE profile to be supported for LAPS for the administrator account.

Important

There is a known issue that affects devices running macOS versions earlier than macOS 26.4. When a macOS device enrolls via ADE with a configured local admin account and a targeted passcode profile, it prompts for an admin password reset—even if **Change at next auth** is not enabled or if a value is set for Max Age (days). This does not affect the standard account.

As a workaround, manually rotate the admin password after the reset on the device to keep the Intune and device password state in sync. Upgrade your device to macOS 26.4 to resolve this issue.

Important

The local admin account does not receive a secure token, due to platform limitations. The first account that signs in after enrollment receives the secure token, which at this time will always be the local user account.

Tip

The Intune implementation of macOS LAPS is similar but distinct from Intune support for Windows LAPS. For information about Windows LAPS in Intune, see [Local administrator account](setup-macos#local-administrator-account).

## Prerequisites

The following are device requirements for the macOS local account configuration with LAPS solution:

- macOS 12 and later
- Devices must be synced over to Intune from Apple Business/School Manager
- Devices must enroll with Intune through a macOS ADE enrollment profile after a factory reset.

Important

macOS LAPS supports ADE enrollments that occur as part of the initial device setup experience. Enrollment scenarios that re‑initiate ADE from an existing macOS installation (for example, by using the `profiles renew` command) aren't supported.

## Role-based access controls for macOS LAPS

The account of an admin that's trusted to view or rotate the local admin account password for a device that was onboarded to macOS LAPS, must have the following Intune role-based access control (RBAC) permissions:

Category: **Enrollment programs**:

- Set **Rotate macOS admin password** to **Yes**
- Set **View macOS admin password** to **Yes**

Important

The two permissions for *Enrollment programs* aren't included with any Intune built-in role or with the Microsoft Entra built-in role of Intune Administrator. Instead, use a [custom Intune role](../../fundamentals/role-based-access-control/create-custom-role) to assign this permission to users who should have these capabilities.

For permissions and details required to manage macOS policies for automated device enrollment, see [Set up automated device enrollment (ADE) for macOS](../../device-enrollment/apple/setup-automated-macos).

## Configuration account and password options

This section provides details for configuring *macOS local account configuration with LAPS*, which is accomplished during step 12 of the [Create an enrollment policy](../../device-enrollment/apple/setup-automated-macos#create-an-enrollment-policy) procedure for macOS automatic device enrollment (ADE) profiles.

When you [configure a macOS automated device enrollment profile](../../device-enrollment/apple/setup-automated-macos), the **Account Settings** tab presents options to configure both the Local administrator account and the Local user account. By default, these options are both set to *No*.

![Screen shot of the default appearance of the automated device enrollment profiles Account Setting pane.](media/setup-macos/account-settings-initial-configuration.png)

When you select **Yes** for either the local or admin or user account options, you're configuring both the macOS local admin account with LAPS configuration as well as a standard user account for devices that enroll using this enrollment profile.

Unique account passwords are created using 15 characters with a mixture of lowercase and uppercase letters, numbers, and special symbols.

Important

For devices with LAPS accounts configured, target password policies only through the settings catalog and disable the **Change at next authentication** setting.

Password settings configured through compliance policies or device restriction templates enable **Change at next authentication** by default and can cause sign-in issues for newly created LAPS accounts.

Whenever any part of the local account configuration, the **Await final configuration** setting is always set to **Yes** in the backend by default. This setting is set because the account configuration occurs during Setup Assistant.

### Local administrator account

![Screen capture that shows the options available for an admin account.](media/setup-macos/configure-local-admin-account-options.png)

The following are examples of the available configuration options. Additional details are accessible through the *Information* icons that follow the name of some settings.

Note

For macOS ADE enrollment policies without user device affinity, we recommend setting **Admin account username** to `{{serialNumber}}-admin` or `{{serialNumber}}-user`. Using the device serial number helps ensure each userless ADE device has a unique identifier.

- **Admin account username** - Specify the account name or use one of the following supported variables to dynamically create the name. By default, this field uses *Admin*.

    - {{serialNumber}} - for example, **F4KN99ZUG5V2**
    - {{partialupn}} - for example, **John.Dupont**
    - {{managedDeviceName}} - for example, **F2AL10ZUG4W2\_14\_4/15/2025\_12:45PM**
    - {{onPremisesSamAccountName}} - for example, **JDoe**
- **Admin account full name** - Specify the account name or use one of the following supported variables to dynamically create the name. By default, this field uses *Admin*.

    - {{username}} - for example, **John@contoso.com**
    - {{serialNumber}} - for example, **F4KN99ZUG5V2**
    - {{onPremisesSamAccountName}} - for example, **JDoe**
- **Hide in Users & Groups** - Make the admin account hidden in the sign-in window and in Users & Groups. By default, this set to *Not Configured*.
- **Admin account password rotation period (days)** - If configured, this setting dictates the period (1-180 days) after which the administrator account password is automatically rotated. This rotation is in addition to the automatic rotation that happens once every 180 days.

### Local user account

![Screen capture that shows the options available for a non-admin user account.](media/setup-macos/configure-local-user-account-options.png)

The following is some guidance for the available options. Additional details are accessible through the Information icons that follow the name of some settings.

- **Account type** - By default this is set to *Standard* to create a standard user account. The local user account type is set to administrator if no local admin account is configured, which is a platform limitation as an admin account is always required to set up any macOS device.
- **Prefill account info** - Set this option to *Yes* if you want to manage the account name or restrict editing.
- **Primary account name** - Specify the account name or use one of the following supported variables to dynamically create the name. Setup Assistant uses this value to prefill the Account Name field if *Prefill account info* is set to *Not configured*. By default, this field uses the *{{partialupn}}* variable.

    - {{serialNumber}} - for example, **F4KN99ZUG5V2**
    - {{partialupn}} - for example, **John.Dupont**
    - {{managedDeviceName}} - for example, **F2AL10ZUG4W2\_14\_4/15/2025\_12:45PM**
    - {{onPremisesSamAccountName}} - for example, **JDoe**
- **Primary account full name** - Specify the full name for the account or use one of the following variables to dynamically create the name. Setup Assistant uses this value to prefill the Full Name field if *Prefill account info* is set to *Not configured*. By default, this field uses the *{{username}}* variable:

    - {{username}} - for example, **John@contoso.com**
    - {{serialNumber}} - for example, **F4KN99ZUG5V2**
    - {{onPremisesSamAccountName}} - for example, **JDoe**
- **Restrict editing** - Prevent the end user from editing the full name and account name. By default, this is set to *Not configured*.

## View account and password details

To view the local Administrator password of a device, your own account must be assigned the following Intune RBAC permission:

- Category: **Enrollment programs** with **View macOS admin password** set to **Yes**

### To view the admin account password

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **macOS devices** &gt; select a **macOS device** to open its *Overview* pane &gt; **Passwords and keys**.

On the **Passwords and keys** pane, you can retrieve the admin password for the macOS device under the **Local administrator account password** section. Here you can also see the last time the password was rotated, manually or automatically.

To see whether an enrolled macOS device has an Intune managed admin password, if the password can be successfully retrieved in the console, that means the password for the local administrator account is managed by Intune.

![Screen capture that shows the Passwords and keys pane, and the Rotate local admin password options.](media/setup-macos/passwords-and-keys-pane.png)

## Manually rotate admin account password

LAPS policy includes a schedule for automatically rotating account passwords (once every six months). In addition to a scheduled rotation, you can use the Intune [device action](../../device-management/actions/) of **Rotate local admin password** to manually rotate a devices password at any time.

To use this device action, your account must be assigned the [Intune RBAC permission](#role-based-access- controls-for-macos-laps) of:

- Category: **Enrollment programs** with **Rotate macOS admin password** set to **Yes**

### To rotate the admin password

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **macOS devices** &gt; select a macOS device with the account you want to rotate.
2. On the devices *Overview* pane, from the list of options at the top of the pane select **Rotate local admin password**.

    ![Screen capture of a devices overview pane.](media/setup-macos/macos-device-overview.png)
3. To confirm when the password was last rotated for the device, from the device's *Overview* pane:

    1. Expand **Monitor** and then select **Passwords and keys**.
    2. On the **Passwords and keys** pane, you can find the last date and time that the password was rotated.

## Monitor password rotation

Password viewing and rotation both create Intune Audit events that you can view from within the Intune admin center.

In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Tenant administration** &gt; **Audit logs**.

Look for the following entries:

- **Get AdminAccountDto** - Identifies when someone viewed the admin password.
- **rotateLocalAdminPassword ManagedDevice** - Identifies when the admin password was rotated.