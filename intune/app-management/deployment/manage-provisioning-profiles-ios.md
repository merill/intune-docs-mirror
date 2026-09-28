---
layout: Conceptual
title: iOS/iPadOS App Provisioning Profiles in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/manage-provisioning-profiles-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- iOS/iPadOS
ms.reviewer: bryanke
ms.subservice: apps
description: Intune gives you the tools to proactively assign a new provisioning profile to devices that have apps that are nearing expiry.
ms.date: 2025-01-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 4568d87b-4966-276e-6b35-5d404c8e57a5
document_version_independent_id: 4568d87b-4966-276e-6b35-5d404c8e57a5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/manage-provisioning-profiles-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/manage-provisioning-profiles-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/manage-provisioning-profiles-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: c149508f-6202-2524-5645-83491887ba4b
---

# iOS/iPadOS App Provisioning Profiles in Microsoft Intune - Microsoft Intune | Microsoft Learn

## Introduction

Apple iOS/iPadOS line-of-business apps that are assigned to iPhones and iPads are built with an included provisioning profile and code that is signed with a certificate. When the app is run, iOS/iPadOS confirms the integrity of the iOS/iPadOS app and enforces policies that are defined by the provisioning profile. The following validations happen:

- **Installation file integrity** - iOS/iPadOS compares the app's details with the enterprise signing certificate's public key. If they differ, the app's content might have changed, and the app is not allowed to run.
- **Capabilities enforcement** - iOS/iPadOS attempts to enforce the app's capabilities from the enterprise provisioning profile (not individual developer provisioning profiles) that are in the app installation (.ipa) file.

The enterprise signing certificate that you use to sign apps typically lasts for three years. However, the provisioning profile expires after a year. While the certificate is still valid, Intune gives you the tools to proactively assign a new provisioning profile to devices that have apps that are nearing expiry. After the certificate expires, you must sign the app again with a new certificate and embed a new provisioning profile with the key of the new certificate.

As the admin, you can include and exclude security groups to assign iOS/iPadOS app provisioning configuration. For example, you can assign an iOS/iPadOS app provisioning configuration to All Users, but exclude an executive group.

## How to create an iOS mobile app provisioning profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **iOS app provisioning profiles** &gt; **Create profile**.
3. On the **Basics** page, add the following values:

    - **Name** - Provide a name for this mobile provisioning profile.
    - **Description** - Optionally, provide a description for the policy.
    - **Upload profile file** - Choose **Open** icon, and then choose an Apple Mobile Configuration Profile file (with the extension `.mobileprovision`) that you downloaded from the [Apple Developer website](https://developer.apple.com/).

    The **Expiration date** will be populated from a value in the Apple Mobile Configuration Profile file that you added above.
![Create profile - Basics](media/manage-provisioning-profiles-ios/app-provisioning-profile-ios-01.png)
4. Click **Next: Scope tags**. On the **Scope tags** page you can optionally configure scope tags to determine who can see iOS/iPadOS app provisioning profile in Intune. For more information about scope tags, see [Use role-based access control and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).
5. Click **Next: Assignments**. The **Assignments** page allows you can assign the profile to users and devices. It is important to note that you can assign a profile to a device whether or not the device is managed by Intune.
6. Click **Next: Review + create** to review the values you entered for the profile.
7. When you are done, click **Create** to create the iOS/iPadOS app provisioning profile in Intune.