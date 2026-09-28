---
layout: Conceptual
title: Manage macOS ADE devices and tokens in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/manage-devices-tokens-macos
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
description: Sync devices, assign enrollment policies, and distribute Mac computers for Apple automated device enrollment in Microsoft Intune.
ms.date: 2026-04-15T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
locale: en-us
document_id: d395897f-dc2e-ce34-a698-3ed2e7758e6b
document_version_independent_id: d395897f-dc2e-ce34-a698-3ed2e7758e6b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/manage-devices-tokens-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/manage-devices-tokens-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/manage-devices-tokens-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/837687b0-8846-4eb2-adb6-2b853e8c70c4
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/8c797fa2-4419-46e7-a4e3-4c97d0a1f2a0
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 03103148-6915-d349-786f-321a354ac61c
---

# Manage macOS ADE devices and tokens in Intune - Microsoft Intune | Microsoft Learn

*Applies to macOS*

Use this article to sync macOS devices with Apple Business, manage your enrollment tokens, and distribute devices to users.

Note

The steps in this article are the same whether you're using Apple Business or Apple School Manager. For brevity, this article refers to *Apple Business* only, except where clarification is necessary.

## Prerequisites

Before completing the tasks in this article:

- [Set up a macOS ADE token](setup-macos-token)
- [Create an enrollment policy for macOS and assign it to devices](setup-automated-macos)

## Sync managed devices

Syncing refreshes existing device status and imports new devices assigned to the Apple MDM server. After creating a token, sync Intune with Apple to see your managed devices in the admin center.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** &gt; **Enrollment**.
2. Select the **Apple** tab.
3. Under **Bulk Enrollment Methods**, select **Enrollment program tokens**.
4. Select a token from the list.
5. Select **Devices** &gt; **Sync**.

    ![Screenshot of Enrollment program token area in the admin center, highlighting the example token, &quot;Devices&quot; link, and &quot;Sync&quot; button.](media/setup-automated-macos/image06.png)

## Sync restrictions

To comply with Apple's terms for acceptable enrollment program traffic, Microsoft Intune imposes the following restrictions:

- A *full sync* can run no more than once every seven days. During a full sync, Intune fetches the most recent, updated list of serial numbers assigned to the connected Apple MDM server. If you delete a device from Intune without unassigning it from the MDM server in Apple Business or Apple School Manager, it won't be reimported to Intune until the full sync runs.

    Important

    If you delete a device from Intune but it remains assigned to the ADE token in Apple Business, the device reappears in Intune on the next full sync. If you don't want the device to reappear, unassign it from the Apple MDM server in Apple Business first.
- If a device is released from Apple Business, it can take up to 45 days for it to be automatically deleted from the **Devices** page in Intune. You can manually delete released devices one by one if needed. Released devices are reported as *removed* from Apple Business in Intune until they're automatically deleted within 30–45 days.
- A sync runs automatically every 24 hours. You can also trigger a sync manually by selecting **Sync**, no more than once every 15 minutes. All sync requests have 15 minutes to finish. The **Sync** button becomes inactive until the sync completes.

## Distribute devices

Important

Users associated with devices that have user affinity must be assigned an Intune license. Devices without user affinity require a device license.

Distribute prepared Mac devices throughout your organization.

- **New or wiped Macs**: New or wiped Macs configured in Apple Business or Apple School Manager automatically enroll in Microsoft Intune during Setup Assistant when someone turns on the device. If you assigned the device to a macOS enrollment policy with user affinity, the device user must sign in to the Company Portal after Setup Assistant is done to finish Microsoft Entra registration and Conditional Access requirements.
- **Existing Macs**: You can enroll devices that already went through Setup Assistant. Complete these steps to enroll corporate-owned Macs running macOS 10.13 and later.

    1. Ensure that:

        - The device is imported to Apple Business or Apple School Manager.
        - The device is assigned a macOS enrollment policy in the admin center.
    2. Sign in to the device with a local administrator account.
    3. To trigger enrollment, from the **Home** page open **Terminal**, and run the following command:

        `sudo profiles renew -type enrollment`
    4. Enter the device password for the local administrator account.
    5. On **Device enrollment**, select **Details**.
    6. On **System preferences**, select **Profiles**.
    7. Follow the onscreen prompts to download the Microsoft Intune management profile, certificates, and policies.

        Tip

        You can confirm which profiles are on the device anytime by returning to **System Preferences** &gt; **Profiles**.
    8. If you assigned the device to a macOS enrollment policy with user affinity, sign in to the Company Portal app to complete Microsoft Entra registration and Conditional Access requirements, and finish enrollment.