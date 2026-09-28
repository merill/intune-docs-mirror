---
layout: Conceptual
title: Configure Rollout Options for Feature Update Policies - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/windows/configure-rollout-options
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Configure rollout options in feature update policies to control when Windows feature updates become available to devices and deploy updates gradually.
ms.date: 2026-01-14T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: davguy; bryanke
locale: en-us
document_id: 3a0762e2-9664-e00c-b3df-5cf744bd646d
document_version_independent_id: 3a0762e2-9664-e00c-b3df-5cf744bd646d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/windows/configure-rollout-options.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/windows/configure-rollout-options
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/windows/configure-rollout-options.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 8220f3aa-4c79-dbf7-2719-fe18b3282090
---

# Configure Rollout Options for Feature Update Policies - Microsoft Intune | Microsoft Learn

Use rollout options with feature update policies to control when a Windows feature update becomes available to devices. Rollout options help you manage update availability by making an update available immediately, on a specific date, or gradually across groups of devices.

When an update becomes available, devices are eligible to install it the next time they scan Windows Update. The actual installation timing is still influenced by user behavior and settings such as deadlines and restart controls.

You configure rollout options when creating or editing a feature update policy by selecting one of the following availability behaviors.

- **Make update available as soon as possible**: Makes the update available to targeted devices without delay. This option reflects the default Windows Update behavior.
- **Make update available on a specific date**: Delays update availability until the date you specify. Devices don't receive the update offer until that date is reached.
- **Make update available gradually**: Distributes the update offer to targeted devices over time, using offer groups. This option helps reduce network impact and allows early detection of issues.

## Make updates available gradually

The **Make update available gradually** option lets you stage a feature update by making it available to subsets of targeted devices at different times. These subsets are called *offer groups*. Staggering availability across offer groups helps reduce deployment risk and limits the impact on network and support resources compared to offering the update to all devices at once. When you select this option, you define the rollout schedule. Windows Update uses these settings to determine how many offer groups are created, when the update is first offered, and how availability progresses across devices.

### Rollout schedule settings

- **First group availability**: Specifies the date when the update is first offered to devices targeted by the policy. This date must be at least two days in the future. The lead time allows Windows Update to identify targeted devices, calculate the number of offer groups, and assign devices to those groups. If you select a date that's too soon, Intune prompts you to choose the earliest valid date.
- **Final group availability**: Specifies the date when the update is offered to the final offer group. This group includes any devices that haven't already received the update offer. Depending on the number of days between groups, the final offer might occur earlier than this date. Devices assigned to the policy after the final group availability date receive the update offer immediately.
- **Days between groups**: Defines the interval between update offers and determines how many offer groups are created.

Example: If the first group availability is January 1, the final group availability is January 10, and the interval is three days, Windows Update creates four offer groups. The update is offered on January 1, January 4, January 7, and January 10, with approximately the same number of devices in each group. Devices become eligible for the update only when their group receives the offer.

### Offer group behavior

Devices are assigned to offer groups randomly, with groups kept evenly sized and a minimum of 100 devices per group.

If you modify rollout dates or the interval between groups:

- Windows Update recalculates offer groups as needed.
- Devices that haven't yet received an offer can be reassigned, which may change when they receive the update.
- If the final group availability date is set in the past, all remaining devices receive the update offer as soon as possible.
- If the first group availability date is moved to the future, devices that already received the offer keep it, while new devices wait until the revised start date.

If the policy assignment changes:

- Newly added devices are placed into the remaining offer groups.
- Windows Update attempts to retract the update offer from devices that are no longer targeted, unless the device has already begun processing the update.

## Intelligent rollouts

To further optimize gradual deployments, you can use *intelligent rollouts*.

With intelligent rollouts, Windows Autopatch uses data collected from devices to optimize how devices are assigned to offer groups. Instead of assigning devices randomly, Autopatch prioritizes diversity in the first offer group by selecting a small set of devices that represent a broad range of hardware, drivers, and configurations. This first group effectively acts as a *pilot ring* for the deployment.

To enable Intelligent rollouts, deploy a settings catalog device configuration profile and set **Allow Windows Update for Business Cloud Processing**. Assign this profile to the same groups used by your feature update policies.

You only need to deploy this profile once per device. After it's enabled, Intelligent rollouts apply automatically to all future gradual rollouts for that device.

## Enable intelligent rollouts

Here are the steps to enable intelligent rollouts for gradual feature update deployments.

1. [Create a Settings catalog policy](../../device-configuration/settings-catalog/) for the Windows platform and use the following setting:

    | Category | Setting name | Value |
    | --- | --- | --- |
    | **System** | Allow WUfB Cloud Processing | Enabled |
2. Assign the policy to a group that contains as members the devices that you want to configure.

After the profile deploys, devices that use gradual rollouts for feature update policies will also have intelligent optimization applied.

## Likely issue safeguard holds

The **Allow Windows Update for Business Cloud Processing** setting also enables Autopatch to apply *likely issue* safeguard holds. For background information about safeguard holds, see [Safeguard holds in Windows Update for Business reports](/en-us/windows/deployment/update/wufb-reports-workbook).

As a rollout progresses, Autopatch monitors for unexpected issues using signals from the broader Windows ecosystem. When a device is likely to encounter an issue with the update, Autopatch can apply a likely issue safeguard hold to pause the update for that device.

By proactively applying safeguard holds, Autopatch helps protect devices and end users from potential productivity‑impacting issues during feature update deployments. To learn more about managing safeguards programmatically, see Manage safeguards using Windows Autopatch in the Graph API documentation.