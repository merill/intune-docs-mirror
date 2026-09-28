---
layout: Conceptual
title: SMS_SofwareDistribution_Event - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/servers/manage/sms_sofwaredistribution_event
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
description: Learn how to use the SMS_SofwareDistribution_Event class to create other advertisement status-message classes.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: f69ff7c1-0da3-66bd-495b-9547cca84b8e
document_version_independent_id: 3cb2f021-3aa6-346c-e5d2-975f300bca7c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/servers/manage/sms_sofwaredistribution_event.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/servers/manage/sms_sofwaredistribution_event
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/servers/manage/sms_sofwaredistribution_event.md
cmProducts: []
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/81a11282-2f1c-4a63-95c5-6e6f262fea55
platformId: e6cbc00d-59b0-db92-0297-949aa2bdd63e
---

# SMS_SofwareDistribution_Event - Configuration Manager | Microsoft Learn

The `SMS_SofwareDistribution_Event` class is the base class for all software-distribution advertisement status-message classes, in Configuration Manager. All advertisement status messages have the insertion strings of this class. Also, each derived class must set the properties of its base `SMS_SofwareDistribution_Event` class.

Note

The misspelling of software in `SMS_SofwareDistribution_Event` in this documentation is intentional as the implementation of the class is misspelled.

## Properties

`AdvertisementId` Data type: `String`

The Advertisement ID of the advertisement that the status message refers to. It appears in the status message text. It maps to the `ADV_AdvertisementID` field in the software distribution policy and to the Advertisement ID in the Configuration Manager console. This is insertion string number 1.

`ClientID` Data type: `String`

The SMS identifier of the client raising this event.

`PackageName` Data type: `String`

The Package ID that appears in the status message text. It maps to the `PKG_PackageID` field in the software distribution policy and to the Package ID in the Configuration Manager console. This is insertion string number 4.

`ProgramName` Data type: `String`

The Program Name that appears in the status message text. It maps to the `PRG_ProgramName` field in the software distribution policy and is the program name that was chosen when the program was created. This is insertion string number 5.