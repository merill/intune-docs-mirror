---
layout: Conceptual
title: Endpoint Protection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/endpoint-protection
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Learn how to manage antimalware policies and Windows Defender Firewall security for clients.
ms.date: 2021-09-09T00:00:00.0000000Z
ms.subservice: protect
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: ac1e9ae8-a9de-99f3-5335-2460fb9d69ce
document_version_independent_id: d2109d70-4f53-7033-1573-3ca6ad43e2f9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/endpoint-protection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/endpoint-protection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/endpoint-protection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c671beaa-a830-4c9f-aceb-97379ee031ca
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8921374c-4dbe-4ed0-b011-a39e18bfbd98
platformId: 65d46870-4943-5a69-c972-fb57166449b8
---

# Endpoint Protection - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Endpoint Protection manages antimalware policies and Windows Defender Firewall security for client computers in your Configuration Manager hierarchy.

When you use Endpoint Protection with Configuration Manager, you have the following benefits:

- Configure antimalware policies, Windows Defender Firewall settings, and manage Microsoft Defender for Endpoint to selected groups of computers.
- Use Configuration Manager software updates to download the latest antimalware definition files to keep client computers up to date.
- Send email notifications, use in-console monitoring, and view reports. These actions inform administrative users when malware is detected on client computers.

Beginning with Windows 10 and Windows Server 2016 computers, Microsoft Defender Antivirus is already installed. For these operating systems, a management client for Microsoft Defender Antivirus is installed when the Configuration Manager client installs. On Windows 8.1 and earlier computers, the Endpoint Protection client is installed with the Configuration Manager client. Microsoft Defender Antivirus and the Endpoint Protection client have the following capabilities:

- Malware and spyware detection and remediation
- Rootkit detection and remediation
- Critical vulnerability assessment and automatic definition and engine updates
- Network vulnerability detection through Network Inspection System
- Integration with Cloud Protection Service to report malware to Microsoft. When you join this service, the Endpoint Protection client or Microsoft Defender Antivirus downloads the latest definitions from the Malware Protection Center when unidentified malware is detected on a computer.

Note

The Endpoint Protection client can be installed on a server that runs Hyper-V and on guest virtual machines with supported operating systems. To prevent excessive CPU usage, Endpoint Protection actions have a built-in randomized delay so that protection services do not run simultaneously.

You can also manage Windows Defender Firewall settings with Endpoint Protection in the Configuration Manager console.

## Manage malware

Endpoint Protection in Configuration Manager allows you to create antimalware policies that contain settings for Endpoint Protection client configurations. Deploy these antimalware policies to client computers. Then monitor compliance in the **Endpoint Protection Status** node under **Security** in the **Monitoring** workspace. Also use Endpoint Protection reports in the **Reporting** node.

For more information, see the following articles:

- [How to create and deploy antimalware policies](endpoint-antimalware-policies): Create, deploy, and monitor antimalware policies with a list of the settings that you can configure.
- [How to monitor Endpoint Protection](monitor-endpoint-protection): Monitoring activity reports, infected client computers, and more.
- [How to manage antimalware policies and firewall settings](endpoint-antimalware-firewall): Remediate malware found on client computers.
- [Log files for Endpoint Protection](../../core/plan-design/hierarchy/log-files#BKMK_EPLog)

## Manage Windows Defender Firewall

Endpoint Protection in Configuration Manager provides basic management of the Windows Defender Firewall on client computers. For each network profile, you can configure the following settings:

- Enable or disable the Windows Defender Firewall.
- Block incoming connections, including connections in the list of allowed programs.
- Notify the user when Windows Defender Firewall blocks a new program.

Note

Endpoint Protection supports managing the Windows Defender Firewall only.

For more information, see [How to create and deploy Windows Defender Firewall policies](create-windows-firewall-policies).

## Microsoft Defender for Endpoint

Configuration Manager manages and monitors Microsoft Defender for Endpoint, formerly known as Windows Defender for Endpoint. The Microsoft Defender for Endpoint service helps you detect, investigate, and respond to advanced attacks on your network. For more information, see [Microsoft Defender for Endpoints](defender-advanced-threat-protection).

## Endpoint Protection workflow

Use the following diagram to help you understand the workflow to implement Endpoint Protection in your Configuration Manager hierarchy.

![Endpoint protection workflow.](../media/endpoint-protection-workflow.gif)

## Recommendations

Use the following recommendations for Endpoint Protection in Configuration Manager.

### Configure custom client settings

When you configure client settings for Endpoint Protection, don't use the default client settings. The defaults apply settings to all computers in your hierarchy. Instead, configure custom client settings and assign these settings to collections of computers in your hierarchy.

When you configure custom client settings, you can do the following:

- Customize antimalware and security settings for different parts of your organization.
- Test the effects of running Endpoint Protection on a small group of computers before you deploy it to the entire hierarchy.
- Add more clients to the collection over time to phase your deployment of the Endpoint Protection settings.

### Distributing definition updates by using software updates

If you use Configuration Manager software updates to distribute definition updates, put definition updates in a package that doesn't include other software updates. This practice keeps the size of the definition update package smaller which allows it to replicate to distribution points more quickly.