---
layout: Landing
title: Device security - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/
summary: Protect organizational data and devices by managing compliance, security baselines, endpoint protection, identity, and network access with Microsoft Intune.
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: protect
description: Manage device compliance, security baselines, Microsoft Defender integration, VPN tunnels, identity protection, and threat defense with Microsoft Intune.
ms.topic: landing-page
ms.date: 2026-05-04T00:00:00.0000000Z
locale: en-us
document_id: ade2f31c-535b-fc00-d7d6-1a175b0079f1
document_version_independent_id: ade2f31c-535b-fc00-d7d6-1a175b0079f1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/index.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: landing
toc_rel: ../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/index.yml
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 6de19223-c73f-dc40-da24-bdd49fc09a01
---

# Device security

Protect organizational data and devices by managing compliance, security baselines, endpoint protection, identity, and network access with Microsoft Intune.

## Get started with device security

### Overview

- [Protect data and devices with Microsoft Intune](overview)

### Concept

- [Endpoint security in Microsoft Intune](endpoint-security-policies)

### Reference

- [Configure Microsoft Intune for increased security](ref-zero-trust-security)
- [Zero Trust for tenant administration](ref-zero-trust-tenant)
- [Zero Trust for devices](ref-zero-trust-devices)
- [Zero Trust for data](ref-zero-trust-data)

## Device compliance

### Overview

- [Device compliance policies in Microsoft Intune](compliance/overview)

### How-To Guide

- [Create device compliance policies](compliance/create-policy)
- [Configure actions for noncompliance](compliance/configure-noncompliance-actions)
- [Monitor results of compliance policies](compliance/monitor-policy)
- [Use custom compliance settings](compliance/custom-settings)

### Reference

- [Windows compliance settings](compliance/ref-windows-settings)

## Security baselines

### Overview

- [Learn about Intune security baselines for Windows devices](security-baselines/overview)

### How-To Guide

- [Configure security baseline policies](security-baselines/configure-baselines)

### Reference

- [Windows security baseline settings](security-baselines/ref-windows-mdm-settings)
- [Microsoft Edge baseline settings (v2)](security-baselines/ref-v2-edge-settings)

## Microsoft Defender for Endpoint

### Overview

- [Integrate Microsoft Defender for Endpoint with Intune](microsoft-defender/overview)

### How-To Guide

- [Configure the Defender integration and onboard devices](microsoft-defender/configure-integration)
- [Manage Defender settings on unenrolled devices](microsoft-defender/security-settings-management)
- [Deploy Microsoft Defender for Endpoint on Android](microsoft-defender/deploy-android)
- [Remediate vulnerabilities found by Defender for Endpoint](microsoft-defender/remediate-vulnerabilities)
- [Monitor Defender for Endpoint risk](microsoft-defender/monitor)

## Microsoft Tunnel VPN

### Overview

- [Microsoft Tunnel VPN solution for Microsoft Intune](microsoft-tunnel/overview)

### Concept

- [Microsoft Tunnel with Mobile Application Management](microsoft-tunnel/mam)

### How-To Guide

- [Microsoft Tunnel prerequisites](microsoft-tunnel/prerequisites)
- [Install the Microsoft Tunnel](microsoft-tunnel/install)
- [Upgrade the Microsoft Tunnel server](microsoft-tunnel/upgrade)
- [Monitor the Microsoft Tunnel](microsoft-tunnel/monitor)

## Conditional Access

### Overview

- [Conditional Access with Intune compliance policies](conditional-access-integration/overview)

### Concept

- [Conditional Access scenarios](conditional-access-integration/scenarios)

### How-To Guide

- [Use app-based Conditional Access policies](conditional-access-integration/app-based-policies)
- [Configure Jamf Pro integration](conditional-access-integration/setup-jamf-manually)
- [Block apps that don't use modern authentication](conditional-access-integration/block-no-modern-auth)

## Identity and credentials

### Concept

- [Windows LAPS overview](laps/overview)
- [Use derived credentials on devices](certificates/derived-credentials)
- [S/MIME for email signing and encryption](certificates/s-mime)

### How-To Guide

- [Configure tenant-wide Windows Hello for Business](identity-protection/configure-tenant-wide-policy)
- [Deploy Windows Hello policy to groups](identity-protection/deploy-group-policy)
- [Deploy Intune policies to manage Windows LAPS](laps/deploy-policy)

## Mobile Threat Defense

### Overview

- [Mobile Threat Defense with Microsoft Intune](mobile-threat-defense/overview)

### How-To Guide

- [Enable the Mobile Threat Defense connector](mobile-threat-defense/enable-connector)
- [Create MTD compliance policies](mobile-threat-defense/create-compliance-policy)
- [Add and assign MTD apps](mobile-threat-defense/assign-apps)
- [Create MTD app protection policies](mobile-threat-defense/create-app-protection-policy)
- [Use MTD on unenrolled devices](mobile-threat-defense/enable-unenrolled-devices)