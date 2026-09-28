---
layout: Conceptual
title: Create an Association Between Two Computers - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-association-between-two-computers-in-configuration-manager
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
description: You create an association between a reference and destination computer, in Configuration Manager, by calling the AddAssociation Method in Class SMS_StateMigration
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 96dee928-7cc8-2e4a-7929-dea1081e3709
document_version_independent_id: 60948b67-9397-0e7e-f763-358b36663f27
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-create-an-association-between-two-computers-in-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-create-an-association-between-two-computers-in-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-create-an-association-between-two-computers-in-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: adafda3a-bf4b-8035-0cef-750b407db23d
---

# Create an Association Between Two Computers - Configuration Manager | Microsoft Learn

You create an association between a reference and destination computer, in Configuration Manager, by calling the [AddAssociation Method in Class SMS_StateMigration](../reference/osd/addassociation-method-in-class-sms_statemigration).

Note

You call the [DeleteAssociation Method in Class SMS_StateMigration](../reference/osd/deleteassociation-method-in-class-sms_statemigration) to delete an association.

### To create an association between two computers

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Call the [AddAssociation Method in Class SMS_StateMigration](../reference/osd/addassociation-method-in-class-sms_statemigration).

## Example

The following example method adds an association between a source and reference computer.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub AssociateComputer(connection, referenceComputerResourceId, destinationComputerResourceId)

    Dim stateMigrationClass
    Dim inParams
    Dim outParams

    ' Get the state migration class.
    Set stateMigrationClass = connection.Get("SMS_StateMigration")

    ' Set up the parameters.
    Set inParams = _
      stateMigrationClass.Methods_("AddAssociation").InParameters.SpawnInstance_
    inParams.SourceClientResourceID = referenceComputerResourceId
    inParams.RestoreClientResourceID = destinationComputerResourceId

    ' Call the method.
    Set outParams = _
      connection.ExecMethod( "SMS_StateMigration", "AddAssociation", inParams)

   End Sub
```

```c
public void AssociateComputer(
    WqlConnectionManager connection,
    int referenceComputerResourceId,
    int destinationComputerResourceId)
{
    try
    {
        // Set up the reference and destination computer in parameters.
        Dictionary<string, object> inParams = new Dictionary<string, object>();
        inParams.Add("SourceClientResourceID", referenceComputerResourceId);
        inParams.Add("RestoreClientResourceID", destinationComputerResourceId);

        // Create the computer association.
       connection.ExecuteMethod("SMS_StateMigration", "AddAssociation", inParams);
    }
    catch (SmsException e)
    {
        Console.WriteLine("failed to make the association" + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `referenceComputerResourceID` | - Managed: `Integer`- VBScript: `Integer` | The Configuration Manager resource identifier for the reference computer. This is available from `SMS_R_System` class `ResourceId` property for the computer. |
| `destinationComputerResourceID` | - Managed: `Integer`- VBScript: `Integer` | The Configuration Manager resource identifier for the destination computer. This is available from `SMS_R_System` class `ResourceId` property for the computer. |

## Compiling the Code

The C# example has the following compilation requirements:

### Namespaces

System

System.Collections.Generic

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).