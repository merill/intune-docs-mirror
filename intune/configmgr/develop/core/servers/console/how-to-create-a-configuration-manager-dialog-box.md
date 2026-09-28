---
layout: Conceptual
title: Create a Dialog Box - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-dialog-box
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
description: These procedures show you how to create a modeless dialog box assembly, in Configuration Manager, by using Visual Studio.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 2511b6e2-51b1-2891-6c15-24108e8e333e
document_version_independent_id: bff317f1-58ac-7fa0-dad0-f78ffa90d4cf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-dialog-box.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-dialog-box
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-dialog-box.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/4628cbd9-6f47-4ae1-b371-d34636609eaf
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/be21deb8-8c64-44b0-b71f-2dc56ca7364f
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 908577b3-94ca-d5dd-4ecf-608ff3015825
---

# Create a Dialog Box - Configuration Manager | Microsoft Learn

These procedures show you how to create a modeless dialog box assembly, in Configuration Manager, by using Visual Studio.

Creating the dialog box is very similar to creating a property sheet. You create a class derived from SmsPageControl and an XML file to describe the dialog.

For more information about the property manager, see [How to Use Objects Passed to a Configuration Manager Forms](how-to-use-objects-passed-to-a-configuration-manager-form).

After you have successfully built the dialog box assembly, you must do the following to integrate it into the Configuration Manager console:

1. Define and deploy the form XML that links the selected action to the assembly you create in this topic. For more information, see [How to Create Form XML for a Configuration Manager Dialog Box](how-to-create-form-xml-for-a-configuration-manager-dialog-box).
2. Define and deploy the action XML for displaying the context menu that the user selects. For more information, see [How to Create Action XML for a Configuration Manager Dialog Box](how-to-create-action-xml-for-a-configuration-manager-dialog-box).

    When you have created the dialog assembly and XML, right-click a package in the Configuration Manager console tree **Packages** node, and then click **Show my Dialog Box**. A dialog box appears with a button on it. Clicking the button displays a message box containing the name of the package you selected.

## Create the Control Class

The following procedure creates the control for the dialog box.

#### To create the Visual Studio project

1. In Visual Studio 2010, on the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.
2. From the list of Visual C#, Windows projects, select the **Windows Control Library** project template, and type `ConfigMgrDialogControl` in the **Name** box.
3. Click **OK** to create the Visual Studio project.
4. In Solution Explorer, right-click **UserControl1.cs**, click **Rename**, and change the name to **ConfigMgrDialogControl.cs**.
5. In Solution Explorer, right-click **References**, and then click **Add Reference**.
6. In the **Add Reference** dialog box, click the **Browse** tab, navigate to **%ProgramFiles%\Microsoft Endpoint Manager\AdminConsole\bin** and then select **microsoft.configurationmanagement.exe**, **microsoft.configurationmanagement.managementprovider.dll**, **Microsoft.ConfigurationManagement.DialogFoundation.dll** and **AdminUI.DialogFoundation.dll**. Click **OK** to add the assemblies as project references.
7. In Solution Explorer, right-click **ConfigMgrDialogControl.cs** and then click **View Code**.
8. In the source code, change the namespace to `Microsoft.ConfigurationManagement.AdminConsole.ConfigMgrDialogBox`
9. Change the class `ConfigMgrDialogControl` so that it derives from `SmsCustomDialog`.
10. In Solution Explorer, right-click **ConfigMgrDialogControl.Designer.cs** and then click **View Code**.
11. In the source code, change the namespace to `Microsoft.ConfigurationManagement.AdminConsole.ConfigMgrDialogBox`
12. Change the class `ConfigMgrDialogControl` so that it derives from `SmsCustomDialog`.
13. In **ConfigMgrDialogControl.cs**, add the following code to initialize the control:

    ```
    public override bool Initialize(System.Reflection.Assembly assembly, SmsFormData formData, SmsPageData pageData)
    {
        base.Initialize(assembly, formData, pageData);
        return true;
    }
    ```
14. In Solution Explorer, right-click **ConfigMgrDialogControl.cs** and select **View Designer**.
15. In the Toolbox, click the **Common Controls** tab, and then double-click **Button**. A button named **button1** is added to your control on the **User Control Designer**.
16. In the **User Control Designer**, double-click **button1** and type the following code in the **button1\_Click** method source code displayed:

    ```
    MessageBox.Show( PageData.PropertyManager["Name"].StringValue);
    ```

## Deploy the Assembly

The following procedure builds and copies the assembly that you have created to the Configuration Manager console `assemblies` folder. For important information about deploying Configuration Manager console extensions, see [About Configuration Manager Console Extension Deployment](console-extension-deployment).

#### To deploy the dialog box assembly

1. Build the project, and depending on where you created your project, your Visual Studio installation, the assembly is created as \Visual Studio 2010\Projects\ConfigMgDialogControl\ConfigMgrDialogControl\bin\Debug\ConfigMgrDialogControl.dll.
2. Copy the assembly to the folder %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\bin.