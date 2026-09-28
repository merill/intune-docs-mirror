---
layout: Conceptual
title: Create Windows Embedded applications - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/get-started/creating-windows-embedded-applications
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
description: See which considerations you must take into account when you create and deploy applications for Windows Embedded devices.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 074ce66a-3c65-e7c3-cd14-6eeeb4a436ba
document_version_independent_id: b4721b87-fe62-798b-ccf5-83f5de0f8623
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/get-started/creating-windows-embedded-applications.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/get-started/creating-windows-embedded-applications
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/get-started/creating-windows-embedded-applications.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b9e11d3d-97fb-ab95-d03e-b91a424325a3
---

# Create Windows Embedded applications - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

In addition to the other Configuration Manager requirements and procedures for creating an application, you must also take the following considerations into account when you create and deploy applications for Windows Embedded devices.

## General considerations

- When you deploy applications to Windows Embedded devices that are enabled for write filtering, you can specify whether to disable the write filter on the device during the app deployment. You can then choose to restart the write filter after the app deployment. If the write filter isn't disabled, the software is deployed to a temporary overlay. This means that unless another deployment forces changes to persist, the software will no longer be installed when the device restarts.
- When you deploy an application to a Windows Embedded device, make sure that the device is a member of a collection that has a configured maintenance window. This lets you manage when the write filter is disabled and enabled, and when the device restarts.
- The setting that controls the write filter behavior is a check box named **Commit changes at deadline or during a maintenance window (requires restarts)**.

## Tips for deploying applications

**Use required applications rather than available applications for Windows Embedded devices that have write filters enabled.** Because users can't install apps from Software Center on a Windows Embedded device that has write filters enabled, always deploy applications with a deployment purpose of **required** rather than **available** to these devices. Typically, this isn't a problem because computers that run a Windows Embedded operating system often run a single application that must run in the same way for multiple users. Because of this, these devices are highly managed and locked down by the IT department. Required applications are well-suited to this scenario.

However, if users do run more than one application on embedded devices when write filters are enabled, educate these users about the following limitations:

- Users can't install required software from Software Center.
- Users can't change their business hours in the Options tab of Software Center.
- Users can't postpone the installation of a required application.

In addition, low-rights users can't sign in during a maintenance period if Configuration Manager is committing changes for software installations and updates. During this period, users see a message informing them that the device is unavailable because it's being serviced.

**Do not deploy applications to Windows Embedded devices that have write filters enabled if the applications require the user to accept the license terms.** When write filters are disabled so that Configuration Manager can install software on embedded devices, low-rights users can't sign in to the device. If the installation requires the user to accept the license terms, this won't be possible and the installation will fail. Make sure that you don't deploy software to Windows Embedded devices if the installation requires user interaction. You can use the Applicable Platforms list to filter these operating systems.