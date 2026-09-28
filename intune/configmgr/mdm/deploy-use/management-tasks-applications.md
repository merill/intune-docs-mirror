---
layout: Conceptual
title: Manage apps for on-premises MDM - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/mdm/deploy-use/management-tasks-applications
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
description: Manage applications for on-premises mobile device management (MDM) in Configuration Manager.
ms.date: 2020-01-13T00:00:00.0000000Z
ms.subservice: mdm
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 90b04cb1-b8af-5109-e780-aa8e93d1b4a6
document_version_independent_id: 84fe21c9-5a4c-7327-712d-749b5c569e68
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/mdm/deploy-use/management-tasks-applications.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/mdm/deploy-use/management-tasks-applications
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/mdm/deploy-use/management-tasks-applications.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2fdb256d-65a6-85b5-0c48-8ade4a6809f7
---

# Manage apps for on-premises MDM - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When you manage devices with Configuration Manager on-premises mobile device management (MDM), you can manage the following application types:

- Windows Phone app package (\*.xap file)
- Windows Phone app package (in the Windows Phone Store)
- Windows Installer through MDM
- Web Application

For more general information about managing Configuration Manager applications and deployment types, see [Management tasks for Configuration Manager applications](../../apps/deploy-use/management-tasks-applications).

## Create Windows Phone application

A Configuration Manager application has one or more deployment types. The deployment type includes the installation files and information that's required to deploy software to a device. A deployment type also has rules that specify when and how the software is deployed.

For the general steps to create an app and deployment types, see [create an application](../../apps/deploy-use/create-applications#bkmk_create).

Configuration Manager supports the following app file types For Windows mobile devices:

| Device type | Supported file types |
| --- | --- |
| Windows Phone 8 | xap |
| Windows Phone 8.1 | xap, appx, appxbundle |
| Windows 10 Mobile | xap, appx, appxbundle |

Deploy Windows Phone apps as **Available** or **Required**. Also use deployments to uninstall apps.

## Deploy and monitor apps

Deploy and monitor applications for mobile devices in Configuration Manager the same as you do for other devices, such as desktops and servers. For more information, see the following articles:

- [Deploy applications](../../apps/deploy-use/deploy-applications)
- [Monitor applications](../../apps/deploy-use/monitor-applications-from-the-console)

Review the following limitations specific to mobile devices:

- MDM-enrolled devices don't support simulated deployments, user experience, or scheduling settings.
- Don't add more than 100 locales to a single app. This action prevents the app from installing on the device.