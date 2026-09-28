---
layout: Conceptual
title: Add and assign the Windows Company Portal app for Intune managed devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/add-company-portal-autopilot
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- Windows
ms.reviewer: bryanke
ms.subservice: apps
description: Add and assign the Windows Company Portal app to Intune managed devices.
ms.date: 2025-01-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 81333133-e1ec-f99f-cf9a-a41701b9b68e
document_version_independent_id: 81333133-e1ec-f99f-cf9a-a41701b9b68e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/add-company-portal-autopilot.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/add-company-portal-autopilot
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/add-company-portal-autopilot.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 2f1f9232-95a8-49dc-7b56-4895886b4cbf
---

# Add and assign the Windows Company Portal app for Intune managed devices - Microsoft Intune | Microsoft Learn

To manage devices and install apps, your users can optionally use the Company Portal app. You can assign the Windows Company Portal app directly from Intune using [Microsoft Store app (new)](add-microsoft-store) apps.

## Prerequisites

You can choose to install the **Company Portal** app using the steps below. The Company Portal app will be installed in device context (also known as system-context) when assigned to the Windows Autopilot group and will be installed on the device before the user logs in.

## Create and Assign the Company Portal app

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with your admin account.
2. Select **Apps** &gt; **All Apps** &gt; **Create**.
3. In **Select app type** pane, select **Microsoft Store app (new)** under the **Store app** section.
4. Choose **Select** at the bottom of the page to begin creating an app from the Microsoft Store.
5. Select **Search the Microsoft Store app (new)**.
6. Enter the text **Company Portal**, select **Company Portal**, then choose **Select** at the bottom of the page.
7. Change **Install behavior** to **System**, then select **Next**.
8. Select scope tags as necessary, then select **Next**.
9. To [Assign](assign-groups) the Company Portal app as a required app to your selected device groups, select &gt; **Add Group** (below **Required**) and then select a device group to assign the app. After you've created all the necessary assignments, select **Next**.
10. Review your settings and select **Create**.