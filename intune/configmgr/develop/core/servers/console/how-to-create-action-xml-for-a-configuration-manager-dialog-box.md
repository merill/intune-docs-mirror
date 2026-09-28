---
layout: Conceptual
title: Create Action XML for a Dialog Box - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-action-xml-for-a-configuration-manager-dialog-box
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
description: Learn how to create action XML for dialog boxes.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 62930714-5b45-4081-3860-d44e60c2a0b4
document_version_independent_id: e5bc8325-81fd-aa88-64ef-48acafa8ba15
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-create-action-xml-for-a-configuration-manager-dialog-box.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-create-action-xml-for-a-configuration-manager-dialog-box
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-create-action-xml-for-a-configuration-manager-dialog-box.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 32eed5b9-78ed-747d-260b-3ca7614d8f01
---

# Create Action XML for a Dialog Box - Configuration Manager | Microsoft Learn

In Configuration Manager, to display a dialog box in the Configuration Manager console, you create a [Configuration Manager ShowDialog Action](showdialog-action) action. To define the `ShowDialog` action, you create an XML file that describes a [ActionDescription](/en-us/previous-versions/system-center/developer/cc147252%28v=msdn.10%29) element.

The following procedure creates the action XML for showing a dialog box. You must complete the procedures in the [How to Create a Configuration Manager Dialog Box](how-to-create-a-configuration-manager-dialog-box) and [How to Create Form XML for a Configuration Manager Dialog Box](how-to-create-form-xml-for-a-configuration-manager-dialog-box) topics before you complete this procedure.

Note

The dialog identifier &lt;`DialogId`&gt; must match the file name, without the XML extension, of the form XML you created in [How to Create Form XML for a Configuration Manager Dialog Box](how-to-create-form-xml-for-a-configuration-manager-dialog-box).

### To create an action for a dialog box

1. If it is open, close the Configuration Manager console.
2. In Notepad, create an XML file that contains the following XML:

    ```
    <ActionDescription Class="ShowDialog" DisplayName="Show my Dialog Box" MnemonicDisplayName="Mnemonic" Description="Description"> <ShowOn>      <string>DefaultContextualTab</string> <!-- RIBBON -->     <string>ContextMenu</string> <!-- Context Menu -->   </ShowOn>
     <DialogId>ConfigMgrDialogControl</DialogId>
    </ActionDescription>
    ```
3. Save the XML file in the folder, %*ProgramFiles*%\AdminUI\XmlStorage\Extensions\Actions\32815086-cce9-42de-95a4-0941da31114e. The GUID value identifies packages in the results pane. The file name can be anything with an .xml extension. Be sure to save the file as type `All Files`.
4. Start the Configuration Manager console, and in the console tree **Packages** node, right-click a package in the results pane, and then click **Show my Dialog Box**. A dialog box appears.