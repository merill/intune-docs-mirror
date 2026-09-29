---
layout: Conceptual
title: Use Intune to remediate vulnerabilities found by Microsoft Defender for Endpoint - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/remediate-vulnerabilities
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-secure-endpoints
ms.reviewer: laarrizz
ms.subservice: protect
description: Integrate Microsoft Defender Vulnerability Management with Intune to create security tasks, track remediation, and reduce vulnerability exposure across managed devices.
ms.date: 2026-04-08T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 1a36b687-9606-f75e-723c-4802ad1e255a
document_version_independent_id: 1a36b687-9606-f75e-723c-4802ad1e255a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/microsoft-defender/remediate-vulnerabilities.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/microsoft-defender/remediate-vulnerabilities
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/microsoft-defender/remediate-vulnerabilities.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c671beaa-a830-4c9f-aceb-97379ee031ca
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8921374c-4dbe-4ed0-b011-a39e18bfbd98
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: bb80a178-65e8-f1c0-5acc-5cb44eae2882
---

# Use Intune to remediate vulnerabilities found by Microsoft Defender for Endpoint - Microsoft Intune | Microsoft Learn

When you [integrate Microsoft Defender for Endpoint with Microsoft Intune](configure-integration#connect-defender-for-endpoint-to-intune), you can use Microsoft Defender Vulnerability Management through Intune security tasks. These tasks help Intune admins understand and address current vulnerabilities based on guidance from Defender for Endpoint. This integration enhances the discovery and prioritization of vulnerabilities, improving remediation response times across your environment.

[Microsoft Defender Vulnerability Management](/en-us/defender-vulnerability-management/defender-vulnerability-management) is part of [Microsoft Defender for Endpoint](/en-us/defender-endpoint/microsoft-defender-endpoint).

## Prerequisites

**Subscriptions**:

- Intune Plan 1
- Defender for Endpoint ([Sign up for a free trial](https://www.microsoft.com/security/business/endpoint-security/microsoft-defender-endpoint).)

Intune configurations for Defender for Endpoint:

- Configure a service-to-service connection with Microsoft Defender for Endpoint, and enable the **Microsoft Intune connection** in the Microsoft Defender portal. This connection allows security admins to create Intune security tasks when submitting remediation requests. For setup instructions, see [Connect Microsoft Defender for Endpoint to Intune](configure-integration#connect-defender-for-endpoint-to-intune).
- Deploy policies to onboard devices to Defender for Endpoint and enable risk assessment. See [Configure Microsoft Defender for Endpoint with Intune](configure-integration).

## How integration works

After you integrate Intune with Defender for Endpoint, Defender Vulnerability Management identifies vulnerabilities on your managed devices.

In the Defender portal, [security admins can review endpoint vulnerabilities](/en-us/defender-vulnerability-management/defender-vulnerability-management#remediation-and-tracking) and create Intune security tasks for remediation. These tasks appear in the Intune admin center, where Intune admins can act and remediate issues based on Defender's guidance:

- Defender for Endpoint identifies vulnerabilities through scans and assessments.
- Not all identified vulnerabilities support remediation through Intune; only compatible vulnerabilities result in security tasks.

Security tasks identify:

- The type of vulnerability
- Priority
- Status
- Steps for remediation

Intune admins can view a security task and then choose to accept or reject it. For accepted tasks, the admin follows the guidance provided to use Intune for remediation. Once the remediation is successful, the admin sets the task to **Complete Task**, which updates its status in both Intune and Defender for Endpoint where security admins can verify the revised status of the vulnerability.

### Workflow example

The following example shows the workflow for discovering and remediating an application vulnerability:

- A Defender for Endpoint scan identifies a vulnerability in the app Contoso Media Player v4, which is an unmanaged app that isn't deployed by Intune. A security admin in the Defender portal creates an Intune security task to update the app.
- The security task appears in the Intune admin center with a status of **Pending**.
- The Intune admin views the task details and selects **Accept**, which changes the status of the task to **Accepted** in both Intune and Defender for Endpoint.
- The admin follows the remediation guidance provided. For managed apps, Intune might include instructions or links to update the app. For unmanaged apps, Intune can only provide text instructions.
- After addressing the vulnerability, the Intune admin marks the task as **Complete Task**. This action updates the status in both Intune and Defender for Endpoint, where security admins confirm the remediation is successful and complete.

### Types of security tasks

Each security task has a *Remediation Type*:

- **Application**: For example, Defender for Endpoint finds a vulnerability in an app like *Contoso Media Player v4*. An admin creates a task to update the app, which might involve applying a security update or installing a new version.
- **Configuration**: For instance, if devices lack protection from *Potentially Unwanted Applications* (PUA), an admin creates a task to configure the setting in the Microsoft Defender Antivirus profile.

When Intune doesn't support implementation of a suitable remediation, Defender for Endpoint doesn't create a security task.

### Remediation actions

Common security task remediations include:

- **Block** an application from running.
- **Deploy** an operating system update to mitigate the vulnerability.
- **Deploy** endpoint security policy to mitigate the vulnerability.
- **Modify** a registry value.
- **Disable** or **Enable** a configuration to affect the vulnerability.
- **Require Attention**, which alerts the admin when no suitable recommendation is available.

## Work with security tasks

Before you can manage security tasks in the Intune admin center, a security admin must first create them in the Defender portal. Security admins create tasks by submitting remediation requests through Defender Vulnerability Management. For instructions, see [Remediate vulnerabilities with Microsoft Defender Vulnerability Management](/en-us/defender-vulnerability-management/tvm-remediation#request-remediation) in the Defender documentation.

Tip

You can also manage these tasks from the centralized [**Admin tasks**](../../governance/admin-tasks) pane in the Intune admin center.

To manage security tasks:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint security** &gt; **Security tasks**.
3. Choose a security task to view its details. In the task window, you can select additional links, including:

    - MANAGED APPS - View the app that's vulnerable. When the vulnerability applies to multiple apps, Intune displays a filtered list of apps.
    - DEVICES - View a list of the *Vulnerable devices* from which you can link through to an entry with more details for the vulnerability on that device.
    - REQUESTOR - Use the link to send mail to the admin who submitted this security task.
    - NOTES - Read custom messages submitted by the requestor when opening the security task.
4. Select **Accept** or **Reject** to send notification to Defender for Endpoint for your planned action. When you accept or reject a task, you can submit notes, which are sent to Defender for Endpoint.
5. After accepting a task, reopen the security task (if it closed), and follow the REMEDIATION details to remediate the vulnerability. The instructions provided by Defender for Endpoint in the security task details vary depending on the vulnerability involved.
6. After completing the remediation steps, open the security task and select **Complete Task**. This action updates the security task status in both Intune and Defender for Endpoint.

Note

Each remediation request in Defender for Endpoint is [limited to 10,000 devices](/en-us/defender-vulnerability-management/tvm-remediation#remediation-request-steps). If a vulnerability affects more devices, the resulting security task in Intune covers only 10,000 of them.

Successful remediation can reduce the risk exposure score in Defender for Endpoint based on subsequent status updates from the remediated devices. You can [monitor these risk levels](monitor) to track compliance improvements over time.

## Troubleshooting

If security tasks don't appear in Intune:

- Verify the Intune connection is enabled in the Defender portal.
- Confirm devices are onboarded to Defender for Endpoint.
- Check that security admins create tasks for vulnerabilities that Intune can remediate.
- Allow time for task synchronization between portals.