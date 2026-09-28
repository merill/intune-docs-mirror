---
layout: Conceptual
title: Configure Update Policies for Apple Devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-updates/apple/
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Learn how to configure software update policies for Apple devices using Apple's Declarative Device Management (DDM) model. Improve security, reduce user disruption, and ensure compliance with reliable, automated updates across your organization.
ms.date: 2026-02-24T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: beflamm
locale: en-us
document_id: 1af334a6-16d9-206f-8332-d5b291c178b2
document_version_independent_id: 1af334a6-16d9-206f-8332-d5b291c178b2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-updates/apple/index.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-updates/apple/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-updates/apple/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 52a66b6e-b8eb-c97c-8207-1179a0104660
---

# Configure Update Policies for Apple Devices - Microsoft Intune | Microsoft Learn

Keeping devices updated is critical for enterprise security, performance, and compliance. Updates deliver essential patches, bug fixes, and new features. Without a consistent strategy, organizations risk exposing endpoints to vulnerabilities and compatibility issues.

With Microsoft Intune, IT admins can configure and enforce update policies for Apple devices, including the ability to:

- Target a specific OS version or enforce the latest version
- Set enforcement deadlines
- Minimize user disruption

This article shows how to configure update policies in Intune using Apple's Declarative Device Management (DDM) model—a more reliable and autonomous approach than traditional MDM-based policies, which are now deprecated.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> The configuration of Software Update for Apple devices requires the following platforms:
> 
> - iOS/iPadOS 17.0 and later
> - macOS 14.0 and later
> 

![](../../media/icons/16/enrollment.svg)**Enrollment methods**

> 
> The following enrollment methods are supported:
> 
> - Device Enrollment
> - Automated Device Enrollment
> 

## Configuration

When designing your Apple device update strategy, align with your organization's security policies, user experience expectations, and compliance mandates. Intune supports two primary policy models for managing software updates:

- **Latest version policy**: automatically installs the latest eligible OS version after a defined deferral period. With this model:

    - You configure a deferral period (in days) and an installation time.
    - Devices autonomously install the update within the declared deadline—no manual triggers required.

    This model is ideal for organizations that prioritize rapid patching, regulatory compliance, and minimal IT overhead.
- **Targeted version policy**: offers granular control over which OS version is installed and when. With this model:

    - You specify the required OS version and set a precise installation deadline.
    - A help URL can be provided for user assistance.
    - Devices enforce compliance independently, without manual enforcement.

    This model is best suited for environments with strict app compatibility requirements, phased deployment strategies, or formal change management workflows.

# [Latest version](#tab/automatic-updates)
1. [Create a settings catalog policy](../../device-configuration/settings-catalog/) for the iOS/iPadOS or macOS platform and use the following settings:

    | Category | Setting name and value |
    | --- | --- |
    | **Declarative Device Management** &gt; **Software Update Enforce Latest** | **Delay in Days** Specify the number of days that should pass before a deadline is enforced. This delay is based on either the posting date of the new update when released by Apple, or when the policy is configured. The delay only determines the target enforcement date and not the date that the update is offered to users. |
    | **Declarative Device Management** &gt; **Software Update Enforce Latest** | **Install Time** Specify the local device time for when updates are enforced. The Install Time setting is configured using the 24-hour clock format where midnight is `00:00` and 11:59pm is `23:59`. Ensure that you include the leading 0 on single digit hours. For example, `01:00`, `02:00`, `03:00`. |
2. [Assign the policy](../../device-configuration/assign-device-profile) to a group to target users or devices.

# [Targeted version](#tab/manual-updates)
1. [Create a settings catalog policy](../../device-configuration/settings-catalog/) for the iOS/iPadOS or macOS platform and use the following settings:

    | Category | Setting name and value |
    | --- | --- |
    | **Declarative Device Management** &gt; **Software Update** | **Details URL** Enter a web page URL that has more information on the update. Typically, this URL is a web page hosted by your organization that users can select if they need organization-specific help with the update. |
    | **Declarative Device Management** &gt; **Software Update** | **Target Build Version** Enter the target build version to update the device to, like `25A354`. The build version can include a supplemental version identifier, like `25A354a`.If the build version you enter isn't consistent with the **Target OS Version** value you enter, then the **Target OS Version** value takes precedence. |
    | **Declarative Device Management** &gt; **Software Update** | **Target Date Time** Select or manually enter the date and the time that specifies when to force the installation of the software update.The **Target Date Time** setting schedules the update using the local timezone of the device. For example, an admin configures an update to install at 2PM. The policy schedules the update to happen at 2PM in the local timezone of devices that receive the policy.If the user doesn't trigger the software update before this time, then a one-minute countdown prompt is shown to the user. When the countdown ends, the device force installs the update and forces a restart.If the device is powered off when the deadline is met, when the device powers back on, there's a one hour grace period. When the grace period ends, the device force installs the update and forces a restart. |
    | **Declarative Device Management** &gt; **Software Update** | **Target OS Version** Select or manually enter the target OS version to update the device to. This value is the OS version number, like `26.0`. You can also include a supplemental version identifier, like `26.0.1`. |
2. [Assign the policy](../../device-configuration/assign-device-profile) to a group to target users or devices.

---

Note

When an update enforcement is assigned, the device ignores software update settings, including automatic update actions. The update may install before the deadline if the device is idle.

For more information about configuring Software Update policies and the available settings, see [Software Update](../../device-configuration/settings-catalog/ref-apple-settings#software-update).

## Software Update Settings

When you configure software updates, you might want to manage aspects of the software update process leading up to the enforcement of an update. Using Software Update Settings policies, you can configure various settings that control how users can interact with software updates on their devices. These settings include the ability to:

- Require that an admin or standard user can perform updates on the device.
- Control how users can manually interact with software update settings like automatic download and install or the behavior of Rapid Security Responses.
- Hide updates from users for a specified time period.
- Suppress update notifications up to one hour before the enforcement deadline.
- Control whether users are allowed to update to the latest major update, latest minor update, or are offered both.

For more information about configuring Software Update Settings policies and the available settings, see [Software Update Settings](../../device-configuration/settings-catalog/ref-apple-settings#software-update-settings).

## Monitor policy settings deployment

Software update policy settings use the same reporting as other device configuration policies. For more information, see [Monitor device configuration policies](../../device-configuration/monitor-device-profile).

A policy that reports *Success* only means that the configuration policy successfully installed on the device. Monitor the OS version of targeted devices to ensure that they update. After devices have updated to a later OS version than configured in the policy, the policy reports an error as the device sees this task as an attempt to downgrade. It's recommended to remove the older OS version policy from devices in this state.

To monitor the update status of your Apple devices, see [View Software Update Reports for Apple Devices](monitor-reports).