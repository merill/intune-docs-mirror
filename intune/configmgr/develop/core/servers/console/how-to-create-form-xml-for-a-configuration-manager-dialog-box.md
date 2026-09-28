---
layout: Conceptual
title: Create Form XML for a Dialog Box - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-form-xml-for-a-configuration-manager-dialog-box
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
description: To create the form XML for a Configuration Manager dialog box, you create an XML file that describes an SmsFormData.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c24e0c8e-8a9d-00a1-61ad-fdbf6afae2c2
document_version_independent_id: a8f6f952-9fe6-f91a-adf3-a0a9defa5790
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-create-form-xml-for-a-configuration-manager-dialog-box.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-create-form-xml-for-a-configuration-manager-dialog-box
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-create-form-xml-for-a-configuration-manager-dialog-box.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 430c375b-7693-07d4-c867-3274e429e111
---

# Create Form XML for a Dialog Box - Configuration Manager | Microsoft Learn

In Configuration Manager, to create the form XML for a Configuration Manager dialog box, you create an XML file that describes a [SmsFormData](/en-us/previous-versions/system-center/developer/cc147304%28v=msdn.10%29).

The form XML is similar to the property sheet form XML with the following exceptions:

- `FormType` must be set to `Dialog`.

    The following procedure demonstrates how to create the form XML file for the dialog box you created in [How to Create a Configuration Manager Dialog Box](how-to-create-a-configuration-manager-dialog-box).

### To create the form XML for a dialog box

1. If it is open, close the Configuration Manager console.
2. In Notepad, create an XML file that contains the following XML:

    ```
    
    <?xml version="1.0" encoding="utf-8"?>
    <SmsFormData FormatVersion="1.0" xmlns="https://schemas.microsoft.com/SystemsManagementServer/2005/03/ConsoleFramework">
      <Form Id="{DIALOGGUID}" CustomData="User Properties" FormType="CustomDialog" >
        <Assembly Name="ConfigMgrDialogControl" Namespace="Microsoft.ConfigurationManagement.AdminConsole.ConfigMgrDialogBox" ClassType="ConfigMgrDialogControl"/>
      </Form>
    </SmsFormData>
    ```
3. In Visual Studio 2010, on the **Tools** menu, click **Create GUID**.
4. In the **Create GUID** dialog box, in the **GUID format** panel, select **Registry Format**.
5. Click **New GUID**, and then click **Copy**.
6. In the XML above, paste the GUID into DIALOGGUID. Be sure to keep the open **{** and closing **}** in the XML.
7. Save the XML file in the folder, %*ProgramFiles*%\AdminConsole\XmlStorage\Extensions\Forms with the file name ConfigMgrDialogControl.xml. The file name must match the `DialogId` element of the action XML. If the Extensions folder does not yet exist, create it. Be sure to save the file as type `All Files`.
8. Start the Configuration Manager console, and select the action you defined in [How to Create Action XML for a Configuration Manager Dialog Box](how-to-create-action-xml-for-a-configuration-manager-dialog-box).

    The property sheet you created in [How to Create a Configuration Manager Dialog Box](how-to-create-a-configuration-manager-dialog-box) appears.