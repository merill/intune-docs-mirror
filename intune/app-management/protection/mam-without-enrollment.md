---
layout: Conceptual
title: Mobile Application Management (MAM) for unenrolled devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/protection/mam-without-enrollment
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.subservice: apps
description: Use mobile application management without enrollment to deploy apps, and protect organization data within the apps. Get an overview of the administrator and end user tasks for this enrollment option.
ms.date: 2024-04-22T00:00:00.0000000Z
ms.topic: article
locale: en-us
document_id: 213fb6a1-e587-6415-877b-7c20b60436d2
document_version_independent_id: 213fb6a1-e587-6415-877b-7c20b60436d2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/protection/mam-without-enrollment.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/protection/mam-without-enrollment
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/protection/mam-without-enrollment.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/80beb97b-18aa-44f8-9420-8f2a4cd448eb
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c09e0ef-0fde-4b6d-bf1b-b517e4db7f80
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 7a3a89ec-88f9-2c98-9fd0-414291b67d29
---

# Mobile Application Management (MAM) for unenrolled devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

MAM for unenrolled devices uses app configuration profiles to deploy or configure apps on devices without enrolling the device. When combined with app protection policies, you can protect data within an app.

MAM for unenrolled devices is commonly used for personal or bring your own devices (BYOD). Or, used for enrolled devices that need extra security. MAM is an option for users who don't enroll their personal devices, but still need access to organization email, Teams meetings, and more.

MAM is available on the following platforms:

- Android
- iOS/iPadOS
- Windows

This article provides recommendations on when to use MAM. It also includes an overview of the administrator and user tasks. For more specific information on MAM, go to:

- [Microsoft Intune app management](../overview)
- [Data protection for Windows MAM](enable-mam-windows)

## Before you begin

For an overview, including any Intune-specific prerequisites, see [Deployment guidance: Enroll devices in Microsoft Intune](../../device-enrollment/guide).

## MAM

Use for personal or bring your own devices (BYOD). Or, use on organization-owned devices that need specific app configuration, or extra app security.

| Feature | Use this enrollment option when |
| --- | --- |
| You want to configure specific apps, and control access to these apps, such as Outlook or Microsoft Teams. | ✅ |
| Devices are personal or BYOD. | ✅ |
| You have new or existing devices. | ✅ |
| Need to manage a few devices, or a large number of devices (bulk enrollment). | ✅ |
| Devices are associated with a single user. | ✅ |
| Devices are managed by another MDM provider. | ✅ |
| You use the device enrollment manager (DEM) account. | ✅ |
| Devices are owned by the organization or school. | ❌  Not recommended as the *only* enrollment method for organization-owned devices. Organization-owned devices should be enrolled and managed by Intune. If you want extra security for specific apps, then use MDM enrollment and MAM together. |
| Devices are user-less, such as kiosk, or dedicated device. | ❌ Typically, user-less or shared devices are organization-owned. These devices should be enrolled and managed by Intune. |

### MAM administrator tasks

This task list provides an overview. For more specific information, see [Microsoft Intune app management](../overview).

- Be sure your devices are [supported](../../fundamentals/ref-supported-platforms).
- In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), [add your apps](../ref-protected-apps) or [configure your apps](../configuration/overview). When the apps are on the device, the apps are considered "managed" by Intune. After you add or configure the app, create an [app protection policy](ref-settings-ios). For example, create a policy that allows or blocks features within the app, such as copy and paste.
- Tell users how to get different apps. For example, you can:

    - Direct users to the Company Portal web site at `portal.manage.microsoft.com`. When they sign in with their organization credentials, they see a list of apps, including required apps. They can get apps from this site.
    - Have users download and install the Company Portal app from the app store. Once authenticated, users can install apps, including required apps.

### MAM end user tasks

The specific tasks depend on how you tell users to install the apps.

- To install the apps, users can:

    - Go to the app store, and download the Company Portal app. Open the Company Portal app, and sign in with their organization credentials (`user@contoso.com`). The Company Portal app authenticates the user. Users see a list of available apps, including required apps.
    - Go to the Company Portal web site at `portal.manage.microsoft.com`, and sign in with their organization credentials (`user@contoso.com`). After users sign in, they see a list of available apps, including required apps.
    - Go to the app store, and download the apps they need. This option is for users who don't want to use the Company Portal app or web site. End users might also have to buy the app.
- After the app is installed, they open the app, and are prompted to sign in with their organization credentials (`user@contoso.com`). When users sign in, they might have to restart the app. After the restart, the app data is "managed" by Intune.
- Some platforms can require specific apps to install other apps, such as Outlook or Teams. For example, on iOS devices, users must install a broker app, such as the Microsoft Authenticator app. On Android devices, users must install the Company Portal app.