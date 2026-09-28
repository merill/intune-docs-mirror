---
layout: Conceptual
title: Configuration Manager Group Action - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/group-action
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
description: Learn how to use the group action in configuration manager to create a submenu for related actions.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 697fc613-f724-8221-d2b9-4b99017cd165
document_version_independent_id: 81e3ebbd-0a90-13e2-80c7-4ad5861da73a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/group-action.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/group-action
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/group-action.md
cmProducts: []
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 245d9a8d-e5f5-6ea7-e0e2-50df986d24e1
---

# Configuration Manager Group Action - Configuration Manager | Microsoft Learn

In Configuration Manager, the Group action creates a menu group, also known as a submenu, for related actions.

The following attributes and elements are specific to an action that creates a group of context menu items:

- The &lt;`ActionDescription`&gt; element `Class` attribute is set to **Group**.
- The &lt;`DisplayName`&gt; attribute is the group name displayed in the context menu.
- The &lt;`GroupAsRegion`&gt; Boolean attribute specifies whether or not to display this group as a region on the ribbon bar.
- The &lt;`ActionGroups`&gt; element is a list of actions (&lt;`ActionDescription`&gt; elements) displayed in the context menu group.

## Group Action XML

The following XML demonstrates a group of actions named New Group Name:

```
<ActionDescription Class="Group" GroupAsRegion="true" DisplayName="New Group Name" MnemonicDisplayName="MnemonicNewGroupName" Description="NewGroupNameDescription">  <ShowOn>      <string>DefaultContextualTab</string> <!-- RIBBON -->     <string>ContextMenu</string> <!-- Context Menu -->   </ShowOn>       <ActionGroups>
    <ActionDescription Class="Executable" DisplayName="Test Action (execute)" MnemonicDisplayName="A test item" Description="A test item Description">          <ShowOn>          <string>DefaultContextualTab</string> <!-- RIBBON -->         <string>ContextMenu</string> <!-- Context Menu -->      </ShowOn>         <Executable>
      <FilePath>https://go.microsoft.com/fwlink/?LinkId=67307</FilePath>
    </Executable>
    </ActionDescription>
    <ActionDescription Class="Report" DisplayName="Test Action (report)" MnemonicDisplayName="Mnemonic" Description="Description">
    <ShowOn>         <string>DefaultContextualTab</string> <!-- RIBBON -->        <string>ContextMenu</string> <!-- Context Menu -->      </ShowOn>            <ReportDescription Id="05874720-1D08-4CF7-B182-5F9D065BEAE5">
      </ReportDescription>
    </ActionDescription>
  </ActionGroups>
</ActionDescription>
```