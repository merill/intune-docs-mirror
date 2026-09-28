---
layout: Conceptual
title: SoftDistProgramCompletedSuccessfullyEvent - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/softdistprogramcompletedsuccessfullyevent
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
description: Learn how to update the Advertisement Status in Configuration Manager console using SoftDistProgramCompletedSuccessfullyEvent message.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 561c21ce-c93b-36c9-d173-d0f35a91c845
document_version_independent_id: 38e14f23-5dbc-a165-4f39-60b55fb80ab6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/softdistprogramcompletedsuccessfullyevent.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/softdistprogramcompletedsuccessfullyevent
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/softdistprogramcompletedsuccessfullyevent.md
cmProducts: []
platformId: fa7bbb8c-a64e-9a67-5c26-cc3ce42627cf
---

# SoftDistProgramCompletedSuccessfullyEvent - Configuration Manager | Microsoft Learn

The `SoftDistProgramCompletedSuccessfullyEvent` message, in Configuration Manager, is sent when a program is completed successfully with an exit code (not MIFsuccess). It appears in the **Advertisement Status** in the Configuration Manager console.

This class is derived from the [SMS_SofwareDistribution_Event](sms_sofwaredistribution_event) class, and each base class property must be set.

## Properties

`AdvertisementId` Data type: `String`

Derived from `SMS_SoftwareDistribution_Event`.

`DummyString2` Data type: `String`

This property does not have to be set.

`DummyString2` Data type: `String`

This property does not have to be set.

`DummyString3` Data type: `String`

This property does not have to be set.

`DummyString6` Data type: `String`

This property does not have to be set.

`DummyString7` Data type: `String`

This property does not have to be set.

`DummyString8` Data type: `String`

This property does not have to be set.

`PackageName` Data type: `String`

Derived from `SMS_SoftwareDistribution_Event`.

`ProgramName` Data type: `String`

Derived from `SMS_SoftwareDistribution_Event`.

`UserContext` Data type: `String`

This property does not have to be set.