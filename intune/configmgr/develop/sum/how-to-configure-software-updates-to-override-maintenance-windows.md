---
layout: Conceptual
title: Configure Software Updates to Override Maintenance Windows - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/how-to-configure-software-updates-to-override-maintenance-windows
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
description: Learn about how to update the OverrideServiceWindows property of deployment to configure software updates to override maintenance windows.
locale: en-us
document_id: ea80c5b0-86f4-a1ae-a85a-f9a12f03d440
document_version_independent_id: 4cab5f49-a64f-be76-cc95-d5917a1cfd9e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/how-to-configure-software-updates-to-override-maintenance-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/how-to-configure-software-updates-to-override-maintenance-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/how-to-configure-software-updates-to-override-maintenance-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: e8947ae3-d375-7e6e-9614-45a3dcc68d8d
---

# Configure Software Updates to Override Maintenance Windows - Configuration Manager | Microsoft Learn

You configure software updates to override maintenance windows, in Configuration Manager, by updating the `OverrideServiceWindows` property of an assignment (deployment).

### To configure software updates to override maintenance windows

1. Set up a connection to the SMS Provider.
2. Load the specific assignment (deployment) to modify using the `SMS_UpdatesAssignment` class.
3. Set the `OverrideServiceWindows` value to `true`.
4. Save the assignment (deployment) and properties.

## Example

The following example method shows how to configure software updates to override maintenance windows by using the `SMS_UpdatesAssignment` class and class properties.

Note

This task only applies to mandatory deployments.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs

Sub ConfigureSoftwareUpdatestoOverrideMaintenanceWindow(connection, existingAssignmentID)

    ' Get the specific SMS_UpdatesAssignment instance to modify.
    Set assignmentToModify = connection.Get("SMS_UpdatesAssignment.AssignmentID=" & existingAssignmentID & "")

    ' Set the new property value.
    assignmentToModify.OverrideServiceWindows = true

    ' Save the assignment.
    assignmentToModify.Put_

    ' Output the new property values.
    Wscript.Echo " "
    Wscript.Echo "Set assignment " & existingAssignmentID & " to override service windows."

End Sub

```

```c

public void ConfigureSoftwareUpdatestoOverrideMaintenanceWindow(WqlConnectionManager connection, int existingAssignmentID)
{
    try
    {
        // Get the specific SMS_UpdatesAssignment instance to change.
        IResultObject updatesAssignmentToChange = connection.GetInstance(@"SMS_UpdatesAssignment.AssignmentID=" + existingAssignmentID);

        // Set OverrideServiceWindows property.
        updatesAssignmentToChange["OverrideServiceWindows"].BooleanValue = true;

        // Save property changes.
        updatesAssignmentToChange.Put();

        // Output success message.
        Console.WriteLine("Set assignment " + existingAssignmentID + " to override service windows.");
    }

    catch (SmsException ex)
    {
        Console.WriteLine("Failed to .... Error: " + ex.Message);
        throw;
    }
}

```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `existingAssignmentID` | - Managed: `Integer`- VBScript: `Integer` | An existing Assignment ID to modify. |

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