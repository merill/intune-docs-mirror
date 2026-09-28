---
layout: Conceptual
title: Remove a Step from an OS Deployment Group - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-remove-a-step-from-an-operating-system-deployment-group
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
description: Deletes a step from an operating system deployment task sequence group by deleting the step from the group's list of task sequence steps.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 43bf820d-86c7-2e80-bee5-f4a499cd5001
document_version_independent_id: de51ff2c-b0aa-75a2-d47f-9e94de3a5239
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-remove-a-step-from-an-operating-system-deployment-group.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-remove-a-step-from-an-operating-system-deployment-group
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-remove-a-step-from-an-operating-system-deployment-group.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 9c507232-4b54-c989-6709-c79b281f9cbc
---

# Remove a Step from an OS Deployment Group - Configuration Manager | Microsoft Learn

In Configuration Manager, you delete a step (an action or a group) from an operating system deployment task sequence group by deleting the step from the group's list of task sequence steps.

### To remove a step from a group

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Get the [SMS_TaskSequence_Group](../reference/osd/sms_tasksequence_group-server-wmi-class) object that you want to add the step to. For more information, see [How to Create an Operating System Deployment Task Sequence Group](how-to-create-an-operating-system-deployment-task-sequence-group).
3. Remove the action from the SMS\_TaskSequence\_Group.Steps array property.

## Example

The following example method removes an action from a task sequence group.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub RemoveActionFromGroup(taskSequenceGroup, actionName)

    Dim i

    If taskSequenceGroup.SystemProperties_("__CLASS")<>"SMS_TaskSequence_Group" Then
        wscript.echo "Not a group"
        return
    End If

        Dim newArray
        Dim actionStep

        newArray = Array(taskSequenceGroup.Steps)
        ReDim newArray(UBound(taskSequenceGroup.Steps))

        i=0
        for each  actionStep in taskSequenceGroup.Steps
            If actionStep.Name = actionName and _
              actionStep.SystemProperties_("__SUPERCLASS") = "SMS_TaskSequence_Action" Then
                 ReDim preserve newArray(UBound(newArray)-1) ' shrink the Array
            else
               wscript.echo actionStep.Name
               Set newArray(i)=actionStep ' copy it
               i=i+1
            End If

         Next

         taskSequenceGroup.Steps=newArray

 End Sub
```

```c
public void RemoveActionFromGroup(
    IResultObject taskSequenceGroup,
    string actionName)
{
    try
    {
        if (taskSequenceGroup["__CLASS"].StringValue != "SMS_TaskSequence_Group")
        {
            throw new System.InvalidOperationException("Not a group");
        }

        List<IResultObject> groupSteps = taskSequenceGroup.GetArrayItems("Steps");
        IResultObject actionFound = null;
        foreach (IResultObject actionStep in groupSteps)
        {
            if (actionStep["Name"].StringValue == actionName && actionStep["__SUPERCLASS"].StringValue == "SMS_TaskSequence_Action")
            {
                actionFound = actionStep;
                break;
            }
        }

        groupSteps.Remove(actionFound);
        taskSequenceGroup.SetArrayItems("Steps", groupSteps);
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to remove action: " + e.Message);
        throw;
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `taskSequenceGroup` | - Managed: IResultObject- VBScript: [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) | The task sequence group containing the action to be deleted. |
| `actionName` | - Managed: `String`- VBScript: `String` | The name of the action to be deleted. This can be obtained from the [SMS_TaskSequenceAction.Name](../reference/osd/sms_tasksequence_action-server-wmi-class) property. |

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