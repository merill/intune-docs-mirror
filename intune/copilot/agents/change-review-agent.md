---
layout: Conceptual
title: Change Review Agent Overview - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/copilot/agents/change-review-agent
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
description: Learn about the Change Review Agent in Microsoft Intune, its prerequisites, and how it works.
ms.date: 2025-11-10T00:00:00.0000000Z
ms.topic: overview
ms.reviewer: zinebtakafi
locale: en-us
document_id: 86de7e48-c37f-8b26-7525-f48534f721d4
document_version_independent_id: 86de7e48-c37f-8b26-7525-f48534f721d4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/copilot/agents/change-review-agent.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: copilot/agents/change-review-agent
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/copilot/agents/change-review-agent.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
platformId: 102bf5b6-69e5-f3fa-eb49-58dc55e2bdce
---

# Change Review Agent Overview - Microsoft Intune | Microsoft Learn

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

In public preview, the Microsoft Intune Change Review Agent uses Microsoft Security Copilot's generative AI to evaluate Multi Admin Approval requests for PowerShell scripts on Windows devices. It provides risk-based recommendations and contextual insights to help administrators understand script behavior and associated risks. These insights help Intune administrators make informed decisions more quickly about whether to approve or deny requests.

To generate these recommendations, the agent aggregates signals from multiple sources:

- Microsoft Defender Vulnerability Management - for threat insights
- Microsoft -Entra ID - for identity risk
- Microsoft Intune - for Multi Admin Approval requests and historical context of similar requests

The agent analyzes these signals to assess the potential risk associated with each request and then delivers actionable insights to support secure and efficient change management.

## Prerequisites

![](../../media/icons/16/cloud.svg)**Cloud requirements**

> 
> The agent is supported on the public cloud only. It isn't supported on government clouds.

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> To use Security Copilot agents in Microsoft Intune, your organization must meet specific licensing requirements.
> 
> Required licenses:
> 
> - [Microsoft Intune Plan 1 subscription](../../fundamentals/licensing)
> - [Microsoft Entra ID P2](/en-us/entra/fundamentals/licensing)
> - [Microsoft Defender Vulnerability Management](/en-us/defender-vulnerability-management/tvm-prerequisites)
> - [Microsoft Security Copilot](/en-us/copilot/security/get-started-security-copilot) with sufficient security compute units (SCUs)
> 

![](../../media/icons/16/plugin.svg)**Plugins requirements**

> 
> Plugins enable Security Copilot agents to connect with Microsoft services and perform specialized actions.
> 
> The Change Review Agent requires the following plugins:
> 
> - ![](../../media/icons/16/intune.svg)[Microsoft Intune](../security-copilot)
> - ![](../../media/icons/16/entra.svg)[Microsoft Entra](/en-us/entra/fundamentals/copilot-security-entra)
> - ![](../../media/icons/16/defender.svg)[Microsoft Defender XDR](/en-us/defender-vulnerability-management/defender-vulnerability-management)
> - ![](../../media/icons/16/defender.svg)[Microsoft Threat Intelligence](/en-us/defender/threat-intelligence/what-is-microsoft-defender-threat-intelligence-defender-ti)
> 
> 
> [Learn more about plugins](https://go.microsoft.com/fwlink/?linkid=2316474).

![](../../media/icons/16/devices.svg)**Platform requirements and scenarios**

> 
> The agent supports evaluation and recommendations for the following platforms and scenarios:
> 
> - Windows
> - PowerShell scripts in Intune
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> Role requirements vary based on whether you're configuring the agent or using it, and on the specific actions performed.
> 
> To **enable and configure** the Change Review Agent, use an account with the following roles:
> 
> ![](../../media/icons/16/entra.svg) Entra roles:
> 
> - [*Intune Administrator*](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)
> - [*Security Reader*](/en-us/entra/identity/role-based-access-control/permissions-reference#security-reader)
> - *Entra/Identity risky user (read)* - This permission maps to the Unified RBAC permission *Security posture / Identity risk / Risky users (read)*.
> 
> 
> ![](../../media/icons/16/defender.svg) Defender roles - Defender role-based access control (RBAC) roles depend on your Defender XDR implementation:
> 
> - [*Unified RBAC*](/en-us/defender-xdr/manage-rbac): Assign the Microsoft Entra ID Security Reader to the agent's identity account. This role provides read-only access to Defender Vulnerability Management data and automatically enforces device group scoping.
> - [*Granular RBAC*](/en-us/defender-endpoint/rbac): Assign a custom RBAC role with permissions equivalent to the Unified RBAC Security Reader role. For example:
> 
>     - *View data – Defender Vulnerability Management* - This permission maps to the Unified RBAC permission *Security posture / Posture management / Vulnerability management (read)*.
> 
> 
>     For details about mapping permissions to the Unified RBAC Security Reader role, see [Microsoft Entra Global roles access](/en-us/defender-xdr/compare-rbac-roles#microsoft-entra-global-roles-access) in the *Map Microsoft Defender XDR Unified role-based access control (RBAC)* article in the Defender documentation.
> 
>     Ensure the agent's identity is scoped in Microsoft Defender to include all relevant device groups. The agent can't access or report on devices outside its assigned scope.
> 
> 
> ![](../../media/icons/16/copilot.svg) Security Copilot roles:
> 
> - [Copilot owner](/en-us/copilot/security/authentication#security-copilot-roles)
> 
> 
> To **use** the agent, sign in with an account that has the following roles:
> 
> ![](../../media/icons/16/intune.svg) Intune roles:
> 
> - [Read Only Operator](../../fundamentals/role-based-access-control/overview#built-in-roles) or [custom role](../../fundamentals/role-based-access-control/overview#custom-roles) with equivalent permissions.
> 
> 
> ![](../../media/icons/16/entra.svg) Entra roles:
> 
> - [Security Reader](/en-us/entra/identity/role-based-access-control/permissions-reference#security-reader)
> 
> 
> ![](../../media/icons/16/defender.svg) Defender roles
> 
> - Use of the agent requires the same access as *enabling and configuring* the agent.
> 
> 
> ![](../../media/icons/16/copilot.svg) Security Copilot roles:
> 
> - [Copilot contributor](/en-us/copilot/security/authentication#security-copilot-roles)
> 

## How the agent works

The Change Review Agent operates using an Intune admins account identity and runs manually when an admin starts it.

At a high level, the agent does the following steps each time it runs:

1. **Signal aggregation** - The agent begins by aggregating signals from the following sources:

    - Microsoft Defender Vulnerability Management - for threat insights
    - Microsoft Entra ID - for identity risk
    - Microsoft Intune - for Multi Admin Approval requests and historical context of similar requests
2. **Evaluation** - The agent evaluates Windows PowerShell scripts for Multi Admin Approval requests using predefined logic that's built in to the agent configuration.
3. **Recommendations** - The agent reviews and then provides recommendations for a maximum of 10 requests per run.

    Suggestions are *suggestions* only. The approval or rejection of a request remains with an Intune administrator.

    The first column of the recommendation list presents Suggested Next Steps, which display the recommended action followed by the name of the request. Possible actions include:

    - Approve - Low-risk request; likely safe to approve.
    - Reject - High-risk request; shouldn't be approved.
    - Needs more info - Risk couldn't be fully assessed. This request requires further review.

    Each recommendation includes supporting details that explain:

    - The rationale behind the agent's recommendation.
    - What the script is intended to accomplish or do.
    - A detailed list of factors that the agent reviewed as part of its process.

## Agent identity

The agent runs under the identity and permissions of the Intune admin account used during setup. The agent's actions are limited to the permissions of that account, and the identity refreshes with each run. If the agent doesn't run for 90 consecutive days, its authentication expires, and subsequent runs fail until its renewed. To maintain functionality, renew the agent identity before the 90-day limit.

## Operational considerations

Before setting up and starting the agent for the first time, review the following considerations:

- An admin must manually start the agent. Once started, there's no option to stop or pause it.
- The agent can only be started from the Microsoft Intune admin center.
- Session details in the [Microsoft Security Copilot portal](https://go.microsoft.com/fwlink/?linkid=2247989) are visible only to the user who set up the agent.
- The agent reviews and then provides recommendations for a maximum of 10 requests per run.
- Only one agent instance is supported per tenant/user context.

## Set up the agent

The agent operates under the identity and permissions of the Intune admin account used during setup. Its operations are limited to the permissions of that account, and the identity refreshes with each run. Any changes to the account's permissions affect the agent's capabilities during its next run.

**To set up the Change Review Agent:**

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Agents** &gt; **Change Review Agent**.
2. In **Overview**, select **Set up Agent** to open the *Set up Change review agent* pane.
3. The **Set up Change review agent** pane lists the required permissions and provides details about setup requirements. When requirements are met, select **Start agent**.

    ![Screenshot of the Set up Change review agent pane.](media/change-review-agent/setup.png)

The agent operates until it completes its evaluation and displays results in the Overview tab. When the run finishes, the agent is ready to use.

To learn more about using the agent, see [Use the Change Review Agent](manage-change-review-agent).

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