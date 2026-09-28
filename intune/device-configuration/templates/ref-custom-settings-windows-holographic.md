---
layout: Conceptual
title: Custom settings - Windows Holographic for Business devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-custom-settings-windows-holographic
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
description: Add or create a custom profile to use the OMA-URI settings for devices running Windows Holographic for Business in Microsoft Intune, including Microsoft HoloLens. You can set AllowFastReconnect, AllowVPN, AllowUpdateService, UpdateServiceURL, RequireUpdatesApproval, ApprovedUpdates, and ApplicationLaunchRestrictions policy configuration service provider (CSP) settings.
ms.date: 2024-04-16T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: mikedano
locale: en-us
document_id: 6976a7ff-edec-a982-93a1-298b83eb5f3d
document_version_independent_id: 6976a7ff-edec-a982-93a1-298b83eb5f3d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-custom-settings-windows-holographic.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-custom-settings-windows-holographic
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-custom-settings-windows-holographic.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 2ea9e3a0-20bb-82a8-42c4-9508547b371e
---

# Custom settings - Windows Holographic for Business devices - Microsoft Intune | Microsoft Learn

Using Microsoft Intune, you can add or create custom settings for your Windows Holographic for Business devices using **custom profiles**. Custom profiles are a feature in Intune. They're designed to add device settings and features that aren't built in to Intune.

This article applies to:

- Windows Holographic for Business
- Windows

Windows Holographic for Business custom profiles use Open Mobile Alliance Uniform Resource Identifier (OMA-URI) settings to configure different features. These settings are typically used by mobile device manufacturers to control features on the device.

Windows Holographic for Business makes many configuration service providers (CSPs) settings available. For a CSP overview, go to [Introduction to configuration service providers (CSPs) for IT pros](/en-us/windows/configuration/provisioning-packages/how-it-pros-can-use-configuration-service-providers). For specific CSPs supported by Windows Holographic, go to [CSPs supported in Windows Holographic](/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens).

If you're looking for a specific setting, remember that the [Windows Holographic for Business device restriction profile](ref-device-restrictions-windows-holographic) includes many built-in settings. So, you might not need to enter custom values.

This article shows you how to create a custom profile for Windows Holographic for Business devices. It also includes a list of the recommended OMA-URI settings.

## Before you begin

- [Create a Windows custom profile](configure-custom-settings#create-the-profile).

## Custom OMA-URI Settings

**Add**: Enter the following settings:

- **Name**: Enter a unique name for the OMA-URI setting so you can identify the setting in the settings list.
- **Description**: Enter a description that gives an overview of the setting, and any other important details.
- **OMA-URI** (case sensitive): Enter the OMA-URI you want to use as a setting.
- **Data type**: Select the data type you want for this OMA-URI setting. Your options:

    - String
    - String (XML file)
    - Date and time
    - Integer
    - Floating point
    - Boolean
    - Base64 (file)
- **Value**: Enter the data value you want to associate with the OMA-URI you entered. The value depends on the data type you selected. For example, if you select **Date and time**, select the value from a date picker.

After you add and **Save** your settings, you can select **Export**. **Export** creates a list of all the values you added in a comma-separated values (`.csv`) file.

## Recommended custom settings

The following settings are useful for devices running Windows Holographic for Business:

### [AllowFastReconnect](/en-us/windows/client-management/mdm/policy-csp-authentication#authentication-allowfastreconnect)

| OMA-URI | Data type |
| --- | --- |
| `./Vendor/MSFT/Policy/Config/Authentication/AllowFastReconnect` | Integer0 - not allowed1 - allowed (default) |

### [AllowUpdateService](/en-us/windows/client-management/mdm/policy-csp-update#update-allowupdateservice)

| OMA-URI | Data type |
| --- | --- |
| `./Vendor/MSFT/Policy/Config/Update/AllowUpdateService` | Integer0 – Update service is not allowed 1 – Update service is allowed (default). |

### [AllowVPN](/en-us/windows/client-management/mdm/policy-csp-settings#settings-allowvpn)

| OMA-URI | Data type |
| --- | --- |
| `./Vendor/MSFT/Policy/Config/Settings/AllowVPN` | Integer0 - not allowed1 - allowed (default) |

### [RequireUpdateApproval](/en-us/windows/client-management/mdm/policy-csp-update#update-requireupdateapproval)

| OMA-URI | Data type |
| --- | --- |
| `./Vendor/MSFT/Policy/Config/Update/RequireUpdateApproval` | This setting is available in RS5 (build 17763) and earlier. Starting with 19H1 (build 18362), use [Windows Update client policies](../../device-updates/windows/).Integer0 – Not configured. The device installs all applicable updates.1 – The device only installs updates that are both applicable and on the Approved Updates list. Set this policy to 1 if IT wants to control the deployment of updates on devices, like when testing is required prior to deployment. |

### [ScheduledInstallTime](/en-us/windows/client-management/mdm/policy-csp-update#update-scheduledinstalltime)

| OMA-URI | Data type |
| --- | --- |
| `./Vendor/MSFT/Policy/Config/Update/ScheduledInstallTime` | Integer 0-23, where 0=12AM and 23=11PMDefault value is 3. |

### [UpdateServiceURL](/en-us/windows/client-management/mdm/policy-csp-update#update-updateserviceurl)

| OMA-URI | Data type |
| --- | --- |
| `./Vendor/MSFT/Policy/Config/Update/UpdateServiceUrl` | This setting is available in RS5 (build 17763) and earlier. Starting with 19H1 (build 18362), use [Windows Update client policies](../../device-updates/windows/).StringURL - the device checks for updates from the WSUS server at the specified URL.Not configured - The device checks for updates from Microsoft Update. |

### [ApprovedUpdates](/en-us/windows/client-management/mdm/update-csp)

| OMA-URI | Data type |
| --- | --- |
| `./Vendor/MSFT/Update/ApprovedUpdates/*GUID*`**Important**You must read and accept the update EULAs on behalf of your end users. If you don't read and accept the EULA, it's a breach of legal or contractual obligations. | Node for update approvals and EULA acceptance on behalf of the end user.For more information, go to [Update CSP](/en-us/windows/client-management/mdm/update-csp). |

### [ApplicationLaunchRestrictions](/en-us/windows/client-management/mdm/applocker-csp)

| OMA-URI | Data type |
| --- | --- |
| `./Vendor/MSFT/AppLocker/ApplicationLaunchRestrictions/*Grouping*/*ApplicationType*/Policy`**Important**The AppLocker CSP article uses escaped XML examples. To configure the settings with Intune custom profiles, you must use plain XML. | StringFor more information, go to [AppLocker CSP](/en-us/windows/client-management/mdm/applocker-csp). |

### [DeletionPolicy](/en-us/windows/client-management/mdm/accountmanagement-csp)

| OMA-URI | Data type |
| --- | --- |
| `./Vendor/MSFT/AccountManagement/UserProfileManagement/DeletionPolicy` | Integer0 - delete immediately when the device returns to a state with no currently active users1 - delete at storage capacity threshold (default)2 - delete at both storage capacity threshold and profile inactivity threshold |

### [EnableProfileManager](/en-us/windows/client-management/mdm/accountmanagement-csp)

| OMA-URI | Data type |
| --- | --- |
| `./Vendor/MSFT/AccountManagement/UserProfileManagement/EnableProfileManager` | BooleanTrue - enableFalse - disable (default) |

### [ProfileInactivityThreshold](/en-us/windows/client-management/mdm/accountmanagement-csp)

| OMA-URI | Data type |
| --- | --- |
| `./Vendor/MSFT/AccountManagement/UserProfileManagement/ProfileInactivityThreshold` | IntegerDefault value is 30. |

### [StorageCapacityStartDeletion](/en-us/windows/client-management/mdm/accountmanagement-csp)

| OMA-URI | Data type |
| --- | --- |
| `./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStartDeletion` | IntegerDefault value is 25. |

### [StorageCapacityStopDeletion](/en-us/windows/client-management/mdm/accountmanagement-csp)

| OMA-URI | Data type |
| --- | --- |
| `./Vendor/MSFT/AccountManagement/UserProfileManagement/StorageCapacityStopDeletion` | IntegerDefault value is 50. |

## Find the policies you can configure

There's a complete list of all configuration service providers (CSPs) that Windows Holographic supports at [CSPs supported in Windows Holographic](/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens). Not all settings are compatible with all Windows Holographic versions. The table in [CSPs supported in Windows Holographic](/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens) lists the supported versions for each CSP.

Also, Intune doesn't support all of the settings listed in [CSPs supported in Windows Holographic](/en-us/windows/client-management/mdm/configuration-service-provider-reference#hololens). To find out if Intune supports the setting you want, open the article for that setting. Each setting page shows its supported operation. To work with Intune, the setting must support the **Add** or **Replace** operations.