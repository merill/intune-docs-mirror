---
layout: Conceptual
title: Delete an OS Deployment Task Sequence Action - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-delete-an-operating-system-deployment-task-sequence-action
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
description: Learn about how to remove an action from an operating system deployment task sequence to delete the action from the sequence.
locale: en-us
document_id: ab446b4e-15bf-871c-8bb7-3c4785083f47
document_version_independent_id: b4067051-fcf1-3b18-2679-a618692e0039
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-delete-an-operating-system-deployment-task-sequence-action.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-delete-an-operating-system-deployment-task-sequence-action
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-delete-an-operating-system-deployment-task-sequence-action.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 4644543a-a7fc-494d-f120-6eaa535e9eb9
---

# Delete an OS Deployment Task Sequence Action - Configuration Manager | Microsoft Learn

You delete an operating system deployment task sequence action, in Configuration Manager, by removing the action from the task sequence steps.

### To delete a task sequence action

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Obtain a task sequence ([SMS_TaskSequence](../reference/osd/sms_tasksequence-server-wmi-class)) object. For more information, see [How to Create an Operating System Deployment Task Sequence](how-to-create-an-operating-system-deployment-task-sequence).
3. Remove the action from the `SMS_TaskSequence.Steps` array property.

## Example

The following example method deletes an action from the task sequence. The action is identified as an action by checking the Windows Management Instrumentation (WMI) property \_\_SUPERCLASS to ensure it derives from [SMS_TaskSequenceAction](../reference/osd/sms_tasksequence_action-server-wmi-class).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub RemoveAction (connection, taskSequence, actionName)

    Dim i
    Dim newArray
    Dim actionStep

    If taskSequence.SystemProperties_("__CLASS")<>"SMS_TaskSequence" Then
        wscript.echo "Not a task sequence"
        Exit Sub
    End If

    if IsNull(taskSequence.Steps) Then
        Wscript.Echo "No steps"
        Exit Sub
    End If

    ' Create an array to hold copied steps.
    newArray = Array(taskSequence.Steps)
    ReDim newArray(UBound(taskSequence.Steps))

    ' Copy the steps into the array and remove the matching action.
    i=0
    for each  actionStep in taskSequence.Steps
        If actionStep.Name = actionName and _
          actionStep.SystemProperties_("__SUPERCLASS") = "SMS_TaskSequence_Action" Then
             ReDim preserve newArray(UBound(newArray)-1) ' shrink the Array
        else
           Set newArray(i)=actionStep ' copy it
           i=i+1
        End If
     Next

     ' Assign new array back to the task sequence.
     taskSequence.Steps=newArray

End Sub
```

```c
public void RemoveAction(
    IResultObject taskSequence,
    string actionName)
{
    try
    {
        // Get a list of steps.
        List<IResultObject> actionSteps = taskSequence.GetArrayItems("Steps");

        // Find the action to be deleted.
        foreach (IResultObject actionStep in actionSteps)
        {
            if (actionStep["Name"].StringValue == actionName && actionStep["__SUPERCLASS"].StringValue == "SMS_TaskSequence_Action")
            {
                // Delete the action.
                actionSteps.Remove(actionStep);
                break;
            }
        }

        // Update the task sequence.
        taskSequence.SetArrayItems("Steps", actionSteps);
    }
    catch (Exception e)
    {
        Console.WriteLine("Failed to remove action: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `Connection` | - Managed:`WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `taskSequence` | - Managed: `IResultObject`- VBScript: [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) | The task sequence containing the action to be deleted. |
| `actionName` | - Managed: `String`- VBScript: `String` | The name of the action to be deleted. This can be obtained from the `SMS_TaskSequenceAction.Name` property. |

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