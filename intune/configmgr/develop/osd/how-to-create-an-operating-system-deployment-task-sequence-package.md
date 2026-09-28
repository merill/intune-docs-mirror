---
layout: Conceptual
title: Create an OS Deployment Task Sequence Package - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-package
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
description: creates an instance of the SMS_TaskSequencePackage class. It is advertised to clients who can then run the task sequence.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: b1ec8ab7-8fe5-019a-e1b5-0c95efc1d6a2
document_version_independent_id: d8bf61ea-0c52-a460-a974-36953b4c3450
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-package.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-package
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-create-an-operating-system-deployment-task-sequence-package.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 376d7832-3b96-b2e9-5ecb-d26ee4b3b99f
---

# Create an OS Deployment Task Sequence Package - Configuration Manager | Microsoft Learn

You create an operating system deployment task sequence, in Configuration Manager, by creating an instance of the [SMS_TaskSequencePackage](../reference/osd/sms_tasksequencepackage-server-wmi-class) class. This class derives from the [SMS_Package](../reference/core/servers/configure/sms_package-server-wmi-class) class and holds the task sequence. It is advertised to clients who can then run the task sequence. The task sequence is associated with the task sequence package by using the `SMS_TaskSequencePackage` class [SetSequence](../reference/osd/setsequence-method-in-class-sms_tasksequencepackage) method.

You can organize task sequence packages into categories by assigning a category to them with the [SMS_TaskSequence](../reference/osd/sms_tasksequence-server-wmi-class) class *Category* property.

For more information about creating task sequences, see [How to Create a Task Sequence](how-to-create-an-operating-system-deployment-task-sequence). For more information about task sequence packages, see the [Task Sequencing Object Model](operating-system-deployment-task-sequence-object-model).

You advertise a task sequence package in the same way that you advertise a Configuration Manager package `SMS_Package`. For more information, see [How to Create an Advertisement](../core/servers/configure/how-to-create-an-advertisement).

### To create a task sequence package

1. Set up a connection to the SMS Provider. For more information, see [About the SMS Provider in Configuration Manager](../core/understand/how-to-connect-to-an-sms-provider-by-using-managed-code).
2. Create an instance of `SMS_TaskSequencePackage`.
3. Populate the task sequence package properties.
4. Call the `SMS_TaskSequencePackage` class `SetSequence` method to associate a task sequence (`SMS_TaskSequence`) with the task sequence package.

## Example

The following example method creates a task sequence package (`SMS_TaskSequencePackage`) and associates task sequence (`SMS_TaskSequence`) with it.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub CreateTaskSequencePackage (connection, taskSequence)

    Dim taskSequencePackage
    Dim packageClass
    Dim objInParams
    Dim objOutParams

    ' Create the new package object.
    Set taskSequencePackage = connection.Get("SMS_TaskSequencePackage").SpawnInstance_

    ' Populate the new package properties.
    taskSequencePackage.Name = "New task sequence package"
    taskSequencePackage.Description = "A new task sequence package description"

    ' Get the parameters object.
    Set packageClass = connection.Get("SMS_TaskSequencePackage")

    Set objInParams = packageClass.Methods_("SetSequence"). _
        inParameters.SpawnInstance_()

    ' Add the input parameters.
    objInParams.TaskSequence =  taskSequence
    objInParams.TaskSequencePackage = taskSequencePackage

    ' Add the sequence.
     Set objOutParams = connection.ExecMethod("SMS_TaskSequencePackage", "SetSequence", objInParams)

End Sub

```

```c
public IResultObject CreateTaskSequencePackage(
    WqlConnectionManager connection,
    IResultObject taskSequence)
{
    try
    {
        Dictionary<string, object> inParams = new Dictionary<string, object>();

        // Create the new task sequence package.
        IResultObject taskSequencePackage = connection.CreateInstance("SMS_TaskSequencePackage");

        taskSequencePackage["Name"].StringValue = "New task sequence package";
        taskSequencePackage["Description"].StringValue = "A brand new task sequence package";
        taskSequencePackage["Category"].StringValue = "A custom category";

        // Note. Add other package properties as required.

        // Set up parameters that associate the task sequence with the package.
        inParams.Add("TaskSequence", taskSequence);
        inParams.Add("TaskSequencePackage", taskSequencePackage);

        // Associate the task sequence with the package. Note that a call to Put is not required.
        IResultObject result = connection.ExecuteMethod("SMS_TaskSequencePackage", "SetSequence", inParams);

        // The path to the new package.
        Console.WriteLine(result["SavedTaskSequencePackagePath"].StringValue);

        return taskSequencePackage;
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
| `taskSequence` | - Managed: `IResultObject`- VBScript: [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) | A valid task sequence `SMS_TaskSequence` |

## Compiling the Code

The C# example requires:

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