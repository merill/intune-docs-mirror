---
layout: Conceptual
title: Discovery views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/discovery-views-configuration-manager
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
description: System resource objects, which include any resources that were discovered on the network.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: fb870862-1b31-5a5f-144f-a99ffb66eac8
document_version_independent_id: dfaf30ef-ea8c-fda3-256d-467c6743db16
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/discovery-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/discovery-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/discovery-views-configuration-manager.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 0749fd7c-9153-363e-52da-80cb38598e9c
---

# Discovery views - Configuration Manager | Microsoft Learn

The Configuration Manager discovery views consist of system resource objects, which include any resources that were discovered on the network. The four main discovery views are **v\_R\_System** for system resources, **v\_R\_User** for user resources, **v\_R\_UserGroup** for user group resources, and **v\_R\_UnknownSystem** for unknown systems.

Each of these discovered resources has a defined resource type, which is stored in the **v\_resourcemap** schema view.

## Discovery schema views

The discovery schema views provide information about all resources in a Configuration Manager site. The two discovery schema views are **v\_ResourceMap** and **v\_ResourceAttributeMap**. The **v\_ResourceMap** view contains a list of all the resource types for discovered data. By default, Configuration Manager has the Unknown System, User Group, User, and System Resource types, each of which has its own resource type number and individual view. The view can be joined to other views by using the **ResourceType** column. The following table contains the default data stored in the **v\_ResourceMap** view.

### v\_R\_System\_Valid

Lists information about valid computers. This view is sorted by **ResourceID** and includes the client version, the processor type, the client's domain, the NetBIOS name, the operating system and more. This view can be joined to other views by using the **ResourceID** column.

| Resource type | Display name | Resource Class Name |
| --- | --- | --- |
| 2 | Unknown System | **v\_R\_UnknownSystem** |
| 3 | User Group | **v\_R\_UserGroup** |
| 4 | User | **v\_R\_User** |
| 5 | System | **v\_R\_System** |
| 6 | IP Network | **V\_R\_IPNetwork** |

The **v\_ResourceAttributeMap** contains all of the attributes that will be discovered for each of the resource types, such as NetBIOS name, operating system, user name, user group name, domain name, and so forth. The **v\_ResourceAttributeMap** view can be joined to other views by using the **ResourceType** column. The discovery schema views are also listed and described in the [Schema views in Configuration Manager](schema-views-configuration-manager) topic.

## Configuration Manager discovery views

The **v\_R\_System** view can be joined with any other view that contains system data (system discovery array views, inventory views, collection views, status views, and so forth) by using the **ResourceID** column. The **v\_R\_System** view will be one of the most often used when joining views. The **v\_R\_UnknownSystem**, **v\_R\_User**, and **v\_R\_UserGroup** views also use the **ResourceID** column to join with views that contain data for their resource type. Most of the remaining discovery views contain data where there can be more than one value for a resource, such as IP address or user organizational unit (OU) name. The discovery views are described in the following table.

### v\_AgentDiscoveries

Lists all resources that have been discovered in the Configuration Manager hierarchy and by what discovery agent. The view contains data about the resource type, resource ID, agent that discovered the resource, site code where the agent resides, and time of the discovery. The view can be joined to other views by using the **ResourceID** column.

### v\_ClientMachines

Lists all discovered system resources, by resource ID, that are not in an obsolete or decommissioned state and whether the system resource is a Configuration Manager client. The view can be joined to other views by using the **ResourceID** column.

### v\_ClientMode

Lists all discovered system resources, by resource ID, that are not in an obsolete or decommissioned state and the associated client mode. The view can be joined to other views by using the **ResourceID** column.

### v\_R\_System

Lists all discovered system resources by resource ID, resource type, whether the resource is a client, what type of client, client version, NetBIOS name, user name, operating system, unique identifier, and more. The view can be joined to other views by using the **ResourceID**, **ResourceType**, **Netbios\_Name0**, and **SMS\_Unique\_Identifier0** columns.

### v\_RA\_System\_SMS\_Resident

Lists the resident site of discovered devices. The view can be joined to other views by using the **ResourceID** column.

### v\_R\_System\_Valid

Lists all discovered system resources that are not in an obsolete or decommissioned state. This view is a subset of the **v\_R\_System** view and includes the resource ID, resource type, whether the resource is a client, what type of client, client version, NetBIOS name, user name, operating system, unique identifier, and so forth. The view can be joined to other views by using the **ResourceID**, **ResourceType**, and **Netbios\_Name0** columns.

### v\_R\_UnknownSystem

Lists all unknown system resources that have been discovered, including resource ID, resource type, user name, domain, and so forth. The view can be joined to other views by using the **ResourceID**, **ResourceType**, and **SMS\_Unique\_Identifier0** columns.

### v\_R\_User

Lists all discovered user resources by resource ID, resource type, user name, domain, and so forth. The view can be joined to other views by using the **ResourceID**, **ResourceType**, and **Unique\_User\_Name0** columns.

### v\_R\_UserGroup

Lists all discovered user group resources by ID, type, user group name, domain, and more. The view can be joined to other views by using the **ResourceID** and **ResourceType** columns.

### v\_RA\_System\_IPAddresses

Lists the IP addresses for discovered system resources. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_System\_IPSubnets

Lists the IP subnets for discovered system resources. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_System\_IPv6Addresses

Lists the IPv6 addresses for discovered system resources. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_System\_IPv6Prefixes

Lists the IPv6 prefixes for discovered system resources. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_System\_IPXAddresses

Lists the IPX addresses for discovered system resources. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_System\_MACAddresses

Lists the MAC addresses for discovered system resources. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_System\_ResourceNames

Lists all discovered system resources by resource ID and fully qualified domain name. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_System\_SMSAssignedSites

Lists all system resources, by resource ID, that are assigned to a site, together with the site code. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_System\_SMSInstalledSites

Lists all system resources, by resource ID that have been installed as clients and the site code they belong to. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_System\_SystemContainerName

Lists all system resources, by resource ID, that are in an associated Active Directory container. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_System\_SystemGroupName

Lists all system resources, by resource ID, that are in an associated Active Directory group. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_System\_SystemOUName

Lists all system resources, by resource ID, that and their associated Active Directory OU. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_System\_SystemRoles

Lists all system resources, by resource ID, that have an associated site system role (site server, management point, software update point, and so forth). The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_User\_UserContainerName

Lists all user resources, by resource ID, that are in an associated Active Directory container. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_User\_UserGroupName

Lists all user resources, by resource ID, that are in an associated Active Directory group. The view can be joined to other views by using the **ResourceID** column.

### v\_RA\_User\_UserOUName

Lists all user resources, by resource ID, that are in an associated OU. The view can be joined to other views by using the **ResourceID** column.

### v\_R\_IPNetwork

Lists information about IP subnets discovered by Configuration Manager network discovery, sorted by **ResourceID**. This includes information about subnet addresses, masks, names and topology. This view can be joined to other views by using the **ResourceID** column.