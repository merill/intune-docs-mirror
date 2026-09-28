---
layout: Conceptual
title: Use a PKCS certificate profile to provision devices with certificates in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/certificates/pkcs-profiles
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- certificates
- sub-certificates
ms.reviewer: wicale
ms.subservice: configuration
description: Use Public Key Cryptography Standards (PKCS) certificates with Microsoft Intune, work with root certificates and certificate templates, and use device configuration profiles for a PKCS Certificate.
ms.date: 2026-08-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 3dda0ec6-0cfa-83b3-7ded-3fc5b8fa77de
document_version_independent_id: 3dda0ec6-0cfa-83b3-7ded-3fc5b8fa77de
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/certificates/pkcs-profiles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/certificates/pkcs-profiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/certificates/pkcs-profiles.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: e6019c02-0299-1a1b-8d9e-9adf5ef32dfc
---

# Use a PKCS certificate profile to provision devices with certificates in Microsoft Intune - Microsoft Intune | Microsoft Learn

**Applies to**L

- Android
- iOS/iPadOS
- macOS
- Windows

Microsoft Intune supports the use of private and public key pair (PKCS) certificates. This article reviews the requirements for PKCS certificates with Intune, including the export of a PKCS certificate then adding it to an Intune device configuration profile.

Microsoft Intune includes built-in settings to use PKCS certificates for access and authentication to your organizations resources. Certificates authenticate and secure access to your corporate resources like a VPN or a WiFi network. You deploy these settings to devices using device configuration profiles in Intune.

For information about using imported PKCS certificates, see [Imported PFX Certificates](imported-pfx-profiles).

Tip

*PKCS certificate* profiles are supported for [Windows Enterprise multi-session remote desktops](../../solutions/azure-virtual-desktop-multi-session).

Note

Device configuration profiles including PKCS certificate profile aren't supported on Microsoft Teams devices running AOSP.

## Requirements

To use PKCS certificates with Intune, you need the following infrastructure:

- Active Directory domain: All servers listed in this section must be joined to your Active Directory domain.

    For more information about installing and configuring Active Directory Domain Services (AD DS), see [AD DS Design and Planning](/en-us/windows-server/identity/ad-ds/plan/ad-ds-design-and-planning).
- Certification Authority: An Enterprise Certification Authority (CA).

    For information on installing and configuring Active Directory Certificate Services (AD CS), see [Active Directory Certificate Services Step-by-Step Guide](/en-us/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772393%28v=ws.10%29).

    Warning

    Intune requires you to run AD CS with an Enterprise Certification Authority (CA), not a Standalone CA.
- A client: To connect to the Enterprise CA.
- Root certificate: An exported copy of your root certificate from your Enterprise CA.
- Certificate Connector for Microsoft Intune: For information about the certificate connector, see:

    - Overview of the [Certificate Connector for Microsoft Intune](../../fundamentals/certificates/connector/overview)
    - [Prerequisites](../../fundamentals/certificates/connector/prerequisites)
    - [Installation and configuration](../../fundamentals/certificates/connector/setup-connector)

## Update certificate connector: Strong mapping requirements for KB5014754

The Key Distribution Center (KDC) requires a strong mapping format in PKCS certificates deployed by Microsoft Intune and used for certificate-based authentication. The mapping must have a security identifier (SID) extension that maps to the user or device SID. If a certificate doesn't meet the new strong mapping criteria set by the full enforcement mode date, authentication will be denied. For more information about the requirements, see [KB5014754: Certificate-based authentication changes on Windows domain controllers](https://support.microsoft.com/topic/kb5014754-certificate-based-authentication-changes-on-windows-domain-controllers-ad2c23b0-15d8-4340-a468-4d4f3b188f16).

In the Microsoft Intune Certificate Connector, version 6.2406.0.1001, we released an update that adds the object identifier attribute containing the user or device SID to the certificate, effectively satisfying the strong mapping requirements. This update applies to users and devices synced from an on-premises Active Directory to Microsoft Entra ID, and is available across all platforms, with some differences:

- Strong mapping changes apply to *user certificates* for all OS platforms.
- Strong mapping changes apply to *device certificates* for Microsoft Entra hybrid-joined Windows devices.

To ensure that certficate-based authentication continues working, you must take the following actions:

- Update the Microsoft Intune Certificate Connector to version 6.2406.0.1001. For information about the latest version and how to update the certificate connector, see [Certificate connector for Microsoft Intune](../../fundamentals/certificates/connector/overview).
- Make changes to registry key information on the Windows server that hosts the certificate connector.

Complete the following procedure to modify the registry keys and apply the strong mapping changes to certificates. These changes apply to new PKCS certificates and PKCS certificates that are being renewed.

Tip

This procedure requires you to modify the registry in Windows. For more information, see the following resources on Microsoft Support:

- [How to back up and restore the registry in Windows - Microsoft Support](https://support.microsoft.com/topic/how-to-back-up-and-restore-the-registry-in-windows-855140ad-e318-2a13-2829-d428a2ab0692)
- [How to add, modify, or delete registry subkeys and values by using a .reg file - Microsoft Support](https://support.microsoft.com/topic/how-to-add-modify-or-delete-registry-subkeys-and-values-by-using-a-reg-file-9c7f37cf-a5e9-e1cd-c4fa-2a26218a1a23)

1. In the Windows registry, change the value for `[HKLM\Software\Microsoft\MicrosoftIntune\PFXCertificateConnector](DWORD)EnableSidSecurityExtension` to **1**.
2. Restart the certificate connector service.

    1. Go to **Start** &gt; **Run**.
    2. Open **services.msc**.
    3. Restart these services:
        - **PFX Create Legacy Connector for Microsoft Intune**
        - **PFX Create Certificate Connector for Microsoft Intune**
3. Changes begin applying to all new certificates, and to certificates being renewed. To verify that authentication works, we recommend testing all places where certificate-based authentication could be used, including:

    - Apps
    - Intune-integrated certification authorities
    - NAC solutions
    - Networking infrastructure

    To roll back changes:

    1. Restore the original registry settings.
    2. Restart these services:

        - **PFX Create Legacy Connector for Microsoft Intune**
        - **PFX Create Certificate Connector for Microsoft Intune**
    3. Create a new PKCS certificate profile for affected devices, to reissue certificates without the SID attribute.

        Tip

        If you use a Digicert CA, you must create a certificate template for users with an SID and another template for users without an SID. For more information, see the [DigiCert PKI Platform 8.24.1 release notes](https://knowledge.digicert.com/general-information/release-notes-pki).

## Export the root certificate from the Enterprise CA

To authenticate a device with VPN, WiFi, or other resources, a device needs a root or intermediate CA certificate. The following steps explain how to get the required certificate from your Enterprise CA.

Use a command line to complete these steps:

1. Sign in to the Root Certification Authority server with Administrator Account.
2. Go to **Start** &gt; **Run**, and then enter **Cmd** to open a command prompt.
3. Enter **certutil -ca.cert ca\_name.cer** to export the root certificate as a file named *ca\_name.cer*.

## Configure certificate templates on the CA

1. Sign in to your Enterprise CA with an account that has administrative privileges.
2. Open the **Certification Authority** console, right-click **Certificate Templates**, and select **Manage**.
3. Find the **User** certificate template, right-click it, and choose **Duplicate Template** to open **Properties of New Template**.

    Note

    For S/MIME email signing and encryption scenarios, many administrators use separate certificates for signing and encryption. If you're using Microsoft Active Directory Certificate Services, you can use the Exchange Signature Only template for S/MIME email signing certificates, and the Exchange User template for S/MIME encryption certificates. If you're using a non-Microsoft certification authority, we recommend reviewing their guidance to set up signing and encryption templates.
4. On the **Compatibility** tab:

    - Set **Certification Authority** to **Windows Server 2008 R2**
    - Set **Certificate recipient** to **Windows 7 / Server 2008 R2**
5. On the **General** tab:

    - Set **Template display name** to something meaningful to you.
    - Deselect **Publish certificate in Active Directory**.

    Warning

    **Template name** by default is the same as **Template display name** with *no spaces*. Note the template name, because you need it later.
6. In **Request Handling**, select **Allow private key to be exported**.

    Note

    Unlike SCEP, with PKCS the certificate private key is generated on the server where the certificate connector is installed and not on the device. The certificate template must allow the private key to be exported so that the connector can export the PFX certificate and send it to the device.

    After the certificates install on the device, the private key is marked as not exportable.
7. In **Cryptography**, confirm that the **Minimum key size** is set to 2048.

    Windows and Android devices support the use of 4096-bit key size with a PKCS certificate profile. To use this key size, adjust the value to 4096.

    Note

    For Windows devices, 4096-bit key storage is supported only in the Software Key Storage Provider (KSP). The following features do not support storage for keys of this size:

    - The hardware TPM (Trusted Platform Module): As a workaround you can use the Software KSP for key storage.
    - Windows Hello for Business: There is no workaround for Windows Hello for Business at this time.
8. In **Subject Name**, choose **Supply in the request**.
9. In **Extensions**, under **Application Policies**, confirm that you see **Encrypting File System**, **Secure Email**, and **Client Authentication**.

    Important

    For iOS/iPadOS certificate templates, go to the **Extensions** tab, update **Key Usage**, and then deselect **Signature is proof of origin**.
10. In **Security**:

    1. Add the computer account for the server where you install the Certificate Connector for Microsoft Intune. Allow this account **Read** and **Enroll** permissions.
    2. Remove the domain users group from the list of groups or user names allowed permissions on this template. To remove the group:
        1. Select the **Domain Users** group.
        2. Select **Remove**.
        3. Review the other entries under **Groups or user names** to confirm permissions and applicability to your environment.
11. Select **Apply** &gt; **OK** to save the certificate template. Close the Certificate Templates Console.
12. In the **Certification Authority** console, right-click **Certificate Templates**.
13. Select **New** &gt; **Certificate Template to Issue**.
14. Choose the template that you created in the previous steps. Select **OK**.
15. Permit the server to manage certificates for enrolled devices and users:

    1. Right-click the Certification Authority, and then choose **Properties**.
    2. On the security tab, add the computer account of the server where you run the connector.
    3. Grant **Issue and Manage Certificates** and **Request Certificates** permissions to the computer account.
16. Sign out of the Enterprise CA.

## Download, install, and configure the Certificate Connector for Microsoft Intune

For guidance, see [Install and configure the Certificate Connector for Microsoft Intune](../../fundamentals/certificates/connector/setup-connector).

## Create a trusted certificate profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select and go to **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create**.
3. Enter the following properties:

    - **Platform**: Choose the platform of the devices receiving this profile.
        - Android device administrator
        - Android Enterprise:
            - Fully Managed
            - Dedicated
            - Corporate-Owned Work Profile
            - Personally-Owned Work Profile
        - iOS/iPadOS
        - macOS
        - Windows
    - **Profile**: Select **Trusted certificate**. Or, select **Templates** &gt; **Trusted certificate**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is *Trusted certificate profile for entire company*.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, specify the .cer file for the Root CA Certificate you previously exported.

    Note

    Depending on the platform you chose in **Step 3**, you may or may not have an option to choose the **Destination store** for the certificate.

    ![Configuration profile form with certificate upload field and destination store options](media/pkcs-profiles/certificates-pfx-configure-profile-fill.png)
8. Select **Next**.
9. In **Assignments**, select the user or device groups you want to include in the assignment. These groups receive the profile after you deploy it. For more granularity, see [Create filters in Microsoft Intune](https://go.microsoft.com/fwlink/?linkid=2150376) and apply them by selecting *Edit filter*.

    Plan to deploy this certificate profile to the same groups that receive:

    - The PKCS certificate profile and
    - A configuration profile, such as a Wi-Fi profile that makes use of the certificate.

    For more information about assigning profiles, see [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
10. (*Applies to Windows only*) In **Applicability Rules**, specify applicability rules to refine the assignment of this profile. You can choose to assign or not assign the profile based on the OS edition or version of a device.

    For more information, see [Applicability rules](../create-device-profile#applicability-rules) in *Create a device profile in Microsoft Intune*.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

## Create a PKCS certificate profile

Important

Android device administrator (DA) management is deprecated and no longer available for devices with access to Google Mobile Services (GMS). If you currently use DA management, we recommend switching to another Android management option. Support and help documentation remain available for some Android 15 and earlier devices without GMS. For more information, see [Ending support for Android device administrator on GMS devices](https://techcommunity.microsoft.com/t5/intune-customer-success/microsoft-intune-ending-support-for-android-device-administrator/ba-p/3915443).

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select and go to **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create**.
3. Enter the following properties:

    - **Platform**: Choose the platform of your devices. Your options:
        - Android device administrator
        - Android Enterprise:
            - Fully Managed
            - Dedicated
            - Corporate-Owned Work Profile
            - Personally-Owned Work Profile
        - iOS/iPadOS
        - macOS
        - Windows
    - **Profile**: Select **PKCS certificate**. Or, select **Templates** &gt; **PKCS certificate**.

    Note

    On devices with an Android Enterprise profile, certificates installed using a PKCS certificate profile are not visible on the device. To confirm successful certificate deployment, check the status of the profile in the Intune admin center.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is *PKCS profile for entire company*.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, depending on the platform you chose, the settings you can configure are different. Select your platform for detailed settings:

    - Android device administrator
    - Android Enterprise
    - iOS/iPadOS
    - Windows

    | Setting | Platform | Details |
    | --- | --- | --- |
    | **Deployment channel** | macOS | Select how you want to deploy the profile. This setting also determines the keychain where the linked certificates are stored, so it's important to select the proper channel. Always select the user deployment channel in profiles with user certificates. The user channel stores certificates in the user keychain. Always select the device deployment channel in profiles with device certificates. The device channel stores certificates in the system keychain.  It's not possible to edit the deployment channel after you deploy the profile. You must create a new profile to select a different channel. |
    | **Renewal threshold (%)** | All | Recommended is 20% |
    | **Certificate validity period** | All | If you didn't change the certificate template, this option might be set to one year.  Use a validity period of five days or up to 24 months. When the validity period is less than five days, there's a high likelihood of the certificate entering a near-expiry or expired state, which can cause the MDM agent on devices to reject the certificate before it's installed. |
    | **Key storage provider (KSP)** | Windows | For Windows, select where to store the keys on the device. |
    | **Certification authority** | All | Displays the internal fully qualified domain name (FQDN) of your Enterprise CA. |
    | **Certification authority name** | All | Lists the name of your Enterprise CA, such as "Contoso Certification Authority." |
    | **Certificate template name** | All | Lists the name of your certificate template. |
    | **Certificate type** | - Android Enterprise (*Corporate-Owned and Personally-Owned Work Profile*)<br>    - iOS<br>    - macOS<br>    - Windows | Select a type:<br>    - **User** certificates can contain both user and device attributes in the subject and subject alternative name (SAN) of the certificate.<br>    - **Device** certificates can only contain device attributes in the subject and SAN of the certificate. Use Device for scenarios such as user-less devices, like kiosks or other shared devices.  This selection affects the Subject name format. For macOS, if this profile is configured to use the device deployment channel, you can select **User** or **Device**. If the profile is configured to use the user deployment channel, you can select only **User**. |
    | **Subject name format** | All | For details on how to configure the subject name format, see Subject name format later in this article. For the following platforms, the Subject name format is determined by the certificate type:<br>    - Android Enterprise (*Work Profile*)<br>    - iOS<br>    - macOS<br>    - Windows |
    | **Subject alternative name** | All | For *Attribute*, select **User principal name (UPN)** unless otherwise required, configure a corresponding *Value*, and then select **Add**.  You can use variables or static text for the SAN of both certificate types. Use of a variable isn't required.For more information, see Subject name format later in this article. |
    | **Extended key usage** | - Android device administrator<br>    - Android Enterprise (*Device Owner*, *Corporate-Owned and Personally-Owned Work Profile*)<br>    - Windows | Certificates usually require *Client Authentication* so that the user or device can authenticate to a server. |
    | **Allow all apps access to private key** | macOS | Set to **Enable** to give apps that are configured for the associated mac device access to the PKCS certificate's private key.  For more information on this setting, see *AllowAllAppsAccess* the Certificate Payload section of [Configuration Profile Reference](https://developer.apple.com/business/documentation/Configuration-Profile-Reference.pdf) in the Apple developer documentation. |
    | **Root Certificate** | - Android device administrator<br>    - Android Enterprise (*Device Owner*, *Corporate-Owned and Personally-Owned Work Profile*) | Select a root CA certificate profile that was previously assigned. |
8. This step applies only to **Android Enterprise** devices profiles for **Fully Managed, Dedicated, and Corporate-Owned work Profile**.

    In **Apps**, configure **Certificate access** to manage how certificate access is granted to applications. Choose from:

    - **Require user approval for apps***(default)* – Users must approve use of a certificate by all applications.
    - **Grant silently for specific apps (require user approval for other apps)** – With this option, select **Add apps**. Then select all apps that should silently use the certificate without user interaction.
9. Select **Next**.
10. In **Assignments**, select the users and groups you want to include in the assignment. Users and groups receive the profile after you deploy it. Plan to deploy this certificate profile to the same groups that receive:

- The trusted certificate profile and
- A configuration profile, such as a Wi-Fi profile that makes use of the certificate.

For more information about assigning profiles, see [Assign user and device profiles](../assign-device-profile).

1. Select **Next**.
2. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

### Subject name format

When you create a PKCS certificate profile for the following platforms, options for the subject name format depend on the Certificate type you select, either **User** or **Device**.

Platforms:

- Android Enterprise (*Corporate-Owned and Personally-Owned Work Profile*)
- iOS
- macOS
- Windows

Note

There is a known issue for using PKCS to get certificates [which is the same issue as seen for SCEP](scep-profiles#avoid-certificate-signing-requests-with-escaped-special-characters) when the subject name in the resulting Certificate Signing Request (CSR) includes one of the following characters as an escaped character (proceeded by a backslash \):

- +
- ;
- ,
- =

Note

Beginning with Android 12, Android no longer supports use of the following hardware identifiers for *personally-owned work profile* devices:

- Serial number
- IMEI
- MEID

Intune certificate profiles for personally-owned work profile devices that rely on these variables in the subject name or SAN will fail to provision a certificate on devices that run Android 12 or later at the time the device enrolled with Intune. Devices that enrolled prior to upgrade to Android 12 can still receive certificates so long as Intune previously obtained the devices hardware identifiers.

For more information about this and other changes introduced with Android 12, see the [Android Day Zero Support for Microsoft Endpoint Manager](https://techcommunity.microsoft.com/t5/intune-customer-success/android-12-day-zero-support-with-microsoft-endpoint-manager/ba-p/2621665) blog post.

- **User certificate type** Format options for the *Subject name format* include two variables: **Common Name (CN)** and **Email (E)**. Email (E) would usually be set with the {{EmailAddress}} variable. For example: E={{EmailAddress}}

    **Common Name (CN)** can be set to any of the following variables:

    - **CN={{UserName}}**: The user name of the user, such as *Jane Doe*.
    - **CN={{UserPrincipalName}}**: The user principal name of the user, such as janedoe@contoso.com.
    - **CN={{AAD\_Device\_ID}}**: An ID assigned when you register a device in Microsoft Entra ID. This ID is typically used to authenticate with Microsoft Entra ID.
    - **CN={{DeviceId}}**: An ID assigned when you enroll a device in Intune.
    - **CN={{SERIALNUMBER}}**: The unique serial number (SN) typically used by the manufacturer to identify a device.
    - **CN={{IMEINumber}}**: The International Mobile Equipment Identity (IMEI) unique number used to identify a mobile phone.
    - **CN={{OnPrem\_Distinguished\_Name}}**: A sequence of relative distinguished names separated by comma, such as *CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com*.

        To use the *{{OnPrem\_Distinguished\_Name}}* variable, be sure to sync the *onpremisesdistinguishedname* user attribute using [Microsoft Entra Connect](/en-us/azure/active-directory/connect/active-directory-aadconnect) to your Microsoft Entra ID.
    - **CN={{onPremisesSamAccountName}}**: Admins can sync the samAccountName attribute from Active Directory to Microsoft Entra ID using Microsoft Entra Connect into an attribute called *onPremisesSamAccountName*. Intune can substitute that variable as part of a certificate issuance request in the subject of a certificate. The samAccountName attribute is the user sign-in name used to support clients and servers from a previous version of Windows (pre-Windows 2000). The user sign-in name format is: *DomainName\testUser*, or only *testUser*.

        To use the *{{onPremisesSamAccountName}}* variable, be sure to sync the *onPremisesSamAccountName* user attribute using [Microsoft Entra Connect](/en-us/azure/active-directory/connect/active-directory-aadconnect) to your Microsoft Entra ID.

    All device variables listed in the following *Device certificate type* section can also be used in user certificate subject names.

    By using a combination of one or many of these variables and static text strings, you can create a custom subject name format, such as: **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

    That example includes a subject name format that uses the CN and E variables, and strings for organizational unit, organization, location, state, and country/region values. [CertStrToName function](/en-us/windows/win32/api/wincrypt/nf-wincrypt-certstrtonamea) describes this function, and its supported strings.

    User attributes aren't supported for devices that don't have user associations, such as devices that are enrolled as Android Enterprise dedicated. For example, a profile that uses *CN={{UserPrincipalName}}* in the subject or SAN can't get the user principal name when there isn't a user on the device.
- **Device certificate type** Format options for the Subject name format include the following variables:

    - **{{AAD\_Device\_ID}}**
    - **{{DeviceId}}** - The Intune device ID
    - **{{Device\_Serial}}**
    - **{{Device\_IMEI}}**
    - **{{SerialNumber}}**
    - **{{IMEINumber}}**
    - **{{AzureADDeviceId}}**
    - **{{WiFiMacAddress}}**
    - **{{IMEI}}**
    - **{{DeviceName}}**
    - **{{FullyQualifiedDomainName}}***(Only applicable for Windows and domain-joined devices)*
    - **{{MEID}}**

    You can specify these variables, followed by the text for the variable, in the textbox. For example, the common name for a device named *Device1* can be added as **CN={{DeviceName}}Device1**.

    Important

    - When you specify a variable, enclose the variable name in curly brackets { } as seen in the example, to avoid an error.
    - Device properties used in the *subject* or *SAN* of a device certificate, like **IMEI**, **SerialNumber**, and **FullyQualifiedDomainName**, are properties that could be spoofed by a person with access to the device.
    - A device must support all variables specified in a certificate profile for that profile to install on that device. For example, if **{{IMEI}}** is used in the subject name of a SCEP profile and is assigned to a device that doesn't have an IMEI number, the profile fails to install.