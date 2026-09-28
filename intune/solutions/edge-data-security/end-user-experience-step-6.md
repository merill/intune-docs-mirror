---
layout: Conceptual
title: Step 6. Understand Microsoft Edge for Business End User Experience for Windows - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/edge-data-security/end-user-experience-step-6
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- FocusArea_Apps_AppManagement
ms.reviewer: samarti
ms.subservice: apps
description: Step 6. Understand Microsoft Edge for Business end user experience Windows.
ms.date: 2026-01-23T00:00:00.0000000Z
ms.topic: how-to
ms.custom: 
locale: en-us
document_id: 566711ed-9217-936c-609d-0269cf675518
document_version_independent_id: 566711ed-9217-936c-609d-0269cf675518
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/edge-data-security/end-user-experience-step-6.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/edge-data-security/end-user-experience-step-6
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/edge-data-security/end-user-experience-step-6.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: b9ca603d-f23a-1f39-94b8-ca507d7f62b4
---

# Step 6. Understand Microsoft Edge for Business End User Experience for Windows - Microsoft Intune | Microsoft Learn

Now that you configured your Microsoft Entra Conditional Access policy, app protection policies, app configuration policies, and settings catalog, you can launch **Microsoft Edge for Business** using a managed or unmanaged device.

The end user experience in Microsoft Edge for Business is designed to be productive, secure, and user-friendly. This secure enterprise browser experience includes the following features:

1. **Visually distinct work browsing experience**: Microsoft Edge for Business provides a visually distinct work browsing experience with refreshed visual treatment. This experience helps users easily distinguish between their work and personal browsing sessions.
2. **Enterprise personal browsing experience**: Microsoft Edge for Business offers a lightly managed personal browsing experience that lets users access their favorite nonwork sites and services without compromising safety for the enterprise.
3. **Context separation**: Work and personal browsing data are kept separate to reduce the risk of sharing sensitive information with unintended audiences.
4. **Security**: It has built-in defenses against phishing and malware and natively supports hardware isolation on Windows.

Microsoft Edge for Business provides dedicated work and personal browsing experiences with separate favorites, cache, and storage locations.

## Onboarding experience

To evaluate the onboarding experience, launch **Microsoft Edge** from the desktop and perform the sign-in process in your browser. The device can't be managed by any MDM solution, otherwise it can't enroll into the MAM service.

1. Locate **Microsoft Edge** on the desktop.
2. Select the **Microsoft Edge** icon and wait for it to load. Once loaded, you see a user icon at the top-left of the browser window.
3. Select the user icon to display your managed account details.
4. Select **Sign in to sync data**.

    [![Sign in to sync data in Microsoft Edge.](media/securing-data-edge-for-business/securing-data-edge-for-business19.png)](media/securing-data-edge-for-business/securing-data-edge-for-business19.png#lightbox)
5. Enter your **email address** for the tenant.

    [![Let us get you signed in to Microsoft Edge.](media/securing-data-edge-for-business/securing-data-edge-for-business20.png)](media/securing-data-edge-for-business/securing-data-edge-for-business20.png#lightbox)
6. Enter your **password** for the account.

    Note

    The sign-in experience varies by organization. Completing the sign-in process is required to add your work profile to Microsoft Edge.

    Note

    A user experience update and admin property for controlling automatic MDM enrollment is rolling out in late 2025. This setting determines whether users on Entra ID-registered devices are prompted to MDM-enroll during the [Add Your Work or School Account to a Windows Device](https://support.microsoft.com/windows/add-your-work-or-school-account-to-a-windows-device-a6505ceb-1a20-4b15-889c-250175481506) flow. To control this behavior, configure the **Disable MDM enrollment when adding a work or school account** setting. For more information, see [Enable MDM automatic enrollment for Windows](../../device-enrollment/windows/enable-automatic-mdm).
7. Select **Yes** to sign in and register the device. Don't select **No, sign in to the app only**, as it prevents enrollment and MAM from being applied to the browser.

[![Prompt asking whether to sign in to all apps, websites, and services on the device, with options for Yes or No, this app only.](media/securing-data-edge-for-business/securing-data-edge-for-business22.png)](media/securing-data-edge-for-business/securing-data-edge-for-business22.png#lightbox)

1. If your organization doesn't opt to use the new property in public preview to manage the MDM option display, select **No**. Selecting Yes enrolls your device into Intune and won't enable MAM.

[![Prompt asking whether to allow your organization to manage the device, with options for Yes or No.](media/securing-data-edge-for-business/securing-data-edge-for-business23a.png)](media/securing-data-edge-for-business/securing-data-edge-for-business23a.png#lightbox)

1. Confirm that you're signed in by selecting the user icon again.

Note

After enrollment is complete, the browser begins protecting your corporate data.

## App protection notifications

Intune displays notifications when a policy requirement isn't met. The following messages can appear:

- **App access blocked message:** Appears when the app protection policy fails the device threat level check.

    [![App Access Blocked in Microsoft Edge for Business.](media/securing-data-edge-for-business/securing-data-edge-for-business25.png)](media/securing-data-edge-for-business/securing-data-edge-for-business25.png#lightbox)
- **Your organization prevents you from copying content from this website:** Appears when your DLP policy blocks a data movement action.

    [![Copying prevention by app protection policy in Microsoft Edge for Business.](media/securing-data-edge-for-business/securing-data-edge-for-business26.png)](media/securing-data-edge-for-business/securing-data-edge-for-business26.png#lightbox)
- **Your organization prevents you from printing this website:** Appears when the applied Level 3 policy blocks printing.

    [![Printing prevention by app protection policy in Microsoft Edge for Business.](media/securing-data-edge-for-business/securing-data-edge-for-business27.png)](media/securing-data-edge-for-business/securing-data-edge-for-business27.png#lightbox)
- **Your organization prevents you from downloading this file:** Appears when the applied Level 3 policy blocks downloads.

    [![Download prevention by app protection policy in Microsoft Edge for Business.](media/securing-data-edge-for-business/securing-data-edge-for-business28.png)](media/securing-data-edge-for-business/securing-data-edge-for-business28.png#lightbox)
- **Offline Grace Period Expired:** Appears when Intune determines the user is offline longer than the allowed period.

    [![Offline Grace Period Expired in Microsoft Edge for Business.](media/securing-data-edge-for-business/securing-data-edge-for-business29.png)](media/securing-data-edge-for-business/securing-data-edge-for-business29.png#lightbox)