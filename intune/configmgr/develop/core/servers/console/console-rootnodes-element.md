---
layout: Conceptual
title: Console RootNodes Element - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-rootnodes-element
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
description: The RootNodes element is responsible for rendering a node. The NodeDescription node defines these user interface elements.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ce90260c-15ab-d843-03c9-9c01773a4488
document_version_independent_id: c52ac59a-925f-1d9c-5a8f-7d430d817b15
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/console-rootnodes-element.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/console-rootnodes-element
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/console-rootnodes-element.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: f1da87fa-ae6d-73ab-8b36-1b6f9cebc5af
---

# Console RootNodes Element - Configuration Manager | Microsoft Learn

`RootNodes` elements are the topmost nodes for a feature. For example, software distribution.

The `RootNodes` element is responsible for rendering a node. It defines the queries and layout that are used to display the results pane and any dynamic nodes that are added to the Configuration Manager console tree node. The `NodeDescription` node defines these user interface elements.

A root node has one type of child node, &lt;ChildNodes&gt;.

## Child Nodes

`ChildNode` elements are static nodes that appear under the root node for a feature. For example, Packages is a child node of the software distribution node. Child nodes appear under the `ChildNodes` node and each child node is described by a `RootNodeDescription` node. Each child node may have further child nodes described in a child `RootNode` element.

## Describing the Tree View Pane and Results Pane

As a child of `RootNodes`, `NodeDescription` provides a description of the tree view pane and results pane used in the Configuration Manager console. `NodeDescription` includes the following three child elements:

- `QueryDescription`
- `DetailsPaneDescription`

## QueryDescription

The `QueryDescription` element can be used to query the SMS Provider for objects to be displayed in the node. The `QueryDescription` element includes the following attributes:

| Attribute | Description |
| --- | --- |
| `NamespaceGuid` | The node that the query applies to. |
| `Type` | The type of the query. Typically this is a WQL query. |
| `DisplayName Description` | Displays text strings for the name and description in the Configuration Manager console. Typically, though you will use the results of the query. The code examples in the next section display the name property of the collection. |

The following elements are some of the child elements of `QueryDescription`:

| Element | Description |
| --- | --- |
| `Query` | The WQL query that is used to populate the node. |
| `ReturnedClassType` | The type of the Configuration Manager or custom object returned. |

## DetailPaneDescription

The `DetailsPaneDescription` element is used to define the details panel associated with a particular node. The `DetailsPaneDescription` element includes the following attributes:

| Attribute | Description |
| --- | --- |
| `ObjectClass` | The object type that the details pane applies to. |

The following elements are some of the child elements of `DetailsPaneDescription`:

| Element | Description |
| --- | --- |
| `PanePageDescription` | Defines the details page that should load in the details pane. Includes the assembly where the page is located, the page title, and query that should be run in order to retrieve any data for display. |

Below is an XML example of a `DetailsPaneDescription` element definition. The details pane is targeted at a `SMS_Package` type and returns all `SMS_Package` objects that are included in the selected `SMS_Package` object. The returned collection is then displayed in a grid view. The properties for display are defined in the `PropertyList` element.

```
<DetailsPaneDescription ObjectClass="SMS_Package">    <PanePageDescription ObjectClass="SMS_Package" PageGuid="ce027fe6-ffd8-4825-ad7b-029c39e97327" Description="ProgramsTabDescription">   <ResourceAssembly>      <Assembly>AdminUI.Program.dll</Assembly>       <Type>Microsoft.ConfigurationManagement.AdminConsole.Program.Properties.Resources.resources</Type>   </ResourceAssembly>   <PageTitle>ProgramsTabName</PageTitle>   <QuerySettingsDescription QueryClass="SMS_Program">    <Queries>       <QueryDescription NamespaceGuid="d13e9848-2c76-418c-ab96-9a2940aaf0de" Type="WQL" DisplayName="##SUB:ProgramName##" Description="##SUB:ProgramName##">         <Query>SELECT * FROM SMS_Program WHERE PackageId='##SUB:PackageId##'</Query>          <ReturnedClassType>SMS_Program</ReturnedClassType>        <Actions>      </Actions>      </QueryDescription>  </Queries>   <PropertyList>       <PropertyDescription Name="ProgramName" />       <PropertyDescription Name="CommandLine" />       <PropertyDescription Name="Run" />       <PropertyDescription Name="DiskSpaceReq" />      <PropertyDescription Name="Comment" />    </PropertyList>   </QuerySettingsDescription> </PanePageDescription></DetailsPaneDescription>
```