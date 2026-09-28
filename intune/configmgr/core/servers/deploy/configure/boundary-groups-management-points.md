---
layout: Conceptual
title: Boundary groups and management points - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/boundary-groups-management-points
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
description: Understand how clients and management points behave with boundary groups.
ms.date: 2022-02-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: bc8d5fef-875f-a9cc-d11f-1a14c0659540
document_version_independent_id: 421d7d3f-26f4-1552-4000-95d8ead24480
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/boundary-groups-management-points.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/boundary-groups-management-points
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/boundary-groups-management-points.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 0830ef00-590b-9281-0378-ba64b071cfd8
---

# Boundary groups and management points - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Configure fallback relationships for management points between boundary groups. This behavior provides greater control for the management points that clients use. On the **Relationships** tab of the boundary group properties, there's a column for management point. When you add a new fallback boundary group, the fallback time for the management point is currently always zero (0). This behavior is the same for the **Default Behavior** on the site default boundary group.

Previously, a common problem occurred when you had a protected management point in a secure network. Clients on the main network received policy that included this protected management point, even though they couldn't communicate with it across a firewall. To address this problem now, use the **Never fallback** option to make sure that clients only fall back to management points with which they can communicate.

Note

If you enable distribution points in the site default boundary group to fallback, and a management point is collocated on a distribution point, the site also adds that management point to the site default boundary group.

If a client is in a boundary group with no assigned management point, the site gives the client the entire list of management points. This behavior makes sure that a client always receives a list of management points.

Tip

If you enable the option to **Prefer cloud-based sources over on-premises sources** then clients will prefer a cloud management gateway (CMG) for both policy and content.

Management point boundary group fallback doesn't change the behavior during client installation (ccmsetup.exe). If the command line doesn't specify the initial management point using the `/MP` parameter, the new client receives the full list of available management points. For its initial bootstrap process, the client uses the first management point it can access. Once the client registers with the site, it receives the management point list properly sorted with this new behavior.

For more information on the client's behavior to acquire content during installation, see [Client installation](boundary-groups-distribution-points#client-installation).

During client upgrade, if you don't specify the `/MP` command-line parameter, the client queries sources such as Active Directory and WMI for any available management point. Client upgrade doesn't honor the boundary group configuration. 

For clients to use this capability, enable the following setting: **Clients prefer to use management points specified in boundary groups** in **Hierarchy Settings**.

Note

OS deployment processes aren't aware of boundary groups for management points.

## Troubleshoot

New entries appear in the **LocationServices.log**. The **Locality** attribute identifies one of the following states:

- **0**: Unknown
- **1**: The specified management point is only in the site default boundary group for fallback.
- **2**: The specified management point is in a remote or neighbor boundary group. When the management point is in both a neighbor and the site default boundary groups, the locality is 2.
- **3**: The specified management point is in the local or current boundary group. When the management point is in the current boundary group and either a neighbor or the site default boundary group, the locality is 3. If you don't enable the preferred management points setting in Hierarchy Settings, the locality is always 3 no matter which boundary group the management point is in.

Clients use local management points first (locality 3), remote second (locality 2), then fallback (locality 1).

When a client receives five errors in 10 minutes and fails to communicate with a management point in its current boundary group, it tries to contact a management point in a neighbor or the site default boundary group. If the management point in the current boundary group later comes back online, the client returns to the local management point on the next refresh cycle. The refresh cycle is 24 hours, or when the Configuration Manager agent service restarts.

## Preferred management points

Note

When you enable **Clients prefer to use management points specified in boundary groups**, Configuration Manager uses the boundary group functionality for the assigned management point.

Preferred management points enable a client to identify a management point that's associated with its current network location (boundary).

- A client tries to use a preferred management point from its assigned site before using one not configured as preferred from its assigned site.
- To use this option, enable **Clients prefer to use management points specified in boundary groups** in **Hierarchy Settings**. Then configure boundary groups at individual primary sites. Include the management points that should be associated with that boundary group's associated boundaries. For more information, see [Enable use of preferred management points](boundary-group-procedures#enable-use-of-preferred-management-points).
- When you configure preferred management points, and a client organizes its list of management points, the client places the preferred management points at the top of its list. This list includes all management points from the client's assigned site.

Note

Client roaming means it changes its network locations. For example, when a laptop travels to a remote office location. When a client roams, it might use a management point from the local site before attempting to use a server from its assigned site. This list of servers from its assigned site includes the preferred management points. For more information, see [Understand how clients find site resources and services](../../../plan-design/hierarchy/understand-how-clients-find-site-resources-and-services).