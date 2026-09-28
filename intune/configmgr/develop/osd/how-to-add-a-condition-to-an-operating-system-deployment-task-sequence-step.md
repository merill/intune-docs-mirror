---
layout: Conceptual
title: Add a Condition to an OS Deployment Task Sequence Step - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-add-a-condition-to-an-operating-system-deployment-task-sequence-step
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
description: How to Add a Condition to an Operating System Deployment Task Sequence Step
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 0743a427-1a7e-453d-ff54-e6b66a405fc1
document_version_independent_id: 19bd7ba3-65f5-40aa-ae74-1d090f67d912
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-add-a-condition-to-an-operating-system-deployment-task-sequence-step.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-add-a-condition-to-an-operating-system-deployment-task-sequence-step
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-add-a-condition-to-an-operating-system-deployment-task-sequence-step.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
platformId: a755296a-fe80-4b34-f05a-c550bb0288ee
---

# Add a Condition to an OS Deployment Task Sequence Step - Configuration Manager | Microsoft Learn

Conditions can be added to an operating system deployment step (action and group), in Configuration Manager, by creating a [SMS_TaskSequence_Condition](../reference/osd/sms_tasksequence_condition-server-wmi-class) class instance and then associating it with the step. If the condition operands are all met, then the step is processed; otherwise it is not. The condition can have one or more operands that are instances of SMS\_TaskSequence\_Condition derived classes. You specify operators for the operands with instances of [SMS_TaskSequence_ConditionOperator](../reference/osd/sms_tasksequence_conditionoperator-server-wmi-class).

### To add a condition to a step

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Obtain a task sequence step object. This can be an [SMS_TaskSequence_Group](../reference/osd/sms_tasksequence_group-server-wmi-class) object for a group, or a [SMS_TaskSequenceAction](../reference/osd/sms_tasksequence_action-server-wmi-class) derived class object for an action, for more information, see [How to Add an Operating System Deployment Task Sequence Action](how-to-add-an-operating-system-deployment-task-sequence-action).
3. Create a new condition by creating an instance of `SMS_TaskSequence_Condition`.
4. Create an expression for the condition by creating an instance of an [SMS_TaskSequence_ConditionExpression](../reference/osd/sms_tasksequence_conditionexpression-server-wmi-class) derived class. For example, [SMS_TaskSequence_RegistryConditionExpression](../reference/osd/sms_tasksequence_registryconditionexpression-server-wmi-class).
5. Populate the expression properties.
6. Add the expression to the condition *Operands* property.
7. Add the condition to the task sequence step class *Condition* property.

## Example

The following example method adds a condition to a supplied step that determines if the HKEY\_LOCAL\_MACHINE\MICROSOFT registry key exists. The SMS\_TaskSequenc\_RegistryCondition Expression is used to specify the condition.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub AddRegistryCondition (connection, taskSequenceStep)

    Dim condition
    Dim registryExpression
    Dim operands

    ' Get or create the condition.
    if IsNull ( taskSequenceStep.Condition) Then
       Set condition = connection.Get("SMS_TaskSequence_Condition").SpawnInstance_
    Else
        Set condition = taskSequenceStep.Condition
    End If

    ' Populate the condition.
    Set registryExpression=connection.Get("SMS_TaskSequence_RegistryConditionExpression").SpawnInstance_
    registryExpression.KeyPath="HKEY_LOCAL_MACHINE\MICROSOFT"
    registryExpression.Operator="exists"
    registryExpression.Type="REG_SZ"
    registryExpression.Data=Null

    ' Add the condition.
    operands=Array(registryExpression)
    condition.Operands=operands
    taskSequenceStep.Condition=condition

End Sub
```

```c
public void AddRegistryCondition(
    WqlConnectionManager connection,
    IResultObject taskSequenceStep)
{
    try
    {
        IResultObject condition;

        if (taskSequenceStep["Condition"].ObjectValue == null)
        {
            // Create a new condition.
            condition = connection.CreateEmbeddedObjectInstance("SMS_TaskSequence_Condition");
        }
        else
        {   // Get the existing condition.
            condition = taskSequenceStep.GetSingleItem("Condition");
        }

        // Create and populate the expression.
        IResultObject registryExpression = connection.CreateEmbeddedObjectInstance("SMS_TaskSequence_RegistryConditionExpression");

        registryExpression["KeyPath"].StringValue = @"HKEY_LOCAL_MACHINE\MICROSOFT";
        registryExpression["Operator"].StringValue = "exists";
        registryExpression["Type"].StringValue = "REG_SZ";
        registryExpression["Data"].StringValue = null;

        // Get the operands and add the expression.
        List<IResultObject> operands = condition.GetArrayItems("Operands");
        operands.Add(registryExpression);

        // Add the expresssion to the list of operands.
        condition.SetArrayItems("Operands", operands);

        // Add the condition to the sequence.
        taskSequenceStep.SetSingleItem("Condition", condition);
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
| `taskSequenceStep` | - Managed: `IResultObject`- VBScript: [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) | A valid task sequence step ([SMS_TaskSequenceStep](../reference/osd/sms_tasksequence_step-server-wmi-class)). |

## Compiling the Code

The C# example has the following compilation requirements:

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