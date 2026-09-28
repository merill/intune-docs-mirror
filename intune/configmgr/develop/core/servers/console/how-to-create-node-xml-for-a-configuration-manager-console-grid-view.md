---
layout: Conceptual
title: How to Create Node XML for a Grid View - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-node-xml-for-a-configuration-manager-console-grid-view
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
description: Learn how to create the node XML for the Configuration Manager console default grid view by creating an XML file describing a RootNodeDescription element.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 873b8892-2ee8-c235-ee30-aa879f879523
document_version_independent_id: c52db969-b583-0ee9-8a68-865f56c63c2c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-create-node-xml-for-a-configuration-manager-console-grid-view.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-create-node-xml-for-a-configuration-manager-console-grid-view
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-create-node-xml-for-a-configuration-manager-console-grid-view.md
cmProducts: []
platformId: 730116ca-8c0b-a55d-67c1-92e09ced6844
---

# How to Create Node XML for a Grid View - Configuration Manager | Microsoft Learn

To create the node XML for the Configuration Manager console default grid view you create an XML file describing a [RootNodeDescription](/en-us/previous-versions/system-center/developer/cc147277%28v=msdn.10%29) element.

The XML in this procedure is used with the assembly you create in [How to Create a Configuration Manager Administrator Console View](how-to-create-a-configuration-manager-console-custom-view). When the user clicks on the "My Node" node, it displays a list of `SMS_SCI_SysResUse` classes in the Configuration Manager in the view pane.

The following elements and attributes are particularly important:

- `RootNodeDescription`. The attribute `NamespaceGuid` identifies the **Site Configuration** node.

### To create the node XML for a view

1. If it is open, close the Configuration Manager console.
2. In Notepad, create an XML file that contains the following XML:

    ```
    <RootNodeDescription NamespaceGuid="c192799c-82cd-43cc-bc11-12996bca800f" Id="MyNode" DisplayName="NodeName" Description="NodeDescription">    <ResourceAssembly>        <Assembly>UIExtensionsDemo.dll</Assembly>        <Type>UIExtensionsDemo.Resources.resources</Type>    </ResourceAssembly>  <ImagesDescription>      <ResourceAssembly>         <Assembly>UIExtensionsDemo.dll</Assembly>          <Type>UIExtensionsDemo.Resources.resources</Type>      </ResourceAssembly>     <ImageResourceName>NodeIcon</ImageResourceName>   </ImagesDescription>   <ViewAssemblyDescriptions>      <ViewAssemblyDescription>         <Assembly>AdminUI.ConsoleView.dll</Assembly>         <Type>Microsoft.ConfigurationManagement.AdminConsole.ConsoleView.ViewDescription</Type>    <CustomData>           <ConfigurationData xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">             <PropertyItemsData>    <Properties>                    <string>RoleName</string>                  <string>SiteCode</string>                </Properties>                <ClassName>SMS_SCI_SysResUse</ClassName>                </PropertyItemsData>  </ConfigurationData>       </CustomData>     </ViewAssemblyDescription>   </ViewAssemblyDescriptions>   <Actions>  </Actions>   <Queries>      <QueryDescription NamespaceGuid="81957874-9c03-4261-84eb-3cf6c31bf251" Type="WQL">         <Query>SELECT * FROM SMS_SCI_SysResUse</Query>         <ReturnedClassType>MyClass</ReturnedClassType>      </QueryDescription>   </Queries></RootNodeDescription>
    ```
3. Save the XML file in the folder %*ProgramFiles*%\AdminConsole\XmlStorage\Extensions\Nodes\c192799c-82cd-43cc-bc11-12996bca800f with the file name ConfigMgrObjectsView.xml. Be sure to save the file as type `All Files`. If the Extensions, Nodes, or GUID folders do not yet exist, create them.
4. Start the Configuration Manager console, select **Site Configuration** in the tree view, and select the **My Node** node. You should see a list of `SMS_SCI_SysResUse` classes in the view.