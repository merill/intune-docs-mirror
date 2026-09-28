---
layout: Conceptual
title: Review App Protection Policy Logs - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/protection/troubleshoot-protection-logs
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
description: This topic describes how to configure Intune app protection policy (APP) logs.
ms.date: 2025-10-23T00:00:00.0000000Z
ms.topic: troubleshooting
ms.reviewer: demerson
locale: en-us
document_id: c9d29c01-b318-374a-7565-98b806c798be
document_version_independent_id: c9d29c01-b318-374a-7565-98b806c798be
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/protection/troubleshoot-protection-logs.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/protection/troubleshoot-protection-logs
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/protection/troubleshoot-protection-logs.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7428317a-e6c2-4461-ad3e-8a8ad3608734
- https://authoring-docs-microsoft.poolparty.biz/devrel/9d7be3ef-f27c-4c7f-9eba-67c3cd429995
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e4f59707-f107-48f2-8d75-0afd91868cd7
- https://authoring-docs-microsoft.poolparty.biz/devrel/feeb50f3-b677-44f9-b3a6-5f2f58182b0d
platformId: c130ede5-4ffa-a5a1-04bf-4bf7352bcaff
---

# Review App Protection Policy Logs - Microsoft Intune | Microsoft Learn

Learn about the settings you can review in the app protection logs. Access logs by enabling Intune Diagnostics on a mobile client.

The process to enable and collect logs varies by platform:

- **iOS/iPadOS devices** - Use Microsoft Edge for iOS/iPadOS to collect logs. For details, see [Use Microsoft Edge for iOS and Android to access managed app logs](../configuration/configure-edge-ios-android#use-microsoft-edge-for-ios-and-android-to-access-managed-app-logs).

## Log files

- **Windows devices** - Use *MDMDiag* and event logs. See, [Collect MDM logs](/en-us/windows/client-management/mdm-collect-logs) in the Windows client management content, and the blog [Troubleshooting Windows Intune Policy Failures](/en-us/archive/blogs/configmgrdogs/troubleshooting-windows-10-intune-policy-failures).
- **Android devices** - Use Microsoft Edge for Android to collect logs. For details, see [Use Microsoft Edge for iOS and Android to access managed app logs](../configuration/configure-edge-ios-android#use-microsoft-edge-for-ios-and-android-to-access-managed-app-logs).

    Note

    On Android Fully Managed devices, in certain instances the Intune Company Portal app may be visible under all apps. This may happen when an app associated with an app protection policy is either not installed or not launched.

The following tables list the App protection policy setting name and supported values that are recorded in the log. In addition, each setting identifies the policy setting found within Microsoft Intune admin center. For detailed information on each setting, see [iOS/iPadOS app protection policy settings](ref-settings-ios) and [Android app protection policy settings in Microsoft Intune](ref-settings-android).

## iOS/iPadOS App protection policy settings

| Name | Value details | Setting in Microsoft Intune App Protection Policy |
| --- | --- | --- |
| AccessRecheckOfflineTimeout | x minutes | **Section**: Conditional launch**Setting**: Offline grace period with action Block access (minutes) |
| AccessRecheckOnlineTimeout | *x* minutes | **Section**: Access requirements**Setting**: Recheck the Access requirements after (minutes of inactivity) |
| AllowedIOSModelsElseBlock | x characters | **Section**: Conditional launch**Setting**: Device model(s) with action Allow specified (Block non-specific) |
| AllowedIOSModelsElseWipe | x characters | **Section**: Conditional launch**Setting**: Device model(s) with action Allow specified (Wipe non-specific) |
| AppActionIfUnableToAuthenticateUser | 0 = Block access1 = Wipe data required | **Section**: Conditional launch**Setting**: Disabled account |
| AppPinDisabled | 0 = Require1 = Not required | **Section**: Access requirements**Setting**: App PIN when device PIN is set |
| AppSharingFromLevel | 0 = None1 = Policy Managed apps2 = All apps | **Section**: Data protection**Setting**: Receive data from other apps |
| AppSharingToLevel | 0 = None1 = Policy managed apps2 = All app | **Section**: Data protection**Setting**: Send org data to other apps |
| AuthenticationEnabled | 0 = Not required1 = Require | **Section**: Access requirements**Setting**: Work or school account credentials for access |
| ClipboardCharacterLengthException | x characters | **Section**: Data protection**Setting**: Cut and copy character limit for any app |
| ClipboardEncryptionEnabled | 0 = Disabled1 = Enabled | No administrative control for this setting. |
| ClipboardSharingLevel | 0 = Blocked1 = Policy managed apps2 = Policy managed apps with paste in3 = Any app | **Section**: Data protection**Setting**: Restrict cut, copy, and paste between other apps |
| ContactSyncDisabled | 0 = Allow1 = Block | **Section**: Data protection**Setting**: Sync app with native contacts app |
| DataBackupDisabled | 0 = Allow1 = Block | **Section**: Data protection**Setting**: Prevent backups |
| DeviceComplianceEnabled | 0 = False1 = True | **Section**: Conditional launch**Setting**: Jailbroken/rooted devices |
| DeviceComplianceFailureAction | 0 = Block access1 = Wipe data | **Section**: Conditional launch**Setting**: Jailbroken/rooted devices |
| DialerRestrictionLevel | 0 = None, do not transfer this data between apps1 = A specific dialer app3 = Any dialer app | **Section**: Data protection**Setting**: Transfer telecommunication data to |
| DictationBlocked | 0 = Allow1 = Block | No administrative control for this setting. |
| DisableShareSense | N/A | N/A: Not actively used by the Intune service. |
| EnableOpenInFilter | 0 = Disabled1 = Enabled | **Section**: Data protection**Setting**: Send Org data to other apps &gt; Policy managed apps with Open-In/Share filtering |
| FaceIDEnabled | 0 = Block1 = Allow | **Section**: Access requirements**Setting**: Face ID instead of PIN for access (iOS 11+/iPadOS) |
| FileEncryptionLevel | 0 = When device is locked1 = When device is locked and there are open files2 = After device restart3 = Use device settings | **Section**: Data protection**Setting**: Encrypt org data |
| FileSharingSaveAsDisabled | 0 = Allow1 = Block | **Section**: Data protection**Setting**: Save copies of org data |
| GenmojiConfigurationState | 0 = Allow1 = Block | **Section**: Data protection**Setting**: Genmoji |
| IntuneIdentityUPN | UPN of the Intune MAM user | N/A |
| ManagedBrowserRequired | 0 = False1 = True | **Section**: Data protection**Setting**: Restrict web content transfer with other apps |
| ManagedLocations | A value that represents the number of managed storage locations to which the app can save data. 1 = OneDrive2 = SharePoint3 = OneDrive & SharePoint4 = Box5 = OneDrive & Box6 = SharePoint & Box7 = OneDrive, SharePoint & Box32 = Local Storage33 = Local Storage & OneDrive34 = Local Storage & SharePoint35 = Local Storage, OneDrive & SharePoint36 = Local Storage & Box37 = Local Storage, OneDrive & Box38 = Local Storage, SharePoint & Box39 = Local Storage, OneDrive, SharePoint & Box128 = Photo Library129 = Photo Library & OneDrive130 = Photo Library & SharePoint131 = Photo Library, OneDrive & SharePoint132 = Photo Library & Box133 = Photo Library, OneDrive & Box134 = Photo Library, SharePoint & Box135 = Photo Library, OneDrive, SharePoint & Box160 = Photo Library, Local Storage161 = Photo Library, Local Storage & OneDrive162 = Photo Library, Local Storage & SharePoint163 = Photo Library, Local Storage, OneDrive & SharePoint164 = Photo Library, Local Storage & Box165 = Photo Library, Local Storage, OneDrive & Box166 = Photo Library, Local Storage, SharePoint & Box167 = Photo Library, Local Storage, OneDrive, SharePoint & Box | **Section**: Data protection**Setting**: Allow user to save copies to selected services |
| ManagedUniversalLinks | A list of universal links that allow data to be open in the corresponding managed apps | **Section**: Data protection**Setting**: Select managed universal links |
| MaxPinRetryExceededAction | 0 = Reset PIN1 = Wipe data | **Section**: Conditional launch**Setting**: Max PIN attempts |
| MaxOsVersion | maximum OS version | **Section**: Conditional launch**Setting**: Max OS version with action Block access |
| MaxOsVersionWarning | maximum OS version | **Section**: Conditional launch**Setting**: Max OS version with action Warn |
| MaxOsVersionWipe | maximum OS version | **Section**: Conditional launch**Setting**: Max OS version with action Wipe data |
| MinAppVersion | "0.0" = no minimum app versionanything else = minimum app version | **Section**: Conditional launch**Setting**: Min app version with action Block access |
| MinAppVersionWarning | "0.0" = no minimum app version.anything else = minimum app version | **Section**: Conditional launch**Setting**: Min app version with action Warn |
| MinAppVersionWipe | "0.0" = no minimum OS versionanything else = minimum OS version | **Section**: Conditional launch**Setting**: Min app version with action Wipe data |
| MinOsVersion | "0.0" = no minimum OS versionanything else = minimum OS version | **Section**: Conditional launch**Setting**: Min OS version with action Block access |
| MinOsVersionWarning | "0.0" = no minimum OS versionanything else = minimum OS version | **Section**: Conditional launch**Setting**: Min OS version with action Warn |
| MinOsVersionWipe | "0.0" = no minimum OS versionanything else = minimum OS version | **Section**: Conditional launch**Setting**: Min OS version with action Wipe data |
| MinSDKVersion | "0.0" = no minimum SDK versionanything else = minimum OS version | **Section**: Conditional launch**Setting**: Min SDK version with action Block access |
| MinSDKVersionWipe | "0.0" = no minimum SDK versionanything else = minimum OS version | **Section**: Conditional launch**Setting**: Min SDK version with action Block access |
| MinimumRequiredDeviceThreatProtectionLevel | 0 = Not configured1 = Secured2 = Low3 = Medium4 = High | **Section**: Conditional launch**Setting**: Max allowed device threat level |
| MobileThreatDefenseRemediationAction | 0 = Block access1 = Wipe data | **Section**: Access requirements**Setting**: Max allowed device threat level action) |
| NonBioPassTimeOutRequired | 0 = Not required1 = Require | **Section**: Access requirements**Setting**: Override Touch ID with PIN after timeout |
| NonBioPassTimeOut | x minutes | **Section**: Access requirements**Setting**: Override Touch ID with PIN after timeout &gt; Timeout (minutes of inactivity) |
| NotificationRestriction | 0 = Allow1 = Block Org Data2 = Block | **Section**: Data protection**Setting**: Org data notifications |
| OpenDataFromManagedLocations | A value that represents the number of managed storage locations to which the app can save data. 1 = OneDrive2 = SharePoint3 = OneDrive & SharePoint4 = Camera5 = OneDrive & Camera6 = SharePoint & Camera7 = OneDrive, SharePoint & Camera8 = Local Storage9 = Local Storage & OneDrive10 = Local Storage & SharePoint11 = Local Storage, OneDrive & SharePoint12 = Local Storage & Camera13 = Local Storage, OneDrive & Camera14 = Local Storage, SharePoint & Camera15 = Local Storage, OneDrive, SharePoint & Camera16 = Photo Library17 = Photo Library & OneDrive18 = Photo Library & SharePoint19 = Photo Library, OneDrive & SharePoint20 = Photo Library & Camera21 = Photo Library, OneDrive & Camera22 = Photo Library, SharePoint & Camera23 = Photo Library, OneDrive, SharePoint & Camera24 = Photo Library & Local Storage25 = Photo Library, Local Storage & OneDrive26 = Photo Library, Local Storage & SharePoint27 = Photo Library, Local Storage, OneDrive & SharePoint28 = Photo Library, Local Storage & Camera29 = Photo Library, Local Storage, OneDrive & Camera30 = Photo Library, Local Storage, SharePoint & Camera31 = Photo Library, Local Storage, OneDrive, SharePoint & Camera | **Section**: Data protection**Setting**: Allow users to open data from selected services |
| OpenDataIntoOrgDocumentsBlocked | 0 = Allow1 = Block | **Section**: Data protection**Setting**: Open data into Org documents |
| OfflineWipeInterval | x days | **Note**: No administrative control for this setting. |
| PINCharacterType | 0 = Passcode1 = Numeric | **Section**: Access requirements**Setting**: Pin type |
| PINEnabled | 0 = Not required1 = Require | **Section**: Access requirements**Setting**: PIN for access |
| PINExpiryDays | x characters | **Section**: Access requirements**Setting**: PIN reset after number of days &gt; Number of days |
| PINMinLength | x characters | **Section**: Access requirements**Setting**: Select minimum PIN length |
| PINNumRetry | x attempts | **Section**: Conditional launch**Setting**: Max PIN attempts |
| PrintingBlocked | 0 = Allow1 = Block | **Section**: Data protection**Setting**: Printing org data |
| ProtectAllIncomingUnknownSourceData | N/A | **Note**: Not actively used by the Intune service. |
| ProtectManagedOpenInData | 0 = False1 = True | **Section**: Data protection**Setting**: Send org data to other apps is set to Policy Managed apps with Open-In/Share filtering when true. Note that this can also be set to 1 when Policy Managed Apps with OS sharing is enabled. |
| ProtocolExclusions | A list of app URL protocol schemes that allow data to be open in the corresponding unmanaged apps data | **Section**: Data protection**Setting**: Select apps to exempt |
| RequireFileEncryption | N/A | **Note**: Not actively used by the Intune service. |
| ScreenCaptureConfigurationState | 0 = Allow1 = Block | **Section**: Data protection**Setting**: Screen capture |
| SimplePINAllowed | 0 = Block1 = Allow | **Section**: Access requirements**Setting**: Simple PIN |
| SpecificDialerProtocol | URL protocol scheme for the specific dialer that is used for phone calls from managed apps | **Section**: Data protection**Setting**: Dialer App URL Scheme |
| ThirdPartyKeyboardsBlocked | 0 = Allow1 = Block | **Section**: Data protection**Setting**: Third party keyboards |
| TouchIDEnabled | 0 = Block1 = Allow | **Section**: Access requirements**Setting**: Touch ID instead of PIN for access (iOS 8+/iPadOS) |
| UniversalLinkExclusions | A list of universal links that allow data to be open in the corresponding unmanaged apps | **Section**: Data protection**Setting**: Select universal links to exempt |
| UnmanagedBrowserProtocol | URL protocol scheme for the unmanaged browser that is used to view managed web links | **Section**: Data protection**Setting**: Restrict web content transfer with other apps |
| WritingToolsConfigurationState | 0 = Allow1 = Block | **Section**: Data protection**Setting**: Writing tools |

## Android App protection policy settings

| Name | Value details | Setting in Microsoft Intune App Protection Policy |
| --- | --- | --- |
| AccessRecheckOfflineTimeout​ | x minutes | **Section**: Conditional launch**Setting**: Offline grace period with action Block access (minutes) |
| AccessRecheckOnlineTimeout​ | x minutes | **Section**: Access requirements**Setting**: Recheck the Access requirements after (minutes of inactivity) |
| AllowedAndroidManufacturersElseBlock | Empty if not set​, otherwise list of allowed manufacturers | **Section**: Conditional launch**Setting**: Device manufacturers with action Allow specified (Block non-specified) |
| AllowedAndroidManufacturersElseWipe | Empty if not set​, otherwise list of allowed manufacturers | **Section**: Conditional launch**Setting**: Device manufacturers with action Allow specified (Wipe non-specified) |
| AllowedAndroidModelsElseBlock | Empty if not set​, otherwise list of allowed models | No administrative control for this setting. |
| AllowedAndroidModelsElseWipe | Empty if not set​, otherwise list of allowed models | No administrative control for this setting. |
| AndroidSafetyNetDeviceAttestationEnforcement | NOT\_REQUIRED = not setBASIC\_INTEGRITY = Basic IntegrityBASIC\_INTEGRITY\_AND\_DEVICE\_CERTIFICATION = Basic Integrity and certified devices | **Section**: Conditional launch**Setting**: Play integrity verdict |
| AndroidSafetyNetDeviceAttestationFailedAction | BLOCK = Block accessWARN = WarnWIPE\_DATA = Wipe Data | **Section**: Conditional launch**Setting**: Play integrity verdict |
| AndroidSafetyNetRequiredEvaluationType | NONE = not setHARDWARE\_BACKED = Check strong integrity | **Section**: Conditional launch**Setting**: Play Integrity verdict evaluation type |
| AndroidSafetyNetVerifyAppsEnforcementType | NOT\_REQUIRED = not setREQUIRE\_ENABLED = configured | **Section**: Conditional launch**Setting**: Require threat scan on apps |
| AndroidSafetyNetVerifyAppsFailedAction | BLOCK = Block accessWARN = Warn | **Section**: Conditional launch**Setting**: Require threat scan on apps |
| AppActionIfSamsungKnoxAttestationRequired | NONE = not setBLOCK = Block accessWIPE = Wipe dataWARN = Warn | **Section**: Conditional launch**Setting**: Samsung Knox device attestation |
| AppActionIfDevicePasscodeComplexityLessThanHigh | NONE = not setBLOCK = Block accessWIPE = Wipe dataWARN = Warn | **Section**: Access requirements**Setting**: Require device lock |
| AppActionIfDevicePasscodeComplexityLessThanLow | NONE = not setBLOCK = Block accessWIPE = Wipe dataWARN = Warn | **Section**: Access requirements**Setting**: Require device lock |
| AppActionIfDevicePasscodeComplexityLessThanMedium | NONE = not setBLOCK = Block accessWIPE = Wipe dataWARN = Warn | **Section**: Access requirements**Setting**: Require device lock |
| AppActionIfAccountIsClockedOut | NONE = not setWARN = WarnBLOCK = Block access | **Section**: Conditional launch**Setting**: Non-working time |
| AppActionIfUnableToAuthenticateUser | NONE = not setBLOCK = Block accessWIPE\_DATA = Wipe apps | **Section**: Conditional launch**Setting**: Disabled account |
| AppPinDisabled | true = Not requiredfalse = Require | **Section**: Access requirements**Setting**: App PIN when device PIN is set |
| ApprovedKeyboards | List of approved keyboard bundle IDs required | **Section**: Data protection**Setting**: Select keyboards to approve |
| AppSharingFromLevel | BLOCKED = NoneMANAGED = Policy Managed appsUNRESTRICTED = All apps | **Section**: Data protection**Setting**: Receive data from other apps |
| AppSharingToLevel | BLOCKED = NoneMANAGED = Policy Managed appsUNRESTRICTED = All app | **Section**: Data protection**Setting**: Send org data to other apps |
| AuthenticationEnabled | false = Not requiredtrue = Require | **Section**: Access requirements**Setting**: Work or school account credentials for access |
| BiometricIdEnabled | 0 = Block1 = Allow | **Section**: Access requirements**Setting**: Biometrics instead of PIN for access |
| BlockAfterCompanyPortalUpdateDeferralInDays | x days | **Section**: Conditional launch**Setting**: Max Company Portal version age (days) |
| BlockClockSttausWithGracePeriod | N/A | **Note**: Not actively used by the Intune service. |
| BlockScreenCapture | false = Allowtrue = Block | **Section**: Data protection**Setting**: Screen capture and Google Assistant |
| ClipboardCharacterLengthException | x characters | **Section**: Data protection**Setting**: Cut and copy character limit for any app |
| ClipboardSharingLevel | BLOCKED = BlockedMANAGED = Policy managed appsMANAGED\_PASTE\_IN = Policy managed apps with paste inUNMANAGED = Any app | **Section**: Data protection**Setting**: Restrict cut, copy, and paste between other apps |
| ConditionalEncryptionEnabled | false = Requiretrue = Not required | **Section**: Data protection**Setting**: Encrypt org data on enrolled devices |
| ConnectToVPNOnLaunch | false = Enabletrue = Disable | **Section**: Data protection**Setting**: Start Microsoft Tunnel connection on app-launch |
| ContactSyncDisabled | false = Allowtrue = Block | **Section**: Data protection**Setting**: Sync app with native contacts app |
| DataBackupDisabled | false = Allowtrue = Block | **Section**: Data protection**Setting**: Prevent backups |
| DeviceComplianceEnabled | false = Falsetrue = True | **Section**: Conditional launch**Setting**: Jailbroken/rooted devices |
| DeviceComplianceFailureAction | BLOCK = Block accessWIPE\_DATA = Wipe data | **Section**: Conditional launch**Setting**: Jailbroken/rooted devices |
| DialerRestrictionLevel | 0 = None, do not transfer this data between apps1 = A specific dialer app2 = Any policy-managed dialer app3 = Any dialer app | **Section**: Data protection**Setting**: Transfer telecommunication data to |
| DictationBlocked | false = Allowtrue = Block | No administrative control for this setting. |
| FileEncryptionKeyLength | 128256 | No administrative control for this setting. |
| FileSharingSaveAsDisabled | false = Allowtrue = Block | **Section**: Data protection**Setting**: Save copies of org data |
| IntuneMAMPolicyVersion | version number | N/A |
| isManaged | truefalse | N/A |
| KeyboardsRestricted | true = Requiredfalse = Not required | **Section**: Data protection**Setting**: Approved keyboards |
| ManagedBrowserRequired | true = Microsoft Edge or Unmanaged browserfalse = Any app | **Section**: Data protection**Setting**: Restrict web content transfer with other apps. |
| ManagedLocations | A value that represents the number of managed storage locations to which the app can save data, separated by a semi-colon.ONEDRIVE\_FOR\_BUSINESSSHAREPOINTLOCAL | **Section**: Data protection**Setting**: Allow user to save copies to selected services |
| MaxPinRetryExceededAction | RESET\_PIN = Reset PINWIPE\_DATA = Wipe data | **Section**: Conditional launch**Setting**: Max PIN attempts |
| MaxOsVersion | "0.0" = no maximum OS versionanything else = maximum OS version | **Section**: Conditional launch**Setting**: Max OS version with action Block access |
| MaxOsVersionWarning | "0.0" = no maximum OS versionanything else = maximum OS version | **Section**: Conditional launch**Setting**: Max OS version with action Warn |
| MaxOsVersionWipe | "0.0" = no maximum OS versionanything else = maximum OS version | **Section**: Conditional launch**Setting**: Max OS version with action Wipe data |
| MessagingRedirectAppDisplayName | Messaging app name | **Section**: Data protection**Setting**: Messaging App Name |
| MessagingRedirectAppPackageId | Messaging app package ID | **Section**: Data protection**Setting**: Messaging App Package ID |
| MinAppVersion | "0.0" = no minimum app versionanything else = minimum app version | **Section**: Conditional launch**Setting**: Min app version with action Block access |
| MinAppVersionWarning | "0.0" = no minimum app version.anything else = minimum app version | **Section**: Conditional launch**Setting**: Min app version with action Warn |
| MinAppVersionWipe | "0.0" = no minimum OS versionanything else = minimum OS version | **Section**: Conditional launch**Setting**: Min app version with action Wipe data |
| MinOsVersion | "0.0" = no minimum OS versionanything else = minimum OS version | **Section**: Conditional launch**Setting**: Min OS version with action Block access |
| MinOsVersionWarning | "0.0" = no minimum OS versionanything else = minimum OS version | **Section**: Conditional launch**Setting**: Min OS version with action Warn |
| MinOsVersionWipe | "0.0" = no minimum OS versionanything else = minimum OS version | **Section**: Conditional launch**Setting**: Min OS version with action Wipe data |
| MinPatchVersion | "0000-00-00" = no minimum Patch versionanything else = minimum Patch version | **Section**: Conditional launch**Setting**: Min Patch version with action Block access |
| MinPatchVersionWarning | "0000-00-00" = no minimum Patch versionanything else = minimum Patch version | **Section**: Conditional launch**Setting**: Min Patch version with action Warn |
| MinPatchVersionWipe | "0000-00-00" = no minimum Patch versionanything else = minimum Patch version | **Section**: Conditional launch**Setting**: Min Patch version with action Wipe data |
| MinimumRequiredCompanyPortalVersion | "0.0" = no minimum Company Portal versionanything else = minimum Company Portal version | **Section**: Conditional launch**Setting**: Min Company Portal version with action Block access |
| MinimumRequiredDeviceThreatProtectionLevel | NOT\_SET = not defined in the policySECURED = SecuredLOW = LowMEDIUM = MediumHIGH = High | **Section**: Conditional launch**Setting**: Max allowed device threat level |
| MinimumWarningCompanyPortalVersion | "0.0" = no minimum Company Portal versionanything else = minimum Company Portal version | **Section**: Conditional launch**Setting**: Min Company Portal version with action Warn |
| MinimumWipeCompanyPortalVersion | "0.0" = no minimum Company Portal versionanything else = minimum Company Portal version | **Section**: Conditional launch**Setting**: Min Company Portal version with action Wipe data |
| MobileThreatDefenseRemediationAction | BLOCK = Block AccessWIPE\_DATA = Wipe data | **Section**: Conditional launch**Setting**: Max allowed device threat level |
| NonBioPassRequiredOnLaunch | N/A | **Note**: Not actively used by the Intune service. |
| NonBioPassTimeOut | x minutes | **Section**: Access requirements**Setting**: Override fingerprint with PIN after timeout &gt; Timeout (minutes of inactivity) |
| NonBioPassTimeOutRequired | false = Not requiredtrue = Require | **Section**: Access requirements**Setting**: Override fingerprint with PIN after timeout |
| NotificationRestriction | UNRESTRICTED = AllowBLOCK\_ORG\_DATA = Block Org DataBLOCK = Block | **Section**: Data protection**Setting**: Org data notifications |
| OpenDataFromManagedLocations | A value that represents the number of managed storage locations to which the app can save data, separated by a semi-colon.ONEDRIVE\_FOR\_BUSINESSSHAREPOINTCAMERA | **Section**: Data protection**Setting**: Allow users to open data from selected services |
| OpenDataIntoOrgDocumentsBlocked | false = Allowtrue = Block | **Section**: Data protection**Setting**: Open data into Org documents |
| PINCharacterType | PASSCODE = PasscodeNUMERIC = Numeric | **Section**: Access requirements**Setting**: Pin type |
| PINEnabled | false = Not requiredtrue = Require | **Section**: Access requirements**Setting**: PIN for access |
| PINExpiryDays | x characters | **Section**: Access requirements**Setting**: PIN reset after number of days &gt; Number of days |
| PINMinLength | x characters | **Section**: Access requirements**Setting**: Select minimum PIN length |
| PINNumRetry | x attempts | **Section**: Conditional launch**Setting**: Max PIN attempts |
| PackageExclusions | Empty if no bundle IDs are configured, otherwise bundle IDs separated by a semi-colon | **Section**: Data protection**Setting**: Select apps to exempt |
| PinHistoryLength | x PIN values to maintain | **Section**: Access requirements**Setting**: Select number of previous PIN values to maintain |
| PolicyCount | number | N/A |
| PrintingBlocked | false = Allowtrue = Block | **Section**: Data protection**Setting**: Printing org data |
| RequireClass3Biometrics | false = Not requiredtrue = Require | **Section**: Access requirements**Setting**: Class 3 Biometrics (Android 9.0+) |
| ProtectedMessagingRedirectAppType | 0 = Any messaging app1 = Any policy-managed messaging app2 = A specific messaging app3 = None, do not transfer this data between apps | **Section**: Data protection**Setting**: Transfer messaging data to |
| RequireDeviceLock | true = Requiredfalse = Not required | **Section**: Conditional launch**Setting**: Require device lock |
| RequireDeviceLockEnforcementType | BLOCK = Block accessWIPE\_DATA = Wipe required | **Section**: Conditional launch**Setting**: Require device lock |
| RequireFileEncryption | false = Not requiredtrue = Require | **Section**: Data protection**Setting**: Encrypt org data |
| RequirePinAfterBiometricChange | false = Not requiredtrue = Require | **Section**: Access requirements**Setting**: Override Biometrics with PIN after biometric updates |
| SimplePINAllowed | false = Blocktrue = Allow | **Section**: Access requirements**Setting**: Simple PIN |
| SpecificDialerDisplayName | Dialer app name | **Section**: Data protection**Setting**: Dialer app name |
| SpecificDialerPackageID | Dialer app bundle ID | **Section**: Data protection**Setting**: Dialer App Package ID |
| TouchIDEnabled | false = Blocktrue = Allow | **Section**: Access requirements**Setting**: Fingerprint instead of PIN for access (Android 9.0+) |
| UnmanagedBrowserDisplayName | Unmanaged web browser display name | **Section**: Data protection**Setting**: Unmanaged Browser name |
| UnmanagedBrowserPackageID | Unmanaged web browser package ID | **Section**: Data protection**Setting**: Unmanaged Browser ID |
| UserStatusPollInterval | N/A | **Note**: Not actively used by the Intune service. |
| UserStatusTimeoutInSeconds | N/A | **Note**: Not actively used by the Intune service. |