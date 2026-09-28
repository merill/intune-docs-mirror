---
layout: Conceptual
title: Common tasks and features in the settings catalog - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/settings-catalog/common-tasks
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Use the settings catalog in Microsoft Intune to configure common features. You can create a Universal Print policy, configure Microsoft Edge and Google Chrome web browsers, and use built in settings instead of plist files for macOS devices.
ms.date: 2026-03-24T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: laarrizz, mayurjadhav, beflamm
locale: en-us
document_id: 4f9678a1-2c1c-9d84-8ab6-3200fb131d3e
document_version_independent_id: 4f9678a1-2c1c-9d84-8ab6-3200fb131d3e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/settings-catalog/common-tasks.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/settings-catalog/common-tasks
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/settings-catalog/common-tasks.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
platformId: 14d267f0-ecca-5df8-aea6-55fa5268929c
---

# Common tasks and features in the settings catalog - Microsoft Intune | Microsoft Learn

Using the [settings catalog](./) in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), you can access many settings that manage apps and features on your devices.

This article lists and describes some of the features you can configure in the settings catalog.

For more information on the settings catalog, and what it is, go to [Use the settings catalog to configure settings on Windows and macOS devices](./). To see all the settings you can configure, [create a settings catalog policy](./).

This feature applies to:

- iOS/iPadOS
- macOS
- Windows

## Configure Microsoft Edge and Google Chrome

This feature applies to:

- macOS
- Windows

These web browser settings are built in, and can be configured & deployed to your managed devices. On Windows devices, you can also configure Google Chrome.

![Screenshot that shows the Google Chrome settings in the settings catalog that are built in to Microsoft Intune and Intune admin center. Use these settings to create and configure a Google Chrome policy on Windows devices.](media/common-tasks/google-chrome-settings.png)

Previously, to configure Google Chrome settings on Windows devices, you created a custom OMA-URI device configuration policy.

For a sample Microsoft Edge scenario, see [Create a Microsoft Edge policy](configure-edge).

## Manage AI features on Android devices

This feature applies to:

- Android Enterprise

There are features and built-in settings to help you manage AI features on Android Enterprise devices. You can block AI websites in web browser apps, block Screen-driven AI experiences, and disable the on-device AI system app.

For more information, go to [Manage AI features on Android devices](../../solutions/ai/manage-ai-android).

## Enable Recovery Lock on macOS devices

This feature applies to:

- macOS

You can configure Recovery Lock on your macOS devices. When you enable Recovery Lock, users are prompted for a password when they try to access the recovery partition environment on the device. This feature helps prevent unauthorized users from reinstalling or wiping the device.

For more information, go to [Protect macOS devices using Recovery Lock with Microsoft Intune](configure-recovery-lock-macos).

## Add Universal Print printers

This feature applies to:

- Windows

You can create a Universal Print policy, add printers, and then deploy this printer list to your managed users. When the policy is deployed, it automatically installs the printers you added. Users can see these printers, and select a printer from your list.

For more information, go to [Create a Universal Print policy in Microsoft Intune](configure-universal-print).

## Use Apple's DDM to manage software updates

This feature applies to:

- iOS/iPadOS
- macOS

You can use the settings catalog to configure Apple's declarative device management (DDM) to manage software updates. With DDM, the device handles the entire software update lifecycle. It prompts users that an update is available and also downloads, prepares the device for the installation, & installs the update.

For more information, go to [Managed software updates with the settings catalog](../../device-updates/apple/).

## Built-in macOS features replacing plist files

This feature applies to:

- macOS

On macOS, you can use property list (plist) files to configure features and settings that aren't built in to Intune. Some of these feature settings are now available in the settings catalog:

- **Microsoft Edge version 77 and newer**: For a list of the settings you can configure, go to [Microsoft Edge - Policies](/en-us/DeployEdge/microsoft-edge-policies) (opens another Microsoft website).

    Previously, you had to [use a property list (plist) file to configure Microsoft Edge](/en-us/deployedge/configure-microsoft-edge-on-mac) (opens another Microsoft website).
- **Microsoft Defender for Endpoint**: For a list of the settings you can configure, go to [Set preferences for Microsoft Defender for Endpoint on macOS](/en-us/microsoft-365/security/defender-endpoint/mac-preferences) (opens another Microsoft website).

    Previously, you had to [use a property list (plist) file to configure Microsoft Defender for Endpoint](/en-us/microsoft-365/security/defender-endpoint/mac-install-with-intune) (opens another Microsoft website).
- **Microsoft AutoUpdate (MAU), Microsoft Office and Microsoft Outlook**: For a list of the settings you can configure, go to:

    - [Use preferences to manage privacy controls for Office for Mac - Deploy Office](/en-us/deployoffice/privacy/mac-privacy-preferences)
    - [Set preferences for Outlook for Mac - Deploy Office](/en-us/deployoffice/mac/preferences-outlook)
    - [Set a deadline for updates from Microsoft AutoUpdate](/en-us/deployoffice/mac/mau-deadline)

        For a list of apps that support MAU, go to [Update Microsoft applications for Mac by using msupdate](/en-us/deployoffice/mac/update-office-for-mac-using-msupdate).

    Previously, you had to [use a property list (plist) file to configure these features for Mac](/en-us/deployoffice/mac/deploy-preferences-for-office-for-mac) (opens another Microsoft website).

Be sure macOS is listed as a supported platform. If some settings aren't available in the settings catalog, then we recommend you continue using the [preference file](../templates/configure-preference-file-macos).