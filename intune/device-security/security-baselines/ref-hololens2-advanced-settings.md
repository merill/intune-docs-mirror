---
layout: Conceptual
title: List of settings for the Microsoft HoloLens 2 advanced security baseline in Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/security-baselines/ref-hololens2-advanced-settings
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- sub-secure-endpoints
ms.reviewer: aanavath
ms.subservice: protect
description: View a list of the settings in the Microsoft Intune advanced security baseline for Microsoft HoloLens 2. This list includes the default values for settings as found in the default configuration of the baseline.
ms.date: 2025-01-27T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: 46353b44-7a7e-eb69-4a02-4749b68dc34a
document_version_independent_id: 46353b44-7a7e-eb69-4a02-4749b68dc34a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/security-baselines/ref-hololens2-advanced-settings.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/security-baselines/ref-hololens2-advanced-settings
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/security-baselines/ref-hololens2-advanced-settings.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/05616262-6974-4662-ac87-15adf94b9c3a
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/25c95491-bd10-484c-89ce-1fa29173d007
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 96d0d8e6-5d95-6632-7dae-31b39e692520
---

# List of settings for the Microsoft HoloLens 2 advanced security baseline in Intune - Microsoft Intune | Microsoft Learn

This article is a reference for the settings that are available in the Microsoft HoloLens 2 advanced security baseline for Microsoft Intune.

Tip

To view settings for the Microsoft HoloLens 2 *standard* security baseline, see [Settings reference for the Microsoft HoloLens 2 standard security baseline for Microsoft Intune](ref-hololens2-standard-settings).

## About this reference article

Each security baseline is a group of preconfigured Windows settings that help you apply and enforce granular security settings that the relevant security teams recommend. You can also customize each baseline you deploy to enforce only those settings and values you require. When you create a security baseline profile in Intune, you're creating a template that consists of multiple device configuration settings.

The details that display in this article are based on baseline version you select at the top of the article. For each version, this article displays:

- A list of each setting with its configuration as found in the default instance of that baseline version.
- When available, a link to the underlying configuration service provider (CSP) documentation or other related content from the relevant product group that provides context and possibly additional details for a settings use.

When a new version of a baseline becomes available, it replaces the previous version. Profile instances that were created before the availability of a new version:

- Become read-only. You can continue to use those profiles but can't edit them to change their configuration.
- Can be updated to the current version. After you update a profile to the current baseline version, you can edit the profile to modify settings.

To learn more about using security baselines, see:

- [Use security baselines](overview)
- [Change the baseline version for a profile](configure-baselines#update-a-baseline-profile-to-the-latest-version)
- [Manage security baselines](configure-baselines)

## HoloLens 2 Advanced security baseline for (version 1) - *January 2025*

### Account Management

- **Deletion Policy** Baseline default: *Delete at both storage capacity threshold and profile inactivity threshold*[Learn more](/en-us/windows/client-management/mdm/AccountManagement-csp#userprofilemanagementdeletionpolicy)
- **Enable Profile Manager** Baseline default: *True*[Learn more](/en-us/windows/client-management/mdm/accountmanagement-csp#userprofilemanagementenableprofilemanager)
- **Profile Inactivity Threshold** Baseline default: *Configured* Value: *30*[Learn more](/en-us/windows/client-management/mdm/accountmanagement-csp#userprofilemanagementprofileinactivitythreshold)
- **Storage Capacity Start Deletion** Baseline default: *Configured* Value: *25*[Learn more](/en-us/windows/client-management/mdm/accountmanagement-csp#userprofilemanagementstoragecapacitystartdeletion)
- **Storage Capacity Stop Deletion** Baseline default: *Configured* Value: *50*[Learn more](/en-us/windows/client-management/mdm/accountmanagement-csp#userprofilemanagementstoragecapacitystopdeletion)

### Accounts

- **Allow Microsoft Account Connection** Baseline default: *Block*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Accounts#allowmicrosoftaccountconnection)

### Administrative Templates

#### System &gt; Power Management &gt; Video and Display Settings

- **Turn off the display (plugged in)** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-power#power-displayofftimeoutpluggedin)

    - **When plugged in, turn display off after (seconds)** Baseline default: *30*

### Browser

- **Allow Autofill** Baseline default: *Block*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Browser#allowautofill)
- **Allow Cookies** Baseline default: *Block only cookies from third party websites*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Browser#allowcookies)
- **Allow Do Not Track** Baseline default: *Block*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Browser#allowdonottrack)
- **Allow Password Manager** Baseline default: *Block*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Browser#allowpasswordmanager)
- **Allow Popups** Baseline default: *Block*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Browser#allowpopups)
- **Allow Search Suggestions in Address Bar** Baseline default: *Block*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Browser#allowsearchsuggestionsinaddressbar)
- **Allow Smart Screen** Baseline default: *Allow*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Browser#allowsmartscreen)

### Connectivity

- **Allow Bluetooth** Baseline default: *Disallow Bluetooth. The radio in the Bluetooth control panel will be grayed out and the user will not be able to turn Bluetooth on.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-connectivity#allowbluetooth)
- **Allow USB Connection** Baseline default: *Not allowed.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-connectivity#allowusbconnection)

### Device Lock

- **Device Password Enabled** Baseline default: *Enabled*[Learn more](/en-us/windows/client-management/mdm/policy-csp-devicelock#devicepasswordenabled)

    - **Max Device Password Failed Attempts** Baseline default: *Configured* Value: *10*[Learn more](/en-us/windows/client-management/mdm/policy-csp-devicelock#maxdevicepasswordfailedattempts)
    - **Allow Idle Return Without Password** Baseline default: *Not allowed.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-deviceLock#allowidlereturnwithoutpassword)
    - **Alphanumeric Device Password Required** Baseline default: *Password or Numeric PIN required.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-devicelock#alphanumericdevicepasswordrequired)
    - **Max Inactivity Time Device Lock** Baseline default: *Configured* Value: *3*[Learn more](/en-us/windows/client-management/mdm/policy-csp-devicelock#maxinactivitytimedevicelock)
    - **Device Password History** Baseline default: *Configured* Value: *15*[Learn more](/en-us/windows/client-management/mdm/policy-csp-devicelock#devicepasswordhistory)
    - **Allow Simple Device Password** Baseline default: *Not allowed.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-devicelock#allowsimpledevicepassword)
    - **Device Password Expiration** Baseline default: *Not configured*[Learn more](/en-us/windows/client-management/mdm/policy-csp-devicelock#devicepasswordexpiration)
    - **Min Device Password Length** Baseline default: *Configured* Value: *12*[Learn more](/en-us/windows/client-management/mdm/policy-csp-devicelock#mindevicepasswordlength)

### Experience

- **Allow Manual MDM Unenrollment** Baseline default: *Block*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Experience#allowmanualmdmunenrollment)

### Microsoft App Store

- **Allow All Trusted Apps** Baseline default: *Explicit deny.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-ApplicationManagement#allowalltrustedapps)
- **Allow apps from the Microsoft app store to auto update** Baseline default: *Allowed.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-ApplicationManagement#allowappstoreautoupdate)
- **Allow Developer Unlock** Baseline default: *Explicit deny.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-ApplicationManagement#allowdeveloperunlock)

### Microsoft Edge

- **Block third party cookies** Baseline default: *Enabled*
- **Configure Do Not Track** Baseline default: *Disabled*
- **Enable AutoFill for addresses** Baseline default: *Disabled*
- **Enable AutoFill for payment instruments** Baseline default: *Disabled*
- **Enable search suggestions** Baseline default: *Disabled*

#### Content settings

- **Default pop-up window setting** Baseline default: *Enabled*

    - **Default pop-up window setting (Device)** Baseline default: *Do not allow any site to show popups*

#### Extensions

- **Control which extensions cannot be installed** Baseline default: *Enabled*

    - **Extension IDs the user should be prevented from installing (or \* for all) (Device)** Baseline default: \*

#### Password manager and protection

- **Configures a setting that asks users to enter their device password while using password autofill** Baseline default: *Enabled*

    - **Configures a setting that asks users to enter their device password while using password autofill (Device)** Baseline default: *Autofill off*
- **Enable saving passwords to the password manager** Baseline default: *Disabled*

#### SmartScreen settings

- **Configure Microsoft Defender SmartScreen** Baseline default: *Enabled*

### Mixed Reality

- **AAD Group Membership Cache Validity In Days** Baseline default: *Configured* Value: *7*[Learn more](/en-us/windows/client-management/mdm/policy-csp-MixedReality#aadgroupmembershipcachevalidityindays)

### Privacy

- **Let Apps Access Account Info** Baseline default: *Force deny.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Privacy#letappsaccessaccountinfo)
- **Let Apps Access Account Info Force Allow These Apps** Baseline default: *Configured* Values:

    - *Microsoft.Dynamics365.Guides\_8wekyb3d8bbwe*
    - *Microsoft.MicrosoftRemoteAssist\_8wekyb3d8bbwe*

    [Learn more](/en-us/windows/client-management/mdm/policy-csp-Privacy#letappsaccessaccountinfo_forceallowtheseapps)
- **Let Apps Access Background Spatial Perception** Baseline default: *Force deny.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Privacy#letappsaccessbackgroundspatialperception)
- **Let Apps Access Background Spatial Perception Force Allow These Apps** Baseline default: *Configured*

    - *Microsoft.Dynamics365.Guides\_8wekyb3d8bbwe*
    - *Microsoft.MicrosoftRemoteAssist\_8wekyb3d8bbwe*

    [Learn more](/en-us/windows/client-management/mdm/policy-csp-Privacy#letappsaccessbackgroundspatialperception_forceallowtheseapps)
- **Let Apps Access Camera** Baseline default: *Force deny.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Privacy#letappsaccesscamera)
- **Let Apps Access Camera Force Allow These Apps** Baseline default: *Configured* Values:

    - *Microsoft.Dynamics365.Guides\_8wekyb3d8bbwe*
    - *Microsoft.MicrosoftRemoteAssist\_8wekyb3d8bbwe*

    [Learn more](/en-us/windows/client-management/mdm/policy-csp-Privacy#letappsaccesscamera_forceallowtheseapps)
- **Let Apps Access Microphone** Baseline default: *Force deny.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Privacy#letappsaccessmicrophone)
- **Let Apps Access Microphone Force Allow These Apps** Baseline default: *Configured* Values:

    - *Microsoft.Dynamics365.Guides\_8wekyb3d8bbwe*
    - *Microsoft.MicrosoftRemoteAssist\_8wekyb3d8bbwe*

    [Learn more](/en-us/windows/client-management/mdm/policy-csp-Privacy#letappsaccessmicrophone_forceallowtheseapps)

### Search

- **Allow Search To Use Location** Baseline default: *Block*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Search#allowsearchtouselocation)

### Security

- **Allow Add Provisioning Package** Baseline default: *Block*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Security#allowaddprovisioningpackage)

### Settings

- **Allow VPN** Baseline default: *Not allowed.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Settings#allowvpn)
- **Page Visibility List** Baseline default: *Configured* Value: *hide:emailandaccounts;workplace;otherusers;bluetooth;usb;network-proxy;network-wifi;network-ethernet;network-airplanemode;powersleep;certificates;developers;windowsinsider;*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Settings#pagevisibilitylist)

### System

- **Allow Storage Card** Baseline default: *SD card use is not allowed and USB drives are disabled. This setting does not prevent programmatic access to the storage card.*[Learn more](/en-us/windows/client-management/mdm/policy-csp-System#allowstoragecard)
- **Allow Telemetry** Baseline default: *Security*[Learn more](/en-us/windows/client-management/mdm/policy-csp-System#allowtelemetry)

### Tenant Lockdown

- **Require Network In OOBE (Device)** Baseline default: *True*

### Wi-Fi Settings

- **Allow Manual Wi Fi Configuration** Baseline default: *Allow*[Learn more](/en-us/windows/client-management/mdm/policy-csp-wifi#allowmanualwificonfiguration)

Important

Allow or block connections to Wi-Fi outside of MDM server-installed networks. If you change this setting to Block, you must deploy enterprise Wi-Fi profiles to the device using the Wi-Fi CSP before you apply this setting. Otherwise, the device will go offline since it won't be able to connect to Wi-Fi. Note that choosing to block Wi-Fi connections will delete any previously installed user-configured Wi-Fi profiles from the device, though not all non-MDM profiles will be deleted.

### Windows Hello For Business

- **Enable Pin Recovery** Baseline default: *False*[Learn more](/en-us/windows/client-management/mdm/passportforwork-csp#devicetenantidpoliciesenablepinrecovery)
- **Restrict use of TPM 1.2** Baseline default: *Disabled*[Learn more](/en-us/windows/client-management/mdm/passportforwork-csp#devicetenantidpoliciesexcludesecuritydevicestpm12)
- **Digits** Baseline default: *Requires the use of at least one digits in PIN.*[Learn more](/en-us/windows/client-management/mdm/passportforwork-csp#devicetenantidpoliciespincomplexitydigits)
- **Expiration** Baseline default: *Configured* Value: *90*[Learn more](/en-us/windows/client-management/mdm/passportforwork-csp#devicetenantidpoliciespincomplexityexpiration)
- **PIN History** Baseline default: *Configured* Value: *10*[Learn more](/en-us/windows/client-management/mdm/passportforwork-csp#usertenantidpoliciespincomplexityhistory)
- **Lowercase Letters** Baseline default: *Required*[Learn more](/en-us/windows/client-management/mdm/PassportForWork-csp#devicetenantidpoliciespincomplexitylowercaseletters)
- **Maximum PIN Length** Baseline default: *Configured* Value: *6*[Learn more](/en-us/windows/client-management/mdm/passportforwork-csp#devicetenantidpoliciespincomplexitymaximumpinlength)
- **Minimum PIN Length** Baseline default: *Configured* Value: *6*[Learn more](/en-us/windows/client-management/mdm/passportforwork-csp#usertenantidpoliciespincomplexityminimumpinlength)
- **Special Characters** Baseline default: *Requires the use of at least one special characters in PIN.*[Learn more](/en-us/windows/client-management/mdm/passportforwork-csp#usertenantidpoliciespincomplexityspecialcharacters)
- **Uppercase Letters** Baseline default: *Required*[Learn more](/en-us/windows/client-management/mdm/passportforwork-csp#usertenantidpoliciespincomplexityuppercaseletters)
- **Require Security Device** Baseline default: *True*[Learn more](/en-us/windows/client-management/mdm/passportforwork-csp#devicetenantidpoliciesrequiresecuritydevice)
- **Use Certificate For On Prem Auth** Baseline default: *Disabled*[Learn more](/en-us/windows/client-management/mdm/passportforwork-csp#devicetenantidpoliciesusecertificateforonpremauth)
- **Use Hello Certificates As Smart Card Certificates** Baseline default: *Disabled*[Learn more](/en-us/windows/client-management/mdm/passportforwork-csp#devicetenantidpoliciesusehellocertificatesassmartcardcertificates)
- **Use Windows Hello For Business (Device)** Baseline default: *True*[Learn more](/en-us/windows/client-management/mdm/passportforwork-csp#devicetenantidpoliciesusepassportforwork)

### Windows Update For Business

- **Allow Update Service** Baseline default: *Allow*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Update#allowupdateservice)
- **Manage Preview Builds** Baseline default: *Disable Preview builds*[Learn more](/en-us/windows/client-management/mdm/policy-csp-Update#managepreviewbuilds)

## Learn more

- [Learn about security baselines](overview)
- [Avoid conflicts](overview#avoid-conflicts)
- [Troubleshoot policies and profiles in Intune](/en-us/troubleshoot/mem/intune/troubleshoot-policies-in-microsoft-intune)