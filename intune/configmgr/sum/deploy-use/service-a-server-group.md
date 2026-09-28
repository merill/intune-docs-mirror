---
layout: Conceptual
title: Service a server group - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/service-a-server-group
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
description: Server groups have been replaced by orchestration groups
ms.date: 2020-04-01T00:00:00.0000000Z
ms.topic: how-to
ms.subservice: software-updates
ms.collection: tier3
locale: en-us
document_id: ebab9fad-df7b-b0f2-3412-a926c90dcfc7
document_version_independent_id: a7ffb20f-824c-4859-5f9a-9650dd23d254
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/deploy-use/service-a-server-group.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/deploy-use/service-a-server-group
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/deploy-use/service-a-server-group.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 406126f7-0c05-e63f-702c-9bc213d5f03e
---

# Service a server group - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

- Starting in Configuration Manager version 2002, server groups have been replaced by orchestration groups. For more information, see [Orchestration groups](orchestration-groups).
- Pre-release features are features that are in the Current Branch for early testing in a production environment. These features are fully supported but are still in active development and might receive changes until they move out of the pre-release category. You must turn on this feature for it to be available. For more information, see [Use pre-release features from updates](../../core/servers/manage/pre-release-features).

Starting in Configuration Manager version 1606, you can configure server group settings for a collection to define how many, what percentage, or in what order computers in the collection will install software updates. You can also configure pre-deployment and post-deployment PowerShell scripts to run custom actions.

When you deploy software updates to a collection that has server group settings configured, Configuration Manager determines how many computers in the collection can install the software updates at any given time and makes the same number of deployment locks available. Only computers that get a deployment lock will start software update installation. When a deployment lock is available, a computer gets the deployment lock, installs the software updates, and then releases the deployment lock when software updates installation successfully completes. Then, the deployment lock becomes available for other computers. If a computer is unable to release a deployment lock, you can manually release all server group deployment locks for the collection.

Important

All of the computers in the collection must be assigned to the same site.

#### To create a collection for a server group

The server group settings are configured in the properties for a device collection. To service a server group, all members in the collection must be assigned to the same site. Use the following steps to create a collection and configure the server group settings:

1. [Create a device collection](../../core/clients/manage/collections/create-collections) that contains the computers in the server group.
2. In the **Assets and Compliance** workspace, click **Device Collections**, right-click the collection that contains the computers in the server group, and then click **Properties**.
3. On the **General** tab, select **All devices are part of the same server group**, and then click **Settings**.
4. On the **Server Group Settings** page, specify one of the following settings:

    - **Allow a percentage of machines to be updated at the same time**: Specifies that only a certain percentage of clients are updated at any one time. If, for example, the collection has 10 clients, and the collection is configured to update 30% of clients at the same time, then only 3 clients will install software updates at any given time.
    - **Allow a number of machines to be updated at the same time**: Specifies that only a certain number of clients are updated at any one time.
    - **Specify the maintenance sequence**: Specifies that the clients in the collection will be updated one at a time in the sequence that you configure. A client will only install software updates after the client that is ahead of it in the list has finished installing its software updates.
5. Specify whether to use a pre-deployment (node drain) script or post-deployment (node resume) script.

    Warning

    Custom scripts are not signed by Microsoft. It is your responsibility to maintain the integrity of these scripts.

    Tip

    The following are examples that you can use in testing for pre-deployment and post-deployment scripts that write the current time to a text file:

    **Pre-deployment**

    `#Start`

    `$a = Get-Date`

    `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`

    `Out-File C:\Windows\Temp\start.txt`

    **Post-deployment**

    `#End`

    `$a = Get-Date`

    `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`

    `Out-File C:\Windows\Temp\end.txt`

## Deploy software updates to the server group and monitor status

You deploy software updates to the server group collection by using the typical deployment process. After you deploy the software updates, you can monitor the software update deployment in the Configuration Manager console.

1. [Deploy software updates](manually-deploy-software-updates) to the server group collection.
2. [Monitor the software update deployment](monitor-software-updates). In addition to the standard monitoring views for software updates deployment, the **Waiting for lock** state is displayed when a client is waiting for its turn to install the software updates. You can review the UpdatesDeployment.log file for more information.

## Clear the deployment locks for computers in a server group

When a computer fails to release a deployment lock, you can manually release all server group deployment locks for the collection. Clear locks only when a deployment is stuck updating computers in the collection and there are computers that are still not compliant.

1. In the **Assets and Compliance** workspace, click **Device Collections**, and click the collection to clear deployment locks.
2. On the **Home** tab, in the **Deployment** group, click **Clear Server Group Deployment Locks**. When clients have failed to install the software updates and are preventing other clients from installing their software updates, the deployment locks can be manually cleared.