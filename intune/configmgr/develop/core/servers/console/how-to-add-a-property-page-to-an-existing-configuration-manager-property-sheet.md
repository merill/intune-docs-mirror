---
layout: Conceptual
title: Add a Property Page to an Existing Property Sheet - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-add-a-property-page-to-an-existing-configuration-manager-property-sheet
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
description: Learn how to add a property page to an existing property sheet, in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 5109877b-d291-199a-fa0f-29d7c4742c5d
document_version_independent_id: 8e2a1673-c9d8-be77-eb28-96bf0583739f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-add-a-property-page-to-an-existing-configuration-manager-property-sheet.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-add-a-property-page-to-an-existing-configuration-manager-property-sheet
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-add-a-property-page-to-an-existing-configuration-manager-property-sheet.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://authoring-docs-microsoft.poolparty.biz/devrel/4628cbd9-6f47-4ae1-b371-d34636609eaf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://authoring-docs-microsoft.poolparty.biz/devrel/be21deb8-8c64-44b0-b71f-2dc56ca7364f
platformId: 228c86fb-2ece-31a7-ff7e-f0e08ba4dd87
---

# Add a Property Page to an Existing Property Sheet - Configuration Manager | Microsoft Learn

To add a property page to an existing property sheet, in Configuration Manager, you add the property page XML to the property sheet's XML file. For existing Configuration Manager property sheets, you copy the existing property XML file to the XmlStorage\Extensions\Forms folder from XmlStorage\Forms. When the Configuration Manager console loads, it will use the XML it finds in the XmlStorage\Extensions\Forms folder in preference to existing forms in XmlStorage\Forms.

Because multiple vendors can extend existing property sheets, you must deploy and remove your property sheets with care. For more information, see [About Configuration Manager Administrator Console Extension Deployment](console-extension-deployment).

The following procedure demonstrates how to add a property page to the `Properties` page for a package. To complete it. you will first need to create a property page. For more information, see [How to Create a Configuration Manager Property Sheet](how-to-create-a-configuration-manager-property-sheet).

### To add a property page to a Properties property sheet

1. Copy the package.xml file from %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Forms to %ProgramFiles%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Forms.
2. In the package.xml file, add the following property page XML (you should place it below the other `<Page>` elements, near the end of the file):

    ```
    <Page VendorId="My Company" Id="{3F52B74A-373A-4c97-A142-C93E230948F8}" Assembly="ConfigMgrControl" Namespace="Microsoft.ConfigurationManagement.AdminConsole.ConfigMgrPropertySheet" Type="ConfigMgrControlPage" />
    ```
3. In Visual Studio 2010, on the **Tools** menu, click **Create GUID**.
4. In the **Create GUID** dialog box, in the **GUID format** panel, select **Registry Format**.
5. Click **New GUID**, and then click **Copy**.
6. In the XML above, paste the GUID into PROPERTYSHEETGUID. A single opening `{` and a single closing `}` must wrap the GUID. For example, `{ab60b75e-b64a-44c0-ad63-d96d289f39ca}`.
7. Save the file, and start the Configuration Manager console.
8. Using the **Packages** node results pane, right-click a package, and then click **Properties**. The properties dialog box is displayed with your property page.