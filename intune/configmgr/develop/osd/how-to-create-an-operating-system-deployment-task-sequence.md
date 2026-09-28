---
layout: Conceptual
title: Create an OS Deployment Task Sequence - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence
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
description: You create a Configuration Manager operating system deployment task sequence by creating an instance of the SMS_TaskSequence class.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: b6c3341e-0e0e-0cab-5cd9-6e958b9690f8
document_version_independent_id: 4aab125b-ea98-c26d-2a51-326ac9f71446
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: e63b0c40-4cc5-aeaf-87c8-27253fdeef26
---

# Create an OS Deployment Task Sequence - Configuration Manager | Microsoft Learn

You create a Configuration Manager operating system deployment task sequence by creating an instance of the [SMS_TaskSequence](../reference/osd/sms_tasksequence-server-wmi-class) class.

A task sequence contains one or more steps that are run sequentially on the client computer. For more information, see [Operating System Deployment Task Sequence Object Model](operating-system-deployment-task-sequence-object-model).

The task sequence is then packaged in an [SMS_TaskSequencePackage](../reference/osd/sms_tasksequencepackage-server-wmi-class) and advertised to the client computer.

### To create a task sequence

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Create a task sequence `SMS_TaskSequence` object.
3. Add actions and, as required, add groups to the action. For more information, see [How to Add an Operating System Deployment Task Sequence Action](how-to-add-an-operating-system-deployment-task-sequence-action).
4. Associate the task sequence with a task sequence package. For more information, see [How to Create an Operating System Deployment Task Sequence Package](how-to-create-an-operating-system-deployment-task-sequence-package).
5. Advertise the task sequence to the client computer. For more information, see [How to Create an Advertisement](../core/servers/configure/how-to-create-an-advertisement).

## Example

The following example method creates a task sequence that installs a software program. The example also creates a task sequence package by calling the example that is defined in [How to Create an Operating System Deployment Task Sequence Package](how-to-create-an-operating-system-deployment-task-sequence-package).

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub CreateInstallSoftwareTaskSequence(connection,name, description, packageID, programName)

    ' Create the task sequence.
    set taskSequence = connection.Get("SMS_TaskSequence").SpawnInstance_

    ' Create the action.
    set action = connection.Get("SMS_TaskSequence_InstallSoftwareAction").SpawnInstance_

    action.ProgramName=programName
    action.PackageID=packageID
    action.Name=name
    action.Enabled=true
    action.ContinueOnError=false

    ' Create an array to hold the action.
    actionSteps= array(action)
    ' Add the array to the task sequence.
    taskSequence.Steps=actionSteps

    wscript.echo taskSequence.Steps(0).Name
    call CreateTaskSequencePackage (connection, taskSequence)

 End Sub
```

```c
public void CreateInstallSoftwareTaskSequence(
    WqlConnectionManager connection,
    string name,
    string packageId,
    string programName)
{
    try
    {
        // Create the task sequence.
        IResultObject taskSequence = connection.CreateInstance("SMS_TaskSequence");

        IResultObject ro = connection.CreateEmbeddedObjectInstance("SMS_TaskSequence_InstallSoftwareAction");
        ro["ProgramName"].StringValue = programName;
        ro["packageId"].StringValue = packageId;
        ro["Name"].StringValue = name;
        ro["Enabled"].BooleanValue = true;
        ro["ContinueOnError"].BooleanValue = false;

        // Add the step to the task sequence.
        List<IResultObject> array = taskSequence.GetArrayItems("Steps");

        array.Add(ro);

        taskSequence.SetArrayItems("Steps", array);

        // Create the task sequence package.
        this.CreateTaskSequencePackage(connection, taskSequence);
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
| `Connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |
| `name` | - Managed: `String`- VBScript: `String` | The task sequence step name. |
| `description` | - VBScript: `String` | The task sequence step description. |
| `packageID` | - Managed: `String`- VBScript: `String` | The package identifier containing the software to be installed. Obtained from `SMS_Package.PackageID`. |
| `programName` | - Managed: `String`- VBScript: `String` | The name of the program to be installed. Obtained from `SMS_Program.ProgramName`. |

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