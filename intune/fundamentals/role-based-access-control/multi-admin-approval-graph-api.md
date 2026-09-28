---
layout: Conceptual
title: Use Multi Admin Approval with the Microsoft Graph API - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/multi-admin-approval-graph-api
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Learn how to update your automation scripts and applications to work with Multi Admin Approval enforcement on app-authenticated API calls in Microsoft Intune.
ms.date: 2026-08-06T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
ms.reviewer: davidra
locale: en-us
document_id: eac0c15d-dc71-b996-6060-ab2f2fba0e97
document_version_independent_id: eac0c15d-dc71-b996-6060-ab2f2fba0e97
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/role-based-access-control/multi-admin-approval-graph-api.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/role-based-access-control/multi-admin-approval-graph-api
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/role-based-access-control/multi-admin-approval-graph-api.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
- https://authoring-docs-microsoft.poolparty.biz/devrel/5fc61396-d075-4560-aece-fdbda73d243f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
- https://authoring-docs-microsoft.poolparty.biz/devrel/ad9437c1-8cda-4537-ad69-b4b263652e13
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 851b3914-a1c0-519f-4823-4c82a7c549f0
---

# Use Multi Admin Approval with the Microsoft Graph API - Microsoft Intune | Microsoft Learn

Multi Admin Approval (MAA) enforces approval workflows on application-authenticated (app-auth) API calls made through the Microsoft Graph API. If your organization uses service principals, automation scripts, or third-party applications to manage Intune resources, those calls are intercepted by MAA when the target resource is protected by an [access policy](multi-admin-approval).

This article explains how to update your automation to work with the MAA approval workflow, and how to exclude specific applications from enforcement when a code change isn't immediately feasible.

Important

MAA is opt-in per workload for every tenant. This enforcement applies only to tenants that have MAA access policies configured. It doesn't automatically enable MAA or change which tenants have MAA. For more information about configuring access policies, see [Use access policies to require multi admin approval](multi-admin-approval).

## What changes for app-auth calls

Previously, only interactive (delegated) admin actions were subject to MAA approval workflows. With this change, automated and scripted calls that use app-only tokens are also intercepted by MAA when the target resource is protected by an access policy.

If your application makes API calls to MAA-protected resources using app-auth and doesn't include the required approval headers, the call returns an HTTP 400 error. The response body indicates that the operation requires Multi Admin Approval.

### Affected resource types

MAA access policies can protect the following resource types. If your app-auth calls target any of these resources and an access policy is active, your automation is affected:

- Apps
- Compliance policies
- Configuration policies
- Device actions
- Role-based access control
- Scripts
- Tenant Configuration

MAA only applies to operations that modify protected resources (POST, PATCH, PUT, DELETE). Read-only operations (GET) aren't affected.

## Prerequisites

- An [app registration](/en-us/entra/identity-platform/quickstart-register-app) with the required Microsoft Graph application permissions for the Intune resources your app manages (for example, `DeviceManagementApps.ReadWrite.All`).
- MAA access policies configured for the relevant workloads. For more information, see [Create an access policy](multi-admin-approval#create-an-access-policy).
- A separate admin account that's a member of the approver group for the access policy. Applications can't approve or reject MAA requests — only interactive admin accounts can approve requests.

## Step 1: Submit a request with a justification header

When MAA is enabled, include a justification header with your request. The `x-msft-approval-justification` header value must be Base64-encoded.

The following example creates a PowerShell script resource in Intune and includes the required justification header:

```http
POST https://graph.microsoft.com/beta/deviceManagement/deviceManagementScripts
Content-Type: application/json
x-msft-approval-justification: YXBwIG9ubHkgdGVzdA==

{
  "displayName": "My Test Script",
  "description": "Testing MAA with app-only token",
  "scriptContent": "V3JpdGUtT3V0cHV0ICJIZWxsbyBXb3JsZCI=",
  "runAsAccount": "system",
  "fileName": "TestScript.ps1",
  "roleScopeTagIds": ["0"]
}
```

Tip

The `x-msft-approval-justification` value is Base64-encoded. For example, `YXBwIG9ubHkgdGVzdA==` decodes to `app only test`. Encode your own justification string before sending.

Without the justification header, the request fails with an error indicating that the `x-msft-approval-justification` header is required.

## Step 2: Handle the approval response

The request returns an HTTP 412 (`Precondition Failed`) with an outer Microsoft Graph error code of `BadRequest`. This response is expected and doesn't indicate a permissions problem — it's how MAA signals that the request was received and is now waiting for approval. The approval-required details are nested in the error message.

The response includes an `x-msft-approval-code` header that you need for the remaining steps. Use the presence of this header together with HTTP 412 as the signal that MAA accepted the request and created an approval request.

Example response:

```json
HTTP/1.1 412 Precondition Failed
x-msft-approval-code: aabb1234-5678-9012-abcd-ef0123456789
Content-Type: application/json

{
  "error": {
    "code": "BadRequest",
    "message": "{\r\n  \"_version\": 3,\r\n  \"Message\": \"Approval Required. Request Approval using the request ID returned as part of the x-msft-approval-code response header. x-msft-approval-code: aabb1234-5678-9012-abcd-ef0123456789 - Operation ID (for customer support): 00000000-0000-0000-0000-000000000000 - Activity ID: <activity-id> - Url: <service-url>\",\r\n  \"CustomApiErrorPhrase\": \"\",\r\n  \"RetryAfter\": null,\r\n  \"ErrorSourceService\": \"\",\r\n  \"HttpHeaders\": \"{\\\"x-msft-approval-code\\\":\\\"aabb1234-5678-9012-abcd-ef0123456789\\\"}\"\r\n}"
  }
}
```

Extract the `x-msft-approval-code` value from the response. Save the original HTTP method, URL, and request body with this value because you must resubmit the same request in Step 4 after approval.

## Step 3: Wait for approval

At this point, the approval request must be reviewed and approved by another administrator in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). Applications can't approve or reject MAA requests — only interactive admin accounts can approve them.

You can query the approval request status at any time by using the approval code:

```http
GET https://graph.microsoft.com/beta/deviceManagement/operationApprovalRequests?$filter=requestId eq 'aabb1234-5678-9012-abcd-ef0123456789'
```

The `status` field indicates the current state of the request. Common values include `needsApproval`, `approved`, `rejected`, and `cancelled`. Wait until the status changes to `approved` before proceeding.

## Step 4: Resubmit with the approval code

After the request is approved, resubmit the original request. Replace the justification header with the `x-msft-approval-code` header and use the approval code from Step 2:

```http
POST https://graph.microsoft.com/beta/deviceManagement/deviceManagementScripts
Content-Type: application/json
x-msft-approval-code: aabb1234-5678-9012-abcd-ef0123456789

{
  "displayName": "My Test Script",
  "description": "Testing MAA with app-only token",
  "scriptContent": "V3JpdGUtT3V0cHV0ICJIZWxsbyBXb3JsZCI=",
  "runAsAccount": "system",
  "fileName": "TestScript.ps1",
  "roleScopeTagIds": ["0"]
}
```

The request completes successfully and the resource is created.

## Exclude an application from MAA enforcement

If you can't immediately update your application to include the approval workflow, you can exclude it from MAA enforcement in the access policy. To configure an exclusion, edit the access policy for the workload your app calls and add the application on the **Exclusions** tab. A second administrator must approve the change before the exclusion takes effect.

Exclusions apply only to app-auth (application-authenticated) calls made by the excluded service principal. Interactive (delegated) admin actions on the same protected resources still require MAA approval.

For more information about exclusions, including scope, limits, and security considerations, see [Create an access policy](multi-admin-approval#create-an-access-policy).

## Monitor MAA activity for app-auth calls

MAA-related events — including approve, block, pass, exclusion add, and exclusion remove — are recorded in the existing Intune audit log. Use the standard [audit log](../../governance/monitor-audit-logs) and Graph API export to see which app-auth calls are going through MAA and how they're being handled.

## Frequently asked questions

### Why are my automation scripts failing?

If your automation calls Microsoft Graph and targets resources protected by an MAA access policy, those calls are intercepted by the MAA approval workflow regardless of whether the script uses delegated or app-only authentication. Update your scripts to include the justification and approval headers described in this article. If your script uses app-only tokens (client-credentials flow), you can also exclude the application from the access policy.

### Does MAA affect read-only API calls?

No. MAA only applies to operations that modify protected resources (POST, PATCH, PUT, DELETE). GET requests aren't affected.

### Can an application approve its own MAA requests?

No. Applications can't approve or reject MAA requests. A separate interactive admin account that's a member of the approver group must approve the request in the Microsoft Intune admin center.

### How do I check if my tenant has MAA enabled?

In the Microsoft Intune admin center, go to **Tenant administration** &gt; **Multi Admin Approval** &gt; **Access policies**. If there are active access policies listed, MAA is enabled for those workloads.

### Can I turn off MAA to stop the enforcement?

MAA access policies can be managed by administrators with the appropriate permissions. However, Microsoft strongly recommends keeping MAA enabled as a security best practice.