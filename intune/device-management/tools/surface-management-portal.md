---
layout: Conceptual
title: Overview of Microsoft Surface Management Portal - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/tools/surface-management-portal
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: apps
description: Learn more about the features and capabilities of Microsoft Surface Management Portal.
ms.date: 2021-10-28T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 9512c6d5-622d-cebe-c5d4-e09810b9b830
document_version_independent_id: 9512c6d5-622d-cebe-c5d4-e09810b9b830
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/tools/surface-management-portal.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/tools/surface-management-portal
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/tools/surface-management-portal.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/062d60c9-ee0f-402e-a046-b4e67c3572d6
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/17d3b3f6-a66e-4c69-9774-14a73c38e669
platformId: 55847c34-8704-e7ad-2e70-d3f53d8b59b3
---

# Overview of Microsoft Surface Management Portal - Microsoft Intune | Microsoft Learn

Microsoft Surface Management Portal is a centralized place in the Microsoft Intune admin center where you can self-serve, manage, and monitor your organization's Intune-managed Surface devices at scale.

Surface Management Portal offers insights about the enrolled Surface devices in your organization, such as warranty eligibility and open support requests. Use it to:

- See all enrolled Surface devices in your organization.
- Drill down into reports, support requests, and individual devices.
- View warranty data and expiration dates.
- Track warranty and support requests.
- Access Microsoft Surface news and resources.

This article describes the main features of Microsoft Surface Management Portal. To access Surface Management Portal, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **All services** &gt; **Surface Management Portal**.

## Monitor

For an overview of Surface devices, support requests, and warranty coverage in your organization, select **Monitor**. You can drill down into any of the information, including:

- **Count**: See the number of enrolled Surface devices by model. Select **View report** for a list of all enrolled devices.
- **Insights**: Get notifications about the state of Surface devices regarding things such as compliance, hardware, and device activity. Select an insight to view all affected Surface devices.
- **Last updated support requests**: Track the status of recently updated support requests. Select a request ID to see details such as who filed the request, when it was created, and what device it pertains to. Select **View all support requests** for a list of all active requests.
- **Warranty and coverage**: Review notifications about the status of your Surface warranties, such as number of expired warranties, and devices eligible for warranty coverage. Select an insight to view all affected Surface devices. Select **View report** to see the coverage status for all Surface devices.
- **News**: Check out the Microsoft Surface IT blog for Microsoft Surface news.

## Warranty and coverage

Warranty information is available for devices enrolled in Microsoft Intune. Select **Warranty and coverage** to manage all of the warranty data that's associated with your Surface devices. You can use the information in this tab to plan for new devices and support requests.

The **coverage status** tracks the expiration and coverage of Surface warranties. Select any status to view and drill down into affected devices. Statuses shown include:

- **Expired**: Number of devices with expired warranties.
- **Covered**: Number of devices still covered under warranty.
- **Expiring**: Number of devices approaching the warranty expiration date.
- **Eligible**: Number of devices eligible for optional coverage.

Links to other resources are provided under **Warranty and coverage resources** and **Customer service and support resources**.

## Support

Select **Support** to access and monitor all Surface support requests. This area is for self-service and troubleshooting, and tracks support activity, including:

- Open requests
- Closed requests
- Last updated support requests

If a Surface device isn't working properly, the Microsoft Surface Diagnostic Toolkit (SDT) for Business can help you find and solve problems. Select **Troubleshoot with SDT** to learn how to install and use SDT to target problems on Surface devices. More support channels are listed under **Resources**.