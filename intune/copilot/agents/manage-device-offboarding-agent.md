---
layout: Conceptual
title: Use the Device Offboarding Agent - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/copilot/agents/manage-device-offboarding-agent
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
description: Learn how to use the Device Offboarding Agent in Microsoft Intune to identify and offboard devices that are no longer in use.
ms.date: 2025-10-15T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: rishitasarin
locale: en-us
document_id: 9040b2a7-8df8-8bdc-7727-ec32bc3d1f2a
document_version_independent_id: 9040b2a7-8df8-8bdc-7727-ec32bc3d1f2a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/copilot/agents/manage-device-offboarding-agent.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: copilot/agents/manage-device-offboarding-agent
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/copilot/agents/manage-device-offboarding-agent.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
platformId: 6e85202a-0b66-78bf-dfa7-67e34f0a25d0
---

# Use the Device Offboarding Agent - Microsoft Intune | Microsoft Learn

Important

**Starting June 1, 2026, the Device Offboarding Agent will no longer be available.**

Review your existing offboarding processes and transition to previously used device lifecycle and remediation options in Microsoft Intune before this date.

**Device Offboarding Agent timeline**

- **April 30, 2026**: You can't set up the Device Offboarding Agent.
- **June 1, 2026**: The Device Offboarding Agent is removed from the Intune admin center and isn't available.

**What this change means for you**

- You can continue using the Device Offboarding Agent until **June 1, 2026** if it's already set up.
- If you delete the agent between **April 30, 2026** and **June 1, 2026**, you can't set it up again.
- After **June 1, 2026**, the Device Offboarding Agent isn't accessible.

**Recommended actions**

- Complete any active offboarding actions before **June 1, 2026**.
- Avoid creating new dependencies on the Device Offboarding Agent.
- Transition existing offboarding workflows to previously used device lifecycle and remediation options in Intune.

The *Device Offboarding Agent* identifies stale or misaligned devices across Intune and Entra ID, providing actionable insights and requiring admin approval before offboarding any devices. The Device Offboarding Agent complements existing Intune automation by surfacing insights and handling ambiguous cases where automated cleanup may not suffice.

This article provides sample responses to show how the agent helps with device offboarding.

## Before you begin

- This feature is in [public preview](../../fundamentals/public-preview).
- Confirm that your environment meets the prerequisites described in [Get started with the Device Offboarding Agent](device-offboarding-agent).
- The agent won't run if no retire, wipe, or deletion actions occurred in the past 30 days.

## Explore the agent options

After configuration, manage the agent from the Device Offboarding Agent pane.

In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Agents** &gt; **Device Offboarding Agent (preview)**:

- On the **Overview** tab, view the suggestions of devices to offboard, and get more details and remediation steps.
- On the **Suggestions** tab, view the full list of suggestions of devices to offboard, including the completed suggestions.
- On the **Settings** tab, review details about the agent's configuration.

Select a tab to learn more about its purpose and available options.

# [Overview](#tab/overview)
After the Device Offboarding Agent completes a run, the **Overview** tab updates with the agent's list of top suggestions for devices to offboard. The **Overview** tab only displays the suggestions that are *not started* or *in progress*.

The following information is available on this tab:

- The agent's availability and run status.
- Agent suggestions, which are the list of devices to offboard that are *not started* or *in progress*.
- Activity section that tracks the current and past run activity of the agent.

[![Screenshot of the overview pane of the Device Offboarding Agent.](media/device-offboarding-agent/overview.png)](media/device-offboarding-agent/overview.png#lightbox)

# [Suggestions](#tab/suggestions)
Agent suggestions are a list of the top devices to offboard. Suggestions are generated after each agent run based on the latest data. In this tab, you can use search and filters to find specific suggestions.

A suggestion displays the following details:

- Summary of the suggestions.
- Factors that the agent considered when suggesting offboarding these devices.
- Details about the associated suggestions, including the number of devices to offboard, their ownership, and their platform.
- Recommended actions to offboard securely.

[![Screenshot of the suggestions tab of the Device Offboarding Agent.](media/device-offboarding-agent/suggestions.png)](media/device-offboarding-agent/suggestions.png#lightbox)

Important

Follow the recommended actions in the order they're listed to prevent orphaned devices and ensure secure offboarding.

After an admin reviews and completes the recommended actions, they can self-attest to applying those actions by updating the **Manage Suggestions** to complete. Marking a suggestion as complete doesn't trigger any device changes by the agent.

# [Settings](#tab/settings)
Use the **Settings** tab to view the agent's current configuration. You can view details about the agent's identity and tailor the agent outputs to your needs by using the optional **Instructions** field.

[![Screenshot of the settings tab of the Device Offboarding Agent.](media/device-offboarding-agent/settings.png)](media/device-offboarding-agent/settings.png#lightbox)

---

## Run the agent

To start using the Device Offboarding Agent, first run an evaluation of your device inventory. This action resets the agent's suggestions and status. The agent doesn't persist suggestions across runs; re-running clears previous recommendations.

To manually run the Device Offboarding Agent:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Agents** &gt; **Device Offboarding Agent (preview)**.
2. Select **Run**.

The agent runs until it completes its evaluation. You can't stop or pause the process.

Note

Each time the agent runs, it uses the identity and permissions of the Intune administrator it's configured to use.

## Refresh agent view

Select **Refresh** to update the agent's view with the latest data from its most recent run. This action doesn't trigger a new evaluation; it only refreshes the displayed information to reflect any changes since the last run.

## View and act on suggestions

After running the agent, review its findings to see which devices may need offboarding.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Agents** &gt; **Device Offboarding Agent (preview)**.
2. View the agent's suggestions in the **Overview** or **Suggestions** tab.

[![Screenshot of the suggestions tab of the Device Offboarding Agent.](media/device-offboarding-agent/suggestions.png)](media/device-offboarding-agent/suggestions.png#lightbox)

Each offboarding suggestionincludes detailed context and recommended actions. To manage these suggestions:

- View details and take action: Select a suggestion to review its rationale and initiate offboarding steps.
- Update status: Choose **Manage suggestion** to mark the offboarding action as *In progress* or *Completed*.

[![Screenshot of a suggestion of the Device Offboarding Agent showing the details and options.](media/device-offboarding-agent/suggestion.png)](media/device-offboarding-agent/suggestion.png#lightbox)

## Device Offboarding Agent logs

You can track agent activity and troubleshoot issues using the available logs.

All agent management actions (create, delete, run) and any permission failures are available in [Security Copilot logs](/en-us/copilot/security/audit-log). Logs don't include which devices were offboarded or when recommended actions were completed.

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