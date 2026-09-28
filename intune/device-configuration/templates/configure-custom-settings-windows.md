---
layout: Conceptual
title: Add custom settings for Windows devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-custom-settings-windows
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
description: Add or create a custom profile to use the OMA-URI settings for devices running Windows 10/11 client in Microsoft Intune. Use a custom profile to add custom settings.
ms.date: 2024-06-25T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mikedano
locale: en-us
document_id: b74820e8-3063-8ef3-64d9-baca2a374fb6
document_version_independent_id: b74820e8-3063-8ef3-64d9-baca2a374fb6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-custom-settings-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-custom-settings-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-custom-settings-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 097a35c0-8947-69fc-d41d-e83c7f1b6e9b
---

# Add custom settings for Windows devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Note

Intune might support more settings than the settings listed in this article. Not all settings are documented, and won't be documented. To see the settings you can configure, create a device configuration policy, and select **Settings catalog**. For more information, go to [settings catalog](../settings-catalog/).

This article describes some of the different custom settings you can control on Windows client devices. As part of your mobile device management (MDM) solution, use these settings to configure settings that aren't built in to Intune.

For more information on custom profiles, go to [Create a profile with custom settings](configure-custom-settings).

These settings are added to a device configuration profile in Intune, and then assigned or deployed to your Windows client devices.

This feature applies to:

- Windows

Windows client custom profiles use Open Mobile Alliance Uniform Resource Identifier (OMA-URI) settings to configure different features. These settings are typically used by mobile device manufacturers to control features on the device.

Windows client makes many Configuration Service Provider (CSP) settings available, such as [Policy Configuration Service Provider (Policy CSP)](/en-us/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers).

If you're looking for a specific setting, the [Windows device restriction profile](ref-device-restrictions-windows) and the [Settings catalog](../settings-catalog/) include many built-in settings. So, you may not need to enter custom values.

## Before you begin

- [Create a Windows custom profile](configure-custom-settings#create-the-profile).

## OMA-URI settings

**Add**: Enter the following settings:

- **Name**: Enter a unique name for the OMA-URI setting to help you identify it in the list of settings.
- **Description**: Enter a description that gives an overview of the setting, and any other important details.
- **OMA-URI** (case sensitive): Enter the OMA-URI you want to use as a setting.
- **Data type**: Select the data type you'll use for this OMA-URI setting. Your options:

    - Base64 (file)
    - Boolean
    - String (XML file)
    - Date and time
    - String
    - Floating point
    - Integer
- **Value**: Enter the data value you want to associate with the OMA-URI you entered. The value depends on the data type you selected. For example, if you select **Date and time**, select the value from a date picker.

After you add some settings, you can select **Export**. **Export** creates a list of all the values you added in a comma-separated values (`.csv`) file.

## Find the policies you can configure

For a complete list of all configuration service providers (CSPs) that Windows client supports, go to the [CSP reference](/en-us/windows/client-management/mdm/configuration-service-provider-reference).

Not all settings are compatible with all Windows client versions. The [CSP reference](/en-us/windows/client-management/mdm/configuration-service-provider-reference) lists the supported versions for each CSP.

Also, Intune doesn't support all the settings listed in [CSP reference](/en-us/windows/client-management/mdm/configuration-service-provider-reference). To find out if Intune supports the setting you want, open the article for that setting. Each setting page shows its supported operation. To work with Intune, the setting must support the **Add**, **Replace**, and **Get** operations. If the value returned by the **Get** operation doesn't match the value supplied by the **Add** or **Replace** operations, then Intune reports a compliance error.

Note

For settings created using a string, base64, or XML data type, the stored value is obscured. If the user who is accessing the value has any of the following permissions or roles, they can see the value:

- A Microsoft Intune role that has the **Device configurations** &gt; **Create**, **Read**, and **Update** permissions, like the **Policy and Profile manager** Intune built-in role.
- Intune Administrator Microsoft Entra role

For more information, go to:

- [Built-in role permissions for Microsoft Intune](../../fundamentals/role-based-access-control/ref-built-in-roles)
- [Microsoft Entra built-in roles - Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)