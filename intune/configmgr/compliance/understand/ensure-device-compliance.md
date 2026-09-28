---
layout: Conceptual
title: Ensure device compliance - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/compliance/understand/ensure-device-compliance
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
description: Manage the configuration and compliance of devices in your organization by using Configuration Manager.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: compliance
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: cf4de73b-59bf-8683-14f1-8d211c93e8ff
document_version_independent_id: f8725972-62a7-424a-6150-4a7b555fc4f0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/compliance/understand/ensure-device-compliance.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/compliance/understand/ensure-device-compliance
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/compliance/understand/ensure-device-compliance.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 023331ac-5bd3-bccf-a2b6-c18b6373475a
---

# Ensure device compliance - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Compliance settings in Configuration Manager gives you the tools and resources you need to manage the configuration and compliance of devices in your organization. This helps you support the following business requirements:

- Compare the configuration of Windows PCs, Macs computers, servers, and mobile devices you manage against best practices configurations you create, or obtain from other vendors
- Identify unauthorized device configurations
- Report compliance with regulatory policies and in-house security policies
- Identify security vulnerabilities
- Provide the help desk with the information to detect probable causes of reported incidents and problems by identifying noncompliant configurations
- Automatically remediate some noncompliant settings on mobile devices
- Remediate noncompliance by deploying applications, packages and programs, or scripts to a collection that is automatically populated with devices that report that they are out of compliance

## Get started

Learn the basics about compliance settings, and the tasks you can accomplish with them.

[Get started with compliance settings](../get-started/get-started-with-compliance-settings)

## Plan and design

Before you start working with compliance settings, make sure you have implemented the necessary prerequisites that you'll find in this topic.

[Plan for and configure compliance settings](../plan-design/plan-for-and-configure-compliance-settings)

## Common tasks

In this section, you'll find some common scenarios that will help you learn to use compliance settings in Configuration Manager.

[Common tasks for managing compliance](../plan-design/common-tasks-for-managing-compliance)

## Remote connection profiles

This configuration item type allows you to configure your user's PCs to remotely connect to work computers when they are not connected to the domain or if their personal computers are connected over the Internet.

[Create remote connection profiles](../deploy-use/create-remote-connection-profiles)

## User data and profiles

This configuration item type contains settings that can manage folder redirection, offline files and roaming profiles on computers that run Windows 8 and later for users in your hierarchy.

[Create user data and profiles configuration items](../deploy-use/create-user-data-and-profiles-configuration-items)

## Windows edition upgrade policy

The edition upgrade policy lets you automatically upgrade Windows 10 devices to a newer version. You can specify a product key to upgrade Windows 10 desktop versions, or a license file that can be used to upgrade devices running Windows 10 Mobile and Windows 10 Holographic.

[Upgrade Windows devices with the edition upgrade policy](../deploy-use/upgrade-windows-version)