---
layout: Conceptual
title: Frequently asked questions for Endpoint Privilege Management - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/epm/frequently-asked-questions
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: mikedano
ms.subservice: suite
description: A list of frequently asked questions for customers deploying Microsoft Intune Endpoint Privilege Management
ms.date: 2026-01-26T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 62dc328d-1698-4c0c-5c45-15aedad73204
document_version_independent_id: 62dc328d-1698-4c0c-5c45-15aedad73204
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/epm/frequently-asked-questions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: epm/frequently-asked-questions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/epm/frequently-asked-questions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/7814ca69-56be-4667-8a46-86327796c328
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/f15dfcd0-2664-48ba-bb88-f1f86eadbfd1
platformId: 5a26ec00-c17c-9d2b-77c2-c73594c868b2
---

# Frequently asked questions for Endpoint Privilege Management - Microsoft Intune | Microsoft Learn

The following sections of this article discuss frequently asked questions for Endpoint Privilege Management (EPM).

## Frequently asked questions

### Is my virtual device supported for onboarding to Endpoint Privilege Management?

Endpoint Privilege Management is supported with the following virtual devices:

- Azure Virtual Desktop single-session virtual machines (VMs), added in January 2026.
- Windows 365, added in September 2023.

### Why is my elevation settings policy showing error/not applicable?

The elevation settings policy controls the enablement of EPM and the configuration of the client side components. When this policy is in error or shows not applicable, it indicates the device had an issue enabling EPM. The two most common reasons are missing the [required Windows updates](deployment-planning#prerequisites) or failure to communicate with required [Intune Endpoints for Endpoint Privilege Management](../fundamentals/endpoints#microsoft-intune-endpoint-privilege-management).

### What happens when someone with administrative privileges uses a device that is enabled for EPM?

Endpoint Privilege Management doesn't manage elevation requests by users that have administrative permissions on a device. If an administrator launches a file with a matching elevation rule, the application launches as it normally does for the administrator and is reported as an unmanaged elevation.

### What files can be elevated to administrator?

Endpoint Privilege Management supports executable files with `.exe``.msi` extensions and `.ps1` PowerShell scripts.

### Why doesn't 'Run with elevated access" show on start menu items?

Certain items that reside in the start menu or taskbar have a curated right-click menu and the EPM right-click context menu isn't able to be added to those menus. We plan to fix this issue in a future release.

### Can I launch multiple files as elevated with the "Run with elevated access" right-click context menu?

Only one file can be elevated at a time. To launch multiple files elevated, right-click each file individually and select *Run with elevated access*.

### What is the difference between Microsoft EPM and Windows Administrator protection?

EPM allows standard users to perform tasks that require elevated privileges without granting them full admin rights. Windows Administrator protection secures admin accounts from token theft.

### Do I need additional licensing for EPM?

Yes, Endpoint Privilege Management requires specific licensing. For more information, see [Microsoft Intune advanced capabilities](../fundamentals/advanced-capabilities).

### How does EPM and Windows Defender Application Control (WDAC) differ?

EPM and WDAC compliment each other. EPM allows apps to elevate, while WDAC ensures only approved/blocked apps (elevated or not) can run.