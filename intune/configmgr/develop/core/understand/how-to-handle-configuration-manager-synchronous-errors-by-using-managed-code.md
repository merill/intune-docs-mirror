---
layout: Conceptual
title: Handle Synchronous Errors by Using Managed Code - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-synchronous-errors-by-using-managed-code
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
description: To handle a Configuration Manager error raised in a synchronous query, catch the SmsQueryException exception.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: f17f6913-9b3e-6665-bbc3-9311b403a7c7
document_version_independent_id: 0f159c68-0a4b-8432-139b-a181ee1457d7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-synchronous-errors-by-using-managed-code.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-handle-configuration-manager-synchronous-errors-by-using-managed-code
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-synchronous-errors-by-using-managed-code.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/029d2366-5c16-4816-8cb8-dadeaf730762
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/082dcafd-01b6-47e9-8abe-5795dbab1ea9
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: d564c035-2f12-6557-07e1-13e3432c4cde
---

# Handle Synchronous Errors by Using Managed Code - Configuration Manager | Microsoft Learn

To handle a Configuration Manager error that is raised in a synchronous query, you catch the [SmsQueryException](/en-us/previous-versions/system-center/developer/cc147436%28v=msdn.10%29) exception. Because this exception is also caught by SMS\_Exception], you can catch it and the [SmsConnectionException](/en-us/previous-versions/system-center/developer/cc147431%28v=msdn.10%29) exception in the same catch block.

If the exception that is caught in an SMS\_Exception is an [SmsQueryException](/en-us/previous-versions/system-center/developer/cc147436%28v=msdn.10%29), you can use it to get to the underlying `__ExtendedException` or `SMS_ExtendedException`. Because the managed SMS Provider library does not wrap these exceptions, you will need to use the System.Management namespace [ManagementException](/en-us/dotnet/api/system.management.managementexception) object to access them.

Note

For clarity, most examples in this documentation simply re-throw exceptions. You can replace them with the following example if you want more informative exception information.

### To handle a synchronous query error

1. Write code to access the SMS Provider.
2. Use the following example code to catch the [SmsQueryException](/en-us/previous-versions/system-center/developer/cc147436%28v=msdn.10%29) and [SmsConnectionException](/en-us/previous-versions/system-center/developer/cc147431%28v=msdn.10%29) exceptions.

## Example

The following C# example function attempts to open a nonexistent `SMS_Package` package. In the exception handler, the code determines what type of error has been raised and displays its information.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```c
public void ExerciseException(WqlConnectionManager connection)
{
    try
    {

        IResultObject package = connection.GetInstance(@"SMS_Package.PackageID='UNKNOWN'");
        Console.WriteLine("Package Name: " + package["Name"].StringValue);
        Console.WriteLine("Package Description: " + package["Description"].StringValue);

    }
    catch (SmsException e)
    {
        if (e is SmsQueryException)
        {
            SmsQueryException queryException = (SmsQueryException)e;
            Console.WriteLine(queryException.Message);

            // Get either the __ExtendedStatus or SMS_ExtendedStatus object and display various properties.
            ManagementException mgmtExcept = queryException.InnerException as ManagementException;

            if (mgmtExcept != null)
            {
                if (string.Equals(mgmtExcept.ErrorInformation.ClassPath.ToString(), "SMS_ExtendedStatus", StringComparison.OrdinalIgnoreCase) == true)
                {
                    Console.WriteLine("Configuration Manager provider exception");
                }

                else if (string.Equals(mgmtExcept.ErrorInformation.ClassPath.ToString(), "__ExtendedStatus", StringComparison.OrdinalIgnoreCase) == true)
                {
                    Console.WriteLine("WMI exception");
                }
                Console.WriteLine(mgmtExcept.ErrorCode.ToString());
                Console.WriteLine(mgmtExcept.ErrorInformation["ParameterInfo"].ToString());
                Console.WriteLine(mgmtExcept.ErrorInformation["Operation"].ToString());
                Console.WriteLine(mgmtExcept.ErrorInformation["ProviderName"].ToString());
            }

        }
        if (e is SmsConnectionException)
        {
            Console.WriteLine("There was a connection error :" + ((SmsConnectionException)e).Message);
            Console.WriteLine(((SmsConnectionException)e).ErrorCode);
        }
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - `WqlConnectionManager` | A valid connection to the provider. |

## Compiling the Code

This C# example requires:

### Namespaces

System

System.Collections.Generic

System.Text

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

System.Management

System.ComponentModel

### Assembly

microsoft.configurationmanagement.managementprovider

adminui.wqlqueryengine

System.Management

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](about-configuration-manager-errors).