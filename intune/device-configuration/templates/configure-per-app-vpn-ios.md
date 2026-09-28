---
layout: Conceptual
title: Set up per-app VPN for iOS/iPadOS devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-per-app-vpn-ios
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
description: See the prerequisites, create a group for the virtual private network (VPN) users, add a SCEP certificate profile, configure a per-app VPN profile, and assign some apps to the VPN profile in Microsoft Intune on iOS/iPadOS devices. Also lists the steps to verify the VPN connection on the device.
ms.date: 2025-02-20T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: abalwan
locale: en-us
document_id: 6d6c7f9a-da12-8405-d2d9-9a38103ef56a
document_version_independent_id: 6d6c7f9a-da12-8405-d2d9-9a38103ef56a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-per-app-vpn-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-per-app-vpn-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-per-app-vpn-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: a3b04126-a947-fd77-aa06-2fe5595f56e4
---

# Set up per-app VPN for iOS/iPadOS devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

In Microsoft Intune, you can create and use Virtual Private Networks (VPNs) assigned to an app. This feature is called **per-app VPN**. You choose the managed apps that can use your VPN on devices managed by Intune. When you use per-app VPNs, end users automatically connect through the VPN, and get access to organizational resources, like documents.

This feature applies to:

- iOS 9 and newer
- iPadOS 13.0 and newer

Check your VPN provider's documentation to see if your VPN supports per-app VPN.

This article shows you how to create a per-app VPN profile, and assign this profile to your apps. Use these steps to create a seamless per-app VPN experience for your end users. For most VPNs that support per-app VPN, the user opens an app, and automatically connects to the VPN.

Some VPNs allow username and password authentication with per-app VPN. Meaning, users need to enter a username and password to connect to the VPN.

Important

- On iOS/iPadOS, per-app VPN isn't supported for IKEv2 VPN profiles.

## Per-app VPN with Microsoft Tunnel or Zscaler

Microsoft Tunnel and Zscaler Private Access (ZPA) integrate with Microsoft Entra ID for authentication. When using Tunnel or ZPA, you don't need the trusted certificate or SCEP or PKCS certificate profiles (described in this article).

If you have a per-app VPN profile set up for Zscaler, then opening one of the associated apps doesn't automatically connect to ZPA. Instead, the user needs to sign in to the Zscaler app. Then, remote access is limited to the associated apps.

## Prerequisites

- Your VPN vendor can have other requirements for per-app VPN, like specific hardware or licensing. Be sure to check with their documentation, and meet those prerequisites before setting up per-app VPN in Intune.
- Export the trusted root certificate `.cer` file from your VPN server. You add this file to the trusted certificate profile you create in Intune, described in this article.

    To export the file:

    1. On your VPN server, open the administration console.
    2. Confirm that your VPN server uses certificate-based authentication.
    3. Export the trusted root certificate file. It has a `.cer` extension.
    4. Add the name of the certificate authority (CA) that issued the certificate for authentication to the VPN server.

        If the CA presented by the device matches a CA in the Trusted CA list on the VPN server, then the VPN server successfully authenticates the device.

    To prove its identity, the VPN server presents the certificate to the device. The device must accept the certificate without prompting the user. To confirm the automatic approval of the certificate, you create a trusted certificate profile in Intune (in this article). The Intune trusted certificate profile must include the VPN server's root certificate (`.cer` file) issued by the Certification Authority (CA).
- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).

## Step 1 - Create a group for your VPN users

Create or choose an existing group in Microsoft Entra ID. This group:

- Must include the users or devices that will use per-app VPN.
- Will receive all the Intune policies you create in this article.

For the steps to create a new group, go to [Add groups to organize users and devices](../../fundamentals/tenant-administration/add-groups).

## Step 2 - Create a trusted certificate profile

Import the VPN server's root certificate issued by the CA into an Intune profile. This root certificate is the `.cer` file you exported in Prerequisites (in this article). The trusted certificate profile instructs the iOS/iPadOS device to automatically trust the CA that the VPN server presents.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **iOS/iPadOS**.
    - **Profile type**: Select **Trusted certificate**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **iOS/iPadOS trusted certificate profile for myApp**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, select the folder icon, and browse to your VPN certificate (`.cer` file) that you exported from your VPN administration console.
8. Select **Next**, and continue [creating the trusted certificate profile](../certificates/trusted-root-profiles). You can save the profile and assign it later.

    ![Create a trusted certificate profile for iOS/iPadOS devices in Microsoft Intune and Intune admin center.](media/configure-per-app-vpn-ios/vpn-per-app-create-trusted-cert.png)

When you're ready to assign the profile, assign this profile to the group you created in Step 1 - Create a group for your VPN users (in this article). When you assign the profile, the users or devices in the group receive the policy the next time they check-in with the Intune service.

## Step 3 - Create a SCEP or PKCS certificate profile

The trusted root certificate profile you created in step 2 allows the device to automatically trust the VPN Server.

In this next step, create the SCEP or PKCS certificate profile in Intune. The SCEP or PKCS certificate provides credentials from the iOS/iPadOS VPN client to the VPN server. The certificate allows the device to silently authenticate without prompting for a username and password.

To configure and assign the client authentication certificate in Intune, go to one of the following articles:

- [Configure infrastructure to support SCEP with Intune](../../fundamentals/certificates/scep-infrastructure)
- [Configure and manage PKCS certificates with Intune](../certificates/pkcs-profiles)

Be sure to configure the certificate for client authentication. You can set client authentication directly in SCEP certificate profiles (**Extended key usage** list &gt; **Client authentication**). For PKCS, set client authentication in the certificate template in the certificate authority (CA).

![Create a SCEP certificate profile in Microsoft Intune and Intune admin center. Include the subject name format, key usage, extended key usage, and more.](media/configure-per-app-vpn-ios/vpn-per-app-create-scep-cert.png)

When you're ready to assign the profile, assign this profile to the group you created in Step 1 - Create a group for your VPN users (in this article). When you assign the profile, the users or devices in the group receive the policy the next time they check-in with the Intune service.

## Step 4 - Create a per-app VPN profile

This VPN profile includes the SCEP or PKCS certificate that has the client credentials, the VPN connection information, and the per-app VPN flag that enables the per-app VPN used by the iOS/iPadOS application.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
2. Enter the following properties and select **Create**:

    - **Platform**: Select **iOS/iPadOS**.
    - **Profile type**: Select **VPN**.
3. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the custom profile. Name your profiles so you can easily identify them later. For example, a good profile name is **iOS/iPadOS per-app VPN profile for myApp**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
4. In **Configuration settings**, configure the following settings:

    - **Connection type**: Select your VPN client app.
    - **Base VPN**: Configure your settings. [iOS/iPadOS VPN settings](ref-vpn-settings-apple) describes all the settings. When using per-app VPN, be sure you configure the following properties as listed:

        - **Authentication method**: Select **Certificates**.
        - **Authentication certificate**: Select an existing SCEP or PKCS certificate &gt; **OK**.
        - **Split tunneling**: Select **Disable** to force all traffic to use the VPN tunnel when the VPN connection is active.

        ![Screenshot that shows a per-app VPN profile, IP address or FQDN, authentication method, and split tunneling in Microsoft Intune and Intune admin center.](media/configure-per-app-vpn-ios/vpn-per-app-create-vpn-profile.png)

        For information on the other settings, go to [iOS/iPadOS VPN settings](ref-vpn-settings-apple).
    - **Automatic VPN** &gt; **Type of automatic VPN** &gt; **Per-app VPN**

        ![Screenshot that shows the Automatic VPN set to per-app VPN on iOS/iPadOS devices in Microsoft Intune.](media/configure-per-app-vpn-ios/vpn-per-app-automatic.png)
5. Select **Next**, and continue [creating the VPN profile](configure-vpn#step-2---create-the-profile).

When you're ready to assign the profile, assign this profile to the group you created in Step 1 - Create a group for your VPN users (in this article). When you assign the profile, the users or devices in the group receive the policy the next time they check-in with the Intune service.

## Step 5 - Associate an app with the VPN profile

After adding your VPN profile, associate the app and Microsoft Entra group to the profile.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Apps** &gt; **All Apps**.
2. Select an app from the list &gt; **Properties** &gt; **Assignments** &gt; **Edit**.
3. Go to the **Required** or **Available for enrolled devices** section.
4. Select **Add group** &gt; Select the group you created in Step 1 - Create a group for your VPN users (in this article) &gt; **Select**.
5. In **VPNs**, select the per-app VPN profile you created in Step 4 - Create a per-app VPN profile (in this article).

    ![Two screenshots that show assigning an app to the per-app VPN profile in Microsoft Intune and Intune admin center.](media/configure-per-app-vpn-ios/vpn-per-app-app-to-vpn.png)
6. Select **OK** &gt; **Save**.

When **all** of the following conditions exist, an association between an app and a profile remains until the user requests a reinstall from the Company Portal app:

- The app was targeted with **available** install intent, **and**
- The profile and the app are assigned to the same group, **and**
- The end user requested the app install in the Company Portal app. This request results in the app and profile being installed on the device, **and**
- You remove or change the per-app VPN configuration from the app assignment.

When **all** of the following conditions exist, an association between an app and a profile is removed during the next device check-in:

- The app was targeted with **required** install intent, **and**
- The profile and the app are assigned to the same group, **and**
- You remove the per-app VPN configuration from the app assignment.

## Verify the connection on the iOS/iPadOS device

With your per-app VPN set up and associated with your app, verify the connection works from a device.

### Before you attempt to connect

- Make sure you deploy all the policies described in this article to the same group. Otherwise, the per-app VPN experience won't work.
- If you're using the Pulse Secure VPN app or a custom VPN client app, then you can choose to use app-layer or packet-layer tunneling:

    - For app-layer tunneling, set the **ProviderType** value to **app-proxy**.
    - For packet-layer tunneling, set **ProviderType** value to **packet-tunnel**.

    Check your VPN provider's documentation to make sure you're using the correct value.

### Connect using the per-app VPN

Verify the zero-touch experience by connecting without having to select the VPN or type your credentials. The zero-touch experience means:

- The device doesn't ask you to trust the VPN server. Meaning, the user doesn't see the **Dynamic Trust** dialog box.
- The user doesn't have to enter credentials.
- When the user opens one of the associated apps, the user's device is connected to the VPN.