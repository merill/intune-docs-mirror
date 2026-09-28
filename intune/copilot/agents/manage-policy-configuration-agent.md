---
layout: Conceptual
title: Use the Policy Configuration Agent to create policies - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/copilot/agents/manage-policy-configuration-agent
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
description: Learn how to use the Policy Configuration Agent in Microsoft Intune to create policies. You can create policies on files you uploaded, natural language prompts, or industry baselines. The Policy Configuration Agent is a feature of Security Copilot in Intune.
ms.date: 2025-11-17T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: aanavath
locale: en-us
document_id: f70a745f-b9b3-9cb3-74e5-b1118b3ce115
document_version_independent_id: f70a745f-b9b3-9cb3-74e5-b1118b3ce115
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/copilot/agents/manage-policy-configuration-agent.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: copilot/agents/manage-policy-configuration-agent
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/copilot/agents/manage-policy-configuration-agent.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
platformId: ecf2b9d5-422e-a0a8-24df-b476cdec03e9
---

# Use the Policy Configuration Agent to create policies - Microsoft Intune | Microsoft Learn

The [Policy Configuration Agent](policy-configuration-agent) is a generative AI feature in Intune. It helps IT admins translate complex requirements and industry standard documents into actionable Intune settings.

After you [set up the agent](policy-configuration-agent), the next step is to upload documents and benchmarks as **knowledge sources**. Or, enter natural language instructions on what to include in the policy draft. The agent analyzes these knowledge sources to suggest relevant Intune settings and then can create device configuration policies using these settings.

This article shows you how to use the Policy Configuration Agent, including:

- Adding, saving, and viewing a knowledge source
- Creating a policy from a knowledge source and natural language prompts

To learn about the agent and how to set it up, see [Set up the Policy Configuration Agent](policy-configuration-agent).

This feature applies to:

- Windows

## Before you begin

- This feature is in [public preview](../../fundamentals/public-preview).
- Make sure you meet the [Policy Configuration Agent](policy-configuration-agent#prerequisites) prerequisites, including signing in with an appropriate account.
- You can upload one knowledge source file at a time. If you have multiple baseline documents, run them separately through the agent.
- Well-structured, well-written input results in better mappings. If a document is poorly formatted or uses unclear language, the agent can produce low-confidence matches. We recommend you review your source documents for clarity.
- You can add text files up to 25 KB in size. Large or complex documents with hundreds of pages of requirements might challenge the agent's ability to process them effectively.

## Use the agent

To use the agent, open the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Agents** &gt; **Policy Configuration Agent**.

The following tabs are available:

# [Overview](#tab/overview)
The **Overview** tab is the landing page for the agent. It provides a summary of the agent's policy suggestions and recent activity.

After the agent completes a run, this tab updates with the agent's suggestions. Only new and in progress policy suggestions are shown.

You can also:

- View the agent's availability.
- View the suggestions based on the information you uploaded or entered. You can select any suggestion to see more details and save the setting mapping for future use.
- View the activity section to see the agent's current and past run activity.

# [Knowledge](#tab/knowledge)
The **Knowledge** tab shows the knowledge sources you uploaded and other important information about the source, like its status.

In this tab, you can:

- Search and filter to find specific knowledge sources.
- View the knowledge source status, like New, In progress, Completed, and Dismissed.
- Select a knowledge source to see all the settings and their recommended values.
- Delete a knowledge source.

# [Suggestions](#tab/suggestions)
The **Suggestions** tab shows a list of the agent's suggestions based on the input you selected, including any natural language prompts. After the agent completes a run, this tab updates with the agent's suggestions.

In this tab, you can:

- Search and filter to find specific suggestions.
- View the suggestion status, like New, In progress, Completed, and Dismissed.
- Select a suggestion to see the settings and their recommended values. When you select a suggestion, you can also save the setting mapping for future use.

# [Settings](#tab/settings)
The **Settings** tab shows the agent's settings, like the required permissions, the identity running the agent, and more requirements. In this tab, you can update the identity running the agent.

---

## Add, save, and view a knowledge source

**Knowledge sources** are files that you upload. These files describe the device configuration requirements in natural language. They can be internal policy documents and baselines, like security and compliance policies and frameworks, industry standards that describe settings, or risk assessment guidelines for device configurations.

For example, you can upload compliance standards and common industry benchmarks, like:

- Security Technical Implementation Guides (STIGs)
- National Institute of Standards and Technology (NIST) guidelines

You can save the agent suggestions so you can create device configuration policies when you're ready.

**To add a knowledge source, use the following steps**:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Agents** &gt; **Policy Configuration Agent**.
2. Select **Create new** &gt; **Knowledge source**.
3. Configure the following settings:

    - **Knowledge source name** - Enter a name for the knowledge source.
    - **Description** - Optional. Enter a description for the knowledge source.
    - **Upload document** - Browse for your file or drag-and-drop the file. The agent supports well-known baseline formats, custom documents, and bulleted lists of requirements.
4. Select **Review**. The agent runs immediately and analyzes the knowledge source you uploaded. Select the link to open it.

    [![Diagram that shows a sample policy draft created with the Copilot Policy Configuration Agent in Microsoft Intune.](media/manage-policy-configuration-agent/suggestion.png)](media/manage-policy-configuration-agent/suggestion.png#lightbox)

    You see suggested settings mapped to the knowledge source you uploaded.
5. In the **Policy details** &gt; **Identified settings** tab, your data is mapped to Intune settings. For each setting, the agent shows:

    - The name of the Intune policy setting
    - The proposed value of the setting
    - The original requirement text it maps to
    - The confidence score for the mapping

    The agent classifies each mapping rule into the following categories:

    - **Supported** – There's a direct Intune setting available. The agent maps the rule to that setting and proposes a configuration.
    - **Unsupported** – There isn't a built-in Intune setting for this requirement. The agent notes that the rule is unsupported, meaning Intune alone can't enforce it. For example, a rule about a very niche OS setting that Intune can't manage would be flagged.

        If any settings are unsupported, then they're listed.

    **We recommend you review and confirm every mapping, especially the low-confidence mappings**.
6. You can also **Save this mapping** to save the suggested mappings and use them in other policies later.

    After you save the mapping, you can choose to create a device configuration profile.
7. After you review the suggestions, select **Manage suggestion**. Use this option to update the suggestion status.

    These statuses are for your tracking purposes only. They help you track the suggestions you reviewed and the suggestions you need to address. The **Dismissed** status removes the suggestion from the **Suggestions** tab.

### View your existing knowledge sources

When you upload a knowledge source, it's available in the **Knowledge** tab. To view your existing knowledge sources, use the following steps:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Agents** &gt; **Policy Configuration Agent**.
2. In the **Knowledge** tab, there's a list of your existing knowledge sources. Select a knowledge source to view its settings and their configured values.
3. You can **Delete** a knowledge source and **Export** its settings.

## Create and view a policy draft

The agent can create a settings catalog device configuration policy based on a knowledge source you uploaded or using a natural language prompt.

To create a policy using the agent, use the following steps:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Agents** &gt; **Policy Configuration Agent**.
2. Select **Create new** &gt; **Policy draft**.
3. Configure the following settings:

    - **Policy name** - Enter a name for the policy draft.
    - **Description** - Optional. Enter a description for the policy.
    - **Knowledge source** - Select the knowledge source you want to use for this policy draft.

        If it's blank, then no knowledge sources are uploaded. Select **add a document** to upload a file that contains your instructions.
    - **Instructions** - In natural language, describe the device configuration settings you want to include in the policy. For example, enter `Create a device configuration policy that enforces strong password requirements and enables BitLocker encryption on Windows devices`.
4. Select **Create**. The agent runs and creates a policy draft based on your selected source.
5. In the **Overview** and **Suggestions** tabs, your policy draft is shown as a suggested next step. Select the draft link.

    An AI Summary describes the policy draft and provides more helpful insights. The policy details show the settings suggested by the agent and its configured values. You can also export the settings as a `.csv` file.

    **In this step, review each setting and its value to ensure they meet your requirements**. You can start with the settings that have a low confidence score.
6. After you review the suggestions, select **Manage suggestion**. Use this option to update the suggestion status.

    These statuses are for your tracking purposes only. They help you track the suggestions you reviewed and the suggestions you need to address. The **Dismissed** status removes the suggestion from the **Suggestions** tab.
7. Select **Create configuration policy** to save the policy draft as a device configuration policy. This step takes you to the settings catalog, and is prepopulated with the agent-generated configuration. The saved policy is shown in **Devices** &gt; **Manage devices** &gt; **Configuration**.

    The agent also automatically adds any required settings to the policy, including parent and child settings. So, the settings count can be different between the agents policy draft and the device configuration policy.

    At this stage, the policy is a normal Intune policy. You can change the policy name, update the policy settings, and assign the policy when you're ready.

    **In this step, review each setting and its value to ensure they meet your requirements**.

### View your existing policy drafts

You can view your existing policy drafts. Use the following steps:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Agents** &gt; **Policy Configuration Agent**.
2. In the **Overview** and **Suggestions** tabs, your policy drafts are shown as suggested next steps. Select a policy draft to view its settings and their configured values.

To update any settings and their values in the policy draft, you must create a device configuration policy from the draft. After you create the policy, you can edit it like any other Intune device configuration policy.

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