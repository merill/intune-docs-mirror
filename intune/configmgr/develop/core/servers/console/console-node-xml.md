---
layout: Conceptual
title: Console Node XML - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-node-xml
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
description: Learn how to use the Configuration Manager Console Node XML to cause a grid view to appear in the view panel displaying the RoleName and SiteCode properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 1e6498c9-ea53-b0a5-10fb-0be7dca9438a
document_version_independent_id: b020d66c-c458-50c3-f924-7f82bff9e12c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/console-node-xml.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/console-node-xml
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/console-node-xml.md
cmProducts: []
platformId: cad5cc94-fd6c-4d28-dd2b-5a8c9e0c01c9
---

# Console Node XML - Configuration Manager | Microsoft Learn

The node XML for the Configuration Manager console is in workspace XML files located in the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\ConsoleRoot\ folder. Your extension node XML files, however, are placed in the folder AdminConsole\XmlStorage\Extensions\Nodes\&lt;GUID&gt;, where &lt;GUID&gt; is the namespace GUID identifier for the parent node.

The following XML defines an extension node called "MyNode". The "MyNode" node is defined as a child of the **Site Configuration** node (d61498cb-7b3f-4748-ae3e-026674fb0cbd) in the Administration workspace of the Configuration Manager console. "MyNode" is associated with a **Microsoft.ConfigurationManagement.AdminConsole.ConsoleView.ViewDescription** type which is a grid view that ships with Configuration Manager. When the node is selected, it will cause a grid view to appear in the view panel. The grid view displays two properties (**RoleName** and **SiteCode**) of each `MyClass` custom management class instance that is returned by the WQL query.

Note

The UIExtensionsDemo.dll referenced below is an example of referencing a custom assembly.

```

<RootNodeDescription NamespaceGuid="d61498cb-7b3f-4748-ae3e-026674fb0cbd" Id="MyNode" DisplayName="NodeName" Description="NodeDescription">   <ResourceAssembly>     <Assembly>UIExtensionsDemo.dll</Assembly>      <Type>UIExtensionsDemo.Resources.resources</Type>  </ResourceAssembly>  <ImagesDescription>     <ResourceAssembly>        <Assembly>UIExtensionsDemo.dll</Assembly>         <Type>UIExtensionsDemo.Resources.resources</Type>      </ResourceAssembly>   <ImageResourceName>NodeIcon</ImageResourceName>  </ImagesDescription>   <ViewAssemblyDescriptions>     <ViewAssemblyDescription>       <Assembly>AdminUI.ConsoleView.dll</Assembly>      <Type>Microsoft.ConfigurationManagement.AdminConsole.ConsoleView.ViewDescription</Type>      <CustomData>         <ConfigurationData xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">          <PropertyItemsData>                 <Properties>                      <string>RoleName</string>                      <string>SiteCode</string>                   </Properties>                     <ClassName>MyClass</ClassName>               </PropertyItemsData>           </ConfigurationData>        </CustomData>     </ViewAssemblyDescription>   </ViewAssemblyDescriptions>  <Actions>  </Actions>   <Queries>    <QueryDescription NamespaceGuid="81957874-9c03-4261-84eb-3cf6c31bf251" Type="WQL">             <Query>SELECT * FROM SMS_SCI_SysResUse</Query>                  <ReturnedClassType>MyClass</ReturnedClassType>        </QueryDescription>      </Queries>\</RootNodeDescription>
```

The important elements are:

| Element | Description |
| --- | --- |
| [RootNodeDescription](/en-us/previous-versions/system-center/developer/cc147277%28v=msdn.10%29) | Describes the root node for the node. |
| [Configuration Manager Console RootNodes Element](console-rootnodes-element) | Root node for describing the node. |
| [NodeDescription](/en-us/previous-versions/system-center/developer/cc147269%28v=msdn.10%29) | Parent for nodes describing the tree view and result pane. |
| [RootNodeDescription.resourceAssembly](/en-us/previous-versions/system-center/developer/cc144054%28v=msdn.10%29) | The assembly from which to load resources for this node instance. |
| [ActionDescription.imageDescription](/en-us/previous-versions/system-center/developer/cc143957%28v=msdn.10%29) | The assembly containing the icon and other image resources used by the node. |
| **ActionDescription.viewAssemblyDescription** | The view type of the node. |

## Node hierarchy

Define cascading nodes in the following manner:

```xml
<RootNodeDescription>
  <ChildNodes>
      <RootNodeDescription>
               <ChildNodes>
               ...
               </ChildNodes>
      </RootNodeDescription>
  </ChildNodes>
</RootNodeDescription>
```