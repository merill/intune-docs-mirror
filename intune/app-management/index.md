---
layout: Landing
title: Application management - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/
summary: Deploy, configure, and monitor applications across your managed devices with Microsoft Intune.
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.subservice: apps
description: Deploy, configure, and monitor applications across managed devices with Microsoft Intune app management.
ms.topic: landing-page
ms.date: 2026-05-04T00:00:00.0000000Z
locale: en-us
document_id: a5ca605c-51cc-66fa-2444-63b539bd41c7
document_version_independent_id: a5ca605c-51cc-66fa-2444-63b539bd41c7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/index.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: landing
toc_rel: ../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/index.yml
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/caec7b7f-4941-4578-b79f-c63b1c1f5af4
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/754dea88-f800-4835-b6b5-280cb5d81e88
platformId: 40fbc6f7-1320-53a1-ce83-464fa5c3695e
---

# Application management

Deploy, configure, and monitor applications across your managed devices with Microsoft Intune.

## Get started with app management

### Overview

- [What is app management in Microsoft Intune?](overview)
- [Add apps to Microsoft Intune](deployment/)

### Concept

- [App lifecycle overview](lifecycle)

### How-To Guide

- [Discovered apps](discovered-apps)

### Reference

- [Intune protected apps](ref-protected-apps)

## Deploy Win32 and LOB apps

### Concept

- [Win32 app management overview](deployment/win32)

### How-To Guide

- [Prepare a Win32 app for upload (create the .intunewin package)](deployment/create-win32-package)
- [Add and assign Win32 apps](deployment/add-win32)
- [Add a Windows LOB app](deployment/add-lob-windows)
- [Configure Win32 app supersedence](deployment/configure-win32-supersedence)
- [Add a macOS LOB app](deployment/add-lob-macos)
- [Deploy Windows update packages](deployment/deploy-win32-update-package)
- [Add an Android LOB app](deployment/add-lob-android)

## Deploy store and Microsoft 365 apps

### How-To Guide

- [Add Microsoft 365 apps for Windows](deployment/add-microsoft-365-windows)
- [Manage Apple volume-purchased apps](deployment/manage-vpp-apple)
- [Add managed Google Play apps](deployment/add-managed-google-play)
- [Deploy Windows apps](deployment/deploy-windows)
- [Add Microsoft Store apps](deployment/add-microsoft-store)

## Enterprise app catalog and volume licensing

### How-To Guide

- [Enterprise App Management overview](deployment/enterprise-app-management)
- [Add an Enterprise App Catalog app](deployment/add-enterprise-catalog-app)
- [Guided update supersedence](deployment/update-enterprise-supersedence)
- [Manage volume-purchased apps and books](deployment/manage-volume-purchased)

## Deploy Company Portal and macOS apps

### How-To Guide

- [Add the Company Portal app for macOS](deployment/add-company-portal-macos)
- [Add an unmanaged macOS PKG app](deployment/add-unmanaged-pkg-macos)
- [Add a macOS DMG app](deployment/add-dmg-macos)
- [Add the Windows Company Portal app](deployment/add-company-portal-windows)
- [Add the Company Portal app for Autopilot](deployment/add-company-portal-autopilot)

## Configure apps

### Overview

- [App configuration policies overview](configuration/overview)

### How-To Guide

- [Configure Microsoft Edge for iOS/Android](configuration/configure-edge-ios-android)
- [Configure managed Android devices](configuration/configure-managed-android)
- [Configure managed iOS/iPadOS devices](configuration/configure-managed-ios)
- [Configure the Managed Home Screen](configuration/configure-managed-home-screen)
- [Configure the Company Portal app](configuration/configure-company-portal)
- [Configure Outlook for iOS/Android](configuration/configure-outlook)

## Protect app data

### Overview

- [App protection policies overview](protection/overview)

### How-To Guide

- [Create an app protection policy](protection/create-policy)
- [App protection without enrollment (MAM-WE)](protection/mam-without-enrollment)
- [Selectively wipe app data](protection/wipe-corporate-data)

### Reference

- [iOS/iPadOS app protection settings](protection/ref-settings-ios)
- [Android app protection settings](protection/ref-settings-android)
- [Windows app protection settings](protection/ref-settings-windows)
- [App protection FAQ](protection/mam-faq)

## Assign, monitor, and troubleshoot apps

### How-To Guide

- [Assign apps to groups](deployment/assign-groups)
- [Include and exclude app assignments](deployment/configure-assignment-scope)
- [Monitor app information and assignments](monitor-assignments)
- [Troubleshoot Win32 apps](deployment/troubleshoot-win32)