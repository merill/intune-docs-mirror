---
layout: Conceptual
title: Association Classes - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/association-classes
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
description: An association allows you to logically relate the instances of two classes. An association consists of two key properties which are paths or pointers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 12f1cbdd-9938-0248-8d61-cccf49865bff
document_version_independent_id: 14abd6c3-4a2a-0cee-67b9-7a6027676558
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/association-classes.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/association-classes
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/association-classes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 5c99c81a-02a0-bd27-a5c6-f5258d37b26d
---

# Association Classes - Configuration Manager | Microsoft Learn

In Configuration Manager, an association allows you to logically relate the instances of two classes. Typically, an association consists of two key properties (which are paths, or pointers, that uniquely identify the location of the other class instances), but an association can also contain additional properties. The provider uses the key properties to retrieve the requested data.

Although association classes provide a convenient means to collect related information, they are inherently slow. If performance is an issue, you should consider collecting the related information yourself.

Note

Association classes are read-only except for the `SMS_CollectToSubCollect_a` class. Association class names are suffixed with \_a.

The following table shows the association classes.

| Association class | Description |
| --- | --- |
| `SMS_AdvertToSourceSite_a` | Relates an advertisement with the site that created the advertisement. |
| `SMS_BaseAssociation` | An abstract class that is the base class for all Configuration Manager association classes. It has no properties. |
| `SMS_CollectionMember_a` | Relates a collection with its member resources. |
| `SMS_CollectionToPkgAdvert_a` | Relates an advertisement with its target collection. |
| `SMS_CollectToSubCollect_a` | Relates a collection with its parent collection. |
| `SMS_ObjectToClassPermissions_a` | Relates a secured object with various users that have class permissions on the object. |
| `SMS_ObjectToInstancePermissions_a` | Relates a secured object with users that have permissions for an instance of a secured object. |
| `SMS_PackageToAdvert_a` | Relates an advertisement to the package it advertises. |
| `SMS_PackageToSourceSite_a` | Relates a package to the site that created the package. |
| `SMS_PDFPkgToPDFProgram_a` | Relates a package definition file package to package definition file programs that are part of the package. |
| `SMS_PkgToPkgAccess_a` | Relates a package with the user accounts that are used to access a package on its distribution points. |
| `SMS_PkgToPkgProgram_a` | Relates a package with the programs that form the package. |
| `SMS_PkgToPkgServer_a` | Relates a package with its distribution points. |
| `SMS_SCFToSCI_a` | Relates a site control file with the site control items that make up the current site control file. |
| `SMS_SCFToSite_a` | Relates a site control file with the site to which it belongs. |
| `SMS_SiteToROOTColl_a` | Relates a site with the root of the collections that belong to it. |
| `SMS_SiteToSiteID_a` | Relates a site with its identifying information. |
| `SMS_SiteToSubSite_a` | Defines the hierarchy of sites by relating a site with its subsites. |