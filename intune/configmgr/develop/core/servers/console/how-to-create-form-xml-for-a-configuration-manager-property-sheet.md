---
layout: Conceptual
title: Create Form XML for a Property Sheet - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-form-xml-for-a-configuration-manager-property-sheet
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
description: Learn how to create an XML file that describes an SmsFormData class using a Create Form XML for a Configuration Manager property sheet.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c4cc9704-9393-c6db-7680-c10596d2a61f
document_version_independent_id: 3181c381-79bb-c340-92ef-bcfd0e92262a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-create-form-xml-for-a-configuration-manager-property-sheet.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-create-form-xml-for-a-configuration-manager-property-sheet
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-create-form-xml-for-a-configuration-manager-property-sheet.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 2b013240-9890-bce9-84d2-73af87307d76
---

# Create Form XML for a Property Sheet - Configuration Manager | Microsoft Learn

In Configuration Manager, to create the form XML for a Configuration Manager property sheet, you create an XML file that describes an `SmsFormData`.

Every Configuration Manager console form extension has an associated form XML file that describes the assembly, the type of the form to be displayed, and—in the case of property sheets—how the property pages are organized. The property sheet XML file is referenced by the action XML when an action is selected.

Note

The name of the form XML file is significant because it is used in the action XML to identify the form XML.

The following procedure demonstrates how to create the form XML file for the control and property page you created in [How to Create a Configuration Manager Property Sheet](how-to-create-a-configuration-manager-property-sheet).

After completing the following procedure, you must create an action to load the property sheet. For more information, see [How to Create Action XML for a Configuration Manager Property Sheet](how-to-create-action-xml-for-a-configuration-manager-property-sheet).

Note

To see the form XML used by the Configuration Manager console, see %*ProgramFiles*%\AdminConsole\XmlStorage\Forms. These can be useful for creating your own form XML.

### To create the form XML for a property sheet

1. If it is open, close the Configuration Manager console.
2. In Notepad, create an XML file that contains the following XML:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <SmsFormData xmlns="https://schemas.microsoft.com/SystemsManagementServer/2005/03/ConsoleFramework" FormatVersion="1">
      <Form Id="PROPERTYSHEETGUID" CustomData="SomeData" FormType="PropertySheet" ForceRefresh="true">
        <Assembly Name="ConfigMgrControl.dll" Namespace="Microsoft.ConfigurationManagement.AdminConsole.ConfigMgrPropertySheet" />
        <Pages>
          <Page VendorId="YOURCOMPANY" Id="VENDORGUID" Type="ConfigMgrControlPage" />
        </Pages>
      </Form>
    </SmsFormData>
    ```
3. In Visual Studio 2010, on the **Tools** menu, click **Create GUID**.
4. In the **Create GUID** dialog box, in the **GUID format** panel, select **Registry Format**.
5. Click **New GUID**, and then click **Copy**.
6. In the XML above, paste the GUID into PROPERTYSHEETGUID. A single opening `{` and a single closing `}` must wrap the GUID. For example, `{ab60b75e-b64a-44c0-ad63-d96d289f39ca}`.
7. Repeat steps 3 through 5, and paste the GUID into VENDORGUID.
8. In the preceding XML, change YOURCOMPANY to your company name.
9. Save the XML file in the folder %*ProgramFiles*%\AdminConsole\XmlStorage\Extensions\Forms with the file name ConfigMgrPropertySheet.xml. Be sure to save the file as type `All Files`. If the Extensions folder and Forms folder do not yet exist, create them.
10. Start the Configuration Manager console, and select the action you defined in [How to Create Action XML for a Configuration Manager Property Sheet](how-to-create-action-xml-for-a-configuration-manager-property-sheet).

    The property sheet you created in [How to Create a Configuration Manager Property Sheet](how-to-create-a-configuration-manager-property-sheet) appears.