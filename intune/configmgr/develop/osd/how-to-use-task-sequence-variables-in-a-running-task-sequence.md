---
layout: Conceptual
title: Use Task Sequence Variables in a Running Task Sequence - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/how-to-use-task-sequence-variables-in-a-running-task-sequence
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
description: In Configuration Manager, you can create, get, and set task sequence variables in a running task sequence by using the task sequence environment COM automation object.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d86d92bf-561b-eff0-b565-cf7c5bd668f2
document_version_independent_id: b20a7712-f7b9-840a-86a9-60bc835154b4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/how-to-use-task-sequence-variables-in-a-running-task-sequence.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/how-to-use-task-sequence-variables-in-a-running-task-sequence
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/how-to-use-task-sequence-variables-in-a-running-task-sequence.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
- https://authoring-docs-microsoft.poolparty.biz/devrel/4628cbd9-6f47-4ae1-b371-d34636609eaf
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
- https://authoring-docs-microsoft.poolparty.biz/devrel/be21deb8-8c64-44b0-b71f-2dc56ca7364f
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
platformId: 476e0438-ca6c-f435-4cea-ceb072523696
---

# Use Task Sequence Variables in a Running Task Sequence - Configuration Manager | Microsoft Learn

In Configuration Manager, you can create, get, and set task sequence variables in a running task sequence by using the task sequence environment COM automation object (`Microsoft.SMS.TSEnvironment`).

Typically, you use a command-line action that runs a script to access the task sequence variables. But you can also access them, within a running a task sequence, by using any programming environment that can use COM automation objects.

Note

When you set a task variable on the Configuration Manager client, it becomes available to subsequent steps in the task sequence.

To create a custom task sequence variable, you set a `Microsoft.SMS.TSEnvironment` property by using the name of the new variable that you want to create. If the variable doesn't already exist, it's created. If the variable already exists, its value is updated. You can later get the custom variable value from `Microsoft.SMS.TSEnvironment`.

When a task sequence variable is an array, it's passed in the following format:

```
<base array name><element #><Property>="value".
```

For example, the `OSDPartitions` variable is an array of `SMS_TaskSequencePartitionSettings`. The following example represents a one element `OSDPartitions` Array:

```
OSDPartitions0Bootable="true"
OSDPartitions0FileSystem="NTFS"
OSDPartition0QuickFormat="false"
OSDPartitions0Size="100"
OSDPartitions0SizeUnits="Percent"
OSDPartitions0Type="Primary"
```

To access `FileSystem` in this array, you would use `OSDPartitions0FileSystem`. If the array is larger, you would use`OSDPartitions1FileSystem` for the second element and so on through the array.

It isn't recommended that you use managed code with the task sequencing environment because you can't use it in the following environments:

- Windows PE
- Windows Server 2008
- Windows 2000

    Managed code does work when the full operating system is running with the correct version of .NET Framework installed.

    The version of .NET Framework that is required depends on the version of Visual Studio that you use.

| Visual Studio | .NET Framework Version |
| --- | --- |
| Visual Studio 2003 | 1.0 |
| Visual Studio 2005 | 2.0 |
| Visual Studio 2008 | 2.0 to 3.5 |

You'll need to use COM interop to access the `TSEnvironment` object. You'll need the following:

- Reference to **TSEnvironment 1.0 Type Library**.
- The **TSEnvironmentLib** namespace.

### To use task variables in a running task sequence

1. In a running task sequence, create an instance of `Microsoft.SMS.TSEnvironment`.
2. Get or set the required environment variable.

## Example

The following example method gets the `_SMSTSLogPath` variable. It also sets the value of a custom variable and an array custom variable value.

For information about calling the sample code, see [Calling Configuration Manager Code Snippets](../core/understand/calling-code-snippets).

```vbs
Sub UseTaskSequenceVariables()
   dim osd: set env = CreateObject("Microsoft.SMS.TSEnvironment")
   dim logPath

   ' You can query the environment to get an existing variable.
   logPath = env("_SMSTSLogPath")

    wscript.echo logPath

   ' You can also set a variable in the Operating System Deployment environment.
   env("MyCustomVariable") = "My Custom Value"

   ' Set the OSDPartitions(0) Bootable array member to 0.
    env("OSDPartitions0Bootable") = "true"
End Sub
```

## Compiling the Code

### Platforms

Operating System Deployment task sequencing environment

## Robust Programming

For more information about error handling, see [About Configuration Manager Errors](../core/understand/about-configuration-manager-errors).

## .NET Framework Security

For more information about securing Configuration Manager applications, see [Configuration Manager role-based administration](../core/servers/configure/role-based-administration).