---
layout: Conceptual
title: Create an OS Deployment Task Sequence Group - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-group
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
description: An operating system deployment task sequence group can be added to a task sequence by creating an instance of the SMS_TaskSequence_Group class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 1153846e-d214-aae1-d79b-97dab61d9d7a
document_version_independent_id: c3e91964-6253-1b42-9ccf-8820013b3cd9
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-group.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-group
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-group.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 8bfdb818-8c43-80a4-7616-97c36783d21c
---

# Create an OS Deployment Task Sequence Group - Configuration Manager | Microsoft Learn

An operating system deployment task sequence group, in Configuration Manager, can be added to a task sequence by creating an instance of the [SMS_TaskSequence_Group](../reference/osd/sms_tasksequence_group-server-wmi-class) class. The group is then added to the list of steps of the task sequence. The list of steps is an array of the [SMS_TaskSequence_Step](../reference/osd/sms_tasksequence_step-server-wmi-class) derived classes. The array is stored in the task sequence, [SMS_TaskSequence](../reference/osd/sms_tasksequence-server-wmi-class), `Steps` property.

### To create a task sequence group

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Obtain a valid task sequence ([SMS_TaskSequence)](../reference/osd/sms_tasksequence-server-wmi-class) object. For more information, see [How to Create an Operating System Deployment Task Sequence](how-to-create-an-operating-system-deployment-task-sequence).
3. Create an instance of the `SMS_TaskSequence_Group` class.
4. Populate the group with the appropriate properties.
5. Update the task sequence `Steps` property with the new group.

## Example

The following example method adds a new group to the supplied task sequence. Because the group is added to the end of the task sequence `Steps` array, you might want to reorder its position. For more information, see [How to Reorder an Operating System Deployment Task Sequence](how-to-reorder-an-operating-system-deployment-task-sequence).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub AddTaskSequenceGroup(connection, taskSequence, name, description)

    Dim group

    ' Create and populate the group.
    Set group = connection.Get("SMS_TaskSequence_Group").SpawnInstance_
    group.Name=name
    group.Description=description
    group.Enabled=True
    group.ContinueOnError=False

    ' Resize the task sequence steps array to hold the new group.
    ReDim steps (UBound (taskSequence.Steps)+1)

    ' Add the group.
    taskSequence.Steps(UBound(steps))=group

End Sub
```

```c
public IResultObject AddTaskSequenceGroup(
    WqlConnectionManager connection,
    IResultObject taskSequence,
    string name,
    string description)
{
    try
    {
        // Create the new group.
        IResultObject ro = connection.CreateEmbeddedObjectInstance("SMS_TaskSequence_Group");

        ro["Name"].StringValue = name;
        ro["Description"].StringValue = description;
        ro["Enabled"].BooleanValue = true;
        ro["ContinueOnError"].BooleanValue = false;

        // Add the group to the task sequence.
        List<IResultObject> array = taskSequence.GetArrayItems("Steps");
        array.Add(ro);

        // Add the new group to the end of the current steps.
        taskSequence.SetArrayItems("Steps", array);

        return ro;
    }
    catch (SmsException e)
    {
        Console.WriteLine("Failed to create Task Sequence: " + e.Message);
        throw;
    }
}
```

This example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `taskSequence` | - Managed: `IResultObject`- VBScript: [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) | A valid task sequence (`SMS_TaskSequence`). The group is added to this task sequence. |
| `Name` | - Managed: `String`- VBScript: `String` | A name for the new group. |
| `Description` | - Managed: `String`- VBScript: `String` | A description for the new group. |

| Parameter | Description |
| --- | --- |
| `connection` | A `WqlConnectionManager` object that is a valid connection to the SMS Provider. |
| `taskSequence` | An `IResultObject` that is a valid task sequence (`SMS_TaskSequence`). The group is added to this task sequence. |
| `name` | A string name for the new group. |
| `description` | A string description for the new group. |

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).