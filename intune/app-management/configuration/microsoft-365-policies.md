---
layout: Conceptual
title: Policies for Microsoft 365 Apps - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/configuration/microsoft-365-policies
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
description: Understand the policies available for Microsoft 365 apps.
ms.date: 2024-05-16T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: bryanke
ms.custom: 
locale: en-us
document_id: caac2651-8df3-6109-6015-e086a02363cd
document_version_independent_id: caac2651-8df3-6109-6015-e086a02363cd
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/configuration/microsoft-365-policies.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/configuration/microsoft-365-policies
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/configuration/microsoft-365-policies.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e2c9f30c-00ec-44c0-846c-b20dbfb3283f
- https://authoring-docs-microsoft.poolparty.biz/devrel/1dd701e0-441f-4b0a-9806-aa47decc4e35
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/702271fe-87d7-4493-828b-2d6fde3de8ab
- https://authoring-docs-microsoft.poolparty.biz/devrel/0a2fc935-5977-4aa6-9f55-0be03bd2acb8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: e0ad1fd1-2fb4-2c1b-bb47-d374119c903e
---

# Policies for Microsoft 365 Apps - Microsoft Intune | Microsoft Learn

Intune provides policies specifically for Microsoft 365 (Office) apps. You can select specific options to create mobile app management policies for Office mobile apps that connect to Microsoft 365 services. There are many policies for Microsoft 365 apps that you can add to Microsoft Intune and apply to groups of end users.

Examples of just a few of the Office app policies include the following:

- Microsoft Word: *Turn off Protected View for attachments opened from Outlook*
- Microsoft Visio: *Block macros from running in Office files from the Internet*
- Microsoft Project: *Allow Trusted Locations on the network*
- Microsoft Publisher: *Publisher Automation Security Level*
- Microsoft PowerPoint: *Turn off Protected View for attachments opened from Outlook*

Note

When you select to configure each specific app policy, additional policy details are provided. You can filter the Office policy list to quickly select the recommended **security baseline** policies.

You can also protect access to Exchange on-premises mailboxes by creating Intune app protection policies for Outlook for iOS/iPadOS and Android enabled with hybrid Modern Authentication. Before using this feature, you must meet the requirements for using the Office cloud policy service. App protection policies are not supported for other apps that connect to on-premises Exchange or SharePoint services. For related information, see [Overview of the Office cloud policy service for Microsoft 365 Apps for enterprise](/en-us/deployoffice/overview-office-cloud-policy-service).

## Prerequisites

You must meet the requirements to use policies for Microsoft 365 apps. For more information, see [Requirements for using the Office cloud policy service](/en-us/deployoffice/overview-office-cloud-policy-service#requirements-for-using-the-office-cloud-policy-service).

## To add an Office app policy

After you set up Intune for your organization, you can create an Office app policy.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** &gt; **Policies for Microsoft 365** &gt; **Create**.
3. Add the following values:

    - **Name:** Type a name (required) for your new policy.
    - **Description:** (Optional) Type a description.
    - **Select the scope:** Select how this policy configuration will be applied.
    - **Select the groups:** If applicable, select the group for this policy configuration.
    - **Configure settings:** Select the Office policy that you want to apply. You can sort the provided list based on policy, platform, application, recommendation, and status.
4. Select **Create** after reviewing the configuration. The policy is created and appears in the table on the **Policy configurations** pane.

    Tip

    The **Policy configurations** pane provides the **Priority** for each policy.

## Quiet time notification policies

The global quiet time settings allow you to create policies to schedule quiet time for your end users. These settings automatically mute Microsoft Outlook email and Teams notifications on iOS/iPadOS and Android platforms. These policies can be used to limit end user work-related notifications received after work hours. You can find these settings in [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) by selecting **Apps** &gt; **Quiet Time** &gt; **Policies**.

## Additional information

- [Overview of the Office cloud policy service for Microsoft 365 Apps for enterprise](/en-us/deployoffice/overview-office-cloud-policy-service)
- [Use policy settings to manage privacy controls for Microsoft 365 Apps for enterprise](/en-us/deployoffice/privacy/manage-privacy-controls)
- [Use preferences to manage privacy controls for Office for Mac](/en-us/deployoffice/privacy/mac-privacy-preferences)
- [Use preferences to manage privacy controls for Office on iOS devices](/en-us/deployoffice/privacy/ios-privacy-preferences)
- [Use policy settings to manage privacy controls for Office on Android devices](/en-us/deployoffice/privacy/android-privacy-controls)