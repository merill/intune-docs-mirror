---
layout: Conceptual
title: Overview of the App Lifecycle for Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/lifecycle
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
description: Learn about the managed apps lifecycle in Microsoft Intune. The app lifecycle involves adding, deploying, configuring, protecting, and retiring apps.
ms.date: 2025-11-18T00:00:00.0000000Z
ms.topic: concept-article
ms.reviewer: bryanke
ms.custom: apps; get-started
locale: en-us
document_id: c9568e4b-98a9-a0c2-65d7-cf0f1bade27a
document_version_independent_id: c9568e4b-98a9-a0c2-65d7-cf0f1bade27a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/lifecycle.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/lifecycle
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/lifecycle.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: f78e4569-16c1-c507-0097-955fd630b7d6
---

# Overview of the App Lifecycle for Microsoft Intune - Microsoft Intune | Microsoft Learn

The Microsoft Intune app lifecycle begins when an app is added and progresses through additional phases until you remove the app. By understanding these phases, you'll have the details you need to get started with app management in Intune.

![The app lifecycle - Add, deploy, configure, protect and retire.](media/lifecycle/app-lifecycle.png)

## Add

The first step in app deployment is to add the apps, which you want to manage and assign, to Intune. While you can work with many different app types, the basic procedures are the same. With Intune you can add different app types, including apps written in-house (line-of-business), apps from the store, apps that are built in, and apps on the web. For more information about each of these app types, see [How to add an app to Microsoft Intune](deployment/).

## Deploy

After you've added the app to Intune, you can then [assign it to users and devices that you manage](deployment/assign-groups). Intune makes this process easy, and after the app is deployed, you can [monitor the success](monitor-assignments) of the deployment from the Intune within the portal. Additionally, in some app stores, such as the [Apple](deployment/manage-vpp-apple) app store, you can purchase app licenses in bulk for your company. Intune can synchronize data with these stores so that you can deploy and track license usage for these types of apps right from the Intune administration console.

## Configure

As part of the app lifecycle, new versions of apps are regularly released. Intune provides tools to easily [update apps](deployment/) that you have deployed to a newer version. Additionally, you can configure extra functionality for some apps, for example:

- [iOS/iPadOS app configuration policies](configuration/configure-managed-ios) supply settings for compatible iOS/iPadOS apps that are used when the app is run. For example, an app might require specific branding settings or the name of a server to which it must connect.
- [Microsoft Edge management policies](configuration/configure-edge-ios-android) help you configure settings for [Microsoft Edge](ref-protected-apps#microsoft-apps), which replaces the default device browser and lets you restrict the websites that your users can visit.

## Protect

Intune gives you many ways to help protect the data in your apps. The main methods are:

- [Conditional Access](../device-security/conditional-access-integration/overview), which controls access to email and other services based on conditions that you specify. Conditions include device types or compliance with a [device compliance policy](../device-security/compliance/overview) that you deployed.
- [App protection policies](protection/overview) works with individual apps to help protect the company data that they use. For example, you can restrict copying data between unmanaged apps and apps that you manage, or you can prevent apps from running on devices that have been jailbroken or rooted.

## Retire

Eventually, it's likely that apps that you deployed become outdated and need to be removed. Intune makes it easy to uninstall apps. For more information, see [Uninstall an app](deployment/#uninstall-an-app).