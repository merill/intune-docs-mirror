---
layout: Conceptual
title: Configuration Manager Actions - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/configuration-manager-actions
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
ms.date: 2016-09-20T00:00:00.0000000Z
description: Learn about the Configuration Manager console actions that let you perform routine or custom tasks.
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 9df6fa32-0a35-4b0e-bf24-fabe430812c8
document_version_independent_id: 4f191a63-1080-fd0d-77da-f41799ce4bfc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/configuration-manager-actions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/configuration-manager-actions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/configuration-manager-actions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
platformId: d9b61056-9153-2d18-82a7-404f3bf3b46d
---

# Configuration Manager Actions - Configuration Manager | Microsoft Learn

Configuration Manager console actions are tasks or commands that are performed by making context menu or action panel selections. There are a number of standard action types such as cut, paste, and properties. You can also add your own custom actions to perform tasks such as running programs and displaying dialog boxes. You can restrict the availability of actions to such criteria as regular expressions, security permissions, and method call results.

In the Configuration Manager console, actions are defined in XML by the [ActionDescription](/en-us/previous-versions/system-center/developer/cc147252%28v=msdn.10%29) element.

## Standard Actions

A custom action can be associated with several standard actions. For example, a `ShowDialog` action can be associated with a `Properties` standard action. In this case, a property page is integrated into the properties property sheet for a selected object.

The standard actions are:

- `Delete`
- `Refresh`
- `Properties`

## Custom Actions

You can define the following custom actions.

| Action | Description |
| --- | --- |
| [Configuration Manager Executable Action](executable-action) | Runs a program or opens a file by using the program registered with Windows. |
| [Configuration Manager ShowDialog Action](showdialog-action) | Opens a dialog box. |
| [Configuration Manager Report Action](report-action) | Opens a report. |
| [Configuration Manager AssemblyType Action](assemblytype-action) | Defines the type and assembly for a method that is called. |
| [Configuration Manager Group Action](group-action) | Creates a menu group, also known as a submenu. |
| Separator | Creates a separator (line) under an action. |

### Adding Custom Actions

The steps for adding a new custom action to the Configuration Manager console are:

1. **Create the action XML file.** The name you choose for the file should have the .xml extension. The arrangement of the actions in the context menu and actions pane is based on the alphabetical ordering of the file names in the actions folder.
2. **Deploy the action XML.** The custom action XML file is placed in the *%ProgramFiles%*\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Actions folder under the GUID named folder of the Configuration Manager console node.

    For example, to create an action that is displayed on the software updates node you would have following folder structure:

    AdminConsole\XmlStorage\Extensions\Actions\f5445252-da1d-450f-a772-7c3d3cb929fb\myfilename.xml

    For more information, see [How to Create a Configuration Manager Action](how-to-create-a-configuration-manager-action).

    For more information about the Configuration Manager console nodes, see [About console nodes](about-configuration-manager-console-nodes).

## Conditional Actions

Actions can be made available (displayed) according to specified conditions. The conditions are defined by the following:

| Condition | Description |
| --- | --- |
| Regular expression | The action is made available depending on a defined search pattern. |
| Method call | The action is made available depending on the result of a method call. |
| Security permissions | The action is made available depending on the security permissions of the selected item. |

For more information, see [Configuration Manager Conditional Actions](conditional-actions).