---
layout: Conceptual
title: Security views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/security-views-configuration-manager
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
description: Information about the permissions that are granted to users and user groups.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: d7588c8f-5786-098c-a9e9-a7dea4166e59
document_version_independent_id: 480f46c5-5c55-4540-b5e2-7b33292e2cef
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/security-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/security-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/security-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 1cc5d441-296b-b882-4de4-0f282537f197
---

# Security views - Configuration Manager | Microsoft Learn

The security views in Configuration Manager contain information about the permissions that are granted to users and user groups to perform operations on secured Configuration Manager object classes and instances, such as collections, applications, deployments, and more.

## Security views

Security views can be used to query for Configuration Manager class or instance permissions for secured objects. In each SQL view, class and instance permission values are listed as a decimal value that is the result of converting bit fields reserved for each security right. More information can be found in the next section. The security views are described in This section.

### v\_SecuredObject

Describes the different types of objects in the Configuration Manager system that can be secured, such as collections, applications, deployments, Wi-Fi and VPN profiles, client settings and many more. The view lists the Configuration Manager objects by object ID and name. The view can be joined to the other security views by using the **ObjectTypeID** or **ObjectTypeName** columns.

### v\_AllItems

Lists all securable objects in the Configuration Manager site by name. It is unlikely that this view will be joined to other views.

### V\_CategoryPermissions

Lists, for each object type, the permissions for each Configuration Manager collection. The view can be joined to the other security views by using the **AdminID** column.

## Configuration Manager secured objects

Class and instance permissions can be set on more than 20 secured objects in Configuration Manager. These Configuration Manager secured objects and their associated object keys are listed in the following table.

| Object key | Object Name |
| --- | --- |
| 1 | Collection |
| 2 | Package |
| 4 | Status message |
| 6 | Site |
| 7 | Query |
| 9 | Software metering rule |
| 11 | Configuration items |
| 14 | OS install package |
| 15 | Deployment template |
| 16 | Deployment |
| 17 | Computer association |
| 18 | OS image |
| 19 | Boot image package |
| 20 | Task sequence package |
| 21 | Device setting package |
| 22 | Device setting item |
| 23 | Driver package |
| 24 | Deployment package |
| 25 | Device driver |
| 26 | Asset intelligence software list |
| 27 | Security roles |
| 28 | Site administrator settings |
| 29 | Categories |
| 30 | Alerts |
| 31 | Applications |
| 32 | Global conditions |
| 33 | User device affinity |
| 34 | Authorization settings |
| 36 | Device enrollment |
| 37 | Software updates |
| 38 | Client settings |
| 40 | Migration site mapping |
| 41 | Migration jobs |
| 42 | Distribution points |
| 43 | Distribution point groups |
| 44 | Inventory reporting |
| 45 | Boundaries |
| 46 | Boundary groups |
| 47 | Endpoint Protection |
| 48 | Configuration policies |
| 49 | Windows Firewall settings |
| 50 | Microsoft Intune subscription |
| 52 | User state management |
| 53 | Windows Firewall policies |
| 54 | Windows Azure subscription |
| 55 | Settings for Windows RT side loading keys |
| 56 | Wi-Fi profiles |
| 57 | VPN profiles |
| 58 | Client authentication certificate settings |
| 59 | Remote connection profiles |
| 60 | Trusted root certificate settings |
| 200 | Configuration data assignments |
| 201 | Deployments |
| 202 | Client settings |
| 203 | Virtual environments |

## How to interpret decimal permission values

In the security views, there are decimal values that equate to a specific class or instance permissions. Each individual permission uses one of 28 bits. The following table lists each of these permissions, the bit that is used, and the decimal value of that bit.

| Permission name | Bit value | Bit position | Decimal value |
| --- | --- | --- | --- |
| Read | 1 | 1 | 1 |
| Modify | 10 | 2 | 2 |
| Delete | 100 | 3 | 4 |
| Distribute | 1000 | 4 | 8 |
| Create Child | 10000 | 5 | 16 |
| Use remote tools | 100000 | 6 | 32 |
| Advertise | 1000000 | 7 | 64 |
| Modify resource | 10000000 | 8 | 128 |
| Administer | 100000000 | 9 | 256 |
| Delete resource | 1000000000 | 10 | 512 |
| Create | 10000000000 | 11 | 1024 |
| View collected files | 100000000000 | 12 | 2048 |
| Read resource | 1000000000000 | 13 | 4096 |
| Delegate | 10000000000000 | 14 | 8192 |
| Meter | 100000000000000 | 15 | 16384 |
| Manage SQL commands | 1000000000000000 | 16 | 32768 |
| Manage status filters | 10000000000000000 | 17 | 65536 |
| Manage folders | 100000000000000000 | 18 | 131072 |
| Network access | 1000000000000000000 | 19 | 262144 |
| Import computer entry | 10000000000000000000 | 20 | 524288 |
| Create task sequence media | 100000000000000000000 | 21 | 1048576 |
| Modify collection setting | 1000000000000000000000 | 22 | 2097152 |
| Manage OSD and ISV Proxy Certificates | 10000000000000000000000 | 23 | 4194304 |
| Recover user state | 100000000000000000000000 | 24 | 8388608 |
| Manage management controllers | 1000000000000000000000000 | 25 | 16777216 |
| View management controllers | 10000000000000000000000000 | 26 | 33554432 |
| Manage Asset Intelligence | 100000000000000000000000000 | 27 | 67108864 |
| View Asset Intelligence | 1000000000000000000000000000 | 28 | 134217728 |

To interpret a permission value, you can convert the decimal value to binary and use the preceding table to get the specific permissions. To help understand this process, see the following examples.

## Decimal conversion example 1

In the **v\_SecuredObject** view, the **SMS\_Site** secured object has a value of 638983 in the **AvailableInstancePermissions** column. To find out what this means, first convert the decimal number to binary. This equates to 10011100000000000111, in which the 1st, 2nd, 3rd, 15th, 16th, 17th, and 20th bits are used. Use the bit values from the preceding table to calculate the values in the following table. When the decimal values are added, they will total the initial 638983 value.

| Permission Name | Binary Position | Decimal Value |
| --- | --- | --- |
| Read | 1 | 1 |
| Modify | 2 | 2 |
| Delete | 3 | 4 |
| Meter | 15 | 16384 |
| Manage SQL commands | 16 | 32768 |
| Manage status filters | 17 | 65536 |
| Import computer entry | 20 | 524288 |

## Decimal conversion example 2

In the **v\_SecuredObject** view, the **SMS\_Collection** secured object has a value of 52435687 in the **AvailableInstancePermissions** column. This decimal number results in 11001000000001101011100111 when converted to binary. This is interpreted as shown in the following table.

| Permission Name | Binary Position | Decimal value |
| --- | --- | --- |
| Read | 1 | 1 |
| Modify | 2 | 2 |
| Delete | 3 | 4 |
| Use remote tools | 6 | 32 |
| Advertise | 7 | 64 |
| Modify resource | 8 | 128 |
| Delete resource | 10 | 512 |
| View collected files | 12 | 2048 |
| Read resource | 13 | 4096 |
| Modify collection setting | 22 | 2097152 |
| Manage management controllers | 25 | 16777216 |
| View management controllers | 26 | 33554432 |

## Role based administration views

This section describes the role based administration views in the Configuration Manager database.

### v\_Roles

Lists all available security roles at the Configuration Manager site. Includes information about whether the role is built-in, who created the role, the role name and description, and more. It is unlikely that this view will be joined to other views.

### v\_Admins

Returns all administrative users (that is, those who appear in the **Administrative Users** node under **Security** in the **Administration** workspace) This view can be joined to other views by using the **AdminID** column.

### v\_SecuredObjectTypes

Lists the various Configuration Manager objects that can be secured by role based administration. It is unlikely that this view will be joined to other views.

### v\_SecuredScopePermissions

Lists each user of the Configuration Manager site and the security roles they are associated with. This view can be joined to other views by using the **AdminID** column.