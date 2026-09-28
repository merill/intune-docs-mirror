---
layout: Conceptual
title: Set up Symantec Endpoint Protection Mobile integration with Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/mobile-threat-defense/setup-symantec
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
description: How to set up the Symantec Endpoint Protection Mobile solution with Microsoft Intune to control mobile device access to your corporate resources.
ms.date: 2024-08-27T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 6854de9c-f4ef-36c8-5483-2329b95d007a
document_version_independent_id: 6854de9c-f4ef-36c8-5483-2329b95d007a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/mobile-threat-defense/setup-symantec.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/mobile-threat-defense/setup-symantec
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/mobile-threat-defense/setup-symantec.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 2840b173-fb55-285a-9308-ecdcc54bc3a1
---

# Set up Symantec Endpoint Protection Mobile integration with Intune - Microsoft Intune | Microsoft Learn

Complete the following steps to integrate the Symantec Endpoint Protection Mobile (SEP Mobile) solution with Intune. You need to add SEP Mobile apps into Microsoft Entra ID P1 to have single sign-on capabilities.

Note

This Mobile Threat Defense vendor is not supported for unenrolled devices.

## Before you begin

### Microsoft Entra account used to integrate Intune and SEP Mobile

- Make sure you have the Microsoft Entra account properly configured in the [Symantec Endpoint Protection Mobile Management console](https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-protection/all/getting-up-and-running-on-for-the-first-time-v45150512-d43e1033/logging-on-to-the-console-v8025272-d23e2462.html) before starting the SEP Mobile Basic setup process.
- The Microsoft Entra account must be a global administrator account to perform the integration.

### Network Setup

You can make sure your network is properly configured for integration with SEP Mobile setup by referring to the Symantec article [Configuring SEP Manager after installation](https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-protection/all/getting-up-and-running-on-for-the-first-time-v45150512-d43e1033/configuring-after-installation-v18374552-d23e1454.html).

### Full integration vs. Read-only

SEP Mobile supports two modes of integration with Intune:

- **Read-only integration (Basic setup):**Only inventories devices from Microsoft Entra ID and populates them in the Symantec Endpoint Protection Mobile Management console.
    - If both the **Report the health and risk of devices to Intune** and **Also report security incidents to Intune** boxes aren't selected in the Symantec Endpoint Protection Mobile Management console, the integration is read-only and therefore will never change a device's state (compliant or noncompliant) in Intune.
- **Full integration:** Allows SEP Mobile to report devices on risk and security incident details to Intune, which creates a bi-directional communication between both cloud services.

### How are the SEP Mobile apps used with Microsoft Entra ID and Intune?

- **iOS app:** Allows end-users to sign in to Microsoft Entra ID using an iOS/iPadOS app.
- **Android app:** Allows end-users to sign in to Microsoft Entra ID using an Android app.
- **Management app:** This is the SEP Mobile Microsoft Entra multi-tenant app, which enables service-to-service communication with Intune.

## To set up the read-only integration between Intune and SEP Mobile

Important

The SEP Mobile admin credentials must consist of an e-mail account that belongs to a valid user in the Microsoft Entra, otherwise the login will fail. SEP Mobile uses Microsoft Entra ID to authenticate its admin using single sign-on (SSO).

1. Go to [Symantec Endpoint Protection Mobile Management Console](https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-protection/all/getting-up-and-running-on-for-the-first-time-v45150512-d43e1033/logging-on-to-the-console-v8025272-d23e2462.html).
2. Enter your **SEP Mobile admin credentials**, and then choose **Continue**.
3. Go to **Settings**, and under **Intune Integration**, choose **Basic Setup**.
4. Next to **iOS App**, choose **Entra ID**.
5. When the sign in page opens, enter your Intune credentials, and then choose **Accept**.

    ![Image of the iOS/iPadOS app Intune login prompt](media/setup-symantec/symantec-portal-basic-accept.png)
6. After the app is added to Microsoft Entra, you'll see an indication that the app was added successfully.
7. Repeat these steps for the **SEP Mobile Android** and **Management** apps.

### Add a Microsoft Entra security group into SEP Mobile

You need to add a Microsoft Entra security group that contains all devices running SEP Mobile.

- Enter and select all the security groups of devices that are running SEP Mobile, and then save the changes.

    ![Image showing user groups for SEP Mobile apps](media/setup-symantec/symantec-portal-basic-groups.png)

SEP Mobile syncs the devices running its Mobile Threat Defense service with the Microsoft Entra security groups.

![Image of Security group configuration on SEP Mobile management console](media/setup-symantec/symantec-portal-basic-status.png)

## To set up the full integration between Intune and SEP Mobile

### Retrieve the Directory ID in Microsoft Entra

1. Sign in to the [Azure portal](https://portal.azure.com).
2. Select **Microsoft Entra ID**.
3. Choose the **Properties** tab.
4. Next to the **Tenant ID**, choose the copy icon, and then paste it to a safe location. You need this identifier in a later step.

    ![Image showing Tenant ID in the Azure portal](media/setup-symantec/symantec-azure-portal-directory-id.png)

### (Optional) Create a dedicated Security Group for devices that need to run the SEP Mobile apps

1. In the [Azure portal](https://portal.azure.com), under **Manage**, choose **Users and groups**, and then choose **All groups**.
2. Choose the **Add** button. Type a group **Name**. Under **Membership type**, choose **Assigned**.
3. In the **Members** blade, select the group members, and then choose the **Select** button.
4. In the **Group** blade, choose **Create**.

### Set up the integration between Symantec Endpoint Protection Mobile and Intune

1. Go to [Symantec Endpoint Protection Mobile Management Console](https://techdocs.broadcom.com/us/en/symantec-security-software/endpoint-security-and-management/endpoint-protection/all/getting-up-and-running-on-for-the-first-time-v45150512-d43e1033/logging-on-to-the-console-v8025272-d23e2462.html).
2. Enter your **SEP Mobile admin credentials**, then choose **Continue**.
3. Go to the **Settings** &gt; **Integrations** &gt; **Intune** &gt; **EMM Integration Selection** section.
4. In the **Directory ID** box, paste the Tenant ID you copied from Microsoft Entra ID in the previous section and save the settings.
5. Go to the **Settings** &gt; **Integrations** &gt; **Intune** &gt; **Basic Setup** section.
6. Next to **iOS App**, choose the **Add to Microsoft Entra** button.
7. Sign in using the Microsoft Entra credentials for the Microsoft 365 account that manages the directory.
8. Choose the **Accept** button to add the SEP Mobile iOS/iPadOS app to Microsoft Entra.

    ![Image showing the accept button](media/setup-symantec/symantec-portal-basic-accept.png)
9. Repeat the same process for the **Android app** and the **Management App**.
10. Select all user groups that need to run the SEP Mobile apps, for example, the security group you created earlier.

![Image showing user groups for SEP Mobile apps](media/setup-symantec/symantec-portal-basic-groups.png)

1. SEP Mobile syncs the devices in the selected groups and starts reporting information to Intune. You can view this data in the Full Integration section. Go to the **Settings** &gt; **Integrations** &gt; **Intune** &gt; **Full Integration** section.

    ![Image showing SEP Mobile full integration completed](media/setup-symantec/symantec-portal-basic-status.png)