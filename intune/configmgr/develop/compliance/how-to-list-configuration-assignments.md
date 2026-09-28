---
layout: Conceptual
title: List Configuration Assignments - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/how-to-list-configuration-assignments
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
description: The following code examples show how to list the current configuration baseline assignments and a specific set of properties for each assignment in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: f4123308-cae5-5175-9206-22d526c32ea0
document_version_independent_id: e0e8fd4f-488e-b24f-97be-ce04121f6376
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/compliance/how-to-list-configuration-assignments.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/compliance/how-to-list-configuration-assignments
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/compliance/how-to-list-configuration-assignments.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/0850fefd-e402-4507-ae98-46cfdfc2e16c
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6ecf98a5-97c7-4249-b209-a9d9e42633a0
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: e6cd5309-5e4b-e14e-27d7-9f740837ec8d
---

# List Configuration Assignments - Configuration Manager | Microsoft Learn

The following code examples show how to list the current configuration baseline assignments and a specific set of properties for each assignment in Configuration Manager.

### To list Configuration Assignments

1. Set up a connection to the SMS Provider.
2. Query for all instances `SMS_BaselineAssignment`.
3. Loop through the array of available configuration baseline assignments, listing each configuration baseline assignment and specific properties.

## Example

The following example method shows how to list the current configuration baseline assignments and a specific set of properties for each assignment in Configuration Manager.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

Sub DCMAssignments_ListProperties(swbemServices)

    On Error Resume Next

    Dim queryBaselineAssignmentResults
    Dim assignment

    ' Query assignments.
    Set queryBaselineAssignmentResults = swbemServices.ExecQuery("Select * From SMS_BaselineAssignment", , 0)

    If Err.Number<>0 Then
        Wscript.Echo "Couldn't get assignments."
        Exit Sub
    End If

    On Error Goto 0

    ' List assignments and various assignment's properties.
    For Each assignment In queryBaselineAssignmentResults
        Wscript.Echo ""
        Wscript.Echo "Listing Assignment Properties for Assignment ID: " & assignment.AssignmentID
        Wscript.Echo "Listing Assignment Properties for Assignment Description: " & assignment.AssignmentDescription
        Wscript.Echo "-------------------------------------------------------------------------------"
        Wscript.Echo "ApplyToSubTargets: " & assignment.ApplyToSubTargets
        Wscript.Echo "AssignmentAction:  " & assignment.AssignmentAction
        Wscript.Echo "AssignmentID: " & assignment.AssignmentID
        Wscript.Echo "AssignmentName: " & assignment.AssignmentName
        Wscript.Echo "AssignmentDescription: " & assignment.AssignmentDescription
        Wscript.Echo "AssignmentUniqueID: " & assignment.AssignmentUniqueID
        Wscript.Echo "Collection: " & assignment.TargetCollectionID
        Wscript.Echo "CreationTime: " & assignment.CreationTime
        Wscript.Echo "DesiredConfigType: " & assignment.DesiredConfigType
        Wscript.Echo "DPLocality: " & assignment.DPLocality
        Wscript.Echo "EvaluationSchedule: " & assignment.EvaluationSchedule
        Wscript.Echo "LogComplianceToWinEvent: " & assignment.LogComplianceToWinEvent
        Wscript.Echo "NotifyUser: " & assignment.NotifyUser
        Wscript.Echo "SendDetailedNonComplianceStatus: " & assignment.SendDetailedNonComplianceStatus
        Wscript.Echo "SourceSite: " & assignment.SourceSite
        Wscript.Echo "StartTime: " & assignment.StartTime
        Wscript.Echo "SuppressReboot: " & assignment.SuppressReboot
        Wscript.Echo "UseGMTTimes: " & assignment.UseGMTTimes
        Wscript.Echo "==============================================================================="
    Next

    If queryBaselineAssignmentResults.Count = 0 Then
        Wscript.Echo "      no query results"
    End If

    set queryBaselineAssignmentResults = Nothing

End Sub

```

```c

public void DCMAssignments_ListProperties(WqlConnectionManager connection)
{

    IResultObject baselineAssignments = connection.QueryProcessor.ExecuteQuery("SELECT * FROM SMS_BaselineAssignment");

    try
    {
        foreach (IResultObject assignment in baselineAssignments)
        {
            Console.WriteLine("Listing Assignment Properties for Assignment ID: " + assignment["AssignmentID"].StringValue);
            Console.WriteLine("Listing Assignment Properties for Assignment Description: " + assignment["AssignmentDescription"].StringValue);
            Console.WriteLine("--------------------------------------------------------------------------------");
            Console.WriteLine("ApplyToSubTargets: " + assignment["ApplyToSubTargets"].BooleanValue);
            Console.WriteLine("AssignmentAction:  " + assignment["AssignmentAction"].IntegerValue);
            Console.WriteLine("AssignmentID: " + assignment["AssignmentID"].StringValue);
            Console.WriteLine("AssignmentName: " + assignment["AssignmentName"].StringValue);
            Console.WriteLine("AssignmentDescription: " + assignment["AssignmentDescription"].StringValue);
            Console.WriteLine("AssignmentUniqueID: " + assignment["AssignmentUniqueID"].StringValue);
            Console.WriteLine("Collection: " + assignment["TargetCollectionID"].StringValue);
            Console.WriteLine("CreationTime: " + assignment["CreationTime"].StringValue);
            Console.WriteLine("DesiredConfigType: " + assignment["DesiredConfigType"].StringValue);
            Console.WriteLine("DPLocality: " + assignment["DPLocality"].IntegerValue);
            Console.WriteLine("EvaluationSchedule: " + assignment["EvaluationSchedule"].StringValue);
            Console.WriteLine("LogComplianceToWinEvent: " + assignment["LogComplianceToWinEvent"].BooleanValue);
            Console.WriteLine("NotifyUser: " + assignment["NotifyUser"].BooleanValue);
            Console.WriteLine("SendDetailedNonComplianceStatus: " + assignment["SendDetailedNonComplianceStatus"].BooleanValue);
            Console.WriteLine("SourceSite: " + assignment["SourceSite"].StringValue);
            Console.WriteLine("StartTime: " + assignment["StartTime"].StringValue);
            Console.WriteLine("SuppressReboot: " + assignment["SuppressReboot"].IntegerValue);
            Console.WriteLine("UseGMTTimes: " + assignment["UseGMTTimes"].BooleanValue);

            // Process the array.
            int[] arrayofAssignedCIs = assignment["AssignedCIs"].IntegerArrayValue;
            Console.Write("Assigned baseline ID(s): ");
            foreach (int i in arrayofAssignedCIs)
            {
                Console.Write(i + " ");
            }

            Console.WriteLine();

            // NULL BY DEFAULT (on a generic assignment created through the user interface).
            //
            //Console.WriteLine("EnforcementDeadline: " + assignment["EnforcementDeadline"].StringValue);
            //Console.WriteLine("ExpirationTime: " + assignment["ExpirationTime"].StringValue);
            //Console.WriteLine("NonComplianceCriticality: " + assignment["NonComplianceCriticality"].IntegerValue);
            //Console.WriteLine("OverrideServiceWindows: " + assignment["OverrideServiceWindows"].BooleanValue);
            //Console.WriteLine("RebootOutsideOfServiceWindows: " + assignment["RebootOutsideOfServiceWindows"].BooleanValue);
            //Console.WriteLine("WoLEnabled: " + assignment["WoLEnabled"].BooleanValue);

            Console.WriteLine("================================================================================");

        }

    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to list assignment properties. Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| - `connection`- `swbemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |

## Compiling the Code

### Namespaces

System

System.Collections.Generic

System.ComponentModel

Microsoft.ConfigurationManagement.ManagementProvider

Microsoft.ConfigurationManagement.ManagementProvider.WqlQueryEngine

### Assembly

adminui.wqlqueryengine

microsoft.configurationmanagement.managementprovider

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).