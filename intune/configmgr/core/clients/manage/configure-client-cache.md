---
layout: Conceptual
title: Configure the client cache - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/configure-client-cache
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
description: Configure the client content cache during or after client install.
ms.date: 2024-12-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 998ab44c-1458-bdd9-881d-cc9f08858adc
document_version_independent_id: 44d38d86-7dff-29fd-c0f4-3d12fce05ac2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/configure-client-cache.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/configure-client-cache
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/configure-client-cache.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 0b1fd96f-5366-d1cd-1cc5-6598ce056d53
---

# Configure the client cache - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The client cache stores temporary files for when clients install applications and programs. Software updates also use the client cache, but always attempt to download to the cache whatever of the size setting. Configure the cache settings, such as size and location, when you manually install the client, when you use client push installation, or after installation.

You can specify the cache folder size using client settings in the Configuration Manager console. For more information, see [Client cache settings](../deploy/about-client-settings#client-cache-settings).

The default location for the Configuration Manager client cache is `%windir%\ccmcache` and the default disk space is 5120 MB.

Important

Don't encrypt the folder used for the client cache. Configuration Manager can't download content to an encrypted folder.

## About

The Configuration Manager client downloads the content for required software soon after the deployment's available time but waits to run it until the deployment's scheduled time. At the scheduled time, the Configuration Manager client checks to see whether the content is available in the cache. If content is in the cache and it's the correct version, the client uses the cached content. When the required version of the content changes, or if the client deletes the content to make room for another package, the client downloads the content to the cache again.

If the client attempts to download content for a program or application that's greater than the size of the cache, the deployment fails because of insufficient cache size. The client generates status message 10050 for insufficient cache size. If you increase the cache size later, the result is:

- For a required program: The client doesn't automatically retry to download the content. Redeploy the package and program to the client.
- For a required application: The client automatically retries to download the content when it downloads its client policy.

If the client attempts to download content that's less than the size of the cache, but the cache is full, all *required* deployments keep retrying until:

- The cache space is available
- The download times out
- The retry count reaches its limit

If you later increase the cache size, the client attempts to download the content again during the next retry interval. The client tries to download the content every four hours until it tries 18 times.

Cached content isn't automatically deleted and is only removed if new content requires its disk space. It remains in the cache for the configured number of minutes after the client uses that content. If you configure the content with the option to persist content in the client cache, the client doesn't automatically delete it. If the cache space is used by content that was downloaded within the configured number of minutes, and the client must download new content, either increase the cache size or choose the option to delete persisted cache content. For more information, see [About client settings](../deploy/about-client-settings#minimum-duration-before-cached-content-can-be-removed-minutes).

Important

Don't manually delete files from the client cache folder using Windows Explorer or the command line. This action can cause issues with the Configuration Manager client. The client manages the cache and tracks the content apart from the file system. Always use a supported method to delete files in the cache.

For applications only, if the content for a related deployment currently exists in the cache, then the client downloads only new or changed files. Related deployments include those deployments for older revisions of the same deployment type and superseded applications.

## Configure

Use the following procedures to configure the client cache during manual client installation or after you install the client.

### Configure the cache during manual client installation

Run the CCMSetup.exe command from the install source location and specify the following properties that you require, and separated by spaces:

- DISABLECACHEOPT
- SMSCACHEDIR
- SMSCACHEFLAGS

Note

Use the cache size settings available in **Client Settings** in the Configuration Manager console instead of SMSCACHESIZE. For more information, see [Client cache settings](../deploy/about-client-settings#client-cache-settings).

For more information about how to use these command-line properties for CCMSetup.exe, see [About client installation properties](../deploy/about-client-installation-properties).

### Configure the cache during client push installation

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Sites** node.
2. Select the appropriate site. On the **Home** tab of the ribbon, in the **Settings** group, select **Client Installation Settings**, and choose **Client Push Installation**. Switch to the **Installation Properties** tab.
3. Specify the following properties, separated by spaces:

    - DISABLECACHEOPT
    - SMSCACHEDIR
    - SMSCACHEFLAGS

    Note

    Use the cache size settings available in **Client Settings** in the Configuration Manager console instead of SMSCACHESIZE. For more information, see [Client cache settings](../deploy/about-client-settings#client-cache-settings).

For more information about how to use these command-line properties for CCMSetup.exe, see [About client installation properties](../deploy/about-client-installation-properties).

### Configure the cache on the client computer

1. On the client computer, open the **Configuration Manager** control panel.
2. Switch to the **Cache** tab. Set the space and location properties. The default location is `%windir%\ccmcache`.
3. To delete the files in the cache folder, choose **Delete Files**.

    Important

    Don't manually delete files from the ccmcache folder using Windows Explorer or the command line. This action can cause issues with the Configuration Manager client. The client manages the cache and tracks the content apart from the file system. Always use a supported method to delete files in the cache. For example, the **Delete Files** option on the control panel.

### Configure client cache size in Client Settings

Adjust the size of the client cache without having to reinstall the client. Use the cache size settings available in **Client Settings** in the Configuration Manager console. For more information, see [Client cache settings](../deploy/about-client-settings#client-cache-settings).