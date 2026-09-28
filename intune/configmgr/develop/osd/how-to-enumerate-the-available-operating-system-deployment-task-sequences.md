---
layout: Conceptual
title: Enumerate the Available OS Deployment Task Sequences - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-enumerate-the-available-operating-system-deployment-task-sequences
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
description: You enumerate the available operating system deployment task sequences, in Configuration Manager, by querying the available task sequence packages.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 34ae8235-913d-5f7a-8408-f4d25f1d8dc6
document_version_independent_id: 918656e5-1866-bc6a-940f-b35e325a8a53
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-enumerate-the-available-operating-system-deployment-task-sequences.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-enumerate-the-available-operating-system-deployment-task-sequences
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-enumerate-the-available-operating-system-deployment-task-sequences.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 4c0f062a-0b8e-1f18-137d-58c73b762510
---

# Enumerate the Available OS Deployment Task Sequences - Configuration Manager | Microsoft Learn

You enumerate the available operating system deployment task sequences, in Configuration Manager, by querying the available task sequence packages. Configuration Manager does not maintain instances of the [SMS_TaskSequence](../reference/osd/sms_tasksequence-server-wmi-class) class for task sequences, but there is one instance of the [SMS_TaskSequencePackage](../reference/osd/sms_tasksequencepackage-server-wmi-class) class for each task sequence.

Note

Several properties are lazy and you must get the object instance before you can access the properties.

You can also access individual task sequence packages by using the [PackageID](../reference/core/servers/configure/sms_package-server-wmi-class) key property. For an example, see [How to Read a Configuration Manager Object by Using Managed Code](../core/understand/how-to-read-a-configuration-manager-object-by-using-managed-code). After you have the task sequence package, you must create an [SMS_TaskSequence](../reference/osd/sms_tasksequence-server-wmi-class) object for the task sequence before you can change it. For more information, see [How to Read a Task Sequence From a Task Sequence Package](how-to-read-a-task-sequence-from-a-task-sequence-package).

### To enumerate the available task sequence packages

1. Set up a connection to the SMS Provider. For more information, see [SMS Provider fundamentals](../core/understand/sms-provider-fundamentals).
2. Query the SMS Provider for the available instances of [SMS_TaskSequencePackage](../reference/osd/sms_tasksequencepackage-server-wmi-class).
3. Display the required properties for each task sequence package returned by the query.

## Example

The following example method queries the SMS Provider for the available instance of [SMS_TaskSequencePackage](../reference/osd/sms_tasksequencepackage-server-wmi-class). To retrieve the lazy properties, the example gets the entire object from the SMS Provider.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub EnumerateTaskSequencePackages(connection)

    Set taskSequencePackages= connection.ExecQuery("Select * from SMS_TaskSequencePackage")

    For Each package in taskSequencePackages
        WScript.Echo package.Name
        WScript.Echo package.Sequence
    Next
End Sub
```

```c
public void EnumerateTaskSequencePackages(
    WqlConnectionManager connection)
{
    IResultObject taskSequencePackages = connection.QueryProcessor.ExecuteQuery("select * from SMS_TaskSequencePackage");

    foreach (IResultObject ro in taskSequencePackages)
    {
        ro.Get();

        // Get the lazy properties - Sequence property contains the Task sequence XML.
        Console.WriteLine(ro["Name"].StringValue);
        Console.WriteLine(ro["Sequence"].StringValue);

        Console.WriteLine();
    }
}
```

The example method has the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| `connection` | - Managed: `WqlConnectionManager`- VBScript: [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) | A valid connection to the SMS Provider. |

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