---
layout: Conceptual
title: Upgrade to Windows Holographic for Business in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-holographic-upgrade-settings
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
description: Upgrade HoloLens (first gen) to Windows 10 Holographic for Business using a device configuration profile in Microsoft Intune.
ms.date: 2025-10-14T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: ed596c15-8fe3-17e1-d8f7-e1a979cf553b
document_version_independent_id: ed596c15-8fe3-17e1-d8f7-e1a979cf553b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-holographic-upgrade-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-holographic-upgrade-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-holographic-upgrade-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/05616262-6974-4662-ac87-15adf94b9c3a
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/25c95491-bd10-484c-89ce-1fa29173d007
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 2a42e940-ddf4-4965-e912-00c115c4a573
---

# Upgrade to Windows Holographic for Business in Microsoft Intune - Microsoft Intune | Microsoft Learn

Microsoft Intune includes many settings to help manage and protect your devices. This article lists and describes the settings to upgrade HoloLens (1st gen) devices running Windows Holographic to Windows Holographic for Business.

This article applies to:

- Microsoft HoloLens (1st gen) devices

Important

HoloLens (1st gen) devices can run Windows Holographic and Windows Holographic for Business. All HoloLens 2 devices use Windows Holographic for Business. You don't need to update the edition of any HoloLens 2 device, regardless of the device SKU.

As part of your mobile device management (MDM) solution, use these settings to upgrade your HoloLens (1st gen) Windows Holographic devices. For the Microsoft HoloLens (1st gen), you can purchase the Commercial Suite to get the required license for the upgrade. For more information, see [Unlock Windows Holographic for Business features](/en-us/hololens/hololens1-upgrade-enterprise).

As an Intune administrator, you can create and assign these settings to your devices.

For more information on this feature, see [Upgrade Windows editions or enable S mode](configure-edition-upgrade-windows).

## Before you begin

- On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.
- [Create a Windows client edition upgrade and mode switch device configuration profile](configure-edition-upgrade-windows#create-the-profile).
- When you create a Windows client edition upgrade and mode switch device configuration profile, there are more settings than what's listed in this article. The settings in this article are supported on Windows Holographic for Business devices.

## Edition upgrade

- **Edition to upgrade to**: Select **Windows 10 Holographic for Business**.
- **License File**: Browse to and select the XML license file that was provided to you.

    ![In Intune, enter the XML file name that includes the Holographic for Business license information.](media/ref-holographic-upgrade-settings/holographic-edition-upgrade.png)