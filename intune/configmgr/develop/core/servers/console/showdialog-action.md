---
layout: Conceptual
title: Configuration Manager ShowDialog Action - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/showdialog-action
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
ms.date: 2016-09-20T00:00:00.0000000Z
description: In Configuration Manager, the ShowDialog action opens a property sheet or regular dialog box in the console. With the ShowDialog action, you can display existing dialog boxes or extension dialog boxes that you create.
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 21c099b6-133c-646f-c383-35e0d813e3f5
document_version_independent_id: 8a3a2bf3-fb69-291a-b645-099cd09176f2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/showdialog-action.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/showdialog-action
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/showdialog-action.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: a6b6f16d-9c6d-746d-ec2b-6abbba3d8e33
---

# Configuration Manager ShowDialog Action - Configuration Manager | Microsoft Learn

The `ShowDialog` action, in Configuration Manager, opens a property sheet or regular dialog box in the Configuration Manager console. With the `ShowDialog` action, you can display existing dialog boxes or extension dialog boxes that you create.

The following attributes and elements are specific to an action that opens a dialog box:

- The `ActionDescription` element `Class` attribute is set to `ShowDialog`.
- The `DialogID` element is the identifier for a property sheet or dialog box displayed in a dialog. It matches the name of the form XML file in the *%ProgramFiles%*\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Forms folder.

## Sample ShowDialog Action XML

The following XML shows how to show a dialog box with the identifier **PrototypeForm**:

```
<ActionDescription Class="ShowDialog" DisplayName="Test Action (dialog)" MnemonicDisplayName="Mnemonic" Description="Description"> <ShowOn>              <string>DefaultHomeTab</string>      <string>ContextMenu</string>           </ShowOn>
 <DialogId>PrototypeForm</DialogId>
</ActionDescription>
```

## Sample Properties ShowDialog Action XML

The following attributes and elements are specific to an action that adds a property page to a properties property sheet:

- The `ActionDescription` element `ActionVerb` attribute is set to `Properties`.
- The `DialogID` element identifies a property sheet containing the property page to be displayed in the `Properties` dialog.

    The following XML shows how to integrate a property page (`PrototypeForm`) into a properties context menu option:

```
<ActionDescription ActionVerb="Properties" Class="ShowDialog">  <ShowOn>    <string>DefaultHomeTab</string>    <string>ContextMenu</string>  </ShowOn>  <DialogId>PrototypeForm</DialogId>
</ActionDescription>
```

For more information about creating and showing dialog boxes, see [About console forms](about-configuration-manager-console-forms).