---
layout: Conceptual
title: Understand App Protection Policy Delivery and Timing - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/protection/policy-delivery-timing
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
description: Learn the different deployment windows for app protection policies to understand when changes should appear on your end user devices.
ms.date: 2024-05-20T00:00:00.0000000Z
ms.topic: concept-article
ms.reviewer: beflamm
ms.custom: 
locale: en-us
document_id: 57cbb7a6-5327-e313-8331-ad61d59e3ac9
document_version_independent_id: 57cbb7a6-5327-e313-8331-ad61d59e3ac9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/protection/policy-delivery-timing.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/protection/policy-delivery-timing
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/protection/policy-delivery-timing.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4da5c433-896e-9d70-e315-058e0a736e65
---

# Understand App Protection Policy Delivery and Timing - Microsoft Intune | Microsoft Learn

Learn about the different delivery timing for app protection policies to understand when changes should appear on your end-user devices.

## Delivery timing summary

App protection policy (APP) delivery depends on the license state and Intune service registration for your users.

| User State | App Protection behavior | Retry Interval (see note) | Why does this happen? |
| --- | --- | --- | --- |
| Tenant Not Onboarded | Wait for next retry interval. App Protection isn't active for the user. | 24 hours | Occurs when you have not setup your tenant for Intune. |
| User Not Licensed | Wait for next retry interval. App Protection isn't active for the user. | 12 hours - However, on Android devices this interval requires Intune APP SDK version 5.6.0 or later. Otherwise for Android devices, the interval is 24 hours. | Occurs when you haven't licensed the user for Intune. |
| User Not Assigned App Protection Policies | Wait for next retry interval. App Protection isn't active for the user. | 12 hours | Occurs when you haven't assigned APP settings to the user. |
| User Assigned App Protection Policies but app isn't defined in the App Protection Policies | Wait for next retry interval. App Protection isn't active for the user. | 12 hours | Occurs when you haven't added the app to APP. |
| User Successfully Registered for Intune MAM | App Protection is applied per policy settings. Updates occur based on retry interval | Intune Service defined based on user load. Typically 30 mins. | Occurs when the user has successfully registered with the Intune service for APP configuration. |

Note

Retry intervals may require active app use to occur, meaning the app is launched and in use. If the retry interval is 24 hours and the user waits 48 hours to launch the app, the Intune APP SDK will retry at 48 hours.

Note

Applications that have not checked-in with the Intune MAM Service within the last 90 days may be automatically deregistered from the Intune MAM Service. When the user next launches the application, the Intune APP SDK will automatically attempt to register the application. The user may be prompted to connect to the internet and enter credentials to complete the registration.

## Handling network connectivity issues

When user registration fails due to network connectivity issues an accelerated retry interval is used. The Intune APP SDK retries at increasingly longer intervals until the interval reaches 60 minutes or a successful connection is made. The Intune APP SDK will then continue to retry at 60-minute intervals until a successful connection is made. Then, the Intune APP SDK returns to the standard retry interval based on the user state.