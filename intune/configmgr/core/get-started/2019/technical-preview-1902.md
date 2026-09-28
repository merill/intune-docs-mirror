---
layout: Conceptual
title: Technical preview 1902 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2019/technical-preview-1902
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
description: Learn about new features available in the Configuration Manager technical preview branch version 1902.
ms.date: 2019-02-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: cb90c2cc-5be3-404b-9501-c3b8bb70e6c3
document_version_independent_id: ff2f7256-7e8d-88dd-4aea-ad1b71338e16
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2019/technical-preview-1902.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2019/technical-preview-1902
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2019/technical-preview-1902.md
platformId: 342e9c59-b6bb-9e96-6a29-0e5274eb0bfb
---

# Technical preview 1902 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 1902. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

**The following sections describe the new features to try out in this version:**

## Replace toast notifications with dialog window

Sometimes users don't see the Windows toast notification about a restart or required deployment. Then they don't see the experience to snooze the reminder. This behavior can lead to a poor user experience when the client reaches a deadline.

Now when deployments need a restart or software changes are required, you have the option of using a more intrusive dialog window.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

#### Software changes are required

1. Deploy an [application](../../../apps/deploy-use/deploy-applications) as required with a deadline in the future.
2. On the **User Experience** page of the Deploy Software Wizard, select the user notification option to **Display in Software Center and show all notifications**. Then select the following option: **When software changes are required, show a dialog window to the user instead of a toast notification**.
3. Complete the Deploy Software Wizard.

Configuring this deployment setting changes the user experience for this scenario.

From the following toast notification:

![Toast notification that Software changes are required](media/3555947-required-toast.png)

To the following dialog window:

![Dialog window for Required software changes](media/3555947-required-dialog.png)

#### Restart required

1. Edit client settings. For more information, see [How to configure client settings](../../clients/deploy/configure-client-settings).
2. In the **Computer Restart** group, enable the following option: **When a deployment requires a restart, show a dialog window to the user instead of a toast notification**.
3. Create a required deployment for an [application](../../../apps/deploy-use/deploy-applications), [task sequence](../../../osd/deploy-use/deploy-a-task-sequence), or [software update](../../../sum/deploy-use/deploy-software-updates) that requires a restart.

Configuring this client setting changes the user experience for all deployments in this scenario.

From the following toast notification:

![Toast notification that Restart required](media/3555947-restart-toast.png)

To the following dialog window:

![Dialog window to Restart your computer](media/3555947-restart-dialog.png)

## Progress status during in-place upgrade task sequence

You now see a more detailed progress bar during a Windows 10 in-place upgrade task sequence. This bar shows the progress of Windows setup, which is otherwise silent during the task sequence. Users now have some visibility into the underlying progress. It helps with concerns that the upgrade process is suspended due to a lack of progress indication.

![Example task sequence progress with Windows upgrade progress](media/3747129-installation-progress.png)

## Redirect Windows known folders to OneDrive

Use Configuration Manager to move Windows known folders to OneDrive for Business. These folders include Desktop, Documents, and Pictures. To simplify your Windows 10 upgrades, deploy these settings to Windows 7 clients before deploying a task sequence.

For more information on this feature of OneDrive for Business, see [Redirect and move Windows known folders to OneDrive](/en-us/onedrive/redirect-known-folders).

### Prerequisites

- [Find your Microsoft 365 tenant ID](/en-us/onedrive/find-your-office-365-tenant-id)
- Deploy the OneDrive sync client version 18.111.0603.0004 or later. For more information, see [Deploy OneDrive apps by using Configuration Manager](/en-us/onedrive/deploy-on-windows).

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, expand **Compliance Settings**, and select the **OneDrive for Business Profiles** node.
2. In the ribbon, select **Create OneDrive for Business Profile**.
3. Specify a name to identify this policy, and select **Next**.
4. On the **Settings** page:

    1. Specify your Microsoft 365 tenant ID.
    2. Select one of the following options to move the known folders to OneDrive:

        - **Prompt users to move Windows known folders to OneDrive**: With this option, the user sees a wizard to move their files. If they choose to postpone or decline moving their folders, OneDrive periodically reminds them.
        - **Silently move Windows known folders to OneDrive**: When this policy applies to the device, the OneDrive client automatically redirects the known folders to OneDrive for Business.

            - **Show notification to users after folders have been redirected**: If you enable this option, the OneDrive client notifies the user after it moves their folders.
    3. **Prevent users from redirecting their Windows known folders back to their PC**: Disables the option in OneDrive for Business on the client for users to move these folders back to the device.
5. Complete the wizard, then deploy the policy.

### Known issue

After you create a OneDrive for Business profile, the Configuration Manager console unexpectedly closes. The wizard successfully created the profile. The same behavior occurs when viewing a policy in the OneDrive for Business Profiles node.

#### Workaround

To manage these profiles, use the following PowerShell cmdlets:

```PowerShell
# View all OneDrive for Business profiles
Get-CMConfigurationPolicy -Fast | Where-Object { $_.CategoryInstance_UniqueIDs -eq "SettingsAndPolicy:SMS_OneDriveKnownFolderMigrationSettings" }

# Deploy a profile
# Use the LocalizedDisplayName property value of the policy as the CommonProfileName parameter.
New-CMConfigurationPolicyDeployment -CommonProfileName "my ODfB profile" -CollectionName "my collection"

# Delete a profile
Remove-CMConfigurationPolicy -Name "my ODfB profile"
```

For more information, see the following articles:

- [Get-CMConfigurationPolicy](/en-us/powershell/module/configurationmanager/get-cmconfigurationpolicy)
- [New-CMConfigurationPolicyDeployment](/en-us/powershell/module/ConfigurationManager/New-CMConfigurationPolicyDeployment)
- [Remove-CMConfigurationPolicy](/en-us/powershell/module/configurationmanager/remove-cmconfigurationpolicy)

## View first screen only during remote control

When connecting to a client with two or more monitors, it can be difficult to view them all in the Configuration Manager remote control viewer. Based on your feedback, a remote tools operator can now choose between seeing **All screens** or the **First screen** only.

The *first screen* is at the top and far left as shown in Windows display settings. You can't select a specific screen. When you switch the configuration of the viewer, reconnect the remote session. The viewer saves your preference for future connections.

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

1. [Start a remote control session](../../clients/manage/remote-control/remotely-administer-a-windows-client-computer).
2. In the Configuration Manager Remote Control viewer, go to the **View** menu, select **Display**, and then switch from **All Screens** to **First Screen**.

## Edit or copy PowerShell scripts

You can now **Edit** or **Copy** an existing PowerShell script used with the [Run Scripts](../../../apps/deploy-use/create-deploy-scripts) feature. Instead of recreating a script that you need to change, now directly edit it. Both actions use the same wizard experience as when you create a new script. When you edit or copy a script, Configuration Manager doesn't persist the approval state.

Tip

Don't edit a script that's actively running on clients. They won't finish running the original script, and you may not get the intended results from these clients.

## Add cloud management gateway to boundary groups

You can now associate a cloud management gateway (CMG) with a boundary group. This configuration allows clients to default or fallback to the CMG for client communication according to boundary group relationships. This behavior is especially useful in branch office and VPN scenarios. You can direct client traffic away from expensive and slow WAN links to instead use faster services in Microsoft Azure.

### Prerequisites

- [Configure boundary groups](../../servers/deploy/configure/boundary-groups)
- [Set up a CMG](../../clients/manage/cmg/setup-cloud-management-gateway)

### Try it out!

Try to complete the tasks. Then send [Feedback](../../understand/product-feedback) with your thoughts on the feature.

When you [create or configure a boundary group](../../servers/deploy/configure/boundary-group-procedures), on the **References** tab, add a cloud management gateway. This action associates the CMG with this boundary group.

## Configure default views in Software Center

This version of Configuration Manager further iterates on how you can customize Software Center:

- Set the default layout of applications, either as tiles or a list

    - If a user changes this configuration, Software Center persists the user's preference in the future
- Configure the default application filter, either all or only required apps

    - Software Center always uses your default setting. Users can change this filter, but Software Center doesn't persist their preference.

Specify these settings in client settings. Choose the **Software Center** group, and then select **Customize**. To configure the visibility of tabs, go to the **Tabs** tab. To configure the Software Center defaults, go to the **Defaults** tab.

For more information, see [About client settings](../../clients/deploy/about-client-settings#software-center).

## Improvements to the client health dashboard

Based on your feedback, this version includes the following improvements to the [client health dashboard](technical-preview-1901#bkmk_health):

- Improved and streamlined layout
- Improved drill-through from tiles to actionable device lists
- Changes to increase performance for large environments and collections

Tip

By default, the client health dashboard shows online clients, and clients active in the past three days. Therefore, you may see different numbers in this dashboard than in other historical sources of client health. For example, other nodes under Client Status, or reports in the client status category.