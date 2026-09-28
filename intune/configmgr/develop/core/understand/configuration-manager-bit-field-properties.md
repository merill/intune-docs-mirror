---
layout: Conceptual
title: Bit Field Properties - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-bit-field-properties
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
description: Some Configuration Manager object properties are implemented as bit fields, where individual binary bits of an integer (usually a uint32 data type) are used as Boolean flags to store information
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 50204960-85ca-3eb5-5370-74b407f97951
document_version_independent_id: 3a619dce-c20e-0807-3349-41806cad97dc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/configuration-manager-bit-field-properties.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/configuration-manager-bit-field-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/configuration-manager-bit-field-properties.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 559c4941-8477-ce7a-2ddc-b263a8f4af80
---

# Bit Field Properties - Configuration Manager | Microsoft Learn

Some Configuration Manager object properties are implemented as bit fields, where individual binary bits of an integer (usually a `uint32` data type) are used as `Boolean` flags to store information. These properties can be difficult to interpret at the user interface because the bit field is often displayed as a decimal number.

For example, the Security User Class Permissions object (`SMS_UserClassPermissions`) contains an integer property called `ClassPermissions`, which is defined as an `int32` data type with the following bit flags:

| Bit | Value |
| --- | --- |
| 0 | READ |
| 1 | MODIFY |
| 2 | DELETE |
| 3 | DISTRIBUTE |
| 4 | CREATE\_CHILD |
| 5 | REMOTE\_CONTROL |
| 6 | ADVERTISE |
| 7 | MODIFY\_RESOURCE |
| 8 | ADMINISTER |
| 9 | DELETE\_RESOURCE |
| 10 | CREATE |
| 11 | VIEW\_COLL\_FILE |
| 12 | READ\_RESOURCE |
| 13 | DELEGATE |
| 14 | METER |
| 15 | MANAGESQLCOMMAND |
| 16 | MANAGESTATUSFILTER |

A typical value of this bit field might be 10100000111. Bit 0 is the least significant bit (on the right) and the other bits are counted right to left. Therefore, in this example, the available class permissions include READ, MODIFY, DELETE, ADMINISTER, and CREATE, corresponding to bit fields 0, 1, 2, 8, and 10, respectively.

The difficulty arises when the binary number 10100000111 appears as the decimal number 1287 in a Configuration Manager console display and in how you interpret the bits. The solution is to open the Windows Calculator application (Calc.exe, in the Accessories group). Use the Scientific view, set the calculator for decimal mode, and enter 1287. Use the radio buttons of the calculator to convert to a binary display. The binary bit field 10100000111 appears. You can read the selected bit flags from this display.

Note

In a typical bit field property, many of the bits are unused and have no defined meaning.