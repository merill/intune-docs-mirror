---
layout: Conceptual
title: Custom action client applications - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/osd/about-configuration-manager-custom-action-client-applications
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
description: About custom action client applications.
ms.date: 2021-10-01T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: e1aa3e5a-e16d-6243-06a4-787ade5e7e1d
document_version_independent_id: 47cdd5a1-3070-daaf-cf61-0a6b478ddf22
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/osd/about-configuration-manager-custom-action-client-applications.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/osd/about-configuration-manager-custom-action-client-applications
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/osd/about-configuration-manager-custom-action-client-applications.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: b5f4a360-e6d4-ac9b-dad1-2c775b4421d1
---

# Custom action client applications - Configuration Manager | Microsoft Learn

The task sequence in Configuration Manager does custom action operations during client deployment. The application can be a process, a script, or other commands. The requirements for the application are defined in a Managed Object Format (MOF) file. Example requirements include the operating environment, command-line arguments, properties, and return codes. They're added to the task sequence environment when the action is processed.

## Custom action MOF file

The MOF file for a custom action is similar to the following example:

```mof
[   CommandLine("smsswd.exe /run:%1 abc.exe %2"),
    : (custom ui control and category qualifiers for action)
    ]
class MyCustomAction : SMS_TaskSequence_Action
{
    [TaskSequencePackage, CommandLineArg(1)]
    string          PackageIDForAbcExe;

    [CommandLineArg(2), AllowedLen("1-32000")]
    string          AbcCommandLineArgs;

    [SuccessCodes, Not_Null]
    string          AbcSuccessCodes = "0 3010";

    string         SomeOtherPropertyThatAbcNeeds;

    string          SupportedEnvironment = "WinPEandFullOS";
};
```

The MOF file describes the information that is needed for the custom action application input, environment, properties, and deployment package information.

For more information, see [About the Configuration Manager custom action MOF file](about-configuration-manager-custom-action-mof-files).

## Application input

Custom actions have to run unattended, so the application shouldn't prompt for user input. All inputs should be received from either the command line, the task sequence environment, or from a data file.

The command line for the action application is set, in the MOF file, by using the **Run command line** built-in action.

For example:

```mof
CommandLine("smsswd.exe /run:PackageID abc.exe [any abc.exe command line args]"
```

## Application processing

The task sequence application runs the custom action operations. It must be aware of its operating environment and have access to the task sequencing environment variables, report progress, and return completion codes.

### Environment

The MOF file should specify the operating environment with the [SMS_TaskSequence_Action Server WMI Class](../reference/osd/sms_tasksequence_action-server-wmi-class)`SupportedEnvironment` property. The available environments are Windows PE (`WinPE`), full operating system (`FullOS`), or both environments (`WinPEandFullOS`).

The choice of environment depends on the circumstances. For example, pre-operating install configuration will likely be done in the Windows PE environment. For more information, see [Infrastructure requirements for OS deployment](../../osd/plan-design/infrastructure-requirements-for-operating-system-deployment). Updates to currently installed operating systems will use the full operating system environment. For example, software or driver installation. Operating system environment agnostic tasks such as reboots or the creation of network connections, can be performed by using both environment settings.

### Processing

During processing, you access the task sequence variables defined by the MOF file by using the `TSEnvironment` COM automation object. For more information, see [How to Use Task Sequence Variables in a Running Configuration Manager Task Sequence](how-to-use-task-sequence-variables-in-a-running-task-sequence).

If the operation takes a long time, you can report progress to the task sequence environment and display a progress indicator by using the [ProgressUI client COM automation class](../reference/core/clients/client-classes/progressui-client-com-automation-class). For more information, see [About reporting Configuration Manager custom action progress](about-reporting-configuration-manager-custom-action-progress).

### Completion

The application should set the `SuccessCodes` environment variable as a return value when it's completed.

| Return | Description |
| --- | --- |
| 0 | Success |
| Non-zero | Failure |

If a reboot is required after the application finishes, the `SMSTSRebootRequested` environment variable should be set. For more information, see [Task sequence variables](../../osd/understand/task-sequence-variables#SMSTSRebootRequested). For information about setting environment variables, see [How to use task sequence variables in a running Configuration Manager task sequence](how-to-use-task-sequence-variables-in-a-running-task-sequence).

## Deployment

To be used by Configuration Manager, the custom action application must be available from a Configuration Manager package. The administrator can create the package by using either the Configuration Manager console or by using a programming language. For more information, see [How to create a package](../core/servers/configure/how-to-create-a-package).

The package identifier must be available for the deployment to work. Typically the MOF file declares a property to hold it, as in the following example:

```mof
[TaskSequencePackage, CommandLineArg(1)]
string PackageIDForAbcExe;
```

Note

The package identifier is the [SMS_Package Server WMI Class](../reference/core/servers/configure/sms_package-server-wmi-class)`PackageID` property.

The package identifier is obtained from the administrator, when the custom action is edited in the task sequence editor.

To enable this behavior, your custom action control can use a text edit control in its implementation to get the package identifier from the administrator. For an example that uses a text control, see [How to create a Configuration Manager custom action control](how-to-create-a-configuration-manager-custom-action-control).

When used by the administrator, the custom action control is edited as part of a task sequence by using the task sequence editor. When saved by the task sequence editor, an [SMS_TaskSequencePackage Server WMI Class](../reference/osd/sms_tasksequencepackage-server-wmi-class) is created to hold the task sequence, including the custom action.

The task sequence package is then advertised to clients along with the custom action package that is referenced by the custom action. For more information, see [How to create an advertisement](../core/servers/configure/how-to-create-an-advertisement).

When the custom action is run on the client, the package identifier for the custom action is supplied as a command-line parameter, from which the binary files for the custom action are extracted and run.

The package identifier is provided by using the `/run` command-line parameter to Smsswd.exe.

## Pre-network partition and pre-partition setup

If you need to configure disk or network connectivity before you have a disk partition and before you have network connectivity, you need to create an application to do these tasks. Your application should be placed in a custom boot image by using the Windows Assessment and Deployment Kit (ADK). For more information, see [Windows ADK scenarios for IT Pros](/en-us/windows/deployment/windows-adk-scenarios-for-it-pros).

Note

Adding files to the boot image file can increase the minimum RAM requirements and can, due to low memory conditions, cause task sequences to fail in unexpected ways.

Then import the image into Configuration Manager as a custom image. For more information, see [Add a boot image](../../osd/get-started/manage-boot-images#add-a-boot-image).

The application, any supporting files, and the custom SMSTS.INI should be placed in the Windows folder.

To use the application, use the custom boot image in a task sequence that contains a pre-partition/network step.