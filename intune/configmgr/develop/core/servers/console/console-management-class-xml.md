---
layout: Conceptual
title: Console Management Class XML - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/console-management-class-xml
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
description: The MyClass node is a subclass of the SMS_SiteControlItem management class, which is defined in ManagementClassDescriptions.xml.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d3124fd9-c43b-02ac-1b19-d25f73803d76
document_version_independent_id: f0f92d77-a9cc-55d8-aaf0-1f134ecc2e20
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/console-management-class-xml.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/console-management-class-xml
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/console-management-class-xml.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 67cdeb36-9cc3-6b09-51fc-baedf97876fb
---

# Console Management Class XML - Configuration Manager | Microsoft Learn

The management classes XML for the Configuration Manager console are located %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\ConsoleRoot\ManagementClassDescriptions.xml file. Your extension management class XML files, however, must be placed in the AdminConsole\XmlStorage\Extensions\ManagementClasses\ folder.

The following XML defines an extension management class called "MyClass". The "MyClass" node is a subclass of the `SMS_SiteControlItem` management class, which is defined in the ConsoleRoot\ManagementClassDescriptions.xml.

```

<ManagementClassDescription Name="MyClass" SuperclassName="SMS_SiteControlItem" SecurityObjectAlias="SMS_Site"> <Properties>          <ManagementClassPropertyDescription Name="RoleName"/>          <ManagementClassPropertyDescription Name="SiteCode" />     </Properties></ManagementClassDescription>
```

You can also expose your own custom management class that is defined within an assembly. For example, the XML below defines a management class called `_SDK`. The `_SDK` class is defined in a custom assembly. Note that the management class must be defined using .NET from within the referenced assembly.

```
<ManagementClassDescription Name="_SDK">       <Properties>          <ManagementClassPropertyDescription Name="MyProperty1"/>         <ManagementClassPropertyDescription Name="MyProperty2"/>           <ManagementClassPropertyDescription Name="MyProperty3"/>      </Properties>       <ResourceAssembly>         <Assembly>UIExtensionsDemo.dll</Assembly>    <Type>UIExtensionsDemo.ConnectionManager._SDK.resources</Type>       </ResourceAssembly>       <ImagesDescription>          <ResourceAssembly>             <Assembly>UIExtensionsDemo.dll</Assembly>        <Type>UIExtensionsDemo.Resources.resources</Type>   </ResourceAssembly>         <ImageResourceName>ViewIcon</ImageResourceName>      </ImagesDescription></ManagementClassDescription>
```