---
layout: Conceptual
title: Create a Property Sheet - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-property-sheet
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
description: In Configuration Manager, to create a console property sheet, you first create a NET Framework assembly that inherits from the SMSPageControl class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 3894be6a-0e10-16a1-7d5b-a261f3db1b1b
document_version_independent_id: 6be5ff32-a1a7-eb34-3f4a-0ae1de53c343
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-property-sheet.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-property-sheet
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-property-sheet.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/4628cbd9-6f47-4ae1-b371-d34636609eaf
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/be21deb8-8c64-44b0-b71f-2dc56ca7364f
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: be9fd9b2-f05d-d37e-d2c4-bea941725a82
---

# Create a Property Sheet - Configuration Manager | Microsoft Learn

To create a Configuration Manager console property sheet, in Configuration Manager, you create a .NET Framework assembly that inherits from the following class:

| Class | Description |
| --- | --- |
| [SmsPageControl](/en-us/previous-versions/system-center/developer/cc147309%28v=msdn.10%29) | The control displayed on the property page. |

The following procedures show you how to create a Configuration Manager property sheet assembly by using Visual Studio. The property sheet displays a property page that contains a button. When it is clicked, the button displays the name of a package selected in the Configuration Manager console **Packages** node.

After you have successfully built the dialog box assembly, you must do the following to integrate it into the Configuration Manager console:

1. Define and deploy the form XML that links the selected action to the assembly you create in this topic. For more information, see [How to Create the Form XML for a Configuration Manager Property Sheet](how-to-create-form-xml-for-a-configuration-manager-property-sheet).
2. Define and deploy the action XML for displaying the context menu that the user selects. For more information, see [How to Create Action XML for a Configuration Manager Property Sheet](how-to-create-action-xml-for-a-configuration-manager-property-sheet).

    When you have created the property sheet assembly and XML, right-click a package in the Configuration Manager console tree **Packages** node results pane, and select the menu item **Show my Property Sheet**. A property sheet is displayed. You can enhance the control by accessing the package that was selected in the Configuration Manager console. For more information, see [How to Use Objects Passed to a Configuration Manager Forms](how-to-use-objects-passed-to-a-configuration-manager-form).

## Create the Control Class

The following procedure creates the control for the property sheet.

#### To create the Visual Studio project

1. In Visual Studio 2010, on the **File** menu, point to **New**, and then click **Project** to open the **New Project** dialog box.
2. From the list of Visual C#, Windows projects, select the **Windows Forms Control Library** project template, and then type `ConfigMgrControl` in the **Name** box.
3. Click **OK** to create the Visual Studio project.
4. In Solution Explorer, right-click the project and select Properties. On the Application tab, change Target framework to .NET Framework 4.
5. In Solution Explorer, right-click **UserControl1.cs**, click **Rename**, and then change the name to **ConfigMgrControl.cs**.
6. In Solution Explorer, right-click **References** and then click **Add Reference**.
7. In the **Add Reference** dialog box, click the **Browse** tab, navigate to **%ProgramFiles%\Microsoft Endpoint Manager\AdminConsole\bin** and then select **microsoft.configurationmanagement.exe**, **Microsoft.ConfigurationManagement.DialogFramework.dll** and **microsoft.configurationmanagement.managementprovider.dll** . Click **OK** to add the assemblies as project references.
8. In Solution Explorer, right-click **ConfigMgrControl.cs**, and then click **View Code**.
9. In the source code, change the namespace to `Microsoft.ConfigurationManagement.AdminConsole.ConfigMgrPropertySheet`
10. Change the class `ConfigMgrControlPage` so that it derives from `SmsPageControl`.
11. In Solution Explorer, right-click **ConfigMgrControl.Designer.cs**, and then click **View Code**.
12. In the source code, change the namespace to `Microsoft.ConfigurationManagement.AdminConsole.ConfigMgrPropertySheet`
13. In **ConfigMgrControl.cs**, Add the following new constructor to the `ConfigMgrControlPage` class:

    ```
    public ConfigMgrControlPage (SmsPageData pageData) : base(pageData)
    {
        InitializeComponent();
    }
    ```
14. Add the following method to initialize the control:

    ```
    public override void InitializePageControl()
    {
       base.InitializePageControl();
    }
    ```

## Deploy the Assembly

The following procedure builds and copies the assembly that you have created to the Configuration Manager console assemblies folder. For important information about deploying Configuration Manager console extensions, see [About Configuration Manager Administrator Console Extension Deployment](console-extension-deployment).

#### To deploy the property sheet assembly

1. Build the project. The assembly should be created as \Visual Studio 2010\Projects\ConfigMgrControl\ConfigMgrControl\bin\Debug\ConfigMgrControl.dll.
2. Copy the assembly to the folder %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\bin.