---
layout: Conceptual
title: Set up Sophos Mobile integration with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-sophos
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
description: How to set up the Sophos Mobile solution with Microsoft Intune to control mobile device access to your corporate resources.
ms.date: 2024-08-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: e8a4ee77-3811-16f5-e57c-2cb283171088
document_version_independent_id: e8a4ee77-3811-16f5-e57c-2cb283171088
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/setup-sophos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/setup-sophos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/setup-sophos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
platformId: 891ae9b6-cf08-b5c6-e568-95471f9363e9
---

# Set up Sophos Mobile integration with Intune - Microsoft Intune | Microsoft Learn

Complete the following steps to integrate the Sophos Mobile Threat Defense solution with Intune.

Note

This Mobile Threat Defense vendor is not supported for unenrolled devices.

## Before you begin

Before starting the process of integrating Sophos Mobile with Intune, make sure you have the following:

- Microsoft Intune Plan 1 subscription
- Microsoft Entra admin credentials to grant the following permissions:
    - Sign in and read user profile
    - Access the directory as the signed-in user
    - Read directory data
    - Send device information to Intune
- Admin credentials to access the Sophos Mobile admin console

### Sophos Mobile app authorization

The Sophos Mobile app authorization process follows:

- Allow the Sophos Mobile service to communicate information related to device health state back to Intune.
- Sophos Mobile syncs with Microsoft Entra Enrollment Group membership to populate its device's database.
- Allow the Sophos Mobile admin console to use Microsoft Entra single sign-on (SSO).
- Allow the Sophos Mobile app to sign in using Microsoft Entra SSO

## To set up Sophos Mobile integration

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Tenant administration** &gt; **Connectors and tokens** &gt; **Mobile Threat Defense** &gt; and select **Add**.
2. On the **Add Connector** page, use the dropdown and select **Sophos**. And then select **Create**.
3. Select the link *Open the Sophos admin console*.
4. Sign in to the [Sophos admin console](https://central.sophos.com/) with your Sophos credentials.
5. Go to **Mobile** &gt; **Settings** &gt; **Setup** &gt; **Sophos setup**.
6. On the **Sophos setup** page, select the **Intune MTD** tab.

    ![Sophos setup](media/setup-sophos/sophos-setup.png)
7. Select **Bind**, and then select **Yes**. Sophos connects to Intune and requires you to sign in to your Intune subscription.
8. In the Microsoft Intune authentication window, enter your Intune credentials and **Accept** the permissions request for *Sophos Mobile Threat Defense*.

    ![Intune authentication](media/setup-sophos/intune-authentication.png)
9. On the **Sophos setup** page, select **Save** to complete the configuration for Intune:

    ![Save Sophos setup](media/setup-sophos/save-sophos-configuration.png)
10. When the message **Successful Integration** appears, integration is complete.
11. In the Intune admin center, Sophos is now available.