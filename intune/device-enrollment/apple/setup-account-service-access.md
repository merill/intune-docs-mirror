---
layout: Conceptual
title: Configure Apple account service access - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-account-service-access
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- highpri
ms.reviewer: beflamm
ms.subservice: enrollment
description: Use Apple access management settings to control how Apple accounts are used on organization‑owned devices managed by Microsoft Intune.
ms.date: 2026-06-01T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 8a5a8a00-06cf-51e0-3d27-baecac577bce
document_version_independent_id: 8a5a8a00-06cf-51e0-3d27-baecac577bce
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/setup-account-service-access.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/setup-account-service-access
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/setup-account-service-access.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/837687b0-8846-4eb2-adb6-2b853e8c70c4
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c797fa2-4419-46e7-a4e3-4c97d0a1f2a0
platformId: cbac20c8-1acf-180e-3c92-19ec064c9818
---

# Configure Apple account service access - Microsoft Intune | Microsoft Learn

You can use Apple access management settings in Apple Business or Apple School Manager to control how Apple accounts are used on organization-owned devices. These settings define which devices users can sign in to with Apple accounts and which Apple apps and services are available.

## Prerequisites

To configure service access for Apple accounts, ensure your environment meets the following prerequisites:

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> Configurations apply to the following platforms:
> 
> - iOS/iPadOS
> - macOS
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> You must have sufficient permissions in Apple Business or Apple School Manager to manage Apple account service access. For current role requirements, see [Customize user access to apps and services using Apple Business](https://support.apple.com/guide/apple-business-manager/customize-user-access-to-apps-and-services-axm53xk34bq/web) (opens Apple support site).

![](../../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> Devices must meet the following requirements:
> 
> - Owned by the organization in Apple Business.
> - Enrolled in Microsoft Intune through automated device enrollment (ADE).
> - Run a supported operating system version:
>     - iOS/iPadOS 17 or later
>     - macOS 14 or later
> 

Important

These settings apply to all Apple accounts regardless of whether a sign in is actively happening. If the setting is changed and the device doesn't meet the requirement, the account is automatically signed out.

## Configure service access

Service access settings are configured in Apple Business or Apple School Manager. Microsoft Intune doesn't configure these settings directly. Instead, Intune issues a management token that Apple uses during device activation to confirm the device's Intune assignment.

### Available settings

In Apple Business or Apple School Manager, you can configure settings that control:

- Which devices users can sign in to with Apple accounts, such as:
    - Any device
    - Managed devices only
    - Supervised devices only
- Whether users can sign in to organization-owned devices using:
    - Managed Apple accounts only
    - Any Apple account
- Which Apple apps and services are available to users, such as:
    - iCloud services
    - Collaboration and communication services

Note

For devices enrolled through automated device enrollment (ADE), the **Managed devices only** and **Supervised devices only** options behave the same. ADE devices are both managed and supervised by default.

These controls apply to organization-owned devices and are defined by Apple as part of their access management model. They aren't supported with bring-your-own-device scenarios. For detailed instructions and descriptions of available settings, see [Service access with Managed Apple Accounts](https://support.apple.com/guide/apple-business-manager/service-access-with-managed-apple-accounts-axm171b3ee95/web) (opens Apple support site).

### How service access enforcement works

Service access for Apple accounts is defined and enforced across Apple and Microsoft Intune as follows:

1. An administrator configures service access settings for Managed Apple Accounts in Apple Business or Apple School Manager. These settings define which devices users can sign in to and which Apple apps and services are available.
2. Devices are enrolled in Microsoft Intune through automated device enrollment.
3. When a user signs in with a managed Apple account on an enrolled device, Apple validates whether the device meets the configured service access requirements.
4. Microsoft Intune enforces the service access requirements on enrolled devices during device check-in and Apple account sign-in.
5. If a device no longer meets the configured requirements, Apple automatically signs the user out of affected Apple services.

These controls help ensure that managed Apple accounts are used only on devices that meet your organization's access requirements.

If a user is having trouble signing in to a device with their personal Apple account, see [Apple support](https://support.apple.com/en-us/122725) (opens Apple Support site).

### What it doesn't do

Configuring service access for Apple accounts doesn't change how devices enroll in Microsoft Intune. Specifically, this configuration-

- Doesn't configure enrollment settings in the Intune admin center. Service access is configured in Apple Business or Apple School Manager, not in Intune.
- Doesn't replace device enrollment. Devices must still be enrolled in Intune using an Apple-supported enrollment method that results in a managed (or supervised) device.
- Doesn't determine whether a device is marked as corporate or personal in Intune. Device ownership is determined by the enrollment method and corporate identifiers.
- Doesn't provide per-service configuration controls in Intune. Apple defines which apps and services (such as iCloud features, FaceTime, or Messages) are available to managed Apple accounts.