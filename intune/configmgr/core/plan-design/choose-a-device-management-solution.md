---
layout: Conceptual
title: Choose a device management solution - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/choose-a-device-management-solution
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
description: Learn about the solutions that Microsoft offers for managing PCs, servers, and devices.
ms.date: 2023-03-30T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 251e3356-f041-2145-5879-d89969ae35dd
document_version_independent_id: bba0b8a2-7622-705f-0283-e32460b58880
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/choose-a-device-management-solution.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/choose-a-device-management-solution
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/choose-a-device-management-solution.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://authoring-docs-microsoft.poolparty.biz/devrel/beac614b-f66d-40ed-a947-3996de709333
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://authoring-docs-microsoft.poolparty.biz/devrel/9da05372-4706-43ec-a899-f436adab380d
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2e31dfc5-2a57-b102-f538-eac406a31224
---

# Choose a device management solution - Configuration Manager | Microsoft Learn

Microsoft offers different solutions for managing PCs, servers, and devices. These solutions are available on-premises, cloud-based, or a combination of both. Choose the solution that's right for the business requirements of your organization. Base your decision on the device platforms you need to manage and the management functionality you need.

## Overview

There are several Microsoft solutions that might work best for you in different scenarios. You don't need to choose just one.

- For a small organization, a tool like the Windows administration center may be a great fit.
- Approximately 75% of IT organizations use Configuration Manager to manage their devices.
- Microsoft Azure provides various solutions from the cloud or on-premises with Azure Arc and Azure Stack that primarily target server management.
- Microsoft Intune provides cloud management of clients.
- You can combine Configuration Manager and Intune with co-management.
- You can use [Security Management for Microsoft Defender for Endpoint (MDE)](../../../device-security/microsoft-defender/security-settings-management) to manage security settings for devices utilizing Microsoft Defender for Endpoint.

Use the following table to help compare these management technologies:

| - | Cloud-only | Cloud-attached | On-premises | Disconnected |
| --- | --- | --- | --- | --- |
| **Hyper-V host** | Not applicable | - Azure Stack - Windows Admin Center - Security Management for MDE - Virtual Machine Manager | - Azure Stack - Windows Admin Center - Virtual Machine Manager | - Azure Stack - Windows Admin Center - Virtual Machine Manager |
| **Windows Server** | - Azure Arc  - Configuration Manager - Security Management for MDE | - Azure Arc - Configuration Manager  - Security Management for MDE | - Azure Arc - Configuration Manager | Configuration Manager |
| **Linux Server** | Azure Arc | Azure Arc | Azure Arc |  |
| **Windows 10/11** | - Intune - Configuration Manager - Security Management for MDE | - Intune - Configuration Manager - Security Management for MDE | - Intune - Configuration Manager - Security Management for MDE | Configuration Manager |
| **Windows 7 or 8.1** | Configuration Manager | Configuration Manager | Configuration Manager | Configuration Manager |
| **Azure Virtual Desktop** | Configuration Manager | Not applicable | Not applicable | Not applicable |

For more information, see the following articles:

- [What is Azure Stack?](/en-us/azure-stack/operator/azure-stack-overview)
- [What is Windows Admin Center?](/en-us/windows-server/manage/windows-admin-center/understand/what-is)
- [What is Virtual Machine Manager?](/en-us/system-center/vmm/overview)
- [Azure Arc products](/en-us/azure/)
- [What is Azure Virtual Desktop?](/en-us/azure/virtual-desktop/overview)
- [Security Management for Microsoft Defender for Endpoint (MDE)](../../../device-security/microsoft-defender/security-settings-management)

For more information on the Configuration Manager and Intune solutions, continue to the next section.

## Client management

This section compares the following four client management solutions:

- Configuration Manager client
- Co-management with Microsoft Intune
- Microsoft Exchange

You can use these solutions by themselves or in combination with each other. For example, use the client-based management approach to manage the computers and servers in your organization, and also use co-management to manage internet-based laptops. By combining approaches this way, you can cover all of your device management needs.

There are also two tables that compare the management solutions by the following factors:

- Compare by supported platforms
- Compare by management functionality

### Configuration Manager client

This option requires installation of the Configuration Manager client on devices. It provides the most features for managing PCs, servers, and other devices in your environment.

For more information, see [Client installation methods](../clients/deploy/plan/client-installation-methods).

### Security Management for Microsoft Defender for Endpoint

This options requires utilizing Microsoft Defender for Endpoint on your devices and is intended to provide security management capability in circumstances where Microsoft Intune or Microsoft Configuration Manager are not present. This uses the Microsoft Defender for Endpoint client to communicate directly with Intune and apply security management policy.

For more information, see [Security Management for Microsoft Defender for Endpoint (MDE)](../../../device-security/microsoft-defender/security-settings-management).

### Co-management with Microsoft Intune

Co-management is one of the primary ways to attach your existing Configuration Manager deployment to the Microsoft 365 cloud. It enables you to concurrently manage Windows devices by using both Configuration Manager and Microsoft Intune. Co-management lets you cloud-attach your existing investment in Configuration Manager by adding new functionality.

For more information, see [What is co-management?](../../comanage/overview).

### Microsoft Exchange

This option uses the Exchange Server connector to connect multiple Exchange servers to Configuration Manager. It centralizes management of devices that can connect to Exchange ActiveSync. You can configure Exchange mobile device management features from the Configuration Manager console. Example features include remote device wipe and the settings control for multiple Exchange servers.

For more information, see [Manage mobile devices with Configuration Manager and Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync).

### Compare solutions by supported platforms

| Platform | Configuration Manager client | On-premises MDM | Configuration Manager with Exchange | Intune |
| --- | --- | --- | --- | --- |
| Android |  |  | Yes | Yes |
| iOS |  |  | Yes | Yes |
| macOS X | Yes |  | Yes | Yes |
| Windows 10/11 | Yes | Yes | Yes | Yes |
| Windows 10 Mobile |  | Yes | Yes | Yes |
| Windows (previous versions) | Yes |  | Yes |  |
| Windows Server | Yes |  | Yes |  |
| Windows Embedded | Yes |  |  |  |

For a complete list of supported platforms, see the following articles:

- [Supported operating systems for clients and devices for Configuration Manager](configs/supported-operating-systems-for-clients-and-devices)
- [Intune supported configurations](/en-us/mem/fundamentals/ref-supported-platforms)

Microsoft recommends using Intune to manage Android, iOS, and Windows 10/11 mobile devices. For more information, see [What is Microsoft Intune?](/en-us/mem/fundamentals/what-is-intune).

### Compare solutions by management functionality

| Management functionality | Configuration Manager client | On-premises MDM | Configuration Manager with Exchange |
| --- | --- | --- | --- |
| Certificate-based mutual authentication | Yes | Yes |  |
| Client installation | Yes |  |  |
| Support over the internet | Yes |  |  |
| Discovery | Yes |  | Yes |
| Hardware inventory | Yes | Yes | Yes |
| Software inventory | Yes |  | Yes |
| Settings | Yes | Yes | Yes |
| Software deployment | Yes | Yes |  |
| Software update management | Yes |  |  |
| OS deployment | Yes |  |  |
| Block from Configuration Manager | Yes | Yes |  |
| Quarantine and block from Exchange Server (and Configuration Manager) |  |  | Yes |
| Remote wipe |  | Yes | Yes |