---
layout: Conceptual
title: Executable action - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/executable-action
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
description: The executable action runs a program or opens a file by using the program registered with Windows for that file type.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 36128f07-1639-5c42-6391-16860b6121f0
document_version_independent_id: a19a3bd3-f826-9b37-d302-ab1bc306ce1c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/executable-action.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/executable-action
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/executable-action.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 42eec2c5-c6bd-46b6-8762-16b03094941f
---

# Executable action - Configuration Manager | Microsoft Learn

In Configuration Manager, the executable action runs a program or opens a file by using the program registered with Windows for that file type.

The following attributes and elements are specific to an action that runs a program:

- The `ActionDescription` element `Class` attribute is set to `Executable`.
- The `Executable` element is parent to `FilePath``,` the path to the program, and to `Parameters`, the parameters passed to the executable.

## Sample Executable Action XML

```
<ActionDescription Class="Executable" DisplayName="Test Action (execute)" MnemonicDisplayName="A test item" Description="A test item Description">
  <ShowOn>
    <string>DefaultHomeTab</string>
    <string>ContextMenu</string>
  </ShowOn>
  <!--<ResourceAssembly>
    <Assembly>Microsoft.ConfigurationManagement.dll</Assembly>
    <Type>Microsoft.ConfigurationManagement.AdminConsole.Properties.Resources.resources</Type>
  </ResourceAssembly>-->
  <!--<ImagesDescription>
    <ExternalImage>
      <Assembly>AdminUI.Package.dll</Assembly>
      <Type>Microsoft.ConfigurationManagement.AdminConsole.Package.SmsPackageUtils</Type>
      <Method>ShowPackageLockedIcon</Method>
    </ExternalImage>
    <ResourceAssembly>
      <Assembly>AdminUI.UIResources.dll</Assembly>
      <Type>Microsoft.ConfigurationManagement.AdminConsole.UIResources.Properties.Resources.resources</Type>
    </ResourceAssembly>
    <ImageResourceName>New</ImageResourceName>
  </ImagesDescription>-->
  <!--<ImagesDescription AliasProperty="OwnedByThisSite">
    <ResourceAssembly>
      <Assembly>AdminUI.UIResources.dll</Assembly>
      <Type>Microsoft.ConfigurationManagement.AdminConsole.UIResources.Properties.Resources.resources</Type>
    </ResourceAssembly>
    <AliasResourceAssembly>
      <Assembly>AdminUI.UIResources.dll</Assembly>
      <Type>Microsoft.ConfigurationManagement.AdminConsole.UIResources.SMS_Collection-OwnedByThisSite.resources</Type>
    </AliasResourceAssembly>
    <ImageResourceName>CollectionsIcon</ImageResourceName>
  </ImagesDescription>-->
  <!--<ActionStateAssembly>
    <Assembly>AdminUI.Report.dll</Assembly>
    <Type>Microsoft.ConfigurationManagement.AdminConsole.Report.ReportsUtilityClass</Type>
    <Method>EnableReportMenu</Method>
    -->
  <!--Method signature: public static bool EnableMenu(object sender, ScopeNode scopeNode, ActionDescription action, ResultObjectBase resultObject)-->
  <!--
  </ActionStateAssembly>-->
  <!--<InstancePermissions>
    <SecurityFlagsDetailDescription BitName="Delete" BitValue="4" DependsOn="1" />
  </InstancePermissions>-->
  <!--<MatchPattern>[^1]</MatchPattern>
  <MatchValueToTest>##SUB:Order##</MatchValueToTest>-->
  <Executable>
    <FilePath>https://go.microsoft.com/fwlink/?LinkId=67307</FilePath>
  </Executable>
</ActionDescription>
```

Other elements and attributes are documented in [ActionDescription](/en-us/previous-versions/system-center/developer/cc147252%28v=msdn.10%29).