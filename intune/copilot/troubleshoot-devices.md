---
layout: Conceptual
title: Copilot in Intune shows device information and helps troubleshoot - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/copilot/troubleshoot-devices
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.update-cycle: 180-days
description: Microsoft Security Copilot in Intune can help you get information about your devices, compare devices, and get error information. Use this information to help you manage and troubleshoot device issues.
ms.date: 2026-05-26T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: ankurgoyal, zadvor, rashok
ms.collection:
- M365-identity-device-management
- msec-ai-copilot
locale: en-us
document_id: 60037251-9d5b-c931-b025-f216e4b0d59c
document_version_independent_id: 60037251-9d5b-c931-b025-f216e4b0d59c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/copilot/troubleshoot-devices.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: copilot/troubleshoot-devices
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/copilot/troubleshoot-devices.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/46e3c7c4-fe77-4a6e-b40a-44c569819fa5
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d0c6fab8-2d7d-4bb0-bf40-589e08d7c132
platformId: 5d4a0064-1050-49cc-6ee6-7c91c631ac0e
---

# Copilot in Intune shows device information and helps troubleshoot - Microsoft Intune | Microsoft Learn

Microsoft Security Copilot is a generative-AI security analysis tool that can help your organization get information quickly. Copilot is [built into Microsoft Intune](./). It can help IT admins manage and troubleshoot devices.

Copilot uses your Intune data. Admins can only access the data that they have permissions to, which includes the [role based access control (RBAC) roles](../fundamentals/role-based-access-control/overview) and [scope tags](../fundamentals/role-based-access-control/scope-tags) assigned to them. For more information, see [Copilot in Intune FAQ](faq).

With Copilot in Intune, you can:

- Get more information about a specific device, including installed apps, group membership, and more.
- Compare devices to see the similarities and differences between them, like the compliance policies, hardware, and device configurations assigned to both devices.
- Use the error analyzer prompt to enter an error code, get more information about the error, and get a possible resolution.

This article describes how to use Copilot to manage and troubleshoot device issues in Intune.

## Before you begin

To use Copilot in Intune, make sure Copilot is enabled. For more information, see:

- [Copilot in Intune](./#before-you-begin)
- [Get started with Microsoft Security Copilot](/en-us/copilot/security/get-started-security-copilot)

## Use a suggested prompt

To troubleshoot devices, you can use Copilot Chat to get more information about a device. For example, you can get a list of installed apps, compare devices, and get information about an error code.

The prompts include:

- Summarize this device.
- Analyze an error code.
- Compare this device with another device.
- Show apps on this device.
- Show policies on this device.
- Show group memberships.
- Show the primary user of this device.

As you type your question in Copilot Chat, an intelligent search matches your request to available prompts built into Intune. These prompts are shown as suggestions that you can select. You can also ask questions about a Microsoft Surface device, or troubleshoot issues in a Windows 365 Cloud PC.

## Get details and troubleshoot a device

This section guides you through some Copilot prompts that you can use.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **All devices**.
3. Select **Copilot**:

    [![Screenshot that shows to select Copilot in the banner in Microsoft Intune or Intune admin center.](media/troubleshoot-devices/copilot-banner.png)](media/troubleshoot-devices/copilot-banner.png#lightbox)
4. Copilot Chat opens and shows some prompts that you can use that apply to all devices. Select a prompt to get more information. For example, select **Show me all non-compliant devices**:

    ![Screenshot that shows all noncompliant devices in a Copilot prompt in Microsoft Intune or Intune admin center.](media/troubleshoot-devices/all-noncompliant-devices.png)

    The results show all noncompliant devices in your organization, including the device name, device ID, and more.

Let's walk through some other prompts.

### Summarize a device

In your Copilot Chat session, enter `summarize` and select the **Summarize an Intune device** prompt.

![Screenshot that shows the summarize an Intune device Copilot prompt in Microsoft Intune or Intune admin center.](media/troubleshoot-devices/summarize-intune-device-prompt.png)

When you submit the prompt, it asks for the device name or ID. The summary includes device-specific information, like the operating system, whether the device is registered in Microsoft Entra ID, malware counts, any noncompliant policies, group membership, and more.

### Compare devices

In your Copilot Chat session, enter `compare` and select the **Compare two Intune devices** prompt.

![Screenshot that shows the compare an Intune device Copilot prompt in Microsoft Intune or Intune admin center.](media/troubleshoot-devices/compare-intune-device-prompt.png)

With this prompt, you can compare a working/healthy device with a non-working/unhealthy device. This comparison helps you identify the differences between the two devices and troubleshoot the nonworking device.

When you submit the prompt, it asks for the device names or IDs to compare:

![Screenshot that shows the Copilot comparing two devices in Microsoft Intune or Intune admin center.](media/troubleshoot-devices/compare-devices-comparison-type.png)

The results show the differences and similarities between the two devices.

### Show policies assigned to this device

In the admin center, go to **Devices** &gt; **All devices** and select any device. In your Copilot Chat session, enter `show policies` and select the **Show me device configuration policies assigned to a device** prompt.

[![Screenshot that shows the device configuration policies assigned to a device in Copilot in Microsoft Intune or Intune admin center.](media/troubleshoot-devices/show-policies-prompt.png)](media/troubleshoot-devices/show-policies-prompt.png#lightbox)

Select the type of policies to show for the device:

[![Screenshot that shows the policy types you can choose in a Copilot prompt in Microsoft Intune or Intune admin center.](media/troubleshoot-devices/show-policies-type-prompt.png)](media/troubleshoot-devices/show-policies-type-prompt.png#lightbox)

This prompt shows all the policies that are assigned to the device. Use this prompt to show configuration profiles, compliance policies, and app configuration policies.