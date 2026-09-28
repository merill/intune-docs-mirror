---
layout: Conceptual
title: Add an OS Deployment Task Sequence Action - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-an-operating-system-deployment-task-sequence-action
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
description: Add an OS deployment task sequence action to a task sequence by creating an instance of an SMS_TaskSequence_Action derived class, and then add it to the steps of the task sequence.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c10c68b2-fed2-79f3-dc7f-50b12cdaefda
document_version_independent_id: bb377b27-1b47-64df-2ebb-6646af376ebf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-add-an-operating-system-deployment-task-sequence-action.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-add-an-operating-system-deployment-task-sequence-action
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-add-an-operating-system-deployment-task-sequence-action.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 3f5f984f-7bb2-08ff-cb02-2f6a047b93fc
---

# Add an OS Deployment Task Sequence Action - Configuration Manager | Microsoft Learn

An operating system deployment task sequence action is added to a task sequence, in Configuration Manager, by creating an instance of an [SMS_TaskSequence_Action](../reference/osd/sms_tasksequence_action-server-wmi-class) derived class and then adding it to the steps of the task sequence.

Note

Configuration Manager has a number of built-in actions that you can use. For example the command-line action class is [SMS_TaskSequence_RunCommandLineAction](../reference/osd/sms_tasksequence_runcommandlineaction-server-wmi-class). These classes derive from the [SMS_TaskSequence_Action](../reference/osd/sms_tasksequence_action-server-wmi-class) class.

[SMS_TaskSequenceAction](../reference/osd/sms_tasksequence_action-server-wmi-class) derives from the [SMS_TaskSequence_Step](../reference/osd/sms_tasksequence_step-server-wmi-class) class, which is the base class for both actions and groups. The task sequence stores its steps in an array of [SMS_TaskSequence_Step](../reference/osd/sms_tasksequence_step-server-wmi-class), thus allowing actions and groups to be stored together.

### To add a task sequence action

1. Set up a connection to the SMS Provider. For more information see, [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Create a task sequence ([SMS_TaskSequence](../reference/osd/sms_tasksequence-server-wmi-class)) object. For more information, see [How to Create an Operating System Deployment Task Sequence](how-to-create-an-operating-system-deployment-task-sequence).
3. Create an [SMS_TaskSequenceAction](../reference/osd/sms_tasksequence_action-server-wmi-class) derived class instance, for example, [SMS_TaskSequence_RunCommandLineAction](../reference/osd/sms_tasksequence_runcommandlineaction-server-wmi-class), for the action you want.
4. Populate the action as appropriate.
5. Add the action to the task sequences steps. This is stored the [SMS_TaskSequence](../reference/osd/sms_tasksequence-server-wmi-class)) class Steps property.

## Example

The following example method creates a command-line action and adds it to the supplied task sequence.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub AddTaskSequenceActionCommandLine(connection, taskSequence, name, description)

    Dim steps
    Dim action

    Set action = connection.Get("SMS_TaskSequence_RunCommandLineAction").SpawnInstance_

    action.CommandLine = "cmd /c Echo Hello"
    action.Name=name
    action.Description=description
    action.Enabled=True
    action.ContinueOnError=False

      If IsNull(taskSequence.Steps) Then
        steps = Array(action)
        taskSequence.Steps=steps
    Else
        steps= Array(taskSequence.Steps)
        ReDim steps (UBound (taskSequence.Steps)+1)
        taskSequence.Steps(UBound(steps))=action
    End if

End Sub

```

```c
public IResultObject AddTaskSequenceActionCommandLine(
    WqlConnectionManager connection,
    IResultObject taskSequence,
    string name,
    string description)
{
    try
    {
        // Create the new step.
        IResultObject ro;

        ro = connection.CreateEmbeddedObjectInstance("SMS_TaskSequence_RunCommandLineAction");
        ro["CommandLine"].StringValue = @"cmd /c Echo Hello";

        ro["Name"].StringValue = name;
        ro["Description"].StringValue = description;
        ro["Enabled"].BooleanValue = true;
        ro["ContinueOnError"].BooleanValue = false;

        // Add the step to the task sequence.
        List<IResultObject> array = taskSequence.GetArrayItems("Steps");

        array.Add(ro);

        taskSequence.SetArrayItems("Steps", array);

        return ro;
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to add action: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `taskSequence` | - Managed: `IResultObject`- VBScript: [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) | A valid task sequence. |
| `Name` | - Managed: `String`- VBScript: `String` | A name for the new action. |
| `Description` | - Managed: `String`- VBScript: `String` | A description for the action. |

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