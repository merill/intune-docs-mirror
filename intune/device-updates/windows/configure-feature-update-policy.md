---
layout: Conceptual
title: Configure Windows Feature Update Policies - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/windows/configure-feature-update-policy
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Learn about Windows feature update polies and how to manage them in Microsoft Intune.
ms.date: 2026-01-14T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: davidmeb; bryanke; davguy
locale: en-us
document_id: edef0da9-eac6-3fcc-98f2-2b4e9fa09aca
document_version_independent_id: edef0da9-eac6-3fcc-98f2-2b4e9fa09aca
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/windows/configure-feature-update-policy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/windows/configure-feature-update-policy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/windows/configure-feature-update-policy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e9cf46cc-e9d6-e34a-2a77-5fe9fc93039c
---

# Configure Windows Feature Update Policies - Microsoft Intune | Microsoft Learn

Feature update policies in Microsoft Intune specify which Windows version devices are eligible to install and keep that version enforced until the policy is changed or removed. Use these policies to target a specific Windows release or to upgrade devices to a newer version according to your deployment plan.

Feature update policies don't downgrade devices. If a device is already running a newer Windows version than the one targeted, the policy doesn't apply and the device continues running its current version. When a feature update installs, the latest applicable monthly quality update is automatically included as part of the upgrade.

Feature update policies remain in effect until you modify or remove them. This behavior differs from pausing feature updates in update rings, which expires automatically after 35 days.

## Before you begin

- Ensure your environment meets the requirements in [Windows feature updates overview](manage-feature-updates#prerequisites).
- Devices won't install a feature update if the targeted Windows version is blocked by a [*safeguard hold*](/en-us/windows/deployment/update/update-compliance-feature-update-status#safeguard-holds).
    - Safeguard holds are applied when known issues exist. Once the issue is resolved, the hold is removed and the device can update.
    - For details about known issues that can result in safeguard holds, see [Windows 11 release information](/en-us/windows/release-health/windows11-release-information).

## Create and assign feature update policies

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Windows**.
2. Select **Windows updates** &gt; **Feature updates**.
3. Select **Create profile**.
4. Under **Deployment settings**:
    - Specify a **Name** and an optional **Description** for the feature updates deployment.
    - From the **Feature update to deploy** dropdown, select the Windows version you want to deploy. Only versions of Windows that remain in support are available to select.
    - Select either:
        - **Make available to users as a required update**: the device will automatically install the update based on device settings.
        - **Make available to users as an optional update**: selected updates are made available to users as an optional update. The rollout settings still control when the update is available to the device but then the user must choose to install the update before it is installed on the device. This option requires a license for Windows Autopatch.
5. Under **Rollout options**, configure how and when the update is made available to devices that receive this policy. For more information, see [Rollout options for Windows Updates](configure-rollout-options).
6. Select **Next**
7. Under **Assignments**, assign the policy to one or more device groups. Select **Next** to continue.
8. Under **Review + create**, review the settings. When ready to save the policy, select **Create**.

## User experience

The user experience for feature update policies depends on whether the update is offered as **Optional** or **Required**.

When a feature update is available as **Optional**, users must open **Windows Update** in device settings to view the update and choose to install it. Users must select **Download** to begin installation. If no action is taken, the update isn't installed unless an administrator later changes the availability to **Required**.

This experience matches the optional update behavior users see on personal Windows devices. It's recommended that administrators notify users through organizational communication channels when an optional feature update is made available.

### Switching update availability

Changing update availability affects devices differently depending on their installation state.

**If an update is changed from Optional to Required:**

- Devices that have already installed the update aren't affected.
- Devices that haven't started installation install the update automatically during the next Windows Update scan.

**If an update is changed from Required to Optional:**

- Devices that have already completed installation aren't affected.
- Devices that are pending restart typically continue installation as a required update.
- Only devices that haven't started installation, or are early in the installation process, switch to optional behavior.

## How feature update policies are evaluated

When a device is targeted by multiple feature update policies, Windows Update evaluates all applicable policies during update scans and determines which feature update to offer.

Keep the following behavior in mind:

- Each feature update policy can target only one Windows version. If a device is targeted by multiple policies, it can therefore be eligible for multiple feature updates.
- Windows Update offers only one feature update to a device at a time and always selects the **latest applicable version**.
- Windows 11 feature updates are always considered later versions than Windows 10 feature updates. If a Windows 10 device is targeted by both Windows 10 and Windows 11 feature update policies, the Windows 11 update is offered because upgrading from Windows 10 to Windows 11 is a supported upgrade path.

Note

If two policies target the same feature update version for the same device and one policy is configured as **Required** while the other is **Optional**, the update is offered as **Required**.

## Manage Windows feature update policies

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Windows**.
2. Select **Windows updates** &gt; **Feature updates**.

For each profile you can view:

- **Feature Update Version**: The feature update version in the profile.
- **Assigned**: If the profile is assigned to one or more groups.
- **Support**: The status of the feature update:

    - **Supported**: The feature update version is in support and can deploy to devices.
    - **Support Ending** - The feature update version is within two months of its support end date.
    - **Not supported**: Support for the feature update has expired and it no longer deploys to devices.
- **Support End Date**: The end of support date for the feature update version.

Note

The date provided is for the Enterprise and Education editions of Windows. To find the support dates for other editions supported by Windows Autopatch, see the [Microsoft Product Lifecycle site](https://aka.ms/lifecycle).

Selecting a profile from the list opens the profiles **Overview** pane where you can:

- Select **Delete** to delete the policy from Intune and remove it from devices.
- Select **Properties** to modify the deployment. On the *Properties* pane, select **Edit** to open the *Deployment settings or Assignments*, where you can then modify the deployment.

Note

The End user update status Last Scanned Time value will return *Not scanned yet* until a user logs on and Update Session Orchestrator (USO) scan is initiated. For more information on the Unified Update Platform (UUP) architecture and related components, see [Get started with Windows Update](/en-us/windows/deployment/update/windows-update-overview).

## Co-management considerations

If you co-manage devices with Configuration Manager, feature update policies might not immediately take effect on devices when you newly configure the [Windows Update policies workload](../../configmgr/comanage/workloads#windows-update-policies) to Intune. This delay is temporary but can initially result in devices updating to a later feature update version than is configured in the policy.

To prevent this initial delay from impacting your co-managed devices:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Windows**.
2. Select **Windows updates** &gt; **Feature updates**.
3. Select **Create profile**.
4. For **Deployment settings**, enter a name and a description for the policy. Then, specify the feature update you want devices to be running.
5. Complete the policy configuration, including assigning the policy to devices. The policy deploys to devices, though any device that already has the version you've selected, or a newer version, won't be offered the update. Monitor the report for the policy. To do so, go to **Reports** &gt; **Windows Updates** &gt; **Reports** tab &gt; **Feature Updates report**. Select the policy you created and then generate the report.
6. Devices that have a state of *OfferReady* or later, are enrolled for feature updates and protected from updating to anything newer than the update you specified in step 3. See [Use the Windows feature updates (Organizational) report](monitor-feature-updates#accessing-feature-updates-reports).
7. With devices enrolled for updates and protected, you can safely change the *Windows Update policies* workload from Configuration Manager to Intune. See, [Switch workloads to Intune](/en-us/configmgr/comanage/how-to-switch-workloads) in the co-management documentation.

## Move from update ring deferrals to feature update policies

When managing feature updates in Intune, you can control Windows version availability using either update ring deferrals or feature update policies. If you use feature update policies, Microsoft recommends that you stop using feature update deferrals in update ring policies.

Combining feature update deferrals with feature update policies adds unnecessary complexity and can delay or block feature updates. While update rings can continue to manage user experience settings—such as restart behavior and notifications—feature update policies should be the primary mechanism for controlling which Windows versions devices can install.

When both policy types apply to a device, Windows Update evaluates the conditions of each policy. If feature update deferrals remain configured, this evaluation can result in unintended blocking or delayed offering of feature updates.

### Plan the transition

Plan the transition from update ring deferrals to feature update policies to ensure Windows Update offers the updates you intend.

When Intune Windows update policies are created or modified, policy details are sent to the Windows Update service, which evaluates update applicability for each device. This evaluation typically completes within 10 minutes, but in some cases can take longer.

If a device scans for updates after a deferral is removed but before Windows Update finishes processing the feature update policy, the device might be offered a feature update you didn't intend to deploy.

### Switch to feature update policies

Use the following process to ensure Windows Update processes the feature update policy before feature update deferrals are removed:

1. In the Microsoft Intune admin center, create a feature update policy that targets the desired Windows version and assign it to the appropriate devices. After the policy is assigned, allow several minutes for Windows Update to process the policy.
2. Review the [Windows feature updates (Organizational)](monitor-feature-updates#accessing-feature-updates-reports) report and verify that targeted devices show a state of **OfferReady**. This state indicates that Windows Update has completed policy processing.
3. After all targeted devices report **OfferReady**, update the applicable [update ring policy](manage-update-rings) and set **Feature update deferral period (days)** to **0**.