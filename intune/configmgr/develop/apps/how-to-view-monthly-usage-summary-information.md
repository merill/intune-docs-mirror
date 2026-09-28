---
layout: Conceptual
title: View Monthly Usage Summary Information - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/apps/how-to-view-monthly-usage-summary-information
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
description: Use the SMS_MeteredFiles, SMS_MonthlyUsageSummary, SMS_MeteredUser, and SMS_R_System classes to view the monthly usage summary information.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 2cf4b77d-1467-88e0-cc3a-1531c25582cf
document_version_independent_id: 24ee6273-4150-1fb0-3d20-31b0c5d33e34
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/apps/how-to-view-monthly-usage-summary-information.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/apps/how-to-view-monthly-usage-summary-information
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/apps/how-to-view-monthly-usage-summary-information.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: b2cf90c7-84de-a220-e4f4-22433693c473
---

# View Monthly Usage Summary Information - Configuration Manager | Microsoft Learn

You view monthly usage summary information, in Configuration Manager, by using the [SMS_MeteredFiles](../reference/apps/sms_meteredfiles-server-wmi-class), [SMS_MonthlyUsageSummary](../reference/apps/sms_monthlyusagesummary-server-wmi-class), [SMS_MeteredUser](../reference/apps/sms_metereduser-server-wmi-class) and [SMS_R_System](../reference/core/clients/manage/sms_r_system-server-wmi-class) classes.

Note

The metering data is only summarized at specified intervals (by default, daily at midnight). Metering data does not appear in the summarized data until the summarization task has run.

### To view monthly usage summary information

1. Set up a connection to the SMS Provider.
2. Get all the metered files ([SMS_MeteredFiles](../reference/apps/sms_meteredfiles-server-wmi-class)).
3. Get all the monthly file usage summary information ([SMS_MonthlyUsageSummary](../reference/apps/sms_monthlyusagesummary-server-wmi-class)).
4. Get all the metered users ([SMS_MeteredUser](../reference/apps/sms_metereduser-server-wmi-class)).
5. Get all the computer names ([SMS_R_System](../reference/core/clients/manage/sms_r_system-server-wmi-class)).
6. Loop through the collections, displaying information as required.

## Example

The following example method displays file usages summary information by using the [SMS_MeteredFiles](../reference/apps/sms_meteredfiles-server-wmi-class) and [SMS_FileUsageSummary](../reference/apps/sms_fileusagesummary-server-wmi-class) classes.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

Sub ViewMonthlySummary(connection)

    ' Get SMS_MeteredFiles - used to match FileID to a file name

        ' Build query to get all metered files.
        meteredFilesQuery = "SELECT * FROM SMS_MeteredFiles"

        ' Run query.
        Set meteredFiles = connection.ExecQuery(meteredFilesQuery, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

    ' Get SMS_MonthlyUsageSummary

        ' Build query to get all monthly summary information.
        monthlyUsageSummaryQuery = "SELECT * FROM SMS_MonthlyUsageSummary"

        ' Run query.
        Set monthlyUsageSummaries = connection.ExecQuery(monthlyUsageSummaryQuery, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

    'Get SMS_MeteredUser

        ' Build query to get all metered users.
        meteredUserQuery = "SELECT * FROM SMS_MeteredUser"

        ' Run query.
        Set meteredUsers = connection.ExecQuery(meteredUserQuery, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

    'Get computer names

        ' Build query to get all metered computers.
        meteredComputerQuery = "SELECT * FROM SMS_R_System"

        ' Run query.
        Set meteredComputers = connection.ExecQuery(meteredComputerQuery, , wbemFlagForwardOnly Or wbemFlagReturnImmediately)

    For Each summary in monthlyUsageSummaries

        For each meteredFile in meteredFiles
            if meteredFile.MeteredFileID=summary.FileID then
                wscript.echo "File Name:" & meteredFile.FileName
                Exit For
            end if
        next

        for each meteredUser in meteredUsers
            if meteredUser.MeteredUserID=summary.MeteredUserID then
                wscript.echo "User Name: " & meteredUser.FullName
                Exit For
            end if
        next

        wscript.echo "Usage Count:" & summary.UsageCount
        wscript.echo "Terminal Service Usage Count:" & summary.TSUsageCount

        for each computer in meteredComputers
            if computer.ResourceId=summary.ResourceID then
                wscript.echo "Computer:" & computer.Name
                Exit For
            end if
        next

        wscript.echo

    Next

end sub

```

```c

public void ViewMonthlySummaryInfo(WqlConnectionManager connection)
{
    try
    {
        // Get SMS_MeteredFiles - used to match FileID to a file name.

            // Build query to get all metered files.
            string meteredFilesQuery = "SELECT * FROM SMS_MeteredFiles";

            // Run meteredFiles query.
            IResultObject meteredFiles = connection.QueryProcessor.ExecuteQuery(meteredFilesQuery);

        // Get SMS_MonthlyUsageSummary.

            // Build query to get all of the monthly file usage summary information.
            string monthlyUsageSummaryQuery = "SELECT * FROM SMS_MonthlyUsageSummary";

            // Run monthlyUsageSummaryQuery query.
            IResultObject monthlyUsageSummaries = connection.QueryProcessor.ExecuteQuery(monthlyUsageSummaryQuery);

        // Get SMS_MeteredUsers.

            // Build query to get all of the metered users.
            string meteredUserQuery = "SELECT * FROM SMS_MeteredUser";

            // Run meteredUser query.
            IResultObject meteredUsers = connection.QueryProcessor.ExecuteQuery(meteredUserQuery);

        // Get computer names.

            // Build query to get all the metered computers.
            string meteredComputersQuery = "SELECT * FROM SMS_R_System";

            // Run fileUsageSummary query.
            IResultObject meteredComputers = connection.QueryProcessor.ExecuteQuery(meteredComputersQuery);

        // Enumerate through the lists, outputs results as matches are found.
        foreach (IResultObject summary in monthlyUsageSummaries)
        {
            foreach (IResultObject meteredFile in meteredFiles)
            {
                if (meteredFile["MeteredFileID"].StringValue == summary["FileID"].StringValue)
                {
                    Console.WriteLine("File Name: " + meteredFile["FileName"].StringValue);
                    break;
                };
            };

            foreach(IResultObject meteredUser in meteredUsers)
            {
                if (meteredUser["MeteredUserID"].StringValue == summary["MeteredUserID"].StringValue)
                {
                    Console.WriteLine("User Name: " + meteredUser["FullName"].StringValue);
                    break;
                }
            };

            Console.WriteLine("Usage Count: " + summary["UsageCount"].StringValue);
            Console.WriteLine("Terminal Service Usage Count: " + summary["TSUsageCount"].StringValue);

            foreach(IResultObject computer in meteredComputers)
            {
                if(computer["ResourceId"].StringValue == summary["ResourceID"].StringValue)
                {
                    Console.WriteLine("Computer: " + computer["Name"].StringValue);
                    break;
                }
            };

            //
            Console.WriteLine(" ");
        };
    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed. Error: " + ex.InnerException.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: **WqlConnectionManager**- VBScript: **SWbemServices** | A valid connection to the SMS Provider. |

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