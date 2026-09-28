---
layout: Conceptual
title: Check compliance on your Android device - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/compliance/validate-compliance-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: During a check-in, Company Portal confirms that the settings on your device meet your organization's policy requirements.
ms.date: 2025-01-27T00:00:00.0000000Z
ms.reviewer: abigailstein
locale: en-us
document_id: 5718fc97-5298-171a-5008-e48db81af2bc
document_version_independent_id: 5718fc97-5298-171a-5008-e48db81af2bc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/compliance/validate-compliance-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/compliance/validate-compliance-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/compliance/validate-compliance-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: c991d8bc-8e49-187e-1df5-a1a29c0f628c
---

# Check compliance on your Android device - Microsoft Intune | Microsoft Learn

*Applies to Intune Company Portal app for Android*

Use the Intune Company Portal app to remotely check the status of an enrolled work device, and confirm or resolve access issues caused by noncompliant settings.

During a status check, Company Portal checks your device to make sure it meets your organization's requirements. Company Portal provides next-step information along with the status if your device doesn't meet requirements. Your organization might limit or restrict the device from accessing work resources until you adjust the settings.

Tip

After you change the settings on a noncompliant device, we recommend running another status check to register the changes with the Company Portal app.

1. Sign in to the Company Portal app for Android with your work account.
2. Tap **DEVICES** and then select your device.
3. Tap **Check device settings**. Wait on the Device Details page while Company Portal confirms your device settings.
4. If you're required to make any changes, the message **You need to update settings on this device** appears at the top of the screen. Tap the message for more details. After you make changes to your settings, repeat step 3 in this procedure.

## Device settings status

The device settings status in Company Portal tells you the following information about your enrolled device:

- **Confirming devices settings**: Company Portal is currently checking your device settings. Return to **Device Settings Status** in a few minutes for an updated status.
- **In Compliance**: Your device is allowed to access work or school resources.
- **Can access resources, but action required**: Your device is allowed to access work or school resources, but one or more settings don't meet your organization's requirements. Update your device settings by the date shown to keep your access.
- **Not in Compliance**: Your device isn't allowed to access work or school resources. Make the required changes to gain access.

For more help and support, contact your IT support person. Go to the **Support** tab in the Company Portal app for contact information, or access support details and device actions on the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980).