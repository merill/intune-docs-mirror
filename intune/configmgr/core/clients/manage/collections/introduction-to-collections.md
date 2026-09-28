---
layout: Conceptual
title: Collections introduction - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/collections/introduction-to-collections
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
description: Get an introduction to using collections in Configuration Manager.
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ebb41d4f-a321-d272-ba76-1e8b7e13ce22
document_version_independent_id: a00debf0-79da-be24-a689-d559883937a5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/collections/introduction-to-collections.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/collections/introduction-to-collections
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/collections/introduction-to-collections.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 504534af-366e-c06e-cc95-1a2db3e867ae
---

# Collections introduction - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Collections help you organize resources into manageable units. You can create collections to match your client management needs, and to perform operations on multiple resources at one time.

Most management tasks rely on or require using one or more collections. Although you can use the built-in collection of All Systems, using it for management tasks is not a best practice. Create custom collections to more specifically identify the devices or users for a task.

Built-in and custom collections appear in the **User Collections** and **Device Collections** nodes in the **Assets and Compliance** workspace in the Configuration Manager console.

Collections that you have recently viewed appear in the **Users** node and in the **Devices** node in the **Assets and Compliance** workspace.

Here are some examples of collection use:

| Operation | Example |
| --- | --- |
| Grouping resources | You can create collections that group resources based on your organization's hierarchy. For example, you could create a collection of all computers in the "London Headquarters" Active Directory Organizational Unit (OU). For more information about how to create this type of collection, see [How to create collections](create-collections). You could use this collection for operations such as configuring Endpoint Protection settings, configuring device power management settings, or installing the Configuration Manager client. |
| Application deployment | You can create a collection of all computers that do not have Microsoft Microsoft 365 Apps installed and then deploy it to all computers in that collection. You can also use application requirements to perform this task. For more information, see [How to create applications with Configuration Manager](../../../../apps/deploy-use/create-applications). |
| [Managing client settings](../../deploy/about-client-settings) | Although the default client settings in Configuration Manager apply to all devices and all users, you can create custom client settings that apply to a collection of devices or a collection of users. For example, if you want remote control to be available on all but a few devices, configure the default client settings to allow remote control and then configure custom client settings that do not allow remote control, and deploy those to the collection of exceptional clients. |
| [Power management](../power/introduction-to-power-management) | You can configure specific power settings per collection. |
| [Role-based administration](../../../servers/deploy/configure/configure-role-based-administration) | Use collections to control which groups of users have access to various functionality in the Configuration Manager console. |
| [Maintenance Windows](use-maintenance-windows) | With maintenance windows you can define a time period when various Configuration Manager operations can be carried out on members of a device collection. |

## Collection types in Configuration Manager

Configuration Manager has built-in collections for common operations, and you can also create custom collections.

### Built-in collections

By default, Configuration Manager includes the following collections, which cannot be modified.

| **Collection name** | Description |
| --- | --- |
| **All User Groups** | Contains the user groups that are discovered by using Active Directory Security Group Discovery. |
| **All Users** | Contains the users who are discovered by using Active Directory User Discovery. |
| **All Users and User Groups** | Contains the All Users and the All User Groups collections. This collection contains the largest scope of user and user group resources. |
| **All Desktop and Server Clients** | Contains the server and desktop devices that have the Configuration Manager client installed. Membership is maintained by Heartbeat Discovery. |
| **All Mobile Devices** | Contains the mobile devices that are managed by Configuration Manager. Membership is restricted to those mobile devices that are successfully assigned to a site or discovered by the Exchange Server connector. |
| **All Systems** | Contains the All Desktop and Server Clients, the All Mobile Devices, and the All Unknown Computers collections, and all mobile devices that are enrolled by Microsoft Intune. This collection contains the largest scope of device resources. |
| **All Unknown Computers** | Contains generic computer records for multiple computer platforms. You can use this collection to deploy an operating system by using a task sequence and PXE boot, bootable media, or prestaged media. |
| **Co-management Eligible Devices** | Contains devices that meet the client prerequisites and are eligible for co-management enrollment (added in version 2111). |

### Custom collections

When you create a custom collection in Configuration Manager, the membership of that collection is determined by one or more collection rules, as described in [How to create collections](create-collections).