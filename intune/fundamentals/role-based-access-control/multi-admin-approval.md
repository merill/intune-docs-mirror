---
layout: Conceptual
title: Use Multi Admin Approval in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/multi-admin-approval
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- setup
ms.subservice: fundamentals
description: Configure Multi Admin Approval to protect your tenant against the use of compromised administrative accounts in Intune.
ms.date: 2026-07-30T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
ms.reviewer: davidra
locale: en-us
document_id: d4342d05-a199-83c8-90d0-9835e0d6d794
document_version_independent_id: d4342d05-a199-83c8-90d0-9835e0d6d794
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/role-based-access-control/multi-admin-approval.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/role-based-access-control/multi-admin-approval
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/role-based-access-control/multi-admin-approval.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/5fc61396-d075-4560-aece-fdbda73d243f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/ad9437c1-8cda-4537-ad69-b4b263652e13
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: e60a26bb-04a3-6aba-4ec7-cb5ca95f1a95
---

# Use Multi Admin Approval in Intune - Microsoft Intune | Microsoft Learn

To help protect against a compromised administrative account, use Microsoft Intune Multi admin approval *access policies* to require that a second administrative account approves a change before the change is applied. This capability is known as Multi Admin Approval.

By using Multi Admin Approval, you can configure access policies that protect specific configurations, like Apps or Scripts for devices. Access policies specify what is protected and which group of accounts can approve changes to those resources.

When you use any account in the tenant to make a change to a resource that's protected by an access policy, Intune doesn't apply the change until a different account explicitly approves it. Only administrators who are members of an approval group that an access protection policy assigns a protected resource to can approve changes. Approvers can also reject change requests.

MAA enforcement applies to both interactive (delegated) admin actions and application-authenticated (app-auth) API calls made through the Microsoft Graph API. If your organization uses service principals, automation scripts, or third-party applications to manage Intune resources via the Microsoft Graph API, those calls are also intercepted by MAA when the target resource is protected by an access policy. For details on how to update your automation to work with MAA, see [Use Multi Admin Approval with the Microsoft Graph API](multi-admin-approval-graph-api). To exclude specific apps from enforcement, see Exclude enterprise applications from an access policy.

Tip

MAA enforcement on API calls made by automation applies only to tenants that already have MAA access policies configured. It doesn't enable MAA or change any tenant's enrollment.

Intune supports access policies for the following resources:

- Apps – Applies to [app deployments](../../app-management/deployment/), but doesn't apply to app protection policies.
- Compliance policies - Applies to creating and managing [compliance policies](../../device-security/compliance/create-policy).
- Configuration policies - Applies to creating and managing policies via the [settings catalog](../../device-configuration/settings-catalog/).
- Device actions - Applies to [wipe](../../device-management/actions/wipe), [retire](../../device-management/actions/retire), and [delete](../../device-management/actions/delete) device actions.
- Role-based access control – Applies to changes to roles, including modifications to role permissions, admin groups, or member group assignments.
- Scripts – Applies to deploying scripts to devices that run [Windows](../../device-management/tools/run-powershell-scripts-windows).
- Tenant Configuration - Applies to managing [device categories](../../device-management/create-device-categories), including creating, editing, or deleting them.

Changes to access policies require a second administrator's approval. Because this resource type is automatically protected, it isn't available as a selectable profile type when you create an access policy.

## Prerequisites for access policies and approvers

To use Multi Admin Approval, your tenant must have at least two administrator accounts. The MAA workflow has three distinct roles, each with different permission requirements:

### Administrator licensing

By default, the administrators who participate in the MAA workflow must have an Intune license assigned to their account. To allow unlicensed administrators to participate in the MAA workflow, enable the **Allow access to unlicensed admins** setting.

Caution

**This setting is irreversible.** Once enabled, you can't turn it off. Make sure your organization understands this limitation before proceeding.

Before enabling this setting, review [Unlicensed admins](../licensing#unlicensed-admin-access) for important limits and behavior details, including group membership caps and how long access changes take to take effect.

### Role 1: Access policy manager

To create and manage access policies, use an account with one of the following options:

- **Custom Intune role** (recommended): Use a [custom role](create-custom-role) that includes the following [Multi Admin Approval permissions](create-custom-role#multi-admin-approval):

    | Permission | Description |
    | --- | --- |
    | *Create access policy* | Create new MAA access policies |
    | *Read access policy* | View existing MAA access policies |
    | *Update access policy* | Modify existing MAA access policies |
    | *Delete access policy* | Remove MAA access policies |
- **Intune Administrator**[![](../../media/icons/16/privileged-label.svg)](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions?tabs=admin-center) (also known as **Intune Service Administrator**): This Microsoft Entra role provides full read/write access to Intune. Because it's a [privileged role](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions?tabs=admin-center), Microsoft recommends using a least-privileged custom Intune role for routine access policy management instead of this role. To learn more, see [Microsoft Entra built-in roles - Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator).

### Role 2: Approver

To approve or reject MAA requests submitted by other admins, an account must meet all of the following requirements:

1. **Approver group membership**: The account must be a member of the approver group that's assigned to the access policy for the specific resource type.
2. **Intune role permission**: The approver account must have the resource-specific *Read* permission for the policy type they're approving. For example, to approve a request for a device delete action, the approver must have *ManagedDevices/Read*. For a full list of available permissions, see [Custom role permissions](create-custom-role#custom-role-permissions).
3. **RBAC role assignment for the group**: The approver security group itself must be added as a member group to at least one Intune role assignment. If the approver group isn't added to a role assignment, approver group members are removed from the group periodically.

    Important

    The approver group has two requirements:

    - It must be a **security group**. Distribution lists, Microsoft 365 groups, and mail-enabled security groups aren't supported and silently fail to resolve approver membership.
    - It must be directly assigned to an RBAC role in Intune as a member group. Intune role permissions held by individual members, whether through other groups or direct user assignments, don't satisfy this requirement.
    - Users must be direct members of the assigned groups. Nested group memberships may result in unreliable behavior.

### Role 3: Change requestor

To submit change requests and complete approved changes for protected resources, an administrator needs the standard Intune RBAC permissions for the specific action they're performing. The same account performs both steps — submitting the initial request and selecting **Complete** after approval by another admin. For example, *MobileApps/Create* to create an app, or *RemoteTasks/Wipe* to wipe a device.

Note

- An administrator can't approve their own requests, even if they're a member of the approver group. A different administrator must approve the request.
- Changes submitted by a Global Administrator or Intune Administrator account must still be approved by a different administrator.

## How Multi Admin Approval and Access policies work

When an admin edits or creates a new object for an area that's protected by an access policy, they see an option on the *Save + Review* surface where they can enter a description of the change as a *business justification*.

- The *business justification* becomes part of the approval request for the change.
- An admin who submitted a change can view the status of their requests in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) by going to **Tenant administration** &gt; **Multi Admin Approval** and viewing the **My requests** page.

After a change is submitted, an *approver* can navigate to the **All requests** page of the **Multi Admin Approval** node, or go to **Tenant administration** &gt; **Admin Tasks** to manage the requests. Both locations provide the list of requests that are active, or recently managed. This view provides some details about the request including when and who submitted it, the type of operation involved like *Create* or *Assign*, and its status. To manage the request:

- The approver selects the *Business justification* link for the request. This action opens the Access policy request pane where you can view more information about the change, including the full details provided in the Business justification field of the request.
- On the Access policy request pane, the approver can enter notes in the **Approver notes** field, and then select an option to **Approve request** or **Reject request**. These notes are added to the request and are visible to the individual who requested the change when they review their requests on the **My requests** page. For example, if the request is rejected, the reason for the rejection can be passed back to the requestor through the Approver notes.
- Individuals who submit a request and are also members of the approval group for that can see their own requests on the All requests page. However, they can't approve their own requests.

### Change Review Agent suggestions in Multi Admin Approval

When the [Change Review Agent](../../copilot/agents/change-review-agent) is set up and has completed a run, the **My requests** and **All requests** tabs display an **Agent Response** column for Windows PowerShell script requests. When a suggestion is available, you can select it to open and complete the Change Review Agent's approval workflow for that request without leaving the Multi Admin Approval node.

Change Review Agent suggestions continue to be available in the [agent's primary experience](../../copilot/agents/manage-change-review-agent) as well. For more information about the agent, see [Change Review Agent overview](../../copilot/agents/change-review-agent).

If a change is approved, Intune processes the requested change and updates the object. While Intune processes the request, its status can display as **Approved**. The original requestor needs to view the request, and choose **Complete** to initiate the change. After being successfully processed, the status updates to **Completed**.

If a request isn't processed further within 3 days, it becomes **Expired**, and must be resubmitted. Each change of status remains visible for up to 30 days after the status changes.

## Create an access policy

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Tenant administration** &gt; **Multi Admin Approval** &gt; **Access policies** &gt; select **Create**.
2. On *Basics*, enter a *Name*, and optional *Description*. For *Profile type*, select from available options. Each policy supports a single profile type.
3. On *Approvers*, select **Add groups** and then select a group as the group of approvers for this policy. More complex configurations that exclude groups aren't supported.
4. On *Exclusions*, optionally select **Add enterprise applications** to exclude specific enterprise applications that use app-auth tokens from MAA enforcement for this policy. Excluded applications can modify protected resources without going through the approval workflow. For more information, see Exclude enterprise applications from an access policy.
5. On *Review + submit for approval*, review the policy summary including the basics, approvers, and any exclusions. Enter a *Business justification*, and then select **Submit for approval**.
6. Next, use a separate administrative account with **Approval for Multi Admin Approval** permission to sign in to the admin center to review and approve the new access policy.
7. Sign back in to the admin center with the first admin account that created the access policy, view the policy, and finalize it by selecting **Complete**. After Intune applies this policy, configurations for the protected profile type require multiple admin approvals.

### Exclude enterprise applications from an access policy

When you create or edit an access policy, you can exclude specific enterprise applications from MAA enforcement for that policy. Excluded applications can modify the protected resource type without going through the approval workflow.

Important

Exclusions apply only to app-auth (application-authenticated) calls. Calls made with delegated authentication are always subject to MAA enforcement, even if the application is excluded.

Warning

Excluding an application bypasses MAA protection for the affected resource type. Each exclusion creates a gap in your approval workflow that could be exploited if the excluded application is compromised. Only exclude applications when necessary, and review your exclusion list regularly to remove entries that are no longer needed.

Keep the following details in mind:

- **Per-policy scope** — Each exclusion applies only to the access policy where it's configured. An exclusion in one access policy doesn't affect other policies or workloads.
- **Limit** — App exclusions are capped at 50 applications per access policy.
- **Approval required** — Adding, removing, or modifying exclusions requires approval by a second administrator, just like other access policy changes.
- **Audit logging** — All add, remove, and modify actions on the exclusion list are captured in the Intune audit log.

## Submit a request

To submit a request when Multi Admin Approval is enabled, use your normal process to create or edit a resource.

On the final page before you can save your changes, add details to the *Business justification* field, and then submit the request. For urgent requests, consider reaching out to a known list of approvers to ensure your request is seen in a timely manner.

When a request for the same object is already pending approval, you can't submit your request. Intune displays a message to alert you to this situation.

To monitor the status of your requests, in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) go to **Tenant administration** &gt; **Multi Admin Approval** &gt; **My requests**.

You can cancel a request before it's approved by selecting it from the **My requests** page, and then selecting **Cancel request**.

## Approve requests

1. To find requests to approve, in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) go to **Tenant administration** &gt; **Multi Admin Approval** &gt; **Received requests**.
2. Select the *Business justification* link for a request to open the review page where you can learn more about the request, and manage approval or rejection.
3. After reviewing the details, enter relevant details in the **Approver notes** field, and then select **Approve request** or **Reject request**.
4. After you approve a request, the requestor needs to select **Complete**. Intune processes the change, and changes the status to *Completed.* Verify the approval succeeded (or failed) by reviewing the console notification upon completion.

    To verify if the approval succeeded (or failed), look at the notifications in the Intune admin center. A message shows if the approval succeeded or failed.

Tip

You can also manage these tasks from the centralized [**Admin tasks**](../../device-management/admin-tasks) pane in the Intune admin center.

## More considerations

- Intune doesn't send notifications when new requests are created, or the status of an existing request changes. When you submit an urgent change request, contact individuals who have permission to approve those requests.
- Monitor the status of your requests through the *My requests* page of the *Multi Admin Approval* node in the Intune admin center.
- When an approval is already pending for an object, you can't submit a new request for it.
- All actions for a protected resource are protected, including but not limited to:

    - Edit
    - Create
    - Modify
    - Delete
    - Assign
- Intune audit logs record actions for requests and the approval process. For more information, see [Audit logs for Intune activities](../../governance/monitor-audit-logs).
- The following status conditions are available for a request:

    - Needs approval – This request is pending action by an approver.
    - Approved – This request is being processed by Intune.
    - Completed – This request has been successfully applied.
    - Rejected – This request was rejected by an approver.
    - Canceled – This request was canceled by the admin who submitted it.
- Be cautious when creating an access policy for the **Role** policy type. This policy type protects all role-related changes, including creating, updating, and deleting RBAC roles and role assignments. Once active, any attempt to modify roles, including the RBAC assignments that MAA itself requires, needs MAA approval first. This requirement can create a deadlock situation where you can't configure the RBAC assignments needed for MAA to function.

    If you experience this deadlock:

    1. Go to **Tenant administration** &gt; **Multi Admin Approval** &gt; **Access policies**.
    2. Find and delete the access policy configured for the **Role** policy type.
    3. Wait 3–5 minutes for the change to propagate.
    4. Go to **Tenant administration** &gt; **Roles** and complete the required RBAC role assignments, adding the approver group to a role assignment.
    5. After RBAC is configured correctly, you can re-create the **Role** access policy if desired.

    To avoid this issue, configure all other MAA access policies and verify RBAC assignments are correct before enabling an access policy for the **Role** policy type.