---
layout: Conceptual
title: Manage Windows Update Ring Policies - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/windows/manage-update-rings
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Learn about Windows Update ring policies for Windows devices, how to create and manage them, and improve update deployment.
ms.date: 2026-01-12T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: davguy; davidmeb; bryanke
locale: en-us
document_id: 2bc3282d-c7f1-5b31-5647-ee19b821f5aa
document_version_independent_id: 2bc3282d-c7f1-5b31-5647-ee19b821f5aa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/windows/manage-update-rings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/windows/manage-update-rings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/windows/manage-update-rings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: fdda9d22-dd5b-2918-64cb-fd033e6c7922
---

# Manage Windows Update Ring Policies - Microsoft Intune | Microsoft Learn

Windows update rings define how and when Windows updates are installed on devices. They control client‑side update behavior such as deferral periods, restart settings, deadlines, active hours, and user notifications. Update rings apply broadly to Windows updates and are commonly used to create deployment stages—for example, test, pilot, and production—by assigning different settings to different device groups.

In Microsoft Intune, update rings are configured through **update ring policies**, which provide a general policy surface for managing Windows Update behavior on devices. These policies use Windows Update client settings and can be used on their own or alongside other Windows update policies, such as feature updates, quality updates, and driver updates.

Note

When devices are managed through Windows Autopatch, update rings may be created and maintained by the service to implement rollout cadence and restart behavior. In these scenarios, admins typically shouldn't assign custom update rings to Autopatch‑managed devices. Instead, update rings work in combination with service‑managed policies that control update targeting and sequencing.

## Prerequisites

![](../../media/icons/16/network-connectivity.svg)**Network and connectivity requirements**

> 
> Devices must have internet access and be able to reach required Microsoft endpoints:
> 
> - [Intune service endpoints](../../fundamentals/endpoints#access-for-managed-devices)
> - [Windows Update endpoints](/en-us/windows/privacy/manage-windows-1809-endpoints#windows-update)
> - [Windows Autopatch endpoints](/en-us/windows/deployment/windows-autopatch/prepare/windows-autopatch-configure-network)
> 

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - [Microsoft Intune Plan 1](../../fundamentals/licensing)
> 

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> Windows Update ring policies support the following Windows editions:
> 
> - Pro
> - Pro Education
> - Enterprise
> - Education
> - Windows IoT Enterprise
> - Windows Team - for Surface Hub devices
> - Windows Holographic for Business - Supports a suset of settings for Windows updates, including:
>     - **Automatic update behavior**
>     - **Microsoft product updates**
>     - **Servicing channel**: Any update build that is generally available. For more information, see [Manage Windows Holographic](../../solutions/windows-holographic).
> 
> 
> Windows Enterprise LTSC and IoT Enterprise LTSC- LTSC is supported for Quality updates, but not for Feature updates. As a result, the following ring controls aren't supported for LTSC:
> 
> - Pause of feature updates
> - Feature Update Deferral period
> - Set feature update uninstall period
> - Enable pre-release builds
> - Use deadline settings for feature updates
> 

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> The *Microsoft Account Sign-In Assistant* service (`wlidsvc`) must be enabled and running.
> 
> If the Microsoft Account Sign-In Assistant service is disabled, Windows Update doesn't offer feature updates. For more information, see [Feature updates are not being offered while other updates are](/en-us/windows/deployment/update/windows-update-troubleshooting#feature-updates-are-not-being-offered-while-other-updates-are).

## Create and assign update rings

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage updates** &gt; **Windows updates**
2. Select the **Update rings** tab &gt; **Create profile**.
3. Under *Basics*, specify a name, a description (optional), and then select **Next**.
4. Under **Update ring settings**, configure settings aligned with your organization's update deployment strategy

    - For information about the available settings, see [Windows update settings](ref-update-ring-settings).
    - After configuring *Update and User experience* settings, select **Next**.
5. Under **Scope tags**, select **+ Select scope tags** to open the *Select tags* pane if you want to apply them to the update ring. Choose one or more tags, and then click **Select** to add them to the update ring and return to the *Scope tag*s page.
6. Select **Next** to continue to *Assignments*.
7. Under **Assignments**, choose **+ Select groups to include** and then assign the update ring to one or more groups. Use **+ Select groups to exclude** to fine-tune the assignment. Select **Next** to continue.

    Tip

    Assign update rings to device groups. The use of device groups removes the need for a user to sign-on to a device before the policy can apply.
8. Under **Review + create**, review the settings, and then select **Create** when ready to save your Windows update ring. Your new update ring is displayed in the list of update rings.

## Manage update rings

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage updates** &gt; **Windows updates**
2. Select the **Update rings** tab and select the ring policy that you want to manage. Intune displays details similar to the following for the selected policy:

    [![Screen capture of the default view for Update ring policy.](media/shared/update-rings.png)](media/shared/update-rings.png#lightbox)

This view includes:

- **Policy actions**: use the available actions to manage the selected update ring policy. For more information about each action, see the Policy actions section.
- **Essentials**: A list of details about the policy, including when it was created, last modified, and a count of groups that are assigned to the policy.
- **Device and user check-in status**: The default report view for this policy. In addition to this default view, the following report details and options are available:

    - **View report**: A button opens a more detailed report view for *Device and user check-in status*.
    - **Two additional report tiles**: You can select the tiles for the following reports to view additional details:
        - **Device assignment status**: This report shows all the devices that are targeted by the policy, including devices in a pending policy assignment state.
        - **Per setting status**: View the configuration status of each setting for this policy across all devices and users.

    For details about this report view, see [Reports for update ring policies](monitor-update-rings).
- **Properties**: View details for each configuration page of the policy, including an option to **Edit** each area of the policy.

### Policy actions

Select a tab to learn more about its purpose and available options.

# [Delete](#tab/delete)
Select **Delete** to stop enforcing the settings of the selected Windows update ring. Deleting a ring removes its configuration from Intune so that Intune no longer applies and enforces those settings.

Deleting a ring from Intune doesn't modify the settings on devices that were assigned the update ring. Instead, the device keeps its current settings. Devices don't maintain a historical record of what settings they held previously. Devices can also receive settings from other update rings that remain active.

To delete a ring:

1. While viewing the overview page for an Update Ring, select **Delete**.
2. Select **OK**.

# [Pause](#tab/pause)
Select **Pause** to prevent assigned devices from receiving feature or quality updates for up to 35 days from the time you pause the ring. After the maximum days have passed, pause functionality automatically expires and the device scans Windows Updates for applicable updates. Following this scan, you can pause the updates again. If you resume a paused update ring, and then pause that ring again, the pause period resets to 35 days.

To pause a ring:

1. While viewing the overview page for an Update Ring, select **Pause**.
2. Select either **Feature** or **Quality** to pause that type of update, and then select **OK**.
3. After pausing one update type, you can select Pause again to pause the other update type.

When an update type is paused, the Overview pane for that ring displays how many days remain before that update type resumes.

Important

After you issue a pause command, devices receive this command the next time they check into the service. It's possible that before they check in, they might install a scheduled update. Additionally, if a targeted device is turned off when you issue the pause command, when you turn it on, it might download and install scheduled updates before it checks in with Intune.

# [Resume](#tab/resume)
While an update ring is paused, you can select **Resume** to restore feature and quality updates for that ring to active operation. After you resume an update ring, you can pause that ring again.

To resume a ring:

1. While viewing the overview page for a paused Update Ring, select **Resume**.
2. Select from the available options to resume either **Feature** or **Quality** updates, and then select **OK**.
3. After resuming one update type, you can select Resume again to resume the other update type.

# [Extend](#tab/extend)
While an update ring is paused, you can select **Extend** to reset the pause period for both feature and quality updates for that update ring to 35 days.

To Extend the pause period for a ring:

1. While viewing the overview page for a paused Update Ring, select **Extend**.
2. Select from the available options to resume either **Feature** or **Quality** updates, and then select **OK**.
3. After extending the pause for one update type, you can select Extend again to extend the other update type.

# [Uninstall](#tab/uninstall)
An Intune administrator can use **Uninstall** to uninstall (roll back) the latest *feature* update or the latest *quality* update for an active or paused update ring. After uninstalling one type, you can then uninstall the other type. Intune doesn't support or manage the ability of users to uninstall updates.

Important

When you use the *Uninstall* option, Intune passes the uninstall request to devices immediately.

- Windows devices start removal of updates as soon as they receive the change in Intune policy. Update removal isn't limited to maintenance schedules, even when they're configured as part of the update ring.
- If the update removal requires a device restart, the device restarts without offering device users an option to delay.

For Uninstall to be successful:

A device must have installed the latest update. Because updates are cumulative, devices that install the latest update will have the most recent feature and quality update. An example of when you might use this option is to roll back the last update should you discover a breaking issue on your Windows machines.

Consider the following when you use Uninstall:

- Uninstalling a feature or quality update is only available for the servicing channel the device is on.
- Using uninstall for feature or quality updates triggers a policy to restore the previous update on your Windows machines.
- After a quality update is successfully rolled back, device users continue to see the update listed in **Windows settings** &gt; **Updates** &gt; **Update History**.
- When you initiate an uninstall of feature or quality updates on an Update Ring, Intune also pauses updates of the same type on that Update Ring.
- Once the feature or quality update pause elapses on an Update Ring, devices will reinstall previously uninstalled feature or quality updates if they're still applicable.
- Uninstallation will not be successful when the feature update was applied using an Enablement Package. To learn more about Enablement Packages, see [KB5015684](https://support.microsoft.com/topic/kb5015684-featured-update-to-version-22h2-by-using-an-enablement-package-09d43632-f438-47b5-985e-d6fd704eee61).
- For feature updates specifically, the time you can uninstall the update is limited from 2-60 days. This period is configured by the update rings Update setting **Set feature update uninstall period (2 – 60 days)**. You can't roll back a feature update that's been installed on a device after the update has been installed for longer than the configured uninstall period.

    For example, consider an update ring with a feature update uninstall period of 20 days. After 25 days you decide to roll back the latest feature update and use the Uninstall option. Devices that installed the feature update over 20 days ago can't uninstall it as they've removed the necessary bits as part of their maintenance. However, devices that only installed the feature update up to 19 days ago can uninstall the update if they successfully check in to receive the uninstall command before exceeding the 20-day uninstall period.

For more information about Windows Update policies, see [Update CSP](/en-us/windows/client-management/mdm/update-csp) in the Windows client management documentation.

To uninstall the latest Windows update:

1. While viewing the overview page for a paused Update Ring, select **Uninstall**.
2. Select from the available options to uninstall either **Feature** or **Quality** updates, and then select **OK**.
3. After you trigger the uninstall for one update type, you can select Uninstall again to uninstall the remaining update type.

---