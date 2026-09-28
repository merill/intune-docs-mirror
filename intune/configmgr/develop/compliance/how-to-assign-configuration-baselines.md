---
layout: Conceptual
title: Assign Configuration Baselines - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/how-to-assign-configuration-baselines
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
description: Learn how to assign a configuration baseline to a collection by creating an assignment instance, populated with a minimum set of required values, and saving.
locale: en-us
document_id: c4def576-dca0-6563-d458-696c8124e8b4
document_version_independent_id: 97cb4c9f-525e-f8a9-31e3-1a1f514c0e7c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/compliance/how-to-assign-configuration-baselines.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/compliance/how-to-assign-configuration-baselines
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/compliance/how-to-assign-configuration-baselines.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 65c1f82d-206c-0163-d8a3-b271380e5486
---

# Assign Configuration Baselines - Configuration Manager | Microsoft Learn

In Configuration Manager, to assign a configuration baseline to a collection, an assignment instance is created, populated with a minimum set of required values, and saved.

### To assign Configuration Baselines

1. Set up a connection to the SMS Provider.
2. Create an instance of `SMS_BaselineAssignment`.
3. Populate the instance properties.
4. Save the new `SMS_BaselineAssignment` instance.

## Example

The following code examples show how to create an instance of a baseline assignment.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

Sub DCMCreateAssignment(swbemServices,                     _
                        baselineID,                        _
                        applyToSubTargets,                 _
                        assignmentAction,                  _
                        assignmentName,                    _
                        assignmentDescription,             _
                        desiredConfigType,                 _
                        distributionPointLocality,         _
                        evaluationSchedule,                _
                        logComplianceToWinEvent,           _
                        notifyUser,                        _
                        sendDetailedNonComplianceStatus,   _
                        startTime,                         _
                        suppressReboot,                    _
                        targetCollectionID,                _
                        useGMTTimes)

' Create new assignment object.
set newAssignment = swbemServices.Get("SMS_BaselineAssignment").SpawnInstance_()

' Assign variable values to assignment properties.
'    //
'    // The following properties are set by the provider on put():
'    //     AssignmentID
'    //     AssignmentUniqueID
'    //     SourceSite
'    //     CreationTime

newAssignment.ApplyToSubTargets = applyToSubTargets
newAssignment.AssignmentAction = assignmentAction
newAssignment.AssignmentName = assignmentName
newAssignment.AssignmentDescription = assignmentDescription
newAssignment.DesiredConfigType = desiredConfigType
newAssignment.DPLocality = distributionPointLocality
newAssignment.EvaluationSchedule = evaluationSchedule
newAssignment.LogComplianceToWinEvent = logComplianceToWinEvent
newAssignment.NotifyUser = notifyUser
newAssignment.SendDetailedNonComplianceStatus = sendDetailedNonComplianceStatus
newAssignment.StartTime = startTime
newAssignment.SuppressReboot = suppressReboot
newAssignment.TargetCollectionID = targetCollectionID
newAssignment.UseGMTTimes = useGMTTimes
newAssignment.AssignedCIs = Array(baselineID)

' Save assignment.
newAssignment.Put_

Wscript.Echo " "
Wscript.Echo "Created new assignment."

End Sub

```

```c

public void DCMCreateAssignment(WqlConnectionManager connection,
                                bool applyToSubTargets,
                                int assignmentAction,
                                string assignmentName,
                                string assignmentDescription,
                                string desiredConfigType,
                                int distributionPointLocality,
                                string evaluationSchedule,
                                bool logComplianceToWinEvent,
                                bool notifyUser,
                                bool sendDetailedNonComplianceStatus,
                                string startTime,
                                int suppressReboot,
                                string targetCollectionID,
                                bool useGMTTimes,
                                int baselineID)
{

    // Set required variables.
    // Set AssignedCIs like array with a known baseline id (this is the initial creation of the assignment, so no existing values).
    int[] arrayBaselineNumbers = new int[] { baselineID };

    try
    {
        // Create new assignment object.
        IResultObject newAssignment = connection.CreateInstance("SMS_BaselineAssignment");

        // Assign variable values to assignment properties.
        //
        // The following properties are set by the provider on put():
        //     AssignmentID
        //     AssignmentUniqueID
        //     SourceSite
        //     CreationTime
        newAssignment["ApplyToSubTargets"].BooleanValue = applyToSubTargets;
        newAssignment["AssignmentAction"].IntegerValue = assignmentAction;
        newAssignment["AssignmentName"].StringValue = assignmentName;
        newAssignment["AssignmentDescription"].StringValue = assignmentDescription;
        newAssignment["DesiredConfigType"].StringValue = desiredConfigType;
        newAssignment["DPLocality"].IntegerValue = distributionPointLocality;
        newAssignment["EvaluationSchedule"].StringValue = evaluationSchedule;
        newAssignment["LogComplianceToWinEvent"].BooleanValue = logComplianceToWinEvent;
        newAssignment["NotifyUser"].BooleanValue = notifyUser;
        newAssignment["SendDetailedNonComplianceStatus"].BooleanValue = sendDetailedNonComplianceStatus;
        newAssignment["StartTime"].StringValue = startTime;
        newAssignment["SuppressReboot"].IntegerValue = suppressReboot;
        newAssignment["TargetCollectionID"].StringValue = targetCollectionID;
        newAssignment["AssignedCIs"].IntegerArrayValue = arrayBaselineNumbers;
        newAssignment["UseGMTTimes"].BooleanValue = useGMTTimes;

        // Save assignment object.
        newAssignment.Put();
    }
    catch (SmsException ex)
    {
        Console.WriteLine("Failed to create new assignment." + "\\n" + ex.Message);
        throw;
    }

    Console.WriteLine("Created new assignment.");

}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| - `connection`- `swbemServices` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `applyToSubTargets` | - Managed: `Boolean`- VBScript: `Boolean` | `true` to apply the configuration item assignment to a subcollection. |
| `assignmentAction` | - Managed: `Integer`- VBScript: `Integer` | Action associated with the configuration item assignment. |
| `assignmentName` | - Managed: `String`- VBScript: `String` | assignmentName |
| `assignmentDescription` | - Managed: `String`- VBScript: `String` | The local assignment name. |
| `desiredConfigType` | - Managed: `String`- VBScript: `String` | The type of the configuration item. |
| `distributionPointLocality` | - Managed: `Integer`- VBScript: `Integer` | Flags that determine how the client obtains distribution points, according to distribution point locality. |
| `evaluationSchedule` | - Managed: `String`- VBScript: `String` | The assignment evaluation schedule. |
| `logComplianceToWinEvent` | - Managed: `Boolean`- VBScript: `Boolean` | `true` to log compliance status to Windows event logs. |
| `notifyUser` | - Managed: `Boolean`- VBScript: `Boolean` | `true` to notify the user when a configuration item is available. |
| `sendDetailedNonComplianceStatus` | - Managed: `Boolean`- VBScript: `Boolean` | `true` to send a detailed non-compliance status message. |
| `startTime` | - Managed: `String`- VBScript: `String` | The date and time when the configuration item assignment was initially offered. |
| `suppressReboot` | - Managed: `Integer`- VBScript: `Integer` | Value indicating whether the client should not reboot the computer, if there is a reboot pending after the configuration item is applied. |
| `targetCollectionID` | - Managed: `String`- VBScript: `String` | The identifier of the collection to which the assignment is targeted. |
| `useGMTTimes` | - Managed: `Boolean`- VBScript: `Boolean` | `true` if the times and schedules are in Universal Coordinated Time (UTC). |
| `baselineID` | - Managed: `Integer` Array- VBScript: `Integer` Array | Array of IDs for the configuration items targeted by the assignment. |

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