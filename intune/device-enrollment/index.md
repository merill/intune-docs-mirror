---
layout: Landing
title: Device enrollment - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/
summary: Enroll devices in Microsoft Intune so they can receive the policies and profiles you configure. Learn about enrollment methods for each platform and how to configure enrollment settings.
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: enrollment
description: Enroll devices in Microsoft Intune to manage and secure them with policies, profiles, and compliance settings across all major platforms.
ms.topic: landing-page
ms.date: 2026-05-04T00:00:00.0000000Z
locale: en-us
document_id: f07584be-a9b0-164b-cdac-c6de00ac7da9
document_version_independent_id: f07584be-a9b0-164b-cdac-c6de00ac7da9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/index.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: landing
toc_rel: ../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/index.yml
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 5b242ca2-9170-1f82-7bed-91d06cd98c0d
---

# Device enrollment

Enroll devices in Microsoft Intune so they can receive the policies and profiles you configure. Learn about enrollment methods for each platform and how to configure enrollment settings.

## Get started with device enrollment

### Overview

- [Device enrollment guide](guide)

### Concept

- [Understand Intune and Microsoft Entra device limit restrictions](limits-intune-entra)
- [Overview of enrollment restrictions](restrictions)

### How-To Guide

- [Enroll devices in Intune](enroll-devices)
- [Enroll devices using a device enrollment manager account](setup-enrollment-manager)
- [Linux device enrollment guide](guide-linux)

## Enroll iOS/iPadOS devices

### Overview

- [iOS/iPadOS device enrollment guide](apple/guide-ios-ipados)

### Concept

- [Overview of automated device enrollment for Apple devices](apple/overview-automated-enrollment-apple)

### How-To Guide

- [Get an Apple MDM Push certificate for Intune](apple/create-mdm-push-certificate)
- [Set up an Apple token for automated enrollment](apple/setup-apple-token)
- [Set up automated device enrollment (ADE) for iOS/iPadOS](apple/setup-automated-ios)
- [Set up account driven Apple User Enrollment](apple/setup-account-driven-user)
- [Set up Apple Configurator enrollment](apple/setup-configurator-ios)
- [Set up web-based device enrollment for iOS/iPadOS](apple/setup-web-based-ios)

## Enroll macOS devices

### Overview

- [macOS device enrollment guide](apple/guide-macos)

### Concept

- [Choose a macOS enrollment method](apple/methods-macos)
- [Overview of automated device enrollment for macOS](apple/overview-automated-enrollment-macos)

### How-To Guide

- [Set up automated device enrollment (ADE) for macOS](apple/setup-automated-macos)
- [Set up a macOS token for automated enrollment](apple/setup-macos-token)
- [Manage Apple device enrollment tokens for macOS](apple/manage-devices-tokens-macos)

## Enroll Android devices

### Concept

- [Android device enrollment guide](android/guide)

### How-To Guide

- [Connect Intune account to managed Google Play account](android/connect-managed-google-play)
- [Set up Android Enterprise dedicated devices](android/setup-dedicated)
- [Set up Android Enterprise corporate-owned work profile](android/setup-corporate-work-profile)
- [Set up Android Enterprise fully managed devices](android/setup-fully-managed)
- [Use device staging for Android](android/device-staging)

## Enroll Windows devices

### Concept

- [Windows device enrollment guide](windows/guide)

### How-To Guide

- [Enable MDM automatic enrollment for Windows](windows/enable-automatic-mdm)
- [Set up the Windows Enrollment Status Page](windows/setup-status-page)
- [Set up automatic enrollment in Intune](windows/quickstart-automatic-mdm)
- [Enroll a Windows device](windows/quickstart-first-device)
- [Enable backup and restore for Windows enrollment](windows/enable-backup-restore)
- [Bulk enrollment for Windows devices](windows/create-bulk-package)
- [Enable autodiscovery of Intune enrollment server](windows/create-cname-autodiscovery)

## Configure enrollment settings

### How-To Guide

- [Add corporate identifiers to Intune](add-corporate-identifiers)
- [Set up enrollment time grouping](setup-time-grouping)
- [Require multifactor authentication for device enrollment](configure-multifactor-authentication)
- [Create device platform restrictions](create-platform-restrictions)
- [Set terms and conditions](create-terms-and-conditions)