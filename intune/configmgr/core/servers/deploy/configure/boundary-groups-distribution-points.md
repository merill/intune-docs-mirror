---
layout: Conceptual
title: Boundary groups and distribution points - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/boundary-groups-distribution-points
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
description: Understand how clients and distribution points behave with boundary groups.
ms.date: 2021-08-02T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 771803b5-8dda-17d2-3b23-4c6f250b9a3f
document_version_independent_id: fc860374-c587-0c9b-9513-90ee558eec87
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/boundary-groups-distribution-points.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/boundary-groups-distribution-points
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/boundary-groups-distribution-points.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: b9fa1166-5ea3-6cd9-8dee-5d9e1056f13c
---

# Boundary groups and distribution points - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When a client requests the location of a distribution point, Configuration Manager sends the client a list of site systems. These site systems are of the appropriate type associated with each boundary group that includes the client's current network location.

- During software distribution, clients request a location for deployment content on a valid content source. This location may be a distribution point, or a peer cache source.
- During OS deployment, clients request a location to send or receive their state migration information.

    - Clients get content based on boundary group behaviors. For more information, see Task sequence support for boundary groups.

During content deployment, if a client requests content that isn't available from a source in its current boundary group, the client continues to request that content. The client tries different content sources in its current boundary group until it reaches the fallback period for a neighbor or the default site boundary group. If the client still hasn't found content, it then expands its search for content sources to include the neighbor boundary groups.

If you configure the content to distribute on-demand, and it isn't available on a distribution point when a client requests it, the site begins to transfer the content to that distribution point. It's possible the client finds that server as a content source before falling back to use a neighbor boundary group.

## Client installation

The Configuration Manager client installer, ccmsetup, can get installation content from a local source or via a management point. Its initial behavior depends upon the command-line parameters you use to install the client:

- If you don't use either `/mp` or `/source` parameters, ccmsetup tries to get a list of management points from Active Directory or DNS.
- If you only specify `/source`, it forces the installation from the specified path. It doesn't discover management points. If it can't find ccmsetup.cab at the specified path, ccmsetup fails.
- If you specify both `/mp` and `/source`, it checks the specified management points, and any it discovers. If it can't locate a valid management point, it falls back to the specified source path.

For more information on these ccmsetup parameters, see [Client installation parameters and properties](../../../clients/deploy/about-client-installation-properties).

When ccmsetup contacts the management point to locate the necessary content, the management point returns distribution points based on boundary group configuration. If you define relationships on the boundary group, the management point returns distribution points in the following order:

1. Current boundary group
2. Neighbor boundary groups
3. The site default boundary group

Note

The client setup process doesn't use the fallback time. To locate content as quickly as possible, it immediately falls back to the next boundary group.

In previous versions of Configuration Manager, during this process the management point only returned distribution points in the client's current boundary group. If no content was available, the setup process fell back to download content from the management point. There was no option to fall back to distribution points in other boundary groups that might have the necessary content.

## Task sequence support

When a device runs a task sequence and needs to acquire content, it uses boundary group behaviors similar to the Configuration Manager client.

Configure this behavior using the following settings on the **Distribution Points** page of the task sequence deployment:

- **When no local distribution point is available, use a remote distribution point**: For this deployment, the task sequence can fall back to distribution points in a neighbor boundary group.
- **Allow clients to use distribution points from the default site boundary group**: For this deployment, the task sequence can fall back to distribution points in the default site boundary group.

To use this new behavior, make sure to update clients to the latest version.

### Location priority

The task sequence tries to acquire content in the following order:

1. Peer cache sources
2. Distribution points in the *current* boundary group
3. Distribution points in a *neighbor* boundary group

    Important

    Due to the real-time nature of task sequence processing, it doesn't wait for the failover time on a neighbor boundary group. It uses the failover times for prioritizing the neighbor boundary groups. For example, if the task sequence fails to acquire content from a distribution point in its current boundary group, it immediately tries a distribution point in a neighbor boundary group with the shortest failover time. If that process fails, it then fails over to a distribution point in a neighbor boundary group with a larger failover time.

    For content like applications and software updates, which are downloaded by the client and not the task sequence engine, the client behaves as normal. In other words, if you install applications or software updates from a task sequence, when the client tries to download the content it will wait for boundary group failover.
4. Distribution points in the *site default* boundary group

The task sequence log file **smsts.log** shows the priority of the location sources that it uses based on the deployment properties.