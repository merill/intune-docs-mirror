---
layout: Conceptual
title: Certificate profile prerequisites - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/prerequisites-for-certificate-profiles
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
description: Learn about certificate profiles in Configuration Manager and their external dependencies and dependencies in the product.
ms.date: 2022-03-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 33226d87-6434-a82a-5e8d-75b1ad39be3d
document_version_independent_id: 6d50eaa1-2698-4d12-203e-f8d43b6f5fec
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/plan-design/prerequisites-for-certificate-profiles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/plan-design/prerequisites-for-certificate-profiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/plan-design/prerequisites-for-certificate-profiles.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: 7c84920e-cf26-b31b-56ac-f8b58ce1e485
---

# Certificate profile prerequisites - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Certificate profiles in Configuration Manager have external dependencies and dependencies in the product.

Important

Starting in version 2203, this company resource access feature is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](resource-access-deprecation-faq).

## Dependencies External to Configuration Manager

| Dependency | More information |
| --- | --- |
| An enterprise issuing certification authority (CA) that is running Active Directory Certificate Services (AD CS). To revoke certificates the computer account of the site server at the top of the hierarchy requires *Issue and Manage Certificates* rights for each certificate template used by a certificate profile in Configuration Manager. Alternatively, grant Certificate Manager permissions to grant permissions on all certificate templates used by that CA Manager approval for certificate requests is supported. However, the certificate templates that are used to issue certificates must be configured for **Supply in the request** for the certificate subject so that Configuration Manager can automatically supply this value. | For more information about Active Directory Certificate Services, see [Active Directory Certificate Services Overview](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831740%28v=ws.11%29). |
| Use the PowerShell script to verify, and if needed, install the prerequisites for the Network Device Enrollment Service (NDES) role service and the Configuration Manager Certificate Registration Point. | The instruction file, readme\_crp.txt, is located in ConfigMgrInstallDir\cd.latest\SMSSETUP\POLICYMODULE\X64.The PowerShell script, Test-NDES-CRP-Prereqs.ps1, is in the same directory as the instructions.  The PowerShell script must be run locally on the NDES server. |
| The Network Device Enrollment Service (NDES) role service for Active Directory Certificate Services, running on Windows Server 2012 R2. In addition: Port numbers other than TCP 443 (for HTTPS) or TCP 80 (for HTTP) are not supported for the communication between the client and the Network Device Enrollment Service. The server that is running the Network Device Enrollment Service must be on a different server from the issuing CA. | Configuration Manager communicates with the Network Device Enrollment Service in Windows Server 2012 R2 to generate and verify Simple Certificate Enrollment Protocol (SCEP) requests. If you will issue certificates to users or devices that connect from the Internet, such as mobile devices that are managed by Microsoft Intune, those devices must be able to access the server that runs the Network Device Enrollment Service from the Internet. For example, install the server in a perimeter network (also known as a DMZ, demilitarized zone, and screened subnet). If you have a firewall between the server that is running the Network Device Enrollment Service and the issuing CA, you must configure the firewall to allow the communication traffic (DCOM) between the two servers. This firewall requirement also applies to the server running the Configuration Manager site server and the issuing CA, so that Configuration Manager can revoke certificates. If the Network Device Enrollment Service is configured to require SSL, a security best practice is to make sure that connecting devices can access the certificate revocation list (CRL) to validate the server certificate. For more information about the Network Device Enrollment Service, see [Using a Policy Module with the Network Device Enrollment Service](/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn473016%28v=ws.11%29). |
| A PKI client authentication certificate and exported root CA certificate. | This certificate authenticates the server that is running the Network Device Enrollment Service to Configuration Manager. For more information, see [PKI certificate requirements for Configuration Manager](../../core/plan-design/network/pki-certificate-requirements). |
| Supported device operating systems. | You can deploy certificate profiles to devices that run Windows 8.1, Windows RT 8.1, and Windows 10. |

## Configuration Manager Dependencies

| Dependency | More information |
| --- | --- |
| Certificate registration point site system role | Before you can use certificate profiles, you must install the certificate registration point site system role. This role communicates with the Configuration Manager database, the Configuration Manager site server, and the Configuration Manager Policy Module. For more information about system requirements for this site system role and where to install the role in the hierarchy, see the **Site System Requirements** section in the [Supported configurations for Configuration Manager](../../core/plan-design/configs/supported-configurations) article. The certificate registration point must not be installed on the same server that runs the Network Device Enrollment Service. |
| Configuration Manager Policy Module that is installed on the server that is running the Network Device Enrollment Service role service for Active Directory Certificate Services | To deploy certificate profiles, you must install the Configuration Manager Policy Module. You can find this policy module on the Configuration Manager installation media. |
| Discovery data | Values for the certificate subject and the subject alternative name are supplied by Configuration Manager and retrieved from information that is collected from discovery: For user certificates: Active Directory User Discovery For computer certificates: Active Directory System Discovery and Network Discovery |
| Specific security permissions to manage certificate profiles | You must have the following security permissions to manage company resource access settings, such as certificate profiles, Wi-Fi profiles, and VPN profiles: To view and manage alerts and reports for certificate profiles: **Create**, **Delete**, **Modify**, **Modify Report**, **Read**, and **Run Report** for the **Alerts** object. To create and manage certificate profiles: **Author Policy**, **Modify Report**, **Read**, and **Run Report** for the **Certificate Profile** object. To manage Wi-Fi, certificate and VPN profile deployments: **Deploy Configuration Policies**, **Modify Client Status Alert**, **Read**, and **Read Resource** for the **Collection** object. To manage all configuration policies: **Create**, **Delete**, **Modify**, **Read**, and **Set Security Scope** for the **Configuration Policy** object. To run queries related to certificate profiles: **Read** permission for the **Query** object. To view certificate profiles information in the Configuration Manager console: **Read** permission for the **Site** object. To view status messages for certificate profiles: **Read** permission for the **Status Messages** object. To create and modify the Trusted CA certificate profile: **Author Policy**, **Modify Report**, **Read**, and **Run Report** for the **Trusted CA Certificate Profile** object. To create and manage VPN profiles: **Author Policy**, **Modify Report**, **Read**, and **Run Report** for the **VPN Profile** object. To create and manage Wi-Fi profiles: **Author Policy**, **Modify Report**, **Read**, and **Run Report** for the **Wi-Fi Profile** object. The **Company Resource Access Manager** security role includes these permissions that are required to manage certificate profiles in Configuration Manager. For more information, see the **Configure role-based administration** section in the [Configure security](../../core/plan-design/security/configure-security) article. |