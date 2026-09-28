---
layout: Conceptual
title: Configure and Deploy Updates - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-configure-and-deploy-updates
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
description: Learn how to use the Configuration Manager SDK to configure and deploy software updates
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 78c0ddfb-4bd9-01ef-795c-4b8c4721ea66
document_version_independent_id: 68e022a2-1a7f-9c53-052e-bd229d3340e1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/how-to-configure-and-deploy-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/how-to-configure-and-deploy-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/how-to-configure-and-deploy-updates.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2bb407c5-c939-4f7a-9174-27da19279675
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6eda2a8b-e231-4335-b766-c055ea6025a6
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 7449db65-d4aa-1c8c-aa50-b385a76740ff
---

# Configure and Deploy Updates - Configuration Manager | Microsoft Learn

You create a software updates deployment, in Configuration Manager, by creating an instance of the [SMS_UpdatesAssignment Server WMI Class](../reference/sum/sms_updatesassignment-server-wmi-class) and populating the properties.

### To configure and deploy updates

1. Set up a connection to the SMS Provider.
2. Create the new deployment object by using the [SMS_UpdatesAssignment](../reference/sum/sms_updatesassignment-server-wmi-class) class.
3. Populate the new deployment properties.
4. Save the new deployment and properties.

## Example

The following example method shows how to create a software updates deployment by using the [SMS_UpdatesAssignment](../reference/sum/sms_updatesassignment-server-wmi-class) class. Note that the parameters of the example method reflect certain properties of `SMS_UpdatesAssignment`.

Important

The methods below require an array of the assigned configuration items (CI\_IDs). The update content for these CI\_IDs must have already been downloaded and added to an updates deployment package.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

Sub ConfigureAndDeploySUMUpdates(connection,                             _
                                  newApplyToSubTargets,                  _
                                  newArrayAssignedCIs,                   _
                                  newAssignmentAction,                   _
                                  newAssignmentDescription,              _
                                  newAssignmentName,                     _
                                  newDesiredConfigType,                  _
                                  newDPLocality,                         _
                                  newLocaleID,                           _
                                  newLogComplianceToWinEvent,            _
                                  newNotifyUser,                         _
                                  newRaiseMomAlertsOnFailure,            _
                                  newSendDetailedNonComplianceStatus,    _
                                  newStartTime,                          _
                                  newSuppressReboot,                     _
                                  newTargetCollectionID,                 _
                                  newUseGMTTimes)

  ' Create the new deployment object.
  Set newSUMUpdatesAssignment = connection.Get("SMS_UpdatesAssignment").SpawnInstance_

  ' Populate the deployment properties.
  newSUMUpdatesAssignment.ApplyToSubTargets = newApplyToSubTargets
  newSUMUpdatesAssignment.AssignedCIs = newArrayAssignedCIs
  newSUMUpdatesAssignment.AssignmentAction = newAssignmentAction
  newSUMUpdatesAssignment.AssignmentDescription = newAssignmentDescription
  newSUMUpdatesAssignment.AssignmentName = newAssignmentName
  newSUMUpdatesAssignment.DesiredConfigType = newDesiredConfigType
  newSUMUpdatesAssignment.DPLocality = newDPLocality
  newSUMUpdatesAssignment.LocaleID = newLocaleID
  newSUMUpdatesAssignment.LogComplianceToWinEvent = newLogComplianceToWinEvent
  newSUMUpdatesAssignment.NotifyUser = newNotifyUser
  newSUMUpdatesAssignment.RaiseMomAlertsOnFailure = newRaiseMomAlertsOnFailure
  newSUMUpdatesAssignment.SendDetailedNonComplianceStatus = newSendDetailedNonComplianceStatus
  newSUMUpdatesAssignment.StartTime = newStartTime
  newSUMUpdatesAssignment.SuppressReboot = newSuppressReboot
  newSUMUpdatesAssignment.TargetCollectionID = newTargetCollectionID
  newSUMUpdatesAssignment.UseGMTTimes = newUseGMTTimes

  ' Save the new deployment and properties.
  newSUMUpdatesAssignment.Put_

  ' Output the new deployment name.
  Wscript.Echo "Created new deployment " & newSUMUpdatesAssignment.AssignmentName

End Sub

```

```c

public void ConfigureAndDeploySUMUpdates(WqlConnectionManager connection,
                                        bool newApplyToSubTargets,
                                        int[] newArrayAssignedCIs,
                                        int newAssignmentAction,
                                        string newAssignmentDescription,
                                        string newAssignmentName,
                                        int newDesiredConfigType,
                                        int newDPLocality,
                                        int newLocaleID,
                                        bool newLogComplianceToWinEvent,
                                        bool newNotifyUser,
                                        bool newRaiseMomAlertsOnFailure,
                                        bool newSendDetailedNonComplianceStatus,
                                        string newStartTime,
                                        int newSuppressReboot,
                                        string newTargetCollectionID,
                                        bool newUseGMTTimes)
{
    try
    {

        // Create the deployment object.
        IResultObject newSUMUpdatesAssignment = connection.CreateInstance("SMS_UpdatesAssignment");

        // Populate new deployment properties.
        // Note: newTemplateName must be unique.

        newSUMUpdatesAssignment["ApplyToSubTargets"].BooleanValue = newApplyToSubTargets;
        newSUMUpdatesAssignment["AssignedCIs"].IntegerArrayValue = newArrayAssignedCIs;
        newSUMUpdatesAssignment["AssignmentAction"].IntegerValue = newAssignmentAction;
        newSUMUpdatesAssignment["AssignmentDescription"].StringValue = newAssignmentDescription;
        newSUMUpdatesAssignment["AssignmentName"].StringValue = newAssignmentName;
        newSUMUpdatesAssignment["DesiredConfigType"].IntegerValue = newDesiredConfigType;
        newSUMUpdatesAssignment["DPLocality"].IntegerValue = newDPLocality;
        newSUMUpdatesAssignment["LocaleID"].IntegerValue = newLocaleID;
        newSUMUpdatesAssignment["LogComplianceToWinEvent"].BooleanValue = newLogComplianceToWinEvent;
        newSUMUpdatesAssignment["NotifyUser"].BooleanValue = newNotifyUser;
        newSUMUpdatesAssignment["RaiseMomAlertsOnFailure"].BooleanValue = newRaiseMomAlertsOnFailure;
        newSUMUpdatesAssignment["SendDetailedNonComplianceStatus"].BooleanValue = newSendDetailedNonComplianceStatus;
        newSUMUpdatesAssignment["StartTime"].DateTimeValue = newStartTime;
        newSUMUpdatesAssignment["SuppressReboot"].IntegerValue = newSuppressReboot;
        newSUMUpdatesAssignment["TargetCollectionID"].StringValue = newTargetCollectionID;
        newSUMUpdatesAssignment["UseGMTTimes"].BooleanValue = newUseGMTTimes;

        // Save new deployment and new deployment properties.
        newSUMUpdatesAssignment.Put();

        // Output the new deployment name.
        Console.WriteLine("Created deployment: " + newAssignmentName);
    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed to create newSUMUpdatesAssignment. Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `newApplyToSubTargets` | - Managed: `Boolean`- VBScript: `Boolean` | Determines whether the deployment applies to subtargets. - True- False |
| `newArrayAssignedCIs` | - Managed: `Integer` array- VBScript: `Integer` array | An array of the assigned configuration items (CI\_IDs). The update content for these CI\_IDs must have already been downloaded and added to an updates deployment package. |
| `newAssignmentAction` | - Managed: `Integer`- VBScript: `Integer` | The new assignment action. |
| `newAssignmentDescription` | - Managed: `String`- VBScript: `String` | The new assignment description. |
| `newAssignmentName` | - Managed: `String`- VBScript: `String` | The new assignment name. |
| `newDesiredConfigType` | - Managed: `Integer`- VBScript: `Integer` | The new desired configuration type. |
| `newDPLocality` | - Managed: `Integer`- VBScript: `Integer` | The new distribution point locality. |
| `newLocaleID` | - Managed: `Integer`- VBScript: `Integer` | The new locale ID. |
| `newLogComplianceToWinEvent` | - Managed: `Boolean`- VBScript: `Boolean` | Determines whether compliance is logged to the Windows Event log. - True- False |
| `newNotifyUser` | - Managed: `Boolean`- VBScript: `Boolean` | Identifies whether users are notified. - True- False |
| `newRaiseMomAlertsOnFailure` | - Managed: `Boolean`- VBScript: `Boolean` | Identifies whether MOM alerts are raised on failure. - True- False |
| `newSendDetailedNonComplianceStatus` | - Managed: `Boolean`- VBScript: `Boolean` | Identifies whether detailed noncompliance status is sent. - True- False |
| `newStartTime` | - Managed: `String`- VBScript: `String` | The new start time. |
| `newSuppressReboot` | - Managed: `Integer`- VBScript: `Integer` | Identifies whether reboot is suppressed. |
| `newTargetCollectionID` | - Managed: `String`- VBScript: `String` | The new target collection IDs. |
| `newUseGMTTimes` | - Managed: `Boolean`- VBScript: `Boolean` | Identifies whether to use Coordinated Universal Time (UTC). - True- False |

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