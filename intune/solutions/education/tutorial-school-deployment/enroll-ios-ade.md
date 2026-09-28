---
layout: Conceptual
title: Education device enrollment with Automated Device Enrollment and Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/education/tutorial-school-deployment/enroll-ios-ade
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: scottbreenmsft
ms.author: scbree
ms.subservice: education
description: Learn how to automatically enroll devices through Apple School Manager with Automated Device Enrollment during Setup Assistant on iOS/iPadOS devices.
ms.date: 2024-05-02T00:00:00.0000000Z
ms.topic: tutorial
locale: en-us
document_id: ae2f57e7-842c-ed87-790e-3cb03d3f10d1
document_version_independent_id: ae2f57e7-842c-ed87-790e-3cb03d3f10d1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/education/tutorial-school-deployment/enroll-ios-ade.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/education/tutorial-school-deployment/enroll-ios-ade
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/education/tutorial-school-deployment/enroll-ios-ade.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 81db3523-8e45-ffc9-7cbc-9a86c6ac87be
---

# Education device enrollment with Automated Device Enrollment and Intune - Microsoft Intune | Microsoft Learn

Automated Device Enrollment through Apple School Manager is designed to simplify all parts of iOS devices lifecycle, from initial deployment through end of life. Using cloud-based services, Automated Device Enrollment can reduce the overall costs for deploying, managing, and retiring devices.

From the user's perspective, it only takes a few simple operations to make their device ready to use. The only interaction required from the end user is to set their language and regional settings, connect to a network, and depending on the profile type - verify their credentials. Everything beyond that is automated.

There are two types of enrollment:

- **User affinity**. This enrollment type is designed for devices that have only one user. In this scenario, the user is prompted for credentials during enrollment.
- **No user affinity**. This enrollment type is designed for shared devices and is common in lower grades. In this scenario, no credentials are required to enroll the device. For iPad devices, a configuration called Shared iPad can be applied that allows users to log in with their Managed Apple ID or use a temporary session.

For more information on configuring Automated Device Enrollment, see:

# [Intune](#tab/intune)
[Set up automated device enrollment in Intune](../../../device-enrollment/apple/setup-automated-ios).

# [Intune For Education](#tab/intune-for-education)
[Set up iOS device management](/en-us/intune-education/setup-ios-device-management)

---