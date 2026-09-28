---
layout: Conceptual
title: Add a Step to an OS Deployment Group - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-step-to-an-operating-system-deployment-group
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
description: Add the step to the SMS_TaskSequenceGroup.Steps array property in Configuration Manager.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 7dbd8e87-8b70-c773-340c-14a16ab0301c
document_version_independent_id: 00effe36-04a4-484b-e3a9-e184763b425a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-add-a-step-to-an-operating-system-deployment-group.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-add-a-step-to-an-operating-system-deployment-group
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-add-a-step-to-an-operating-system-deployment-group.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: b9711f9c-f7bd-d80b-0344-3b914f64bf9f
---

# Add a Step to an OS Deployment Group - Configuration Manager | Microsoft Learn

You add a step (an action or a group) to an operating system deployment task sequence group, in Configuration Manager, by adding the step to the `SMS_TaskSequenceGroup.Steps` array property.

### To add a step to a task sequence group

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get the [SMS_TaskSequenceGroup](../reference/osd/sms_tasksequence_group-server-wmi-class) object that you want to add the step to. For more information, see [How to Create an Operating System Deployment Task Sequence Group](how-to-create-an-operating-system-deployment-task-sequence-group).
3. Create the task sequence step. For an example of creating an action step, see [How to Add an Operating System Deployment Task Sequence Action](how-to-add-an-operating-system-deployment-task-sequence-action).
4. Add the step to the `SMS_TaskSequenceGroup.Steps` array property.
5. Reorder the step within the array property as necessary. For more information, see [How to Re-order an Operating System Deployment Task Sequence](how-to-reorder-an-operating-system-deployment-task-sequence)

## Example

The following example method adds a command-line action to a task sequence group.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub AddStepToGroup(taskSequenceStep, group)

    Dim steps

    ' If needed, create a new steps array.
    If IsNull(group.Steps) Then
        steps = Array(taskSequenceStep)
        group.Steps=steps
    Else
        ' Resize the existing steps and add step.
        steps= Array(group.Steps)
        ReDim steps (UBound (group.Steps)+1)
        group.Steps(UBound(steps))=taskSequenceStep
    End if

End Sub
```

```c
public void AddStepToGroup(
    WqlConnectionManager connection,
    IResultObject taskSequence,
    string groupName)
{
    try
    {
        // Get the group.
        List<IResultObject> steps = taskSequence.GetArrayItems("Steps"); // Array of SMS_TaskSequence_Steps.

        foreach (IResultObject ro in steps)
        {
            if (ro["Name"].StringValue == groupName && ro["__CLASS"].StringValue == "SMS_TaskSequence_Group")
            {
                IResultObject action = connection.CreateEmbeddedObjectInstance("SMS_TaskSequence_RunCommandLineAction");
                action["CommandLine"].StringValue = @"C:\donowtingroup.bat";
                action["Name"].StringValue = "Action in group " + groupName;
                action["Description"].StringValue = "Action in a group";
                action["Enabled"].BooleanValue = true;
                action["ContinueOnError"].BooleanValue = false;

                // Add the step to the task sequence.
                List<IResultObject> array = ro.GetArrayItems("Steps");

                array.Add(action);

                ro.SetArrayItems("Steps", array);
                taskSequence.SetArrayItems("Steps", steps);
                break;
            }
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to create Task Sequence: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `taskSequence``taskSequenceStep` | - Managed: `IResultObject`- VBScript: [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) | - A valid task sequence ([SMS_TaskSequence](../reference/osd/sms_tasksequence-server-wmi-class)) that contains the group. |
| `groupName``group` | - Managed: `String`- VBScript: `String` | The name of the group that the command-line action is added to. This is obtained from the `SMS_TaskSequenceGroup.Name` property. |

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