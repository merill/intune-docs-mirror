---
layout: Conceptual
title: Client management fundamentals - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/fundamentals-of-client-management-tasks
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
description: Learn about tasks that you run to manage Configuration Manager clients.
ms.date: 2016-12-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 478292ef-249b-cfe5-60f7-fa05a40155cf
document_version_independent_id: 33d66032-e8d1-650b-a2e2-5b4f0b88762c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/fundamentals-of-client-management-tasks.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/fundamentals-of-client-management-tasks
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/fundamentals-of-client-management-tasks.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 84b76437-35c0-b230-2495-140e69ed10b5
---

# Client management fundamentals - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

After you install the Configuration Manager clients, there are several tasks that you run to manage the clients. Some of the tasks are run from the Configuration Manager console. Other tasks are run from the Configuration Manager client application. The Configuration Manager client application is installed with the Configuration Manager client software.

## Configuration Manager console tasks

In the Configuration Manager console, you can perform various client management tasks:

- Deploy applications, software updates, maintenance scripts, and operating systems. Configure installation for a specific date and time, make the software available for users to install when they are requested, or configure applications to be uninstalled.
- Help protect computers from malware and security threats, and notify you when problems are detected.
- Define client configuration settings that you want to monitor, and remediate if they are out of compliance.
- Collect hardware and software inventory information, which includes monitoring and reconciling license information from Microsoft.
- Troubleshoot computers by using remote control.
- Implement power management settings to manage and monitor the power consumption of computers.

The Configuration Manager console monitors the previous tasks in near real time. Notification and status information for each task is available in the Configuration Manager console. To capture data and historical trending, use the integrated reporting capabilities of SQL Server Reporting Services. Clients submit details to the site as client status. Client status information provides data about the health of the client and client activity, and is viewed in the console or by using the built-in reports for Configuration Manager. This data helps identify computers that are not responding and in some cases, problems are automatically remediated.

For more information about management tasks for clients, see [How to manage clients](../clients/manage/manage-clients). To learn about using reports, see [Introduction to reporting](../servers/manage/introduction-to-reporting).

## Configuration Manager client application

When you install the Configuration Manager client software, the Configuration Manager client application is installed too. Unlike Software Center, the Configuration Manager client application is designed for the help desk rather than for the end user. Some configuration options require local administrative permissions, and most options require technical knowledge about how the Configuration Manager client application works. You can use this application to perform the following tasks on a client:

- View properties about the client, such as the build number, its assigned site, the management point it is communicating with, and whether the client is using a public key infrastructure (PKI) certificate or a self-signed certificate.
- Confirm that the client has successfully downloaded a client policy after the client is installed for the first time. Also confirm that the client settings are enabled or disabled as expected, according to the client settings that are configured in the Configuration Manager console.
- Start client actions. For example, download the client policy if there was a recent configuration change in the Configuration Manager console, and you do not want to wait until the next scheduled time.
- Manually assign a client to a Configuration Manager site or try to find a site. Then specify the Domain Name System (DNS) suffix for management points that publish to DNS.
- Configure the client cache that temporarily stores files. Then delete files in the cache if you require more disk space to install software.
- Configure settings for Internet-based client management.
- View configuration baselines that were deployed to the client, initiate compliance evaluation, and view compliance reports.