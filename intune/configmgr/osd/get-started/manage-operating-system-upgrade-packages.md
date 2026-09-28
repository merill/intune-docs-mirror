---
layout: Conceptual
title: Manage OS upgrade packages - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/get-started/manage-operating-system-upgrade-packages
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
description: Learn how to manage OS upgrade packages in Configuration Manager.
ms.date: 2025-07-31T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 6cb08fb9-94f2-7085-5754-f9e6b2a341b2
document_version_independent_id: 6fd5a889-5ebb-c6e4-311f-e0f50f05101d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/get-started/manage-operating-system-upgrade-packages.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/get-started/manage-operating-system-upgrade-packages
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/get-started/manage-operating-system-upgrade-packages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: a034257b-0ea4-386d-ef19-42f12c4b2c99
---

# Manage OS upgrade packages - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

An OS upgrade package in Configuration Manager contains the Windows setup source files to upgrade an existing OS on a computer. This article describes how to add, distribute, and service an OS upgrade package.

Note

OS upgrade packages can also be used for new installations of Windows. However it's dependent on drivers being compatible with this method. When new installations of Windows are performed from an OS upgrade package, drivers are installed while still in Windows PE versus simply being injected while in Windows PE. Some drivers aren't compatible with being installed while in Windows PE. If drivers aren't compatible with being installed while in Windows PE, then use an [OS image](manage-operating-system-images), such as **install.wim**, instead.

## Add an OS upgrade package

Before you can use an OS upgrade package, first add it to your Configuration Manager site.

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Operating Systems**, and then select the **Operating System Upgrade Packages** node.
2. On the **Home** tab of the ribbon, in the **Create** group, select **Add Operating System Upgrade Package**. This action starts the Add Operating System Upgrade Wizard.
3. On the **Data Source** page, specify the following settings:

    - The network **Path** to the installation source files of the OS upgrade package. For example, `\\server\share\path`.

        Note

        The installation source files contain setup.exe and other files and folders to install the OS.

        Important

        Limit access to these installation source files to prevent unwanted tampering.
    - Starting in version 2107, review and agree to the license terms for this OS media on behalf of your organization.
    - **Extract a specific image index from install.wim file of selected upgrade package** and then select an image index from the list. This option automatically imports a single index rather than all image indexes in the file. Using this option results in a smaller image file, and faster offline servicing. It also supports the process to Optimize image servicing, for a smaller image file after applying software updates.

        Important

        Configuration Manager overwrites the existing install.wim in the OS upgrade package. It extracts the image index to a temporary location, and then moves it into the original source directory. Before you import an OS upgrade package and enable this option, make sure to backup the original source files.
    - If you want to pre-cache content on a client, specify the **Architecture** and **Language** of the image. For more information, see [Configure pre-cache content](../deploy-use/configure-precache-content).
4. On the **General** page, specify the following information. This information is useful for identification purposes when you have more than one OS upgrade package.

    - **Name**: A unique name for the OS upgrade package.
    - **Version**: An optional version identifier. This property doesn't need to be the OS version of the upgrade package. It's often your organization's version for the package.
    - **Comment**: An optional brief description.
5. Complete the wizard.

Next, distribute the OS upgrade package to distribution points.

## Distribute content to a distribution point

Distribute OS upgrade packages to distribution points the same as other content. Before you deploy the task sequence, distribute the OS upgrade package to at least one distribution point. For more information, see [Distribute content](../../core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute).

## Apply software updates to an image

Important

Configuration Manager doesn’t support offline servicing for Windows images and update packages that use the [Unified Update Platform](/en-us/windows/deployment/update/windows-update-overview#unified-update-platform-uup-architecture) (UUP), including Windows Server 2025 and recent Windows 11 releases. This limitation is due to changes in how UUP updates are delivered.

To keep UUP-based Operating System Deployments up to date, use the latest patched operating system ISO available from the [Microsoft 365 admin center](https://admin.microsoft.com). After you obtain the updated operating system ISO:

- Import the **install.wim** image from the ISO as an **Operating System Image** for use with bare metal and refresh task sequences.
- Import the entire ISO contents as an **Operating System Upgrade Package** for use with in-place upgrade task sequences.

Note

This section applies to both **Operating System Images** and **Operating System Upgrade Packages**. It uses the general term "image" to refer to the Windows image file (WIM). Both of these objects have a WIM, which contains Windows installation files. Software updates are applicable to these files in both objects. The behavior of this process is the same between both objects.

Each month there are new software updates applicable to the image. Before you can apply software updates to it, you need the following prerequisites:

- A software updates infrastructure
- Successfully synchronized software updates
- Downloaded the software updates to the content library on the site server

For more information, see [Deploy software updates](../../sum/deploy-use/deploy-software-updates).

Apply applicable software updates to an image on a specified schedule. This process is sometimes called *offline servicing*. On this schedule, Configuration Manager applies the selected software updates to the image. It can then also redistribute the updated image to distribution points.

Important

While you can select any software update that's applicable to the image based on version, DISM can only apply certain types of updates to the image. The **OfflineServicingMgr.log** file shows the following entry: `Not applying this update binary, it is not supported`.

The site database stores information about the image, including the software updates that were applied at the time of the import. Software updates that you apply to the image since it was initially added are also stored in the site database. When you start the wizard to apply software updates, it retrieves the list of applicable software updates that the site hasn't yet applied to the image. Configuration Manager copies the software updates that you select from the content library on the site server. It then applies the software updates to the image.

### Servicing process

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Operating Systems**, and then select either **Operating System Images** or **Operating System Upgrade Packages**.
2. Select the object to which to apply software updates.
3. On the ribbon, select **Schedule Updates** to start the wizard.
4. On the **Choose Updates** page, select the software updates to apply to the image. It might take some time for the list of updates to appear in the wizard. Use the **Filter** to search for strings in the metadata. Use the **System architecture** drop-down list to filter on **X86**, **X64**, or **All**. You can select one, many, or all updates in the list. When you're finished selecting updates, select **Next**.
5. On the **Set Schedule** page, specify the following settings, and then select **Next**.

    1. **Schedule**: Specify the schedule for when the site applies the software updates to the image.
    2. **Continue on error**: Select this option to continue to apply software updates to the image even when there's an error.
    3. **Update distribution points with the image**: Select this option to update the image on distribution points after the site applies the software updates.
6. Complete the Schedule Updates Wizard.

Note

To minimize the payload size, the servicing of OS upgrade packages and OS images removes the older version.

### Servicing operations

In the Configuration Manager console, in either the **OS Images** or **OS Upgrade Packages** node, add the following columns to the view:

- **Scheduled Updates Date**: This property shows the next defined schedule.
- **Scheduled Updates Status**: This property shows the status. For example, **Successful** or **In Process**.

Select a specific image object, and then switch to the **Update Status** tab in the details pane. This tab shows the list of updates in the image.

Select a specific image object, and select **Properties** in the ribbon. The **Installed Updates** tab shows the list of updates in the image. The **Servicing** tab is a read-only view of the current servicing schedule and the updates that you've scheduled to apply.

When the status is **In Process**, you can select **Cancel Scheduled Updates** on the ribbon. This action cancels the active servicing process.

To troubleshoot this process, view the **OfflineServicingMgr.log** and **dism.log** files on the site server. For more information, see [Log files](../../core/plan-design/hierarchy/log-files).

### Specify the drive for offline OS image servicing

You can specify the drive that Configuration Manager uses during offline servicing of OS images. This process can consume a large amount of disk space with temporary files. This option gives you flexibility to select the drive to use.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Sites** node. In the ribbon, select **Configure Site Components** and then choose **Operating System Deployment**.
2. On the **Offline Servicing** tab, specify the option for **A local drive to be used by offline servicing of images**.

By default, this setting is **Automatic**. With this value, Configuration Manager selects the drive on which it's installed.

If you select a drive that doesn't exist on the site server, Configuration Manager behaves the same as if you select **Automatic**.

During offline servicing, Configuration Manager stores temporary files in the folder, `<drive>:\ConfigMgr_OfflineImageServicing`. It also mounts the OS image in this folder.

### Optimized image servicing

When you apply software updates to an OS image, you can optimize the output by removing any superseded updates. The optimization to offline servicing only applies to images with a single index.

When you schedule the site to apply software updates to an OS image, it uses the Windows Deployment Image Servicing and Management (DISM) command-line tool. During the servicing process, this change introduces the following two additional steps:

- It runs DISM against the mounted offline image with the parameters `/Cleanup-Image /StartComponentCleanup /ResetBase`. If this command fails, the current servicing process fails. It doesn't commit any changes to the image.
- After Configuration Manager commits changes to the image and unmounts it from the file system, it exports the image to another file. This step uses the DISM parameter `/Export-Image`. It removes unneeded files from the image, which reduces the size.

Microsoft recommends that you regularly apply updates to your offline images. You don't have to use this option every time you service an image. When you do this process each month, this option provides you the greatest advantage by using it over time. For more information, see [Recommendations for Install Software Updates step](../understand/install-software-updates#recommendations).

While this option helps reduce the overall size of the serviced image, it does take longer to complete the process. Use the wizard to schedule servicing during convenient times. It also requires additional storage on the site server. You can customize the site to use an alternate location. For more information, see Specify the drive for offline OS image servicing.

#### Process to optimize image servicing

1. Start the servicing process.
2. On the **Set Schedule** page, select the option to **Remove superseded updates after the image is updated**. This option isn't automatically enabled. If the image has more than one index, you can't use this option.
3. To schedule image servicing, complete the wizard.

Validate and monitor the process using the **OfflineServicing.log**.