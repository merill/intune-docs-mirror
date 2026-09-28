---
layout: Conceptual
title: Overview of Apple device enrollment in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/personal-device-options-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: rishitasarin
ms.subservice: enrollment
description: Utilize Apple device enrollment to enroll and manage user-owned iOS/iPadOS devices in Microsoft Intune.
ms.date: 2025-12-08T00:00:00.0000000Z
ms.topic: concept-article
locale: en-us
document_id: d0a17172-612b-54e8-a5a4-bc8220a02308
document_version_independent_id: d0a17172-612b-54e8-a5a4-bc8220a02308
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/personal-device-options-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/personal-device-options-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/personal-device-options-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 6780dbb6-849f-4cde-a434-bf7c5d5900ae
---

# Overview of Apple device enrollment in Microsoft Intune - Microsoft Intune | Microsoft Learn

*Apple device enrollment* lets employees and students enroll new and existing personal devices for work or school. It unlocks essential iOS/iPadOS management capabilities for you in the Microsoft Intune admin center, while also protecting the personal data of employees and students. This article provides an overview of the Apple device enrollment features and functionality supported by Microsoft Intune.

## App or web based enrollment

Device enrollment supports an app based enrollment experience and web based enrollment experience. In the admin center, your device enrollment options are:

- **Device enrollment with Company Portal**
- **Web based device enrollment**

Create an enrollment policy in the admin center to select and configure enrollment types. Go to **Devices** &gt; **By platform** &gt; **iOS/iPadOS** &gt; **Device onboarding** &gt; **Enrollment** and select **Enrollment types**.

Web-based enrollment utilizes just in time (JIT) registration with the Apple single sign-on (SSO) extension to facilitate Microsoft Entra registration within the employee's work apps and reduce the number of times they have to authenticate. We recommend web enrollment using JIT registration with SSO as the most secure enrollment method for device attestation. We also recommend enabling web-based enrollment for devices because it doesn't require employees and students to install the Company Portal app. Post-enrollment functionality remains the same as with app-based enrollment. To enable JIT registration in enrollments, [create a device configuration profile with an SSO app extension policy](setup-web-based-ios#step-1-set-up-just-in-time-registration).

The following table provides details about app and web-based enrollment.

| Specification | App-based enrollment | Web-based enrollment |
| --- | --- | --- |
| Supported version | iOS/iPadOS 14 and later | iOS/iPadOS 15 and later |
| BYOD and personal devices | ✔️ | ✔️ |
| Device associated with single user | ✔️ | ✔️ |
| Device reset required | ❌ | ❌ |
| Enrollment initiated by device user | ✔️ | ✔️ |
| Supervision | ❌ | ❌ |
| Just-in-time registration | ✔️ | ✔️ |
| Required apps | Intune Company Portal app for iOS  Microsoft Authenticator | Microsoft Authenticator |
| Enrollment location | App-based enrollment takes place in the Company Portal app, Safari, and device settings app. | Web-based enrollment takes place in Safari and the device settings app. |

## Supported settings

Microsoft Intune supports a subset of device management options for devices enrolled via Apple device enrollment. If a pre-existing configuration profile is applied to a device, only the settings supported by Apple device enrollment take effect.

## User experience

Employees and students can access management options for their personal devices in the Intune Company Portal app or on the Company Portal website. Supported actions include:

- Rename
- Remove
- Remote lock
- Check status

Note

The *rename* action that's available to device users changes the display name in Company Portal. It doesn't rename the device in the Microsoft Intune admin center.

For more information about how employees and students can access these actions in the web version, see [Using the Intune Company Portal website](../../user-help/company-portal/website).

## Certificates

This enrollment type supports the Automated Certificate Management Environment (ACME) protocol. When new devices enroll, the management profile from Intune receives an ACME certificate. The ACME protocol provides better protection than the SCEP protocol against unauthorized certificate issuance through robust validation mechanisms and automated processes, which helps reduce errors in certificate management.

Devices that are already enrolled do not get an ACME certificate unless they re-enroll into Microsoft Intune. Acme is supported on devices running:

- iOS 16.0 or later
- iPadOS 16.1 or later

This capability is also supported in [GCC High tenants](../../fundamentals/government-service).

## Known issues and limitations

Intune enrollment with Apple device enrollment has the following known issues and limitations.

- Due to Apple restrictions, device users going through web based device enrollment must download the management profile in Safari.
- Just like Company Portal enrollment, once the management profile downloads, users have a limited amount of time to go to the Settings app and install the profile. If they wait too long, they must download the management profile again to continue.
- Device users may be unable to access work apps if they try signing in on their newly enrolled device while Microsoft Authenticator is still trying to deploy. Users should wait a few minutes while Authenticator catches up with the Intune service, and then try to sign in to their work app again.
- Web-based device enrollment can be used without JIT registration. We recommend using the web version of Company Portal instead of Company Portal for iOS to deploy apps to the device. If you are planning to use the Company Portal app for app deployment, MS Authenticator and the SSO extension policy must be sent to the device post web enrollment.
- There is a known issue with web-based enrollment and JIT registration that prevents the Company Portal app from recognizing enrolled devices. When a user tries to sign in to Company Portal for iOS on a device that doesn't have the SSO extension policy, Company Portal is unable to determine that the device has been enrolled. We are actively working to resolve this issue. To avoid this issue, we recommend deploying the SSO extension policy to enrolling devices. Or, as a temporary workaround, you can deploy a web clip for the web version of Company Portal, as described under [Best practices for web enrollment](setup-web-based-ios#best-practices).