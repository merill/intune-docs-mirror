---
layout: Conceptual
title: Enumerate the Steps in an OS Deployment Task Sequence - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-enumerate-the-steps-in-an-operating-system-deployment-task-sequence
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
description: You enumerate an operating system deployment task sequence, in Configuration Manager, by using a recursive method to scan through the task sequence steps and groups.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 37421b4b-2090-7182-52fb-d15e0e41e9da
document_version_independent_id: b12f11c0-b152-b66e-e144-885435d7b2f0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-enumerate-the-steps-in-an-operating-system-deployment-task-sequence.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-enumerate-the-steps-in-an-operating-system-deployment-task-sequence
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-enumerate-the-steps-in-an-operating-system-deployment-task-sequence.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 4a7a9463-4621-b9c9-68cf-2b5c76c02066
---

# Enumerate the Steps in an OS Deployment Task Sequence - Configuration Manager | Microsoft Learn

You enumerate an operating system deployment task sequence, in Configuration Manager, by using a recursive method to scan through the task sequence steps and groups.

### To enumerate the steps in a task sequence

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Obtain a valid task sequence [SMS_TaskSequence](../reference/osd/sms_tasksequence-server-wmi-class) object. For more information, see [How to Create an Operating System Deployment Task Sequence](how-to-create-an-operating-system-deployment-task-sequence)
3. Enumerate through the steps to display any action ([SMS_TaskSequence_Action](../reference/osd/sms_tasksequence_action-server-wmi-class)) names. Use recursion to access any groups ([SMS_TaskSequence_Group](../reference/osd/sms_tasksequence_group-server-wmi-class)) that are found and display their actions.

## Example

The following example displays the actions and groups within a task sequence.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub RecurseTaskSequenceSteps(taskSequence, indent)

    Dim osdStep
    Dim i

    ' Indent each new group.
    for each osdStep in taskSequence.Steps

        for i=0 to indent
            WScript.StdOut.Write " "
        next

        If osdStep.SystemProperties_("__CLASS")="SMS_TaskSequence_Group" Then
            wscript.StdOut.Write "Group: "
        End If

        WScript.Echo osdStep.Name

        ' Recurse into each group found.
        If osdStep.SystemProperties_("__CLASS")="SMS_TaskSequence_Group" Then
            If IsNull(osdStep.Steps) Then
                Wscript.Echo "No steps"
            Else
                Call RecurseTaskSequenceSteps (osdStep, indent+3)
            End If
        End If
     Next
End Sub
```

```c
public void RecurseTaskSequenceSteps(
    IResultObject taskSequence,
    int indent)
{
    try
    {
        // The array of SMS_TaskSequence_Steps.
        List<IResultObject> steps = taskSequence.GetArrayItems("Steps");

        foreach (IResultObject ro in steps)
        {
            for (int i = 0; i < indent; i++)
            {
                Console.Write(" ");
            }

            if (ro["__CLASS"].StringValue == "SMS_TaskSequence_Group")
            {
                Console.Write("Group: ");
            }

            Console.WriteLine(ro["Name"].StringValue);

            // Child groups that are found. Use recursion to view them.
            if (ro["__CLASS"].StringValue == "SMS_TaskSequence_Group")
            {
                this.RecurseTaskSequenceSteps(ro, indent + 3);
            }
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
| `taskSequence` | - Managed: `IResultObject`- VBScript: [SWbemObject](/en-us/windows/win32/wmisdk/swbemservices) | A valid task sequence (`SMS_TaskSequence`). The group is added to this task sequence. |
| `indent` | - Managed: `Integer`- VBScript: `Integer` | Indent is used to space console output for child groups. |

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