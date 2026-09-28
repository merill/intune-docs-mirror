---
layout: Conceptual
title: Automatically Hide Devices With Cleanup Rules - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/governance/configure-cleanup-rules
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
description: Intune's device cleanup rules offer a simple, automated way to ensure that only actively managed devices remain visible in the admin center. Learn more about device cleanup rules and how to configure them.
ms.date: 2025-10-08T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: acabello
locale: en-us
document_id: b1cf93b7-3319-f128-30ff-42da529e9d66
document_version_independent_id: b1cf93b7-3319-f128-30ff-42da529e9d66
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/governance/configure-cleanup-rules.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: governance/configure-cleanup-rules
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/governance/configure-cleanup-rules.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: ddfc8099-e1e0-1d9c-5bd1-a0c1f9e75fce
---

# Automatically Hide Devices With Cleanup Rules - Microsoft Intune | Microsoft Learn

Managing a dynamic device fleet means constantly tracking devices that come and go—due to upgrades, user turnover, or inactivity. Intune's device cleanup rules help keep the admin center clean by automatically hiding stale records.

Device cleanup rules in Intune run on a schedule and automatically hide records of devices that didn't check in for a specified period (for example, 90 days). These rules:

- Hide devices from the Intune portal and reports.
- **Don't trigger any actions on the device (no wipe or retire).**
- Allow cleaned-up devices to reappear if they check in before their device certificate expires.
- Require re-enrollment after the certificate expires.
- Aren't available for Jamf-managed devices.

## Prerequisites

![](../media/icons/16/rbac.svg)**Roles requirements**

> 
> To configure device cleanup rules, use an account with at least one of the following roles:
> 
> - [Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)
> - [Custom role](/en-us/intune/fundamentals/role-based-access-control/create-custom-role)that includes:
>     - The permission **Managed Device Cleanup Rules/Update**
>     - The permission **Managed Device Cleanup Settings/Update**
>     - Permissions that provide visibility into and access to managed devices in Intune (for example, Organization/Read, Managed devices/Read)
> 

## How to create a device cleanup rule

1. In the [Microsoft Intune admin center], select [**Devices**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/overview).
2. Under **Organize devices**, select [**Device cleanup rules**](https://go.microsoft.com/fwlink/?linkid=2109431#view/Microsoft_Intune_DeviceSettings/DevicesMenu/%7E/deviceCleanUp).
3. Select **Create**.
4. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the rule.
    - **Description**: Enter a description for the rule. This setting is optional.
    - **Platform**: Select the platform that the rule applies to. The options are:
        - All platforms
        - Android (AOSP)
        - Android (fully managed/dedicated/corporate-owned work profile)
        - Android (device administrator)
        - Android (personally-owned work profile)
        - ChromeOS
        - iOS/iPadOS
        - macOS
        - Windows
        - Windows Holographic
        - visionOS
        - tvOS

    You can create one rule per platform. The rule applies to all devices in your organization with the platform you select.

Important

If both platform-specific and *All platforms* rules exist, the one with fewer days will be applied.

1. Select **Next**.
2. In **Rule settings** &gt; **Remove devices that haven't checked in for this many days**, enter a number between 30 and 270.

    This setting determines how many days a device must check in with the Intune service before the device is considered stale or inactive. If a device doesn't check in before the period ends, the device is cleaned up.

    Tip

    Select **Preview affected devices** to get a list of devices that didn't check in during the specified number of days.
3. Select **Next**.
4. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the rule applies.

Note

Devices hidden from Intune aren't removed from Microsoft Entra ID. For more information about removing devices from Microsoft Entra ID, see [Manage stale devices in Microsoft Entra ID](/en-us/entra/identity/devices/manage-stale-devices).

## Device cleanup rules logging

Intune audit logs show the devices hidden by the device cleanup rules. In the logs, filter by **Activity name** &gt; **Device set to be hidden from admin by Device Cleanup Rule [*Your Rule Name*]**.

For more information, see [Monitor audit logs in Intune](monitor-audit-logs).