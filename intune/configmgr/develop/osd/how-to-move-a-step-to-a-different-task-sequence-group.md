---
layout: Conceptual
title: Move a Step to a Different OS Deployment Task Sequence Group - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-move-a-step-to-a-different-task-sequence-group
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
description: Move a step from one operating system deployment task sequence group to another by adding the step to the target group.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 05b8fb1d-6620-3357-a1da-5bb06adfed6d
document_version_independent_id: 97487d73-c931-4f7c-9717-87951b63ab74
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-move-a-step-to-a-different-task-sequence-group.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-move-a-step-to-a-different-task-sequence-group
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-move-a-step-to-a-different-task-sequence-group.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: fe07564d-18b6-5143-0031-62f858244fc1
---

# Move a Step to a Different OS Deployment Task Sequence Group - Configuration Manager | Microsoft Learn

You move a step (an action or a group) from one operating system deployment task sequence group to another, in Configuration Manager, by adding the step to the target group and then by deleting the step from the source group.

### To move a step from one group to another

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get the source and target [SMS_TaskSequenceGroup](../reference/osd/sms_tasksequence_group-server-wmi-class) objects. Copy a step that you want to add the step to. For more information, see [How to Create an Operating System Deployment Task Sequence Group](how-to-create-an-operating-system-deployment-task-sequence-group).
3. Add the step to the target group. For more information, see [How to Add a Step to an Operating System Deployment Group](how-to-add-a-step-to-an-operating-system-deployment-group).
4. Reorder the step within the target group array property as necessary. For more information, see [How to Re-order an Operating System Deployment Task Sequence](how-to-reorder-an-operating-system-deployment-task-sequence)
5. Delete the step from the source group. For more information, see [How to Remove a Step From an Operating System Deployment Group](how-to-remove-a-step-from-an-operating-system-deployment-group).

## Example

The following example method moves a step from one task sequence group to another.

You will need the code snippet in [How to Remove a Step From an Operating System Deployment Group](how-to-remove-a-step-from-an-operating-system-deployment-group) to run this example.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub MoveActionToGroup( taskSequenceStep, sourceGroup,targetGroup)

        Dim steps
        Dim groupSteps

        Steps = Array(targetGroup.Steps)

        If IsNull(targetGroup.Steps) Then
            groupSteps = Array(taskSequenceStep)
            targetGroup.Steps = groupSteps
        Else
            ReDim steps (UBound (targetGroup.Steps)+1)
            targetGroup.Steps(UBound(steps))=taskSequenceStep
        End If

        Call RemoveActionFromGroup(sourceGroup,taskSequenceStep.Name)

End Sub
```

```c
public void MoveActionToGroup(
    IResultObject taskSequenceStep,
    IResultObject sourceGroup,
    IResultObject targetGroup)
{
    try
    {
        // Add the step to the target group.
        // Note. You can use MoveTaskSequenceStepUp and MoveTaskSequenceStepDown
        // to place the step in the target group.

        List<IResultObject> groupSteps = targetGroup.GetArrayItems("Steps");
        groupSteps.Add(taskSequenceStep);
        targetGroup.SetArrayItems("Steps", groupSteps);

        // Remove action from the source group.
        this.RemoveActionFromGroup(sourceGroup, taskSequenceStep["Name"].StringValue);
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
| `taskSequenceStep` | - Managed: `IResultObject`- VBScript: [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) | A valid task sequence step (Group or action) ([SMS_TaskSequence_Step](../reference/osd/sms_tasksequence_step-server-wmi-class)). |
| `sourceGroup` | - Managed: `IResultObject`- VBScript: `SWbemObject` | The group `SMS_TaskSequenceGroup` the step is copied from. |
| `targetGroup` | - Managed: `IResultObject`- VBScript: `SWbemObject` | The group `SMS_TaskSequenceGroup` the step is copied to. |

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