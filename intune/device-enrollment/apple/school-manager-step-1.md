---
layout: Conceptual
title: Apple School Manager - get Apple token and assign devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/school-manager-step-1
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: annovich
ms.subservice: enrollment
description: Get the Apple token needed to set up Apple School Manager and Microsoft Intune for corporate-owned devices.
ms.date: 2025-01-07T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 87b04657-c130-a84d-9636-fb1e576700c5
document_version_independent_id: 87b04657-c130-a84d-9636-fb1e576700c5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/school-manager-step-1.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/school-manager-step-1
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/school-manager-step-1.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: f8685108-41e9-f29b-4d6c-39700bbb5d38
---

# Apple School Manager - get Apple token and assign devices - Microsoft Intune | Microsoft Learn

Before you can enroll corporate-owned devices with Apple School Manager, you need a token (.p7m) file from Apple. This token lets Intune sync information about Apple School Manager-participating devices. It also permits Intune to perform enrollment policy uploads to Apple and to assign devices to those policies. While you are in the Apple portal, you can also assign device serial numbers to manage.

## Get Apple token

In the first set of steps, you download the Intune public key certificate required to create an Apple token.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Devices**.
2. Expand **Device onboarding**, and then select **Enrollment**.
3. Select the **Apple mobile** tab.
4. Choose **Enrollment program tokens**.
5. Select **Create**.
6. Select **I agree** to give permission to Microsoft to send user and device information to Apple.
7. Select **Download your public key**. This step downloads and saves the encryption key (.pem) file locally. The .pem file is used to request a trust-relationship certificate from the Apple School Manager portal.

    In the next set of steps, you download a token and assign devices. Keep the browser and tab with the admin center open while you're completing steps in Apple School Manager.

    Tip

    The following steps describe what you need to do in Apple School Manager. For the specific steps, see the [Apple School Manager User Guide](https://support.apple.com/guide/apple-school-manager/device-workflow-axm6a88f692e/1/web/1) (opens Apple Support).
8. Choose **Create a token via Apple School Manager**, and sign in to [Apple School Manager](https://school.apple.com) with your company Apple ID. You can use this Apple ID to renew your Apple School Manager token.
9. In Apple School Manager, go to your MDM Server assignments to add an MDM server.
10. Enter the mobile device management (MDM) server name. The server name is for your reference to identify the MDM server. It isn't the name or URL of the Microsoft Intune server.
11. Upload the public key certificate file (.pem file).
12. Save your MDM server.
13. Select the download button to download the server token (.p7m) file to your computer.
14. Go to **Devices** and select the devices you want to assign to this token. You can sort by various device properties, like serial number. You can also select multiple devices simultaneously.
15. Select **Edit MDM Server**. Select the MDM server you just added, and then save your changes. This step assigns devices to the token.
16. Return to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and enter the Apple ID you used to create the token.

    ![Example screenshot showing the Apple ID used to create the enrollment program token and browsing to the enrollment program token.](media/school-manager/image03.png)
17. For **Apple token**, browse to the certificate (.pem) file. Select **Open**, and then choose **Create**. With the push certificate, Intune can enroll and manage devices by pushing policies to enrolled devices. Intune automatically syncs your Apple School Manager devices from Apple.