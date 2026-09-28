---
layout: Conceptual
title: Example validation state transitions - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/example-validation-state-transitions-for-asset-intelligence
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
description: See examples of validation state transitions for Asset Intelligence in Configuration Manager.
ms.date: 2017-02-22T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 564cf534-81a6-bdf2-8e9f-8ca09ace2487
document_version_independent_id: 19943b9c-0882-5d16-582a-a7b4e512ffdf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/asset-intelligence/example-validation-state-transitions-for-asset-intelligence.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/asset-intelligence/example-validation-state-transitions-for-asset-intelligence
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/asset-intelligence/example-validation-state-transitions-for-asset-intelligence.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: 75186890-f5e7-1d3f-a45d-8794b2feb5d2
---

# Example validation state transitions - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Asset Intelligence validation states in Configuration Manager aren't static and can change from administrative actions that you take to affect the data that are stored in the Asset Intelligence catalog. This topic provides examples for possible validation state transitions.

## Uncategorized catalog item is categorized by the administrative user

| **State transition** | **State transition description** |
| --- | --- |
| **Uncategorized** | An inventoried software title that hasn't been previously categorized by System Center Online or that the administrative user has entered into the Asset Intelligence catalog. |
| **Uncategorized** to **UserDefined** | The uncategorized item is categorized by the administrative user. |

## Categorized catalog item is recategorized by the administrative user

| **State transition** | **State transition description** |
| --- | --- |
| **Validated** | Catalog item has been defined by System Center Online researchers and is present in the Asset Intelligence catalog. |
| **Validated** to **User Defined** | The validated catalog item is re-categorized by the administrative user. |

Note

Because categorization information obtained from System Center Online is stored in the database and cannot be deleted, the administrative user can revert back to the System Center Online categorization later.

## User-defined catalog item is recategorized by System Center Online

| **State transition** | **State transition description** |
| --- | --- |
| **Uncategorized** | An inventoried software title is entered into the Asset Intelligence catalog that hasn't been previously categorized by System Center Online or the administrative user. |
| **User Defined** | The uncategorized item is categorized by the administrative user. |
| **User Defined** to **Updateable** | A user-defined catalog item has been categorized differently by System Center Online during subsequent manual bulk updates of the Asset Intelligence catalog. The administrative user can use the **Software Details Conflict Resolution** dialog box to decide whether to use the new categorization information or the previous user-defined value. |
| **Updateable** to **Validated** | The administrative user uses the **Software Details Conflict Resolution** dialog box to use the new categorization information received from System Center Online during the previous catalog update. |
| or |  |
| **Updateable** to **User Defined** | The administrative user uses the **Software Details Conflict Resolution** dialog box to use the previous user-defined value. |

Note

Because categorization information obtained from System Center Online is stored in the database and cannot be deleted, the administrative user can revert back to the System Center Online categorization later.

## Uncategorized catalog item is submitted to System Center Online for categorization

| **State transition** | **State transition description** |
| --- | --- |
| **Uncategorized** | An inventoried software title is entered into the Asset Intelligence database that hasn't been previously categorized by System Center Online or the administrative user. |
| **Uncategorized** to **Pending** | The uncategorized item is submitted to System Center Online for categorization by the administrative user. |
| **Pending** to **Validated** | The item is categorized by System Center Online. The administrative user imports the item into the Asset Intelligence catalog by using a bulk catalog update or Asset Intelligence catalog synchronization. Both are available by using the Asset Intelligence synchronization point site system role. |

## User-defined catalog item is submitted to System Center Online for categorization

| **State transition** | **State transition description** |
| --- | --- |
| **Uncategorized** | An inventoried software title is entered into the Asset Intelligence database that hasn't been previously categorized by an administrative user or System Center Online. |
| **User Defined** | You categorized the uncategorized item. |
| **User Defined** to **Pending** | You submit the user-defined item to System Center Online for categorization. |
| **Pending** to **Updateable** | A user-defined catalog item has been categorized differently by System Center Online during subsequent catalog synchronization. You can use the **Resolve Conflict** action to decide whether to use the new categorization information or the previous user-defined value. For more information about resolving conflicts, see [Resolve software details conflicts](operations-for-asset-intelligence#BKMK_ResolveSoftwareDetails). |
| **Updateable** to **Validated** | You use the **Resolve Conflict** action and select the new categorization information received from System Center Online during the previous catalog update. For more information about resolving conflicts, see [Resolve software details conflicts](operations-for-asset-intelligence#BKMK_ResolveSoftwareDetails). |
| or |  |
| **Updateable** to **User Defined** | You use the **Resolve Conflict** action and select to use the previous user-defined value. For more information about resolving conflicts, see [Resolve software details conflicts](operations-for-asset-intelligence#BKMK_ResolveSoftwareDetails). |

Note

Because categorization information obtained from System Center Online is stored in the database and cannot be deleted, you can revert back to the System Center Online categorization later.