---
layout: Conceptual
title: Bind Configuration Manager Data to a Form - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-bind-configuration-manager-data-to-a-form
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
description: In Configuration Manager, to bind console data to a property sheet, you use the DataBindings property of the property sheet's control class.
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 3a1c2623-0367-493f-344e-9011d6bf292b
document_version_independent_id: c43dcf5d-34e9-d7fb-a97c-a9edb0cd3bc5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-bind-configuration-manager-data-to-a-form.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-bind-configuration-manager-data-to-a-form
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-bind-configuration-manager-data-to-a-form.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 35d1e414-7954-20d7-859c-ab07d300d2b3
---

# Bind Configuration Manager Data to a Form - Configuration Manager | Microsoft Learn

In Configuration Manager, to bind Configuration Manager console data to a property sheet, you use the `DataBindings` property of the property sheet's control class.

The `DataBindings` property is used to bind to the objects in the form's `Property Manager`. After an object changes, mark the object as changed with *SetDirtyFlag*. This ensures that the object is serialized properly when the dialog box is dismissed.

### To bind Configuration Manager data to a form

1. If the Configuration Manager console is open, close it.
2. In Visual Studio 2010, open the project you created in [How to Create a Configuration Manager Property Sheet](how-to-create-a-configuration-manager-property-sheet).
3. In Solution Explorer, right-click **ConfigMgrControl.cs**, and then click **View Designer**.
4. In the Toolbox, click the **Common Controls** tab, and then double-click **TextBox**. A field named **textBox1** is added to your control on the **User Control Designer**.
5. In Solution Explorer, right-click **ConfigMgrControl.cs**, and then click **View Source**.
6. Add the following code to the `InitializePageControl` method:

    ```
    textBox1.DataBindings.Add("Text", PropertyManager["Name"], "StringValue");
    ```
7. In Solution Explorer, right-click **ConfigMgrPropertySheet.cs**, and then click **View Designer**.
8. Double-click the text box you added. A new event handler, `TextChanged`, is created.
9. In **textBox1\_TextChanged**, add the following code to set the dirty flag when text is changed: `Dirty = true;`
10. Build the project and copy the assembly to %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\bin.
11. Open the Configuration Manager console, and navigate to the **Packages** node under **Software Distribution**.
12. Right-click a package, and then click **Show My Property Sheet**.

    In the property sheet that is displayed, the text box displays the name of the selected package.
13. Type a new name for the package, and then click **OK**.

    In the Configuration Manager console results pane, the package name is changed to the name you entered.