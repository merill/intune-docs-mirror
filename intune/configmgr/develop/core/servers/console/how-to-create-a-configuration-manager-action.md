---
layout: Conceptual
title: Create a Configuration Manager Action - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-action
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
description: Learn how to create a console action by creating an XML file that populates an ActionDescription XML element for the action.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: cccc4558-ae23-22ed-af42-206197dd81cb
document_version_independent_id: 47042361-0d3b-e8c9-d4f9-5fd012d93941
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-action.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-action
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/how-to-create-a-configuration-manager-action.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7ddd0ba-08b8-4055-8ab8-0da61f3dfbb3
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5cf7e60a-ca26-4c6f-befd-5e90eae977f5
platformId: 1df9f755-707c-25c6-e1a0-2a4e4ff3e5e8
---

# Create a Configuration Manager Action - Configuration Manager | Microsoft Learn

To create a Configuration Manager console action, in Configuration Manager, you create an XML file that populates an [ActionDescription](/en-us/previous-versions/system-center/developer/cc147252%28v=msdn.10%29) XML element for the action. You must then copy the XML file to the %*ProgramFiles*%\Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Actions\GUID folder.

For sample XML for each action type, see the following:

- [Configuration Manager Executable Action](executable-action)
- [Configuration Manager ShowDialog Action](showdialog-action)
- [Configuration Manager Report Action](report-action)
- [Configuration Manager AssemblyType Action](assemblytype-action)
- [Configuration Manager Group Action](group-action)

    For information about deploying the action XML, see [Configuration Manager Console Extension Deployment](console-extension-deployment).

### To add an executable action to the Configuration Manager console

1. If the Configuration Manager console is open, close it.
2. In Notepad, create an empty text file named MyConfigurationManagerNote.txt and save it to C:\.
3. In Notepad, create an XML file that contains the following XML:

    ```
    <ActionDescription Class="Executable" DisplayName="Make a Note" MnemonicDisplayName="Note" Description = "Make a note about software updates">    <ShowOn>      <string>DefaultContextualTab</string> <!-- RIBBON -->     <string>ContextMenu</string> <!-- Context Menu -->   </ShowOn>       <Executable>
      <FilePath>Notepad.exe</FilePath>
      <Parameters>C:\MyConfigurationManagerNote.txt</Parameters>
     </Executable>
    </ActionDescription>
    ```
4. Save the XML file in the folder &lt;%*Program Files*%&gt; Microsoft Endpoint Manager\AdminConsole\XmlStorage\Extensions\Actions\f5445252-da1d-450f-a772-7c3d3cb929fb. The GUID identifies the software updates folder. The file name can be anything with an .xml extension, but it does alphabetically affect the ordering of actions in the context-sensitive menu and in the actions pane. If it is not already created, you must create the Extensions\Actions\f5445252-da1d-450f-a772-7c3d3cb929fb folder structure. Be sure to save the file as type `All Files`.
5. Start the Configuration Manager console.

    In the Configuration Manager console, right-click the **Software Updates** node under **Computer Management**, and then click **Make a Note**. Notepad opens the text file.