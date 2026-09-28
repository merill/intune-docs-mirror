---
layout: Conceptual
title: Configuration Manager Console Extension - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-extension
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
description: Learn how the Configuration Manager console with an XML-based architecture can be easily extended.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 94da3dbd-0db4-3fa8-580a-3fe55a578f59
document_version_independent_id: eeea2171-d6e2-d96b-95bf-84abcf47d6a5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-extension.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/about-configuration-manager-console-extension
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/about-configuration-manager-console-extension.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 9980a76f-d3a5-77ca-2859-ce2099bd0e81
---

# Configuration Manager Console Extension - Configuration Manager | Microsoft Learn

The Configuration Manager console has an XML-based architecture that can be easily extended. The Configuration Manager console supports the following extensions:

## Actions

An action is a task or command accessed through either a context menu or the ribbon. Many standard actions are available, and you can extend them to add new functionality, such as displaying a dialog box or launching an application.

## Forms

You can extend the Configuration Manager console with dialog boxes or property sheets. You can also add new property pages to existing Configuration Manager console property sheets, such as the properties dialog for an object.

## Nodes

You can add new nodes to the Configuration Manager console.

## Views

You can create new views that are displayed in the result pane. You can also create new home pages. For example, you might want to add a new home page that is associated with a new navigation node that you have created.

## Wizards

You can integrate your own custom wizards into the Configuration Manager console by using a wizard framework of your choice.

## Management Classes

You can define your own custom classes that can be used by your Configuration Manager console extension. For more information, see [About console management classes](about-configuration-manager-console-management-classes).

## Unsupported Features

The Configuration Manager console doesn't support the following features:

### Wizard Creation

You can't create wizards by using the existing Configuration Manager console framework. You also can't modify or remove steps from the existing Configuration Manager wizards.

### Modification of Core Configuration Manager Console Items

Don't change or remove items in the core Configuration Manager console XML, because this could break the Configuration Manager console. The core XML is stored in *%ProgramFiles%*\Microsoft Endpoint Manager\AdminConsole\XmlStorage\ConsoleRoot.

### SMS 2003 IMMF Interfaces

The Configuration Manager console is built by using managed code and doesn't support the SMS 2003 IMMF interfaces.

### Registry-Based Extensions

Registry-based extensions, similar to those available in SMS 2003, aren't supported in the Configuration Manager console.

### Microsoft Management Console SDK Extensions

Extensions written with the Microsoft Management Console SDK aren't supported by the Configuration Manager console.

## Accessibility

When developing console extensions, they should be based on designs with accessibility considerations. For example, you can make use of color, layout, intelligent default values, sound, and exposing appropriate keyboard focus. By using various accessibility techniques, you'll make it easier for users with disabilities to use your software. For more information, see [Resources for designing accessible applications](/en-us/visualstudio/ide/reference/resources-for-designing-accessible-applications).