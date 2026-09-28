---
layout: Conceptual
title: Boundaries and boundary groups - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups
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
description: Use boundaries and boundary groups to define network locations for clients and site systems in your environment.
ms.date: 2021-08-02T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection: tier3
locale: en-us
document_id: ffb91cfb-5738-55a8-25d9-e922320cb53d
document_version_independent_id: c84d8b17-2aa6-a3f8-279f-6a4b95997274
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: da073747-3e92-05bb-660c-99eec1697342
---

# Boundaries and boundary groups - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

*Boundaries* in Configuration Manager define network locations on your intranet. These locations include devices that you want to manage. *Boundary groups* are logical groups of boundaries that you configure. A hierarchy can include any number of boundary groups. Each boundary group can contain any combination of the following boundary types:

- IP subnet
- Active Directory site name
- IPv6 prefix
- IP address range
- VPN (starting in version 2006)

Clients on the intranet evaluate their current network location and then use that information to identify boundary groups to which they belong.

Clients use boundary groups to:

- Find an assigned site: Boundary groups enable clients to find a primary site for client assignment. This behavior is also known as *automatic site assignment*.
- Find certain site system roles they can use: Associate a boundary group with certain site system roles. Then the site provides clients with that list of site systems in the boundary group. Clients use these site systems for actions such as finding content or a nearby management point.

Clients that are on the internet or configured as internet-only clients don't use boundary information. These clients can't use automatic site assignment. They can download content from an internet-based distribution point from their assigned site or a content-enabled cloud management gateway.

During OS deployment, while a device is running Windows PE, the site can convert Active Directory site boundary information to IP subnet information. This behavior is only during this process, and specifically for these devices. In other words, if your site only has Active Directory site boundaries, Windows PE clients during an OS deployment will still be in a boundary.

## Overlapping boundaries

Configuration Manager supports overlapping boundary and boundary group configurations for content and service location requests. Overlapping occurs when a client's location maps to multiple boundary groups. This behavior happens for one of two reasons:

- You add the same boundary to multiple boundary groups.
- You add separate boundaries that include the client's location to different boundary groups.

When overlapping occurs, Configuration Manager creates a list of all site systems referenced by all boundary groups that include a client's location. Configuration Manager sends this list to a client in response to a content or service location request. Configuration Manager doesn't apply any precedence or deterministic ordering to this list based on overlapping boundaries and boundary groups. Instead, the client chooses at random from this list.

For client content requests, Configuration Manager includes only distribution points that have the requested content in the list of site systems returned. For other service location requests, Configuration Manager includes only site systems that host the type of role requested which may be one of the following roles:

- State migration point
- Software update point
- Management point

This behavior enables the client to select the nearest server to communicate with for each request type.

## Recommendations

### Use a mix of the fewest boundaries that meet your needs

Use whichever boundary type or types you choose that work for your environment. To simplify your management tasks, use boundary types that let you use the fewest number of boundaries you can.

### Avoid overlapping boundaries for automatic site assignment

Although each boundary group supports both site assignment and site system reference, create a separate set of boundary groups to use only for site assignment. Make sure that each boundary in a boundary group isn't a member of another boundary group with a different site assignment.

- A single boundary can be included in multiple boundary groups.
- Each boundary group can be associated with a different primary site for site assignment.
- For a boundary that's a member of two different boundary groups with different site assignments, clients randomly select a site to join. This behavior might not be for the site you want the client to join. This configuration is called *overlapping boundaries*.

    Overlapping boundaries aren't a problem for content location. It can be a useful configuration that provides clients more resources or content locations they can use.

For more information on boundary groups and site assignment, see [Site assignment](boundary-groups#site-assignment).