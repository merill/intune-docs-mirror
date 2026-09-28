---
layout: Conceptual
title: Handle Asynchronous Errors by Using Managed Code - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-asynchronous-errors-by-using-managed-code
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
description: To handle a Configuration Manager error raised during an asynchronous query, test the RunWorkerCompletedEventArgs parameter Error Exception property passed to the SmsBackgroundWorker.QueryProcessorCompleted event handler.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 94fea7a8-7dee-71f2-ea42-b516a29bb140
document_version_independent_id: b93de05a-50a9-8eac-4307-bbd1b8647477
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-asynchronous-errors-by-using-managed-code.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/how-to-handle-configuration-manager-asynchronous-errors-by-using-managed-code
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/how-to-handle-configuration-manager-asynchronous-errors-by-using-managed-code.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: b39e197d-a64d-c0d0-bdf4-54412cc27427
---

# Handle Asynchronous Errors by Using Managed Code - Configuration Manager | Microsoft Learn

To handle a Configuration Manager error that is raised during an asynchronous query, you test the `RunWorkerCompletedEventArgs` parameter [Error](/en-us/previous-versions/t1yswz5k%28v=vs.90%29) Exception property that is passed to the [SmsBackgroundWorker.QueryProcessorCompleted](/en-us/previous-versions/system-center/developer/cc143778%28v=msdn.10%29) event handler. If [Error](/en-us/previous-versions/t1yswz5k%28v=vs.90%29) is not `null`, an exception has occurred and you use [Error](/en-us/previous-versions/t1yswz5k%28v=vs.90%29) to discover the cause.

If [Error](/en-us/previous-versions/t1yswz5k%28v=vs.90%29) is an [SmsQueryException](/en-us/previous-versions/system-center/developer/cc147436%28v=msdn.10%29), you can use it to get to the underlying `__ExtendedException` or `SMS_ExtendedException`. Because the managed SMS Provider library does not wrap these exceptions you will need to use the System.Management namespace [ManagementException](/en-us/dotnet/api/system.management.managementexception) object to access them.

### To handle an asynchronous query error

1. Create an asynchronous query.
2. In the asynchronous query [SmsBackgroundWorker.QueryProcessorCompleted](/en-us/previous-versions/system-center/developer/cc143778%28v=msdn.10%29) event handler, implement the code in the following example.
3. Run the asynchronous query. To test the exception handler, pass a badly formed query string such as `Select & from &&&` to the [QueryProcessorBase.ProcessQuery](/en-us/previous-versions/system-center/developer/cc146295%28v=msdn.10%29) method.

## Example

The following example implements a [SmsBackgroundWorker.QueryProcessorCompleted](/en-us/previous-versions/system-center/developer/cc143778%28v=msdn.10%29) event handler.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](calling-code-snippets).

```c
void bw1_QueryProcessorCompleted(object sender, RunWorkerCompletedEventArgs e)
{
    if (e.Error != null)
    {
        Console.WriteLine("There was an Error");
        if (e.Error is SmsQueryException)
        {
            SmsQueryException queryException = (SmsQueryException)e.Error;
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
        if (e.Error is SmsConnectionException)
        {
            Console.WriteLine("There was a connection error :" + ((SmsConnectionException)e.Error).Message);
            Console.WriteLine(((SmsConnectionException)e.Error).ErrorCode);
        }
    }

    Console.WriteLine("Done...");
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `sender` | - `Object` | The source of the event. |
| `e` | - `RunWorkerCompletedEventArgs` | The event data. For more information, see [RunWorkerCompletedEventArgs Class](/en-us/dotnet/api/system.componentmodel.runworkercompletedeventargs). |

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