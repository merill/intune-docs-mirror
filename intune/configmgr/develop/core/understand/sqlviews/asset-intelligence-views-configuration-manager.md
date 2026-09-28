---
layout: Conceptual
title: Asset intelligence views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/asset-intelligence-views-configuration-manager
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
description: Information about software applications that are in use throughout the Configuration Manager hierarchy.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fac80643-b1a9-d503-6d5f-9cb82328e71f
document_version_independent_id: 0bc2d93f-7533-aea2-4906-64f9b9eddcc0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/asset-intelligence-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/asset-intelligence-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/asset-intelligence-views-configuration-manager.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 11b21d28-d1ec-323b-1c2f-4ec6d4bab5f9
---

# Asset intelligence views - Configuration Manager | Microsoft Learn

The Asset Intelligence views in Configuration Manager contain information about software applications that are in use throughout the Configuration Manager hierarchy, software license management in the enterprise, Asset Intelligence configuration settings, and so on. The Asset Intelligence information is retrieved from clients only after the specific reporting classes have been enabled. By default, the Asset Intelligence reporting classes are disabled, and until the classes are enabled and Configuration Manager clients collect hardware inventory, these views will not contain any information. Other Asset Intelligence views contain information from the Asset Intelligence catalog, summary information, and product licensing information. There are external dependencies and dependencies within the product that should be considered before implementing Asset Intelligence or using the SQL views.

For information about the Asset Intelligence prerequisites, see [Prerequisites for asset intelligence in Configuration Manager](../../../../core/clients/manage/asset-intelligence/prerequisites-for-asset-intelligence) in the Configuration Manager Documentation Library.

For the step-by-step procedure for enabling Asset Intelligence, see [Configuring asset intelligence in Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence) in the Configuration Manager Documentation Library.

The following sections provide detailed information about Asset Intelligence views, Asset Intelligence hardware inventory views, and Asset Intelligence status views.

## Asset intelligence views

The Asset Intelligence views are described in this section.

### v\_AI\_MVLS

Lists the Microsoft Volume Licensing (MVLS) product pools, by **MLSProductPool**, and the product family name, version, effective quantity, and unresolved quantity. It is unlikely that this view will be joined to other views.

### v\_AI\_NON\_MS\_LICENSE

Lists the non-Microsoft product license information, including the product name, publisher, version, language, effective quantity, date of purchase, and so on. It is unlikely that this view will be joined to other views.

### v\_AIProxy

Lists proxy information for the Asset Intelligence synchronization point, if one is configured. It is unlikely that this view will be joined to other views.

### v\_CAL\_INSTALLED\_SOFTWARE\_DATA

Lists information about the installed software applications on Configuration Manager clients found through Asset Intelligence. This view contains the same information as the **v\_GS\_INSTALLED\_SOFTWARE** view, but it limits the columns displayed. The view can be joined with other views by using the **MachineID** column, which is the same as the **ResourceID** column in other views.

### v\_CAL\_Processor\_Count

Lists the number of processors found on Configuration Manager clients. This view uses the same hardware inventory data as the **v\_GS\_PROCESSOR** view, but it displays only the count for processors on each client. The view can be joined with other views by using the **MachineID** column, which is the same as the **ResourceID** column in other views.

### v\_LU\_CAL\_ProductList

Lists the products, by **SoftwareCode**, that are being tracked for CALs, as well as the software hash, product category, license type, and when the product license was last updated. The view can be joined to other views by using the **SoftwareCode** column.

### v\_LU\_Category

Lists information about the Asset Intelligence software categories, by category ID and category name, as well as the language ID, description, and whether the category was created locally. The information contained in this view can be displayed and customized from the **Catalog** node in the Configuration Manager console. The view can be joined to other views by using the **CategoryID** column.

### v\_LU\_Category\_Editable

Lists information about the Asset Intelligence software categories, software families, and custom labels, including the category ID, category name, language ID, description, type, whether the category was created locally, and so on. This view contains information that is found in the **v\_LU\_Category**, **v\_LU\_Family**, and **v\_LU\_Tags** views. It is unlikely that this view will be joined to other views.

### v\_LU\_Family

Lists information about the Asset Intelligence software families, by family ID and family name, as well as language ID, description, and whether the family was created locally. The information contained in this view can be displayed and customized from the **Software Families** node in the Configuration Manager console. The view can be joined to other views by using the **FamilyID** column.

### v\_LU\_HardwareReadiness

Lists information about the hardware requirements for specific software applications, including product, minimum CPU, minimum RAM, minimum hard disk size, minimum hard disk free space, and more. The information contained in this view can be displayed and customized from the **Hardware Requirements** node in the Configuration Manager console. It is unlikely that this view will be joined to other views.

### v\_LU\_MSProd

Lists information about the Microsoft products contained in the Asset Intelligence catalog, including part number, family name, product name, version, language, license type, and so on. It is unlikely that this view will be joined to other views.

### v\_LU\_SoftwareCode

Lists information about the software application codes contained in the Asset Intelligence catalog, as well as the associated software ID and when the software was last updated. The view can be joined to other Asset Intelligence and hardware inventory views by using the **SoftwareCode** and **SoftwareID** columns.

### v\_LU\_SoftwareHash

Lists information about the software applications contained in the Asset Intelligence catalog, by software property hash, including application name, version, publisher, software ID, and when the software was last updated. The view can be joined to other Asset Intelligence and Asset Intelligence hardware inventory views by using the **SoftwarePropertiesHash** and **SoftwareID** columns.

### v\_LU\_SoftwareList

Lists information about the software applications contained in the Asset Intelligence catalog, by software ID and name, including the version, publisher, software category ID, software family ID, custom labels, and so on. The view can be joined to other Asset Intelligence and Asset Intelligence hardware inventory views by using the **SoftwareID**, **CategoryID**, **FamilyID**, **Tag1ID**, **Tag2ID**, and **Tag3ID** columns.

### v\_LU\_SoftwareList\_Editable

Lists information about the software applications, by software ID and name, where the software category, software family, or custom label can be configured with items from the custom catalog. The view also provides the software code, software properties hash, publisher, version, category name and ID, family name and ID, custom labels, and so on. The information contained in this view can be displayed and customized from the **All Inventoried Software Titles** node in the Configuration Manager console. The view can be joined to other Asset Intelligence and Asset Intelligence hardware inventory views by using the **CategoryID**, **FamilyID**, **Tag1ID**, **Tag2ID**, and **Tag3ID** columns.

### v\_LU\_SoftwareList\_Local

Lists information about the software applications contained in the Asset Intelligence catalog, by software ID and name that have a custom software category, custom software family, or custom label. The view also provides the version, publisher, category ID, family ID, label ID (tag ID), last updated date, and so on. This view contains the same source data as the **v\_LU\_SoftwareIdentity\_Local\_Repl** view. The view can be joined to other Asset Intelligence and Asset Intelligence hardware inventory views by using the **SoftwareID**, **CategoryID**, **FamilyID**, **Tag1ID**, **Tag2ID**, and **Tag3ID** columns.

### v\_LU\_Tags

Lists information about the Asset Intelligence custom labels, by tag ID and tag name, as well as the language ID and a description. The information contained in this view can be displayed and customized from the **Custom Labels** node in the Configuration Manager console. The view can be joined to other views by using the **TagID** column, which is the same as the **CategoryID** column in the **v\_LU\_Category\_Editable** view.

### v\_LU\_LicensedProduct

Lists information about the licensed products contained in the Asset Intelligence catalog, by licensed product ID. This includes the family name, the product name, and the version code. It is unlikely that this view will be joined to other views.

## Asset intelligence hardware inventory views

The Asset Intelligence hardware inventory views contain information that is retrieved from Configuration Manager client computers using hardware inventory. For more information about the hardware inventory views, see [Hardware Inventory Views in Configuration Manager](hardware-inventory-views-configuration-manager). The hardware inventory views that contain Asset Intelligence information are described in this section.

### v\_GS\_AUTOSTART\_SOFTWARE

Lists information about the applications on Configuration Manager clients that start automatically with the operating system found through Asset Intelligence. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_BROWSER\_HELPER\_OBJECT

Lists information about the browser objects found on Configuration Manager clients through Asset Intelligence. While some browser helper objects are beneficial, most software considered "malware" is in the form of browser helper objects. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_INSTALLED\_EXECUTABLE

Lists information about the installed software application executables on Configuration Manager clients found through Asset Intelligence. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_INSTALLED\_SOFTWARE

Lists information about the installed software applications on Configuration Manager clients found through Asset Intelligence. The view can be joined with other views by using the **ResourceID** column and with Asset Intelligence views by using the **SoftwareCode0** and **SoftwarePropertiesHash0** columns.

### v\_GS\_INSTALLED\_SOFTWARE\_CATEGORIZED

Lists information about the installed software applications on Configuration Manager clients found through Asset Intelligence. This view contains the information in the **v\_GS\_INSTALLED\_SOFTWARE** view provides additional details about the installed software. The view can be joined with other views by using the **ResourceID** column and with Asset Intelligence views by using the **SoftwareCode0**, **SoftwarePropertiesHash0**, **FamilyID**, **CategoryID**, and **SoftwareID** columns.

### v\_GS\_INSTALLED\_SOFTWARE\_MS

Lists information about the installed Microsoft software applications on Configuration Manager clients found through Asset Intelligence. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SOFTWARE\_LICENSING\_PRODU

Lists software licensing product information for Windows Configuration Manager clients found through Asset Intelligence. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SOFTWARE\_LICENSING\_SERVICE

Lists software licensing service information for Windows Configuration Manager clients found through Asset Intelligence. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SOFTWARE\_SHORTCUT

Lists software shortcut information for Configuration Manager clients found through Asset Intelligence. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SYSTEM\_CONSOLE\_USAGE

Lists all system console usage information for Configuration Manager clients found through Asset Intelligence by polling the System Security Event Log. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SYSTEM\_CONSOLE\_USAGE\_MAXGROUP

Lists all system console usage information for Configuration Manager clients found through Asset Intelligence by polling the Windows System Security Event Log. This view contains a subset of information from the **v\_GS\_SYSTEM\_CONSOLE\_USAGE** view. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_SYSTEM\_CONSOLE\_USER

Lists all system console user information for Configuration Manager clients found through Asset Intelligence by polling the System Security Event Log. The view can be joined with other views by using the **ResourceID** column.

### v\_GS\_USB\_DEVICE

Lists information about the USB devices found on Configuration Manager clients through Asset Intelligence. The view can be joined with other views by using the **ResourceID** column.

## Asset intelligence status view

The Asset Intelligence status view contains summary information about the software applications on Configuration Manager clients. For more information about status views, see [Status and alert views in Configuration Manager](status-alert-views-configuration-manager). The status view that contains Asset Intelligence information is described in this section.

### v\_INSTALLED\_SOFTWARE\_DATA\_Summary

Lists the count of the installed software applications on Configuration Manager clients found through Asset Intelligence. This view contains the same source information as the **v\_GS\_INSTALLED\_SOFTWARE** view, but it provides summary information instead of listing the individual system resources. It is unlikely that this view will be joined to other views.