---
layout: Conceptual
title: Use on-premises services with cloud-native endpoints - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/solutions/cloud-native-endpoints/on-premises-resources
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.reviewer: ahamil, jasandys, wicale
description: For cloud-native endpoints to access on-premises resources, such as file servers, printers, and web servers, use Windows integrated authentication (WIA) and Microsoft Entra Connect.
ms.date: 2025-02-20T00:00:00.0000000Z
ms.topic: how-to
ms.collection:
- M365-identity-device-management
- intune-scenario
locale: en-us
document_id: de3f7db1-db33-d285-7899-c4c69e1c5452
document_version_independent_id: de3f7db1-db33-d285-7899-c4c69e1c5452
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/solutions/cloud-native-endpoints/on-premises-resources.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: solutions/cloud-native-endpoints/on-premises-resources
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/solutions/cloud-native-endpoints/on-premises-resources.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: aacd88ca-6170-a205-2b62-b5f4787bf201
---

# Use on-premises services with cloud-native endpoints - Microsoft Intune | Microsoft Learn

Cloud-native endpoints can access on-premises resources. This article goes into more detail, and answers some common questions.

This feature applies to:

- Windows cloud-native endpoints

For an overview of cloud-native endpoints, and their benefits, go to [What are cloud-native endpoints](overview).

Tip

When reading about cloud native endpoints, you see the following terms:

- **Endpoint**: An endpoint is a device, like a mobile phone, tablet, laptop, or desktop computer. "Endpoints" and "devices" are used interchangeably.
- **Managed endpoints**: Endpoints that receive policies from the organization using an MDM solution or Group Policy Objects. These devices are typically organization owned, but can also be BYOD or personally owned devices.
- **Cloud native endpoints**: Endpoints that are joined to Microsoft Entra. They aren't joined to on-premises AD.
- **Workload**: Any program, service, or process.

## Prerequisites

For cloud-native Windows endpoints to access on-premises resources and services that use on-premises Active Directory (AD) for authentication, the following prerequisites are required:

- Client apps **must use Windows integrated authentication (WIA)**. For more specific information, go to [Windows Integrated Authentication (WIA)](/en-us/aspnet/web-api/overview/security/integrated-windows-authentication).
- **Configure Microsoft Entra Connect**. Microsoft Entra Connect synchronizes user accounts from the on-premises AD to Microsoft Entra. For more specific information, go to [Microsoft Entra Connect sync: Understand and customize synchronization](/en-us/entra/identity/hybrid/connect/how-to-connect-sync-whatis).

    In Microsoft Entra Connect, you may have to adjust your domain-based filtering to confirm that the required domains data is synchronized to Microsoft Entra.
- The device has line of sight **connectivity (either directly or through VPN) to a domain controller** from the AD domain and to the service or resource being accessed.

## Similar to on-premises Windows devices

For end users, a Windows cloud-native endpoint behaves like any other on-premises Windows device.

The following list is a common set of on-premises resources that users can access from their Microsoft Entra joined devices:

- A file server: Using SMB (Server Message Block), you can map a network drive to a domain-member server that hosts a network share or NAS (Network Attached Storage).

    Users can map drives to shared and personal documents.
- A printer resource on a domain-member server: Users can print to their local or nearest printer.
- A web server on a domain-member server that uses Windows Integrated security: Users can access any Win32 or web-based application.
- Want to manage your on-premises AD domain from a Microsoft Entra joined endpoint: Install the [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=45520):

    - Use the Active Directory Users and Computers (ADUC) snap-in to administer all AD objects. You must manually enter the domain that you want to connect to.
    - Use the DHCP snap-in to administer an AD-joined DHCP server. You might need to enter the DHCP server name or address.

Tip

To understand how Microsoft Entra joined devices use cached credentials in a cloud-native approach, watch [OPS108: Windows authentication internals in a hybrid world (syfuhs.net)](https://syfuhs.net/ops108-windows-authentication-internals-in-a-hybrid-world) (opens an external website).

## Authentication and access to on-premises resources

The following steps describe how a Microsoft Entra joined endpoint authenticates and accesses (based on permissions) an on-premises resource.

The following steps are an overview. For more specific information, including detailed swimlane graphics that describe the full process, go to [Primary Refresh Token (PRT) and Microsoft Entra](/en-us/entra/identity/devices/concept-primary-refresh-token).

1. When users sign in, their credentials are sent to the Cloud Authentication Provider (CloudAP) and the Web Account Manager (WAM).
2. The CloudAP plugin sends the user and device credentials to Microsoft Entra. Or, [it authenticates using Windows Hello for Business](/en-us/windows/security/identity-protection/hello-for-business/hello-how-it-works-authentication).
3. During Windows sign-in, the Microsoft Entra CloudAP plugin requests a Primary Refresh Token (PRT) from Microsoft Entra using the user credentials. It also caches the PRT, which enables cached sign-in when users don't have an internet connection. When users try to access applications, the Microsoft Entra WAM plugin uses the PRT to enable SSO.
4. Microsoft Entra authenticates the user and device, and returns a PRT and an ID token. The ID token includes the following attributes about the user:

    - `sAMAccountName`
    - `netBIOSDomainName`
    - `dnsDomainName`

    These attributes are synced from on-premises AD using Microsoft Entra Connect.

    The Kerberos Authentication Provider receives the credentials and the attributes. On the device, the Windows Local Security Authority (LSA) service enables Kerberos and NTLM authentication.
5. During an access attempt to an on-premises resource requesting Kerberos or NTLM authentication, the device uses the domain name related attributes to find a Domain Controller (DC) using DC Locator.

    - If a DC is found, it sends the credentials and the `sAMAccountName` to the DC for authentication.
    - If using Windows Hello for Business, it does [PKINIT](/en-us/openspecs/windows_protocols/ms-pkca/d0cf1763-3541-4008-a75f-a577fa5e8c5b) with the Windows Hello for Business certificate.
    - If no DC is found, then no on-premises authentication happens.

    Note

    PKINIT is a preauthentication mechanism for Kerberos 5 which uses X.509 certificates to authenticate the Key Distribution Center (KDC) to clients and vice versa.

    [MS-PKCA: Public Key Cryptography for Initial Authentication (PKINIT) in Kerberos Protocol](/en-us/openspecs/windows_protocols/ms-pkca/d0cf1763-3541-4008-a75f-a577fa5e8c5b)
6. The DC authenticates the user. The DC returns a Kerberos Ticket-Granting Ticket (TGT) or an NTLM token based on the protocol that the on-premises resource or application supports. Windows caches the returned TGT or NTLM token for future use.

    If the attempt to get the Kerberos TGT or NTLM token for the domain fails (related DCLocator timeout can cause a delay), then Windows Credential Manager retries. Or, the user may receive an authentication pop-up requesting credentials for the on-premises resource.
7. All apps that use [Windows Integrated Authentication (WIA)](/en-us/aspnet/web-api/overview/security/integrated-windows-authentication) automatically use SSO when a user tries to access the apps. WIA includes standard user authentication to an on-premises AD domain using NTLM or Kerberos when accessing on-premises services or resources.

    For more information, go to [How SSO to on-premises resources works on Microsoft Entra joined devices](/en-us/entra/identity/devices/device-sso-to-on-premises-resources).

    It's important to emphasize the value of Windows Integrated Authentication. Native cloud endpoints simply "work" with any application configured for WIA.

    When users access a resource that uses WIA (file server, printer, web server, etc.), then the TGT is exchanged with a Kerberos service ticket, which is the usual Kerberos workflow.

## Follow the cloud-native endpoints guidance

1. [Overview: What are cloud-native endpoints?](overview)
2. [Tutorial: Set up cloud-native Windows endpoints with Microsoft Intune](tutorial-cloud-native-setup)
3. [Concept: Microsoft Entra joined vs. Hybrid Microsoft Entra joined](entra-join-types)
4. 🡺 **Concept: Cloud-native endpoints and on-premises resources** (*You are here*)
5. [High level planning guide](planning-guide)
6. [Known issues and important information](troubleshoot)

## Helpful online resources

- [Primary Refresh Token (PRT) and Microsoft Entra](/en-us/entra/identity/devices/concept-primary-refresh-token)
- [How SSO to on-premises resources works on Microsoft Entra joined devices](/en-us/entra/identity/devices/device-sso-to-on-premises-resources)
- [How Windows Hello for Business works - Authentication - Windows security](/en-us/windows/security/identity-protection/hello-for-business/hello-how-it-works-authentication)
- [Integrated Windows Authentication](/en-us/aspnet/web-api/overview/security/integrated-windows-authentication)
- [Microsoft Entra Kerberos authentication](/en-us/azure/active-directory/authentication/how-to-authentication-kerberos)
- [Microsoft Entra Authentication overview](/en-us/entra/identity/authentication/overview-authentication)