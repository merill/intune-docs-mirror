---
layout: Conceptual
title: Set up user enrollment with Company Portal for iOS - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-user-company-portal
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: rishitasarin
ms.subservice: enrollment
description: Set up the profile based Apple User Enrollment option for personal devices enrolling in Microsoft Intune.
ms.date: 2024-12-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: ae0c7e20-eee7-10d5-cd7a-2b7f141f3fc3
document_version_independent_id: ae0c7e20-eee7-10d5-cd7a-2b7f141f3fc3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/setup-user-company-portal.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/setup-user-company-portal
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/setup-user-company-portal.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 1d0d28f0-c1f1-7563-cde0-cd78c518d2f8
---

# Set up user enrollment with Company Portal for iOS - Microsoft Intune | Microsoft Learn

Note

Microsoft Intune doesn't support this enrollment profile type for newly enrolled devices. This article is only applicable to existing devices with this profile type. We recommend [account-driven user enrollment](setup-account-driven-user) for new enrollments.

Set up user enrollment with Company Portal for iOS/iPadOS personal devices enrolling in Microsoft Intune. This Apple User Enrollment method gives you access to a limited but appropriate set of device management settings and actions, so you can protect work data without affecting the device user's personal data or apps.

When the device owner attempts to sign in to an app with their work or school account, Intune prompts them to enroll their device and provides instructions for next steps. The device user authenticates and initiates enrollment by signing in to the Intune Company Portal app. From there, they're redirected to Safari and the device settings app, where they download and install the enrollment profile.

This article describes how to set up an enrollment profile in the Microsoft Intune admin center for Apple User Enrollment with Company Portal.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This enrollment method supports the following platforms:
> 
> - iOS 13 or later
> - iPadOS 13.1 or later
> 

![](../../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> - [Set mobile device management (MDM) authority](../../fundamentals/setup-mdm-authority)
> - [Get Apple MDM Push certificate](create-mdm-push-certificate)
> - [Create Managed Apple IDs for device users](https://support.apple.com/en-us/HT210737) (Opens Apple Support website)
> 

Additionally, review the following information:

- Apple User Enrollment requires you to create and provide managed Apple IDs to enrolling users. If you enable federated authentication, which consists of linking Apple Business with Microsoft Entra ID, you don't have to create and provide unique Apple IDs to each user. Instead, a device user can sign in to their apps with the same credentials they use for their work account. For more information, see [Intro to federated authentication with Apple Business](https://support.apple.com/guide/apple-business-manager/intro-to-federated-authentication-axmb19317543/1/web/1) in the Apple Business User Guide.

## Create enrollment profile

Note

A user enrollment profile overrides an Intune enrollment restriction policy.

Complete these steps to create an enrollment profile for devices enrolling via user enrollment with Company Portal.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Device onboarding** &gt; **Enrollment**.
3. Under **Enrollment Options**, choose **Enrollment types**.
4. Select **Create profile** &gt; **iOS/iPadOS**.
5. On the **Basics** page, enter a name and description for the profile so that you can distinguish it from other profiles in the admin center. Device users don't see these details.

    Tip

    You can use the name field to create a dynamic group in Microsoft Entra ID, and assign devices to the enrollment profile automatically. Use the profile name to define the *enrollmentProfileName* parameter. For more information, see [Microsoft Entra dynamic groups](/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership#rules-for-devices).
6. Select **Next**.
7. On the **Settings** page, select **User enrollment with Company Portal**.
8. Select **Next**.
9. On the **Assignments** page, assign the profile to all users, or select specific groups. Device groups aren't supported in user enrollment scenarios because user enrollment requires user identities.
10. Select **Next**.
11. On the **Review + create** page, review your choices, and then select **Create** to finish creating the profile.

## Profile priority

Intune applies enrollment profiles in the order you prioritize them. To change the order in which they're applied:

1. Go back to **Enrollment types** to view your profiles.
2. Drag and drop the profiles in the list to reorder their priority.

If a conflict occurs because a user is assigned more than one profile, Intune applies the profile with the higher priority.

## Removing device from management

The volume and cryptographic keys created to manage the work data on the device are erased when the device unenrolls from Intune.