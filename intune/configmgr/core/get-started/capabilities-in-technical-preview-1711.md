---
layout: Conceptual
title: Technical Preview 1711 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/capabilities-in-technical-preview-1711
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
description: Learn about features available in the Technical Preview version 1711 for Configuration Manager.
ms.date: 2017-11-17T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 9e9ed863-a538-2e60-034e-5d56b6118ff6
document_version_independent_id: 7e8039e6-b4a3-b548-8c7d-319ebfaa3a18
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/capabilities-in-technical-preview-1711.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/capabilities-in-technical-preview-1711
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/capabilities-in-technical-preview-1711.md
platformId: d49f1090-d151-762d-2797-b2b3b86193d2
---

# Technical Preview 1711 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the Technical Preview for Configuration Manager, version 1711. You can install this version to update and add new capabilities to your Configuration Manager technical preview site. Before installing this version of the technical preview, review [Technical Preview for Configuration Manager](technical-preview) to become familiar with general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback about the features in a technical preview.

**Known Issues in this Technical Preview:**

- **Support for Windows 10, version 1709 (also known as the Fall Creators Update)**. Beginning with this Windows release, Windows media includes multiple editions. When configuring a task sequence to use an operating system upgrade package or operating system image, be sure to select an [edition that is supported for use by Configuration Manager](../plan-design/configs/support-for-windows-10).
- **Update to a new preview version fails when you have a site server in passive mode**. When you run a preview version that has a [primary site server in passive mode](capabilities-in-technical-preview-1706#site-server-role-high-availability), you must uninstall the passive mode site server before you can successfully update your preview site to this new preview version. You can reinstall the passive mode site server after your site completes the update.

    To uninstall the passive mode site server:

    1. In the console go to **Administration** &gt; **Overview** &gt; **Site Configuration** &gt; **Servers and Site System Roles**, and then select the passive mode site server.
    2. In the **Site System Roles** pane, right click on the **Site server** role, and then choose **Remove Role**.
    3. Right-click on the passive mode site server, and then choose **Delete**.
    4. After the site server uninstalls, on the active primary site server restart the service **CONFIGURATION\_MANAGER\_UPDATE**.

**The following are new features you can try out with this version.**

## Improvements to Run Task Sequence

This technical preview will improve the Run Task Sequence step. Improvements include the following items:

- Support for all operating system deployment scenarios from Software Center, PXE, and media.
- Improvements to console actions such as copy, import, export, and warning during object deletion.
- Support for the **Create Prestage Content** wizard.
- Integration with deployment verification.
- The Run Task Sequence step can now be used across multiple levels of task sequences, not just a single parent-child relationship. Multi-level relationships increase the complexity, so use with caution. These relationships are still checked for circular references.

### Try it out!

Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:

1. In the task sequence editor, click **Add**, select **General**, and click **Run Task Sequence**.
2. Click **Browse** to select the child task sequence.

## Allow user interaction when installing an application

With this preview, you can allow an end user to interact with an application installation during the running of the task sequence. For example, run a setup process that prompts the end user for various options. Some application installers cannot have user prompts silenced, or the installation process may require specific configuration values only known to the user. This feature allows you to handle these installation scenarios.

### Try it out!

Try to complete the following tasks and then send **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:

1. Create or edit an application. For more information, see [Create applications with Configuration Manager](../../apps/deploy-use/create-applications).

    a. Choose the **User Experience** tab in the **Windows Installer (\*msi file) Properties**.

    b. Select **Install for system** for **Install behavior**.

    c. Select **Whether or not a user is logged on** for **Log on requirement**.

    d. Select **Normal** for **Installation program visibility**. You can select from three options: **Minimized**, **Normal**, or **Maximized**.

    e. Select the **Allow users to interact with the program installation** box.
2. Create or edit a task sequence to install the application using the **Install Application** step. For more information, see [Install Application](../../osd/understand/task-sequence-steps#BKMK_InstallApplication) in the [Task sequence steps](../../osd/understand/task-sequence-steps).

    a. Imaging task sequence after the Setup Windows and Configuration Manager step.

    b. In-place upgrade task sequence in the Post-Processing group.
3. Deploy the task sequence to a client.
4. Install the task sequence from Software Center.

During task sequence progress, the application installation interface appears on the target end-user device. The task sequence progress pauses until the end user completes the application installation workflow.

### Install using the wizard

You can also use this feature when deploying an app using the wizard.

1. Create or edit an application.
2. Deploy the application to a client.
3. Install the application from Software Center. The application installation interface should appear. The end-user should follow the application installation wizard and the application will be successfully installed.