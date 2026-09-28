---
layout: Conceptual
title: "'Advanced exercise 2: Create a new report for hardware inventory' - Configuration Manager | Microsoft Learn"
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-2-create-new-report-hardware-inventory-configuration-manager
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
description: Create a Configuration Manager report that displays hardware inventory information.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: a1c272aa-667e-d1dd-b9d0-b93adc6baf7e
document_version_independent_id: eba86399-2bca-ba75-2b3f-1e6a5ff7b387
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-2-create-new-report-hardware-inventory-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/advanced-exercise-2-create-new-report-hardware-inventory-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-2-create-new-report-hardware-inventory-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: c1230e0a-4bc3-a565-168c-90668debbd09
---

# 'Advanced exercise 2: Create a new report for hardware inventory' - Configuration Manager | Microsoft Learn

In this exercise, you will create a Configuration Manager report that displays the computer name, site code, the date of the last scan for hardware inventory, and the number of days since the last scan for a specified computer.

Important

Before you begin this exercise, you should review the basic exercises to learn about the report elements, the properties for a report, and the different ways to create the report SQL statement.

## Report requirements

Use the following report requirements to create the new report.

## SQL Server views in the SQL statement

Use the following Configuration Manager SQL Server views when creating the report SQL statement:

- **v\_GS\_WORKSTATION\_STATUS**: This SQL Server view contains the date and time of the last scan for hardware inventory reported by client computers. For more information about this SQL Server view, see [Hardware Inventory Views in Configuration Manager](hardware-inventory-views-configuration-manager).
- **v\_R\_System**: This SQL Server view contains all of the discovered system resources. For more information about this SQL Server view, see [Discovery Views in Configuration Manager](discovery-views-configuration-manager).
- **v\_RA\_System\_SMSInstalledSites**: This SQL Server view contains the installed site for all client computers. For more information about this SQL Server view, see [Discovery Views in Configuration Manager](discovery-views-configuration-manager).

## JOINS in the SQL statement

Create the following JOINS in the SQL statement:

- **v\_GS\_WORKSTATION\_STATUS** is joined to **v\_R\_System** by using the **ResourceID** columns.
- **v\_RA\_System\_SMSInstalledSites** is joined to **v\_R\_System** by using the **ResourceID** columns.

## Columns in the SQL statement

Use the following report columns, in the order listed:

1. **Netbios\_Name0** AS **[Computer Name]** from **v\_R\_System**
2. **SMS\_Installed\_Sites0** AS **[Site Code]** from **v\_RA\_System\_SMSInstalledSites**
3. **LastHWScan** AS **[Last HWScan]** from **v\_GS\_WORKSTATION\_STATUS**
4. **DATEDIFF(day, v\_GS\_WORKSTATION\_STATUS.LastHWScan, GETDATE())** AS **[Days Since Last HWScan]**

Note

This report integrates two SQL Server functions to determine the difference between the last hardware scan date and the current date. To display this column, you can copy the whole line into the SQL statement, or you can copy **DATEDIFF(day, v\_GS\_WORKSTATION\_STATUS.LastHWScan, GETDATE())** into the **Column** column and **Days Since Last HWScan** into the **Alias** column in Query Designer.

Sort the data in descending order, using the **LastHWScan** column.

## Filters in the SQL statement

The report SQL statement does not contain any filters.

## Report prompts

The Configuration Manager report should contain a report prompt for the computer name that will be reported on.

## Solution

See [Advanced exercise 2 solution: Create a new report for hardware inventory in Configuration Manager](advanced-exercise-2-solution-create-new-report-hardware-inventory-configuration-manager) for detailed information about how to create this report.