---
layout: Conceptual
title: Manage network bandwidth for content - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/manage-network-bandwidth
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
description: Configure scheduling, throttling, and prestaged content for Configuration Manager.
ms.date: 2017-02-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 36b7dcc4-756d-70b9-2592-4cbe58043c53
document_version_independent_id: b1b7bbae-deb6-3ec1-4b9e-3eb261392983
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/hierarchy/manage-network-bandwidth.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/hierarchy/manage-network-bandwidth
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/hierarchy/manage-network-bandwidth.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aebdc4a3-c54b-4eea-94e3-663d5e166f57
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e2c9f30c-00ec-44c0-846c-b20dbfb3283f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1baec8e6-ab38-4b56-bb59-f6282d94f311
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/702271fe-87d7-4493-828b-2d6fde3de8ab
platformId: 828e698b-fc79-31d7-2da8-76856a76a65a
---

# Manage network bandwidth for content - Configuration Manager | Microsoft Learn

To help you manage network bandwidth that is used for the content management process of Configuration Manager, you can use built-in controls for scheduling and throttling. You can also use prestaged content. The following sections describe these options in more detail.

## Scheduling and throttling

When you create a package, change the source path for the content, or update content on the distribution point, the files are copied from the source path to the content library on the site server. Then, the content is copied from the content library on the site server to the content library on the distribution points. When content source files are updated, and the source files have already been distributed, Configuration Manager retrieves only the new or updated files, and then sends them to the distribution point.

You can use scheduling and throttling controls for site-to-site communication, and for communication between a site server and a remote distribution point. If network bandwidth is limited even after you set up the scheduling and throttling controls, you might consider prestaging the content on the distribution point.

In Configuration Manager, you can set up a schedule and specify throttling settings on remote distribution points that determine when and how content distribution is performed. Each remote distribution point can have different configurations that help address network bandwidth limitations from the site server to the remote distribution point. The controls for scheduling and throttling to the remote distribution point are similar to the settings for a standard sender address. In this case, the settings are used by a new component, called Package Transfer Manager.

Package Transfer Manager distributes content from a site server, as a primary site or secondary site, to a distribution point that is installed on a site system. The throttling settings are specified on the **Rate Limits** tab, and the scheduling settings are specified on the **Schedule** tab, for a distribution point that is not on a site server. The time settings are based on the time zone from the sending site, not the distribution point.

Important

The **Rate Limits** and **Schedule** tabs are displayed only in the properties for distribution points that are not installed on a site server.

For more information, see [Install and configure distribution points for Configuration Manager](../../servers/deploy/configure/install-and-configure-distribution-points).

## Prestaged content

You can prestage content to add the content files to the content library on a site server or distribution point, before you distribute the content. Because the content files are already in the content library, they do not transfer over the network when you distribute the content. You can prestage content files for applications and packages.

In the Configuration Manager console, select the content that you want to prestage, and then use the **Create Prestaged Content File Wizard**. This creates a compressed, prestaged content file that contains the files and associated metadata for the content. Then, you can manually import the content at a site server or distribution point. Note the following points:

- When you import the prestaged content file on a site server, the content files are added to the content library on the site server, and then registered in the site server database.
- When you import the prestaged content file on a distribution point, the content files are added to the content library on the distribution point. A status message is sent to the site server that informs the site that the content is available on the distribution point.

You can optionally configure the distribution point as **prestaged** to help manage content distribution. Then, when you distribute content, you can choose whether you want to:

- Always prestage the content on the distribution point.
- Prestage the initial content for the package, and then use the standard content distribution process when there are updates to the content.
- Always use the standard content distribution process for the content in the package.

### Determine whether to prestage content

Consider prestaging content for applications and packages in the following scenarios:

- **To address the issue of limited network bandwidth from the site server to a distribution point.** If scheduling and throttling aren't enough to satisfy your concerns about bandwidth, consider prestaging the content on the distribution point. Each distribution point has the **Enable this distribution point for prestaged content** setting that you can choose in the distribution point properties. When you enable this option, the distribution point is identified as a prestaged distribution point, and you can choose how to manage the content on a per-package basis.

    The following settings are available in the properties for an application, package, driver package, boot image, operating system installer, and image. These settings let you choose how content distribution is managed on remote distribution points that are identified as prestaged:

    - **Automatically download content when packages are assigned to distribution points**: Use this option when you have smaller packages, and the scheduling and throttling settings provide enough control for content distribution.
    - **Download only content changes to the distribution point**: Use this option when you expect future updates to the content in the package to be generally smaller than the initial package. For example, you might prestage an application like Microsoft 365 Apps, because the initial package size is over 700 MB and is too large to send over the network. However, content updates to this package might be less than 10 MB, and are acceptable to distribute over the network. Another example might be driver packages, where the initial package size is large, but incremental driver additions to the package might be small.
    - **Manually copy the content in this package to the distribution point**: Use this option when you have large packages, with content such as an operating system, and you never want to use the network to distribute the content to the distribution point. When you select this option, you must prestage the content on the distribution point.

    Important

    The preceding options are applicable on a per-package basis, and are only used when a distribution point is identified as prestaged. Distribution points that have not been identified as prestaged ignore these settings. In this case, content always is distributed over the network from the site server to the distribution points.
- **To restore the content library on a site server.** When a site server fails, information about packages and applications that is contained in the content library is restored to the site database as part of the restore process, but the content library files are not restored as part of the process. If you do not have a file system backup to restore the content library, you can create a prestaged content file from another site that contains the packages and applications that you have to have. You can then extract the prestaged content file on the recovered site server. For more information about site server backup and recovery, see [Backup and recovery for Configuration Manager](../../servers/manage/backup-and-recovery).