---
layout: Conceptual
title: Centrally manage Admin Tasks - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/governance/admin-tasks
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
description: Centrally manage admin tasks in Microsoft Intune. Use the unified Admin tasks view to organize and act on administrative tasks from Device Offboarding, Endpoint Privilege Management, and more.
ms.date: 2026-01-26T00:00:00.0000000Z
ms.topic: article
ms.reviewer: davidra
locale: en-us
document_id: 9843ba70-d5e0-7cff-b00d-e668986ec4e1
document_version_independent_id: 9843ba70-d5e0-7cff-b00d-e668986ec4e1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/governance/admin-tasks.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: governance/admin-tasks
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/governance/admin-tasks.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: e2479895-6462-9770-bfd0-5fb2410ecd82
---

# Centrally manage Admin Tasks - Microsoft Intune | Microsoft Learn

In the Microsoft Intune admin center, the **admin tasks** node provides a centralized view to discover, organize, and act on administrative tasks and user elevation requests. This unified experience helps you focus on what matters most without navigating across multiple nodes.

Admin tasks supports tasks from the following Intune capabilities:

- [Device Offboarding tasks](../copilot/agents/device-offboarding-agent) - Found in the admin center at *Agents &gt; Device Offboarding Agent*.
- [Endpoint Privilege Management file elevation requests](../epm/manage-support-approvals#manage-pending-elevation-requests) – Found in the admin center at *Endpoint security &gt; Endpoint Privilege Management*.
- [Microsoft Defender security tasks](../device-security/microsoft-defender/remediate-vulnerabilities#work-with-security-tasks) - Found in the admin center at *Endpoint security &gt; Security Tasks*.
- [Multi Admin Approval requests](../fundamentals/role-based-access-control/multi-admin-approval#approve-requests) - Found in the admin center at *Tenant administration &gt; Multi Admin Approval*.

## Role-based access control for Admin tasks

Access to tasks in the admin tasks node is based on your Intune role-based access control (RBAC) permissions.The following permission is required to access the Admin tasks pane in the Intune admin center:

- **Organization** &gt; **Read**

When viewing Admin tasks, you can only see and manage tasks permitted by your assigned roles within the task's original source node. For RBAC requirements and related prerequisites specific to each capability, see:

- [Device Offboarding tasks](../copilot/agents/device-offboarding-agent#prerequisites)
- [Endpoint Privilege Management file elevation requests](../epm/manage-support-approvals#rbac-permissions-for-elevation-requests)
- [Microsoft Defender security tasks](../device-security/microsoft-defender/remediate-vulnerabilities#prerequisites)
- [Multi Admin Approval requests](../fundamentals/role-based-access-control/multi-admin-approval#prerequisites-for-access-policies-and-approvers)

## Manage admin tasks in the centralized view

**To review and manage tasks:**

1. Open the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Tenant administration** &gt; **Admin tasks**.
2. Intune displays a consolidated list of tasks that are available to you, based on your RBAC permissions. Use the filter control to adjust the displayed tasks.
3. Select a task from the **Task** column to open its management pane. The pane that opens is the *same interface and workflow* you'd use if managing the task from its original location in the admin center. This ensures a consistent experience whether you're working from the admin tasks node or directly within the source capability.

For task-specific workflows, refer to the documentation for that task type.

**Task list columns:**

The list of available tasks includes the following columns of information:

- **Task** – The name of the task. Select it to open a flyout pane with task details and management options.
- **Source** – Identifies the task type, like a Defender security task, Endpoint Privilege Management elevation request, or Multi Admin Approval request.
- **Status**– Indicates the current state of the task. Values include:
    - **Active** – The task hasn't been managed yet.
    - **Pending** – The task has been accepted but not resolved. For example, a Defender task might require remediation before being marked as complete
    - **Completed** – The task is complete and no further action is needed.
    - **Rejected** – The task was declined.
    - **Expired** – The task expired. Expired tasks are automatically removed after 30 days.
    - **Needs approval** – Indicates a change awaiting approval.
- **Due in** – Shows how much time remains before the task expires (if applicable).
- **Last updated** – The date the task was last modified.
- **Created** – The date the task was created.

Tasks are removed from this view when they are removed from their source node.