---
layout: Conceptual
title: Console Extension Architecture - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-extension-architecture
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
description: The Configuration Manager console architecture is built on the following four distinct layers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 9a0e72c9-c1da-5d21-cc99-6837b9b77b74
document_version_independent_id: cad48fd3-8440-8b48-7c37-2bfc815aba58
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/console-extension-architecture.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/console-extension-architecture
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/console-extension-architecture.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 18af13ce-237a-077a-2c7f-54cc12846dcf
---

# Console Extension Architecture - Configuration Manager | Microsoft Learn

The Configuration Manager console architecture is built on the following four distinct layers.

- SMS Provider
- Managed SMS Provider SDK
- User interface framework
- Configuration Manager console XML

## SMS Provider in Configuration Manager

The SMS Provider is essentially the same as the SMS 2007 Provider, with the addition of new classes that support new Configuration Manager features. You can access the SMS Provider through the usual WBEM interfaces, but for managed code you must use the managed SMS Provider SDK.

## Managed SMS Provider SDK

The managed SMS Provider SDK provides a managed code library that abstracts the SMS Provider. It provides .NET Framework classes and interfaces that connect to the SMS Provider, make queries, and otherwise manipulate Configuration Manager objects and the site control file. You can use the managed SMS Provider SDK in stand-alone applications, or you can use the user interface framework to extend the existing Configuration Manager console.

## User Interface Framework

The user interface framework lies on top of the managed SMS Provider SDK. The user interface framework provides functionality for dialog boxes and the Configuration Manager console, and it provides user interface validation within the Configuration Manager console. You can extend this user interface framework to add your own forms to the Configuration Manager console, or you can integrate your own forms within existing Configuration Manager console forms.

## Configuration Manager Console XML

The Configuration Manager console XML defines how the Configuration Manager console looks and behaves. The XML defines nodes, queries, actions, forms, and everything else that is necessary to render the Configuration Manager console hierarchy, the results pane, and the action pane.

The XML files that are used by the Configuration Manager console are stored under %*ProgramFiles%*\Microsoft Endpoint Manager\AdminConsole\XmlStorage\. The following table shows the subfolders.

| Folder | Description |
| --- | --- |
| ConsoleRoot | This folder contains various XML files that define built in user interface elements and classes. ManagementClassDescriptions.xml: definitions for the SMS Provider classes. ConnectedConsole.xml: definitions for sticky nodes and go-to navigation. AssetManagementNode.xml, MonitoringNode.xml, SiteConfigurationNode.xml, SoftwareLibraryNode.xml: definitions for each workspace in the Configuration Manager console. |
| Extensions | Location for XML that is related to the SMS Provider. There are four types of extension folders: - Actions. XML files for Configuration Manager console actions. For more information, see [About Configuration Manager console actions](configuration-manager-actions).- Forms. XML files for form extensions to the Configuration Manager console. For more information, see [About console forms](about-configuration-manager-console-forms).- Nodes. XML files for node extensions to the Configuration Manager console. For more information, see [About console nodes](about-configuration-manager-console-nodes).- Management Classes. XML files for management class extensions to the Configuration Manager console. For more information, see [About console management classes](about-configuration-manager-console-management-classes). |
| Other | Various helper XML files. |
| Validation | Validation rules for the Configuration Manager console forms. |