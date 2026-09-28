---
layout: Conceptual
title: Remove a Category from a Windows Driver - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-remove-a-category-from-a-windows-driver
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
description: Learn about how to remove a category from a Windows driver by modifying the CategoryInstance_UniqueIDs array property.
locale: en-us
document_id: 504404a1-2806-87bc-0582-b789b7f3f817
document_version_independent_id: 52a5e7a8-c075-7b84-3384-c1c57e58b7ad
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-remove-a-category-from-a-windows-driver.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-remove-a-category-from-a-windows-driver
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-remove-a-category-from-a-windows-driver.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d1274a33-5e1f-43e1-b6c6-c6e111f32e49
---

# Remove a Category from a Windows Driver - Configuration Manager | Microsoft Learn

In Configuration Manager, you remove a category from a Windows driver by removing the unique identifier for the category from the [SMS_Driver Server WMI Class](../reference/osd/sms_driver-server-wmi-class)`CategoryInstance_UniqueIDs` array property.

### To remove a category from a Windows driver

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get the [SMS_Driver](../reference/osd/sms_driver-server-wmi-class) object for the driver that you want remove the category from.
3. Get the category name identifier from the [SMS_CategoryInstance Server WMI Class](../reference/compliance/sms_categoryinstance-server-wmi-class) object that matches the desired category.
4. Remove the category identifier from the [SMS_Driver Server WMI Class](../reference/osd/sms_driver-server-wmi-class) object `CategoryInstance_UniqueIDs` array property.
5. Commit the [SMS_Driver Server WMI Class](../reference/osd/sms_driver-server-wmi-class) changes.

## Example

The following example method removes a category from a Windows driver. `driverID` is a valid [SMS_Driver Server WMI Class](../reference/osd/sms_driver-server-wmi-class) object. For more information, see [About Operating System Deployment Driver Management](about-operating-system-deployment-driver-management).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub RemoveDriverCategory(connection,driver,categoryName)

    Dim results
    Dim driverCategoryID
    Dim category
    Dim categories
    Dim i

    If IsNull(driver.CategoryInstance_UniqueIDs) _
           or UBound (driver.CategoryInstance_UniqueIDs) = -1 Then
        ' There are no categories, so quit.
        Wscript.Echo "No categories found"
        Exit Sub
    End If

     Set results = _
      connection.ExecQuery("SELECT * From SMS_CategoryInstance WHERE LocalizedCategoryInstanceName = '" _
      + categoryName+ "'")

    ' If the category was found, delete, if it is there, from the driver.
    For Each category In results

        ' Destination for copied categories.
        categories = Array(driver.CategoryInstance_UniqueIDs)
        i=0

        For Each driverCategoryID in driver.CategoryInstance_UniqueIDs
            If driverCategoryID = category.CategoryInstance_UniqueID Then
                ' Found it, so skip it.
                 Redim Preserve categories (UBound(categories))
            Else
                ' Copy the category.
                categories(i) = driverCategoryID
                i=i+1
            End If
        Next

        ' Make sure the array is empty.
        if i = 0  Then
            Redim categories(-1)
        End If

         driver.CategoryInstance_UniqueIDs = categories
         driver.Put_
    Next
End Sub
```

```c
public void RemoveDriverCategory(WqlConnectionManager connection,
    IResultObject driver,
    string categoryName)
{
    try
    {
        // Get the category.
        IResultObject results =
            connection.QueryProcessor.ExecuteQuery(
            "SELECT * From SMS_CategoryInstance WHERE LocalizedCategoryInstanceName = '"
            + categoryName
            + "'");

        ArrayList driverCategories = new ArrayList(driver["CategoryInstance_UniqueIDs"].StringArrayValue);

        // Remove the category from the driver.
        foreach (IResultObject category in results)
        {
            driverCategories.Remove(category["CategoryInstance_UniqueID"].StringValue);
        }

        // Update the driver.
        driver["CategoryInstance_UniqueIDs"].StringArrayValue = (string[])driverCategories.ToArray(typeof(string));
        driver.Put();
    }
    catch(SmsException e)
    {
        Console.WriteLine("Failed to remove category :" + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | - Managed:`WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `driver` | - Managed: `IResultObject`- VBScript: `SWbemObject` | The Windows driver. It is an instance of [SMS_Driver Server WMI Class](../reference/osd/sms_driver-server-wmi-class). |
| `categoryName` | - Managed: `String`- VBScript: `String` | The name of an existing category. This matches the [SMS_CategoryInstance Server WMI Class](../reference/compliance/sms_categoryinstance-server-wmi-class)e `LocalizedCategoryInstanceName` property. |

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