---
layout: Conceptual
title: Data Transfer Policy Exceptions for Apps - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/protection/create-data-transfer-exceptions
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.subservice: apps
description: Create exceptions to the Intune App Protection Policy (APP) data transfer policy.
ms.date: 2025-12-02T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: beflamm
locale: en-us
document_id: 44a6314f-c71d-db73-fa43-261eba04fc68
document_version_independent_id: 44a6314f-c71d-db73-fa43-261eba04fc68
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/protection/create-data-transfer-exceptions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/protection/create-data-transfer-exceptions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/protection/create-data-transfer-exceptions.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: a34f5020-06c2-1c7f-4b56-a966029b46ef
---

# Data Transfer Policy Exceptions for Apps - Microsoft Intune | Microsoft Learn

As an administrator, you can create exceptions to the Intune App Protection Policy (APP) data transfer policy. An exception allows you to specifically choose which unmanaged apps can transfer data to and from managed apps. Your IT must trust the unmanaged apps that you include in the exception list.

Warning

You're responsible for making changes to the data transfer exception policy. Additions to this policy allow unmanaged apps (apps that aren't managed by Intune) to access data protected by managed apps. This access to protected data may result in data security leaks. Only add data transfer exceptions for apps that your organization must use, but that don't support Intune APP (Application Protection Policies). Additionally, only add exceptions for apps that you don't consider to be data leak risks.

Within an Intune Application Protection Policy, setting **Allow app to transfer data to other apps** to **Policy managed apps** means that the app can transfer data only to apps managed by Intune. If you need to allow data to be transferred to specific apps that don't support Intune APP, you can create exceptions to this policy by using **Select apps to exempt**. Exemptions allow applications managed by Intune to invoke unmanaged applications based on URL protocol (iOS/iPadOS) or package name (Android). By default, Intune adds vital native applications to this list of exceptions.

Note

Modifying or adding to the data transfer policy exceptions doesn't impact other App Protection Policies, such as cut, copy, and paste restrictions.

## iOS data transfer exceptions

For a policy targeting iOS/iPadOS, you can configure data transfer exceptions by URL protocol. To add an exception, check the documentation provided by the developer of the app to find information about supported URL protocols. For more information about iOS/iPadOS data transfer exceptions, see [iOS/iPadOS app protection policy settings - Data transfer exemptions](ref-settings-ios#data-transfer-exemptions).

Note

Microsoft doesn't have a method to manually find the URL protocol for creating app exceptions for third-party applications.

## Android data transfer exceptions

For a policy targeting Android, you can configure data transfer exceptions by app package name. You can check the **Google Play** store page for the app you would like to add an exception for to find the app package name. For more information about Android data transfer exceptions, see [Android app protection policy settings - Data transfer exemptions](ref-settings-android#data-transfer-exemptions).

Tip

You can find the package ID of an app by browsing to the app on the Google Play store. The package ID is contained in the URL of the app's page. For example, the package ID of the Microsoft Word app is **com.microsoft.office.word**.

### Example

By adding the **Webex** package as an exception to the MAM data transfer policy, Webex links inside a managed Outlook email message are allowed to open directly in the Webex application. Data transfer is still restricted in other unmanaged apps.

- iOS/iPadOS **Webex** example: To exempt the **Webex** app so that it's allowed to be invoked by Intune managed apps, you must add a data transfer exception for the following string: `wbx`. To exempt the **Webex Meetings** app so that it's allowed to be invoked by Intune managed apps, you must add a data transfer exception for the following string: `webexteams`
- iOS/iPadOS **Maps** example: To exempt the native **Maps** app so that it's allowed to be invoked by Intune managed apps, you must add a data transfer exception for the following string: `maps`
- Android **Webex** example: To exempt the **Webex** app so that it's allowed to be invoked by Intune managed apps, you must add a data transfer exception for the following string: `com.cisco.webex.meetings`
- Android **SMS** example: To exempt the native **SMS** app so that it's allowed to be invoked by Intune managed apps across different messaging apps and Android devices, you must add data transfer exceptions for the following strings:

    - `com.google.android.apps.messaging`
    - `com.android.mms`
    - `com.samsung.android.messaging`