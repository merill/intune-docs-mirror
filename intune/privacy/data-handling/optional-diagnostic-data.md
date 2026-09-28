---
layout: Conceptual
title: Optional diagnostic data that is collected by Intune client apps - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/privacy/data-handling/optional-diagnostic-data
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
description: Learn about the optional diagnostic data that Intune Client apps collect.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: angerobe
ms.collection:
- M365-identity-device-management
- privacy
- sub-data-privacy
locale: en-us
document_id: f929fe10-2915-71ec-2992-605ffa060076
document_version_independent_id: f929fe10-2915-71ec-2992-605ffa060076
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/privacy/data-handling/optional-diagnostic-data.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: privacy/data-handling/optional-diagnostic-data
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/privacy/data-handling/optional-diagnostic-data.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 661e9059-0ff6-9421-446c-b9807574d9b4
---

# Optional diagnostic data that is collected by Intune client apps - Microsoft Intune | Microsoft Learn

Intune collects various optional data to detect, diagnose, and fix problems from users through various Intune client apps. These optional diagnostic data we collect help to proactively detect problems in your organization so they can be addressed before they become an issue. Intune client apps include:

- iOS/iPadOS Company Portal
- macOS Company Portal
- Windows Company Portal
- Android Company Portal
- Android Intune app
- Microsoft Intune Management Agent for macOS
- Microsoft Intune Management Extension
- Android Mobile App Management (MAM)

The optional data collected from clients aren't required to successful run Intune services. The data collected helps:

- Provides enhanced information to help us proactively detect, diagnose, and fix issues.
- Makes product and service improvements.

## Data collected

Optional diagnostic data collected by Intune client apps may cover the following areas:

- Microsoft-generated user information
    - Microsoft Entra user ID
    - Device ID
    - Correlation ID
    - App Session ID
    - User Session ID
- Admin and account information
    - Tenant ID
    - Microsoft Entra tenant ID
- Hardware and software information
    - Device OS version
    - Device model
    - Device make
    - Application ID
    - User language
    - User time zone
- Service events and error information
    - Enrollment event
    - Failure event
        - Network failure
        - Runtime failure
        - Task schedule failure
        - Enrollment failure
        - Microsoft Entra authentication failure
    - Crash report
    - Consent state
    - Compliance status
    - Policy status
- Company Portal events
    - Company Portal error
    - Company Portal page action
    - Company Portal page view
    - Company Portal version
- Performance measurement
    - Duration
    - Response time

## Data not collected

The data do not include any customer information, like:

- Device name
- Phone number
- Contents to the user's files or photo.

## Turn off data collection

We think there are compelling reasons for people to share this optional data. All optional diagnostic data Microsoft collects during the use of any Microsoft 365 Apps for enterprise applications and services is pseudonymized as defined in the ISO/IEC 19944-1:2020 (section 8.3.3) standard.

Users can [turn off usage data collection](../../user-help/privacy/disable-usage-data-collection-android) for their individual devices.