---
layout: Conceptual
title: Add Platform SSO policy to ADE Profile on macOS devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/configure-platform-sso-during-enrollment
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
description: Add a settings catalog platform single sign-on (PSSO) policy to an Automated Device Enrollment (ADE) profile and configure it to run during Setup Assistant with modern authentication on macOS devices.
ms.date: 2026-06-01T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: iye, arnab
locale: en-us
document_id: 84f95cdc-6420-3a77-b8dc-e8d8bc63c9b5
document_version_independent_id: 84f95cdc-6420-3a77-b8dc-e8d8bc63c9b5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/settings-catalog/configure-platform-sso-during-enrollment.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/settings-catalog/configure-platform-sso-during-enrollment
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/settings-catalog/configure-platform-sso-during-enrollment.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/837687b0-8846-4eb2-adb6-2b853e8c70c4
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c797fa2-4419-46e7-a4e3-4c97d0a1f2a0
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 8d144fe4-2819-7477-7580-89838a4bf616
---

# Add Platform SSO policy to ADE Profile on macOS devices - Microsoft Intune | Microsoft Learn

On macOS devices, you can configure [Platform Single Sign-On (PSSO)](configure-platform-sso-macos) during Automated Device Enrollment (ADE). With Platform SSO, users sign in with their Microsoft Entra account and can get immediate access to Microsoft Entra ID resources. Platform SSO also minimizes the number of times users need to enter their organizational credentials.

When you add the Platform SSO policy and enable the Setup Assistant await final configuration in an ADE enrollment profile, the Platform SSO policy runs during device registration. When users arrive at the desktop, they're already signed in to Microsoft Entra resources and can start using productivity apps, like Teams, immediately.

This feature:

- Enables Microsoft Entra device registration during macOS Setup Assistant.
- Establishes device identity early in the provisioning process.
- Allows Platform SSO credentials to be set up during initial device configuration.
- Minimizes delays accessing resources, including resources protected by Conditional Access.

This article lists and describes the settings you need to configure to enable Platform SSO during ADE with Setup Assistant. It also lists the other required steps to use this feature, including adding the Company Portal as a line-of-business app, and configuring the enrollment profile.

To learn more about Platform SSO, see [Platform SSO configuration guide for macOS devices using Microsoft Intune](configure-platform-sso-macos).

This feature applies to:

- macOS

## Before you begin

- During enrollment, users are prompted to enter their Microsoft Entra organizational credentials at least twice. The first sign-in starts the regular enrollment process. The second sign-in authenticates the identity in Company Portal, which gets the SSO extension.
- This feature requires three different policies - settings catalog policy, line-of-business app policy, and enrollment profile. All the policies and settings listed in this article are required and work together. If any of the steps are misconfigured or skipped, the enrollment fails. In this situation, [wipe](../../device-management/actions/wipe) the device, follow the steps, and re-enroll the device.
- Assign all the policies to the same **Assigned (static)** user groups that will use this feature. You can use [assignment filters](../../fundamentals/filters/overview) on the static user groups.

    You can create new groups for this feature and add the users to those groups. If you assign these policies to different groups, Platform SSO during enrollment fails.

    Remember, the groups must be:

    - User groups, not device groups. This feature doesn't work with device groups.
    - Assigned (static) groups, not dynamic groups. This feature doesn't work with dynamic groups.
- Platform SSO has its own set of requirements and configurations. Make sure to review the requirements before you start configuring this feature. For more information, see [Platform SSO configuration guide for macOS devices using Microsoft Intune](configure-platform-sso-macos).

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This feature supports the following platform:
> 
> - macOS 26 and newer
> 

![](../../media/icons/16/enrollment.svg)**Enrollment methods**

> 
> - Devices enrolled using Apple Business
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To configure this policy, use an account with at least one of the following roles:
> 
> - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).
> 

## Step 1 - Create or update the Platform SSO settings catalog policy

This policy enables the Platform SSO registration process during Setup Assistant in the ADE enrollment flow.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), create the settings catalog policy (**Devices &gt; Manage devices &gt; Configuration**):

    - If you already use Platform SSO on existing devices, update your existing Platform SSO settings catalog policy. You can apply only one Platform SSO policy to a device.
    - If you're configuring Platform SSO for the first time, follow the steps in [Platform SSO configuration guide for macOS devices using Microsoft Intune](configure-platform-sso-macos).

        When you create the policy, Microsoft recommends using the **Secure Enclave** authentication method.
2. In your settings catalog policy, add and configure the following setting:

    | Name | Configuration value | Description |
    | --- | --- | --- |
    | **Authentication &gt; Extensible single sign-on &gt; Platform SSO &gt; Enable Registration During Setup** | Enabled | When enabled, the system enables the Platform SSO registration process during Setup Assistant. |

    **If you're using the Password authentication method**, also add and configure the following setting. If you're not using the **Password** authentication method, don't add or configure the following setting.

    | Name | Configuration value | Description |
    | --- | --- | --- |
    | **Authentication &gt; Extensible single sign-on &gt; Platform SSO &gt; Enable Create First User During Setup** | Enabled | When enabled, the system enables the password synchronization experience during Setup Assistant.  Configure this setting if you're using the **Password** authentication method. If you're not using the **Password** authentication method, it's not required to configure this setting. |
3. Assign the policy to the static groups you created.

When you create the Platform SSO settings catalog policy, you add and configure more settings than what's listed in this article. This article only lists the settings that are required to enable Platform SSO during ADE with Setup Assistant. So, add this setting to your existing Platform SSO policy. Or, if you're creating a new Platform SSO policy, add this setting along with the other Platform SSO settings that are required to configure Platform SSO.

## Step 2 - Install Company Portal as a line-of-business app

The Company Portal for macOS deploys and installs the Microsoft Enterprise SSO plug-in. This plug-in enables Platform SSO. Make sure you add the latest Company Portal version. If you install an older version of the Company Portal, Platform SSO fails.

1. Download the Company Portal for macOS PKG app from https://go.microsoft.com/fwlink/?linkid=853070.

    Important

    Company Portal 5.2604.0 and newer is required.
2. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), add the Company Portal as a line-of-business (LOB) app (**Apps &gt; All Apps &gt; Create**). In the **App bundle ID** list, only add the `com.microsoft.CompanyPortalMac` app bundle ID. Remove any app bundle IDs that aren't related to the Company Portal.

    - [Add macOS Line-of-Business (LOB) Apps to Microsoft Intune](../../app-management/deployment/add-lob-macos)
3. Make it a required app and assign it to the same groups as the Platform SSO policy you created or updated in Step 1.

When Intune detects the Company Portal as a deployed policy, it sends the Company Portal with priority in the enrollment process.

## Step 3 - Set up enrollment profile and configure await final configuration

This policy configures the enrollment profile to run during Setup Assistant with modern authentication and configures the await final configuration. These settings are required for Platform SSO to run correctly during enrollment.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), create the Automated Device Enrollment profile (**Devices** &gt; **Device onboarding** &gt; **Enrollment** &gt; **Apple** tab):

    - [Set up automated device enrollment (ADE)](../../device-enrollment/apple/setup-automated-macos)
2. In **Management Settings**, configure the following settings:

    | Name | Configuration value |
    | --- | --- |
    | **User affinity** | Enroll with User Affinity |
    | **Authentication** | Setup Assistant with modern authentication |
    | **Await final configuration** | Yes |
    | **Locked enrollment** | Yes |
3. Assign the profile to the same groups as the Platform SSO policy you created or updated in Step 1.

When devices enroll using this ADE profile, the Platform SSO policy and LOB app policy will automatically apply during Setup Assistant. When enrollment completes and users arrive at the desktop, they have a more integrated sign-in experience on the device and can access Microsoft Entra ID resources.

## Possible issues and resolutions

If there are issues completing the Setup Assistant with Platform SSO (PSSO), make sure all three policies and their settings are configured and assigned correctly. If troubleshooting is still needed after verifying the policies, the following steps can help.

### Unable to sign in message during Setup Assistant

**Issue**: During Setup Assistant, you might see the following error message:

```error
Unable to sign-in  
There was an issue with the extension while registering your account for single sign-on. Try again in a few moments or contact your administrator.
```

The Company Portal includes the SSO extension used by Platform SSO. If the settings catalog policy and/or the Company Portal policy arrive late, Setup Assistant might show this message.

It's possible the Platform SSO settings catalog policy is delivered, and the Company Portal is still downloading or installing. Enrollment actions occur in separate steps rather than as a single transaction.

**Resolution**: Select the **Try again** button on the error message until the Company Portal finishes downloading and installing. When it completes, the SSO extension is available and the error message no longer appears.

### Remove Platform SSO and reenroll if steps are misconfigured

All the steps in this article are required - the settings catalog policy, Company Portal as a LOB app, and using Setup assistant with Modern Authentication and await final configuration enabled in the ADE profile. If any of these steps are misconfigured or missing, then the configuration fails.

In this situation, remove the existing Platform SSO (PSSO) configuration and re-enroll the devices by using the following steps. Complete all of the following steps. For more information, see [Steps to Opt out of Platform SSO on macOS](/en-us/entra/identity/devices/troubleshoot-mac-sso-extension-plugin#steps-to-opt-out-of-platform-sso-on-macos).

1. Unassign the Platform SSO policy that has the **Enable Registration During Setup** setting enabled. [Sync](../../device-management/actions/sync) the device to ensure the policy is removed.
2. Update the Platform SSO policy and set the **Enable Registration During Setup** setting to disabled. [Sync](../../device-management/actions/sync) the device to ensure the setting is removed.

    If you use the **Password** authentication method in the Platform SSO policy, set the **Enable Create First User During Setup** to disabled. [Sync](../../device-management/actions/sync) the device.
3. [Wipe](../../device-management/actions/wipe) the device. Wiping is required as it restarts the enrollment process and applies the updated enrollment profiles.

When complete, follow the steps in this article and make sure all your policies are correctly configured. Ensure you update the Platform SSO policy to set the **Enable Registration During Setup** setting to enabled.

Tip

Platform SSO and its components, including the Microsoft Enterprise SSO Extension plugin, are features of Microsoft Entra. Intune manages the deployment and configuration of these features on enrolled devices. If you need more troubleshooting help, see:

- [Troubleshooting the Microsoft Enterprise SSO Extension plugin on Apple devices](/en-us/entra/identity/devices/troubleshoot-mac-sso-extension-plugin)
- [macOS Platform single sign-on known issues and troubleshooting](/en-us/entra/identity/devices/troubleshoot-macos-platform-single-sign-on-extension)