---
layout: Conceptual
title: Add a Category to a Windows Driver - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-category-to-a-windows-driver
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
description: In Configuration Manager, you add a category to a Windows driver by adding the unique identifier for the category to the SMS_Driver Server WMI Class CategoryInstance_UniqueIDs array property.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 68b6dfbf-66d4-35b0-41e5-9872a35384b8
document_version_independent_id: 3e2c1c05-5e62-9843-c7ca-79b58b25e38d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-add-a-category-to-a-windows-driver.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-add-a-category-to-a-windows-driver
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-add-a-category-to-a-windows-driver.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 9b6bb180-9c62-4058-88c2-f0321abd4539
---

# Add a Category to a Windows Driver - Configuration Manager | Microsoft Learn

In Configuration Manager, you add a category to a Windows driver by adding the unique identifier for the category to the [SMS_Driver Server WMI Class](../reference/osd/sms_driver-server-wmi-class)`CategoryInstance_UniqueIDs` array property. The array contains one or more string identifiers that match the [SMS_CategoryInstance Server WMI Class](../reference/compliance/sms_categoryinstance-server-wmi-class)`CategoryInstance_UniqueID` property value. There is an instance of [SMS_CategoryInstance Server WMI Class](../reference/compliance/sms_categoryinstance-server-wmi-class) object for each category in the system.

Note

The unique identifier for a driver category is prepended with the text "DriverCategories". Other category types have different text.

A category has localization information, and it is from the [SMS_CategoryInstance Server WMI Class](../reference/compliance/sms_categoryinstance-server-wmi-class)`LocalizedCategoryInstanceName` property that the display name of the category is obtained.

### To add a category to a Windows driver

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get the [SMS_Driver](../reference/osd/sms_driver-server-wmi-class) object for the driver you want to add a category to.
3. Get the category name identifier from the [SMS_CategoryInstance Server WMI Class](../reference/compliance/sms_categoryinstance-server-wmi-class) object that matches the desired category.
4. Add the category identifier to the [SMS_Driver Server WMI Class](../reference/osd/sms_driver-server-wmi-class) object `CategoryInstance_UniqueIDs` array property.
5. Commit the [SMS_Driver Server WMI Class](../reference/osd/sms_driver-server-wmi-class) changes.

## Example

The following example method adds a category to a Windows driver. `driverID` is a valid [SMS_Driver Server WMI Class](../reference/osd/sms_driver-server-wmi-class) object. For more information, see [About Operating System Deployment Driver Management](about-operating-system-deployment-driver-management).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub AddDriverCategory(connection,driver,categoryName)

    Dim categories
    Dim category
    Dim driverCategoryID
    Dim categoryID
    Dim results
    Dim existingCategory

    ' Find the category that matches the supplied category name.
    Set results = _
      connection.ExecQuery("SELECT * From SMS_CategoryInstance WHERE LocalizedCategoryInstanceName = '" _
      + categoryName+ "'")

    ' If the category was found, add it to the driver.
    For Each category in results

        If IsNull(driver.CategoryInstance_UniqueIDs) or UBound (driver.CategoryInstance_UniqueIDs) = -1 Then
            ' It is empty. Add the category.
            driver.CategoryInstance_UniqueIDs =  Array(category.CategoryInstance_UniqueID)
         Else

            ' Determine if the category is already applied to the driver.
            For each existingCategory in driver.CategoryInstance_UniqueIDs
                if existingCategory = category.CategoryInstance_UniqueID Then
                    WScript.Echo "Already added"
                    Exit Sub
                End If
            Next

            ' Add the category.
            categories = driver.CategoryInstance_UniqueIDs
            Redim Preserve categories (UBound (driver.CategoryInstance_UniqueIDs)+1)
            categories (Ubound (categories)) =  category.CategoryInstance_UniqueID
            driver.CategoryInstance_UniqueIDs = categories
        End If

        driver.Put_
    Next
End Sub
```

```c
public void AddDriverCategory(
    WqlConnectionManager connection,
    IResultObject driver,
    string categoryName)
{
    try
    {
        // Get the category.
        IResultObject results = connection.QueryProcessor.ExecuteQuery(
        "SELECT * From SMS_CategoryInstance WHERE LocalizedCategoryInstanceName = '" + categoryName + "'");

       ArrayList driverCategories = new ArrayList(driver["CategoryInstance_UniqueIDs"].StringArrayValue);//;driverCategories);

        foreach (IResultObject category in results)
        {
            foreach (string driverCategory in driverCategories)
            {
                // Do nothing if the driver already has the category.
                if (driverCategory == category["CategoryInstance_UniqueID"].StringValue)
                {
                    Console.WriteLine("Already exists");
                    return;
                }
           }

            // Add the category to the action.
           driverCategories.Add(category["CategoryInstance_UniqueID"].StringValue);
        }

        // Update the driver.
        driver["CategoryInstance_UniqueIDs"].StringArrayValue = (string[])driverCategories.ToArray(typeof(string));
        driver.Put();

    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to add the category" + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | - Managed: `WqlConnectionManager` - VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices-get) | A valid connection to the SMS Provider. |
| `driver` | - Managed: `IResultObject` - VBScript: `SWbemObject` | The Windows driver. It is an instance of [SMS_Driver Server WMI Class](../reference/osd/sms_driver-server-wmi-class). |
| `categoryName` | - Managed: `String` - VBScript: `String` | The name of an existing category. This matches the [SMS_CategoryInstance Server WMI Class](../reference/compliance/sms_categoryinstance-server-wmi-class)`LocalizedCategoryInstanceName` property. |

## Compiling the Code

This C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).