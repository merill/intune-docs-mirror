---
layout: Conceptual
title: Check device status on Intune Company Portal website - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/compliance/validate-status-company-portal-website
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Check device status to verify whether or not your device has access to work resources.
ms.date: 2024-11-08T00:00:00.0000000Z
ms.reviewer: 
locale: en-us
document_id: 2199c85c-fea4-1593-ded4-d258959ad18b
document_version_independent_id: 2199c85c-fea4-1593-ded4-d258959ad18b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/compliance/validate-status-company-portal-website.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/compliance/validate-status-company-portal-website
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/compliance/validate-status-company-portal-website.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 540d338f-9d04-409d-4de9-1be1911300fe
---

# Check device status on Intune Company Portal website - Microsoft Intune | Microsoft Learn

**Applies to:**

- Android
- iOS/iPadOS
- macOS
- Windows

Remotely check the status of a device from the Company Portal website. During a status check, Company Portal assesses the selected device to determine whether or not it has work access.

## Check status

To check the status of a device:

1. Sign in to the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).
2. Go to **Devices**, and then select your device.
3. Under **Status**, select **Check status**. Wait while Company Portal checks your device.

## Device status

After the check, the status updates to show the most current state of your device.

- **Can access**: Your device is allowed to access work or school resources.
- **Out of compliance - can still access company resources**: Your device is allowed to access work or school resources, but one or more settings don't meet your organization's requirements. Update your device settings by the date shown to keep your access.
- **Cannot access company resources**: Your device isn't allowed to access work or school resources. Make the required changes to gain access.

The specific requirements and next steps are determined by your organization's policies. If you're required to make any changes to your device, Company Portal will include that information next to the device status.