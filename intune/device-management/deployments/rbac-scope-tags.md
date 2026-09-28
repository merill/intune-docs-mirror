---
layout: Conceptual
title: Permissions, scope tags, and approvals for deployments in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/deployments/rbac-scope-tags
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: wicale
ms.collection:
- M365-identity-device-management
description: Learn about RBAC permissions, scope tag behavior, and Multi Admin Approval for deployment plans and deployments in Microsoft Intune.
ms.date: 2026-08-26T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: wicale
locale: en-us
document_id: 99d167b3-03f9-98a7-0faf-4d0fbcae3094
document_version_independent_id: 99d167b3-03f9-98a7-0faf-4d0fbcae3094
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/deployments/rbac-scope-tags.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/deployments/rbac-scope-tags
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/deployments/rbac-scope-tags.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
platformId: 1346938f-7b95-8984-67bc-59389b73b79c
---

# Permissions, scope tags, and approvals for deployments in Microsoft Intune - Microsoft Intune | Microsoft Learn

Note

This feature is in public preview. For more information, see [Public preview in Microsoft Intune](../../fundamentals/public-preview).

This article describes role-based access control (RBAC) permissions, scope tag behavior, and Multi Admin Approval for deployment plans and deployments. For general information about Intune RBAC, see [Role-based access control with Microsoft Intune](../../fundamentals/role-based-access-control/overview).

## Deployment plan permissions

The following permissions are available for deployment plans:

| Permission | Action | Description |
| --- | --- | --- |
| Deployment plan | Create (C) | Create a plan |
| Deployment plan | Read (R) | Read a plan |
| Deployment plan | Update (U) | Edit or modify a plan |
| Deployment plan | Delete (D) | Delete a plan |

Intune built-in roles include deployment plan permissions that align with each role's management category, such as device configurations or mobile apps, and its supported actions. For example, the **Policy and Profile Manager** role has CRUD permissions for device configurations, so it also has CRUD permissions for deployment plans.

Deployment plan permissions are included in the following built-in roles:

| Built-in role | Deployment plan permissions |
| --- | --- |
| Application Manager | Create, Read, Update, Delete |
| Read Only Operator | Read |
| Endpoint Security Manager | Create, Read, Update, Delete |
| Help Desk Operator | Read |
| Policy and Profile Manager | Create, Read, Update, Delete |
| School Administrator | Create, Read, Update, Delete |

## Deployment permissions

Deployments don't have a dedicated permission. Permissions are based on the selected payload's category.

| Action | Payload type | Required permission |
| --- | --- | --- |
| Create a deployment | Device configuration | Read and Assign permissions for the **Device configurations** category |
| Create a deployment | Apps | Read and Assign permissions for the **Mobile apps** category |
| View a deployment | Device configuration | Read permission for the **Device configurations** category |
| View a deployment | Apps | Read permission for the **Mobile apps** category |

## Scope tags

Scope tags control object visibility in Intune. Administrators can only view objects that have scope tags within their assigned scope.

| Action | Scope tags enforced | Behavior |
| --- | --- | --- |
| View deployments in the **Deployments** list | Yes | An administrator can only see deployments whose payload is within the administrator's scope. |
| View plans in the **Deployment plans** list | Yes | An administrator can only see plans within the administrator's scope. |
| Select a payload when creating a deployment | Yes | The payload list only displays payloads within the administrator's scope. |

You can assign scope tags directly to deployment plans. You can't assign scope tags to deployments. Because apps and policies support scope tags, the selected payload is the visibility control plane for its deployment.

For general information, see [Use scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

## Multi Admin Approval

Intune deployments support Multi Admin Approval (MAA). When an MAA access policy is configured for a policy type that deployments support, Intune enforces the approval flow. For example, if you create a deployment for a Windows app and an access policy protects the **App Windows** platform, the deployment requires approval.

The following deployment actions trigger an MAA approval flow:

- Create
- Resume
- Cancel
- Delete

Note

An MAA approver needs Read permission for the payload to access the deployment properties link in the approval request.

When a deployment creation request requires approval, the deployment doesn't appear in the **Deployments** list until the approval is complete.

For more information, see [Use Multi Admin Approval in Intune](../../fundamentals/role-based-access-control/multi-admin-approval).