---
layout: Conceptual
title: Set up web based device enrollment - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-web-based-ios
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
description: Set up web-based device enrollment to manage user-owned iOS/iPadOS devices in Microsoft Intune.
ms.date: 2024-09-23T00:00:00.0000000Z
ms.topic: install-set-up-deploy
locale: en-us
document_id: 0ea48985-41db-a0fb-7841-c948f34d3fb7
document_version_independent_id: 0ea48985-41db-a0fb-7841-c948f34d3fb7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/setup-web-based-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/setup-web-based-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/setup-web-based-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/5686b492-7c45-4088-8291-ecc0458747d3
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/838f4f15-80c1-4d49-b873-501fe4ed2d28
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
platformId: 89c08d17-5065-6b9b-6a9c-dc061858a370
---

# Set up web based device enrollment - Microsoft Intune | Microsoft Learn

**Applies to iOS/iPadOS**

Set up web-based device enrollment in Microsoft Intune for iOS/iPadOS personal devices. This is one of two *Apple device enrollment* methods supported in Microsoft Intune, with the other being [device enrollment with the Company Portal app](personal-device-options-ios#app-or-web-based-enrollment). Both methods give you access to a limited but appropriate set of device management settings and actions for bring-your-own-device (BYOD) scenarios, so you can protect work data without affecting the device user's personal data or apps.

Web-based device enrollment provides a faster and more user-friendly enrollment experience. The Company Portal app isn't required because employees and students do everything in Safari and in their device settings. Additionally, web-based device enrollment works with JIT registration. When it's enabled, Intune uses JIT registration with the Microsoft Authenticator app for registration of the device and single sign-on (SSO) to reduce the number of times users have to sign in during enrollment and when accessing work apps.

This article describes how to set up web based device enrollment in Microsoft Intune. You will:

- Set up JIT registration.
- Create an enrollment profile.
- Prepare employees and students for enrollment.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This enrollment method supports the following platforms:
> 
> - iOS/iPadOS 15 or later
> 
> 
> If you assign a web-based enrollment profile to device users running iOS/iPadOS 14.9 or earlier, Microsoft Intune will automatically enroll them via app-based device enrollment. App-based device enrollment requires the Company Portal app for iOS/iPadOS.

![](../../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> - [Set mobile device management (MDM) authority](../../fundamentals/setup-mdm-authority)
> - [Get Apple MDM Push certificate](create-mdm-push-certificate)
> 

## Best practices

Deploy the web app version of Intune Company Portal so that device users have quick access to device status, device actions, and compliance information. The web app appears on the home screen and functions as a link to the [Company Portal website](https://portal.manage.microsoft.com/). For more information about how to add a web app, see [Add web apps to Microsoft Intune](../../app-management/deployment/add-web). Without the web app, devices users can still access the Company Portal website, but they have to open the browser and enter the website link.

The Microsoft Authenticator app is required for work or school access. We recommend telling employees and students to install Microsoft Authenticator before they begin device enrollment.

## Step 1: Set up just in time registration

Create a device configuration, single sign-on app extension policy to enable just-in-time (JIT) registration. For steps, see [Set up JIT registration in Intune](setup-just-in-time-registration). Return to this article when you're done so you can continue to the next step.

## Step 2: Create enrollment profile

Create an enrollment profile for devices enrolling via web-based device enrollment. The enrollment profile triggers the device user's enrollment experience, and enables them to initiate enrollment in Safari.

1. In the Microsoft Intune admin center, go to **Devices** &gt; **Enrollment**.
2. Select the **Apple** tab.
3. Under **Enrollment Options**, choose **Enrollment types**.
4. Select **Create profile** &gt; **iOS/iPadOS**.
5. On the **Basics** page, enter a name and description for the profile so that you can distinguish it from other profiles in the admin center. Device users don't see these details.
6. Select **Next**.
7. On the **Settings** page, for **Enrollment type**, select **Web based device enrollment**.
8. Select **Next**.
9. On the **Assignments** page, assign the profile to all users or a group of users.
10. Select **Next**.
11. On the **Review + create** page, review your choices, and then select **Create** to finish creating the profile.

Return to **Enrollment types** to see a list of your enrollment profiles. Intune applies enrollment profiles in the order you prioritize them. If a conflict occurs because a user is assigned more than one profile, Intune applies the profile with the higher priority. Drag and drop the profiles in the list to reposition them and change the order in which they're applied.

## Step 3: Prepare employees for enrollment

When an employee attempts to sign in to a work app on their personal device, the app alerts them to the enrollment requirement and redirects them to the Company Portal website for enrollment.

Alternatively, you can provide employees and students with a URL that opens the Company Portal website. If you aren't utilizing Conditional Access, it's important to share the enrollment link with device users so that they know how to initiate enrollment. The link to share is:

`https://portal.manage.microsoft.com/enrollment/webenrollment/ios`

This section provides the high-level enrollment steps for device users. We recommend using this information in your organization's device onboarding documentation or for troubleshooting and support.

Important

Safari browser is the only supported browser for this type of enrollment, and is needed to download the management profile and complete enrollment. If a user's default browser is anything other than Safari, they will need to copy the enrollment link and paste it into a Safari browser to initiate enrollment. After they complete enrollment, users can return to their preferred browser.

1. Open Safari and go to https://portal.manage.microsoft.com/enrollment/webenrollment/ios. Sign in with your work or school account.
2. When prompted to, download the management profile. Wait in Safari while Company Portal downloads the management profile.
3. Go to your device settings app to view and install the management profile.
4. Wait until Microsoft Authenticator is installed on the device before signing in to a work or school app. The device won't be ready for work use until Authenticator is on the device, which can take a few minutes. To verify that Authenticator installed, open your device settings and go to **General** &gt; **VPN & Device Management** &gt; **Management Profile** &gt; **More Details**. Authenticator should be listed as the SSO extension.
5. Sign in to a work app, such as Microsoft Teams, with your work account.
6. Wait while the app identifies required setting updates. For example, you may be required to update your device's operating system before you can use the app. Check the app you're signed in to for pending action items. When you're done making changes, select **Recheck**.

After compliance checks are complete, users can access apps configured with the SSO app extension policy for the rest of their session without needing to sign in again.

### Removing device from management

The volume and cryptographic keys created to manage the work data on the device are erased when the device unenrolls from Intune.

### Onboarding documentation resources

For end user help and how-to guides, see [Microsoft Intune user help docs](../../user-help/). Feel free to use the articles in that doc set as templates for your organization's onboarding resources.

For more details about Apple Device Enrollment features and functionality, see [Device Enrollment and MDM](https://support.apple.com/guide/deployment/device-enrollment-and-mdm-depd1c27dfe6/web) on the Apple support website.

### Troubleshooting

For information about how to troubleshoot device enrollment issues in Microsoft Intune, see [Troubleshoot device enrollment](/en-us/troubleshoot/mem/intune/troubleshoot-device-enrollment-in-intune#device-cap-reached).