---
layout: Conceptual
title: Set up Trellix Mobile Security MTD with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-trellix
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-mtd-apps
ms.reviewer: ilwu
ms.subservice: protect
description: How to set up the Trellix Mobile Security mobile threat defense (MTD) solution with Microsoft Intune to control mobile device access to your corporate resources
ms.date: 2024-08-23T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 17f50ec3-ce2a-7f2f-fc06-463ec254938a
document_version_independent_id: 17f50ec3-ce2a-7f2f-fc06-463ec254938a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/setup-trellix.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/setup-trellix
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/setup-trellix.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: b9f40788-3a9b-14c7-90f3-806ea52f85a7
---

# Set up Trellix Mobile Security MTD with Microsoft Intune - Microsoft Intune | Microsoft Learn

Complete the following steps to integrate the Trellix Mobile Security threat defense solution with Intune.

## Before you begin

The following steps are done in the [Trellix console](https://manage.trellix.com) to enable a connection to the Trellix service for Intune enrolled devices (using device compliance) and unenrolled devices (using app protection policies).

Before starting the process of integrating Trellix Mobile Security with Intune, make sure you have the following subscription and credentials:

- Microsoft Intune Plan 1 subscription
- Microsoft Entra Global Administrator admin credentials to grant the following permissions:

    - Sign in and read user profile
    - Access the directory as the signed-in user
    - Read directory data
    - Send device information to Intune
- Admin credentials to access the Trellix console.

### Trellix Mobile Security app authorization

The Trellix Mobile Security app authorization process follows:

- Grant the Trellix Mobile Security service permissions to communicate information related to device health state back to Intune. To grant these permissions, you must use Global Administrator credentials. Granting permissions is a one-time operation. After the permissions are granted, the Global Administrator credentials aren't needed for day to day operation.
- Trellix Mobile Security syncs with Microsoft Entra Enrollment Group membership to populate its device's database.
- Allow Trellix Mobile Security admin console to use Microsoft Entra Single Sign On (SSO).
- Allow the Trellix Mobile Security app to sign in using Microsoft Entra SSO.

For more information about consent and Microsoft Entra applications, see [Request the permissions from a directory admin](/en-us/azure/active-directory/develop/v2-permissions-and-consent#request-the-permissions-from-a-directory-admin) in the Microsoft Entra article *Permissions and consent in the Microsoft Entra v2.0 endpoint*.

## To set up Trellix Mobile Security integration

1. Open the [Trellix console](https://manage.trellix.com) and sign in with your credentials. To perform the Trellix Mobile Security integration setup process, you must sign in with a Microsoft Entra user who has the Global Administrator role. This one-time setup operation uses the Global Administrator rights to grant permission in your organization for the Trellix Mobile Security apps to communicate with Intune.
2. Choose **Manage** from the left menu.
3. Choose the **Integrations** tab.
4. Choose **Add MDM,** then select **Microsoft Intune** from the **MDM provider** list.
5. After you set Microsoft Intune as the MDM service, the **Microsoft Intune Configuration** window pops up, choose the **Add Microsoft Entra ID** for each option: **Trellix console**, **Trellix Mobile Security iOS and Android apps** to authorize Trellix Mobile Security to communicate with Intune and Microsoft Entra ID through Microsoft Entra single sign-on.

    Important

    You must add the console, and the Trellix Mobile Security iOS and Android apps to complete the integration process with Intune.
6. Choose **Accept** to authorize the Trellix Mobile Security app to communicate with Intune and Microsoft Entra ID.
7. After you add the console and Trellix Mobile Security iOS and Android apps to Microsoft Entra ID, add the Microsoft Entra security groups. This addition allows Trellix Mobile Security to synchronize the Microsoft Entra security group with its service.
8. Choose **Finish** to save the configuration and start the first Microsoft Entra security group synchronization.
9. Sign out of the Trellix Mobile Security MTD console.