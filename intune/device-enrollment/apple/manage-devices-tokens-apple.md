---
layout: Conceptual
title: Manage Apple mobile devices and tokens in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/manage-devices-tokens-apple
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
description: Sync devices, distribute devices, and re-enroll devices for Apple automated device enrollment on iOS/iPadOS in Microsoft Intune.
ms.date: 2026-04-29T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
locale: en-us
document_id: 9eae5ec5-825d-f93b-733a-a5668ba7a005
document_version_independent_id: 9eae5ec5-825d-f93b-733a-a5668ba7a005
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/manage-devices-tokens-apple.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/manage-devices-tokens-apple
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/manage-devices-tokens-apple.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 08154bce-5ae0-298f-8d12-136cf5e058a4
---

# Manage Apple mobile devices and tokens in Intune - Microsoft Intune | Microsoft Learn

Use this article to sync Apple mobile devices with Apple Business, manage your enrollment tokens, and distribute devices to users.

Note

The steps in this article are similar whether you're using Apple Business or Apple School Manager. For brevity, this article refers to *Apple Business* only, except where clarification is necessary.

This article applies to:

- iOS/iPadOS
- tvOS
- visionOS

## Sync managed devices

Syncing refreshes existing device status and imports new devices assigned to the Apple MDM server. After creating a token, sync Intune with Apple to see your managed devices in the Microsoft Intune admin center.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Enrollment**.
2. Select the **Apple** tab.
3. Under **Bulk Enrollment Methods**, select **Enrollment program tokens**.
4. Select a token from the list.
5. Select **Devices** &gt; **Sync**.

## Sync restrictions

To comply with Apple's terms for acceptable enrollment program traffic, Microsoft Intune imposes the following restrictions:

- A *full sync* can run no more than once every seven days. During a full sync, Intune fetches the complete, updated list of serial numbers assigned to the connected Apple MDM server.

    Important

    If you delete a device from Intune but it remains assigned to the ADE token in Apple Business, the device reappears in Intune on the next full sync. If you don't want the device to reappear, unassign it from the Apple MDM server in Apple Business first.
- If a device is released from Apple Business, it can take up to 45 days for it to be automatically deleted from the **Devices** page in Intune. You can manually delete released devices one by one if needed. Released devices are reported as *removed* from Apple Business in Intune until they're automatically deleted within 30–45 days.
- A delta sync runs automatically every 12 hours. You can also trigger a sync manually by selecting **Sync**, no more than once every 15 minutes. All sync requests have 15 minutes to finish. The **Sync** button becomes inactive until the sync completes.
- Apple Business and Apple School Manager sync approximately 3,000 devices to Intune per minute. If you have more than 200,000 devices per token, we recommend waiting for all devices to finish syncing before manually triggering another sync (total devices ÷ 3,000 devices per minute = estimated wait time).

## Re-enroll a device

Complete these steps to re-enroll a device that already went through automated device enrollment.

1. There are two options for resetting the device:
    - Wipe the device in the Microsoft Intune admin center.
    - Retire the device in the admin center, and then reset the device to factory settings using the Settings app or Apple Configurator 2.
2. Turn on the device and follow the onscreen steps in Setup Assistant to retrieve the remote management profile.

## Renew your token

1. Go to [Apple Business](http://business.apple.com) and sign in with an account that has an Administrator or Device Enrollment Manager role.
2. Select the **Devices** tab in Apple Business, or go to your account profile &gt; **Preferences** in Apple School Manager.
3. Go to **Management Services** in Apple Business, or go to **Your MDM servers** in Apple School Manager.
4. Select the device management servivce in Apple Business, or MDM server in Apple School Manager associated with the token file you want to renew.
5. Select **Download Token** (this is found under the ... Actions menu in the top right in Apple Business).

    Note

    Don't select **Download Token** unless you intend to renew the token. Doing so invalidates the token currently in use by Intune. If you already downloaded the token, complete the remaining steps to finish the renewal.
6. After downloading the token, go to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
7. Go to **Devices** &gt; **Enrollment**.
8. Select the **Apple** tab.
9. Under **Bulk Enrollment Methods**, select **Enrollment program tokens**.
10. Select the token you want to renew.
11. Select **Renew token**. Enter the **Apple ID** used to create the original token.

    [![Screenshot showing the Renew token page.](media/setup-automated-ios/renewtoken.png)](media/setup-automated-ios/renewtoken.png#lightbox)
12. Upload the newly downloaded token.
13. Select **Next**. Assign scope tags if needed.
14. Select **Renew token** and wait for confirmation that the renewal is complete.

    ![Screenshot showing the token renewal confirmation message.](media/setup-automated-ios/confirmation.png)

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

## Limits

If you exceed 200,000 devices per token, you might experience sync problems. Split devices across multiple ADE tokens instead.

| Resource | Maximum |
| --- | --- |
| Enrollment policies per token | 1,000 |
| ADE devices per policy | 200,000 |
| ADE tokens per Intune account | 2,000 |
| ADE devices per token | 200,000 |

## Distribute devices

Users on devices enrolled with user affinity must have an Intune license assigned. Devices enrolled without user affinity need an Intune device license, unless an Intune-licensed user is associated with the device. For more information, see [Microsoft Intune licensing](../../fundamentals/licensing) and the [Intune planning guide](../../intune-service/fundamentals/intune-planning-guide).

A device that is already activated needs to be wiped before it can enroll with automated device enrollment. After you wipe it but before activating it again, you can apply the enrollment policy. For more information, see [Set up an existing iPhone, iPad, or iPod touch](https://support.apple.com/en-us/HT207516) (opens Apple support site).

If you're enrolling with ADE and user affinity, the following error can happen during setup:

`The SCEP server returned an invalid response.`

You can resolve this error by trying to download the management profile again within 15 minutes. After 15 minutes, you have to factory reset the device to resolve the error. This error occurs because of a 15-minute time limit on SCEP certificates, enforced for security.

## End user experience

For information about the end user experience, see:

- [ADE end user tasks](guide-ios-ipados#ade-end-user-tasks)
- [Enroll your iOS/iPadOS device](../../user-help/enrollment/enroll-automated-ios)