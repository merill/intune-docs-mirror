---
layout: Conceptual
title: Configuration Manager Console Views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-views
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
description: Configuration Manager console views are displayed in the results pane of the Configuration Manager console.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 6a510227-100e-72ec-63d9-0fc94def4ecd
document_version_independent_id: ff0444fc-951e-f569-c4dd-69fc25aad942
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/about-configuration-manager-console-views.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/about-configuration-manager-console-views
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/about-configuration-manager-console-views.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://authoring-docs-microsoft.poolparty.biz/devrel/a1d24c9d-72df-405d-986b-5fdc11501831
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://authoring-docs-microsoft.poolparty.biz/devrel/16af8d78-81c3-4bd4-b07d-c042d47161d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 16350cc1-2c05-48f9-1ef1-d6f09c5f47ea
---

# Configuration Manager Console Views - Configuration Manager | Microsoft Learn

Configuration Manager console views are displayed in the results pane of the Configuration Manager console. You can create your own views and make them available anywhere in the tree view hierarchy.

## Creating the View Assembly

To create a view, you must define a class within that implements the **IConsoleView2** interface.

After you create the class and build the assembly, place it in the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\bin folder where it is loaded by the Configuration Manager console.

For more information, see [How to Create a Configuration Manager Administrator Console View](how-to-create-a-configuration-manager-console-custom-view).

## Creating the Node XML

The view is integrated into the Configuration Manager console when you create an XML file that describes the location, queries, actions, and resources that are needed for the node that displays the view. The node XML file is placed in the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\ConsoleRoot\Extensions\Nodes folder, under a folder that is named with the GUID of the parent node for the node.

For more information, see [How to Create Node XML for a Configuration Manager Administrator Console View](how-to-create-node-xml-for-a-configuration-manager-console-grid-view).

For more information about node XML, see [About console nodes](about-configuration-manager-console-nodes).

## Help

### F1 Help

You can add F1 Help support to your views by specifying the `HelpID` attribute of the view `QueryDescription` element in the node XML. In the `HelpID` attribute you specify the path to the .chm file and the topic that you want to display in the following format:

`HelpID="<path to chm>::<path to topic><topic name>.htm"`

For example, the following `QueryDescription` element declaration loads the "How to Create a Package" topic from the Configuration Manager .chm. The .chm is assumed to be in c:\chm.

Note

The assembly referenced below (ConfigMgrObjectsControl.dll) is created in the [How to Create a Configuration Manager Console Custom View](how-to-create-a-configuration-manager-console-custom-view).

```
<ViewAssemblyDescriptions>    <ViewAssemblyDescription>         <Assembly> ConfigMgrObjectsControl.dll </Assembly>        <Type> Microsoft.ConfigurationManagement.AdminConsole.ConfigMgrObjectsView.ConfigMgrObjectsViewDescription </Type>   <CustomData>            <ConfigurationData xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">       <PropertyItemsData>               <Properties>                       <string>MyProperty1</string>           <string>MyProperty2</string>                   </Properties>                    <ClassName>_SDK</ClassName>               </PropertyItemsData>    </ConfigurationData>         </CustomData>      </ViewAssemblyDescription>   </ViewAssemblyDescriptions>   <Actions>  </Actions>   <Queries>      <QueryDescription NamespaceGuid="a4b9867e-8fc8-4fae-8a1a-0c798c22e010" Type="WQL" HelpTopic="C:\chm\SystemCenterConfigurationManager_SDK.chm::/html/2c295b3b-e23c-4084-ad4a-8bba328ef6fc.htm">          <Query>GetData</Query>          <ReturnedClassType>_SDK</ReturnedClassType>         <Actions>               <ActionDescription Class="ShowDialog" DisplayName="ShowDialogActionName" Description="ShowDialogActionDescription">                <ShowOn>                   <string>DefaultHomeTab</string>                   <string>ContextMenu</string>              </ShowOn>               <ResourceAssembly>                  <Assembly>UIExtensionsDemo.dll</Assembly>                      <Type>UIExtensionsDemo.Resources.resources</Type>              </ResourceAssembly>             <ImagesDescription>                <ResourceAssembly>                   <Assembly>UIExtensionsDemo.dll</Assembly>                  <Type>UIExtensionsDemo.Resources.resources</Type>    </ResourceAssembly>                  <ImageResourceName>ActionIcon</ImageResourceName>  </ImagesDescription>             <DialogId>MyDialog</DialogId>          </ActionDescription>      </Actions>    </QueryDescription>  </Queries>
```

For more information about using the `QueryDescription` element, see [How to Create Node XML for a Configuration Manager Console View](how-to-create-node-xml-for-a-configuration-manager-console-grid-view).

### Custom Help

You can also display your own .chm outside of the F1 Help system. For example, you can add a button to your form that opens your Help .chm. For more information about opening Help from Windows forms, see the [Help class](/en-us/dotnet/api/system.windows.forms.help) in the .NET Framework Class Library.