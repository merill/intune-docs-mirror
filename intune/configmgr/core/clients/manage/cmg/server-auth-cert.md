---
layout: Conceptual
title: CMG server authentication certificate - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/server-auth-cert
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
manager: laurawi
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
author: sccmavenger
ms.author: dannygu
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: The CMG uses HTTPS for secure client communication over the public internet. You can get a certificate from a public provider, or issue one from your public key infrastructure (PKI).
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: ade53de5-3c7a-669d-2786-41d14fb6cea8
document_version_independent_id: 036c9651-1adc-fdcb-7d67-32d212e574e5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/cmg/server-auth-cert.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/cmg/server-auth-cert
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/cmg/server-auth-cert.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/96f6b0a2-2fd7-4de1-936d-89ad6e0eb7cc
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/ef8b0a5a-ba0a-4ec0-8636-48246ccd954f
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
platformId: 331e92de-9a4f-7f2c-d1ee-f8f8deb5a570
---

# CMG server authentication certificate - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The first step when you set up a cloud management gateway (CMG) is to get the server authentication certificate. The CMG creates an HTTPS service to which internet-based clients connect. The server requires a server authentication certificate to build the secure channel. You can acquire a certificate for this purpose from a public provider, or issue it from your public key infrastructure (PKI).

When you create the CMG in the Configuration Manager console, you provide this certificate. The common name (CN) of this certificate defines the service name of the CMG.

Note

You may need additional certificates for clients and management points. These certificates are covered in the third step of the CMG setup process, [Configure client authentication](configure-authentication).

A reminder of some CMG terminology that's used in this article:

- **Service name**: The common name (CN) of the CMG server authentication certificate. Clients and the CMG connection point site system role communicate with this service name. For example, `GraniteFalls.contoso.com` or `GraniteFalls.WestUS.CloudApp.Azure.Com`.
- **Deployment name**: The first part of the service name plus the Azure location for the cloud service deployment. The cloud service manager component of the service connection point uses this name when it deploys the CMG in Azure. The deployment name is always in an Azure domain. The Azure location depends upon the deployment method, for example:

    - Virtual machine scale set: `GraniteFalls.WestUS.CloudApp.Azure.Com`
    - Classic deployment: `GraniteFalls.CloudApp.Net`

    Important

    This article uses examples with a virtual machine scale set as the recommended deployment method in version 2107 and later. If you use a classic deployment, note the difference as you read this article and prepare the server authentication certificate.

## Choose the certificate type

First, decide where you want to get the certificate. There are several factors to consider.

Clients must trust the CMG server authentication certificate to establish the HTTPS channel with the CMG service. There are two methods to accomplish this trust:

1. Use a certificate from a public and globally trusted certificate provider.

    - Windows clients include trusted root certificate authorities (CAs) from these providers. By using a certificate issued by one of these providers, your clients automatically trust it.
    - There's a cost associated with this certificate, which is specific to the provider.
2. Use a certificate issued by an enterprise CA from your public key infrastructure (PKI).

    - Most enterprise PKI implementations add the trusted root CAs to Windows clients. For example, if you use Active Directory Certificate Services with group policy. If you issue the CMG server authentication certificate from a CA that your clients don't automatically trust, add the CA trusted root certificate to internet-based clients.

        If you plan to [install the Configuration Manager client from Intune](../../../../comanage/how-to-prepare-win10#install-the-configuration-manager-client), you can also use Intune certificate profiles to provision certificates on clients. For more information, see [Configure a certificate profile](../../../../../fundamentals/certificates/overview).
    - Your organization may have an internal cost to issue certificates, but there are generally no external costs associated with this certificate.

Important

Before you get this certificate, make sure the service name is globally unique for the cloud service and storage account. Also make sure the name uses supported characters. For more information, see Globally unique name.

### Summary comparison of certificate types

| - | Public provider | Enterprise PKI |
| --- | --- | --- |
| **Client trust** | Trusted in Windows by default | Automatic with some implementations, otherwise need to deploy |
| **Cost** | Yes | Not typical |
| **Service name example** | `GraniteFalls.contoso.com` | `GraniteFalls.contoso.com` or `GraniteFalls.WestUS.CloudApp.Azure.Com` |
| **DNS CNAME required** | Yes | No for Azure domain service name (`GraniteFalls.WestUS.CloudApp.Azure.Com`) |

Note

The CMG server authentication certificate supports wildcards. Some certificate authorities issue certificates using a wildcard character for the service name prefix. For example, `*.contoso.com`. Some organizations use wildcard certificates to simplify their PKI and reduce maintenance costs.

For more information on how to use a wildcard certificate with a CMG, see [Set up a CMG](setup-cloud-management-gateway#set-up-a-cmg).

## Globally unique name

This certificate requires a globally unique name to identify the service in Azure. Before you request a certificate, confirm that the Azure *deployment name* you want is unique. For example, `GraniteFalls.WestUS.CloudApp.Azure.Com`.

### Virtual machine scale set

1. Sign in to the [Azure portal](https://portal.azure.com).
2. From the Azure portal home page, select **Create a resource** under Azure services.
3. Search for **Virtual machine scale set**. Select **Create**.
4. Select the **Subscription** and **Resource group** that you'll use for the CMG.
5. In the **Virtual machine scale set name** field, type the prefix that you want. For example, `GraniteFalls`.
6. Select the **Region** that you'll use for the CMG. For example, **(US) West US**.

The interface reflects whether the domain name is available or already in use by another service.

Important

Don't create the service in the portal, just use this process to check the name availability.

Repeat this process for the **Key Vault** resource. The virtual machine scale set deployment creates a key vault with the same name, which also needs to be globally unique.

### Content-enabled CMG storage account

If you also enable the CMG for content, confirm that it's also a unique Azure storage account name. If the CMG deployment name is unique, but the storage account isn't, Configuration Manager fails to provision the service in Azure. Repeat the above process in the Azure portal with the following changes:

- Search for **Storage account**.
- Test your name in the **Storage account name** field.

Important

The DNS name prefix should be 3 to 24 characters long, and contain numbers and lowercase letters only. Don't use special characters, like a dash (`-`). For example: `granitefalls`.

## Issue the certificate

The CMG server authentication certificate supports the following configurations:

- 2048-bit or 4096-bit key length
- This certificate supports key storage providers for certificate private keys (v3). For more information, see [CNG v3 certificates overview](../../../plan-design/network/cng-certificates-overview).

### Use a public provider certificate

A third-party certificate provider can't create a certificate for an Azure domain like `cloudapp.azure.com`, because Microsoft owns those domains. You can only get a certificate issued for a domain you own. The main reason for acquiring a certificate from a third-party provider is that your clients already trust that provider's root certificate.

The specific process to get this certificate varies by provider. For more information, contact your third-party certificate provider.

For the web server certificate common name (CN):

- You've made sure the *deployment name* is globally unique in Azure for the cloud service and storage account. For example, `GraniteFalls.WestUS.CloudApp.Azure.Com`.
- To determine the *service name*, append the *deployment name* prefix (`GraniteFalls`) to your organization's domain name (`contoso.com`).
- Use this *service name* for the certificate common name (CN). For example, `GraniteFalls.contoso.com`.

Next, you need to create a DNS CNAME alias.

### Use an enterprise PKI certificate

Issuing a web server certificate from your organization's PKI varies by product. The instructions for [Deploying the service certificate for cloud-based distribution points](../../../plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012) are for Active Directory Certificate Services. This process generally applies for the CMG server authentication certificate.

For the web server certificate common name (CN):

- You've made sure the *deployment name* is globally unique in Azure for the cloud service and storage account. For example, `GraniteFalls.WestUS.CloudApp.Azure.Com`.
- To determine the *service name*, you have two options:

    - Use your domain name (recommended). Append the *deployment name* prefix (`GraniteFalls`) to your organization's domain name (`contoso.com`). For example, `GraniteFalls.contoso.com`. For this option, you also need to create a DNS CNAME alias.
    - Use the Azure deployment name. This option doesn't require a DNS CNAME alias. For example:

        - For the Azure public cloud: `GraniteFalls.WestUS.CloudApp.Azure.Com`.
        - For the Azure US Government cloud: `GraniteFalls.usgovcloudapp.net`.

        Note

        If the Azure deployment name changes, you'll need to redeploy the service to change this service name. For example, if your service name is in the `cloudapp.net` domain, you can't convert the classic cloud service CMG to a virtual machine scale set. If you use your domain name for the CMG service name, then you can update the DNS CNAME for the new deployment name.
- Use this *service name* for the certificate common name (CN).

## Create a DNS CNAME alias

If the CMG service name uses your organization's domain name (`GraniteFalls.contoso.com`), you need to create a DNS canonical name record (CNAME). This alias maps the *service name* to the *deployment name*.

Create a CNAME record in your organization's public DNS. The CMG service in Azure and all clients that use it need to resolve the service name. For example:

- Contoso names their CMG **GraniteFalls**.
- The deployment name in Azure is `GraniteFalls.WestUS.CloudApp.Azure.Com`.
- In Contoso's public DNS `contoso.com` namespace, the DNS administrator creates a new CNAME record for the service name `GraniteFalls.contoso.com` to the Azure deployment name, `GraniteFalls.WestUS.CloudApp.Azure.Com`.

When you create the CMG, while the certificate has `GraniteFalls.contoso.com` as the CN, Configuration Manager only extracts the service name prefix, for example: **GraniteFalls**. It appends this prefix to the Azure service domain (`cloudapp.azure.com`) with the region (`westus`) to create the deployment name. For example, `GraniteFalls.WestUS.CloudApp.Azure.Com`. The CNAME alias in the DNS namespace for your domain (`contoso.com`) maps together these two FQDNs.

The Configuration Manager client policy includes the CMG service name, `GraniteFalls.contoso.com`. The client resolves the service name via the CNAME alias to the deployment name, `GraniteFalls.WestUS.CloudApp.Azure.Com`. It then can resolve the IP address of the deployment name to communicate with the service in Azure.