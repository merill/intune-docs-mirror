---
layout: Conceptual
title: Create an Update List - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-create-an-update-list
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
description: You create an update list that contains a set of software updates, in Configuration Manager, by creating an instance of the SMS_AuthorizationList class and populating the properties.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: db641724-25d7-268d-8e99-f30db98bc8be
document_version_independent_id: 292fffd5-18b7-6fb5-18eb-016ad2e93c36
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/how-to-create-an-update-list.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/how-to-create-an-update-list
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/how-to-create-an-update-list.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: ff2c4351-a4cd-e392-62fb-083872505a9d
---

# Create an Update List - Configuration Manager | Microsoft Learn

You create an update list that contains a set of software updates, in Configuration Manager, by creating an instance of the [SMS_AuthorizationList](../reference/sum/sms_authorizationlist-server-wmi-class) class and populating the properties.

### To create an update list

1. Set up a connection to the SMS Provider.
2. Create the new update list object using the `SMS_AuthorizationList` class.
3. Populate the new update list properties.
4. Save the new update list and properties.

## Example

The following example method shows how to create an update list that contains a set of software updates by creating an instance of the `SMS_AuthorizationList` class and populating the properties.

Important

The `LocalizedInformation` property that is used in this example requires an object array (embedded array) of the description information.

In the example, the `LocaleID` property is hard-coded to English (U.S.). If you need the locale for non-U.S. installations, you can get it from the [SMS_Identification Server WMI Class](../reference/core/servers/configure/sms_identification-server-wmi-class)`LocaleID` property.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

The following example shows the subroutine call in Visual Basic:

```vbscript

' Prework for CreateSUMUpdateList
' Create the array of CI_IDs.
dim newUpdates
newUpdates = Array(9)

' Create and populate an SMS_CI_LocalizedProperties object.
set SMSCILocalizedProperties = swbemservices.Get("SMS_CI_LocalizedProperties").SpawnInstance_

SMSCILocalizedProperties.Description = "Test Description"
SMSCILocalizedProperties.DisplayName = "Test Display Name"
SMSCILocalizedProperties.InformativeURL = "Test URL"
SMSCILocalizedProperties.LocaleID = "1033"

' Create an array to hold the SMS_CI_LocalizedProperties object.
dim newDescriptionInfo
newDescriptionInfo = Array(SMSCILocalizedProperties)

' Call the CreateSUMUpdateList method.
Call CreateSUMUpdateList(swbemServices,       _
                         newUpdates,          _
                         newDescriptionInfo)
```

The following example shows the method call in C#:

```csharp

// Prework for CreateSUMUpdateList
// Create array list (to hold the array of Localized Properties).
List<IResultObject> newDescriptionInfo = new List <IResultObject>();
IResultObject SMSCILocalizedProperties = WMIConnection.CreateEmbeddedObjectInstance("SMS_CI_LocalizedProperties");

// Populate the initial array values (this could be a loop to added more localized info).
SMSCILocalizedProperties["Description"].StringValue = "4 CI_IDs - 9,34,53,72 ";
SMSCILocalizedProperties["DisplayName"].StringValue = "Test Display Name";
SMSCILocalizedProperties["InformativeURL"].StringValue = "Test URL";
SMSCILocalizedProperties["LocaleID"].StringValue = "1033";

// Add the 'embedded properties' to newDescriptionInfo.
newDescriptionInfo.Add(SMSCILocalizedProperties);

// Create the array of CI_IDs.
int[] newCI_ID = new int[] { 9, 34, 53, 72 };

// Call the CreateSUMUpdateList method.
SUMSnippets.CreateSUMUpdateList(WMIConnection,
                                newCI_ID,
                                newDescriptionInfo);

```

```vbscript

Sub CreateSUMUpdateList(connection,         _
                        newUpdates,         _
                        newDescriptionInfo)

    ' Create the new UpdateList object.
    Set newUpdateList = connection.Get("SMS_AuthorizationList").SpawnInstance_

    ' Populate the UpdateList properties.
    ' Updates is an int32 array that maps to the CI_ID in SMS_SoftwareUpdate.
    newUpdateList.Updates = newUpdates
    ' Need to pass embedded properties (LocalizedInformation) here.
    newUpdateList.LocalizedInformation = newDescriptionInfo

    ' Save the new UpdateList and properties.
    newUpdateList.Put_

    ' Output the new UpdateList name.
    Wscript.Echo "Created Update List " & newUpdateList.LocalizedDisplayName

End Sub
```

```csharp

public void CreateSUMUpdateList(WqlConnectionManager connection,
                                 int [] newUpdates,
                                 List<IResultObject> newDescriptionInfo)
{
    try
    {
        // Create the new SMS_AuthorizationList object.
        IResultObject newUpdateList = connection.CreateInstance("SMS_AuthorizationList");

        // Populate the new SMS_AuthorizationList object properties.
        // Updates is an int32 array that maps to the CI_ID in SMS_SoftwareUpdate.
        newUpdateList["Updates"].IntegerArrayValue = newUpdates;
        // Pass embedded properties (LocalizedInformation) here.
        newUpdateList.SetArrayItems("LocalizedInformation", newDescriptionInfo);

        // Save changes.
        newUpdateList.Put();

        Console.WriteLine();
        Console.WriteLine("Created Update List. " );

    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed to create update list. Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `newUpdates` | - Managed: `Integer` array- VBScript: `Integer` array | An array of the updates that is associated with the Update List. |
| `newDescriptionInfo` | - Managed: `Object` array- VBScript: `Object` array | An object array (embedded properties) of the type `LocalizedInformation`. |

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

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).