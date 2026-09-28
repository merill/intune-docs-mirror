---
layout: Conceptual
title: Intune Company Portal device password messages - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/compliance/ref-password-messages
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: This article lists the Company Portal device password messages for devices running Windows, Android, macOS, and iOS/iPadOS, with information about how to resolve them.
ms.date: 2024-10-08T00:00:00.0000000Z
ms.reviewer: anuragjain
locale: en-us
document_id: 1efcd21e-729a-26c5-5155-c68a3217f855
document_version_independent_id: 1efcd21e-729a-26c5-5155-c68a3217f855
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/compliance/ref-password-messages.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/compliance/ref-password-messages
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/compliance/ref-password-messages.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: cefd71cd-b688-826b-13ea-9b70c49a8e37
---

# Intune Company Portal device password messages - Microsoft Intune | Microsoft Learn

**Applies to**:

- Windows
- Android
- iOS/iPadOS
- macOS

This article lists the password-related messages you could receive from Intune Company Portal. These messages appear on devices during and after device enrollment, and enforce your organization's device password requirements. If you receive one or more of these messages, you may be blocked from accessing your org's network until you change your password settings. This article gives a brief description on how to fix your settings to meet each requirement. For more specific information about your organization's policies, contact your IT support person. Sign in to the [Company Portal website](https://go.microsoft.com/fwlink/?linkid=2010980) or app to find your organization's helpdesk information.

Messages in this article are organized by operating system.

## Windows password messages

These password-related messages are sent to devices running Windows.

| Message | How to fix |
| --- | --- |
| Password is required. | Set a password. Your organization requires that you enter a password to unlock your device. |
| Password is too simple. | Make sure that your password doesn't contain sequential or repeating numbers, such as 1234 or 1111. |
| Password is too short. | Update or set a password with more characters. Your organization requires that your password is a certain length. The minimum length they can require is 4 characters, and the maximum is 16. |
| Password must only contain numbers. | Set a password that only contains numbers. |
| Password must only contain alphanumeric characters. | Set a password that contains a mix of numbers and letters. |
| Password must contain complex characters. | Add complex characters such as numbers, capital letters, and symbols like `$`, `%`, and `#`. Your organization requires a mix of letters, numbers, and nonalphanumeric characters to make it harder for others to guess the password. |
| Password has expired. | Set a new password. Your organization requires you to change your password from time-to-time to ensure your device stays secure. |
| Your password was used too recently. | Create a brand new password. Your organization requires a certain amount of time to pass before you can reuse a password. |

## iOS passcode messages

These password-related messages are sent to iOS/iPadOS devices.

| Message | How to fix |
| --- | --- |
| Passcode is required. | Set a passcode. Your organization requires that you enter a passcode to unlock your device. |
| Passcode is too simple. | Make sure that your passcode doesn't contain sequential or repeating numbers, such as 1234 or 1111. |
| Passcode is too short. | Update or set a passcode with more characters. Your organization requires that your passcode is a certain length. The minimum length they can require is 4 characters, and the maximum is 14. When you change your passcode, you might see a prompt from Apple telling you to enter 6 or more characters; this message is only an Apple system recommendation. If your organization only requires a passcode that's 4 or 5 characters, you don't have to enter a 6-digit passcode. |
| Passcode must only contain numbers. | Set a passcode that only contains numbers. |
| Passcode must only contain alphanumeric characters. | Set a passcode that contains a mix of numbers and letters. |
| Passcode must contain nonalphanumeric characters. | Add special characters such as `&`, `!`, `$`, `%`, and `#`. Your organization requires a mix of letters, numbers, and nonalphanumeric characters to make it harder for others to guess the passcode. |
| Passcode has expired. | Set a new password. Your organization requires you to change your password from time-to-time to keep your device secure. |
| Your passcode was used too recently. | Create a brand new passcode. Your organization requires a certain amount of time to pass before you can reuse a passcode. |
| Touch ID or Face ID authentication required. | Set up Touch ID or Face ID. Your organization requires you to authenticate with one of these methods before using autofill for passwords or credit card information. |

## macOS password messages

These password-related messages are sent to Mac devices.

| Message | How to fix |
| --- | --- |
| Password is required. | Set a password. Your organization requires that you enter a password to unlock your device. |
| Password is too simple. | Make sure that your password doesn't contain sequential or repeating numbers, such as 1234 or 1111. |
| Password is too short. | Update or set a password with more characters. Your organization requires that your password is a certain length. |
| Password must only contain numbers. | Set a password that only contains numbers. |
| Password must only contain alphanumeric characters. | Set a password that contains a mix of numbers and letters. |
| Password must contain non-alphanumeric characters. | Add special characters such as `&`, `!`, `$`, `%`, and `#`. Your organization requires a mix of letters, numbers, and nonalphanumeric characters to make it harder for others to guess the password. |
| Password has expired. | Set a new password. Your organization requires you to change your password from time-to-time to keep your device secure. |
| Your password was used too recently. | Create a brand new password. Your organization requires a certain amount of time to pass before you can reuse a password. |

## Android password messages

These password-related messages are sent to Android devices.

### Android work profile

| Message | How to fix |
| --- | --- |
| Set a work profile password. | Create a work profile password or pattern. Your organization requires that you enter a password to unlock your work profile. |
| Set a stronger work profile password. | Create a work profile PIN or password with at least four characters and no repeating (4444) or ordered (1234, 4321, 2468) sequences. |
| Set a more complex work profile password. | Create a work profile PIN or password that's at least eight digits long with no repeating or ordered sequences, or create an alphabetic or alphanumeric password with at least six characters. |
| Set a longer work profile password. | Update or set a password with more characters. Your organization requires that your password is a certain length. |
| Work profile password requires numbers. | Set a password or PIN that contains numbers. |
| Work profile password can't have repeating numbers. | Make sure that your password or PIN doesn't contain sequential or repeating numbers, such as 1234 or 1111. |
| Work profile password requires a letter. | Set a password that contains letters from the alphabet. |
| Work profile password must have letters and numbers. | Set a password that contains a mix of numbers and letters. |
| Work profile password must include symbols. | Set a password that contains a mix of letters, numbers, and special characters such as `&`, `!`, `$`, `%`, and `#`. |
| Work profile password must use biometrics. | Set up your work profile to use biometric authentication, such as fingerprint or facial recognition. |
| Work profile password expired. | Set a new password. Your organization requires you to change your password after a certain number of days. |
| Work profile password was recently used. | Create a brand new password. Your organization requires a certain amount of time to pass before you can reuse a password. |

### Android (no work profile)

| Message | How to fix |
| --- | --- |
| Password is required. | Set a password or PIN. Your organization requires that you enter a password to unlock your device. |
| Password is too simple. | Make sure that your password or PIN doesn't contain sequential or repeating numbers, such as 1234 or 1111. |
| Password is too short. | Update or set a password with more characters. Your organization requires a longer device password. |
| Password must contain numbers. | Set a password or PIN that contains numbers. |
| Password must contain letters. | Set a password that contains letters from the alphabet. |
| Password must contain alphanumeric characters. | Set a password that contains a mix of numbers and letters. |
| Password must contain alphanumeric characters and symbols. | Set a password that contains a mix of letters, numbers, and special characters such as `&`, `!`, `$`, `%`, and `#`. |
| Password must use biometric technology. | Set up your device to use biometric authentication, such as fingerprint or facial recognition. |
| Password has expired. | Set a new password. Your organization requires you to change your password from time-to-time to keep your device secure. |
| Your password was used too recently. | Create a brand new password. Your organization requires a certain amount of time to pass before you can reuse a password. |