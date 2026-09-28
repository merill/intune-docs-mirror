---
layout: Conceptual
title: Interpret Bitfield Properties - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/interpreting-bitfield-properties
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
description: Some SMS object properties are implemented as bit fields, where individual binary bits of an integer (usually a **uint32** data type) are used as Boolean flags to store information. These properties can be difficult to interpret at the user interface because the bit field is often displayed as a decimal number.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: a35355f9-3782-f2d0-76e1-25a9ab989434
document_version_independent_id: 9c7fe5d6-62d3-83da-f4b5-53aee38ebd34
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/interpreting-bitfield-properties.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/interpreting-bitfield-properties
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/interpreting-bitfield-properties.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 83c3fda1-e8d8-cdb8-cf43-e5dffaf06fb3
---

# Interpret Bitfield Properties - Configuration Manager | Microsoft Learn

Some SMS object properties are implemented as bit fields, where individual binary bits of an integer (usually a **uint32** data type) are used as Boolean flags to store information. These properties can be difficult to interpret at the user interface because the bit field is often displayed as a decimal number.

For example, the Security User Class Permissions object (**SMS\_UserClassPermissions**) contains an integer property called **ClassPermissions**, which is defined as an **int32** data type with the following bit flags:

| Bit | Flag |
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

The difficulty arises when the binary number 10100000111 appears as the decimal number 1287 in an SMS Administrator console display and how you interpret the bits. The solution is to open the Windows Calculator application (Calc.exe, in the Accessories group). Use the Scientific view, set the calculator for decimal mode, and enter 1287. Use the radio buttons of the calculator to convert to a binary display. The binary bit field 10100000111 appears. You can read the selected bit flags from this display.

Note

In a typical bit field property, many of the bits are unused and have no defined meaning.