---
layout: Conceptual
title: Explore Intune data with natural language and take action - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/copilot/explorer
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.update-cycle: 180-days
description: In Microsoft Intune, use Explorer to query your data in natural language and run built-in queries that match your request. Copilot summarizes the results, and provides recommendations and actions based on the query results. You can also create policies that target users and groups in the query results. Use this feature to explore your Intune data, troubleshoot issues, and create custom reports.
ms.date: 2025-11-11T00:00:00.0000000Z
ms.topic: get-started
ms.reviewer: ankurgoyal, rashok
ms.collection:
- M365-identity-device-management
- security-copilot
- msec-ai-copilot
locale: en-us
document_id: 1c20a841-95a6-77b4-16ca-bb294fcabf77
document_version_independent_id: 1c20a841-95a6-77b4-16ca-bb294fcabf77
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/copilot/explorer.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: copilot/explorer
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/copilot/explorer.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 2601be4d-fad6-d644-5709-20db73884dca
---

# Explore Intune data with natural language and take action - Microsoft Intune | Microsoft Learn

Using natural language and your own words, you can query and explore your Intune data. An intelligent search matches your request to available query views that are built into Intune.

These queries can have parameter inputs that you enter, like the platform or device-specific info. A Copilot summary summarizes the query results and provides recommendations you can consider based on the query results.

This feature can help with situations like finding devices based on your query, identifying users with compliance issues, finding devices that need updates, or finding specific apps or policies. You can use this data to help troubleshoot.

You can also use the query output to add users or devices to groups, and create custom reports. For example, you can find devices that are noncompliant and out of the grace period, and then add those devices to a group. You can then target apps and policies to this group.

## Before you begin

- To explore your data using this capability:

    - Security Copilot must be enabled in your tenant.
    - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has access to Security Copilot with a **Copilot owner** or **Copilot contributor** role.

    To learn more about the prerequisites for using Microsoft Copilot in Intune, see [Microsoft Copilot in Intune overview](./).
- As you explore, the data you see is scoped to your Intune permissions. Some of the data is retrieved from Microsoft Graph using your permissions. If you don't have permissions to view a resource, then it isn't included in the results. Data from Intune and Microsoft Entra are most commonly used.

## Explore your data

The best way to explore is to ask your specific questions in natural language. The intelligent search helps you find a query that matches your request. A Copilot summary with a query explanation and suggestions helps you understand and navigate the results.

There are also built-in examples that help you understand the kinds of questions you can ask. Your search is matched to available query views, with more queries continually being added.

### 1 - Start exploring

In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Explorer**. When it opens, you see a prompt input.

[![Select the Copilot Explorer in the Microsoft Intune admin center.](media/explorer/admin-center-explorer.png)](media/explorer/admin-center-explorer.png#lightbox)

### 2 - Type a request in natural language

In the prompt box, type your request in natural language. When you start typing, a drop-down list of prompts similar to your text is shown. These prompts are built into Intune and list the kinds of questions you can ask.

Select the prompt that best matches your request, or continue typing for more suggestions. For example, start typing `what are the top 5 apps`. As you type, a list of suggestions is shown. Continue typing to make your request more specific. Or, try different natural language text if you don't find what you're looking for.

[![Sample prompt in Copilot Explorer that asks about the top five apps in the Microsoft Intune admin center.](media/explorer/explorer-prompt-apps-example.png)](media/explorer/explorer-prompt-apps-example.png#lightbox)

#### What data can I explore?

You can explore several Intune resources and the relationships between them. The areas you can ask about, the queries, and the query capabilities continue to evolve as we add more data coverage and exploration features. The areas you can explore include:

- [Advanced Analytics](../advanced-analytics/)
- App configuration and app protection
- Apps
- Audit logs
- Compliance
- Device Configuration
- Device updates
- Devices (device properties)
- [Endpoint Privilege Management](../epm/overview)
- Role based access control (RBAC)
- Users and groups
- Windows Autopilot deployments

### 3 - Use the built-in examples

There are also built-in examples that you can use. You can filter the examples by category to find an example that best matches your request. The examples help you understand the types of requests you can make.

[![Select an example or filter the example list by the category in the Microsoft Intune admin center.](media/explorer/explorer-prompt-categories.png)](media/explorer/explorer-prompt-categories.png#lightbox)

The examples include parameter inputs that you enter. For example, if you select the **Compliance** category, there's a list of queries related to compliance. You can select one of the examples, like **Get *Platform* devices that are noncompliant..**. In the prompt, select a platform. The prompt is updated to show the platform.

[![When exploring data, select the compliance example and select the Windows platform in the Microsoft Intune admin center.](media/explorer/explorer-example-compliance-category-platform.png)](media/explorer/explorer-example-compliance-category-platform.png#lightbox)

### 4 - Get results

The **Get results** button runs your query. Copilot summarizes and helps you understand the results, suggests other queries that could help, and recommends actions you can take based on the query results.

[![When exploring data, the Copilot Summary summarizes the query results, and shows suggestions and actions in the Microsoft Intune admin center.](media/explorer/explorer-copilot-summary.png)](media/explorer/explorer-copilot-summary.png#lightbox)

### 5 - Take action

In the query results, you can export the results and select an item that goes to its individual resource page with more information. If your query results are a list of users or devices, you can add them to a group, and target apps and policies to this group.

[![When exploring data, you can export the query results and add users or devices to groups in the Microsoft Intune admin center.](media/explorer/explorer-query-results.png)](media/explorer/explorer-query-results.png#lightbox)

When you add to a group, you can select an existing group or create a new group. When finished, a progress report is automatically created. If you want to keep the report, export it now, as the report isn't available again.

In the following example, a query found noncompliant devices that are past the grace period. These devices are added to a group. Some devices failed to be added to the group, and the **Status detail** shows the reason why. You can use the **Add filters** option to filter the results, like the devices that were successfully added to the group.

[![When exploring data, add the device query results to a group and view the report status in the Microsoft Intune admin center.](media/explorer/explorer-add-to-group-report.png)](media/explorer/explorer-add-to-group-report.png#lightbox)

## Feedback and future updates

This data exploration capability is constantly improving. We continue to add more areas of Intune data that you can explore, more data coverage in each area, more querying capabilities and interaction with Copilot, more Intune data sources, and more actions. We want your feedback as we make improvements, including any capabilities you want to see and missing queries that you need.

[![Submit feedback about the capabilities available to explore data with Copilot in the Microsoft Intune admin center.](media/explorer/explorer-provide-feedback.png)](media/explorer/explorer-provide-feedback.png#lightbox)