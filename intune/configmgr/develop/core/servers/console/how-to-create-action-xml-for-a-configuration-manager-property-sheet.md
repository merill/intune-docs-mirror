---
layout: Conceptual
title: Create Action XML for a Property Sheet - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-action-xml-for-a-configuration-manager-property-sheet
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
description: Learn how to use Create Action XML for a Property Sheet to you create a ShowDialog action. Like other actions, the ShowDialog action defines a context menu and action pane action that the user selects to show the dialog box.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 3d84db68-cc87-4a1c-7cab-9785589c5453
document_version_independent_id: 595cb5b1-a1c3-97c1-531c-022408e00baf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-create-action-xml-for-a-configuration-manager-property-sheet.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-create-action-xml-for-a-configuration-manager-property-sheet
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-create-action-xml-for-a-configuration-manager-property-sheet.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 274c57c2-fe01-53bd-56ab-5653eb4d3c93
---

# Create Action XML for a Property Sheet - Configuration Manager | Microsoft Learn

In Configuration Manager, to display a property sheet or dialog box in the Configuration Manager console, you create a `ShowDialog` action. Like other actions, the `ShowDialog` action defines a context menu and action pane action that the user selects to show the dialog box. To define the `ShowDialog` action, you create an XML file that describes a [ActionDescription](/en-us/previous-versions/system-center/developer/cc147252%28v=msdn.10%29) element.

For more information about property sheet and dialog box actions, see [Configuration Manager ShowDialog Action](showdialog-action).

The following procedure creates the action XML for showing the property sheet you created in [How to Create a Configuration Manager Property Sheet](how-to-create-a-configuration-manager-property-sheet). You must also complete [How to Create Form XML for a Configuration Manager Property Sheet](how-to-create-form-xml-for-a-configuration-manager-property-sheet) before completing the following procedure.

### To create action XML for a property sheet

1. If it is open, close the Configuration Manager console.
2. In Notepad, create an XML file that contains the following XML:

    ```xml
    <?xml version="1.0"?>
    <ActionDescription Description="DisplayDescription" DisplayName="DisplayName" SynchronousAction="true" Class="ShowDialog" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
       <ShowOn>       <string>DefaultHomeTab</string>
           <string>ContextMenu</string>
       </ShowOn>
       <DialogId>Package</DialogId>
    </ActionDescription>
    ```
3. Save the XML file in the folder %*ProgramFiles*%\AdminConsole\XmlStorage\Extensions\Actions\9c69b0aa-a27c-43c9-8c26-5f964106a881. The GUID value identifies packages in the results pane. The file name can be anything with an .xml extension. Be sure to save the file as type `All Files`. If they do not exist, create the Actions folder and Actions subfolder.
4. Load the Configuration Manager console, and in the console tree **Packages** node, right-click a package in the results pane, and then click **DisplayName**. A property sheet appears.