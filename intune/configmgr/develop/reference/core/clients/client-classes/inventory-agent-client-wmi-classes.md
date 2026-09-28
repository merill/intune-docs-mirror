---
layout: Conceptual
title: Inventory Agent Client WMI Classes - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/inventory-agent-client-wmi-classes
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
description: In Configuration Manager, the inventory client agent classes can be broken into three categories.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 05791ba0-3996-c101-ad75-1ccd88da3e2d
document_version_independent_id: ebc526d5-5e0a-ff08-de5f-ae190200240b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/core/clients/client-classes/inventory-agent-client-wmi-classes.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/core/clients/client-classes/inventory-agent-client-wmi-classes
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/core/clients/client-classes/inventory-agent-client-wmi-classes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d1ec7fa5-d9cc-c97d-e973-fad06d857b95
---

# Inventory Agent Client WMI Classes - Configuration Manager | Microsoft Learn

In Configuration Manager, the inventory client agent classes can be broken into three categories:

- Inventory client agent settings
- Inventory collection
- Report state Configuration Manager inventory provider

    If the IDMIF class name is more than 32 characters, the IDMIF is collected on the client, but the data is not written to the SQL Server database.

## Inventory Agent Settings

These classes define what an inventory client agent collects and how the collection set should be reported.

| Class | Description |
| --- | --- |
| [CollectableFileItem Client WMI Class](collectablefileitem-client-wmi-class) | Defines a file collection query. |
| [FileCollectionAction Client WMI Class](filecollectionaction-client-wmi-class) | Defines a file collection set for reporting, such as software file collection or IDMIF collection. |
| [InventoryAction Client WMI Class](inventoryaction-client-wmi-class) | Defines an inventory collection set for reporting, such as discovery, hardware inventory, software inventory, software file collection, or IDMIF collection. |
| [InventoryDataContext Client WMI Class](inventorydatacontext-client-wmi-class) | Defines an optional context qualifier for a class query. |
| [InventoryDataItem Client WMI Class](inventorydataitem-client-wmi-class) | Defines an inventory class property query to be collected for a particular inventory action. |

## Inventory Collection and Report State

These classes are used to track the current state of inventory collection and reporting. The inventory client agent generates these class instances for each type of inventory report.

| Class | Description |
| --- | --- |
| [InventoryActionStatus Client WMI Class](inventoryactionstatus-client-wmi-class) | Saves the state of each inventory action. |

## SMS Inventory Provider Classes

These classes are defined by Configuration Manager-supplied instance providers and extend inventory collection beyond the standard Windows Management Instrumentation (WMI) providers. In general, these classes expose additional system data through WMI for inventory collection.

| Class | Description |
| --- | --- |
| [FileSystemFile Client WMI Class](filesystemfile-client-wmi-class) | Allows the querying of files based on various criteria. |
| [SMS_MIFGroup Client WMI Class](sms_mifgroup-client-wmi-class) | A dynamic instance provider class that allows WMI reporting of Management Information Format (MIF) files that extend the client inventory. |
| [NEW : SMS_Windows8Application Client WMI Class](sms_windows8application-client-wmi-class) | A client Windows Management Instrumentation (WMI) class that defines an application. |
| [SMS_Windows8ApplicationUserInfo Client WMI Class](sms_windows8applicationuserinfo-client-wmi-class) | A client Windows Management Instrumentation (WMI) class that defines user information of an application. |

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Client Runtime Requirements](../../../../core/reqs/client-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Client Development Requirements](../../../../core/reqs/client-development-requirements).