---
layout: Conceptual
title: Apply custom client settings - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/programming/how-to-apply-custom-client-settings
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
description: Use the SDK to apply custom client settings.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: afc639e9-9f0e-b677-1dfc-7ba61e82dbfa
document_version_independent_id: 7f5379f8-9295-b299-3c9c-c7605751f25e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/programming/how-to-apply-custom-client-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/programming/how-to-apply-custom-client-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/programming/how-to-apply-custom-client-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 2098eb80-9d79-b4d8-9474-730cd311b509
---

# Apply custom client settings - Configuration Manager | Microsoft Learn

In Configuration Manager, you apply custom client settings by creating an instance of a Client Configuration class, and then deploying the custom client settings by creating an instance of the `SMS_ClientSettingsAssignment` class and associating the instance of the Client Configuration class and a target collection.

### To apply custom client settings

1. Set up a connection to the SMS Provider.
2. Create an instance of a Client Configuration class (such as `SMS_StateSystemConfig` used below).
3. Populate specific custom client agent settings.
4. Create an instance of the `SMS_ClientSettingsAssignment` class.
5. Populate the client settings assignment values. `ClientSettingsID` to identify the custom client settings instance and `CollectionID` to identify the target collection for the deployment of the custom client settings.

## Example

The following example applies custom client settings by creating an instance of a Client Configuration class, and then deploying the custom client settings by creating an instance of the `SMS_ClientSettingsAssignment` class and associating the instance of the Client Configuration class and a target collection.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../../understand/calling-code-snippets).

```c

public void ApplyCustomClientSettings(WqlConnectionManager connection,string targetCollectionID){
    try
    {
        // Create a new instance of specific client agent settings (in this case State Messaging)
        IResultObject newCustomClientAgentSettings = connection.CreateEmbeddedObjectInstance("SMS_StateSystemConfig");

        // Populate specific custom client agent settings
        newCustomClientAgentSettings["BulkSendInterval"].IntegerValue = 120;
        newCustomClientAgentSettings["BulkSendIntervalHigh"].IntegerValue = 5;
        newCustomClientAgentSettings["BulkSendIntervalLow"].IntegerValue = 30;

        // Create a new array list to hold the custom client agent settings object(s)
        List<IResultObject> tempAgentConfigurationsArray = new List<IResultObject>();

        // Add the custom client agent settings embedded object to the local array list
        tempAgentConfigurationsArray.Add(newCustomClientAgentSettings);

        // Create a new instance of SMS_ClientSettings
        IResultObject newClientSettings = connection.CreateInstance("SMS_ClientSettings");

        // Populate the client agent settings
        newClientSettings["Name"].StringValue = "Custom State Messaging Configuration";

        // Add the array of custom client agent settinsg object(s) to the AgentConfigurations property
        newClientSettings.SetArrayItems("AgentConfigurations", tempAgentConfigurationsArray);

        // Save and retrieve the new instance of SMS_ClientSettings
        newClientSettings.Put();
        newClientSettings.Get();

        // Get the SettingsID value of the new SMS_ClientSettings instance
        Int32 SettingsID = newClientSettings["SettingsID"].IntegerValue;

        // Create a new instance of SMS_ClientSettingsAssignment
        IResultObject newClientSettingsAssignment = connection.CreateInstance("SMS_ClientSettingsAssignment");

        // Populate the client settings assignment values
        // ClientSettingsID to identify the custom client settings
        // CollectionID to identify the target collection for the custom client settings
        newClientSettingsAssignment["ClientSettingsID"].IntegerValue = SettingsID;
        newClientSettingsAssignment["CollectionID"].StringValue = targetCollectionID;

        // Save the new instance of the client settings assignment.
        newClientSettingsAssignment.Put();
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager` | A valid connection to the SMS Provider. |
| `targetCollectionID` | - Managed: `String` | The target collection for the custom client settings deployment. |

## Compiling the Code

This C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../../understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../../servers/configure/role-based-administration).