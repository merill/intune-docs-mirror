---
layout: Conceptual
title: Set up BlackBerry Protect with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-blackberry
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
description: How to set up the CylancePROTECT (BlackBerry) MTD solution with Microsoft Intune to control mobile device access to your corporate resources.
ms.date: 2024-08-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 71c806c3-970b-e821-f742-f1258a3a2b2a
document_version_independent_id: 71c806c3-970b-e821-f742-f1258a3a2b2a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/setup-blackberry.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/setup-blackberry
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/setup-blackberry.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: 94f021ff-7375-6229-5588-a9245e0bf11f
---

# Set up BlackBerry Protect with Microsoft Intune - Microsoft Intune | Microsoft Learn

Connect the BlackBerry Protect Mobile MTD connector to monitor and mitigate device risk levels on Intune-managed devices. BlackBerry Protect Mobile (powered by Cylance AI) works by reporting device risk levels to Microsoft Intune. Intune then uses that information to enforce the appropriate app configuration and risk assessment policies.

This article describes the requirements and steps to connect the MTD connector in your tenant.

## Before you begin

The following subscriptions and accounts are required to integrate UES with Microsoft Intune.

- Microsoft Intune Plan 1 subscription
- Microsoft Entra account with Global Administrator rights to grant the following permissions:

    - Sign in and read user profile
    - Access the directory as the signed-in user
    - Read directory data
    - Send device information to Intune

Caution

The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role, and should only be used when another role can't be used. This feature requires the Global Administrator role.

To reduce risk, assign the least-privileged role that can complete the task. For more information on the built-in Intune roles and what they can do, see [Role-based access control (RBAC) with Intune](../../fundamentals/role-based-access-control/overview) and [Built-in role permissions for Intune](../../fundamentals/role-based-access-control/ref-built-in-roles).
- Admin sign-in credentials to access the UES management console

### App authorization

The following authorization process happens when you connect the BlackBerry Protect Mobile MTD connector:

- Allow BlackBerry UES to communicate information related to device health state back to Intune. To grant these permissions, you must use Global Administrator credentials. Granting permissions is a one-time operation. After the permissions are granted, the Global Administrator credentials aren't needed for day-to-day operation.
- Allow BlackBerry UES to sync Microsoft Entra enrollment group membership to populate its device's database.
- Allow BlackBerry UES management console to use Microsoft Entra single sign-on (SSO).
- Allow BlackBerry Protect app to sign in using Microsoft Entra SSO.

For more information about consent and Microsoft Entra applications, see [Introduction to permissions and consent](/en-us/azure/active-directory/develop/v2-permissions-and-consent).

## Set up BlackBerry Protect Mobile MTD connector

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an Intune administrator account.
2. Go to **Tenant administration**.
3. Select **Connectors and tokens**.
4. Under **Cross platform**, select **Mobile Threat Defense**.
5. Select **Add**.
6. For **Select the Mobile Threat Defense connector to setup,** choose **CylancePROTECT Mobile**.
7. Select **Open the CylancePROTECT Mobile admin console**. Keep the Microsoft Intune admin center tab open for later.
8. Sign in with your Microsoft Entra account and complete the setup.
9. After you finish setup in the UES management console, return to your tab in the Microsoft Intune admin center.
10. Under **MDM Compliance Policy Settings**, turn on the following settings:
    - **Connect Android devices to BlackBerry Protect Mobile**
    - **Connect iOS devices to BlackBerry Protect Mobile** These settings allow BlackBerry Protect Mobile to evaluate the devices in your organization.
11. Select **Create** to save your connector configurations.