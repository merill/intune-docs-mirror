---
layout: Conceptual
title: Protect computers from malware - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/scenarios-endpoint-protection
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
description: Learn how to implement Endpoint Protection in Configuration Manager to protect computers from malware attacks.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 90bc5ee0-910d-5875-cecd-6f80b95d9554
document_version_independent_id: 33e673f8-16ba-fa92-a60c-35880bc3de0b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/scenarios-endpoint-protection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/scenarios-endpoint-protection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/scenarios-endpoint-protection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: abb7fb34-e54a-0fc0-7d27-22ec3b89f9e5
---

# Protect computers from malware - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article provides an example scenario for how you can implement Endpoint Protection in Configuration Manager to protect computers in your organization from malware attacks.

## Scenario overview

Configuration Manager is installed and used at Woodgrove Bank. The bank currently uses Endpoint Protection to protect computers against malware attacks. Additionally, the bank uses Windows Group Policy to ensure that the Windows Firewall is enabled on all computers in the company and that users are notified when Windows Firewall blocks a new program.

The Configuration Manager administrators have been asked to upgrade the Woodgrove Bank antimalware software to Endpoint Protection so that the bank can benefit from the latest antimalware features and be able to centrally manage the antimalware solution from the Configuration Manager console.

## Business requirements

This implementation has the following requirements:

- Use Configuration Manager to manage the Windows Firewall settings that are currently managed by Group Policy.
- Use Configuration Manager software updates to download malware definitions to computers. If software updates aren't available, for example if the computer isn't connected to the corporate network, computers must download definition updates from Microsoft Update.
- Users' computers must perform a quick malware scan every day. Servers, however, must run a full scan every Saturday, outside business hours, at 1 A.M.
- Send an email alert whenever any one of the following events occurs:

    - Malware is detected on any computer
    - The same malware threat is detected on more than 5 percent of computers
    - The same malware threat is detected more than 5 times in any 24-hour period
    - More than 3 different types of malware are detected in any 24-hour period

    The admins then do the following steps to implement Endpoint Protection:

## Steps to implement Endpoint Protection

| Process | Reference |
| --- | --- |
| The admins review the available information about the basic concepts for Endpoint Protection in Configuration Manager. | For overview information about Endpoint Protection, see [Endpoint Protection](endpoint-protection). |
| The admins install the Endpoint Protection site system role on one site system server only, at the top of the Woodgrove Bank hierarchy. | For more information about how to install the Endpoint Protection site system role, see "Prerequisites" in [Configure Endpoint Protection](endpoint-protection-configure). |
| The admins configure Configuration Manager to use an SMTP server to send the email alerts.**Note:** You must configure an SMTP server only if you want to be notified by email when an Endpoint Protection alert is generated. | For more information, see [Configure alerts in Endpoint Protection](endpoint-configure-alerts). |
| The admins create a device collection that contains all computers and servers to install the Endpoint Protection client. They name this collection **All Computers Protected by Endpoint Protection**.**Tip:** You can't configure alerts for user collections. | For more information about how to create collections, see [How to create collections](../../core/clients/manage/collections/create-collections) |
| The admins configure the following alerts for the collection: 1) **Malware is detected**: The admins configure an alert severity of **Critical**. 2) **The same type of malware is detected on a number of computers**: The admins configure an alert severity of **Critical** and specify that the alert will be generated when more than 5 percent of computers have malware detected. 3) **The same type of malware is repeatedly detected within the specified interval on a computer**: The admins configure an alert severity of Critical and specify that the alert will be generated when malware is detected more than 5 times in a 24-hour period. 4) **Multiple types of malware are detected on the same computer within the specified interval**: The admins configure an alert severity of Critical and specify that the alert will be generated when more than 3 types of malware are generated in a 24-hour period. The value for **Alert Severity** indicates the alert level that will be displayed in the Configuration Manager console and in alerts that they receive in an email message. They additionally select the option **View this collection in the Endpoint Protection dashboard** so that they can monitor the alerts in the Configuration Manager console. | See "Configure Alerts for Endpoint Protection" in [Configuring Endpoint Protection](endpoint-configure-alerts). |
| The admins configure Configuration Manager software updates to download and deploy definition updates three times a day by using an automatic deployment rule. | For more information, see the "Using Configuration Manager Software Updates to Deliver Definition Updates" section in [Use Configuration Manager software updates to deliver definition updates](endpoint-definitions-configmgr). |
| The admins examine the settings in the default antimalware policy, which contains recommended security settings from Microsoft. For computers to perform a quick scan every day to, they change the following settings: 1) **Run a daily quick scan on client computers**: **Yes**. 2) **Daily quick scan schedule time**: **9:00 AM**. The admins note that **Updates distributed from Microsoft Update** is selected by default as a definition update source. This fulfills the business requirement that computers download definitions from Microsoft Update when they can't receive Configuration Manager software updates. | See [How to create and deploy antimalware policies for Endpoint Protection](endpoint-antimalware-policies). |
| The admins create a collection that contains only the Woodgrove Bank servers named **Woodgrove Bank Servers**. | See [How to create collections](../../core/clients/manage/collections/create-collections) |
| The admins create a custom antimalware policy named **Woodgrove Bank Server Policy**. They add only the settings for **Scheduled scans** and make the following changes:**Scan type**: **Full** **Scan day**: **Saturday** **Scan time**: **1:00 AM** **Run a daily quick scan on client computers**: **No**. | See [How to create and deploy antimalware policies for Endpoint Protection](endpoint-antimalware-policies). |
| The admins deploy the **Woodgrove Bank Server Policy** custom antimalware policy to the **Woodgrove Bank Servers** collection. | See "To deploy an antimalware policy to client computers" [How to create and deploy antimalware policies for Endpoint Protection](endpoint-antimalware-policies) article. |
| The admins create a new set of custom client device settings for Endpoint Protection and names these **Woodgrove Bank Endpoint Protection Settings**.**Note:** If you don't want to install and enable Endpoint Protection on all clients in your hierarchy, make sure that the options **Manage Endpoint Protection client on client computers** and **Install Endpoint Protection client on client computers** are both configured as **No** in the default client settings. | For more information, see [Configure Custom Client Settings for Endpoint Protection](endpoint-protection-configure-client). |
| They configure the following settings for Endpoint Protection:**Manage Endpoint Protection client on client computers**: **Yes** This setting and value ensures that any existing Endpoint Protection client that is installed becomes managed by Configuration Manager.**Install Endpoint Protection client on client computers**: **Yes**. |  |
| The admins deploy the **Woodgrove Bank Endpoint Protection Settings** client settings to the **All Computers Protected by Endpoint Protection** collection. | See "Configure Custom Client Settings for Endpoint Protection" in [Configuring Endpoint Protection in Configuration Manager](endpoint-antimalware-policies). |
| The admins use the Create Windows Firewall Policy Wizard to create a policy by configuring the following settings for the domain profile: 1) **Enable Windows Firewall**: **Yes** 2)**Notify the user when Windows Firewall blocks a new program**: **Yes** | See [How to create and deploy Windows Firewall policies for Endpoint Protection](create-windows-firewall-policies) |
| The admins deploy the new firewall policy to the collection **All Computers Protected by Endpoint Protection** that they created earlier. | See "To deploy a Windows Firewall policy" in the [How to create and deploy Windows Firewall policies for Endpoint Protection](create-windows-firewall-policies) |
| The admins use the available management tasks for Endpoint Protection to manage antimalware and Windows Firewall policies, perform on-demand scans of computers when necessary, force computers to download the latest definitions, and to specify any further actions to take when malware is detected. | See [How to manage antimalware policies and firewall settings for Endpoint Protection](endpoint-antimalware-firewall) |
| The admins use the following methods to monitor the status of Endpoint Protection and the actions that are taken by Endpoint Protection: 1) By using the **Endpoint Protection Status** node under **Security** in the **Monitoring** workspace. 2) By using the **Endpoint Protection** node in the **Assets and Compliance** workspace. 3) By using the built-in Configuration Manager reports. | See [How to monitor Endpoint Protection](monitor-endpoint-protection) |

The admins report a successful implementation of Endpoint Protection to their manager, and confirms that the computers at Woodgrove Bank are now protected from antimalware, according to the business requirements that they were given.