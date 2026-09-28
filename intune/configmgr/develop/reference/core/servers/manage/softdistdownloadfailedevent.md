---
layout: Conceptual
title: SoftDistDownloadFailedEvent - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/softdistdownloadfailedevent
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
description: In Configuration Manager, the SoftDistDownloadFailedEvent message is raised when a download for a package fails. It appears in Package Status in the Configuration Manager console.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: b88150f3-f314-e071-9d28-4a2e974d07f3
document_version_independent_id: 7e19505f-bcc5-bd3c-d44b-f699b02551b6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/softdistdownloadfailedevent.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/softdistdownloadfailedevent
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/softdistdownloadfailedevent.md
cmProducts: []
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/81a11282-2f1c-4a63-95c5-6e6f262fea55
platformId: 7831e2eb-caad-3f7f-6201-96ff987a844c
---

# SoftDistDownloadFailedEvent - Configuration Manager | Microsoft Learn

In Configuration Manager, the `SoftDistDownloadFailedEvent` message is raised when a download for a package fails. It appears in **Package Status** in the Configuration Manager console.

`SoftDistDownloadFailedEvent` is derived from the [SoftwareDistributionPackageEvent](softwaredistributionpackageevent) class, and each base class property must be set.

The text of the status message is:

%11Content download for the package "%4" - "%2" has failed.%12.%nPossible cause: The content can't be found on the network, or the content couldn't be accessed. %nSolution: Check to ensure this content has been made available on a distribution point. Check to ensure the access control list allows this program to be accessed. Check to make sure that the file system path for the content, including the path to the cache directory, isn't greater than 255 characters.%0.

## Properties

`ClientID` Data type: `String`

The SMS identifier of the client raising this event.

`PackageId` Data type: `String`

The Package ID of the package to which status message refers. It maps to the `PKG_PackageID` field in the software distribution policy and to the **Package ID** in the Configuration Manager console.

`PackageName` Data type: `String`

The Package ID, but it's an insertion string that appears in the status message text. It maps to the `PKG_PackageID` field in the software distribution policy and to the **Package ID** in the Configuration Manager console. This is insertion string number 4.

`PackageVersion` Data type: `String`

The package version. It's the value that appears in the status message text. It isn't the value that is specified in the Configuration Manager console. It maps to `PKG_SourceVersion` field in the software distribution policy. This is insertion string number 2.

`Severity` Data type: `Int32`

The severity of the failed event. The default value is 2.