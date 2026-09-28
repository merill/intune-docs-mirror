---
layout: Conceptual
title: What is Configuration Manager? - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/understand/introduction
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
description: Learn the basics of Microsoft Configuration Manager.
ms.date: 2024-06-19T00:00:00.0000000Z
ms.subservice: core-infra
ms.custom: intro-overview
ms.topic: overview
ms.collection:
- tier3
- essentials-overview
locale: en-us
document_id: 18d310b4-e073-e8f0-cd76-6abd2073d166
document_version_independent_id: 715571fa-a919-b81f-5563-cd6218ae4ff4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/understand/introduction.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/understand/introduction
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/understand/introduction.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: c6c740bd-833f-9015-90a2-ffab5bfe9073
---

# What is Configuration Manager? - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configuration Manager is part of the Microsoft Intune family of products.

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune, without a complex migration, and with simplified licensing. Continue to leverage your existing Configuration Manager investments, while taking advantage of the power of the Microsoft cloud at your own pace.

The following Microsoft management solutions are all now part of the **Microsoft Intune** brand:

- [Configuration Manager](../../)
- [Intune](../../../intune-service/)
- [Endpoint analytics](../../../endpoint-analytics/)
- [Windows Autopilot](/en-us/autopilot/index)

For more information, see [Microsoft Configuration Manager FAQ](microsoft-endpoint-manager-faq).

## Introduction

Use Configuration Manager to help you with the following systems management activities:

- Increase IT productivity and efficiency by reducing manual tasks and letting you focus on high-value projects.
- Maximize hardware and software investments.
- Empower user productivity by providing the right software at the right time.

Configuration Manager helps you deliver more effective IT services by enabling:

- Secure and scalable deployment of applications, software updates, and operating systems.
- Real-time actions on managed devices.
- Cloud-powered analytics and management for on-premises and internet-based devices.
- Compliance settings management.
- Comprehensive management of servers, desktops, and laptops.

Configuration Manager extends and works alongside many Microsoft technologies and solutions. For example, Configuration Manager integrates with:

- Microsoft Intune to co-manage a wide variety of mobile device platforms
- Microsoft Azure to host cloud services to extend your management services
- Windows Server Update Services (WSUS) to manage software updates
- Certificate Services
- Exchange Server and Exchange Online
- Group Policy
- DNS
- Windows Automated Deployment Kit (Windows ADK) and the User State Migration Tool (USMT)
- Windows Deployment Services (WDS)
- Remote Desktop and Remote Assistance

Configuration Manager also uses:

- Active Directory Domain Services and Microsoft Entra ID for security, service location, configuration, and to discover the users and devices that you want to manage.
- Microsoft SQL Server as a distributed change management database—and integrates with SQL Server Reporting Services (SSRS) to produce reports to monitor and track management activities.
- Site system roles that extend management functionality and use the web services of Internet Information Services (IIS).
- Delivery Optimization, Windows Low Extra Delay Background Transport (LEDBAT), Background Intelligent Transfer Service (BITS), BranchCache, and other peer caching technologies to help manage content on your networks and between devices.

To be successful with Configuration Manager in a production environment, thoroughly plan and test the management features. Configuration Manager is a powerful management application, with the potential to affect every computer in your organization. When you deploy and manage Configuration Manager with careful planning and consideration of your business requirements, Configuration Manager can reduce your administrative overhead and total cost of ownership.

## User interfaces

### The Configuration Manager console

After you install Configuration Manager, use the Configuration Manager console to configure sites and clients, and to run and monitor management tasks. This console is the main point of administration, and lets you manage multiple sites.

You can install the Configuration Manager console on additional computers, and restrict access and limit what administrative users can see in the console by using Configuration Manager role-based administration.

For more information, see [Use the Configuration Manager console](../servers/manage/admin-console).

### Software Center

**Software Center** is an application that's installed when you install the Configuration Manager client on a Windows device. Users use Software Center to request and install software that you deploy. Software Center lets users do the following actions:

- Browse for and install applications, software updates, and new OS versions
- View their software request history
- View device compliance against your organization's policies

You can also show custom tabs in Software Center to meet additional business requirements.

For more information, see the [Software Center user guide](software-center).