---
layout: Conceptual
title: Security Copilot Agents in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/copilot/agents/
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
description: Discover how Microsoft Security Copilot enhances Microsoft Intune through AI-powered security agents. Learn about available agents and explore their capabilities.
ms.date: 2025-11-10T00:00:00.0000000Z
ms.topic: overview
ms.reviewer: 
locale: en-us
document_id: 175bb9ca-a8dc-88b0-7329-5229a81d0d7e
document_version_independent_id: 175bb9ca-a8dc-88b0-7329-5229a81d0d7e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/copilot/agents/index.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: copilot/agents/index
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/copilot/agents/index.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/03921bea-3752-4ddc-98c2-5aa70db91565
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/09911d3e-3eb9-4c8d-ab86-ce80d8d36bbd
platformId: 6878c4e7-abf6-2563-be22-10f59de870d9
---

# Security Copilot Agents in Intune - Microsoft Intune | Microsoft Learn

Security Copilot agents in Intune are AI-powered assistants that enhance enterprise security. They automate tasks for endpoint protection, identity management, threat intelligence, and device configuration. They help IT teams quickly address vulnerabilities, policy gaps, and emerging threats.

Agents are built on Microsoft Security Copilot's generative AI and automation capabilities. They observe, reason, and act with oversight and review from your administrators. Each agent is tailored to a specific use case, operates within the Intune admin center, and uses role-based access controls.

## Available agents

Microsoft Intune includes specialized Security Copilot agents, each designed for a specific security scenario. The following agents are available:

#### Change Review Agent

![](icons/change-review-agent.svg)

> 
> The *Change Review Agent* evaluates the effect of approval requests in Intune and makes recommendations for the actions you can take.

#### Device Offboarding Agent

![](icons/device-offboarding-agent.svg)

> 
> The *Device Offboarding Agent* identifies stale or misaligned devices across Intune and Microsoft Entra ID, providing actionable insights and requiring admin approval before offboarding any devices.

#### Policy Configuration Agent

![](icons/policy-configuration-agent.svg)

> 
> With the *Policy Configuration Agent*, you import documents or write instructions in plain language. The agent uses this information to find matching settings in the Intune settings catalog and recommends values for these settings. You can then use the agent to create a policy with those settings and their values.

#### Vulnerability Remediation Agent

![](icons/vulnerability-remediation-agent.svg)

> 
> The *Vulnerability Remediation Agent* uses Defender data to monitor vulnerabilities and prioritize remediation with AI-driven risk assessments.

## Getting started with agents

### Prerequisites

Before you begin, make sure you have:

- [Security compute units (SCU)](/en-us/copilot/security/manage-usage) available
- Reviewed the [Privacy and data security in Microsoft Security Copilot](/en-us/copilot/security/privacy-data-security) to understand how your data is handled.

### Setup process

1. Enable Security Copilot using the [Security Copilot setup guide](/en-us/copilot/security/get-started-security-copilot).
2. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) using the least privileged role required for the agent you want to configure.
3. Browse to **Agents** and select **View details** for the agent you want to configure.

[![Screenshot of the security copilot feature in the Intune admin center.](media/index/security-copilot-agents.png)](media/index/security-copilot-agents.png#lightbox)

## Agents in the Microsoft ecosystem

While this article focuses on Intune agents, similar agents are available across other Microsoft security products. For more information, see:

- [Microsoft Entra](/en-us/entra/security-copilot/entra-agents)
- [Microsoft Defender](/en-us/defender-xdr/security-copilot-agents-defender)
- [Microsoft Purview](/en-us/purview/copilot-in-purview-agents)