---
layout: Conceptual
title: Prestart commands for task sequence media - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/understand/prestart-commands-for-task-sequence-media
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
description: Create a script to use for the prestart command, distribute the content associated with the prestart command, and configure the prestart command in media.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 90b208b5-1d9d-75f8-a80e-6b64658d900d
document_version_independent_id: 1bb8da76-bb09-c2fe-37ac-fbb00bd5544d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/understand/prestart-commands-for-task-sequence-media.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/understand/prestart-commands-for-task-sequence-media
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/understand/prestart-commands-for-task-sequence-media.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 71312368-678b-ea7f-7815-c28666578f5f
---

# Prestart commands for task sequence media - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can create a prestart command in Configuration Manager to use with boot media, stand-alone media, and prestaged media. The prestart command is a script or executable that runs before the task sequence is selected and can interact with the user in Windows PE. The prestart command can prompt a user for information and save it in the task sequence environment or query a task sequence variable for information. When the destination computer boots, the command-line is run before the policy is downloaded from the management point. Use the following procedures to create a script to use for the prestart command, distribute the content associated with the prestart command, and configure the prestart command in media.

## Create a script file to use for the Prestart Command

Task sequence variables can be read and written by using the Microsoft.SMS.TSEnvironment COM object while the task sequence is running. The following example illustrates a Visual Basic script file that queries the \_SMSTSLogPath task sequence variable to get the current log location. The script also sets a custom variable.

```VBScript
dim osd: set env = CreateObject("Microsoft.SMS.TSEnvironment")
dim logPath
' You can query the environment to get an existing variable.
logPath = env("_SMSTSLogPath")
' You can also set a variable in the OSD environment.
env("MyCustomVariable") = "varname"
```

## Create a Package for the Script File and Distribute the Content

After you create the script or executable for the prestart command, you must create a package source to host the files for the script or executable, create a package for the files (no program required), and then distribute the content to a distribution point.

For more information about creating a package, see [Packages and programs](../../apps/deploy-use/packages-and-programs).

For more information about distributing content, see [Distribute content](../../core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute).

## Configure the Prestart Command in Media

You can configure a prestart command in the Create Task Sequence Media Wizard for stand-alone media, bootable media, or prestaged media. For more information about the media types, see [Create task sequence media](../deploy-use/create-task-sequence-media). Use the following procedure to create a prestart command in media.

#### To create a prestart command in media

1. In the Configuration Manager console, click **Software Library**.
2. In the **Software Library** workspace, expand **Operating Systems**, and then click **Task Sequences**.
3. On the **Home** tab, in the **Create** group, click **Create Task Sequence Media** to start the Create Task Sequence Media Wizard.
4. On the **Select Media Type** page, select **Stand-alone media**, **Bootable media**, or **Prestaged media**, and then click **Next**.
5. Navigate to the **Customization** page of the wizard. For more information about configuring the other pages in the wizard, see [Create task sequence media](../deploy-use/create-task-sequence-media).
6. On the **Customization** page, specify the following information, and then click **Next**.

    - Select **Enable prestart command**.
    - In the **Command line** text box, enter the script or executable that you created for the prestart command.

        Important

        Use **cmd /C &lt;prestart command&gt;** to specify the prestart command. For example, if you used TSScript.vbs as the name for your prestart command script, you would enter **cmd /C TSScript.vbs** for the command line. Where **cmd /C** opens a new Windows command interpreter window and uses the Path environment variable to find the prestart command script or executable. You can also specify the full path to the prestart command, but the drive letter could be different on computers with different drive configurations.
    - Select **Include files for the prestart command**.
    - Click **Set** to select the package that is associated with the prestart command files.
    - Click **Browse** to select the distribution point that hosts the content for the prestart command.
7. Complete the wizard.