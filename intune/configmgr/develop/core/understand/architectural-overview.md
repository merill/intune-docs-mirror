---
layout: Conceptual
title: Architectural overview - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/architectural-overview
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
description: A description of Configuration Manager server and client architectures.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 0073cc7f-96f0-f07b-be60-fe91f995417d
document_version_independent_id: b70f9bb3-5b75-9cc8-2bb8-ded426cf88f5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/architectural-overview.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/architectural-overview
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/architectural-overview.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: be9e02ce-f925-a75f-5b2e-1131e4e585d4
---

# Architectural overview - Configuration Manager | Microsoft Learn

Configuration Manager is a configuration management product that requires servers to administer client computers. The following sections describe both Configuration Manager server and client architecture. Gaining an understanding of the concepts relating to both server and client architecture will help you understand how you can customize Configuration Manager for specific uses in your organization.

## Configuration Manager server architecture

The Configuration Manager server architecture can be divided into two separate tiers:

- The Configuration Manager components
- The WBEM interface to the Configuration Manager architecture (SMS Provider)

Configuration Manager components are analogous to the mechanisms and devices that enable the elevator, the phone system, and the electrical system in an office building to work properly. When you make changes through the Configuration Manager console, Configuration Manager services and components start working to complete the operation successfully, whether it's software distribution, hardware inventory, or any other administrator-initiated or schedules Configuration Manager task, feature, or tool.

The WBEM interface to the Configuration Manager architecture is a description of the Configuration Manager framework, much as building plans describe a building. As you become more familiar with Configuration Manager, you might find that your organization needs to provide Configuration Manager functionality in a slightly different fashion. You might need to gather additional inventory information and store it in your Configuration Manager database. The WBEM interface enables you to customer Configuration Manager for optimal change and configuration management.

### SMS component and data store architecture

To fully understand Configuration Manager features, you need a basic understanding of the elements that make up Configuration Manager. Service components, thread components, and data stores are the major elements of Configuration Manager server architecture. Each of these elements does a specific function to complete the work that you assign and schedule.

#### SMS components

In Configuration Manager, components are threads, services, and applications that run on both server and client computers and provide Configuration Manager functionality. Service and thread components accomplish the many tasks Configuration Manager requires to function – tasks such as communication for inter- and intra-site connectivity, configuration, resource discovery, client installation, database maintenance, status, site system installation, and reporting.

#### Data stores

A dynamic computing environment must have a central location that stores the critical operations information. Also, server and client components need access to their configuration data, scheduled times of operation, and the data in the Configuration Manager site database to accomplish tasks. For example, Collection Evaluator operation requires information such as which collections to evaluate, when to evaluate them, and what resources belong to each specific collection. To do these tasks, Collection Evaluator needs access to both configuration data and data stored in the Configuration Manager site database.

In Configuration Manager, there are two basic types of data stores: configuration data and system data.

##### Configuration data

Configuration Manager gathers configuration data from Configuration Manager default settings, changes you make through the Configuration Manager console, and changes Configuration Manager services make. Configuration is a dynamic system that enables you to make decisions about how and with the site will operate. As you make configuration changes, Configuration Manager updates the site control file and the registry. The site control file contains configuration for a Configuration Manager site. Many Configuration Manager features, such as Software Inventory, function on a schedule. After Configuration Manager server service and thread components are enabled, they periodically check the site control file for their configuration and schedule as they continue to work.

##### System data

Configuration Manager gathers system data from the various resources in the site. Systems within an organization change constantly as hardware and software are upgraded and repaired, new systems are brought on line, and old systems are retired. Configuration Manager stores the information in the Configuration Manager site database. This database stores all of the data pertinent to Configuration Manager functions including DDRs, MIF files, network discovery data, and site configuration data.

### The WBEM interface with the SMS architecture

Configuration Manager provides an open architecture that enables you to write applications and scripts that automate and customize Configuration Manager features, such as Software Distribution. You can also create and install customized programs that you can start from the Configuration Manager console.

![The WBEM interface with the SMS architecture](media/cm_architecture2.gif)

Terms and concepts that relate to Configuration Manager architecture originate from various sources. Some originated with the Desktop Management Task Force (DMTF) and were created to describe managed objects. Others are standard COM and Web-Based Enterprise Management (WBEM) initiative terms and concepts. Still others are specific to Configuration Manager.

| Term | Definition |
| --- | --- |
| Windows Management | The Microsoft implementation of one of the DMTF standards for identifying and manipulating managed objects. |
| CIM Object Manager | The primary component in the management infrastructure of the WBEM technology. Client applications access the CIM Object Manager to find the correct provider. |
| SMS Provider | The WBEM provider that exposes the Configuration Manager site database. The SMS Provider acts as an intermediary between the CIM Object Manager and any Configuration Manager data. The SMS Provider also accesses the Configuration Manager site database to provide data to the Configuration Manager console. |
| Configuration Manager Site Database | A SQL Server database that stores Configuration Manager data. The managed objects (such as disk drives or collections) stored in the Configuration Manager site database are represented by instances of Configuration Manager classes in the database rather than records in a database. |
| WBEM Application | An executable application that makes API calls to the CIM Object Manager to view or manage data from providers. |
| Windows Management Service | A Windows service that starts and stops the CIM Object Manager. |
| Configuration Manager Console | A WBEM application. |

### Configuration Manager and the WBEM architecture

Configuration Manager uses the WBEM architecture to manage objects. WBEM is an industry initiative adopted by the DMTF that is also supported by many non-Windows computer and network device manufacturers. The WBEM initiative complements Active Directory that locates and manages entity policies. WBEM also provides a unifying mechanism through which management applications can interact with the managed entities (like Configuration Manager objects) – without you having to understand the underlying management protocols that these entities use.

In Configuration Manager, objects are items such as client computers, advertisements, and packages stored in the Configuration Manager database. The WBEM initiative outlines the architecture used by Windows Management, Microsoft's implementation of one of the DMTF object management standards.

The CIM Object Manager stores the metadata, Windows Management provides access to the Configuration Manager configuration and operations data with an extensible, platform-independent interface. And managed object, such as a disk drive or a collection is represented by an instance of a Configuration Manager class. Each Configuration Manager managed object is represented by a CIM class.

### Configuration Manager and Windows management

To view and manipulate objects, Configuration Manager makes a request to the CIM Object Manager (the central WBEM component). Configuration Manager uses the site database to store managed object data. However, Configuration Manager uses the CIM Object Manager interface and the SMS Provider to view and manipulate that managed data. You can't view or manipulate the Configuration Manager database directly. Instead, you gain access to the underlying Configuration Manager site database through the CIM Object Manager, which in turn communicates with the SMS Provider.

![Configuration Manager and Windows management](media/cm_architecture1.gif)

## Client architecture

A Configuration Manager client computer is any computer in your organization that has the Configuration Manager client software installed. Computers serving as Configuration Manager site servers and site systems can also be installed as Configuration Manager client computers, in addition to any other servers in your organization where you install Configuration Manager client software.

Configuration Manager client software:

- Runs almost entirely as services, processes, or applications started from Configuration Manager services.
- Runs from the client computer (as opposed to over the network).
- Maintains history information for most function so the client computer (such as software and hardware inventory).