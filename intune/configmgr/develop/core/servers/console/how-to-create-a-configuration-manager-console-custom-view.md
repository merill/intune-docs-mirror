---
layout: Conceptual
title: Create a Console Custom View - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-console-custom-view
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
description: Learn how to create  a view that displays a custom control. In this example, the view displays the string content of a label control.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 22935c0a-73b9-cf24-d51a-f4f6a94bcce9
document_version_independent_id: 60fac94f-a787-268f-fbf2-de1aab1d7d39
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-console-custom-view.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-console-custom-view
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-console-custom-view.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 89bea454-6c4e-9749-a618-66a8af1c47a5
---

# Create a Console Custom View - Configuration Manager | Microsoft Learn

In Configuration Manager, to create a custom console view, you must create two .NET Framework classes. If you do not wish to create your own custom view control, see [How to Create Node XML for a Configuration Manager Console View](how-to-create-node-xml-for-a-configuration-manager-console-grid-view) for more information.

The following procedure creates a view that displays a custom control. In this case, the view displays the string content of a label control.

The procedures in this topic create a "My View" console extension node that displays. beneath the **Site Configuration** console node in the Administration workspace. When you click the "My View" node, your custom view control will load into the Configuration Manager console.

## Creating a Custom View

The following procedures create an extension node with a custom view control.

### Create the View Controller Class

The following procedure creates the `OverviewControllerBase` derived class. The controller class's Content property is set contain your custom control. In the example below, the Content property is assigned a simple label control.

##### To create a console view class

- Create the following new class. In this case, your custom control is a simple label control:

    ```
    
    public class MyViewController : OverviewControllerBase{   public MyViewController(): base()   {}   public override void EndInit()   {                 base.EndInit();     this.Content = new Label() { Content = "My Content" };   }}
    ```

### Create the View Description Class

The following procedure creates the `IConsoleView2` derived class.

##### To create a console view class

- Create the following new class:

    ```
    
    public class MyViewDescription : IConsoleView2
    {
        override protected Type TypeOfViewController    {       get { return typeof(MyViewController); }     }
        override protected Type TypeOfView     {      get { return typeof(Overview); }     }        public override bool TryConfigure(ref XmlElement persistedConfigurationData)    {        return false;    }
    new public bool TryInitialize(ScopeNode scopeNode, AssemblyDescription resourceAssembly, ViewAssemblyDescription viewAssemblyDescription)    {      return true;    }
    }
    ```

### Create the extension node XML

The following XML is required in order to load your extension into the console. Note that the `DisplayName` and `Description` properties refer to names in your assembly's resource file.

```
<RootNodeDescription NamespaceGuid="c192799c-82cd-43cc-bc11-12996bca800f" Id="MyViewNode" DisplayName="ViewNodeName" Description="ViewNodeDescription">  <ResourceAssembly>    <Assembly>NameofMyAssembly.dll</Assembly>    <Type>NameofMyAssembly.Resources.resources</Type>  </ResourceAssembly>  <ImagesDescription>    <ResourceAssembly>      <Assembly> NameofMyAssembly.dll</Assembly>      <Type> NameofMyAssembly.Resources.resources</Type>    </ResourceAssembly>    <ImageResourceName>NodeIcon</ImageResourceName>  </ImagesDescription>  <ViewAssemblyDescriptions>    <ViewAssemblyDescription>      <Assembly> NameofMyAssembly.dll</Assembly>      <Type>NameofMyAssembly.MyViewDescription</Type>    </ViewAssemblyDescription>  </ViewAssemblyDescriptions></RootNodeDescription>
```

## Deploy the Assembly

The following procedure builds the assembly you have created and copies it to the Configuration Manager console assemblies folder. For important information about deploying Configuration Manager console extensions, see [Configuration Manager Console Extension Deployment](console-extension-deployment).

#### To deploy the view assembly

1. Build the project, and depending on where you created your project, the assembly should be created as \Visual Studio 2010\Projects\ConfigMgrControl\ConfigMgrObjectsControl\bin\Debug\NameofMyAssembly.dll.

    Note

    In other parts of the Console Extension section, the examples use an assembly named `ConfigMgrObjectsControl.dll`. If you are building the examples in other sections, make sure to name the assembly `ConfigMgrObjectsControl.dll` at this step (or change the other assembly references to your specific assembly name).
2. Copy the assembly to the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\bin folder.