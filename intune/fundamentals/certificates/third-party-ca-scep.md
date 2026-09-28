---
layout: Conceptual
title: Use third-party certification authorities (CA) with SCEP in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/certificates/third-party-ca-scep
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
ms.subservice: fundamentals
description: In Microsoft Intune, you can add a vendor or third-party certificate authority (CA) to issue certificates to mobile devices using the SCEP protocol. In this overview, a Microsoft Entra application gives Microsoft Intune permissions to validate certificates. Then, use the application ID, authentication key, and tenant ID of the Microsoft Entra application in the setup of your SCEP server to issue certificates.
ms.date: 2024-10-15T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: a59bde4a-9358-fe70-a3cb-bd684d837cf4
document_version_independent_id: a59bde4a-9358-fe70-a3cb-bd684d837cf4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/certificates/third-party-ca-scep.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/certificates/third-party-ca-scep
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/certificates/third-party-ca-scep.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 439a8ce8-1435-8b88-611d-df6c7a14d320
---

# Use third-party certification authorities (CA) with SCEP in Microsoft Intune - Microsoft Intune | Microsoft Learn

Use third-party certification authorities (CA) with Intune. Third-party CAs can provision mobile devices with new or renewed certificates by using the Simple Certificate Enrollment Protocol (SCEP), and can support Windows, iOS/iPadOS, Android, and macOS devices.

There are two parts to using this feature: open-source API, and the Intune administrator tasks.

**Part 1 - Use an open-source API** Microsoft created an API to integrate with Intune. Through the API you can validate certificates, send success or failure notifications, and use SSL, specifically SSL socket factory, to communicate with Intune.

The API is available on the [Intune SCEP API public GitHub repository](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation) for you to download, and use in your solutions. Use this API with third-party SCEP servers to run custom challenge validation against Intune before SCEP provisions a certificate to a device.

[Integrate with Intune SCEP management solution](ref-scep-api) provides more details on using the API, its methods, and testing the solution you build.

**Part 2 - Create the application and profile** Using a Microsoft Entra application, you can delegate rights to Intune to handle SCEP requests coming from devices. The Microsoft Entra application includes application ID and authentication key values that are used within the API solution the developer creates. Administrators then create and deploy SCEP certificates profiles using Intune and can view reports on the deployment status on the devices.

This article provides an overview of this feature from an Administrator-perspective, including creating the Microsoft Entra application.

## Overview

The following steps provide an overview of using SCEP for certificates in Intune:

1. In Intune, an administrator creates a SCEP certificate profile, and then targets the profile to users or devices.
2. The device checks in to Intune.
3. Intune creates a unique SCEP challenge. It also adds additional integrity-check information, such as what the expected subject and SAN should be.
4. Intune encrypts and signs both the challenge and integrity-check information, and then sends this information to the device with the SCEP request.
5. The device generates a certificate signing request (CSR) and public/private key pair on the device based on the SCEP certificate profile that's pushed from Intune.
6. The CSR and encrypted/signed challenge are sent to the third-party SCEP server endpoint.
7. The SCEP server sends the CSR and the challenge to Intune. Intune then validates the signature, decrypts the payload, and compares the CSR to the integrity-check information.
8. Intune sends back a response to the SCEP server, and states whether the challenge validation is successful or not.
9. If the challenge is successfully verified, then the SCEP server issues the certificate to the device.

The following diagram shows a detailed flow of third-party SCEP integration with Intune:

![Data flow diagram showing how third-party certification authority SCEP integrates with Microsoft Intune](media/third-party-ca-scep/scep-certificate-vendor-integration.png)

## Set up third-party CA integration

### Validate third-party certification authority

Before integrating third-party certification authorities with Intune, confirm that the CA you're using supports Intune. Third-party CA partners (in this article) includes a list. You can also check your certification authority's guidance for more information. The CA may include setup instructions specific to their implementation.

Note

To support the following devices, the CA must support the use of an HTTPS URL when you configure you must configure an HTTPS URL when you configure *SCEP Server URLs* for the [SCEP certificate profile](../../device-configuration/certificates/scep-profiles):

- Android device administrator
- Android Enterprise device owner
- Android Enterprise corporate-owned work profile
- Android Enterprise personally-owned work profile

### Authorize communication between CA and Intune

To allow a third-party SCEP server to run custom challenge validation with Intune, create an app in Microsoft Entra ID. This app gives delegated rights to Intune to validate SCEP requests.

Be sure you have the required permissions to register a Microsoft Entra app. See [Required permissions](/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal#required-permissions), in the Microsoft Entra documentation.

#### Create an application in Microsoft Entra ID

1. In the [Azure portal](https://portal.azure.com), go to **Microsoft Entra ID** &gt; **App Registrations**, and then select **New registration**.
2. On the **Register an application** page, specify the following details:

    - In the **Name** section, enter a meaningful application name.
    - For the **Supported account types** section, select **Accounts in any organizational directory**.
    - For **Redirect URI**, leave the default of Web, and then specify the sign-on URL for the third-party SCEP server.
3. Select **Register** to create the application and to open the Overview page for the new app.
4. On the app **Overview** page, copy the **Application (client) ID** value and record it for later use. You'll need this value later.
5. In the navigation pane for the app, go to **Certificates & secrets** under **Manage**. Select the **New client secret** button. Enter a value in Description, select any option for **Expires**, and then and choose **Add** to generate a *value* for the client secret.

    Important

    Before you leave this page, copy the value for the client secret and record it for later use with your third-party CA implementation. This value is not shown again. Be sure to review the guidance for your third-party CA on how they want the Application ID, Authentication Key, and Tenant ID configured.
6. Record your **Tenant ID**. The Tenant ID is the domain text after the @ sign in your account. For example, if your account is *admin@name.onmicrosoft.com*, then your tenant ID is **name.onmicrosoft.com**.
7. In the navigation pane for the app, go to **API permissions**, which are under **Manage**. You're going to add two separate application permissions:

    1. Select **Add a permission**:

        1. On the *Request API permissions* page, select **Intune** and then select **Application permissions**.
        2. Select the checkbox for **scep\_challenge\_provider** (SCEP challenge validation).
        3. Select **Add permissions** to save this configuration.
    2. Select **Add a permission** again.

        1. On the *Request API permissions* page, select **Microsoft Graph** &gt; **Application permissions**.
        2. Expand **Application** and select the checkbox for **Application.Read.All** (Read all applications).
        3. Select **Add permissions** to save this configuration.
8. Remain on the **API permissions** page, and select **Grant admin consent for*****&lt;your tenant&gt;***, and then select **Yes**.

    The app registration process in Microsoft Entra ID is complete.

### Configure and deploy a SCEP certificate profile

As the administrator, create a SCEP certificate profile to target to users or devices. Then, assign the profile.

- [Create a SCEP certificate profile](../../device-configuration/certificates/scep-profiles#create-a-scep-certificate-profile)
- [Assign the certificate profile](../../device-configuration/certificates/scep-profiles#assign-the-certificate-profile)

## Removing certificates

After you unenroll or wipe the device, the certificates are removed from the device by Intune and queued for revocations. Revocation on the certificate authority depends on API implementation by each third party.

## Third-party certification authority partners

The following third-party certification authorities support Intune:

- [AWS Private Certificate Authority](https://docs.aws.amazon.com/privateca/latest/userguide/connector-for-scep-getting-started.html)
- [Cogito Group](https://training.cogitogroup.net/documentation/simple-certificate-enrolment-protocol-scep)
- [DigiCert](https://knowledge.digicert.com/tutorials/microsoft-intune.html)
- [EasyScep](https://docs.just-software.com/EasyScep/)
- [EJBCA](https://doc.primekey.com/ejbca/ejbca-integration/integrating-with-third-party-applications/microsoft-intune-device-certificate-enrollment)
- [Entrust](https://go.entrustdatacard.com/pki/intune/)
- [EverTrust](https://evertrust.fr/en/products/)
- [GlobalSign](https://downloads.globalsign.com/acton/attachment/2674/f-6903f60b-9111-432d-b283-77823cc65500/1/-/-/-/-/globalsign-aeg-microsoft-intune-integration-guide.pdf)
- [HID Global](https://help.hydrantid.com/HydrantID_Intune_Integration.pdf)
- [IDnomic](https://www.idnomic.com/)
- [Keyfactor Command](https://software.keyfactor.com/Guides/SCEPGuide/Content/SCEPGuide/Introduction.htm)
- [KeyTalk](https://keytalk.com/)
- [Keytos](https://docs.keytos.io/azure-pki/intune-certificate-authority/how-intune-scep-works/)
- [Nexus Certificate Manager](https://doc.nexusgroup.com/nexus-certificate-manager/8.13/scep-support-in-certificate-manager)
- [SCEPman](https://azuremarketplace.microsoft.com/marketplace/apps/glueckkanja-gabag.scepman)
- [Sectigo](https://sectigo.com/products)
- [SecureW2](https://www.securew2.com/solutions/managed-devices/scep-ca-integration-with-microsoft-intune)
- [Splashtop](https://docs.foxpass.com/docs/scep)
- [Venafi](https://www.venafi.com/platform/enterprise-mobility)

If you're a third-party CA interested in integrating your product with Intune, review the API guidance:

- [Intune SCEP API GitHub repository](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/CsrValidation)
- [Intune SCEP API guidance for third party CAs](ref-scep-api)

## Security and privacy information

Some user information in the SCEP profile becomes visible to the third-party certificate authority (CA) receiving the certificate signing request. This happens when you deploy a new or updated SCEP profile that contains the `Common name (CN)` user attribute, and variables such as `UserName`, `OnPrem_Distinguished_Name`, and `OnPremisesSamAccountName`. During profile deployment, Microsoft Intune replaces these variables with actual values. The targeted devices in turn must reach out to the third-party CA to request a certificate with the actual values.

For a list of supported user variables, see **Step 7** under [Create a SCEP certificate profile](../../device-configuration/certificates/scep-profiles#create-a-scep-certificate-profile).