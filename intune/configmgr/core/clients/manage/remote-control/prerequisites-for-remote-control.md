---
layout: Conceptual
title: Remote control prerequisites - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/remote-control/prerequisites-for-remote-control
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
description: Get the prerequisites for remote control in Configuration Manager.
ms.date: 2022-03-18T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 1353b374-cf89-dcd0-6975-8c2d3cbf8a5b
document_version_independent_id: 2842d2cb-42dc-ad27-9eaf-ebd35b4a7497
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/remote-control/prerequisites-for-remote-control.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/remote-control/prerequisites-for-remote-control
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/remote-control/prerequisites-for-remote-control.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 239ccccb-4174-27b8-4f21-6bbf397ea9e4
---

# Remote control prerequisites - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Remote control in Configuration Manager has external dependencies and dependencies in the product.

## Dependencies external to Configuration Manager

To help improve performance, install the most up-to-date video driver on client devices.

You can't use Configuration Manager remote control to remotely administer client computers that run versions of the Configuration Manager client earlier than current branch.

Note

No Windows services are required as an external dependency for remote control.

### Supported operating systems for the remote control viewer

The remote control viewer is supported on all operating systems that are supported for the Configuration Manager console. For information, see [Supported configurations for Configuration Manager consoles](../../../plan-design/configs/supported-operating-systems-consoles).

The following OS versions don't support the remote control viewer, but they do support the remote control client:

- Windows Embedded
- Windows Embedded for Point of Service (POS)
- Windows Fundamentals for Legacy PCs

## Configuration Manager dependencies

### Enable remote control

By default, remote control isn't enabled when you install Configuration Manager. For more information about how to enable and configure remote control, see [Configure remote control](configuring-remote-control).

### Reporting

Before you can run reports for remote control, install the reporting services point site system role. For more information, see [Introduction to reporting](../../../servers/manage/introduction-to-reporting).

### Security permissions

- To access collection resources and to start a remote control session from the Configuration Manager console, your account needs the **Read**, **Read Resource**, and **Remote Control** permissions for the **Collection** object.
- The **Remote Tools Operator** security role includes the permissions that are required to manage remote control in Configuration Manager.
- Permitted viewers must be given permission to use remote control by adding these users to the **Permitted viewers of Remote Control and Remote Assistance** list in the **Remote Tools** client settings.

For more information, see [Configure role-based administration](../../../servers/deploy/configure/configure-role-based-administration).

### Remote clients

Remote tools aren't supported for clients that are connected remotely. For example, you can't remote control a client that communicates with the site through a cloud management gateway (CMG). For more information about the network ports required for remote tools, see [Ports used in Configuration Manager](../../../plan-design/hierarchy/ports#BKMK_PortsConsole-Client).

Tip

For tenant-attached devices, remote tools are available in the Microsoft Intune admin center. For more information, see [Support for remote tools](../cmg/supported-configurations#bkmk_note3).