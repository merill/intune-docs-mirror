---
layout: Conceptual
title: iOS/iPadOS bundle IDs for built-in apps in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-bundle-ids-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: See a list of the bundle IDs for the built-in iOS and iPadOS apps. Use these bundle IDs to explicitly allow apps in device configuration profiles and policies in Microsoft Intune.
ms.date: 2025-09-22T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 06c3f861-0f40-b7d5-bf68-1766344437e9
document_version_independent_id: 06c3f861-0f40-b7d5-bf68-1766344437e9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-bundle-ids-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-bundle-ids-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-bundle-ids-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 312c02e1-6da4-4ddb-ee69-9d7918f84b2d
---

# iOS/iPadOS bundle IDs for built-in apps in Microsoft Intune - Microsoft Intune | Microsoft Learn

When you configure features on iOS/iPadOS devices, you can also add the built-in apps on these devices. This article lists the bundle IDs of some common built-in iOS/iPadOS apps.

To get the bundle ID of other apps, you can:

- [Get the app bundle ID using the Intune admin center](../../app-management/collect-bundle-ids).
- Go to Apple's list of [iOS/iPadOS bundle IDs](https://support.apple.com/guide/deployment/bundle-ids-for-native-ios-and-ipados-apps-depece748c41/1/web/1.0) (opens Apple's web site).

Tip

On macOS devices, you can get the bundle ID using the Terminal app and AppleScript: `osascript -e 'id of app "AppName"'`.

This feature applies to:

- iOS/iPadOS

## Bundle IDs

| Bundle ID | App Name | Publisher |
| --- | --- | --- |
| com.apple.AppStore | App Store | Apple |
| com.apple.store.Jolly | Apple Store | Apple |
| com.apple.calculator | Calculator | Apple |
| com.apple.mobilecal | Calendar | Apple |
| com.apple.camera | Camera | Apple |
| com.apple.mobiletimer | Clock | Apple |
| com.apple.clips | Clips | Apple |
| com.apple.compass | Compass | Apple |
| com.apple.MobileAddressBook | Contacts | Apple |
| com.apple.facetime | FaceTime | Apple |
| com.apple.DocumentsApp | Files | Apple |
| com.apple.mobileme.fmf1 | Find Friends | Apple |
| com.apple.mobileme.fmip1 | Find iPhone | Apple |
| com.apple.games | Games | Apple |
| com.apple.gamecenter | Game Center | Apple |
| com.apple.mobilegarageband | GarageBand | Apple |
| com.apple.Health | Health | Apple |
| com.apple.Home | Home | Apple |
| com.apple.iBooks | iBooks | Apple |
| com.apple.iMovie | iMovie | Apple |
| com.apple.itunesconnect.mobile | iTunes Connect | Apple |
| com.apple.MobileStore | iTunes Store | Apple |
| com.apple.itunesu | iTunes U | Apple |
| com.apple.Keynote | Keynote | Apple |
| com.apple.mobilemail | Mail | Apple |
| com.apple.Maps | Maps | Apple |
| com.apple.measure | Measure | Apple |
| com.apple.MobileSMS | Messages | Apple |
| com.apple.Music | Music | Apple |
| com.apple.news | News | Apple |
| com.apple.mobilenotes | Notes | Apple |
| com.apple.Numbers | Numbers | Apple |
| com.apple.Pages | Pages | Apple |
| com.apple.Passwords | Passwords | Apple |
| com.apple.mobilephone | Phone | Apple |
| com.apple.Photo-Booth | Photo Booth | Apple |
| com.apple.mobileslideshow | Photos | Apple |
| com.apple.podcasts | Podcasts | Apple |
| com.apple.preview | Preview | Apple |
| com.apple.reminders | Reminders | Apple |
| com.apple.mobilesafari | Safari | Apple |
| com.apple.Preferences | Settings | Apple |
| com.apple.shortcuts | Shortcuts | Apple |
| com.apple.SiriViewService | Siri | Apple |
| com.apple.stocks | Stocks | Apple |
| com.apple.tips | Tips | Apple |
| com.apple.tv | TV | Apple |
| com.apple.videos | Videos | Apple |
| com.apple.VoiceMemos | VoiceMemos | Apple |
| com.apple.Passbook | Wallet | Apple |
| com.apple.Bridge | Watch | Apple |
| com.apple.weather | Weather | Apple |
| com.apple.barcodesupport.qrcode | QR Code Reader | Apple |