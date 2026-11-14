---
layout: Conceptual
title: Configure maintenance windows for Windows updates in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/maintenance-windows
author: iceorbital
ms.author: maholdaa
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
ms.subservice: protect
description: Create maintenance window policies in Microsoft Intune to control when automatic Windows update downloads, installations, and restarts begin.
ms.date: 2026-11-05T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: abce2a56-1768-460e-d355-a50390bef02c
document_version_independent_id: abce2a56-1768-460e-d355-a50390bef02c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/maintenance-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/maintenance-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/maintenance-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: dce417cb-e88e-49cb-4a44-211f958ff835
---

# Configure maintenance windows for Windows updates in Microsoft Intune - Microsoft Intune | Microsoft Learn

Use maintenance windows in Microsoft Intune to control when automatic Windows Update actions can begin on managed devices. You can restrict downloads, installations, and update-related restarts to a scheduled period.

Maintenance windows help you plan updates for devices that need to remain available during operating hours, such as kiosks, shared devices, and manufacturing equipment. Configure a one-time window or a recurring daily, weekly, or monthly schedule.

Maintenance windows govern Windows Update content, including quality updates, feature updates, Hotpatch updates, .NET updates, drivers, and firmware. They don't determine which updates are approved or offered to a device.

## Before you begin

Before you create a policy:

- Confirm that devices are enrolled in Intune and run a supported Windows version. The underlying maintenance window settings require Windows 11, version 24H2 with KB5077181, build 26100.7840, or later.
- Confirm that you have Intune permissions to create, configure, and assign device configuration policies.
- Identify a device group for your initial deployment. Test the policy on representative devices before assigning it more broadly.
- Review the update policies assigned to those devices, including deferrals, deadlines, grace periods, and expedited updates.

For the underlying Windows settings and operating system requirements, see [Update Policy CSP](/en-us/windows/client-management/mdm/policy-csp-update).

## How maintenance windows work

A maintenance window controls when the automatic update actions you select can begin. Actions that aren't selected continue to follow other applicable Windows Update policies.

| Update action | Actions restricted to the maintenance window | Actions that can occur outside the window |
| --- | --- | --- |
| Download, install and restart | Download, installation, and update-related restart | None of these automatic actions, except where another policy or event takes priority |
| Install and restart | Installation and update-related restart | Download |
| Restart only | Update-related restart | Download and installation |

All maintenance window times use the device's local time. For example, a window that starts at 23:00 starts at 11:00 PM in each device's local time zone.

An action that begins during the window can continue after the window ends. A maintenance window doesn't guarantee that all update work finishes before the end of the scheduled period.

Maintenance windows control automatic update actions. Users can still initiate update actions outside the window when the Windows experience and other applicable policies allow them.

## Create a maintenance window policy

### 1. Create the policy

1. Sign in to the Microsoft Intune admin center.
2. Select **Devices** &gt; **Manage devices** &gt; **Maintenance windows**.
3. Select **Create policy**.
4. On **Basics**, enter a descriptive **Name** and an optional **Description**.
5. Select **Next**.

For example, use the name **Weekly kiosk maintenance** and describe the devices and approved maintenance period.

### 2. Choose the update actions

On **Configuration settings**, expand **Maintenance Windows** and configure these settings:

1. For **Workload type**, select **Updates**.
2. Set **Enable Maintenance windows** to **On**.
3. For **Update action**, select one of the following options:
    - **Download, install and restart**
    - **Install and restart**
    - **Restart only**

Choose the option that matches the activities you need to restrict. For example, select **Install and restart** if devices can download updates during operating hours but must wait until the maintenance period to install them and restart.

### 3. Configure the schedule

Configure the schedule settings in the order shown in the admin center:

1. **Repeat schedule**
2. Schedule-specific options, when applicable
3. **Start date**
4. **Duration (hours)**
5. **Start time**

Enter the start date in `YYYY-MM-DD` format and the start time in `HH:MM` format. The duration must be from 2 through 24 hours.

The admin center requires a start date. Windows uses that date for a non-repeating window. For recurring windows, Windows starts on the earliest date that matches the configured schedule.

#### One-time window

To configure a single maintenance period:

1. Set **Repeat schedule** to **None**.
2. Enter the **Start date**.
3. Enter the **Duration (hours)**.
4. Enter the **Start time** in device-local time.

Keep one-time schedules current. After the scheduled period passes, update the date or remove the one-time configuration as appropriate.

#### Daily window

To configure a maintenance period every day:

1. Set **Repeat schedule** to **Daily**.
2. Complete **Start date**.
3. Enter the **Duration (hours)** and **Start time**.

No weekday or monthly selections are required.

#### Weekly window

To configure a maintenance period on selected days:

1. Set **Repeat schedule** to **Weekly**.
2. Under **Weekly – Day selection**, select one or more days.
3. Complete **Start date**.
4. Enter the **Duration (hours)** and **Start time**.

The window occurs on each selected day.

#### Monthly window

Set **Repeat schedule** to **Monthly**, and then configure **Monthly – Schedule type**.

For a day-based schedule:

1. Select **Day-based**.
2. Set **Day of month** to a value from 1 through 28.
3. Complete **Start date**, **Duration (hours)**, and **Start time**.

For a week-based schedule:

1. Select **Week-based**.
2. Choose **Week in Month**: **First**, **Second**, **Third**, **Fourth**, or **Last**.
3. Choose **Day of the week**.
4. Complete **Start date**, **Duration (hours)**, and **Start time**.

For example, a week-based schedule can run on the second Tuesday or last Sunday of each month.

After you configure the schedule, select **Next**.

### 4. Assign and create the policy

1. On **Scope tags**, add the scope tags your organization uses to control administrative access, and then select **Next**.
2. On **Assignments**, select the groups that receive the policy. Add exclusions if needed, and then select **Next**.
3. On **Review + create**, review the update action, schedule, scope tags, and assignments.
4. Select **Create**.

## Example: Weekly overnight maintenance

An organization allows kiosks to download updates during operating hours but wants installation and update-related restarts to begin during an overnight maintenance period.

Configure the policy as follows:

| Setting | Value |
| --- | --- |
| Workload type | Updates |
| Enable Maintenance windows | On |
| Update action | Install and restart |
| Repeat schedule | Weekly |
| Weekly – Day selection | Sunday |
| Duration (hours) | 4 |
| Start time | 23:00 |

Complete the required **Start date** field. For this recurring schedule, Windows uses the selected weekday and start time rather than the start date to determine the next window.

The window starts every Sunday at 11:00 PM in each device's local time and ends Monday at 3:00 AM. Downloads can occur outside the window. Installation or restart work that begins during the window can continue after it ends.

## Monitor the policy and validate update behavior

To review policy deployment:

1. Select **Devices** &gt; **Manage devices** &gt; **Maintenance windows**.
2. Select the policy.
3. Review **Device and user check-in status**, **Device assignment status**, and **Per setting status**.
4. Investigate errors, conflicts, and devices that haven't received the policy.

Per-setting reports can show the underlying Windows policy settings separately. For example, a weekly schedule can appear as separate settings for individual days of the week.

Policy deployment status shows whether the configuration reached the device. It doesn't, by itself, confirm that an update installed or a restart occurred during the window.

Use your existing Windows Update or Windows Autopatch reporting to validate update behavior. Compare installation and restart timestamps with the configured schedule, accounting for each device's local time zone.

## Interactions with other update policies

Maintenance windows work alongside other Windows Update policies. Review these interactions when you plan a deployment.

### Policies and events that can take priority

The following policies or events can allow update actions outside the maintenance window:

| Policy or event | Effect |
| --- | --- |
| Expedited quality updates | An expedited deployment can take priority over the maintenance window. |
| Expired deadlines and grace periods | Windows can enforce the update and required restart outside the window after the applicable deadline and grace period expire. |
| Device provisioning | Required update or setup actions during provisioning can take priority over maintenance window restrictions. |
| Education cart servicing policy | This specialized servicing policy can take priority when configured. |
| Minor-impact updates | Updates classified by Windows as minor impact can occur outside the window. |

### Deferrals affect update availability

Deferrals control when an update is offered to a device. They don't create an alternative maintenance window.

If an update is still deferred when a window occurs, it isn't available for that window. After the deferral expires and the update is offered, the selected automatic actions can begin during a subsequent applicable window.

For example, a device with a seven-day quality update deferral and a Saturday maintenance window might not process a Tuesday release during the first Saturday window.

### Other scheduling settings

For actions governed by a maintenance window, active hours and other update scheduling settings don't provide an alternative period for those actions to begin.

Review the complete update configuration rather than treating the maintenance window as a replacement for update approval, availability, or deadline policies.

## Troubleshoot unexpected behavior

### Update activity occurs outside the window

Check whether:

- The activity is included in **Update action**. For example, **Restart only** doesn't restrict downloads or installations.
- The action began during the window and continued after it ended.
- A user initiated the action.
- An expedited update, expired deadline, or another higher-priority event applied.
- You compared the event time with the device's local time.

### An update doesn't install or the device doesn't restart

Check whether:

- The policy successfully reached the device.
- An applicable update is available and is no longer deferred.
- A restart is required.
- The device is powered on and available.
- Required download and installation work has completed.
- The schedule matches the device's local time.
- A one-time window has already passed.
- The window provides enough time for the selected actions.

### A recurring window doesn't run when expected

Check the recurrence and schedule-specific settings:

- For a weekly schedule, select at least one day.
- For a monthly day-based schedule, use a day from 1 through 28.
- For a monthly week-based schedule, configure both the week and weekday.
- Confirm that the device received the policy and uses the expected local date and time.