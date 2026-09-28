---
layout: Conceptual
title: SoftwareDistributionPackageEvent - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/softwaredistributionpackageevent
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
description: Learn how to set the base class for all software distribution package related status messages using SoftWareDistributionPackageEvent.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: afe61492-a902-ffbd-4562-0fd89e3e481b
document_version_independent_id: ce12c006-621c-35af-8d77-c2b8846058d6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/softwaredistributionpackageevent.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/softwaredistributionpackageevent
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/softwaredistributionpackageevent.md
cmProducts: []
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/81a11282-2f1c-4a63-95c5-6e6f262fea55
platformId: 0d86d4a2-b8f5-1a32-0750-1d9239dce647
---

# SoftwareDistributionPackageEvent - Configuration Manager | Microsoft Learn

In Configuration Manager, the `SoftwareDistributionPackageEvent` class is the base class for all software distribution-package-related status messages. Every status message has its own class that is derived from `SoftwareDistributionPackageEvent`; and therefore, all package status messages have the insertion strings of this class. Each status message that is derived from this class must set the base class `SoftwareDistributionPackageEvent` properties.

## Properties

`ClientID` Data type: `String`

The SMS identifier of the client raising this event.

`PackageId` Data type: `String`

The Package ID of the package to which status message refers. It maps to the `PKG_PackageID` field in the software distribution policy and to the **Package ID** in the Configuration Manager console.

`PackageName` Data type: `String`

The Package ID, but it is an insertion string that appears in the status message text. It maps to the `PKG_PackageID` field in the software distribution policy and to the **Package ID** in the Configuration Manager console. This is insertion string number 4.

`PackageVersion` Data type: `String`

The package version. It is the value that appears in the status message text. It is not the value that is specified in the Configuration Manager console. It maps to `PKG_SourceVersion` field in the software distribution policy. This is insertion string number 2.