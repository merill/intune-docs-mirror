---
layout: Conceptual
title: Access requirements policy mapping from Basic Mobility and Security to Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/ref-policy-map-access-requirements
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: A detailed list of the policy map between Basic Mobility and Security access requirements and Intune.
ms.date: 2025-12-03T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: dagerrit
locale: en-us
document_id: 88d15dd8-1877-9f03-8853-18a31607e0bc
document_version_independent_id: 88d15dd8-1877-9f03-8853-18a31607e0bc
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/ref-policy-map-access-requirements.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/ref-policy-map-access-requirements
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/ref-policy-map-access-requirements.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 2b707267-aa4e-36e4-5f37-a0338b935d2a
---

# Access requirements policy mapping from Basic Mobility and Security to Intune - Microsoft Intune | Microsoft Learn

This article provides mapping details between Basic Mobility and Security to Intune. Specifically, this page maps the Microsoft Purview compliance portal Access Requirement policies to the equivalent policies in Microsoft Intune. Intune offers more policy flexibility. So, each Office policy translates into multiple Intune and Microsoft Entra policies to achieve the same result.

To see these settings in the Microsoft Purview compliance portal, sign in to the [Purview compliance portal](https://protection.office.com/devicev2). Then, go to the **Device security policies** list, select your policy name &gt; **Edit policy** &gt; **Access Requirements**.

## Before you begin

To configure the settings in an Intune policy, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). [Role-based access control (RBAC) with Microsoft Intune](role-based-access-control/overview) lists and describes the built-in roles that can create policies.

## If a device doesn't meet the requirements above, then...

This setting determines if you should use Intune compliance policies or configuration profiles for all the access requirement settings. Make sure to review the details for this setting first.

Note

Basic Mobility and Security never supported enforcing Conditional Access on Windows.

### Allow access and report violation (one-time enrollment is still enforced)

All Access Requirements are deployed in an Intune device configuration profile.

### Block access and report violation

All Access Requirements are deployed in an Intune compliance policy. The groups assigned are assigned to classic Conditional Access policies:

- [GraphAggregatorService] Device policy
- [Office 365 Exchange Online] Device policy
- [Outlook Service for Exchange] Device policy
- [Office 365 SharePoint Online] Device policy
- [Outlook Service for OneDrive] Device policy

## Require a password

Note

All password-related settings impact only local accounts on Windows. User accounts sourced from Microsoft Entra ID are not managed by these policies.

When **If a device doesn't meet the requirements above, then…** is set to **Block access and report violation**, use Intune compliance policies as shown below. If the setting is set to **Allow…**, use configuration profiles instead.

Three compliance policies:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_W &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Require a password to unlock mobile devices**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_i &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Require a password to unlock mobile devices**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Require a password to unlock mobile devices**

## Prevent simple passwords

For Android devices, this setting and multiple other Office settings are covered by one Android compliance setting. So this setting alone doesn't determine a specific Android compliance value.

When **If a device doesn't meet the requirements above, then…** is set to **Block access and report violation**, use Intune compliance policies as shown below. If the setting is set to **Allow…**, use configuration profiles instead.

Three compliance policies:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_W &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Simple passwords**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_i &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Simple passwords**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Required password type**.

    - If **Prevent simple passwords** is selected, choose **Numeric complex**, **Alphabetic**, **Alphanumeric**, or **Alphanumeric with symbols** (based on other Office settings).
    - If **Prevent simple passwords** isn't selected, choose **Numeric** or a higher type in the list (based on other Office settings).

## Require an alphanumeric password

For Android devices, this setting and multiple other Office settings are covered by one Android compliance setting. So this setting alone doesn't determine a specific Android compliance value.

When **If a device doesn't meet the requirements above, then…** is set to **Block access and report violation**, use Intune compliance policies as shown below. If the setting is set to **Allow…**, use configuration profiles instead.

Three compliance policies:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_W &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Required password type**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_i &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Required password type**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Required password type**.

    - If **Prevent simple passwords** is selected, choose **Numeric complex**, **Alphabetic**, **Alphanumeric**, or **Alphanumeric with symbols** (based on other Office settings).
    - If **Prevent simple passwords** isn't selected, choose **Numeric** or a higher type in the list (based on other Office settings).

## Password must include at least [1-4] character sets

When **If a device doesn't meet the requirements above, then…** is set to **Block access and report violation**, use Intune compliance policies as shown below. If the setting is set to **Allow…**, use configuration profiles instead.

Four compliance policies:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_W &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Password complexity**.

    | Office value | Intune value |
    | --- | --- |
    | 1 | **Require digits and lowercase letters**. The Windows compliance policy doesn't allow only one character set, so an Office setting of **1** translates to **Require digits and lowercase letters**. |
    | 2 | **Require digits and lowercase letters** |
    | 3 | **Require digits, lowercase and uppercase letters** |
    | 4 | **Require digits, lowercase, uppercase, and special characters** |
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_i &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Number of non-alphanumeric characters in password**.

    The iOS compliance policy doesn't enforce the number of character sets but only the number of non-alphanumeric characters that must be used. So Office values are translated to the same number of non-alphanumeric characters required.

    | Office value | Intune value |
    | --- | --- |
    | Disabled (0) | Not configured |
    | 1 | 1 |
    | 2 | 2 |
    | 3 | 3 |
    | 4 | 4 |
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Required password type**.

    Android doesn't support distinguishing lowercase and uppercase as different character sets, and so the Office value of 4 can't be enforced. Instead it translates to at least **Alphanumeric with symbols**.

    | Office value | Intune value |
    | --- | --- |
    | 1 | At least **Numeric** or **Numeric complex** (based on other Office settings) |
    | 2 | At least **Alphanumeric** |
    | 3 | At least **Alphanumeric with symbols** |
    | 4 | At least **Alphanumeric with symbols** |
- policy-name\_OfficeMDM &gt; **Access controls** &gt; **Grant** &gt; **Require device to be marked as compliant**

## Minimum password length

When **If a device doesn't meet the requirements above, then…** is set to **Block access and report violation**, use Intune compliance policies as shown below. If the setting is set to **Allow…**, use configuration profiles instead.

Three compliance policies:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_W &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Minimum password length**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_i &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Minimum password length**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Required password type** and **Minimum password length**.

    | Office value for**Require an alphanumeric password** | Intune value for**Required password type** |
    | --- | --- |
    | Selected | At least **Numeric** (based on other Office settings) |
    | Not selected | At least **Numeric** (based on other Office settings) |

## Number of sign-in failures before the device is wiped

Although this setting is listed under **Access requirements** in Basic Mobility and Security, access is still allowed. It's allowed even if this setting isn't enabled on the device yet, and this setting isn't a device compliance criterion.

When **If a device doesn't meet the requirements above, then…** is set to **Block access and report violation**, use Intune compliance policies as shown below. If the setting is set to **Allow…**, use configuration profiles instead.

Three configuration profiles:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Configuration** &gt; policy name\_O365\_W &gt; **Properties** &gt; **Compliance settings Edit** &gt; **Password** &gt; **Number of sign-in failures before wiping device**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration** &gt; policy name\_O365\_i &gt; **Properties** &gt; **Compliance settings Edit** &gt; **Password** &gt; **Number of sign-in failures before wiping device**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Configuration** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Compliance settings Edit** &gt; **Password** &gt; **Number of sign-in failures before wiping device**

## Lock devices if they are inactive for this many minutes

The Windows, iOS/iPadOS, and Android compliance policies don't offer the same granularity of values, so the Office setting range is mapped to fewer Intune values.

Three compliance policies:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_W &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Maximum minutes of inactivity before password is required**

    | Office value | Intune value |
    | --- | --- |
    | 1 through 4 | 1 minute |
    | 5 through 14 | 5 minutes |
    | 15 or more | 15 minutes |
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_i &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Maximum minutes of inactivity before password is required**

    | Office value | Intune value |
    | --- | --- |
    | 1 | 1 minute |
    | 2 | 2 minutes |
    | 3 | 3 minutes |
    | 4 | 4 minutes |
    | 5 through 9 | 5 minutes (maximum for iOS) |
    | 10 through 14 | 10 minutes (iPadOS only) |
    | 15 or more | 15 minutes (iPadOS only) |
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Required password type**.

    | Office value | Intune value |
    | --- | --- |
    | 1 through 4 | 1 minute |
    | 5 through 14 | 5 minutes |
    | 15 through 29 | 15 minutes |
    | 30 through 59 | 30 minutes |
    | 60 | 60 minutes |

## Password expiration

When **If a device doesn't meet the requirements above, then…** is set to **Block access and report violation**, use Intune compliance policies as shown below. If the setting is set to **Allow…**, use configuration profiles instead.

Three compliance policies:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_W &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Password expiration (days)**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_i &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Password expiration (days)**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Number of days until password expires**.

## Remember password history and prevent reuse

When **If a device doesn't meet the requirements above, then…** is set to **Block access and report violation**, use Intune compliance policies as shown below. If the setting is set to **Allow…**, use configuration profiles instead.

Three compliance policies:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_W &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Number of previous passwords to prevent reuse**
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_i &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Number of previous passwords to prevent reuse**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Number of previous passwords to prevent reuse** and **Required password type**

    | Office value for**Require an alphanumeric password** | Intune value for**Required password type** |
    | --- | --- |
    | Selected | At least **Numeric** (based on other Office settings) |
    | Not selected | At least **Numeric** (based on other Office settings) |

## Require data encryption on devices

This setting was never configurable for Windows or iOS/iPadOS in Basic Mobility and Security.

When **If a device doesn't meet the requirements above, then…** is set to **Block access and report violation**, use Intune compliance policies as shown below. If the setting is set to **Allow…**, use configuration profiles instead.

One compliance policy:

- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Compliance settings Edit** &gt; **System Security** &gt; **Encryption of data storage on device**

## Prevent jail broken or rooted devices from connecting

This setting was never configurable for Windows in Basic Mobility and Security.

For Android devices, Intune only supports this setting for Android device administrator devices.

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

When **If a device doesn't meet the requirements above, then…** is set to **Block access and report violation**, use Intune compliance policies as shown below. If the setting is set to **Allow…**, use configuration profiles instead.

Two compliance policies:

- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_i &gt; **Properties** &gt; **Compliance settings Edit** &gt; **Device Health** &gt; **Jailbroken devices**
- **Devices** &gt; **By platform** &gt; **Android** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_A &gt; **Properties** &gt; **Compliance settings Edit** &gt; **Device Health** &gt; **Rooted devices**

## Require managing email profile (required for selective wipe on iOS)

Requiring this setting was never supported for Windows or Android compliance in Basic Mobility and Security.

For Android, this setting was only supported on Samsung Knox devices in Basic Mobility and Security.

Intune requires more settings be configured when deploying email that weren't available in device security policies. For more information, see More settings required by Intune for email profiles.

When **If a device doesn't meet the requirements above, then…** is set to **Block access and report violation**, use Intune compliance policies as shown below. If the setting is set to **Allow…**, use configuration profiles instead.

Three configuration profiles and one compliance policy:

- **Devices** &gt; **By platform** &gt; **Windows** &gt; **Manage devices** &gt; **Configuration** &gt; policy name\_O365\_W\_Email &gt; **Properties** &gt; **Configuration settings Edit**

    | Setting | Value |
    | --- | --- |
    | Email server | outlook.office365.com |
    | Account name | Office 365 email |
    | Username attribute from Microsoft Entra ID | User Principal Name |
    | Email address attribute from Microsoft Entra ID | User Principal Name |
    | SSL | Enable |
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Configuration** &gt; policy name\_O365\_i\_Email &gt; **Properties** &gt; **Configuration settings Edit**

    | Setting | Value |
    | --- | --- |
    | Email server | outlook.office365.com |
    | Account name | Office 365 email |
    | Username attribute from Microsoft Entra ID | User Principal Name |
    | Email address attribute from Microsoft Entra ID | User Principal Name |
    | Authentication name | Username and password |
    | SSL | Enable |
- **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Manage devices** &gt; **Compliance** &gt; policy name\_O365\_i &gt; **Properties** &gt; **Compliance settings Edit** &gt; **Email** &gt; **Unable to set up email on the device** &gt; **Require**
- **Devices** &gt; **Android \*\* &gt; Configuration profiles &gt; policy name\_O365\_A\_Email &gt; Properties &gt; \*\* Configuration settings Edit**

    | Setting | Value |
    | --- | --- |
    | Email server | outlook.office365.com |
    | Account name | Office 365 email |
    | Username attribute from Microsoft Entra ID | User Principal Name |
    | Email address attribute from Microsoft Entra ID | User Principal Name |
    | Authentication name | Username and password |
    | SSL | Enable |

### More settings required by Intune for email profiles

The following settings aren't deployed by device security policies. But when deploying email profiles, Intune requires the settings have a value.

| Platform | Setting | Value in migration |
| --- | --- | --- |
| Android | Require S/mime | false |
| Android | Sync Contacts | true |
| Android | Sync Calendar | true |
| Android | Sync Tasks | true |
| Android | Sync Notes | false |
| iOS | Block moving messages to other email accounts | false |
| iOS | Block sending Email from third party addresses | false |
| iOS | Block syncing recently used email addresses | false |
| iOS | Require S/mime | false |
| Windows | Sync Contacts | true |
| Windows | Sync Calendar | true |
| Windows | Sync Tasks | true |

## Related article

- [Move from Basic Mobility and Security to Intune](migrate-from-other-mdm)