---
layout: Conceptual
title: AssemblyType Action - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/assemblytype-action
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
description: Learn how the AssemblyType action defines the type and assembly for a method that is called by the Configuration Manager console.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 8c4544f3-64f4-9bdd-c81e-be2092def8d3
document_version_independent_id: f353af72-f78f-1d5c-4468-f8f7da8a7377
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/assemblytype-action.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/assemblytype-action
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/assemblytype-action.md
cmProducts: []
platformId: 689a4f73-91e9-f210-be46-89ed7fe4a2e1
---

# AssemblyType Action - Configuration Manager | Microsoft Learn

The `AssemblyType` action defines the type and assembly for a method that is called by the Configuration Manager console.

Note

The XML and C# code in this topic is available in the Dialog Prototype sample in the Configuration Manager SDK.

The following attributes and elements are specific to an action that calls a method in an assembly:

- The `Class` attribute of the `ActionDescription` element is set to `AssemblyType`.
- The `ActionAssembly` element has a number of child elements that are used to define the method and assembly.
- The `Assembly` element identifies the assembly that contains the method. If the assembly is in a folder other than %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\bin folder then the `Assembly` element should include the assembly filename and the full path to the file.
- The `Type` element contains the namespace and class for the method.
- The `Method` element contains the name of the method to be called.

## Method

The method signature is:

```
public static void Method(object, ScopeNode, ActionDescription, IResultObject, PropertyDataUpdated, Status)
```

Where the parameters are as follows:

`object` The object calling the method.

`ScopeNode` The Configuration Manager console node that was active when the action was called.

`ActionDescription` The `ActionDescription` class instance that initiated the action.

`IResultObject` The selected object, or `null` if there is no selected object.

`PropertyDataUpdated` The delegate to open to provide update information for the Configuration Manager console view.

`Status` Allows control of the Configuration Manager console busy status indicator.

### Example Implementation

The following is an example implementation of the method.

```
public static void Method(object sender, ScopeNode scopeNode, ActionDescription action, IResultObject resultObject, PropertyDataUpdated dataUpdatedDelegate, Status status)
{
    if (resultObject != null)
    {
        MessageBox.Show(string.Format("The {0} package was selected", resultObject["Name"].StringValue));
    }
    else
    {
        MessageBox.Show("No package was selected");
    }
}

```

## AssemblyType Action XML

The following XML example demonstrates how to call a method, `Method`, in a class, `SampleClass`. The method is in the assembly `AdminUI.PrototypeDialog.dll`.

```
<ActionDescription Class="AssemblyType" DisplayName="Test Action (method)" MnemonicDisplayName="Mnemonic" Description="Description">
  <ShowOn>
    <string>DefaultHomeTab</string>
    <string>ContextMenu</string>
  </ShowOn>
  <ActionAssembly>
    <Assembly>AdminUI.PrototypeDialog.dll</Assembly>
    <Type>Microsoft.ConfigurationManagement.AdminConsole.PrototypeDialog.ExampleClass</Type>
    <Method>Method</Method>
    <!--Method signature: public static void Method(object sender, ScopeNode scopeNode, ActionDescription action, IResultObject resultObject, PropertyDataUpdated dataUpdatedDelegate, Status status)-->
  </ActionAssembly>
</ActionDescription>

```