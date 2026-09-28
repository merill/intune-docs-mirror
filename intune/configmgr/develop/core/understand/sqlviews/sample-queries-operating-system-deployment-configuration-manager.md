---
layout: Conceptual
title: Sample queries for operating system deployment - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-operating-system-deployment-configuration-manager
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
description: Sample queries that show how to join operating system deployment views to each other and to compliance settings views.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 4ca490d2-57df-2bfa-2a69-e377f0bfdd30
document_version_independent_id: 4d947a5a-5b69-e497-2968-2d57c48a185e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-operating-system-deployment-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-operating-system-deployment-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-operating-system-deployment-configuration-manager.md
cmProducts: []
platformId: 12da1cb9-1cab-a217-3e17-6fcf4e76455c
---

# Sample queries for operating system deployment - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how to join operating system deployment views to each other and to compliance settings views. You can join the operating system deployment views to other operating system deployment views and application management views by using the view column that contains the package ID, which might have different column names depending on the view. You can join the operating system deployment views to compliance settings views by using the **CI\_ID** column, and they can be joined to discovery views by using the **ResourceID** column.

## Joining operating system deployment and application management views

The following query lists all task sequence packages, by package ID and package name, the associated boot image package, by package ID and package name, and the source path for the boot image package. The query results are sorted by the task sequence package ID. A LEFT OUTER JOIN is used to join the **v\_TaskSequencePackage** and **v\_BootImagePackage** operating system deployment views by using the **BootImageID** and **PackageID** columns, respectively.

```sql
    SELECT DISTINCT 
    ��v_TaskSequencePackage.PackageID AS [Task Sequence Package ID], 
    ��v_TaskSequencePackage.Name AS [Task Sequence Package Name], 
    ��v_TaskSequencePackage.BootImageID AS [Boot Image Package ID], 
    ��v_BootImagePackage.Name AS [Boot Image Package Name], 
    ��v_BootImagePackage.PkgSourcePath AS [Boot Image Package Source Path] 
    FROM v_TaskSequencePackage LEFT OUTER JOIN v_BootImagePackage ON 
    ��v_TaskSequencePackage.BootImageID = v_BootImagePackage.PackageID 
    ORDER BY [Task Sequence Package ID] 
```

## Joining operating system deployment and compliance settings views

The following query lists all operating system deployment boot image packages, by package ID and package name, the drivers that are contained in the boot image package, and the source path for the driver. The query results are sorted by the boot image package ID and then by the driver name. The **v\_BootImagePackage** and **v\_BootImagePackage\_References** operating system deployment views are joined by using the **PackageID** and **PkgID** columns, respectively; the **v\_BootImagePackage\_References** view is joined to the **v\_ConfigurationItems** compliance settings view by using the **CI\_ID** column; and the **v\_ConfigurationItems** view is joined to the **v\_LocalizedCIProperties** compliance settings view by using the **CI\_ID** column.

```sql
    SELECT v_BootImagePackage.PackageID AS [Boot Image Package ID], 
    ��v_BootImagePackage.Name AS [Boot Image Package Name], 
    ��v_LocalizedCIProperties.DisplayName AS [Driver Name], 
    ��v_BootImagePackage_References.SourcePath AS [Driver Source Path] 
    FROM v_BootImagePackage INNER JOIN v_BootImagePackage_References ON 
    ��v_BootImagePackage.PackageID = v_BootImagePackage_References.PkgID 
    ��INNER JOIN v_ConfigurationItems ON 
    ��v_BootImagePackage_References.CI_ID = v_ConfigurationItems.CI_ID 
    ��INNER JOIN v_LocalizedCIProperties ON 
    ��v_ConfigurationItems.CI_ID = v_LocalizedCIProperties.CI_ID 
    ORDER BY [Boot Image Package ID], [Driver Name] 
```