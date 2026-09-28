---
layout: Conceptual
title: Miscellaneous policy mapping from Basic Mobility and Security to Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/ref-policy-map-miscellaneous
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: A detailed miscellaneous policy map between Basic Mobility and Security access requirements and Intune.
ms.date: 2025-12-03T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: dagerrit
locale: en-us
document_id: 737432c3-223e-5f53-6885-eb20dbd75bf1
document_version_independent_id: 737432c3-223e-5f53-6885-eb20dbd75bf1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/ref-policy-map-miscellaneous.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/ref-policy-map-miscellaneous
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/ref-policy-map-miscellaneous.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/57eae111-0f3b-497e-be07-450fd1409dea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ac8bf8ab-8134-4c9a-9f2e-58b31575b492
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 7b7c247a-86b7-caed-f00e-87452f0f5b40
---

# Miscellaneous policy mapping from Basic Mobility and Security to Intune - Microsoft Intune | Microsoft Learn

This article provides mapping details between Basic Mobility and Security to Intune. Specifically, this page maps the following Microsoft Purview compliance portal policies and device properties to the equivalent policies and properties in the Microsoft Intune admin center:

- Device properties and actions
- Organization-wide device access settings
- Device security policies Name and Description

Intune offers more policy flexibility. So, each Office policy translates into multiple Intune and Microsoft Entra policies to achieve the same result.

## Device properties and actions

To see these settings, sign in to the [Microsoft 365 admin center](https://portal.office.com/adminportal/home#/MifoDevices) and then select a device.

### User

- **Devices** &gt; **All devices** &gt; device name &gt; **Overview** &gt; **Enrolled by**

### Device type

- **Devices** &gt; **All devices** &gt; device name &gt; **Overview** &gt; **Operating system**

### State

This setting isn't a default column in the admin center device list. You can show it by using the **Columns** picker.

- **Devices** &gt; **All devices** &gt; **Device state** column

### OS version

- **Devices** &gt; **All devices** &gt; device name &gt; **Hardware** &gt; **Operating system version**

### Factory reset

- **Devices** &gt; **All devices** &gt; device name &gt; **Overview** &gt; **Wipe**

### Remove company data

- **Devices** &gt; **All devices** &gt; device name &gt; **Overview** &gt; **Retire**

## Organization-wide device access settings

To see these settings in the Microsoft Purview compliance portal, sign in to the [Purview compliance portal](https://protection.office.com/devicev2). Then, select **Device security policies** &gt; **Manage organization-wide device access settings**.

These settings are backed by the Conditional Access policy [GraphAggregatorService] Device policy. It includes:

- Device platforms: iOS, Android
- Target client apps: Mobile app desktop clients
- Access controls: require compliant device

### If a device isn't supported by MDM for Office 365, do you want to allow or block it from using an Exchange account to access your organization's email?

This setting modifies one classic Conditional Access policy:

- **Endpoint security** &gt; **Conditional Access** &gt; **Classic policies** &gt; **[GraphAggregatorService] Device policy** &gt; **Conditions** &gt; **Client apps (Preview)** &gt; **Mobile apps and desktop clients** &gt; **Exchange ActiveSync clients** &gt; **Apply policy only to supported platform**

### Are there any security groups you want to exclude from access control?

This setting modifies five classic Conditional Access policies:

- [GraphAggregatorService] Device policy
- [Office 365 Exchange Online] Device policy
- [Outlook Service for Exchange] Device policy
- [Office 365 SharePoint Online] Device policy
- [Outlook Service for OneDrive] Device policy
- **Endpoint security** &gt; **Conditional Access** &gt; policy name &gt; **Users and groups** &gt; **Exclude**

## Device security policy Name and Description

To see these settings in the Microsoft Purview compliance portal, sign in to the [Purview compliance portal](https://protection.office.com/devicev2). Then, select **Device security policies** &gt; policy name &gt; **Edit policy** &gt; **Name**.

### Name

Up to three compliance policies and up to six configuration profiles (three for restrictions and three for email):

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_W &gt; **Properties** &gt; **Basics Edit** &gt; **Name**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_i &gt; **Properties** &gt; **Basics Edit** &gt; **Name**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Basics Edit** &gt; **Name**
- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Configuration** &gt; policy name\_O365\_W &gt; **Properties** &gt; **Basics Edit** &gt; **Name**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration**&gt; policy name\_O365\_i &gt; **Properties** &gt; **Basics Edit** &gt; **Name**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Configuration** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Basics Edit** &gt; **Name**
- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Configuration** &gt; policy name\_O365\_W\_Email &gt; **Properties** &gt; **Basics Edit** &gt; **Name**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration**&gt; policy name\_O365\_i\_Email &gt; **Properties** &gt; **Basics Edit** &gt; **Name**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Configuration** &gt; policy name\_O365\_A\_Email &gt; **Properties** &gt; **Basics Edit** &gt; **Name**

### Description

Up to three compliance policies and up to six configuration profiles (three for restrictions and three for email):

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_W &gt; **Properties** &gt; **Basics Edit** &gt; **Description**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_i &gt; **Properties** &gt; **Basics Edit** &gt; **Description**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Basics Edit** &gt; **Description**
- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Configuration** &gt; policy name\_O365\_W &gt; **Properties** &gt; **Basics Edit** &gt; **Description**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration**&gt; policy name\_O365\_i &gt; **Properties** &gt; **Basics Edit** &gt; **Description**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Configuration** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Basics Edit** &gt; **Description**
- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Configuration** &gt; policy name\_O365\_W\_Email &gt; **Properties** &gt; **Basics Edit** &gt; **Description**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration**&gt; policy name\_O365\_i\_Email &gt; **Properties** &gt; **Basics Edit** &gt; **Description**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Configuration** &gt; policy name\_O365\_A\_Email &gt; **Properties** &gt; **Basics Edit** &gt; **Description**

## Related article

- [Move from Basic Mobility and Security to Intune](migrate-from-other-mdm)