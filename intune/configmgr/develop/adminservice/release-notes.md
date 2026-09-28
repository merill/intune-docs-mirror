---
layout: Conceptual
title: Admin service release notes - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/adminservice/release-notes
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
description: Information about changes to the administration service with each Configuration Manager release
ms.date: 2020-08-11T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: release-notes
ms.collection: tier3
locale: en-us
document_id: 56cb2c8e-7a30-7c67-b33f-f3b47d9a7b86
document_version_independent_id: eaa6c3e1-6a0a-df76-1018-0cd336672e63
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/adminservice/release-notes.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/adminservice/release-notes
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/adminservice/release-notes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/d3197845-b4ce-44c6-a237-cd4be160e76c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aea905fb-0a9d-4d46-b30f-e9cbaf772d1b
platformId: b2020d36-9c6a-c5db-2e2f-89e4d7126583
---

# Admin service release notes - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

## Changes in version 2006

The WMI route is now case-insensitive. For example, in version 2002, you had to specify `AdminService/wmi/SMS_Site`. Now in version 2006, you can also use `AdminService/wmi/sms_site`

## Changes in version 2002

Starting in version 2002, the administration service automatically uses the site's self-signed certificate. This change helps reduce the friction for easier use of the administration service. The site always generates this certificate. Now the administration service ignores the Enhanced HTTP site setting, as it always uses the site's certificate even if no other site system is using Enhanced HTTP. For more information, see [Enable secure HTTPS communication](set-up#enable-secure-https-communication).

New properties for the v1.0 Device class:

- Events on a device: `Device(<ResourceID>)/Events`
- Application on a device: `Device(<ResourceID>)/AvailableApplications?$expand=Application`
- Boundary groups on a device: `Device(<ResourceID>)/BoundaryGroups?$expand=BoundaryGroup`

## Changes in version 1910

- The WMI route now supports static WMI methods. For example:

    ```rest
    Verb: Post
    URI: https://<ProviderFQDN>/AdminService/wmi/SMS_Admin.GetAdminExtendedData
    Body: {"Type":1}
    ```
- The Configuration Manager console now sends console connection health information through the administration service.
- Use OData query options **startswith** and **endswith** on WMI route. For example: `https://<ProviderFQDN>/AdminService/wmi/SMS_Collection?$filter=startswith(Name,'All') eq true`
- Use the Power BI Desktop feature to get data from an **OData feed**. You can then see all WMI entities and their objects in Power BI Desktop to create custom reports.
- The **v1.0** route exposes the **Device** class. For example: `https://<ProviderFQDN>/AdminService/v1.0/Device`

Tip

For more examples, see [How to use the administration service](usage).

### Classes available to the WMI route in version 1910

- SMS\_ReplicationGroup
- SMS\_BoundaryGroup
- SMS\_G\_System\_DISK
- SMS\_G\_System\_LOGICAL\_DISK
- SMS\_G\_System\_OPERATING\_SYSTEM
- SMS\_G\_System\_PARTITION
- SMS\_G\_System\_PHYSICAL\_DISK
- SMS\_G\_System\_PHYSICAL\_MEMORY
- SMS\_G\_System\_X86\_PC\_MEMORY
- SMS\_DistributionDPStatus
- SMS\_WinPEOptionalComponentInfo
- SMS\_OSDeploymentKitWinPEOptionalComponent
- SMS\_WinPEOptionalComponentInBootImage
- SMS\_G\_System\_AdvancedThreatProtectionHealthStatus
- SMS\_SearchFolder
- SMS\_DPStatusDetails