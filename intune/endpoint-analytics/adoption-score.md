---
layout: Conceptual
title: Endpoint Analytics in Microsoft Adoption Score - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/endpoint-analytics/adoption-score
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.subservice: endpoint-analytics
description: Learn how Microsoft Adoption Score integrates endpoint analytics to provide insights on device performance, startup performance, application reliability, and work-from-anywhere readiness for your organization.
ms.date: 2025-10-09T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: 4c9ae454-2aca-044b-fe5f-8967aa4e3eda
document_version_independent_id: 4c9ae454-2aca-044b-fe5f-8967aa4e3eda
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/endpoint-analytics/adoption-score.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: endpoint-analytics/adoption-score
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/endpoint-analytics/adoption-score.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3ce7bda1-3b6d-8611-a2fd-0d58a0e391ff
---

# Endpoint Analytics in Microsoft Adoption Score - Microsoft Intune | Microsoft Learn

Understanding how devices in your organization contribute to the user's experience is critical to any digital transformation effort. To help you understand this aspect, the Microsoft Adoption Score includes endpoint analytics information. The **Endpoint analytics** page in [Microsoft Adoption Score](/en-us/microsoft-365/admin/productivity/productivity-score) shares organizational level insights with roles outside of Microsoft Intune. The visibility and insights provided in areas like device boot times and application reliability can help your users by highlighting potential issues within your organization. For instance, endpoint analytics can expose a long sign-in process or issues with applications unexpectedly stopping.

## Endpoint analytics page in the Adoption Score report

Endpoint analytics contains great insights, but it requires access to the Microsoft Intune admin center. If you're an Intune Administrator, you can display the analytics. However, other users of Microsoft Adoption Score might be unaware this information exists. Displaying these insights to Microsoft Adoption Score users allows them to use the data to help drive transformation efforts across your organization.

[![Endpoint analytics in the Microsoft 365 admin center](media/adoption-score/endpoint-analytics-microsoft-365-admin-center.png)](media/adoption-score/endpoint-analytics-microsoft-365-admin-center.png#lightbox)

The **Endpoint analytics** page looks similar to the other pages in Adoption Score, making it easy to dive right in. The following information is displayed on the **Endpoint analytics** page:

- The current endpoint analytics score
- Endpoint analytics score over the past 180 days
- Startup performance scores

## About the endpoint analytics scores

The **endpoint analytics score** is a weighted average of the [Startup performance](startup-performance), [Application reliability](app-reliability), and [Work from anywhere](work-from-anywhere) scores.

## Startup performance metrics

Select the **Learn more** link under the startup performance information to get more details and a link to **View more in Microsoft Intune**. The **Startup performance metrics** are averages of the following items:

- **Average device startup time in seconds**

    - **Total boot time**: The combination of the **Group Policy phase** and the **Time to sign-in prompt**
    - **Group Policy phase**: The time spent querying and processing Group Policy
    - **Time to sign-in prompt**: Boot time minus the time spent processing Group Policy
- **Average sign-in time in seconds**

    - **Total sign-in time**: Total time for the **Group Policy phase**, **Time to desktop**, and **Time to responsive desktop**
    - **Group Policy phase**: The time spent querying and processing Group Policy
    - **Time to desktop**: The time it takes to reach the desktop but where background processes are still running, and users experience slower performance
    - **Time to responsive desktop**: Time where background processes are complete and CPU utilization is less than 50%

[![Endpoint analytics startup performance metrics](media/adoption-score/startup-performance-metrics.png)](media/adoption-score/startup-performance-metrics.png#lightbox)

## Application reliability metrics

The chart shows the overall **Application reliability score** for your tenant with the peer benchmark. Select the **Learn more about app reliability** link under the app reliability information to get more details and a link to **View more in Microsoft Intune**. The following **Application reliability** information comes from [Microsoft Adoption Score](/en-us/microsoft-365/admin/productivity/productivity-score):

- **Top apps reducing your score in the last 14 days**
    - **App name**: The app identifier in the file manifest provided by your client devices. The app name is typically in executable (or .exe) format.
    - **App reliability score**: A score between 0 and 100 that represents the relative reliability of the application in your tenant. This score is calculated based on Mean time to failure and Total usage duration (14 days). A score of 0 represents an unreliable app that likely hampers end-user productivity. A score of 100 represents a reliable app that likely contributes to end-user productivity.
    - **Mean time to failure in hours**: The average amount of engagement time that an end user is able to use the application before a crash occurs over the past 14 days. This value is calculated by dividing Total usage duration (14 days) by Total crashes (14 days). By relating usage duration and crash counts, the frequency of crashes across different applications is normalized. Applications without crash events in your tenant over the past 14 days are given a mean time to failure value of `No crash events`.
    - **Active devices**: The total number of your tenant's enrolled devices that launched this app at least once in the past 14 days.

[![Endpoint analytics application reliability metrics](media/adoption-score/application-reliability.png)](media/adoption-score/application-reliability.png#lightbox)