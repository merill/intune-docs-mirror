---
layout: Conceptual
title: Learn about Policy Configuration Agent and set it up - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/copilot/agents/policy-configuration-agent
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
description: Learn about the Policy Configuration Agent in Microsoft Intune, its prerequisites, how it works, and how to set it up. The agent is a generative AI feature that helps create Intune policies based on uploaded documents or benchmarks. The Policy Configuration Agent is a feature of Security Copilot in Intune.
ms.date: 2025-11-18T00:00:00.0000000Z
ms.topic: overview
ms.reviewer: aanavath, jubaptis
locale: en-us
document_id: 10843900-73d3-4ed7-b15d-81d16f42b48e
document_version_independent_id: 10843900-73d3-4ed7-b15d-81d16f42b48e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/copilot/agents/policy-configuration-agent.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: copilot/agents/policy-configuration-agent
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/copilot/agents/policy-configuration-agent.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 5d0c8d32-448a-b86e-66e0-075ca346369b
---

# Learn about Policy Configuration Agent and set it up - Microsoft Intune | Microsoft Learn

Important

**Starting August 31, 2026, the Policy Configuration Agent (PCA) and Change Review Agent (CRA) will no longer be available in the Microsoft Intune admin center.**

Review any existing processes that use these agents and complete any active agent runs before this date. Avoid creating new dependencies on these agents.

**What this change means for you**:

- You can continue using existing Policy Configuration Agent (PCA) and Change Review Agent (CRA) experiences until August 31, 2026.
- After August 31, 2026, these agents and their associated experiences are no longer accessible in the Microsoft Intune admin center.
- If your organization relies on these agents, review and update affected operational processes before the retirement date.

**Recommended actions**:

- Complete any active Policy Configuration Agent (PCA) and Change Review Agent (CRA) activities before **August 31, 2026.**
- Avoid creating new workflows or dependencies that rely on these agents.
- Review existing administrative processes that depend on these agents and plan alternative approaches before the retirement date

The Intune Policy Configuration Agent uses the generative AI-powered features in Security Copilot. It helps IT admins translate complex requirements and industry standard documents into actionable Intune settings.

Admins can quickly generate Intune [settings catalog](../../device-configuration/settings-catalog/) policies that align with organizational or regulatory baselines, including any hardening initiatives.

With the agent, you:

- Upload a document or industry benchmark, and the agent identifies relevant and matching Intune settings.

    You can upload compliance standards and common industry benchmarks, like Security Technical Implementation Guides (STIGs) and National Institute of Standards and Technology (NIST) guidelines.
- Can upload internal policy documents and baselines, like your organization's security policies or compliance requirements.
- Get relevant configuration settings and actionable suggestions based on your uploaded documents.
- Can customize the suggestions to create a baseline that fits your environment. For example, if your organization has an exception to a CIS rule, you can remove that rule from the final policy.

The agent also guides you through creating a policy using the suggestions and helps configure each setting based on your organization's needs. You can review and save these suggestions.

This article:

- Lists the prerequisites to use the agent
- Explains how the agent works
- Shows you how to set up the agent
- Shows you how to renew or remove the agent

To learn how to use the agent, see [Use the Policy Configuration Agent](manage-policy-configuration-agent).

## Prerequisites

![](../../media/icons/16/cloud.svg)**Cloud requirements**

> 
> The agent is supported on the public cloud only. It isn't supported on government clouds.

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> To use Security Copilot agents in Microsoft Intune, the following licenses are required:
> 
> - [Microsoft Intune Plan 1 subscription](../../fundamentals/licensing)
> - [Microsoft Security Copilot](/en-us/copilot/security/get-started-security-copilot) with sufficient security compute units (SCUs)
> 

![](../../media/icons/16/plugin.svg)**Plugins requirements**

> 
> Plugins enable Security Copilot agents to connect with Microsoft services and perform specialized actions. This agent requires the following plugin:
> 
> - ![](../../media/icons/16/intune.svg)[Microsoft Intune](../security-copilot)
> 
> 
> If you use Copilot in Intune, then the Intune plugin is already enabled. [Learn more about plugins](https://go.microsoft.com/fwlink/?linkid=2316474).

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This feature supports the following platforms:
> 
> - Windows
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To **enable and configure** the agent, use an account with the following roles:
> 
> ![](../../media/icons/16/copilot.svg) Security Copilot roles:
> 
> - [Copilot owner](/en-us/copilot/security/authentication#security-copilot-roles)
> 
>     To learn about the Security Copilot roles, see [Security Copilot roles and permissions](/en-us/copilot/security/authentication).
> 
> 
> ![](../../media/icons/16/intune.svg) Intune roles:
> 
> - [Read only operator](../../fundamentals/role-based-access-control/ref-built-in-roles#read-only-operator) or a [Custom role](../../fundamentals/role-based-access-control/overview#custom-roles)with the following permissions:
>     - Device configurations/Read
> 
> 
> To **use the agent**, **generate suggestions**, and **get policy recommendations**, use an account with the following roles:
> 
> ![](../../media/icons/16/copilot.svg) Security Copilot roles:
> 
> - [Copilot Contributor](/en-us/copilot/security/authentication#security-copilot-roles)
> 
> 
> ![](../../media/icons/16/intune.svg) Intune roles:
> 
> - [Read only operator](../../fundamentals/role-based-access-control/ref-built-in-roles#read-only-operator) or a [Custom role](../../fundamentals/role-based-access-control/overview#custom-roles)with the following permissions:
>     - Device configurations/Read
> 
> 
> To **use the agent**, **generate suggestions**, **get policy recommendations**, and **create policies**, use an account with the following roles:
> 
> ![](../../media/icons/16/copilot.svg) Security Copilot roles:
> 
> - [Copilot Contributor](/en-us/copilot/security/authentication#security-copilot-roles)
> 
> 
> ![](../../media/icons/16/intune.svg) Intune roles:
> 
> - [Policy and Profile manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager) or a [Custom role](../../fundamentals/role-based-access-control/overview#custom-roles)with the following permissions:
>     - Device configurations/Create
>     - Device configurations/Update
> 

## How the agent works

[![Diagram that shows different steps and stages of the policy configuration agent workflow in Microsoft Intune.](media/policy-configuration-agent/policy-agent-workflow-svg.png)](media/policy-configuration-agent/policy-agent-workflow-svg.png#lightbox)

At a high level, the agent does the following steps.

1. **Input ingestion**: You give the agent an input that has your policy requirements. It can be a document you upload or direct text input, like `All laptops must have BitLocker enabled with AES-256 encryption`.

    The agent supports custom documents and bulleted lists of requirements.
2. **Natural language processing and parsing**: When you run the agent against your input, the agent uses Security Copilot to parse and map the input. It reads through the language and identifies individual settings that the text describes.

    For example, if the document says "Disallow use of USB storage devices", then the agent interprets the text as a requirement about external storage policy.

    Security Copilot is tuned to recognize common policy statements and technical controls from textual descriptions. It can handle complex wording or varied formats.
3. **Maps rules to Intune settings**: For each parsed requirement, the agent attempts to find a corresponding settings catalog setting that achieves that goal. The agent uses built-in knowledge of Intune's capabilities to choose the correct setting and the setting value that meets the requirement.
4. **Generates policy suggestions**: The agent compiles the mapping results into a draft Intune configuration profile with the recommended settings.
5. **Admin review and confirmation**: Before anything is applied, you review the agent's output. In the admin center, select the agent's suggestion to see the details. You might see a list of recommended settings (supported mappings) and separate lists for unsupported or unmapped items.

    At this stage, you should:

    - **View Details** - You can drill into each recommended setting to read the rationale and adjust. For instance, the agent might suggest a password length of 14 characters because the baseline said `at least 12`.
    - **Remove or Exclude** - If there are certain suggestions you don't want to implement, then you can remove them when you tell the agent to create the device configuration policy.
    - **Acknowledge Unsupported Items** - For any requirements that Intune can't enforce, document how you plan to handle them, or acknowledge them. The agent's role is informational and to make sure you're aware of any gaps.
6. **Policy creation**: After you confirm the suggestions, you can choose to create a new configuration profile with all the recommended settings. This settings catalog policy isn't enforced until you assign it, just like any Intune policy you manually create.

    At this stage, the policy is a normal Intune policy. You can assign it to the appropriate groups and rename the policy.
7. **Deploy and monitor**: Once the policy is assigned, devices start reporting with the new settings. The agent's job is done until you run it again.

## Agent identity

The agent runs under the identity and permissions of the account used during this setup. Actions are limited to the permissions of that account, and the identity refreshes with each run. So, any changes to the account's permissions affect the agent's capabilities during its next run.

We recommend you sign in with the **Security Copilot Owner** role to set up the agent. Some roles might automatically have the required permissions. To learn more, see [Security Copilot roles](/en-us/copilot/security/authentication#security-copilot-roles).

## Set up the agent

**Before you enable the agent**:

- An admin must manually start the agent. Once started, there's no option to stop or pause the agent.
- The agent can only be started from the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
- Session details in the [Microsoft Security Copilot portal](https://go.microsoft.com/fwlink/?linkid=2247989) are visible only to the user who set up the agent.
- Only one agent instance is supported per tenant.

**Use the following steps to set up the agent**:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Agents** &gt; **Policy Configuration Agent**.
2. In **Overview**, select **Set up agent**.

    The **Set up Policy Configuration Agent** pane lists the required permissions to set up the agent, and provides more information about the setup requirements.
3. Select **Set up agent**.

When it completes, the agent is ready to use. To learn more about using the agent, see [Use the Policy Configuration Agent](manage-policy-configuration-agent).

## Renew the agent

If you don't use an agent for 90 days, the agent authorization expires and agent runs fail until reauthentication. You can renew the agent authentication anytime.

As the expiration gets closer, Intune shows a warning on the agent overview page that each **Copilot owner** and **Copilot contributor** can see. The warning prompts to renew the agent identity.

To reauthorize the agent identity, select **Renew authentication**. When you renew the agent authentication, the agent automatically uses the signed-in credentials. If you don't want to use the signed-in credentials, then select the agent &gt; **Settings** tab &gt; **Choose another identity**.

After renewal, the warning banner disappears, and a toast notification validates that the renewal is successful.

[![Screenshot of the Policy Configuration Agent change identity screen in Microsoft Intune.](media/policy-configuration-agent/change-identity.png)](media/policy-configuration-agent/change-identity.png#lightbox)

## Remove the agent

When you remove an agent, all associated data generated including suggestions and activities are deleted. Previously applied suggestions remain unchanged.

Steps to remove an agent instance:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Agents**.
2. Select the agent instance you want to remove.
3. Select **Remove agent** and confirm the removal.

After removal:

- The agent pane returns to its original state.
- An admin can reinstall the agent later by repeating the setup process.

## ![](../../media/icons/32/feedback.svg) Help shape the future of Intune agents

Join our **Intune Agents Feedback Forum** to share insights and influence upcoming capabilities in Microsoft Intune.

Sign up and learn more: https://aka.ms/IntuneAgentsForum