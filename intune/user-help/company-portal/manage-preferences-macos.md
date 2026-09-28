---
layout: Conceptual
title: Manage Intune Company Portal preferences for macOS - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/company-portal/manage-preferences-macos
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Choose your preferences for single sign-on and in-app data collection in Company Portal for macOS.
ms.date: 2024-10-08T00:00:00.0000000Z
ms.reviewer: esmich
locale: en-us
document_id: a49566cd-4503-e1a3-1c82-597eee39f942
document_version_independent_id: a49566cd-4503-e1a3-1c82-597eee39f942
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/company-portal/manage-preferences-macos.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/company-portal/manage-preferences-macos
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/company-portal/manage-preferences-macos.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 18d2886f-d621-02a1-ee72-6758517aed08
---

# Manage Intune Company Portal preferences for macOS - Microsoft Intune | Microsoft Learn

Select your preferences for single sign-on and in-app data collection in Company Portal. To access your preferences:

1. Open the Company Portal app.
2. Go to the menu bar and select **Company Portal** &gt; **Preferences**.

## Single sign-on

Single sign-on (SSO) configures your work or school account so that you only have to authenticate once to access all cloud-based work apps and services. Preferences include:

- **Register device**: Register your device to enable SSO and gain access to protected resources. This setting is only available on devices enabled for platform SSO.
- **Deregister**: Remove device registration and disable SSO. To access protected resources again on this device, you must reregister. This setting is only available on devices enabled for platform SSO.
- **Remove account from this device**: Remove your work or school account and any SSO authentication tokens from the device.

To opt out of SSO on your Mac, select the checkbox next to **Don't ask me to sign in with single sign-on for this device**.

## Send usage data to Microsoft

This setting enables Microsoft to collect data about your Intune Company Portal usage. When the checkbox is selected, your in-app performance and usage data are automatically anonymized and shared with Microsoft to help improve the reliability and performance of our products. Your organization doesn't have control over the collection of this data and cannot change your preference.

To turn off data collection in Company Portal, deselect the checkbox next to **Allow Microsoft to collect usage data**.

## Advanced logging

Select the checkbox next to **Turn on advanced logging** to turn on verbose logging, which is used for troubleshooting, for Company Portal and MSAL. Company Portal logs certificate usage and network responses when advanced logging is turned on. Advanced logging is turned off by default. Keep this setting turned off unless otherwise instructed by your organization's IT administrator.