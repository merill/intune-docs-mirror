---
layout: Conceptual
title: View File Usage Summary Information - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-view-file-usage-summary-information
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
description: Learn how to use the SMS_MeteredFiles and SMS_FileUsageSummary classes to view file usage summary in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c076d20c-fb75-b2b2-9002-eee53f77809d
document_version_independent_id: 6dcecc6b-9d02-422d-78ce-acdf0bfff2a6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-view-file-usage-summary-information.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-view-file-usage-summary-information
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-view-file-usage-summary-information.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
platformId: e27b9261-3400-d77b-215e-9ebd92618989
---

# View File Usage Summary Information - Configuration Manager | Microsoft Learn

You view file usage summary information, in Configuration Manager, by using the [SMS_MeteredFiles](../reference/apps/sms_meteredfiles-server-wmi-class) and [SMS_FileUsageSummary](../reference/apps/sms_fileusagesummary-server-wmi-class) classes.

### To view file usage summary information

1. Set up a connection to the SMS Provider.
2. Get a collection of all of the metered files [SMS_MeteredFiles](../reference/apps/sms_meteredfiles-server-wmi-class).
3. Get a collection of all of the summarized files [SMS_FileUsageSummary](../reference/apps/sms_fileusagesummary-server-wmi-class).
4. Loop through the summarized file information, displaying information as required.

## Example

The following example method displays file usage summary information by using the [SMS_MeteredFiles](../reference/apps/sms_meteredfiles-server-wmi-class) and [SMS_FileUsageSummary](../reference/apps/sms_fileusagesummary-server-wmi-class) classes.

Note

The example code below is relatively inefficient. In an environment with large amounts of data (large result sets), it would be better to do the query on SMS\_MeteredFiles, then loop over that result, doing individual queries for SMS\_FileUsageSummary where SMS\_FileUsageSummary.FileID=meteredFile.FileID.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

sub ViewFileUsageSummaryInfo(connection)

' Get SMS_MeteredFiles - used to match FileID to a file name

' Build query to get all metered files.
meteredFilesQuery = "SELECT * FROM SMS_MeteredFiles"

' Run query.
Set meteredFiles = connection.ExecQuery(meteredFilesQuery, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

' Get the summarized files.

' Build query to get all file usage summary information.
fileUsageSummaryQuery = "SELECT * FROM SMS_FileUsageSummary"

' Run query.
Set fileUsageSummary = connection.ExecQuery(fileUsageSummaryQuery, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

' Output file usage summary information.
For Each summariedFile in fileUsageSummary

    For each meteredFile in meteredFiles

        if meteredFile.MeteredFileID=summariedFile.FileID then
            wscript.echo "File Name: " & meteredFile.FileName
            Exit For
        end if

    next

    ' As matching summary information is found, output details.
    wscript.echo "File ID: "             & summariedFile.FileID
    wscript.echo "Distinct User Count: " & summariedFile.DistinctUserCount
    wscript.echo "Interval Start: "      & summariedFile.IntervalStart
    wscript.echo "Interval Width: "      & summariedFile.IntervalWidth
    wscript.echo "Site Code: "           & summariedFile.SiteCode
    wscript.echo " "

Next

end sub

```

```c

public void ViewFileUsageSummaryInfo(WqlConnectionManager connection)
{
    try
    {
        // Build query to get all metered files.
        string meteredFilesQuery = "SELECT * FROM SMS_MeteredFiles";

        // Run meteredFiles query.
        IResultObject meteredFilesTemp = connection.QueryProcessor.ExecuteQuery(meteredFilesQuery);

        // Cache values to local list.
        List<IResultObject> meteredFiles = new List<IResultObject>();
        foreach (IResultObject meteredFileTemp in meteredFilesTemp)
        {
            meteredFiles.Add(meteredFileTemp);
        }

        // Build query to get all the file usage summary information.
        string fileUsageSummaryQuery = "SELECT * FROM SMS_FileUsageSummary";

        // Run fileUsageSummary query.
        IResultObject fileUsageSummaryTemp = connection.QueryProcessor.ExecuteQuery(fileUsageSummaryQuery);

        // Cache values to local list.
        List<IResultObject> fileUsageSummary = new List<IResultObject>();
        foreach (IResultObject summariedFileTemp in fileUsageSummaryTemp)
        {
            fileUsageSummary.Add(summariedFileTemp);
        }

        // Enumerate through the files.
        foreach (IResultObject summariedFile in fileUsageSummary)
        {
            foreach (IResultObject meteredFile in meteredFiles)
            {
                if (meteredFile["MeteredFileID"].StringValue == summariedFile["FileID"].StringValue)
                {
                    // As matching summary information is found, output details.
                    Console.WriteLine("File Name: " + meteredFile["MeteredFileName"].StringValue);
                    break;
                };
            };

            // As matching summary information is found, output details.
            Console.WriteLine("File ID: " + summariedFile["FileID"].StringValue);
            Console.WriteLine("Distinct User Count: " + summariedFile["DistinctUserCount"].StringValue);
            Console.WriteLine("Interval Start: " + summariedFile["IntervalStart"].StringValue);
            Console.WriteLine("Interval Width: " + summariedFile["IntervalWidth"].StringValue);
            Console.WriteLine("Site Code: " + summariedFile["SiteCode"].StringValue);
            Console.WriteLine(" ");
        };
    }
    catch (SmsException ex)
    {
        Console.WriteLine();
        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |

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