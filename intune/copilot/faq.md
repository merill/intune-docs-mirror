---
layout: Conceptual
title: FAQ for Microsoft Copilot in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/copilot/faq
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.update-cycle: 180-days
description: Get answers to common questions when using Copilot in Microsoft Intune, including accessing Copilot, licensing, and more.
ms.date: 2026-05-26T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: ankurgoyal, rashok
ms.collection:
- M365-identity-device-management
- msec-ai-copilot
locale: en-us
document_id: 334e06df-f1be-8777-4793-cd649a3874fe
document_version_independent_id: 334e06df-f1be-8777-4793-cd649a3874fe
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/copilot/faq.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: copilot/faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/copilot/faq.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
platformId: 9f8e8522-4bf0-05c4-2bf4-78802dcf9ab8
---

# FAQ for Microsoft Copilot in Intune - Microsoft Intune | Microsoft Learn

This article answers common questions about using Microsoft Copilot in Intune. To learn more about Copilot in Intune and to get started, see [Microsoft Copilot in Intune overview](./).

## Access to Copilot

### How can I control access to Copilot in Intune?

When Microsoft Intune is enabled as a data source in Security Copilot, by default:

- The Microsoft Entra ID **Intune Administrator** role automatically inherits **Security Copilot owner** access to Copilot in Intune.
- All the other built-in and custom Intune role-based access (RBAC) roles automatically inherit **Security Copilot contributor** access to Copilot in Intune.

The Security Copilot owner and contributor roles are described in [Roles and authentication in Microsoft Security Copilot](/en-us/copilot/security/authentication). [Microsoft Copilot in Intune overview](./) also has more information.

There are also Microsoft Entra roles that can control access to Security Copilot.

After you enable Intune in Security Copilot, your Intune admins can see the Copilot features in the Intune admin center. But they can only access the data that they have permission to. Copilot honors existing [Intune RBAC roles](../fundamentals/role-based-access-control/overview) and [Intune scope tags](../fundamentals/role-based-access-control/scope-tags) that are assigned to your admins.

So, if an admin tries to access Intune data that they don't have permissions to, they get the following error message:

`You don't have permission to access this feature. Reach out to your IT administrator for help.`

### Can I use Security Copilot if I'm not an Intune admin, and vice versa?

Yes. Access to Security Copilot is managed by using Security Copilot or Microsoft Entra roles. For more information, see [Roles and authentication in Microsoft Security Copilot](/en-us/copilot/security/authentication).

Security Copilot is scoped to all your embedded services.

If you're an Intune admin or IT admin and only want Intune data, you should use [Copilot in Intune](./). Its scope is only Intune data, and its capabilities are integrated into the relevant areas of the Intune admin center.

If you're a security admin, you can use [Copilot in Intune](./) if you only want insights into your Intune data.

## Capabilities and cost

### How do I turn on Intune capabilities?

In the [Microsoft Security Copilot portal](https://go.microsoft.com/fwlink/?linkid=2247989), select **Sources** (prompt bar &gt; right corner), and enable the Microsoft Intune plug-in. This plug-in allows you to access your Intune data and use the Copilot features in the Intune admin center.

For more information about managing plug-ins, see [Manage plug-ins in Security Copilot](/en-us/copilot/security/manage-plugins).

### Can I use capabilities for other Copilot services in the Intune admin center?

No. Copilot in Intune in the Intune admin center is available only for Intune capabilities.

You can't get insights from other Microsoft services, like Microsoft Defender, Microsoft Entra, and Microsoft Purview. To get insights from other Microsoft services, you can use the [Security Copilot portal](https://go.microsoft.com/fwlink/?linkid=2247989).

### How much does Copilot in Intune cost?

Copilot in Intune is included with Security Copilot. Security Copilot uses security compute units (SCUs). There aren't any other licensing requirements or Intune-specific licenses for using Copilot in Intune.

You need Security Copilot enabled to access Copilot in Intune features. Some Copilot in Intune capabilities can use little to none of your provisioned SCUs, while other capabilities can use more. Usage will also change as Copilot in Intune capabilities are changed and improved over time.

For more information about SCUs, see:

- [Get started with Security Copilot](/en-us/copilot/security/get-started-security-copilot)
- [Manage capacity in Security Copilot](/en-us/copilot/security/manage-usage)

### Is there a limit on the prompt output?

Copilot in Intune is bound by any token limits in Security Copilot. For more information, see [Security Copilot FAQ - Token limits](/en-us/copilot/security/faq-security-copilot#how-is-copilot-for-security-dealing-with-a-token-limit).

## Security Copilot vs. Copilot in Intune

### Does Security Copilot give admins more access to Intune data than is available in the Intune admin center?

No. The Intune capabilities in Security Copilot are built using the existing Microsoft Graph APIs, which are the same APIs that the Intune admin center uses. Both Copilot experiences use the same Intune capabilities.

### To get Intune insights, should I use Security Copilot or Copilot in Intune?

To use Copilot with your Intune data, you can use Copilot in Intune or Security Copilot. Here's a comparison of the two experiences:

| Feature | Copilot in Intune | Security Copilot |
| --- | --- | --- |
| **Access and data insights** | This Copilot is embedded in the Intune admin center and is scoped to only show Intune data. Intune admins should use Copilot in Intune for Intune-only tasks. | This Copilot is a standalone experience. It can access other embedded services, like Microsoft Defender, Microsoft Entra ID, Microsoft Purview, and Microsoft Intune. It accesses the same Intune capabilities as Copilot in Intune. |
| **Open prompting** | Intune has built-in prompts you can use and access from Copilot Chat in Intune. In Copilot Chat, you can enter a query. Copilot summarizes the results and recommends built-in prompts based on the text you enter. There isn't an open prompt. There are plans to include an open prompt in the future (no ETA). | Can use open prompts or use [promptbooks](/en-us/copilot/security/using-promptbooks). |
| **Prompt history** | The prompt/response history isn't available in the Intune admin center. To view the prompt history, use Security Copilot.The prompts can look different compared with the prompts shown in Intune, as Intune enters the prompt for you. | You can review the prompt/response history even when the prompt is submitted in the standalone or embedded experience. |
| **Target audience** | Focus is the IT admin/IT Pro. | Focus is the Security Operations Center (SOC) and can be used by IT admins. |

## Feedback and troubleshooting Copilot

### Copilot appears to show the wrong info. How can I debug and validate?

If you think that the output is incorrect, submit feedback in your Copilot Chat session in Intune, and include details about what you're seeing.

Every Copilot response has two feedback buttons – a thumbs up when the response is what you expect, and a thumbs down when the response isn't what you expect. This feedback helps improve the Copilot experience.

![Screenshot that shows how to provide Copilot feedback in Microsoft Intune and Intune admin center.](media/faq/thumbs-up-thumbs-down.png)

Other things you can try:

- In Microsoft Edge, you can use the F12 developer tools to debug the issue. In the developer debug tool, select the **Network** view. In Copilot, select the prompt to get the output. In the developer debug tool, use the **logs** entries to look more closely at the steps between the prompt input and output.
- If you're working with Microsoft to debug the issue, support might ask you for the session ID. To get the session ID, you can:

    - Use the F12 developer tools in your browser. This information shows the capabilities that Copilot uses.
    - In the [Security Copilot portal](https://go.microsoft.com/fwlink/?linkid=2247989), you can view the prompt sessions and session IDs from the Intune embedded experience.

To learn more about privacy and data security, what data is collected as part of feedback, and how to disable feedback, see [Privacy and data security in Security Copilot](/en-us/copilot/security/privacy-data-security).

### Can I use Give Feedback to submit feedback?

In the admin center, if you select the three dots (...) in the top right corner, you see the **Give Feedback** option. This option is for general feedback about Microsoft Azure, not for Copilot in Intune. Don't use this option to provide any feedback related to Security Copilot in Intune.

![Screenshot that shows how the Azure feedback option in Microsoft Intune and Intune admin center.](media/faq/azure-give-feedback.png)

To disable the Microsoft Azure **Give Feedback** form, see [Manage access to Microsoft Copilot in Azure](/en-us/azure/copilot/manage-access).