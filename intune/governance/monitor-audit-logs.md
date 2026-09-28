---
layout: Conceptual
title: Audit changes and events in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/governance/monitor-audit-logs
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
description: Learn how to review audit logs that record Microsoft Intune activities.
ms.date: 2025-03-17T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: c2459e20-cf7f-a333-0782-4fd07a5a367f
document_version_independent_id: c2459e20-cf7f-a333-0782-4fd07a5a367f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/governance/monitor-audit-logs.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: governance/monitor-audit-logs
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/governance/monitor-audit-logs.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 62935837-4f6f-786a-d019-1f2f73cd118e
---

# Audit changes and events in Microsoft Intune - Microsoft Intune | Microsoft Learn

In Microsoft Intune, there are audit logs that include a record of activities that generate a change. For example, the create, update (edit), delete, assign, and remote actions all create audit events.

Administrators can review the audit logs to track and monitor events for most Intune workloads. Auditing is enabled for all customers. It can't be disabled.

## Who can access the data?

Users with the following permissions can review audit logs:

- [Intune Administrator Microsoft Entra role](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)
- Administrators assigned to an Intune role with **Audit data** - **Read** permissions. For a list of built-in Intune roles that have this permission, go to [Built-in role permissions for Microsoft Intune](../fundamentals/role-based-access-control/ref-built-in-roles).

## View the audit logs

You can review audit logs in the monitoring group for each Intune workload, like compliance or Conditional Access.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Tenant administration** &gt; **Audit logs**.
3. A list of the logs is shown. Select a log from the list to see the activity details.
4. If there are many logs, you can:

    1. Select **Date** and enter a start and end date. This date range can show logs for the previous year, month, week, or day.

        ![Filter audit logs by date in Microsoft Intune and Intune admin center.](media/monitor-audit-logs/audit-logs-date-range.png)
    2. Select **Add filters** &gt; **Category**. Select a category from the list, like **Compliance**, **Device**, or **Role**. Then, select **Apply**.
    3. Select **Add filters** &gt; **Activity**. The available options depend on the **Category** you select. Then, select **Apply**.

        For example, if you select the **Compliance** category, your **Activity** filter options look similar to the following image:

        ![Filter audit logs by compliance category and select an activity in Microsoft Intune and Intune admin center.](media/monitor-audit-logs/audit-logs-compliance-category-activity-options.png)

For related information about audit logs, go to:

- [Data storage and processing in Intune](../privacy/data-handling/data-storage-processing)
- [Use audit logs throughout Intune](integrate-azure-monitor#use-audit-logs-throughout-intune)
- [Audit, export, or delete personal data in Intune](../privacy/personal-data/manage-data-requests)

## Route logs to Azure Monitor

Audit logs and operational logs can also be routed to [Azure Monitor](/en-us/azure/azure-monitor/overview). In the Intune admin center, select **Tenant administration** &gt; **Audit logs** &gt; **Export**:

![Export log data to Azure monitor by selecting Export data settings in Microsoft Intune and Intune admin center.](media/monitor-audit-logs/audit-logs-export-data-settings.png)

When you export, a `.csv` file is created and saved locally, possibly in `C:\Users\UserName\AppData\Local\Temp\MicrosoftEdgeDownloads\GUID`.

When looking at the `.csv` file:

- **Initiated by (actor)** includes information on who ran the task, and where it was run.

    For example, if you run the activity in Intune in the Azure portal, then **Application** always lists **Microsoft Intune portal extension**, and the **Application ID** always uses the same GUID.
- The **Target(s)** section lists multiple targets and the properties that were changed.

For more information about this feature, including the prerequisites, go to [send log data to storage, event hubs, or log analytics](integrate-azure-monitor).

## Use Graph API to retrieve audit events

You can also use Graph API to get two years of audit events. For more information, go to [List auditEvents](/en-us/graph/api/intune-auditing-auditevent-list).