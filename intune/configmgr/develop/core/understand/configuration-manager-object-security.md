---
layout: Conceptual
title: Object Security - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/configuration-manager-object-security
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
description: The delegate verb in Configuration Manager provides administrators with a way of allowing users to assign to other users the instance permissions to an object in a very limited way.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 5f34910e-3809-ae8b-c97b-15320406dfb2
document_version_independent_id: 4623393a-2c49-6c45-d90f-41fb600607f3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/configuration-manager-object-security.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/configuration-manager-object-security
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/configuration-manager-object-security.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 0f96d70c-815b-0903-9716-0319f90696bb
---

# Object Security - Configuration Manager | Microsoft Learn

## Delegate Verb

The delegate verb in Configuration Manager provides administrators with a way of allowing users to assign to other users the instance permissions to an object in a very limited way. The rights that a user is allowed to assign (or revoke) to other users are limited to the instance rights that have been explicitly granted to that user. When a user creates a secured object, that user is automatically granted explicit instance rights to that object (usually read, modify, and delete).

To some extent, these explicitly granted rights provide the user with a certain level of ownership of the object. With the delegate right, this ownership is extended to the control of the default group of instance rights. To limit which rights a user can delegate, only rights explicitly granted to them (not a group to which they belong) can be delegated. A user can also remove other users (or groups) instance rights if the user has the delegate permission and explicit rights to an object (this is why a user is said to own an object if they have explicit instance rights). Users with administrator rights still have full control of administering permissions.

A common scenario for using the delegate verb is when a user has created and delegated rights for an object type and wants to create an object and allow members of a user group to see it. They create an instance of the object and then delegate read permissions for the instance to the user group.

The delegate verb is applicable to the following Configuration Manager classes:

- `SMS_Collection`
- `SMS_Package`
- `SMS_Advertisement`
- `SMS_Site`
- `SMS_Query`
- `SMS_Report`
- `SMS_MeteredProductRule`

## System Resource (SMS\_R\_System) as a Secured Resource

Secured resources are resources (the SMS\_R\_\* classes) that require collection read rights to be viewed. If the user has class-level collection read rights, the user can see all the instances of a secured resource. If the user only has instance-level read rights to certain collections, the user only has rights to see resources that are members of those collections. `SMS_R_User` and `SMS_R_UserGroup` are secured resources in SMS 2.0. In SMS 2003, `SMS_R_System` (the system resource) is also a secured resource.

Inventory instances (SMS\_G\_System\_\*) are secured similarly with the read resource verb. If a user has class-level rights, that user can see inventory data belonging to all resources. If the user doesn't have class-level rights, the user can see only inventory data for inventory that belongs to resources that are members of collections to which the user has instance-level read resource rights. Conversely, if a user has read resource rights to a collection, a user can see the inventory data for the members of that collection. This hasn't been affected by the change in security to `SMS_R_System`. Read resource rights can't be granted to a user without granting read rights. When a user doesn't have the appropriate class-level collection rights, resource security is enforced through collection limiting.

## Securing File Submissions to a Configuration Manager Server

The recommended location for copying data discovery record (DDR) files and Managed Information Format (MIF) files that not related to existing Configuration Manager clients is directly in the site server inboxes. This requires administrator level permissions on the site server to be granted to the application that is copying these files. These are located as follows:

DDR files: &lt;SMS&gt;/inboxes/ddm.box

MIF files: &lt;SMS&gt;/inboxes/inventry.box