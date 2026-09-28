---
layout: Conceptual
title: Windows Autopilot device preparation known issues | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/device-preparation/known-issues
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Information regarding known issues that might occur during a Windows Autopilot device preparation deployment.
ms.date: 2026-09-14T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: troubleshooting
locale: en-us
document_id: dcdda1dd-4300-040a-95db-bd35d4576bdc
document_version_independent_id: dcdda1dd-4300-040a-95db-bd35d4576bdc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/device-preparation/known-issues.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-preparation/known-issues
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/device-preparation/known-issues.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 617e573f-d422-3218-484d-960e2be30f84
---

# Windows Autopilot device preparation known issues | Microsoft Learn

This article describes known issues that can often be resolved with:

- Configuration changes.
- Cumulative updates.
- Might be resolved automatically in a future release.

Tip

RSS can be used to notify when new known issues are added to this page. For example, the following RSS link includes this article:

```url
https://learn.microsoft.com/api/search/rss?search=%22Information+regarding+known+issues+that+might+occur+during+a+Windows+Autopilot+device+preparation%22&locale=en-us&%24filter=
```

This example includes the `&locale=en-us` variable. The `locale` variable is required, but it can be changed to another supported locale. For example, `&locale=es-es`.

For more information on using RSS for notifications, see [How to use the docs](/en-us/intune/use-docs#notifications) in the Intune documentation.

## Known issues

### Device preparation deployments on Windows 365 devices time out after 60 minutes

Date added: *November 10, 2025* Date updated: *February 5, 2026*

There is a known issue for Windows 365 devices where the value set for **Minutes allowed before device preparation fails** in the Cloud PC provisioning policy does not get configured correctly during Autopilot device preparation provisioning. As a result, deployments time out if they require more than 60 minutes to install all configurations selected in the Device preparation policy. To avoid unexpected failures, we recommend that admins limit the number of blocking apps configured for the Device preparation policy in automatic mode until the issue is resolved. This issue will be fixed in the future.

**This issue was resolved in February 2026.**

### Exporting logs during the out-of-box experience (OOBE) doesn't show result

Date added: *January 6, 2025*

When a failure occurs during the provisioning process, an **Export logs** option is displayed to the user. When selected, it saves the file to the first USB drive on the device without displaying the browse dialog. The browse dialog isn't displayed for security reasons. Currently, users don't see failure or success messages to indicate the logs were saved. This issue will be fixed in the future.

### Apps and scripts tabs don't display properly when editing the Windows Autopilot device preparation profile

Date added: *December 18, 2024*

During the editing flow of the Windows Autopilot device preparation policy, there's a known issue when displaying the **Applications** and **Scripts** tabs where the tabs might display incorrect information. For example, under the **Scripts** tab, a list of applications might be shown instead of a list of scripts. The issue is impacting only the view in Microsoft Intune and not the configuration being applied to the device. The issue is being investigated.

As a workaround, select the table header **Allowed Applications** or **Allowed Scripts** to reload the table's contents.

### Win32, WinGet, and Enterprise App Catalog applications are skipped when Managed installer policy is enabled for the tenant

Date added: *October 10, 2024* Date updated: *April 10, 2026*

When the [Managed installer policy](/en-us/intune/device-configuration/endpoint-security/manage-app-control) is **Active** for a tenant, Win32 apps, Microsoft Store, and Enterprise App Catalog apps aren't delivered during OOBE. The apps are instead installed after the device gets to the Desktop and the Managed installer policy is delivered. The [Windows Autopilot device preparation deployment status report](whats-new#windows-autopilot-device-preparation-deployment-status-report-available-in-the-monitor-tab-under-enrollment) reports the apps as **Skipped.**

Note

Managed installer policy is always enabled automatically for Education customers due to the requirements for [Windows 11 SE](/en-us/education/windows/tutorial-deploy-apps-winse/).

For more information, see [Known issue: Windows Autopilot device preparation with Win32 apps and managed installer policy](https://techcommunity.microsoft.com/t5/intune-customer-success/known-issue-windows-autopilot-device-preparation-with-win32-apps/ba-p/4273286).

**This issue was resolved in April 2026.**

### Security group membership update failures might lead to non-compliant devices

Date added: *September 27, 2024*

If security groups aren't properly configured in Microsoft Intune, devices might lose compliance and be left in an unsecured state. The following are potential reasons for security group membership failures:

- **Retry failures**: Security group membership updates might not succeed during retry windows, leading to delays in group updates.
- **Static to dynamic group changes**: After the Windows Autopilot device preparation profiles are configured, changing a security group from static to dynamic could cause failures.
- **Owner removal**: If the **Intune Provisioning Client** service principal is removed as an owner of a configured security group, updates might fail.
- **Group deletion**: If a configured security group is deleted and devices are deployed before Microsoft Intune detects the deletion, security configurations might fail to apply.

To mitigate the issue, follow these steps:

1. **Validate security group configuration before provisioning**:

    - Ensure the correct security group is selected within the Microsoft Intune admin center or the Microsoft Entra admin center.
    - The security group should be configured within the Windows Autopilot device preparation profile.
    - The group shouldn't be assignable to other groups.
    - The **Intune Provisioning Client** service principal should be an owner of the group.
2. **Manually fix the provisioned devices**:

    - If devices are already deployed or the security group isn't applicable, manually add the affected devices to the correct security group.

Security group membership failures can be prevented by following these steps, ensuring devices remain compliant and secure.

### Deployment fails for devices not in the Coordinated Universal Time (UTC) time zone

Date added: *July 8, 2024* Date updated: *July 23, 2024*

Windows Autopilot device preparation deployments fail when devices aren't in the UTC time zone. The issue is being investigated.

As a workaround, customers can manually set the time zone in OOBE via Windows PowerShell until the issue is resolved:

```powershell
Set-TimeZone -Id "UTC"
```

**This issue was resolved in July 2024.**

### BitLocker encryption defaults to 128-bit when 256-bit encryption is configured

Date added: *July 8, 2024* Date updated: *September 14, 2026*

In some Windows Autopilot device preparation deployments, BitLocker encryption may default to 128-bit even though the admin configured 256-bit encryption due to a known race condition.

The issue is resolved in [KB5124012](https://support.microsoft.com/en-us/servicing/os/windows-11/2026/09/kb5124012-windows-11-26h1-security-update) and later Windows updates.

### Windows Autopilot device preparation policy shows 0 groups assigned

Date added: *June 18, 2024* Date updated: *July 23, 2024*

There's a known issue that the Windows Autopilot device preparation policy shows **0 groups assigned** even when:

- An assigned device security group was properly added to the policy.
- The **Intune Provisioning Client** service principal with AppID of **f1346770-5b25-470b-88bd-d5744ab7952c** is the owner of the device security group specified in the policy.

The issue is being investigated. As a workaround, create a new assigned device security group with the **Intune Provisioning Client** service principal with AppID of **f1346770-5b25-470b-88bd-d5744ab7952c** as the owner, and then assign the new device group to the Windows Autopilot device preparation policy. For more information on creating the assigned device group, see [Create an assigned device group](tutorial/user-driven/entra-join-device-group#create-an-assigned-device-group).

**This issue was resolved in July 2024.**

### Unable to assign Windows Autopilot device preparation policy to user group

Date added: *June 18, 2024* Date updated: *July 23, 2024*

There's a known issue where an administrator might not be able to assign the Windows Autopilot device preparation policy to a user group. When the issue occurs, the following error might occur:

> 
> **Unable to save group assignment for &lt;policy\_name&gt;. You do not have permission to save these assignments.**

The issue is being investigated. As a workaround, add the following additional role-based access control (RBAC) permission for the Windows Autopilot device preparation administrator role:

- **Device configurations**
    - Assign

For more information, see [Required RBAC permissions](requirements?tabs=rbac#required-rbac-permissions).

Note

The [Required RBAC permissions](requirements?tabs=rbac#required-rbac-permissions) article doesn't list the **Device configurations** - **Assign** permission. This permission requirement is only temporary until the issue is resolved. However, the article can be used as a guide on how to properly add this permission. **This issue was resolved in July 2024.**

### Device is stuck at 100% during the out-of-box experience (OOBE)

Date added: *June 3, 2024*

If during Windows Autopilot device preparation deployment a device gets stuck at 100% during the out-of-box experience (OOBE), the end-user needs to manually restart the device for the deployment to continue. This issue is a known issue and a fix is being worked on.

### Object with AppID of f1346770-5b25-470b-88bd-d5744ab7952c displays as Intune Autopilot ConfidentialClient

Date added: *June 3, 2024*

In some tenants, when trying to set the owner of the device group used in the Windows Autopilot device preparation policy, the service principal with AppID of **f1346770-5b25-470b-88bd-d5744ab7952c** displays as **Intune Autopilot ConfidentialClient** instead of **Intune Provisioning Client**. As long as the service principal has an AppID of **f1346770-5b25-470b-88bd-d5744ab7952c**, it's the correct service principal and can be selected.

### Conflict between Microsoft Entra ID and Windows Autopilot device preparation local administrator setting

Date added: *June 3, 2024*

There's a compatibility problem between the Windows Autopilot device preparation policy **User account type** setting and the Microsoft Entra ID **Local administrator settings**. Specifically, when the Windows Autopilot device preparation policy **User account type** setting is set to **Standard user** and the Microsoft Entra ID setting **Registering user is added as local administrator on the device during Microsoft Entra join (Preview)** under **Local administrator settings** is set to either **Selected** or **None**, provisioning gets skipped during a Windows Autopilot device preparation deployment. This settings conflict leads to a scenario where users could reach the desktop without having the expected applications installed. The Microsoft Entra ID **Local administrator settings** can be found by signing in to the [Azure portal](https://portal.azure.com/) and navigating to **Microsoft Entra ID** &gt; **Manage | Devices** &gt; **Manage | Devices settings**.

Until the issue is fixed, for users to be standard non-administrators on their device, make sure that the settings are set to one of the following three setting combinations:

- **Standard user option 1**

    - The Microsoft Entra ID **Local administrator settings** is set to **None**.
    - The Windows Autopilot device preparation policy **User account type** setting is set to **Administrator**.
- **Standard user option 2**

    - The Microsoft Entra ID **Local administrator settings** is set to **Selected** and the standard non-administrator users aren't selected.
    - The Windows Autopilot device preparation policy **User account type** setting is set to **Administrator**.
- **Standard user option 3**

    - The Microsoft Entra ID **Local administrator settings** is set to **All**.
    - The Windows Autopilot device preparation policy **User account type** is set to **Standard user**.

In all three cases, the end result is that the user is a standard non-administrative user on the device.

If the intention is for the user to be a local administrator user on the device, make sure that the settings are set to one of the following two setting combinations:

- **Administrator user option 1**

    - The Microsoft Entra ID **Local administrator settings** is set to **All**.
    - The Windows Autopilot device preparation policy **User account type** setting is set to **Administrator**.
- **Administrator user option 2**

    - The Microsoft Entra ID **Local administrator settings** is set to **Selected** and the administrator users are selected.
    - The Windows Autopilot device preparation policy **User account type** setting is set to **Administrator**.

### Initial release of Windows Autopilot device preparation

Date added: *June 3, 2024*

The initial release of Windows Autopilot device preparation has the following known issues and limitations:

- Dependency and supersedence relationships are marked in reports as **Dependent**.
- Application uninstall intent is marked in reports as **Installed** if completed successfully.
- Managed Installer policy during the out-of-box experience (OOBE) isn't supported due to the possibility of incorrect reporting.
- Custom compliance isn't supported during Windows Autopilot device preparation deployments.
- The device health script isn't supported during Windows Autopilot device preparation deployments.