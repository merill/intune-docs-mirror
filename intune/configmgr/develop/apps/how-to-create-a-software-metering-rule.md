---
layout: Conceptual
title: How to Create a Software Metering Rule - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-create-a-software-metering-rule
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
description: You can create a software metering rule in Configuration Manager by creating an instance of the SMS_MeteredProductRule class and populating the properties.
locale: en-us
document_id: f9e44297-1b0c-2c40-63e2-0e1a6de6f5d7
document_version_independent_id: 02261161-dd33-b282-ef2f-d78f03c1cb5d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-create-a-software-metering-rule.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-create-a-software-metering-rule
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-create-a-software-metering-rule.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 6052cdf9-887c-1f18-f0af-7c794c24a0ac
---

# How to Create a Software Metering Rule - Configuration Manager | Microsoft Learn

You create a software metering rule, in Configuration Manager, by creating an instance of the `SMS_MeteredProductRule` class and populating the properties.

### To create software metering rule

1. Set up a connection to the SMS Provider.
2. Create the new software metering rule object by using the `SMS_MeteredProductRule` class.
3. Populate the new software metering rule properties.
4. Save the new software metering rule and properties.

## Example

The following example method shows how to create a software metering rule by creating an instance of the `SMS_MeteredProductRule` class and populating the properties.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vb

Sub CreateSWMRule(connection,              _
                  newProductName,          _
                  newFileName,             _
                  newOriginalFileName,     _
                  newFileVersion,          _
                  newLanguageID,           _
                  newSiteCode,             _
                  newApplyToChildSites)

    ' Create the new MeteredProductRule object.
    Set newSWMRule = connection.Get("SMS_MeteredProductRule").SpawnInstance_

    ' Populate the SMS_MeteredProductRule properties.
    newSWMRule.ProductName= newProductName
    newSWMRule.FileName = newFileName
    newSWMRule.OriginalFileName =  newOriginalFileName
    newSWMRule.FileVersion = newFileVersion
    newSWMRule.LanguageID = newLanguageID
    newSWMRule.SiteCode = newSiteCode
    newSWMRule.ApplyToChildSites = newApplyToChildSites

    ' Save the new rule and properties.
    newSWMRule.Put_

    ' Output new rule name.
    Wscript.Echo "Created new SWM Rule: " & newProductName

End Sub
```

```c

public void CreateSWMRule(WqlConnectionManager connection,
                          string newProductName,
                          string newFileName,
                          string newOriginalFileName,
                          string newFileVersion,
                          int newLanguageID,
                          string newSiteCode,
                          bool newApplyToChildSites)
{
    try
    {
        // Create the new SMS_AuthorizationList object.
        IResultObject newSWMRule = connection.CreateInstance("SMS_MeteredProductRule");

        // Populate the new SMS_MeteredProductRule object properties.
        newSWMRule["ProductName"].StringValue = newProductName;
        newSWMRule["FileName"].StringValue = newFileName;
        newSWMRule["OriginalFileName"].StringValue = newOriginalFileName;
        newSWMRule["FileVersion"].StringValue = newFileVersion;
        newSWMRule["LanguageID"].IntegerValue = newLanguageID;
        newSWMRule["SiteCode"].StringValue = newSiteCode;
        newSWMRule["ApplyToChildSites"].BooleanValue = newApplyToChildSites;

        // Save changes.
        newSWMRule.Put();

        Console.WriteLine();
        Console.WriteLine("Created new SWM Rule: " + newProductName);
    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed to create SWM rule. Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: `SWbemServices` | A valid connection to the SMS Provider. |
| `newProductName` | - Managed: `String`- VBScript: `String` | The new product name. |
| `newFileName` | - Managed: `String`- VBScript: `String` | The new file name. |
| `newOriginalFileName` | - Managed: `String`- VBScript: `String` | The new original file name. |
| `newFileVersion` | - Managed: `String`- VBScript: `String` | The new file version. |
| `newLanguageID` | - Managed: `Integer`- VBScript: `Integer` | The new language ID. |
| `newSiteCode` | - Managed: `String`- VBScript: `String` | The new site code. |
| `newApplyToChildSites` | - Managed: `Boolean`- VBScript: `Boolean` | Determines whether the rule will apply to child sites. |

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