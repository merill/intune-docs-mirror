---
layout: Conceptual
title: Technical preview 2108 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2108
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2108.
ms.date: 2021-08-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 78ad1b56-f206-0264-e23e-5716b9385bf5
document_version_independent_id: e41ad0c7-943e-f539-61c1-eb382cd04860
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2021/technical-preview-2108.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2021/technical-preview-2108
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2021/technical-preview-2108.md
platformId: e0d6e6a0-21ac-e27f-9298-24aadf752380
---

# Technical preview 2108 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2108. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Export to CSV

You can now export the contents of a grid view in the console along with the column headers to a comma-separated values (CSV) file that can be used to import to Excel or other applications. While you could previously cut and paste from a grid view, exporting to CSV makes extracting a large number of rows faster and easier. You can export either all or selected items from the following nodes:

- Device Collections
- User Collections
- Devices
- Users

To export the information, select **Export to CSV file** from either the ribbon or the right-click menu. Choose **Export selected items** to only export items you've already selected, or you can choose to **Export all items**.

![Screenshot of the export to csv option in the ribbon of the device collections node](media/9663857-export-csv.png)

## Custom properties for devices in the console

In Configuration Manager current branch version 2107, you can use the [administration service to set custom properties on devices](../../../develop/adminservice/custom-properties). These custom properties let you add external data to a device to help with deployment targeting, collection building, and reporting.

Starting in this technical preview release, you can create and edit these custom properties in the Configuration Manager console. This new user interface makes it easier to view and edit these properties. You can still use the administration service interface to automate the process from an external system.

![Custom Properties tab on a device with multiple values.](media/10642650-custom-device-properties.png)

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select the **Devices** node.
2. Select a device, and then in the ribbon select **Properties**
3. Switch to the **Custom Properties** tab.
4. Select the gold star icon ![](media/new-icon.png) to create a new custom property. Provide a name for the property and set a value for this device. Select **OK** to save the properties.

You can now create a collection that queries for this property from the **Device Custom Properties** class.

## Improvements to Software Center notifications with logos

In [technical preview version 2011](../2020/technical-preview-2011#bkmk_notify), your Software Center logo would also appear in Windows 10 notifications.

Starting in this release, when you customize Software Center settings, the logo that you specify for Windows 10 notifications is separate from the Software Center logo. The logo for notifications has the following requirements:

- A JPG, PNG, or BMP file
- Square aspect ratio, with minimum dimensions of 90 x 90 pixels and maximum dimensions of 125 x 125 pixels
- A maximum size of 750 KB
- No spaces in the file name

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. Configure the **Software Center** group of client settings. For more information, see [How to configure client settings](../../clients/deploy/configure-client-settings).
2. For Software Center settings, select **Customize**.
3. Select the option to **Select a logo for notifications** and then browse to the image file.
4. Select **OK** to save the client settings. If you're using a custom client settings object, make sure it's deployed to a collection of devices.

Then create a deployment to a device that also has this client setting applied. When the client triggers a notification, you'll see your logo.

### Known issue with Software Center notifications on Windows 11 Insider Preview builds

Current builds of Windows 11 Insider Preview have **Focus assist** turned on by default for *priority only* notifications. Software Center isn't registered as a priority notification provider, so its notifications won't appear on devices running current versions of Windows 11 Insider Preview. To work around this issue, turn off focus assist. For more information, see [Turn Focus assist on or off in Windows](https://support.microsoft.com/windows/turn-focus-assist-on-or-off-in-windows-5492a638-b5a3-1ee0-0c4f-5ae044450e09).

## PowerShell release notes preview

These release notes summarize changes to the Configuration Manager PowerShell cmdlets in this technical preview release.

For more information about PowerShell for Configuration Manager, see [Get started with Configuration Manager cmdlets](/en-us/powershell/sccm/overview).

### New cmdlets

#### Get-CMDeploymentTypeRequirement

Use this cmdlet to get the requirement rules for the specified deployment type. You can use the returned object to add the same rules to another deployment type.

For example, the following sample first gets a deployment type object from **AppA**. It passes that object to the **Get-CMDeploymentTypeRequirement** cmdlet to get its requirement rules. It then uses the **Set-CMScriptDeploymentType** cmdlet to add the same requirement rule to another deployment type on a different application.

```powershell
$dt1 = Get-CMDeploymentType -ApplicationName "AppA" -DeploymentTypeName "dt1"

$rule = $dt1 | Get-CMDeploymentTypeRequirement

Set-CMScriptDeploymentType -ApplicationName "AppB" -DeploymentTypeName "dt2" -AddRequirement $rule
```

#### Get-CMSecurityRolePermission

Use this cmdlet to get the permissions for the specified security role.

This example first gets an object for the built-in security role **Application author** in the variable **$role**. It then passes that object to the **Get-CMSecurityRolePermission** cmdlet, and saves the list of permissions in the **$rolePermission** variable.

```powershell
$roleName = "Application author"
$role = Get-CMSecurityRole -Name $roleName
$rolePermission = $role | Get-CMSecurityRolePermission
```

For more information on security roles and permissions, see [Fundamentals of role-based administration](../../understand/fundamentals-of-role-based-administration).

#### Set-CMSecurityRolePermission

Use this cmdlet to configure a security role with specific permissions.

This example first gets an object for the security role **Contoso custom role** in the variable **$role**. It then creates a hashtable of allowed operations, or permissions, in the **$ops** variable. These permissions include the following operations:

- Create and delete boundaries
- Read applications
- Modify alert subscriptions, including set security scope

The example then uses the **Set-CMSecurityRolePermission** cmdlet to set the specified permissions on the specified security role.

```powershell
$roleName = "Contoso custom role"
$role = Get-CMSecurityRole -Name $roleName

$ops = @{Boundaries="Create,Delete";Application="Read";"Alert Subscription"="Modify,Set Security Scope"}

$role | Set-CMSecurityRolePermission -RolePermission $ops
```

### Modified cmdlets

#### Get-CMPersistentUserSettingsGroup

For more information, see [Get-CMPersistentUserSettingsGroup](/en-us/powershell/module/configurationmanager/Get-CMPersistentUserSettingsGroup).

**Bugs that were fixed**

Fixed an issue with the **Name** parameter to filter on setting groups.

#### Get-CMUserDeviceAffinity

For more information, see [Get-CMUserDeviceAffinity](/en-us/powershell/module/configurationmanager/Get-CMUserDeviceAffinity).

**Non-breaking changes**

Add parameter **ShowApprovedOnly** to filter out non-approved affinities.

#### New-CMRequirementRule\*

This change applies to all cmdlets that start with **New-CMRequirementRule**. For example, [New-CMRequirementRuleExistential](/en-us/powershell/module/configurationmanager/New-CMRequirementRuleExistential).

**Bugs that were fixed**

Fixed a requirement rule name issue with these cmdlets.

#### Set-CMDeviceVariable

For more information, see [Set-CMDeviceVariable](/en-us/powershell/module/configurationmanager/Set-CMDeviceVariable).

**Non-breaking changes**

The parameter **VariableName** is now case-insensitive.

#### Set-CM\*DeploymentType

This change applies to all cmdlets to configure application deployment types. For example, [Set-CMMsiDeploymentType](/en-us/powershell/module/configurationmanager/Set-CMMsiDeploymentType).

**Bugs that were fixed**

Fixed a requirement rule name issue with these cmdlets.

#### Set-CMSoftwareUpdatePointComponent

For more information, see [Set-CMSoftwareUpdatePointComponent](/en-us/powershell/module/configurationmanager/Set-CMSoftwareUpdatePointComponent).

**Breaking changes**

Removed the deprecated parameter **EnableSynchronization** from this cmdlet. To set the synchronization schedule, use the **Schedule** parameter.

For example, to disable the synchronization schedule:

```powershell
Set-CMSoftwareUpdatePointComponent -Name "Contoso-SiteSysSrv.Western.Contoso.com" -Schedule $null
```

## General known issues

### Configuration Manager console won't automatically update

If you update a technical preview site from version 2108 to a later version, the Configuration Manager console fails to update. This problem is because of a known issue in the extension installer.

To work around this issue, manually update the console. After you update the site from version 2108 to a later version, run **ConsoleSetup.exe**. For more information, see [Install the Configuration Manager console](../../servers/deploy/install/install-consoles).