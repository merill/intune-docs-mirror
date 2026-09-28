---
layout: Conceptual
title: Procedures for boundary groups - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/boundary-group-procedures
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
description: Configure boundary groups to logically organize related network locations called boundaries.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 4f3fbc0b-ca7c-ff7b-c9c3-768dc85308d4
document_version_independent_id: a55825e1-d871-5e62-5323-fe6e7908cab6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/boundary-group-procedures.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/boundary-group-procedures
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/boundary-group-procedures.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 47d9d92a-0c0c-9640-238c-0113a4393ec6
---

# Procedures for boundary groups - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article includes procedures on how to view and configure boundary groups. Before you begin, make sure you understand boundary group concepts. For more information, see [Boundary groups](boundary-groups).

## Show boundary groups for devices

To help you better identify and troubleshoot device behaviors with boundary groups, you can view the boundary groups for specific devices. In the **Devices** node or when you show the members of a **Device Collection**, add the **Boundary Group(s)** column to the list view.

- If a device is in more than one boundary group, the value is a comma-separated list of boundary group names.
- The data updates when the client makes a location request to the site, or at most every 24 hours.
- If a client is roaming and not a member of a boundary group, the value is blank.

Note

This information is site data and only available on primary sites. You won't see a value for this column when you connect the Configuration Manager to a central administration site (CAS). For more information, see [Types of data](../../../plan-design/hierarchy/database-replication#types-of-data).

## Create a boundary group

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Hierarchy Configuration**, and select the **Boundary Groups** node.
2. On the **Home** tab, in the **Create** group, select **Create Boundary Group**.
3. In the **Create Boundary Group** dialog box, on the **General** tab, specify a **Name** for this boundary group. Optionally include a **Description**.
4. Select **OK** to save the new boundary group, or continue to the next section to configure the boundary group.

## Configure a boundary group

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Hierarchy Configuration**, and select the **Boundary Groups** node.
2. Select the boundary group you want to modify, and select **Properties** in the ribbon. This action opens the boundary group Properties window.

Configure the following settings:

- Add or remove boundaries
- Configure site assignment and select site system servers
- Configure fallback behavior
- Configure boundary group options

### Add or remove boundaries

In the boundary group Properties window, use the **General** tab to modify the boundaries that are members of this boundary group:

- To add boundaries, select **Add**. In the Add Boundaries window, select the check box for one or more boundaries, and select **OK**.
- To remove boundaries, select the boundary in the list, and select **Remove**.

### Configure site assignment and select site system servers

To modify the site assignment and associated site system server configuration, switch to the **References** tab in the boundary group Properties window.

- To enable this boundary group for use by clients for site assignment, select **Use this boundary group for site assignment**. Then select a site from the **Assigned site** dropdown list. For more information, see [Site assignment](boundary-groups#site-assignment).
- To associate available site system servers with this boundary group, select **Add**. The Add Site Systems window only lists servers that have supported site system roles. Select the check box for one or more servers, and select **OK**. It adds them as associated site system servers for this boundary group.

    Note

    You can select any combination of available site systems from any site in the hierarchy. Selected site systems are listed on the **Site Systems** tab in the properties of each boundary that's a member of this boundary group.
- To remove a server from this boundary group, select the server and then select **Remove**.

    Note

    To stop use of this boundary group for associating site systems, remove all servers listed as associated site system servers.

### Configure fallback behavior

To configure fallback behavior, switch to the **Relationships** tab in the boundary group Properties window.

- To create a relationship with another boundary group:

    - Select **Add**. In the Fallback Boundary Groups window, select the boundary group to configure.
    - Set a fallback time for the following site system roles:

        - Distribution point
        - Software update point
        - Management point

            Note

            For example, you open the Properties window for the Branch Office boundary group. In the Fallback Boundary Groups window, you select the Main Office boundary group. You set the distribution point fallback time to `20`. When you save this configuration, clients in the Branch Office boundary group will start searching for content from the distribution points in the Main Office boundary group after 20 minutes.
    - To prevent fallback to a specific boundary group, select the boundary group, and then select **Never fallback** for the type of site system role. This action can include the *default site boundary group*.
- To modify the configuration of an existing relationship, select the boundary group in the list, and select **Change**. This action opens the Fallback Boundary Groups window for just this boundary group.
- To remove a relationship, select the boundary group in the list, and select **Remove**.

For more information, see [Fallback](boundary-groups#fallback).

### Configure boundary group options

To configure options for clients in this boundary group, switch to the **Options** tab. For more information, see [Boundary group options](boundary-group-options).

- **Allow peer downloads in this boundary group**: This option is enabled by default. The management point provides clients a list of content locations that includes peer sources.

    - **During peer downloads, only use peers within the same subnet**: This setting is dependent upon the one above. If you enable this option, the management point only includes in the content location list peer sources that are in the same subnet as the client.
    - **Prefer distribution points over peers within the same subnet**: By default, the management point prioritizes peer cache sources at the top of the list of content locations. This setting reverses that priority for clients in the same subnet as a peer cache source.
- **Prefer cloud based sources over on-premises sources**: A common scenario is if you have a branch office with a faster internet link, you can prioritize cloud content and policy. This behavior includes cloud management gateways (CMG) or Microsoft Update.

    Note

    Starting in version 2203, this setting also applies for software update scanning. To reduce the performance impact of this change, existing clients don't automatically switch to a cloud-based software update point. For more information, see [Boundary groups and software update points](boundary-groups-software-update-points#bkmk_prefer_cmgsup).

## Configure a fallback site for automatic site assignment

If clients aren't in a boundary group with an assigned site, assign them to this site when they're installed.

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Sites** node.
2. On the **Home** tab of the ribbon, in the **Sites** group, select **Hierarchy Settings**.
3. On the **General** tab, select the checkbox to **Use a fallback site**. Then select a site from the **Fallback site** drop-down list.
4. Select **OK** to save the configuration.

For more information, see [Site assignment](boundary-groups#site-assignment).

## Enable use of preferred management points

For more information, see [Preferred management points](boundary-groups-management-points#preferred-management-points).

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Site Configuration**, and select the **Sites** node.
2. On the **Home** tab of the ribbon, in the **Sites** group, select **Hierarchy Settings**.
3. On the **General** tab, select **Clients prefer to use management points specified in boundary groups**.
4. Select **OK** to save the configuration.