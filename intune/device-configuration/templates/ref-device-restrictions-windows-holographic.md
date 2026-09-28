---
layout: Conceptual
title: Windows Holographic Business device settings - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/ref-device-restrictions-windows-holographic
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
description: Read about and configure device restriction settings in Microsoft Intune for Windows Holographic for Business. Control unenrollment, geolocation, passwords, install apps from app store, cookies, and pop ups in Microsoft Edge, Microsoft Defender, search, cloud and storage, bluetooth connectivity, system time, and usage data.
ms.date: 2026-06-22T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: mikedano
suite: ems
locale: en-us
document_id: a5bb6f83-6c24-4da6-d575-b74a572507d0
document_version_independent_id: a5bb6f83-6c24-4da6-d575-b74a572507d0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/ref-device-restrictions-windows-holographic.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/ref-device-restrictions-windows-holographic
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/ref-device-restrictions-windows-holographic.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: 354da9ba-463a-0df0-c9f5-f8fadab5de92
---

# Windows Holographic Business device settings - Microsoft Intune | Microsoft Learn

This article describes the different settings you can control on Windows Holographic for Business devices, such as Microsoft HoloLens. As part of your mobile device management (MDM) solution, use these settings to allow or disable features, control security, and more.

As an Intune administrator, you can create and assign these settings to your devices.

## Before you begin

- [Create a Windows device restrictions configuration profile](configure-device-restrictions#create-the-profile).

When you create a Windows device restrictions configuration profile, there are more settings than what's listed in this article. The settings in this article are supported on Windows Holographic for Business devices.

## App Store

- **Auto-update apps from store**: **Block** prevents updates from being automatically installed from the Microsoft Store. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS might allow apps installed from the Microsoft Store to be automatically updated.

    [ApplicationManagement/AllowAppStoreAutoUpdate CSP](/en-us/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowappstoreautoupdate)
- **Trusted app installation**: Choose if non-Microsoft Store apps can be installed, also known as sideloading. Sideloading is installing, and then running or testing an app that isn't certified by the Microsoft Store. For example, an app that is internal to your company only. Your options:

    - **Not configured** (default): Intune doesn't change or update this setting.
    - **Block**: Prevents sideloading. Non-Microsoft Store apps can't be installed.
    - **Allow**: Allows sideloading. Non-Microsoft Store apps can be installed.

    [ApplicationManagement/AllowAllTrustedApps CSP](/en-us/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowalltrustedapps)
- **Developer unlock**: Allow Windows developer settings, such as allowing sideloaded apps to be modified by users. Your options:

    - **Not configured** (default): Intune doesn't change or update this setting.
    - **Block**: Prevents developer mode and sideloading apps.
    - **Allow**: Allows developer mode and sideloading apps.

    [ApplicationManagement/AllowDeveloperUnlock CSP](/en-us/windows/client-management/mdm/policy-csp-applicationmanagement#applicationmanagement-allowdeveloperunlock)

## Cellular and Connectivity

- **Bluetooth**: **Block** prevents users from enabling Bluetooth. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS might allow Bluetooth on the device.

    [Connectivity/AllowBluetooth CSP](/en-us/windows/client-management/mdm/policy-csp-connectivity#connectivity-allowbluetooth)
- **Bluetooth discoverability**: **Block** prevents the device from being discoverable by other Bluetooth-enabled devices. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS might allow other Bluetooth-enabled devices, such as a headset, to discover the device.

    [Bluetooth/AllowDiscoverableMode CSP](/en-us/windows/client-management/mdm/policy-csp-bluetooth#bluetooth-allowdiscoverablemode)
- **Bluetooth advertising**: **Block** prevents the device from sending out Bluetooth advertisements. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS might allow the device to send out Bluetooth advertisements.

    [Bluetooth/AllowAdvertising CSP](/en-us/windows/client-management/mdm/policy-csp-bluetooth#bluetooth-allowadvertising)

## Cloud and Storage

- **Microsoft account**: **Block** prevents users from associating a Microsoft account with the device. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS might allow adding and using a Microsoft account.

    [Accounts/AllowMicrosoftAccountConnection CSP](/en-us/windows/client-management/mdm/policy-csp-accounts#accounts-allowmicrosoftaccountconnection)

## Control Panel and Settings

- **System time modification**: **Block** prevents users from changing the date and time settings on the device. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS might allow users to change these settings.

    [Settings/AllowDateTime CSP](/en-us/windows/client-management/mdm/policy-csp-settings#settings-allowdatetime)

## General

- **Manual unenrollment**: **Block** prevents users from deleting the workplace account using the workplace control panel on the device. When set to **Not configured** (default), Intune doesn't change or update this setting.

    [Experience/AllowManualMDMUnenrollment CSP](/en-us/windows/client-management/mdm/policy-csp-experience#experience-allowmanualmdmunenrollment)
- **Geolocation**: **Block** prevents users from turning on location services on the device. When set to **Not configured** (default), Intune doesn't change or update this setting.

    [Experience/AllowFindMyDevice CSP](/en-us/windows/client-management/mdm/policy-csp-experience#experience-allowfindmydevice)
- **Cortana**: **Block** disables the Cortana voice assistant on the device. When Cortana is off, users can still search to find items on the device. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS might allow Cortana.

    [Experience/AllowCortana CSP](/en-us/windows/client-management/mdm/policy-csp-experience#experience-allowcortana)

    Note

    Microsoft deprecated the Windows Cortana standalone app. The Cortana productivity assistant is still available. For more information on deprecated features on Windows client, go to [Deprecated features for Windows client](/en-us/windows/whats-new/deprecated-features).

## Microsoft Edge Browser

- **Start experience** &gt; **Allow pop-ups**: **Yes** (default) allows pop-ups in the web browser. **No** prevents pop-up windows in the browser.

    [Browser/AllowPopups CSP](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowpopups)
- **Favorites and search** &gt; **Show search suggestions**: **Yes** (default) allows your search engine to suggest sites as you type search phrases in the address bar. **No** prevents this feature.

    [Browser/AllowSearchSuggestionsinAddressBar CSP](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowsearchsuggestionsinaddressbar)
- **Privacy and security** &gt; **Allow Password Manager**: **Yes** (default) allows Microsoft Edge to automatically use Password Manager, which allows users to save and manage passwords on the device. **No** prevents Microsoft Edge from using Password Manager.

    [Browser/AllowPasswordManager CSP](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager)
- **Privacy and security** &gt; **Cookies**: Choose how cookies are handled in the web browser. Your options:

    - **Allow**: Cookies are stored on the device.
    - **Block all cookies**: Cookies aren't stored on the device.
    - **Block only third party cookies**: Third party or partner cookies aren't stored on the device.

    [Browser/AllowCookies CSP](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowcookies)
- **Privacy and security** &gt; **Send do-not-track headers**: **Yes** sends do-not-track headers to websites requesting tracking info (recommended). **No** (default) doesn't send headers that allow websites to track the user. Users can configure this setting.

    [Browser/AllowDoNotTrack CSP](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowdonottrack)

## Microsoft Defender SmartScreen

- **SmartScreen for Microsoft Edge**: **Require** turns on Microsoft Defender SmartScreen, and prevents users from turning it off. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS might turn on SmartScreen, and allow users to turn it on and off.

    [Browser/AllowSmartScreen CSP](/en-us/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen)

## Password

- **Password**: **Require** forces users to enter a password to access the device. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS might allow access to devices without a password. Applies to local accounts only. Domain account passwords remain configured by Active Directory (AD) and Microsoft Entra ID.

    [DeviceLock/DevicePasswordEnabled CSP](/en-us/windows/client-management/mdm/policy-csp-devicelock#devicelock-devicepasswordenabled)
- **Require password when device returns from idle state**: **Require** forces users to enter a password to unlock the device after being idle. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS might not require a PIN or password after being idle.

    [DeviceLock/AllowIdleReturnWithoutPassword CSP](/en-us/windows/client-management/mdm/policy-csp-devicelock#devicelock-allowidlereturnwithoutpassword)

## Reporting and Telemetry

- **Share usage data**: Choose the level of diagnostic data that's submitted. Your options:

    - **Not configured** (default): Intune doesn't change or update this setting. No setting is forced. Users choose the level that's submitted. By default, the OS might not share any data.
    - **Security**: Information that's required to help keep Windows more secure, including data about the Connected User Experience and Telemetry component settings, the Malicious Software Removal Tool, and Microsoft Defender
    - **Basic**: Basic device information, including quality-related data, app compatibility, app usage data, and data from the Security level
    - **Enhanced**: Additional insights, including how Windows, Windows Server, System Center, and apps are used, how they perform, advanced reliability data, and data from both the Basic and the Security levels
    - **Full**: All data necessary to identify and help to fix problems, plus data from the Security, Basic, and Enhanced level.

    [System/AllowTelemetry CSP](/en-us/windows/client-management/mdm/policy-csp-system#system-allowtelemetry)

## Search

- **Search location**: **Block** prevents Windows Search from using the location. When set to **Not configured** (default), Intune doesn't change or update this setting. By default, the OS might allow this feature.

    [Search/AllowSearchToUseLocation CSP](/en-us/windows/client-management/mdm/policy-csp-search#search-allowsearchtouselocation)