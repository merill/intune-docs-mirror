---
layout: Conceptual
title: Plan for security - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/plan-for-security
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
description: Get best practices and other information about security in Configuration Manager.
ms.date: 2021-08-02T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection:
- tier3
- essentials-security
locale: en-us
document_id: db3c5515-4047-886b-5fe2-e0717f73028d
document_version_independent_id: 692eff5e-879c-aa4f-d346-cb0d1758573e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/security/plan-for-security.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/security/plan-for-security
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/security/plan-for-security.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
platformId: 48a3ac84-8f32-7dd7-ab54-fa72eededac2
---

# Plan for security - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article describes the following concepts for you to consider when planning for security with your Configuration Manager implementation:

- Certificates (self-signed and PKI)
- The trusted root key
- Signing and encryption
- Role-based administration
- Microsoft Entra ID
- SMS Provider authentication

Before you start, make sure you're familiar with the [fundamentals of security in Configuration Manager](../../understand/fundamentals-of-security).

## Certificates

Configuration Manager uses a combination of self-signed and public key infrastructure (PKI) digital certificates. Use PKI certificates whenever possible. Some scenarios require PKI certificates. When PKI certificates aren't available, the site automatically generates self-signed certificates. Some scenarios always use self-signed certificates.

For more information, see [Plan for certificates](plan-for-certificates).

## The trusted root key

The Configuration Manager trusted root key provides a mechanism for Configuration Manager clients to verify that site systems belong to their hierarchy. Every site server generates a site exchange key to communicate with other sites. The site exchange key from the top-level site in the hierarchy is called the trusted root key.

The function of the trusted root key in Configuration Manager resembles a root certificate in a public key infrastructure. Anything signed by the private key of the trusted root key is trusted further down the hierarchy. Clients store a copy of the site's trusted root key in the `root\ccm\locationservices` WMI namespace.

For example, the site issues a certificate to the management point, which it signs with the private key of the trusted root key. The site shares with clients the public key of its trusted root key. Then clients can differentiate between management points that are in their hierarchy and management points that aren't in their hierarchy.

Clients automatically get the public copy of the trusted root key by using two mechanisms:

- You extend the Active Directory schema for Configuration Manager, and publish the site to Active Directory Domain Services. Then clients retrieve this site information from a global catalog server. For more information, see [Prepare Active Directory for site publishing](../network/extend-the-active-directory-schema).
- When you install clients using the client push installation method. For more information, see [Client push installation](../../clients/deploy/plan/client-installation-methods#client-push-installation).

If clients can't get the trusted root key by using one of these mechanisms, they trust the trusted root key that's provided by the first management point that they communicate with. In this scenario, a client might be misdirected to an attacker's management point where it would receive policy from the rogue management point. This action requires a sophisticated attacker. This attack is limited to the short time before the client retrieves the trusted root key from a valid management point. To reduce this risk of an attacker misdirecting clients to a rogue management point, pre-provision the clients with the trusted root key.

For more information and procedures to manage the trusted root key, see [Configure security](configure-security#manage-the-trusted-root-key).

## Signing and encryption

When you use PKI certificates for all client communications, you don't have to plan for signing and encryption to help secure client data communication. If you set up any site systems that run IIS to allow HTTP client connections, decide how to help secure the client communication for the site.

Important

Starting in Configuration Manager version 2103, sites that allow HTTP client communication are deprecated. Configure the site for HTTPS or Enhanced HTTP. For more information, see [Enable the site for HTTPS-only or enhanced HTTP](../../servers/deploy/install/list-of-prerequisite-checks#enable-site-system-roles-for-https-or-enhanced-http).

To help protect the data that clients send to management points, you can require clients to sign the data. You can also require the SHA-256 algorithm for signing. This configuration is more secure, but don't require SHA-256 unless all clients support it. Many operating systems natively support this algorithm, but older operating systems might require an update or hotfix.

While signing helps protect the data from tampering, encryption helps protect the data from information disclosure. You can enable encryption for the inventory data and state messages that clients send to management points in the site. You don't have to install any updates on clients to support this option. Clients and management points require more CPU usage for encryption and decryption.

Note

To encrypt the data, the client uses the public key of the management point's encryption certificate. Only the management point has the corresponding private key, so only it can decrypt the data.

The client bootstraps this certificate with the management point's signing certificate, which it bootstraps with the site's trusted root key. Make sure to securely provision the trusted root key on clients. For more information, see The trusted root key.

For more information about how to configure the settings for signing and encryption, see [Configure signing and encryption](configure-security#signing-and-encryption).

For more information on the cryptographic algorithms used for signing and encryption, see [Cryptographic controls technical reference](cryptographic-controls-technical-reference).

## Role-based administration

With Configuration Manager, you use role-based administration to secure the access that administrative users need to use Configuration Manager. You also secure access to the objects that you manage, like collections, deployments, and sites.

With the combination of security roles, security scopes, and collections, you segregate the administrative assignments that meet your organization's requirements. Used together, they define the *administrative scope* of a user. This administrative scope controls the objects that an administrative user views in the Configuration Manager console, and it controls the permissions that a user has on those objects.

For more information, see [Fundamentals of role-based administration](../../understand/fundamentals-of-role-based-administration).

## Microsoft Entra ID

Configuration Manager integrates with Microsoft Entra ID to enable the site and clients to use modern authentication.

For more information about Microsoft Entra ID, see [Microsoft Entra documentation](/en-us/entra/).

Onboarding your site with Microsoft Entra ID supports the following Configuration Manager scenarios:

### Client scenarios

- [Manage clients on the internet via cloud management gateway](../../clients/manage/cmg/overview)
- [Manage cloud domain-joined devices](../../clients/deploy/deploy-clients-cmg-azure)
- [Co-management](../../../comanage/overview)
- [Deploy user-available apps](../../../apps/plan-design/prerequisites-deploy-user-available-apps)
- [Microsoft Store for Business online apps](../../../apps/deploy-use/manage-apps-from-the-windows-store-for-business)
- [Manage Microsoft 365 Apps for enterprise](../../../sum/deploy-use/manage-office-365-proplus-updates)

### Server scenarios

- [Tenant attach](../../../tenant-attach/device-sync-actions)
- [Endpoint analytics](../../../../endpoint-analytics/)
- [Azure Log Analytics](/en-us/azure/azure-monitor/platform/collect-sccm)
- [Community Hub](../../get-started/capabilities-in-technical-preview-1807#bkmk_hub)
- [User discovery](../../servers/deploy/configure/configure-discovery-methods#azureaadisc)

## SMS Provider authentication

You can specify the minimum authentication level for administrators to access Configuration Manager sites. This feature enforces administrators to sign in to Windows with the required level before they can access Configuration Manager. It applies to all components that access the SMS Provider. For example, the Configuration Manager console, SDK methods, and Windows PowerShell cmdlets.

Configuration Manager supports the following authentication levels:

- **Windows authentication**: Require authentication with Active Directory domain credentials. This setting is the previous behavior, and the current default setting.
- **Certificate authentication**: Require authentication with a valid certificate that's issued by a trusted PKI certificate authority. You don't configure this certificate in Configuration Manager. Configuration Manager requires the administrator to be signed in to Windows using PKI.
- **Windows Hello for Business authentication**: Require authentication with strong two-factor authentication that's tied to a device and uses biometrics or a PIN. For more information, see [Windows Hello for Business](/en-us/windows/security/identity-protection/hello-for-business/hello-identity-verification).

    Important

    When you select this setting, the SMS Provider and administration service require the user's authentication token to contain a multi-factor authentication (MFA) claim from Windows Hello for Business. In other words, a user of the console, SDK, PowerShell, or administration service has to authenticate to Windows with their Windows Hello for Business PIN or biometric. Otherwise the site rejects the user's action.

    This behavior is for *Windows Hello for Business*, not Windows Hello.

For more information on how to configure this setting, see [Configure SMS Provider authentication](configure-security#sms-provider-authentication).