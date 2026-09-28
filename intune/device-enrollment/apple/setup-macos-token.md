---
layout: Conceptual
title: Set up a macOS ADE token in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-macos-token
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
description: Create, renew, and delete Apple enrollment program tokens for macOS automated device enrollment in Microsoft Intune.
ms.date: 2026-04-15T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
locale: en-us
document_id: bd9eef5a-f40b-005b-1d40-7b0a1cf7f89b
document_version_independent_id: bd9eef5a-f40b-005b-1d40-7b0a1cf7f89b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/setup-macos-token.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/setup-macos-token
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/setup-macos-token.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/837687b0-8846-4eb2-adb6-2b853e8c70c4
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c797fa2-4419-46e7-a4e3-4c97d0a1f2a0
platformId: fa52dbd6-82b5-008f-2c2f-de9634294b9b
---

# Set up a macOS ADE token in Intune - Microsoft Intune | Microsoft Learn

*Applies to macOS*

An *enrollment program token* (sometimes called an automated device enrollment token) is a required component of Apple automated device enrollment (ADE) for macOS. It creates the trust relationship between Microsoft Intune and Apple Business or Apple School Manager, and allows Intune to:

- Sync device information from your Apple enrollment program account.
- Upload enrollment policies to Apple.
- Assign devices to enrollment policies.

This article describes how to create, renew, and delete enrollment program tokens for macOS.

## Create an enrollment program token

The steps in this section apply to both Apple Business and Apple School Manager. Where the user interface differs, separate instructions are provided.

### Step 1: Download the Intune public key certificate

The public key certificate is needed to request a trust-relationship certificate from Apple Business and Apple School Manager.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Enrollment**.
2. Select the **Apple** tab.
3. Under **Bulk Enrollment Methods**, select **Enrollment program tokens**.
4. Select **Create**.
5. Select **I agree** to grant permission to Microsoft to send user and device information to Apple.
6. Select **Download your public key** and save the key as a PEM file locally. The key is used to get the MDM server token in the next step.

    Important

    Keep this browser tab open. If you close the tab, the certificate you downloaded is invalidated and you'll need to start over.

### Step 2: Create the connection and download the server token

Create a connection between Microsoft Intune and Apple Business or Apple School Manager, and then download the server token. Apple Business creates a device management service, while Apple School Manager creates an MDM server. Both processes result in a server token that you upload to Intune.

1. In the admin center, select the link that corresponds with the Apple portal you use. Your options:

    - **Create a token via Apple Business**
    - **Create a token via Apple School Manager**

    The selected portal opens in a new browser tab. Keep the Intune tab open.
2. Sign in to the Apple portal with your organization's Apple ID.

    Important

    Use your organization's Apple ID, not a personal one. You will need this Apple ID to renew and manage the token in the future.
3. Go to the management settings:

    - Apple Business: Select the **Devices** tab and go to **Management Services**.
    - Apple School Manager: Go to your account profile &gt; **Preferences** &gt; **Your MDM servers**.
4. Create a new connection:

    - Apple Business: Select **Connect external device management**, and then select **Continue**.
    - Apple School Manager: Select **Add**.
5. Enter a name for the device management service or MDM server. The name is for identification purposes only and doesn't need to match your Microsoft Intune tenant name, server name, or URL.
6. Upload your public key (.pem) file. Then select **Next** in Apple Business or **Save** in Apple School Manager.
7. Download the token (.p7m file).

### Step 3: Assign devices

After you create the connection:

- In Apple Business, assign devices to the device management service.
- In Apple School Manager, assign devices to the MDM server.

We recommend assigning devices now while you're in the Apple portal. You can use available features like *filters* and *bulk assignment* to simplify selection. For more information, see [Assign, reassign, or unassign devices in Apple Business](https://support.apple.com/guide/business/axmf500c0851/web).

### Step 4: Save the Apple ID

1. Return to the Intune admin center tab.
2. In the **Apple ID** field, enter the Apple ID used to download the server token.

    This ID is the Apple ID you'll need to renew the token each year. Make sure future Intune admins know which Apple ID was used, in case you leave your organization and need to transition token management.

    ![Screenshot highlighting the Apple ID field in the Add enrollment program token pane.](media/setup-automated-ios/image03.png)

### Step 5: Upload the server token and finish

1. In the **Apple token** field, browse to the token (.p7m file) you downloaded from Apple.
2. Select **Open**, and then select **Create**.

Intune automatically connects with Apple Business or Apple School Manager to sync device information from your enrollment program account.

## Renew an enrollment program token

Renew your enrollment program token yearly. The Intune admin center shows the token expiration date. Also renew the token in these situations:

- The Apple ID password changes for the user who set up the token in Apple Business or Apple School Manager.
- The user who set up the token leaves the organization.

To renew the token, download a new token from the Apple connection associated with Intune. In Apple Business, the connection is a device management service. In Apple School Manager, the connection is an MDM server.

1. Sign in to the Apple portal with an account that has the appropriate administrator permissions.
2. Go to the management settings:

    - Apple Business: Select the **Devices** tab and go to **Management Services**.
    - Apple School Manager: Go to your account profile &gt; **Preferences** &gt; **Your MDM servers**.
3. Select the connection associated with the token you want to renew:

    - Apple Business: Select the device management service.
    - Apple School Manager: Select the MDM server.
4. Download a new token:

    - Apple Business: Open the **Actions** menu and select **Download Token**.
    - Apple School Manager: Select **Download Token**.

    Note

    Don't select **Download Token** unless you intend to renew the token. Doing so invalidates the token currently in use by Intune. If you already downloaded the token, complete the remaining steps to finish the renewal.
5. After downloading the token, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
6. Go to **Devices** &gt; **Enrollment**.
7. Select the **Apple** tab.
8. Under **Bulk Enrollment Methods**, select **Enrollment program tokens**.
9. Select the token you want to renew.
10. Select **Renew token**. Enter the **Apple ID** used to create the original token.
11. Upload the newly downloaded token.
12. Select **Next**. Assign scope tags if needed.
13. Select **Create** to save your changes.

## Delete an enrollment program token

Warning

Deleting devices from a token (required before you can delete the token) removes those devices from Intune management. If the devices are still in use, users will lose access to corporate resources and apps managed by Intune. Wipe and re-enroll devices with a new token if you want to continue managing them.

You can delete an enrollment program token from Intune as long as:

- No devices are assigned to the token.
- No devices are assigned to the default policy.
- There are no enrollment policies under that token.

To delete an enrollment program token:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Enrollment**.
2. Select the **Apple** tab.
3. Under **Bulk Enrollment Methods**, select **Enrollment program tokens**.
4. Select the token, and then select **Devices**.
5. Delete all devices assigned to the token.
6. Return to **Enrollment program tokens**. Select the token, and then select **Enrollment policies**.
7. Delete all enrollment policies listed, including any default policy.
8. Return to **Enrollment program tokens**. Select the token, and then select **Delete**.