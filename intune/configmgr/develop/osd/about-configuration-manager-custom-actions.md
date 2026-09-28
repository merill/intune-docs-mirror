---
layout: Conceptual
title: Custom Actions - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-configuration-manager-custom-actions
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
description: You can create custom actions that can be used with existing Configuration Manager actions.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 561537da-7e09-328d-7c85-8a69a8cb1a9e
document_version_independent_id: fb96a83a-4cf4-f607-62a7-4dbf7843b0c7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/about-configuration-manager-custom-actions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/about-configuration-manager-custom-actions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/about-configuration-manager-custom-actions.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/4628cbd9-6f47-4ae1-b371-d34636609eaf
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/be21deb8-8c64-44b0-b71f-2dc56ca7364f
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: eac847d8-779c-3554-679a-f5f0f10ba83e
---

# Custom Actions - Configuration Manager | Microsoft Learn

You can create custom actions that can be used with existing Configuration Manager actions.

Custom actions are command-line actions that calls an application. The application can be a process, a script or other commands that you specify in a Managed Object Format (MOF) file description.

For more information, see [About Configuration Manager Custom Action Client Applications](about-configuration-manager-custom-action-client-applications).

To allow users to configure your custom action, you can create a custom action control that integrates into the Task Sequence Editor.

Creating a custom action control requires the following steps.

## Creating the Custom Action Control

To create a custom action control, you use Visual Studio 2005 to create a Windows control that implements two classes.

The control that is displayed in the Task Sequence Editor is the first class, which derives from the **SMSOsdEditorPageControl** class. In this class, you define the user interface and the data transfer to and from the action. When a custom action is created, the control's PropertyManager makes the custom action's properties available for use. These are the properties that are defined in the custom action MOF file.

The second class implements the options control, and it derives from the **TaskSequenceOptionControl** class.

For more information about creating a custom control in Visual Studio, see [How to Create a Configuration Manager Custom Action Control](how-to-create-a-configuration-manager-custom-action-control).

Note

The Configuration Manager SDK sample CustomTasksequenceAction shows how to create a custom task sequence action control and MOF.

### Supporting Help

You cannot integrate your control's Help with the Configuration Manager console F1 key Help support. If a user presses F1 in your control, the control does nothing. However, you can implement Help in your control by using a mechanism of your choice to open the Help .chm file. For example, you can add a Help button that opens your Help .chm file.

## Creating the Custom Action MOF File

Each Configuration Manager action is defined in the task sequence provider MOF file, \_tasksequenceprovider.mof. A custom action extends this MOF file with a description for the custom action class. You should create the description of your custom action in a separate MOF file.

For more information, see [About the Configuration Manager Custom Action MOF File](about-configuration-manager-custom-action-mof-files) and [How to Create a MOF File for a Configuration Manager Custom Action](how-to-create-a-mof-file-for-a-configuration-manager-custom-action).

## Deploying the Custom Action Control Assembly

After the custom action control assembly is created, it must be copied to the same directory as the Adminui.tasksequenceeditor.dll. Typically this directory is in %ProgramFiles%\Microsoft Configuration Manager\AdminUI\bin.

## Using the Custom Action Control

To use the custom action, you create and edit a task sequence in the Configuration Manager console. Clicking **Add** displays a list of categories, and you should see the custom action listed in the category that you specified in the custom action MOF file.

After you select it, you will see the control that you have created. The action behaves like the default Configuration Manager actions. You can add conditions to the action and you can move the action within the task sequence.

For more information, see [How to Use a Configuration Manager Custom Action](how-to-use-a-configuration-manager-custom-action-control).