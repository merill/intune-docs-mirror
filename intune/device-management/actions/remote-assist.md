---
layout: Conceptual
title: 'Device Action: New Remote Assistance Session - Microsoft Intune | Microsoft Learn'
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/actions/remote-assist
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.reviewer: mattcall
ms.subservice: remote-actions
description: Learn how to use the new remote assistance session action in Intune to offer support to your users.
ms.date: 2025-10-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 1b159660-c25b-c851-2398-5b925ff73073
document_version_independent_id: 1b159660-c25b-c851-2398-5b925ff73073
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/actions/remote-assist.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/actions/remote-assist
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/actions/remote-assist.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
platformId: 4c99a544-9702-d298-f1ca-04f9f193af3f
---

# Device Action: New Remote Assistance Session - Microsoft Intune | Microsoft Learn

Microsoft Intune provides remote assistance capabilities to help IT support teams troubleshoot and resolve issues on user devices. This functionality is available through two integration paths: **Remote Help** (part of the Intune Suite) and **TeamViewer**. Each option offers different features, licensing requirements, and setup steps.

## How It Works

When selecting the **New remote assistance session** action in Intune:

- If your tenant is configured for **Remote Help**, the session will launch using Microsoft's Remote Help app.
- If your tenant is configured for **TeamViewer**, the session will launch using TeamViewer's remote support interface.

## Learn More

Every solution has its own requirements and options. For more information, see:

- [Use Remote Help with Microsoft Intune](../../remote-help/)
- [Use TeamViewer to remotely administer Intune devices](../tools/teamviewer-legacy)