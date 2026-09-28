---
layout: Conceptual
title: About Configuration Manager Inventory - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/clients/inventory/about-configuration-manager-inventory
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
ms.date: 2016-09-20T00:00:00.0000000Z
description: You can use Configuration Manager to collect hardware and software inventory from Configuration Manager clients by enabling the client agents on a site-by-site basis.
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: bf23ccf3-9e0d-dd90-16d3-cca8dbc8362e
document_version_independent_id: 9b94df52-b39e-123e-255c-4ba5bb394b1d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/clients/inventory/about-configuration-manager-inventory.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/clients/inventory/about-configuration-manager-inventory
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/clients/inventory/about-configuration-manager-inventory.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bebeecd4-43b9-9d43-d3ea-f64c94af551a
---

# About Configuration Manager Inventory - Configuration Manager | Microsoft Learn

You can use Configuration Manager to collect hardware and software inventory from Configuration Manager clients by enabling the client agents on a site-by-site basis.

When the hardware inventory client agent is enabled for Configuration Manager sites, hardware inventory data gives you system information (such as available disk space, processor type, and operating system) about each computer. When the software inventory client agent is enabled, you can inventory information, such as the specific file types and versions that are present on client computers. The software inventory client agent can also collect information about files that are inventoried on client systems. Configuration Manager software inventory can also collect files, not just details about the files, from client computers. With file collection, you specify a set of files to be copied from clients to the Configuration Manager site server that the clients are assigned to.

Note

For more information, see [Introduction to hardware inventory](../../../../core/clients/manage/inventory/introduction-to-hardware-inventory).

## About Collecting Hardware Inventory

When it's enabled, the Configuration Manager hardware inventory client agent automatically collects detailed information about the hardware characteristics of clients in a Configuration Manager site. By using this feature, you can collect a wide variety of information about client computers, such as memory, operating system, and peripherals for client computers.

The hardware inventory feature collects data from client computers by querying several data stores on client computers, such as the registry and Windows Management Instrumentation (WMI) namespace classes. The hardware inventory client agent doesn't query for all possible WMI classes, but it does provide the ability to report on approximately 1,500 hardware properties from almost 100 different WMI classes, by default.

## About Collecting Software Inventory

When it's enabled, the Configuration Manager software inventory client agent can collect software inventory data directly from files (such as .exe files) by inventorying the file header information. Configuration Manager can also inventory unknown files—files that don't have detailed information in their file headers. This provides a flexible, easy-to-maintain software inventory method. You can also have Configuration Manager collect copies of files that you specify. You can view software inventory and collected file information for a client by using Resource Explorer.

## About NOIDMIF and IDMIF Files

Management Information Format (MIF) files can be used to extend hardware inventory information that is collected from clients by the Configuration Manager hardware inventory client agent. During hardware inventory, the information that is stored in MIF files is added to the client inventory report and stored in the site database, where you can use the data in the same ways that you use default client inventory data. Two MIF files can be used when performing client hardware inventories: NOIDMIF and IDMIF.

By default, NOIDMIF and IDMIF file information isn't inventoried by Configuration Manager sites. To enable NOIDMIF and IDMIF file information to be inventoried, NOIDMIF and IDMIF collection must be enabled. You can choose to enable one or both types of MIF file collection for Configuration Manager sites on the **MIF Collection** tab of the hardware inventory client agent properties.

Important

Before you can add information from MIF files to the Configuration Manager database, you must create or import class information for them. For more information, see the sections **To add a new inventory class** and **To import hardware inventory classes** in [How to Extend Hardware Inventory in Configuration Manager](../../../../core/clients/manage/inventory/extend-hardware-inventory).

### NOIDMIF Files

Standard MIF files that are used in Configuration Manager hardware inventory are called NOIDMIF files. NOIDMIF files don't contain a unique identifier for the data. Configuration Manager automatically associates NOIDMIF file data with the client that the NOIDMIF file is collected from when reporting inventory information.

Note

NOIDMIF files themselves are not sent to the site server during a client hardware inventory cycle. The information that is contained within the NOIDMIF file is collected and added to the client inventory report.

If the classes defined in an inventoried NOIDMIF file don't already exist in the Configuration Manager site database, new inventory class tables are created in the site database to store the inventoried information. Subsequent inventories will inventory the data stored in the NOIDMIF file and update the existing inventory data for the client in the site database. If the NOIDMIF file is removed from the client, all the classes and properties relating to the NOIDMIF file are deleted from the current inventory information for the client in the site database.

For NOIDMIF file information to be inventoried by default, the NOIDMIF file must be stored in the following directory on Configuration Manager clients:

%*Windir*%\System32\CCM\Inventory\Noidmifs

### IDMIF Files

Custom MIF files, called IDMIF files, can also be used in Configuration Manager hardware inventory. IDMIF files contain a unique ID and aren't associated with the computer they're collected from. IDMIF files can be used to collect inventory data about devices that aren't Configuration Manager clients; for example, a shared network printer, DVD player, photocopier, or similar equipment that isn't associated with a client-specific computer.

When IDMIF collection is enabled for a site, IDMIF files are collected only if they are within the size limit that is specified for custom MIF files defined in the **General** tab of the hardware inventory client agent properties.

Important

Because IDMIF files are not associated with a Configuration Manager client, they are collected by the hardware inventory client agent and sent to the site server along with the client hardware inventory report. Depending on the maximum custom MIF size specified for the site, IDMIF collection might cause increased network bandwidth usage during client inventories and should be planned for before enabling IDMIF file collection.

IDMIF files are identical to NOIDMIF files, with these exceptions:

- IDMIF files must have a delta header that provides architecture, and a unique ID. NOIDMIF files are automatically given a similar header by the system during processing on the client.
- IDMIF files must include a top-level group with the same class as the architecture being added or changed, and that group must include at least one property.
- Like NOIDMIF files, IDMIF files have key properties that must be unique. Any class that has more than one instance must have at least one key property defined, or subsequent instances overwrite previous instances.
- Removing IDMIF files from clients doesn't cause the associated data in the site database to be deleted during subsequent hardware inventories.
- IDMIF file information isn't added to client inventory reports and sent as MIF files across the network to be processed at the site server.

    For IDMIF file information to be inventoried by default, the IDMIF file must be stored in the following directory on Configuration Manager clients:

    %*Windir*%\System32\CCM\Inventory\Idmifs