---
layout: Conceptual
title: Get an Apple MDM Push certificate for Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/create-mdm-push-certificate
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: beflamm
ms.subservice: enrollment
description: Get an Apple MDM Push certificate to manage iOS/iPadOS devices with Intune.
ms.date: 2025-05-12T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 54cb288f-9f34-16b1-c480-524d5dfb25fa
document_version_independent_id: 54cb288f-9f34-16b1-c480-524d5dfb25fa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/create-mdm-push-certificate.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/create-mdm-push-certificate
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/create-mdm-push-certificate.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 92385a1f-4b9d-4fb0-638f-c73f26cc1642
---

# Get an Apple MDM Push certificate for Intune - Microsoft Intune | Microsoft Learn

Upload and renew your Apple MDM push certificates in Microsoft Intune. An Apple MDM Push certificate is required to manage iOS/iPadOS and macOS devices in Microsoft Intune, and enables devices to enroll via:

- The Intune Company Portal app.
- Apple bulk enrollment methods, such as Apple Business, Apple School Manager, and Apple Configurator.

Certificates must be renewed annually. This article describes how to use Intune to create and renew an Apple MDM push certificate.

## Requirements

Use an [Intune-supported web browser](../../fundamentals/ref-supported-platforms#intune-supported-web-browsers) to create and renew an Apple MDM push certificate.

## Steps to get your certificate

Access your Apple MDM push certificate settings in Microsoft Intune.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices**.
3. Expand **Device onboarding**, and then select **Enrollment**.
4. Select the **Apple** tab.
5. Select **Apple MDM Push Certificate**. Your MDM push certificate settings open.

### Step 1: Grant Microsoft permission to send user and device information to Apple

Select **I agree** to give Microsoft permission to send data to Apple.

![Screenshot of the Configure MDM Push Certificate screen with MDM Push not set up.](media/create-mdm-push-certificate/create-mdm-push-certificate.png)

### Step 2: Download the Intune certificate signing request required to create an Apple MDM push certificate

Select **Download your CSR** to download and save the request file locally. The file is used to request a trust relationship certificate from the Apple Push Certificates Portal.

### Step 3. Create an Apple MDM push certificate

1. Select **Create your MDM push Certificate** to go to the [Apple Push Certificates Portal](https://identity.apple.com/).
2. Sign in with your organization's Apple ID.
3. Select **Create a Certificate**.
4. Read and accept the terms and conditions.
5. Select **Choose File** and then select the CSR file you downloaded in Intune.
6. Select **Upload**.
7. On the confirmation page, select **Download**. The certificate file (.pem) downloads to your device. Save this file for later.

Note

- The certificate is associated with the Apple ID used to create it. As a best practice, use a company email address as your Apple ID and make sure the mailbox is monitored by more than one person, such as by a distribution list. Avoid using a personal Apple ID.
- If you later change the Apple ID associated with your certificate, sign in to the Apple Push Certificates Portal with your new Apple ID, redownload the certificate file, and upload it to Intune with your new Apple ID as described in [Step 4](create-mdm-push-certificate#step-4-enter-the-apple-id-used-to-create-your-apple-mdm-push-certificate) and [Step 5](create-mdm-push-certificate#step-5-browse-to-your-apple-mdm-push-certificate-to-upload) in this article.

#### Managed Apple ID

If you plan to federate your existing Microsoft Entra accounts with Apple to use Managed Apple ID, contact Apple to have the existing APNS certificate migrated to your new Managed Apple ID. For more information, see the Apple Support [user guide for Apple School Manager](https://support.apple.com/guide/apple-school-manager/apd6603d9206/web).

### Step 4: Enter the Apple ID used to create your Apple MDM push certificate

Return to the admin center and enter your Apple ID. This is needed to remind you when you need to renew the certificate.

### Step 5: Browse to your Apple MDM push certificate to upload

1. Select the **Folder** icon.
2. Select the certificate file (.pem) you downloaded in the Apple portal.
3. Select **Upload** to finish configuring the MDM push certificate.

## Renew Apple MDM push certificate

The Apple MDM push certificate is valid for 365 days. You must renew it annually to maintain iOS/iPadOS and macOS device management. Once the certificate expires, there is a 30-day grace period to renew it.

Renew the MDM push certificate with the same Apple account you used to create it.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices**.
3. Go to **Device onboarding** &gt; **Enrollment**.
4. Select the **Apple** tab.
5. Select **Apple MDM Push Certificate**. Your MDM push certificate settings open.
6. Select **Download your CSR** to download and save the request file locally. The file is used to request a trust relationship certificate from the Apple Push Certificates Portal.
7. Select **Create your MDM push Certificate** to go to the [Apple Push Certificates Portal](https://identity.apple.com/).
8. In the Apple portal, find the certificate you want to renew and select **Renew**.
9. Select **Choose File**. Choose the new CSR file you downloaded.
10. In the provided field, enter a unique note about the certificate so that you can easily identify it later.

Tip

Each certificate has a unique UID. To find it, look for the subject ID, which shows the GUID portion of the UID, in the certificate details. You can also find this information on the enrolled iOS/iPadOS device. Go to **Settings** &gt; **General** &gt; **Device Management** &gt; **Management Profile** &gt; **More Details** &gt; **Management Profile**. The **Topic** value contains the unique GUID that you can match up to the certificate in the Apple Push Certificates portal. 11. Select **Upload**. 12. On the **Confirmation** screen, select **Download**. 13. Return to the admin center and upload your certificate file.

Renewal is complete when your Apple MDM push certificate status appears active in both the admin center and Apple Push Certificates portal.