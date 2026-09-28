---
layout: Conceptual
title: Configure clients to use DNS publishing - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/configure-client-computers-to-find-management-points-by-using-dns-publishing
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
description: Configure Configuration Manager client computers to find management points by using DNS publishing.
ms.date: 2017-04-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 66c55d8d-6ec7-5353-2be8-800a07e2e852
document_version_independent_id: 748be005-0abe-eeb6-c7c6-fad151b4f78f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/configure-client-computers-to-find-management-points-by-using-dns-publishing.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/configure-client-computers-to-find-management-points-by-using-dns-publishing
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/configure-client-computers-to-find-management-points-by-using-dns-publishing.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 6481ef00-e351-9b6b-21cf-d0e4291a1991
---

# Configure clients to use DNS publishing - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Clients in Configuration Manager must locate a management point to complete site assignment and as an on-going process to remain managed. Active Directory Domain Services provides the most secure method for clients on the intranet to find management points. However, if clients cannot use this service location method (for example, you have not extended the Active Directory schema, or clients are from a workgroup), use DNS publishing as the preferred alternative service location method.

Before you use DNS publishing for management points, make sure that DNS servers on the intranet have service location resource records (SRV RR) and corresponding host (A or AAA) resource records for the site's management points. The service location resource records can be created automatically by Configuration Manager or manually, by the DNS administrator who creates the records in DNS.

For more information about DNS publishing as a service location method for Configuration Manager clients, see [Understand how clients find site resources and services for Configuration Manager](../../plan-design/hierarchy/understand-how-clients-find-site-resources-and-services).

By default, clients search DNS for management points in their DNS domain. However, if there are no management points published in the clients' domain, you must manually configure clients with a management point DNS suffix. You can configure this DNS suffix on clients either during or after client installation:

- To configure clients for a management point suffix during client installation, configure the CCMSetup Client.msi properties.
- To configure clients for a management point suffix after client installation, in Control Panel, configure the **Configuration Manager Properties**.

#### To configure clients for a management point suffix during client installation

- Install the client with the following CCMSetup Client.msi property:

    - **DNSSUFFIX=***&lt;management point domain&gt;*

        If the site has more than one management point and they are in more than one domain, specify just one domain. When clients connect to a management point in this domain, they download a list of available management points, which will include the management points from the other domains.

        For more information about the CCMSetup command-line properties, see [About client installation properties](about-client-installation-properties).

#### To configure clients for a management point suffix after client installation

1. In Control Panel of the client computer, navigate to **Configuration Manager**, and then double-click **Properties**.
2. On the **Site** tab, specify the DNS suffix of a management point, and then click **OK**.

    If the site has more than one management point and they are in more than one domain, specify just one domain. When clients connect to a management point in this domain, they download a list of available management points, which will include the management points from the other domains.