---
layout: Conceptual
title: Configuration Manager SEDO - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sedo
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
ms.date: 2016-09-20T00:00:00.0000000Z
description: SEDO in SDK provides a mechanism for assigning and unassigning locks to globally replicated SDK provider objects in the context of a site, computer, and user.
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 2d5d0301-a02b-0f4d-85c9-170416037289
document_version_independent_id: 24226f31-6fc2-b361-edf2-7892761a046d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sedo.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sedo
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sedo.md
cmProducts: []
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 10cdb22c-207d-55f6-d693-9bff94444347
---

# Configuration Manager SEDO - Configuration Manager | Microsoft Learn

Configuration Manager SEDO (Serialized Editing of Distributed Objects) in the Configuration Manager SDK provides a mechanism for assigning and unassigning locks to globally replicated SDK provider objects in the context of a site, computer and user. SEDO-enabled objects are globally replicated SDK provider objects that require the user to obtain a lock if that user wishes to edit and save that object. When the user obtains that lock, the lock will be assigned to that user, the user's computer and the site in which the computer resides. While that lock is assigned, no other user or computer will be able to edit that object until the user releases the lock.

Only SEDO-enabled objects require users to obtain a lock before editing them. The SEDO-enabled objects are the following:

- SMS\_Application
- SMS\_AuthorizationList
- SMS\_BootImagePackage
- SMS\_ConfigurationBaselineInfo
- SMS\_ConfigurationItem
- SMS\_DeploymentType
- SMS\_Driver
- SMS\_DriverPackage
- SMS\_GlobalCondition
- SMS\_ImagePackage
- SMS\_OperatingSystemInstallPackage
- SMS\_Package
- SMS\_SoftwareUpdatesPackage
- SMS\_TaskSequencePackage

## Implicit and Explicit Lock Requests

To prevent SEDO from breaking current SDK application functionalities, SEDO supports both implicit and explicit lock requests. In the case of implicit requests, if the lock is already assigned to the local site and the user attempts to edit a SEDO-enabled object, then SEDO will automatically attempt to retrieve the lock. If SEDO succeeds in obtaining the lock from the local site and the user edits the object, then that object will be saved at the user's request, without having to make an explicit programmatic lock request.

However, if the lock is not assigned to the local site and a transfer of the lock from another site must be requested, a request must be sent to the remote site that contains the lock. This request must be made explicitly by the user.

For more information, and to learn how to explicitly request a lock, see [How to Acquire a Lock on a SEDO-Enabled Object](how-to-acquire-a-lock-on-a-sedo-enabled-object).

## Implicit and Explicit Lock Releases

SEDO also supports both implicit and explicit lock releases. In the case of implicit releases, when a user saves an object using a `Put()` method, SEDO will attempt to automatically release the lock. Otherwise, the release must be explicitly made.

To learn how to explicitly and implicitly release a lock, see [How to Release a Lock on a SEDO-Enabled Object](how-to-release-a-lock-on-a-sedo-enabled-object).