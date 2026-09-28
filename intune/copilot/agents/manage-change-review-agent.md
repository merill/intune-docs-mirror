---
layout: Conceptual
title: Use the Change Review Agent - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/copilot/agents/manage-change-review-agent
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
description: Learn how to use the Change Review Agent in Microsoft Intune.
ms.date: 2026-04-27T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: zinebtakafi
locale: en-us
document_id: d744df4b-9c24-3631-55cd-9ce327baf278
document_version_independent_id: d744df4b-9c24-3631-55cd-9ce327baf278
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/copilot/agents/manage-change-review-agent.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: copilot/agents/manage-change-review-agent
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/copilot/agents/manage-change-review-agent.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 44768b67-658a-ed65-8f6e-ee6720139a3a
---

# Use the Change Review Agent - Microsoft Intune | Microsoft Learn

The [Change Review Agent](change-review-agent) (public preview) is a generative AI feature in Intune. It evaluates Multi Admin Approval requests for PowerShell scripts on Windows devices and provides risk-based recommendations with contextual insights. These insights help administrators understand script behavior and associated risks, so they can decide whether to approve or deny requests more quickly.

After the [agent is set up](change-review-agent#set-up-the-agent), its recommendations can be viewed, and the agent can be run again on demand to refresh its recommendations.

## Prerequisites

Before you start, review the requirements in the [Change Review Agent overview](change-review-agent#prerequisites) article.

## Explore the Change Review Agent

After configuration, manage the agent from the Change Review Agent pane.

In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Agents** &gt; **Change Review Agent**. The agent includes the following three tabs:

- **Overview** - View the agent's current status, suggestions for the top Multi Admin Approval requests, and the records of recent agent activity.
- **Suggestions** - Here you'll find the full list of suggestions for assessed approval requests.
- **Settings** - This tab displays the agent's configuration details.

To learn more about each tab, select the following tabs:

# [Overview](#tab/overview)
The Overview tab includes:

- **Agent status** - Various tiles introduce the agent, detail whether the agent is available and its current run status.
- **Agent suggestions** – This short list highlights the top suggestions for Multi-Admin Approval requests. Recommended actions include approving low-risk requests and rejecting those assessed as high-risk.
- **Activity** – This area displays records of the current and past agent runs.

After the agent completes a run, the Overview tab updates with its top suggestions for Multi Admin Approval requests. This tab shows only a few suggestions at a time; the full list is available on the Suggestions tab. Use either tab to drill down and review or manage recommendations.

![Screenshot of the overview pane of the Change Review Agent.](media/manage-change-review-agent/overview.png)

# [Suggestions](#tab/suggestions)
The *Suggestions* tab shows the full list of requests reviewed by the agent. Suggestions are generated after each agent run and reflect the latest data. Use search and filters to find specific suggestions.

Each suggestion includes columns with these details:

- **Risk threshold** - An assessment of the change request.
- **Resource type** - The type of request, such as PowerShell script
- **Requested by** - The user account that submitted the request.
- **Approval expiration** - The Date when the request expires if no action is taken.
- **Status** - Current status of the request. Requests that require no further action are marked as *Completed*.

![Screenshot of the suggestions tab of the Change Review Agent.](media/manage-change-review-agent/suggestions.png)

# [Settings](#tab/settings)
Use the Settings tab to view details about the agent's identity, current configuration, and requirements. This includes:

- **Agent jobs** - Request types that agent reviews.
- **Identity** - Details about the agents use of a user account as its identity.
- **Required permissions** – Role-based access controls required to configure or use the agent.
- **Plugins** – Components the agent uses during evaluation.

![Screenshot of the settings tab of the Change Review Agent.](media/manage-change-review-agent/settings.png)

---

## Run the Change Review Agent

Run the agent to refresh recommendations and evaluate new Multi Admin Approval requests. The agent runs until evaluation completes; you can't stop or pause it.

The agent uses the identity and permissions of the assigned Intune admin account. Its operations are limited to the permissions of that account. If the agent doesn't run for 90 consecutive days, its authentication expires and subsequent runs fail until the identity is renewed.

The agent doesn't support scheduled runs and must be started manually each time you want to update its results.

**To manually run the Change Review Agent:**

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Agents** &gt; **Change Review Agent**.
2. Select **Run**, located above the agent's tab selection.

## Manage agent suggestions

Use the Change Review Agent node to review and manage (approve or reject) Multi Admin Approval script requests.

Tip

When Multi Admin Approval protects PowerShell script deployments, agent suggestions for those script approval requests are also available inline in the **Multi Admin Approval** node. On the **My requests** and **All requests** tabs, an **Agent Response** column displays when a suggestion is available. Select the suggestion to open and complete the approval workflow without leaving Multi Admin Approval. For more information, see [Change Review Agent suggestions in Multi Admin Approval](../../fundamentals/role-based-access-control/multi-admin-approval#change-review-agent-suggestions-in-multi-admin-approval).

To review and manage a request that's been evaluated by the agent, select an agent suggestion from the **Suggested Next Steps** column in either the *Overview* or *Suggestions* tab. Intune opens a new window showing the detailed results of the agent's review for that request. The detailed view is named after the selected suggestion and includes the agent's recommendation followed by the name of the request. For example, the following image shows the upper part of the review details for a request named *ReputationScoreScript*, which the agent recommends rejecting:

![Screenshot of the details for a rejected request.](media/manage-change-review-agent/reject.png)

The following are the agent recommendations you might see:

- **Approve** – A low-risk request assessed as safe to approve.
- **Reject** – A high-risk request that shouldn't be approved.
- **Needs more info** – The risk couldn't be fully assessed, and the request requires careful admin review.

When you open an agent suggestion, the review page is divided into two main areas. Each area provides specific information to help you understand the recommendation.

Tip

Near the end of this section are details for the *View request* button. You can use this button to open the Multi Admin Approval request and then *approve* or *reject* it. The final decision to approve or reject a request always remains with the admin.

- **Details tile**

    On the right side, this tile displays metadata related to the agent suggestion.
- **Main tile**

    On the left side, this tile displays the following sections and information:

    - **Suggested action:** This section provides a summary of the agent's review, including key details to help you decide whether to accept or reject the request. It outlines the rationale behind the assessment and includes a brief overview of the script.
    - **Factors:** Factors are the specific details and conditions the agent considered when evaluating the script.
    - **Additional resources and feedback:**

        Below the *Factors* section, you'll find:

        - Links to relevant content for the skills the agent used during evaluation.
        - A simple feedback system to share your input on the agent's results.
    - **View request:** This button opens a review window for the current request. The review window provides the same options available in the *Multi Admin Approval* node of the admin center

        - Use the *Approver note* to explain your decision for this request.
        - Complete the approval process by selecting **Approve request** or **Reject request**.

        After you approve or reject the request, the agent suggestion status changes to **Completed**.

## Agent logs

Security Copilot logs include all agent management actions and permission failures. Logs don't include recommendation details or completion times.

## Common errors

While the agent run might fail due to insufficient SCUs, there are other possible errors that can occur. This section lists some common error messages you might encounter while using the agent, along with explanations and suggested actions.

### The agent doesn't provide accurate suggestions

In this case, the agent may not have enough data to generate accurate suggestions, or its settings might not fully align with your organization's environment.

To help improve future suggestions, use the like/dislike buttons ![](../../media/icons/16/like.svg)![](../../media/icons/16/dislike.svg) available on each suggestion to share your feedback.

### You don't have access to this agent - Licenses

**Details:** You don't have the licenses needed to access this agent.

Check the licensing and plugins requirements for this agent, and make sure the necessary licenses and configurations are assigned in your tenant.

### You don't have access to this agent - Workspace

**Details:** You aren't part of the workspace needed to access this agent.

This message indicates that your account doesn't have permission to view or use the [Security Copilot workspace](/en-us/copilot/security/workspaces-overview), which is configured at the time Security Copilot is added to your Tenant. Contact the administrator who installed or manages your Security Copilot subscription for assistance in gaining access, and see [Understand authentication in Microsoft Security Copilot](/en-us/copilot/security/authentication).

### You don't have access to this agent - Permissions

**Details:** You don't have the permissions needed to access this agent.

Review the roles requirements to use the agent. Work with an Intune Administrator to assign your account the required permissions.

### The agent encountered an error and didn't finish the run. Try running the agent again.

**Details:** The agent instance failed to start or successfully complete its run. Details of the failure can't be identified. Despite failing to run or complete, admins can continue to view and manage the agent suggestions from past runs.

If the agent continues to fail, it's possible that its lost authorization for its identity account and can't run until it's reauthorized. Possible reasons for a loss of authorization include but aren't limited to:

- The agent's authorization period of 90 days was reached.
- The user account that the agent was installed with is subject to a policy that requires periodic reauthentication.
- An access token has been revoked.

Agent reauthorization requires that the agent is removed and then set up again.

Warning

When an agent is removed, all existing agent suggestions are deleted. This includes details about suggestions that were marked as *Applied*.

### Security Copilot couldn't retrieve details for this factor at this time

The agent was unable to retrieve details related to the specified factor. The exact reason for this failure is unknown.

### Couldn't complete your request. Security Copilot doesn't currently support that type of request

The agent cannot proceed because the request violates Microsoft's Responsible AI policies. This typically occurs when the system detects a prohibited action, like a prompt injection attempt.