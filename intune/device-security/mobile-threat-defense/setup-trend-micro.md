---
layout: Conceptual
title: Set up Trend Micro MTD integration with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-trend-micro
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
description: How to set up Trend Micro Mobile Security with Microsoft Intune to control mobile device access to your corporate resources
ms.date: 2024-08-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 327c06ac-c926-f2a6-1896-030910f6fdb2
document_version_independent_id: 327c06ac-c926-f2a6-1896-030910f6fdb2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/setup-trend-micro.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/setup-trend-micro
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/setup-trend-micro.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/d01d0bfd-3c23-4b54-82d6-f9d06ad11cbd
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/da7889d8-fed4-4c4c-a52d-b6a3ea4ce02a
platformId: 0e8e13f1-3834-f575-e186-acc7b94b199e
---

# Set up Trend Micro MTD integration with Intune - Microsoft Intune | Microsoft Learn

Connect Trend Micro Mobile Security as a Service to monitor and mitigate device risk levels on Intune-managed devices. Trend Micro Mobile Security as a Service works by reporting device risk levels to Microsoft Intune. Intune then uses that information to enforce the appropriate app configuration and risk assessment policies. For more information about Trend Micro Mobile Security as a Service, see [Getting Started with Mobile Security](https://docs.trendmicro.com/documentation/article/trend-vision-one-getting-started-mobile-security) in the Trend Micro documentation.

This article describes the requirements and steps to connect Trend Micro Mobile Security as a Service in your tenant.

## Before you begin

The following subscriptions and accounts are required to integrate Trend Micro Mobile Security as a Service with Microsoft Intune.

- Microsoft Intune Plan 1 subscription
- Microsoft Entra account with Global Administrator rights to grant the following permissions:
    - Sign in and read user profile
    - Access the directory as the signed-in user
    - Read directory data
    - Send device information to Intune
- Admin sign-in credentials to access the Trend Micro Vision One management console

### Trend Micro Mobile Security as a Service App authorization

The following authorization process happens when you configure the integration with Trend Micro Mobile Security as a Service:

- Allow Trend Micro Mobile Security as a Service to communicate information related to device health state back to Intune. To grant these permissions, you must use Global Administrator credentials. Granting permissions is a one-time operation. After the permissions are granted, the Global Administrator credentials aren't needed for day-to-day operation.
- Allow Trend Micro Mobile Security as a Service to sync Microsoft Entra enrollment group membership to populate its device's database.
- Allow Trend Micro Vision One management console to use Microsoft Entra single sign-on (SSO).
- Allow Trend Micro Mobile as a Service agent app to sign in using Microsoft Entra SSO.
- Allow Trend Micro Mobile Security as a Service to get installed app information to perform malware scanning.
- Allow Trend Micro Mobile Security as a Service to add its mobile apps in Intune for deployment.
- Allow Trend Micro Mobile Security as a Service to create device configuration profiles.
- Allow Trend Micro Mobile Security as a Service to perform remote actions when necessary.

For more information about consent and Microsoft Entra applications, see [Introduction to permissions and consent](/en-us/azure/active-directory/develop/v2-permissions-and-consent).

## Configuration Overview

The configuration of Trend Micro Mobile Security as a Service and Intune integration can be done on [Trend Micro Vision One console](https://portal.xdr.trendmicro.com/) with the following steps:

1. **Configure Intune integration settings.** - Grant permissions required by Trend Micro Mobile Security as a Service, select the platforms of your mobile devices, and choose data synchronization frequency. Device configuration profiles and app configuration policies are created automatically in Intune.
2. **Select groups to install Trend Micro Mobile Security as a Service mobile app.** - Trend Micro Mobile Security as a Service mobile app installs automatically on devices in the selected groups.
3. **(Optional) Create mobile policies.** - Optionally create customized mobile security policies provided by Trend Micro Mobile Security as a Service. For more information, see [Configuring Mobile Policies](https://docs.trendmicro.com/enterprise/trend-micro-xdr-help/configuringmobilepolicy).
4. **Confirm mobile app status update.**

## Set up Mobile Security as a Service integration

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an Intune administrator account.
2. Go to **Tenant administration**.
3. Select **Connectors and tokens**.
4. Under **Cross platform**, select **Mobile Threat Defense**.
5. Select **Add**.
6. For **Select the Mobile Threat Defense connector to setup**, choose **Trend Micro**.
7. Select **Open the**[**Trend Micro Vision One console**](https://portal.xdr.trendmicro.com/). Keep the Microsoft Intune tab open for later.
8. Sign in with your Trend Micro Vision One administration account, and then follow the instructions in [Setting up Intune Integration](https://docs.trendmicro.com/en-us/enterprise/trend-vision-one/mobile-security/getting-started-with_003.aspx) (opens Trend Micro Mobile Security documentation) to complete setup.
9. After you finish setup in the Trend Micro Vision One console, Trend Micro Mobile Security as a Service is now available in Intune.