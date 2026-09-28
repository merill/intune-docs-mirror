---
layout: Conceptual
title: "'Advanced exercise 1: Create a new report for compliance settings' - Configuration Manager | Microsoft Learn"
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-1-create-new-report-compliance-settings-configuration-manager
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
description: Create a Configuration Manager report that displays the name and description of the configuration baselines.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 8966d725-f438-d9b3-a23b-1c8d5b47fddf
document_version_independent_id: 1ad1b8cb-ea08-9ec1-c20a-fbc2d006f55a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-1-create-new-report-compliance-settings-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/advanced-exercise-1-create-new-report-compliance-settings-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-1-create-new-report-compliance-settings-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: eca06e9c-6d9d-d5b7-e217-d94236076f75
---

# 'Advanced exercise 1: Create a new report for compliance settings' - Configuration Manager | Microsoft Learn

In this exercise, you will create a Configuration Manager report that displays the name and description of the configuration baselines that are deployed to a specified computer and whether the computer returns compliant or noncompliant for the configuration baseline.

Important

Before you begin this exercise, you should review the basic exercises to learn about the report elements, the properties for a report, and the different ways to create the report SQL statement.

## Report requirements

Use the following report requirements to create the new report.

## SQL Server views in the SQL statement

Use the following Configuration Manager SQL views when creating the report SQL statement:

- **v\_CICurrentComplianceStatus:** This SQL view contains compliance information for all configuration items. For more information about this SQL view, see [Compliance Settings Views in Configuration Manager](compliance-settings-views-configuration-manager).
- **v\_ConfigurationItems:** This SQL view contains all of the configuration items. For more information about this SQL view, see [Compliance Settings Views in Configuration Manager](compliance-settings-views-configuration-manager).
- **v\_LocalizedCIProperties:** This SQL view contains the localized titles and descriptions for the configuration items. For more information about this SQL view, see [Compliance Settings Views in Configuration Manager](compliance-settings-views-configuration-manager).
- **v\_R\_System:** This SQL view contains all of the discovered system resources. For more information about this SQL view, see [Discovery Views in Configuration Manager](discovery-views-configuration-manager).

## JOINS in the SQL statement

Create the following JOINS in the SQL statement:

- **v\_CICurrentComplianceStatus** is joined to **v\_ConfigurationItems** by using the **CI\_ID** column.
- **v\_CICurrentComplianceStatus** is joined to **v\_LocalizedCIProperties** by using the **CI\_ID** column.
- **v\_CICurrentComplianceStatus** is joined to **v\_R\_System** by using the **ResourceID** column.

## Columns in the SQL statement

Use the following report columns, in the order listed:

1. **ComplianceStateName** from **v\_CICurrentComplianceStatus**
2. **DisplayName** from **v\_LocalizedCIProperties**
3. **Description** from **v\_LocalizedCIProperties**
4. **Netbios\_Name0** from **v\_R\_System**
5. **CIType\_ID** from **v\_ConfigurationItems** (Not displayed)

Sort the returned data in ascending order, using the **Netbios\_Name0** column.

## Filters in the SQL statement

The report SQL statement should meet the following filtering criteria:

- Select only configuration baselines. You can filter specifically on configuration baselines by selecting the **CIType\_ID**. Configuration baselines are CI type 2.

## Report prompts

The Configuration Manager report should contain a report prompt for the computer name that will be reported on.

## Solution

See [Advanced exercise 1 solution: create a new report for compliance settings in Configuration Manager](advanced-exercise-1-solution-create-new-report-compliance-settings-configuration-manager) for detailed information about how to create this report.