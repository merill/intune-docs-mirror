---
layout: Conceptual
title: Configuration Manager programming - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/getting-started-with-configuration-manager-programming
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
description: Learn the basics of programming and automation with the Configuration Manager software development kit (SDK).
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: get-started
ms.collection: tier3
locale: en-us
document_id: b7d5e3b7-009a-39a2-1e8f-e9cdba9b6ed5
document_version_independent_id: 42615026-ab89-4c5b-5311-d179c1e46d19
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/getting-started-with-configuration-manager-programming.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/getting-started-with-configuration-manager-programming
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/getting-started-with-configuration-manager-programming.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: fab51410-2b96-d1b1-a54d-eb71344721d0
---

# Configuration Manager programming - Configuration Manager | Microsoft Learn

To get started with programming for Configuration Manager, it's beneficial to have a basic functional and architectural understanding of Configuration Manager. In addition, there are a number of key tools and resources that critical to validating and troubleshooting solutions. Below are tips and resources for someone new to programming for Configuration Manager.

Important

You should recognize that Configuration Manager, previously Systems Management Server (SMS), has quite a long history as a product. In reviewing namespaces, classes, methods, properties and log files you'll find many references containing "SMS" – in fact, most WMI classes start with "SMS\_" and the primary Configuration Manager WMI namespace is "SMS". Over the course of years, numerous legacy classes, methods and properties have accumulated – not apparent to an administrative user, but when programming the history/legacy can be confusing.

## Functional understanding

To successfully automate or extend Configuration Manager, it is incredibly important to gain a functional understanding of the product. Configuration Manager is multi-tiered, distributed management system, most often spread over numerous servers and numerous locations. For more information, see [Fundamentals of Configuration Manager](../../../core/understand/fundamentals).

### More resources

#### Books

- [System Center 2012 Configuration Manager: Mastering the Fundamentals](https://www.amazon.com/System-Center-2012-Configuration-Manager/dp/9197939048)
- [System Center 2012 Configuration Manager (SCCM) Unleashed](https://www.amazon.com/System-Center-Configuration-Manager-Unleashed/dp/0672334372/ref=sr_1_1?s=books&amp;ie=UTF8&amp;qid=1382812114&amp;sr=1-1&amp;keywords=System+Center+2012+Configuration+Manager+%28SCCM%29+Unleashed)
- [Microsoft System Center 2012 Configuration Manager: Administration Cookbook](https://www.amazon.com/Microsoft-System-Center-Configuration-Manager/dp/1849684944/ref=sr_1_1?s=books&amp;ie=UTF8&amp;qid=1382812164&amp;sr=1-1&amp;keywords=Microsoft+System+Center+2012+Configuration+Manager%3A+Administration+Cookbook)

#### Videos

- [YouTube: Technical Deep Dive: Configuration Manager 2012 Technical Overview](https://www.youtube.com/watch?v=qLACm3910_A)

#### Forums

- [Configuration Manager on Microsoft Q&A](/en-us/answers/products/mem)
- [windows-noob.com: Configuration Manager 2012](https://www.windows-noob.com/forums/index.php?/forum/92-setup-sccm-2012/)

## Architectural understanding

Configuration Manager is multi-tiered, distributed management system. It's important to understand the general architecture of Configuration Manager. Below is a link to an overview of the Configuration Manager architecture.

- [Architectural Overview](architectural-overview)

In addition to the architectural information, there are several key points that commonly confuse administrators and programmers new to Configuration Manager.

- **Server:** In a general sense, most programming actions (in particular, automation) take place on a Configuration Manager site server. Actions or configuration changes are propagated throughout the Configuration Manager hierarchy to the clients via policy. Policy is pulled down by the client on a configurable polling interval **NOT** pushed immediately to the client by the server. In general, once a client is installed, there is no direct communication from the site server to the client or the client to the site server – all communication takes place through intermediary server roles.
- **Client:** Configuration Manager clients are systems and devices managed by Configuration Manager. A 'server' can be a Configuration Manger client. An Exchange server, an Active Directory server, and a Configuration Manager server can all be Configuration Manager clients. In addition, Windows 10, Windows Phone, and macOS devices can all be Configuration Manager clients.

Configuration Manager clients receive policy by periodically polling a Configuration Manager Management Point. The polling interval for retrieving basic policy is configurable, as are other settings. Because of this, there are inherent delays in client targeted actions initiated from the Configuration Manager site server.

- **Console:** Remote Configuration Manager console binaries and files are not automatically updated when changes are made on the site server. Modifications and extensions must be copied to systems running the Configuration Manager console, either manually or using Configuration Manager Application Management/Software Distribution.
- **SMS Provider vs SQL Server:** Although Configuration Manager leverages SQL Server for data storage, SQL Server is **NOT** the primary programming interface to Configuration Manager. The primary programming interface to Configuration Manager is the SMS Provider (WMI) - object creation and modification **must** be done via the SMS Provider. You should consider SQL Server as providing read-only access to Configuration Manager data for querying and reporting purposes. This is not a matter of permissions, rather matter of maintaining data integrity.

## Namespaces and Classes

### Server

**Primary WMI Namespace:** ROOT\SMS\SITE\_&lt;site code&gt;

**Server WMI Classes:**[Configuration Manager API reference](../../reference/configuration-manager-reference)

### Client

**Primary WMI Namespace:** ROOT\CCM

**Client WMI Classes:**[Configuration Manager API reference](../../reference/configuration-manager-reference)

Important

The client-side programming story for Configuration Manager is evolving to be primarily WMI-based. In the past, a set of client-side COM classes were the primary method used to access client functionality, although additional client-side WMI classes/methods were also used. With the release of System Center 2012 Configuration Manager, the focus is shifting to a set of WMI classes in the namespace: **root/ccm/ClientSDK**. Understandably, an abstraction, in the form of COM or specific SDK classes, provides a useful abstraction from underlying architectural changes over the course of product updates.

### Console

**Console-related Managed Classes:**

- Microsoft.configurationmanagement.exe
- Microsoft.configurationmanagement.managementprovider.dll
- Microsoft.ConfigurationManagement.DialogFoundation.dll
- AdminUI.DialogFoundation.dll

**Introductory Configuration Manager Console topics:**

- [About Configuration Manager Console Extension](../servers/console/about-configuration-manager-console-extension)
- [Configuration Manager Console Extension Architecture](../servers/console/console-extension-architecture)

## Programming fundamentals

The Configuration Manager Programming Fundamentals section of the SDK provides examples of how to work with the various types of objects and structures available in Configuration Manager. Configuration Manager contains some objects/concepts that can be initially confusing. Of particular interest are **embedded properties** (used primary with the Site Control File) and **lazy properties** (used throughout the Configuration Manager classes). Below are links to the Programming Fundamentals (and other sub-sections) of the SDK. These sections contain code examples showing how to work with the various object types.

Important

The SDK most often provides code examples in VBScript and C#. This does not mean that other languages will not work with the SMS Provider. The SMS Provider is language agnostic, as long as the correct objects and constructs can be exchanged. Use the language (tool) that is most appropriate for your environment. C# is used internally as a baseline for testing the SDK code snippets, so examples of object manipulation and code constructs will most often be provided in C#. If you use another language, you should be comfortable translating from C# to your language of choice.

- [SMS Provider fundamentals](sms-provider-fundamentals)
- [Objects overview](configuration-manager-objects-overview)
- [About the site control file](about-the-configuration-manager-site-control-file)
- [About errors](about-configuration-manager-errors)

## Basic tools

### WBEMTEST

If you spend much time around Configuration Manager you become aware that much of it runs through WMI. WMI is "Windows Management Instrumentation" and is Microsoft's implementation of an Internet standard called Web Based Enterprise Management (WBEM). There are many WMI tools out there. However, WBEMTEST is immediately available on most systems, rather than having to be downloaded first. You might think of it like Notepad.exe – there are text editors with richer capabilities available, but Notepad.exe is always there when you need to view or create a text file.

[Introduction to WBEMTEST](introduction-to-wbemtest)

Tip

Internally, the most commonly used tool when troubleshooting SMS Provider related issues (object creation, modification and deletion) is WBEMTEST.

### CMTrace

**CMTrace:** CMTrace is a customized log file viewer that is useful in monitoring and troubleshooting Configuration Manager. CMTrace provides a continuous view of the log file changes (rather than having to reload to monitor logged activity) and is particularly useful when monitoring/troubleshooting object creation or modification via the SMS Provider (see the SMSProv.log below).

CMTrace can be found on the Configuration Manager site server, under the "&lt;Configuration Manager Installation Directory&gt;\tools" folder.

**SMSProv.log:** SMS Provider log file (&lt;Configuration Manager Installation Directory&gt;\Logs\SMSProv.log) logs the activity of the SMS Provider and provides low-level information that is useful to monitor/troubleshoot issues when programmatically creating or modifying Configuration Manager objects via the SMS Provider.

### Client Spy and Policy Spy

**Client Spy:** A tool that helps you troubleshoot issues related to software distribution, inventory, and software metering on System Center 2012 Configuration Manager clients.

**Policy Spy:** A policy viewer that helps you review and troubleshoot the policy system on System Center 2012 Configuration Manager clients.

## Basic Configuration Manager program example

Below is link to a very simple Configuration Manager program showing some basic operations common to many Configuration Manager programs:

- `Connect` to the SMS Provider
- `List` all programs
- **Create** a new program
- **Modify** an existing program
- **Delete** an existing program
- [Simple Example of List, Create, Modify, and Delete](simple-example-of-list--create--modify--and-delete)