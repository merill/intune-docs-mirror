---
layout: Conceptual
title: Set up account driven Apple User Enrollment - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-enrollment/apple/setup-account-driven-user
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
description: Set up account driven Apple User Enrollment for personal devices enrolling in Microsoft Intune.
ms.date: 2025-06-12T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 1f8b72f3-eaa9-89fb-d7af-4abc41da0e21
document_version_independent_id: 1f8b72f3-eaa9-89fb-d7af-4abc41da0e21
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-enrollment/apple/setup-account-driven-user.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-enrollment/apple/setup-account-driven-user
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-enrollment/apple/setup-account-driven-user.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7ebba99b-05c3-4387-8883-f7bbf6632cb8
- https://authoring-docs-microsoft.poolparty.biz/devrel/5686b492-7c45-4088-8291-ecc0458747d3
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/006ab567-b18c-4cf1-9a25-c24daa46ede1
- https://authoring-docs-microsoft.poolparty.biz/devrel/838f4f15-80c1-4d49-b873-501fe4ed2d28
platformId: 925725f0-f333-2712-abde-419226e46547
---

# Set up account driven Apple User Enrollment - Microsoft Intune | Microsoft Learn

Set up account driven Apple User Enrollment for personal devices enrolling in Microsoft Intune. Account driven user enrollment provides a faster and more user-friendly enrollment experience than [user enrollment with Company Portal](setup-user-company-portal). The device user initiates enrollment by signing in to their work account in the Settings app. After the user approves device management, the enrollment policy silently installs and Intune policies are applied. Intune uses just-in-time (JIT) registration and the Microsoft Authenticator app for authentication to reduce the number of times users have to sign in during enrollment and when accessing work apps.

This article describes how to set up account driven Apple User Enrollment in Microsoft Intune. You will:

- Set up JIT registration.
- Create an enrollment policy.
- Prepare employees and students for enrollment.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This enrollment method supports the following platforms:
> 
> - iOS/iPadOS 15 or later
> 
> 
> If you assign an account driven user enrollment profile to device users running iOS/iPadOS 14.9 or earlier, Microsoft Intune automatically enrolls them via user enrollment with Company Portal.

![](../../media/icons/16/tenant-administration.svg)**Tenant configuration requirements**

> 
> - [Set mobile device management (MDM) authority](../../fundamentals/setup-mdm-authority)
> - [Get Apple MDM Push certificate](create-mdm-push-certificate)
> - [Create Managed Apple IDs for device users](https://support.apple.com/en-us/HT210737) (Opens Apple Support website)
> 

You also need to set up service discovery so that Apple can reach the Intune service and retrieve enrollment information. To complete this prerequisite, set up and publish an HTTP well-known resource file on the same domain that employees sign in to. Apple retrieves the file via an HTTP GET request to `"https://contoso.com/.well-known/com.apple.remotemanagement"`, with your organization's domain in place of `contoso.com`. Publish the file on a domain that can handle HTTP GET requests.

Note

The well-known resource file must be saved without a file extension, such as .json, to function correctly.

Create the file in JSON format, with the content type set to `application/json`. We provide the following JSON samples that you can copy and paste into your file. Use the one that aligns with your environment. Replace the *YourAADTenantID* variable in the base URL with your organization's Microsoft Entra tenant ID.

Microsoft Intune environments:

```json
{"Servers":[{"Version":"mdm-byod", "BaseURL":"https://manage.microsoft.com/EnrollmentServer/PostReportDeviceInfoForUEV2?aadTenantId=YourAADTenantID"}]}
```

Microsoft Intune for US Government environments:

```json
{"Servers":[{"Version":"mdm-byod", "BaseURL":"https://manage.microsoft.us/EnrollmentServer/PostReportDeviceInfoForUEV2?aadTenantId=YourAADTenantID"}]}
```

Microsoft Intune operated by 21 Vianet in China environments:

```json
{"Servers":[{"Version":"mdm-byod", "BaseURL":"https://manage.microsoft.cn/EnrollmentServer/PostReportDeviceInfoForUEV2?aadTenantId=YourAADTenantID"}]}
```

The rest of the JSON sample is populated with all of the information you need, including:

- Version: The server version is `mdm-byod`.
- BaseURL: This URL is the location where the Intune service resides.

Tip

For more information about the technical requirements for service discovery, see [Implementing the simple authentication user-enrollment flow](https://developer.apple.com/documentation/devicemanagement/user_enrollment/onboarding_users_with_account_sign-in/implementing_the_simple_authentication_user-enrollment_flow) in the Apple Developer documentation.

If the service discovery isn't configured correctly, users receive the following error message:

- Title: Sign-in Failed
- Description: Your Apple ID does not support the expected services on this device. Contact your administrator to sign in.

In order to solve this issue, make sure that your webserver is hosting the service discovery file with the content type set to `application/json`. You can validate that by running the following commands:

```cmd
   curl -I "https://contoso.com/.well-known/com.apple.remotemanagement"
```

```cmd
   curl -I "https://contoso.com/.well-known/com.apple.remotemanagement?user-identifier=firstname.surname@contoso.com&model-family=iPhone"
```

Both of these commands should return `Content-Type: application/json`.

## Best practices

We recommend extra configurations to help improve the enrollment experience for device users. This section provides more information about each recommendation.

### Deploy Company Portal web app

Deploy the web app version of the Intune Company Portal website so that users have quick access to device status, device actions, and compliance information. The web app appears on the home screen and functions as a link to the [Company Portal website](https://portal.manage.microsoft.com/). Without the web app, devices users can still access the Company Portal website but have to open the browser and type the address into the search field. For more information about how to add a web app, see [Add web apps to Microsoft Intune](../../app-management/deployment/add-web).

### Enable federated authentication

Apple User Enrollment requires you to create and provide managed Apple IDs to enrolling users. If you enable federated authentication, which consists of linking Apple Business with Microsoft Entra ID, you don't have to create and provide unique Apple IDs to each user. Instead, a device user can sign in to their apps with the same credentials they use for their work account. For more information, see [Intro to federated authentication with Apple Business](https://support.apple.com/guide/apple-business-manager/intro-to-federated-authentication-axmb19317543/1/web/1) in the Apple Business User Guide.

## Step 1: Set up just in time registration and assign Microsoft Authenticator

Configure just-in-time registration and assign Microsoft Authenticator as a required app. For steps, see [Set up JIT registration in Intune](setup-just-in-time-registration). Return to this article when you're done so you can continue to the next step.

## Step 2: Create enrollment profile

Create an enrollment profile for devices enrolling via account driven user enrollment. The enrollment profile triggers the device user's enrollment experience, and enables them to initiate enrollment from the Settings app.

1. In the Microsoft Intune admin center, go to **Devices** &gt; **Enrollment**.
2. Select the **Apple** tab.
3. Under **Enrollment options**, choose **Enrollment types**.
4. Select **Create profile** &gt; **iOS/iPadOS**.
5. On the **Basics** page, enter a name and description for the profile so that you can distinguish it from other profiles in the admin center. Device users don't see these details.
6. Select **Next**.
7. On the **Settings** page, for **Enrollment type**, select how you want to enroll devices. You can choose the enrollment method or allow users to make their own choice. Their choice determines the enrollment process that Microsoft Intune carries out. It's also reflected in the device ownership attribute in Microsoft Intune. To learn more about the user's experience and what they see onscreen during enrollment, see [Set up personal iOS device for work or school](../../user-help/enrollment/enroll-ios).

    Your options:

    - **Account driven user enrollment**: Assigned users who initiate enrollment are enrolled via account driven user enrollment.
    - **Determine based on user choice**: Assigned users who initiate enrollment can select how they want to enroll their device. Their options:

        - **I own this device:** More settings appear with this selection. The user has the option to secure their entire device or only secure work-related apps and data.
        - **(Company) owns this device:** The device enrolls via Apple Device Enrollment. For more information about this enrollment method, see [Device Enrollment and MDM](https://support.apple.com/guide/deployment/device-enrollment-and-mdm-depd1c27dfe6/web) on the Apple Support website.
8. Select **Next**.
9. On the **Assignments** page, assign the profile to all users, or select specific groups. Device groups aren't supported in user enrollment scenarios because user enrollment requires user identities.
10. Select **Next**.
11. On the **Review + create** page, review your choices, and then select **Create** to finish creating the profile.

## Step 3: Prepare employees for enrollment

To initiate device enrollment on a personal device, the device owner must go to the Settings app and sign in with their work or school account. If they attempt to sign in to an app with their work or school account, the app alerts them to the enrollment requirement and tells them how to proceed.

This section describes the enrollment steps for device users. We recommend using this information in your organization's device onboarding documentation or for troubleshooting and support.

1. Open the **Settings** app on your device.
2. Select **General**.
3. Select **VPN & Device Management**.
4. Sign in with your work or school account, or with the Apple ID provided to you by your organization.
5. Select **Sign In to iCloud**.
6. Enter the password for the username that appears onscreen. Then select **Continue**.
7. Select **Allow Remote Management**.
8. Wait a few minutes while your device is configured and the management profile is installed.
9. To confirm your device is ready to use for work, go to **VPN & Device Management**. Confirm that your work account is listed under **MANAGED ACCOUNT**.
10. Microsoft Authenticator is required to access work apps. Wait a few minutes after enrollment for Authenticator to install on your device. An error message appears if you try to sign in to a work app without Authenticator.
11. You might receive more prompts asking for your approval to install work apps. Select **Install** to approve installation.

## Profile priority

Intune applies enrollment profiles in the order you prioritize them. To change the order in which they're applied:

1. Go back to **Enrollment types** to view your profiles.
2. Drag and drop the profiles in the list to reorder their priority.

If a conflict occurs because a user is assigned more than one profile, Intune applies the profile with the higher priority.

## Removing device from management

The volume and cryptographic keys created to manage the work data on the device are erased when the device unenrolls from Intune.