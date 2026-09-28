---
layout: Conceptual
title: Windows Autopilot Enrollment Status Page | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/enrollment-status
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Gives an overview of the Enrollment Status Page capabilities, configuration.
ms.date: 2025-06-13T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: article
locale: en-us
document_id: 17160996-84b0-a222-39a5-80d58643f75a
document_version_independent_id: 17160996-84b0-a222-39a5-80d58643f75a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/enrollment-status.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: enrollment-status
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/enrollment-status.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 7dfd05e9-4738-1e7b-3760-d88dd783466a
---

# Windows Autopilot Enrollment Status Page | Microsoft Learn

When a user signs into a device for the first time, the Enrollment Status Page (ESP) displays the device's configuration progress. The ESP also makes sure the device is in the expected state before the user can access the desktop for the first time.

The ESP tracks the installation of applications, security policies, certificates, and network connections.

## ESP profiles

An administrator can deploy ESP profiles to a licensed Intune user and configure specific settings within the ESP profile. A few of these settings include:

- Force the installation of specified applications.
- Allow users to collect troubleshooting logs.
- Specify what a user can do if device setup fails.

For more information, see [Set up the Enrollment Status Page](/en-us/intune/intune-service/enrollment/windows-enrollment-status).

![Screenshot that shows Enrollment Status Page](images/enrollment-status-page.png)