---
layout: Conceptual
title: Reorder an OS Deployment Task Sequence - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-reorder-an-operating-system-deployment-task-sequence
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
description: In Configuration Manager, you can reorder the steps (an action or a group) in a task sequence or group by rearranging the step sequence in the [Steps] property array.
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 3b15214d-9b27-311e-a354-a2ed2139782a
document_version_independent_id: a442e92a-58a2-345a-72a4-a854d9da9293
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-reorder-an-operating-system-deployment-task-sequence.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-reorder-an-operating-system-deployment-task-sequence
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-reorder-an-operating-system-deployment-task-sequence.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: c8296724-96a5-2f76-1c74-969b0a4b8605
---

# Reorder an OS Deployment Task Sequence - Configuration Manager | Microsoft Learn

In Configuration Manager, you can reorder the steps (an action or a group) in a task sequence or group by rearranging the step sequence in the [Steps](../reference/osd/sms_tasksequence-server-wmi-class) property [SMS_TaskSequence_Step](../reference/osd/sms_tasksequence_step-server-wmi-class) array.

### To reorder a task sequence

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Obtain a valid task sequence ([SMS_TaskSequence](../reference/osd/sms_tasksequence-server-wmi-class)) or task sequence group ([SMS_TaskSequence_Group](../reference/osd/sms_tasksequence_group-server-wmi-class)). For more information, see [How to Read a Task Sequence From a Task Sequence Package](how-to-read-a-task-sequence-from-a-task-sequence-package).
3. Within the `Steps` array property, move the [SMS_TaskSequence_Step](../reference/osd/sms_tasksequence_step-server-wmi-class) to its new location.
4. Update the task sequence or group.

## Example

The following example shows how to move a step up or down within a task sequence or group.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub MoveTaskSequenceStepDown(taskSequence, stepName)
   Dim index
   Dim osdStep
   Dim temp

    index=0

    ' If found, move the step down.
    for each osdStep in taskSequence.Steps
        If osdStep.Name=stepName Then
            If index < Ubound (TaskSequence.Steps) Then
                Set temp=osdStep
                taskSequence.Steps(index)=taskSequence.Steps(index+1)
                taskSequence.Steps(index+1)=temp
                Exit For
           End If
        End If

        index=index+1
    next
End Sub

Sub MoveTaskSequenceStepUp(taskSequence, stepName)
    Dim index
    Dim osdStep
    Dim temp

    index=0

    ' If found, move the step up.
    for Each osdStep In taskSequence.Steps
        If osdStep.Name=stepName Then
            If index >1 Then
                Set temp=osdStep
                taskSequence.Steps(index)=taskSequence.Steps(index-1)
                taskSequence.Steps(index-1)=temp
                Exit For
           End If
        End If

        index=index+1

    next
End Sub
```

```c
public void MoveTaskSequenceStepDown(
    IResultObject taskSequence,
    string taskSequenceStepName)
{
    try
    {
        // Get the task sequence steps.
        List<IResultObject> steps = taskSequence.GetArrayItems("Steps"); // Array of SMS_TaskSequence_Steps.

        int index = 0;

        // Scan through the steps to find the step to move down.
        foreach (IResultObject ro in steps)
        {
            if (ro["Name"].StringValue == taskSequenceStepName)
            {
                // Move the step.
                if (index < steps.Count - 1) // Not at end, so we can flip.
                {
                    steps.Insert(index + 2, steps[index]);
                    steps.Remove(steps[index]);
                    taskSequence.SetArrayItems("Steps", steps);
                    break;
                }
            }

            index++;
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed To enumerate task sequence items: " + e.Message);
        throw;
    }
}

public void MoveTaskSequenceStepUp(
    IResultObject taskSequence,
    string taskSequenceStepName)
{
    try
    {
        // Get the task sequence steps.
        List<IResultObject> steps = taskSequence.GetArrayItems("Steps"); // Array of SMS_TaskSequence_Steps.

        int index = 0;

        foreach (IResultObject ro in steps)
        {
            if (ro["Name"].StringValue == taskSequenceStepName)
            {
                if (index > 0) // Not the first step, so you can move it up.
                {
                    steps.Insert(index + 1, steps[index - 1]);
                    steps.Remove(steps[index - 1]);
                    taskSequence.SetArrayItems("Steps", steps);
                    break;
                }
            }
            index++;
        }
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed To enumerate task sequence items: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `taskSequence` | - Managed: `IResultObject`- VBScript: [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) | A valid task sequence or task sequence group |
| `taskSequenceStepName``stepName` | - Managed: `String`- VBScript: `String` | The name of the task sequence step to move. |

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