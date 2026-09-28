---
layout: Conceptual
title: Shared iOS and iPadOS devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/shared-device-solutions-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: annovich
ms.subservice: enrollment
description: Learn about Shared iOS and iPadOS devices.
ms.date: 2024-09-16T00:00:00.0000000Z
ms.topic: overview
locale: en-us
document_id: 308e83fb-4f12-350b-7998-261ee39a5176
document_version_independent_id: 308e83fb-4f12-350b-7998-261ee39a5176
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/shared-device-solutions-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/shared-device-solutions-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/shared-device-solutions-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: c7fa9d71-2022-ade6-631c-59afb84ed325
---

# Shared iOS and iPadOS devices - Microsoft Intune | Microsoft Learn

Important

Shared device mode for iOS/iPadOS isn't currently available for GCC High tenants.

Shared devices are organization-owned multi-user devices. These devices can be special-purpose or multi-purpose as needed in each environment. Shared devices enable front-line workers in healthcare, hospitality, retail, manufacturing, and other industries to access critical applications and tools essential to their role in the organization. In education, shared devices are used as learning aids or test-taking devices in classrooms.

Microsoft Intune supports two types of shared device solutions for iOS and iPadOS:

- [Shared iPads](shared-ipad)
- [Shared Device Mode](/en-us/azure/active-directory/develop/msal-ios-shared-devices)

## Compare solutions

The following table captures the key differences between the two available shared devices solutions on iOS/iPadOS. Review this to select the most appropriate iOS/iPadOS shared device strategy for your organization.

| Consideration | Shared iPad | Shared Device Mode |
| --- | --- | --- |
| Supported device types | iPad | iPhone, iPod touch, iPad |
| Minimum device requirements | iPadOS 13.4 or later with at least 32 GB of storage. | iOS 13 or later, iPadOS 13 or later |
| Microsoft Entra federation with Apple Business or School Manager | Required. This enables users to sign in using their Microsoft Entra username and password. | Not required |
| Managed Apple ID | Microsoft Entra federation automatically creates Managed Apple ID when user signs in on Shared iPad for the first time.<br>If Microsoft Entra federation isn't set up, Managed Apple IDs can be created manually in Apple Business or School Manager and shared with users for signing in. | Not required |
| Device provisioning | Shared iPad can be enabled on iPads enrolled using Automated Device Enrollment without user affinity. | Shared Device Mode can be configured on devices enrolling using Automated Device Enrollment without user affinity. For more information, see [Microsoft Entra shared device mode for iOS devices](/en-us/azure/active-directory/develop/msal-ios-shared-devices#use-intune-to-enable-shared-device-mode--sso-extension). |
| Temporary session without signing in | Temporary sessions that don't require a Managed Apple ID or password are allowed by default. Temporary sessions can be allowed or blocked by Intune policy. For more information, see [Shared iPad](../../device-configuration/templates/ref-device-restrictions-apple). | Not applicable |
| Supported app types | Device-licensed purchased or custom apps (VPP), line-of-business apps, web apps. | Apps modified to support Shared Device Mode including MSAL integration. For more information, see [Modify your iOS application to support shared device mode](/en-us/azure/active-directory/develop/msal-ios-shared-devices#modify-your-ios-application-to-support-shared-device-mode). |
| Policy and app assignment | Device-assigned required apps and policies are supported. The same apps and policies apply to any user signing in on a Shared iPad.Some device configuration policies can be user-assigned. For more information, see [Configure settings for Shared iPads](shared-ipad#configure-settings-for-shared-ipads). | Device-assigned required apps and policies are supported.App Protection Policies. |
| Unsupported scenarios | Conditional Access.\*App Protection Policies.Intune Company Portal app.Available apps. | Intune Company Portal app.Available apps.Apps that don't support Shared Device Mode.User-assigned policies and apps. |

\* The following Conditional Access configurations are not supported with Shared iPad:

- Granting Conditional Access conditions for a device that require an approved client app, require an app protection policy, require [per-device terms of use](/en-us/azure/active-directory/conditional-access/terms-of-use#per-device-terms-of-use), or require the device to be marked as compliant.
- Conditional Access conditions that use filters for devices.

## Recommended iOS/iPadOS shared device strategy

Shared iPad is the recommended shared device solution for Microsoft 365 on iPadOS. If you're planning your organization's shared device strategy, we recommended that you choose iPadOS devices that meet the minimum requirements for Shared iPad (see section above). If your organization's shared device strategy requires cellphone capabilities or includes iOS devices, Shared Device Mode is the recommended shared device solution on iOS. Review the differences between Shared iPad and Shared Device Mode to ensure that the recommendations above will fit your organization's needs.