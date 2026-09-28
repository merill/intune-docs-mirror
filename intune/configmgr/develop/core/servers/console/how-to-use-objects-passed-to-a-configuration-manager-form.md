---
layout: Conceptual
title: Use Objects Passed to a Form - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-use-objects-passed-to-a-configuration-manager-form
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
description: Learn how to use the SmsPageControl.PropertyManager object to access objects selected in the Configuration Manager console.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 485f8370-0b88-3624-5306-d0c88ded2af4
document_version_independent_id: 7824514d-f11e-08c2-3952-4ccd2ea617b8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-use-objects-passed-to-a-configuration-manager-form.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-use-objects-passed-to-a-configuration-manager-form
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-use-objects-passed-to-a-configuration-manager-form.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 6349bb90-2c18-5c0e-b0c9-cc736fd9d1dc
---

# Use Objects Passed to a Form - Configuration Manager | Microsoft Learn

In Configuration Manager, you use the [SmsPageControl.PropertyManager](/en-us/previous-versions/system-center/developer/cc146982%28v=msdn.10%29) object to access objects that are selected in the Configuration Manager console.

Note

If no object is selected in the Configuration Manager console, an empty PropertyManager object is created and passed to the form. This can be used for creating new objects.

The form manages the serialization of objects in the PropertyManager object, and any changes you make are automatically saved when you click **OK**, or they are abandoned when you click **Cancel**.

Depending on the SelectionMode attribute of the action's [ActionDescription](/en-us/previous-versions/system-center/developer/cc147252%28v=msdn.10%29) element, more than one object can be passed to the *PropertyManager* object. Changes that you make by using the *PropertyManager* object are then applied to all objects that are passed in. If you want to access the individual objects, you must cast the *PropertyManager* object to a [ResultObjectsManager](/en-us/previous-versions/system-center/developer/cc147410%28v=msdn.10%29). You then access the objects through the ResultObjectsManager object collection.

For more information, see [Configuration Manager Action XML](configuration-manager-action-xml).

For information about getting the property manager in a dialog box, see [How to Create a Configuration Manager Dialog Box](how-to-create-a-configuration-manager-dialog-box).

## Displaying the Package Name

The following procedure demonstrates using a [PropertyManager](/en-us/previous-versions/system-center/developer/cc146982%28v=msdn.10%29) object to access a single object passed to a property sheet. Clicking a button displays a message box that contains the name of a selected package. To complete these steps, you must first perform the actions in the following topics:

- [How to Create a Configuration Manager Property Sheet](how-to-create-a-configuration-manager-property-sheet)
- [How to Create Form XML for a Configuration Manager Property Sheet](how-to-create-form-xml-for-a-configuration-manager-property-sheet)
- [How to Create Action XML for a Configuration Manager Property Sheet](how-to-create-action-xml-for-a-configuration-manager-property-sheet)

#### To display the package name

1. If the Configuration Manager console is open, close it.
2. In Visual Studio 2010, open the project you created in [How to Create a Configuration Manager Property Sheet](how-to-create-a-configuration-manager-property-sheet).
3. In Solution Explorer, right-click **ConfigMgrControl.cs**, and then click **View Designer**.
4. In the Toolbox, click the **Common Controls** tab, and then double-click **Button**. A button named **button1** is added to your control on the **User Control Designer**.
5. In the **User Control Designer**, double-click **button1** and type the following code in the **button1\_Click** method source code that is displayed:

    ```
    MessageBox.Show(string.Format("The {0} package was selected", PropertyManager["Name"].StringValue));
    ```
6. Build the project and copy the assembly to the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\bin folder.
7. Open the Configuration Manager console, and navigate to the **Packages** node under **Software Distribution**.
8. Right-click a package, and then click **Show my Dialog Box**. The dialog box is displayed.
9. Click the button, and the name of the package is displayed in the dialog box.