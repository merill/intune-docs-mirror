---
layout: Landing
title: Device management - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/
summary: Perform operational actions on managed devices, run scripts and remediations, view device inventory, and generate reports in Microsoft Intune.
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
description: Run remote actions, manage scripts and remediations, view device inventory, and export reports in Microsoft Intune.
ms.topic: landing-page
ms.date: 2026-05-04T00:00:00.0000000Z
locale: en-us
document_id: 9f5f6047-408e-4808-f908-a6b7760e5b2c
document_version_independent_id: 9f5f6047-408e-4808-f908-a6b7760e5b2c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/index.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: landing
toc_rel: ../toc.json
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/index.yml
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: d9727cf6-dc68-e694-dd06-affe02ad8529
---

# Device management

Perform operational actions on managed devices, run scripts and remediations, view device inventory, and generate reports in Microsoft Intune.

## Deployments (preview)

### Concept

- [Deployments overview](deployments/overview)

### How-To Guide

- [Create a deployment plan](deployments/create-deployment-plan)
- [Create a deployment](deployments/create-deployment)

### Reference

- [Permissions, scope tags, and approvals](deployments/rbac-scope-tags)
- [Known issues (preview)](deployments/known-issues)

## Get started with device management

### Overview

- [Device management overview](overview)

### Concept

- [Manage specialty devices](specialty-devices)

### How-To Guide

- [Create and assign device categories](create-device-categories)

## Run device actions

### How-To Guide

- [Wipe a device](actions/wipe)
- [Retire a device](actions/retire)
- [Sync a device](actions/sync)
- [Restart a device](actions/restart)
- [Find lost devices](actions/locate)
- [Collect diagnostics](actions/collect-diagnostics)
- [Remote lock](actions/remote-lock)
- [Fresh start for Windows devices](actions/fresh-start)

## Manage device passwords and keys

### How-To Guide

- [Reset passcode](actions/reset-passcode)
- [Remove passcode](actions/remove-passcode)
- [Disable Activation Lock](actions/disable-activation-lock)
- [Rotate BitLocker recovery keys](actions/rotate-bitlocker-keys)
- [Rotate FileVault recovery key](actions/rotate-filevault-recovery-key)
- [Rotate recovery lock passcode](actions/rotate-recovery-lock-passcode)

## Use scripts and remediations

### Concept

- [Understand the Intune Management Extension](tools/management-extension-windows)

### How-To Guide

- [Use remediations to detect and fix issues](tools/deploy-remediations)
- [Add PowerShell scripts to Windows devices](tools/run-powershell-scripts-windows)
- [Use shell scripts on macOS devices](tools/run-shell-scripts-macos)

### Reference

- [PowerShell scripts for remediations](tools/ref-remediation-scripts)

## View device inventory and status

### How-To Guide

- [Change a device's primary user](inventory-and-status/find-primary-user)
- [View device details](inventory-and-status/device-details)
- [View ChromeOS device information](inventory-and-status/chrome-enterprise-details)

### Concept

- [Surface Management Portal overview](tools/surface-management-portal)

## Generate and export reports

### How-To Guide

- [Microsoft Intune reports](reports/overview)
- [Export reports using Graph APIs](reports/export-graph-apis)

### Reference

- [Graph API report properties](reports/ref-graph-available-reports)

## Integrate with external services

### How-To Guide

- [Remote Help with ServiceNow](tools/setup-servicenow)
- [Set up TeamViewer integration](tools/setup-teamviewer)
- [Remotely administer devices with TeamViewer](tools/teamviewer-legacy)