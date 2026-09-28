---
layout: Conceptual
title: About status messages - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-configuration-manager-status-messages
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
description: Learn about status messages in Configuration Manager
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 10af8aee-88b7-16e3-ce32-a98b89db6200
document_version_independent_id: bf4aa7e1-839a-2993-eb20-1980d2aac523
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/manage/about-configuration-manager-status-messages.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/manage/about-configuration-manager-status-messages
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/manage/about-configuration-manager-status-messages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/1ae5c491-970a-4062-8301-6336e69f9026
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/f2c3e52e-3667-4e8a-bf11-20b9eaccdc8c
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: cf817eff-fb12-b61c-6093-04991da59545
---

# About status messages - Configuration Manager | Microsoft Learn

In Configuration Manager, status messages are the universal means for components to communicate information about their health to the Configuration Manager administrator. Status messages are similar to Windows NT Events; they have a severity, ID, description, and so on.

The Configuration Manager Status System is a fully-distributed, enterprise-wide aggregation and summarization system for status messages. Status messages flow from components to the Configuration Manager site servers and up the Configuration Manager site hierarchy.

The administrator configures how Configuration Manager processes the status messages at each site server in the hierarchy. This processing can include storing the status messages in a SQL Server database, replicating the messages to the parent Configuration Manager site, reporting the messages as Windows Events on the site server, and exporting the messages to another eventing or alerting application.

Certain kinds of status messages are automatically processed by Summarizer components that are running on the site servers. The Summarizers produce high-level data about the raw flows of status messages. Administrators monitor this data in the Configuration Manager console.

Status messages are similar to Windows events; they have a severity, ID, and description. They also support message insertion strings and named attribute values. This allows user-defined messages to be reported through the site.

## Types of Status Messages

### Predefined Status Messages

Each Configuration Manager component has a set of predefined status messages assigned to it. It's important that the context in which an application reports a predefined status message matches exactly the purpose of the Configuration Manager component status message. Otherwise, the integrity of the site might be affected by Configuration Manager misinterpreting the meaning of the status message. For more information, see [About Configuration Manager Component Status Messages](about-configuration-manager-component-status-messages).

### User-defined Generic Status Messages

Configuration Manager provides three types of user-defined generic status messages.

- Information
- Warning
- Error

    Along with the message type, insertion strings and attributes can be supplied. The text that is provided as the insertion string, when creating the status message, is the text seen in the user interface. This makes using generic messages simple, but it doesn't allow for localization. For more information, see [How to Read User-Defined Status Messages](how-to-read-user-defined-status-messages).

## Creating Status Messages on the Client

You can create events on client computers in the following ways:

### SMSEvent

[SMSEvent Class](../../../reference/core/servers/manage/smsevent-class) is a COM automation class that you use to raise user-defined status messages on a client. As a COM Automation object, it can readily be used by VBScript. For more information, see [SMSEvent Class](../../../reference/core/servers/manage/smsevent-class).

### SMSCSTAT.DLL

SMSCSTAT.DLL is a Win32 dynamic link library that is available on clients. It has been installed on Configuration Manager clients since SMS 2.0 Service Pack 1. It can't be easily be used by VBScript. For more information, see [About Using SMSCSTAT.DLL to Create Status Messages](about-using-smscstat.dll-to-create-status-messages).

### Management Point Interface

Using the management point interfaces, you can raise status messages that are defined by XML from client computers. The management point interfaces can't be used by VBScript. Using the management point interface is recommended for raising status messages on client computers that aren't running a Windows operating system.

## Creating Status Messages on the Site Server

You raise events on the server by creating instances of `SMS_StatusMessage`. For more information, see [How to Report User-Defined Status Messages](how-to-report-user-defined-status-messages).