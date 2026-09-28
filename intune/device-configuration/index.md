---
layout: Landing
title: Device configuration - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/
summary: Configure device settings and features in Microsoft Intune. Use the settings catalog, templates, single sign-on, endpoint security profiles, and certificates to manage your device fleet.
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: configuration
description: Configure device settings, SSO, endpoint security, and certificates in Microsoft Intune using the settings catalog and templates.
ms.topic: landing-page
ms.date: 2026-05-04T00:00:00.0000000Z
locale: en-us
document_id: 73345a77-8262-dbd8-d009-257cbd7cc935
document_version_independent_id: 73345a77-8262-dbd8-d009-257cbd7cc935
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/index.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: landing
toc_rel: ../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/index.yml
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9a577e35-1c5d-0d6e-8f63-390e1e94103f
---

# Device configuration

Configure device settings and features in Microsoft Intune. Use the settings catalog, templates, single sign-on, endpoint security profiles, and certificates to manage your device fleet.

## Get started with device configuration

### Overview

- [Device features and settings](overview)

### Concept

- [Settings insights for configuration policies](settings-insight)

### How-To Guide

- [Create a device configuration profile](create-device-profile)
- [Assign a device configuration profile](assign-device-profile)
- [Collect device hardware info with the properties catalog](collect-device-properties)
- [Monitor device configuration policies](monitor-device-profile)
- [Troubleshoot device configuration profiles](troubleshoot-device-profiles)

## Use the settings catalog

### Overview

- [Settings catalog overview](settings-catalog/)

### How-To Guide

- [Common tasks and features in the settings catalog](settings-catalog/common-tasks)
- [Deploy Microsoft Edge policy with the settings catalog](settings-catalog/configure-edge)
- [Import custom ADMX and ADML templates](settings-catalog/import-custom-admx-templates)
- [Configure Recovery Lock for macOS](settings-catalog/configure-recovery-lock-macos)
- [Configure Universal Print policy](settings-catalog/configure-universal-print)
- [Restrict USB devices](settings-catalog/restrict-usb)

## Configure devices with templates

### How-To Guide

- [Use custom device settings](templates/configure-custom-settings)
- [Use custom OMA-URI settings on Windows devices](templates/configure-custom-settings-windows)
- [Use custom settings on Apple devices](templates/configure-custom-settings-apple)
- [Create a Wi-Fi profile for devices](templates/configure-wifi)
- [Use OEMConfig on Android Enterprise devices](templates/configure-oemconfig-android)
- [Configure delivery optimization for Windows](templates/configure-delivery-optimization-windows)
- [Create iOS/iPadOS or macOS device profile](templates/configure-device-features-apple)
- [Kiosk settings for Windows and Holographic devices](templates/configure-kiosk)

## Configure single sign-on (SSO)

### Concept

- [Use the Enterprise SSO plug-in on Apple devices](enterprise-sso-plugin)

### How-To Guide

- [Configure Platform SSO for macOS](settings-catalog/configure-platform-sso-macos)
- [Platform SSO scenarios for macOS](settings-catalog/configure-platform-sso-scenarios-macos)
- [Configure the Enterprise SSO plug-in for iOS/iPadOS](settings-catalog/configure-enterprise-sso-plugin-ios)
- [Configure the Enterprise SSO plug-in for macOS using a template](templates/configure-enterprise-sso-plugin-macos)

## Endpoint security profiles

### Concept

- [Manage attack surface reduction settings](endpoint-security/attack-surface-reduction)
- [Manage account protection settings](endpoint-security/account-protection)

### How-To Guide

- [Encrypt Windows devices with BitLocker](endpoint-security/encrypt-bitlocker-windows)
- [Manage approved apps with App Control for Business](endpoint-security/manage-app-control)

### Reference

- [Manage firewall settings with endpoint security policies](endpoint-security/firewall)

## Deploy device certificates

### How-To Guide

- [Use SCEP certificate profiles](certificates/scep-profiles)
- [Use PKCS certificate profiles](certificates/pkcs-profiles)
- [Create trusted certificate profiles](certificates/trusted-root-profiles)
- [Use imported PFX certificates](certificates/imported-pfx-profiles)
- [Remove SCEP or PKCS certificates](certificates/remove-profiles)

## Settings reference

### Reference

- [Apple device restriction settings](templates/ref-device-restrictions-apple)
- [Android device restriction settings](templates/ref-device-restrictions-android-enterprise)
- [Windows device restriction settings](templates/ref-device-restrictions-windows)
- [Apple device feature settings](templates/ref-device-features-apple)
- [Apple Wi-Fi settings](templates/ref-wifi-settings-apple)
- [Kiosk settings for Windows](templates/ref-kiosk-settings-windows)
- [Edition upgrade and mode change settings for Windows](templates/ref-edition-upgrade-settings-windows)
- [Apple settings catalog reference](settings-catalog/ref-apple-settings)