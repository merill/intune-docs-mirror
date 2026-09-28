---
layout: Conceptual
title: Sample queries for software inventory - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/sample-queries-software-inventory-configuration-manager
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
description: Sample queries that show how software inventory views can be joined to other views to retrieve specific data.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 43cfe225-2236-e065-7e35-403fdbf4c1b5
document_version_independent_id: 479b287e-72f6-b50f-8acb-668df9351843
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/sample-queries-software-inventory-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/sample-queries-software-inventory-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/sample-queries-software-inventory-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e93f3d5f-c77d-4365-a7fb-c9f2234416c7
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/62e8d07a-cc62-4934-b30b-e168a571e51d
platformId: 765af3b5-3afc-899d-7642-d0315aa26aeb
---

# Sample queries for software inventory - Configuration Manager | Microsoft Learn

The following sample queries demonstrate how the Configuration Manager software inventory views can be joined to other views to retrieve specific data. The software inventory views are typically joined to other views by using the **ProductID**, **FileID**, and **ResourceID** columns.

## Joining software inventory views

The following query lists all software files for the Configuration Manager product that have been inventoried on Configuration Manager clients. The **v\_GS\_SoftwareProduct** and **v\_GS\_SoftwareFile** views are joined by using the **ProductID** columns.

```sql
    SELECT DISTINCT SF.FileName, SF.FileDescription, SF.FileVersion 
    FROM v_GS_SoftwareProduct SP INNER JOIN v_GS_SoftwareFile SF 
    ��ON SP.ProductID = SF.ProductId 
    WHERE SP.ProductName = 'Configuration Manager' 
    ORDER BY SF.FileName 
```

## Joining software inventory and discovery views

The following query lists all inventoried products and the associated files for a computer with the NetBIOS name of COMPUTER1. The **v\_R\_System** and **v\_GS\_SoftwareProduct** views are joined by using the **ResourceID** column, and the **v\_GS\_SoftwareProduct** and **v\_GS\_SoftwareFile** views are joined by using the **ProductID** columns.

```sql
    SELECT DISTINCT SP.ProductName, SF.FileName 
    FROM v_R_System SYS INNER JOIN v_GS_SoftwareProduct SP 
    ��ON SYS.ResourceID = SP.ResourceID INNER JOIN v_GS_SoftwareFile SF 
    ��ON SP.ProductID = SF.ProductId 
    WHERE SYS.Netbios_Name0 = 'COMPUTER1' 
    ORDER BY SP.ProductName 
```

## Joining software inventory, discovery, and hardware inventory views

The following query lists all computers that have Microsoft Office installed and have less than 1 GB of free space on the local C drive. The **v\_GS\_SoftwareFile** and **v\_SoftwareProduct** views are joined by the **ProductID** column, and the **v\_GS\_LOGICAL\_DISK** and **v\_R\_System** views are joined to **v\_GS\_SoftwareFile** by using the **ResourceID** columns.

```sql
    SELECT DISTINCT SYS.Netbios_Name0, SYS.User_Domain0, LD.FreeSpace0 
    FROM v_GS_SoftwareFile SF INNER JOIN v_SoftwareProduct SP 
    ��ON SF.ProductId = SP.ProductID 
    ��INNER JOIN v_GS_LOGICAL_DISK LD 
    ��ON SF.ResourceID = LD.ResourceID 
    ��INNER JOIN v_R_System SYS 
    ��ON SF.ResourceID = SYS.ResourceID 
    WHERE (LD.Description0 = 'local Fixed Disk') 
    ��AND (SP.ProductName LIKE 'Microsoft Office%') 
    ��AND (LD.FreeSpace0 < 1000) 
    ��AND (LD.DeviceID0 = 'C:') 
```

## Joining software inventory, discovery, and software metering views

The following query lists all files that have been metered through software metering rules and sorted first by NetBIOS name, and then by product name, and then by file name. The **v\_GS\_SoftwareProduct** and **v\_MeteredFiles** views are joined by the **ProductID** column, and the **v\_GS\_SoftwareProduct** and **v\_R\_System** views are joined by using the **ResourceID** columns.

```sql
    SELECT SYS.Netbios_Name0, SP.ProductName, SP.ProductVersion, 
    ��MF.FileName, MF.MeteredFileVersion 
    FROM v_GS_SoftwareProduct SP INNER JOIN v_MeteredFiles MF 
    ��ON SP.ProductID = MF.MeteredProductID INNER JOIN v_R_System SYS 
    ��ON SP.ResourceID = SYS.ResourceID 
    ORDER BY SYS.Netbios_Name0, SP.ProductName, MF.FileName 
```