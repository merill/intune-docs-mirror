---
layout: Conceptual
title: Console extension deployment - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-extension-deployment
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
description: The deployment of a typical Configuration Manager extension has to account for actions, forms, views, management classes and node extensions.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: a83b3eec-b8a6-7d0e-dc81-cb8a07aa5e48
document_version_independent_id: 0b70cede-44b5-7f3b-54df-ae6481c8b586
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/console-extension-deployment.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/console-extension-deployment
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/console-extension-deployment.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: a13bb6c4-1b57-93d7-c14f-b43a8bd6aebe
---

# Console extension deployment - Configuration Manager | Microsoft Learn

The deployment of a typical Configuration Manager extension has to account for actions, forms, views, management classes and node extensions.

When you deploy a Configuration Manager extension, you install the files in the following directories:

| Extension Type | Directory |
| --- | --- |
| Actions | %ProgramFiles%\Microsoft Endpoint Manager\AdminConsole\bin for the assembly %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Actions for the action XML files |
| Forms | %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\bin for the assembly %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Forms for the form XML files |
| Views | %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\bin for the assembly |
| Nodes | %ProgramFiles%\Microsoft Endpoint Manager\AdminConsole\bin for the assembly %*ProgramFiles*%Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Nodes for the node XML files |
| ManagementClasses | %ProgramFiles%\Microsoft Endpoint Manager\AdminConsole\bin for the assembly %ProgramFiles%Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\ManagementClasses for the management classes XML files |

Important

Placing your assemblies and dependencies in the %ProgramFiles%\Microsoft Endpoint Manager\AdminConsole\bin folder may create conflicts with other console extensions and prevent your extension from loading.

You must also perform the following tasks during installing and uninstalling actions.

## Custom Actions

### Installing a Custom Action

To install a custom action XML file, copy the file to the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Actions\&lt;GUID&gt; folder, where &lt;GUID&gt; is the GUID identifier for the node that the action applies to.

### Removing a Custom Action

To remove a custom action, delete the custom action XML file. If there are no other XML files in the folder then it is safe to remove the folder.

## Forms

### Installing a Form

You copy the form assembly to either %*ProgramFiles*%\ Microsoft Endpoint Manager\AdminConsole\bin or to your application's installation folder.

If you are deploying to a directory other than the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\bin folder, the form XML&lt;`Assembly`&gt; attribute, `Name`, should include the assembly filename and the full path to the file. For more information, see [How to Create Form XML for a Configuration Manager Property Sheet](how-to-create-form-xml-for-a-configuration-manager-property-sheet).

To install an extension property sheet XML file for a form, copy the file to the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Forms folder. Because all extension forms are placed in this folder, you must ensure that your XML file has a unique name. It is suggested that you use your company name as part of the file name.

If the form is an extension of an existing property sheet, you must determine whether the property sheet already exists in the Extensions\Forms folder, then add your property page to that property sheet.

When the Configuration Manager console loads, it loads property sheets in the Extensions\Forms folder in preference to existing property sheets.

You should use the `VendorId` attribute of the `Page` element, because this allows other vendors to identify and avoid changing your extensions.

### Removing a Form

To remove a form that does not extend an existing property sheet, remove the property sheet XML file from the folder %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Forms.

To remove a property page that you have added to an existing property sheet, you must take the following actions with the property sheet:

- Check the property pages for VendorIDs other than Microsoft Corporation. If none exist then it is safe to delete the property sheet XML file from the Extensions\Forms folder.
- If other VendorIDs exist, remove your property page XML from the property sheet, and leave the property sheet in the Extensions\Forms folder.

## Views

### Installing a View

To install a view, copy the view assembly to the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\bin folder, or to your application's installation folder.

If you are deploying to a folder other than %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\bin, the node XML&lt;`Assembly`&gt; element should include the assembly filename and the full path to the file. For more information, see [How to Create Node XML for a Configuration Manager Console View](how-to-create-node-xml-for-a-configuration-manager-console-grid-view).

You must also copy the node XML that integrates the view into the Configuration Manager console to the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Nodes\&lt;GUID folder&gt;, where &lt;GUID&gt; is the GUID identifier for the node that the action applies to. For more information, see the "Nodes" section later in this topic.

### Removing a View

To remove a view, delete the view assembly from the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\bin folder. You must ensure that no other extension is referencing the view before you delete it. You must also delete the view's node XML file from the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Nodes\&lt;GUID&gt; folder, where &lt;GUID&gt; is the GUID identifier for the node that the action applies to.

## Custom Management Classes

### Installing a Custom Management Class

Copy the management class assembly to either %*ProgramFiles*%\ Microsoft Endpoint Manager\AdminConsole\bin or to your application's installation folder.

To install a custom management class XML file, copy the file to the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\ManagementClasses folder. Because all custom management classes are placed in this folder, you must ensure that your XML file has a unique name. It is suggested that you use your company name as part of the file name.

### Removing a Custom Management Class

To remove a custom management class, delete the custom management class XML file. If there are no other XML files in the folder then it is safe to remove the folder.

## Nodes

### Installing a Node

To install a node, create a folder %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Nodes\&lt;GUID&gt; , where &lt;GUID&gt; is the GUID identifier of the Configuration Manager console parent node. Copy the node XML file to the GUID folder. For more information, see [About console nodes](about-configuration-manager-console-nodes).

### Removing a Node

To remove a node, delete the node XML file from the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Nodes\&lt;GUID&gt; folder.