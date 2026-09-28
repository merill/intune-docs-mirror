---
layout: Conceptual
title: Planning certificate template permissions - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/planning-for-certificate-template-permissions
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
description: Learn about planning for the permissions that you need to configure the certificate templates that Configuration Manager uses.
ms.date: 2022-03-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: de6483ff-fe02-04f7-b5c0-343463eb5b6b
document_version_independent_id: 5204af5b-10a0-56a7-1294-0e801f888423
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/plan-design/planning-for-certificate-template-permissions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/plan-design/planning-for-certificate-template-permissions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/plan-design/planning-for-certificate-template-permissions.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: af79927e-e86a-a5cf-4cd7-1bb9184c497b
---

# Planning certificate template permissions - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in version 2203, this company resource access feature is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](resource-access-deprecation-faq).

The following information can help you plan for how to configure permissions for the certificate templates that Configuration Manager uses when you deploy certificate profiles.

## Default Security Permissions and Considerations

The default security permissions that are required for the certificate templates that Configuration Manager will use to request certificates for users and devices are as follows:

- Read and Enroll for the account that the Network Device Enrollment Service application pool uses
- Read for the account that runs the Configuration Manager console

    For more information about these security permissions, see [Configuring certificate infrastructure](../deploy-use/certificate-infrastructure).

    When you use this default configuration, users and devices can't directly request certificates from the certificate templates and all requests must be initiated by the Network Device Enrollment Service. This is an important restriction, because these certificate templates must be configured with **Supply in the request** for the certificate Subject, which means that there is a risk of impersonation if a rogue user or a compromised device requests a certificate. In the default configuration, the Network Device Enrollment Service must initiate such a request. However, this risk of impersonation remains if the service that runs the Network Device Enrollment Service is compromised. To help avoid this risk, follow all security best practices for the Network Device Enrollment Service and the computer that runs this role service.

    If the default security permissions don't fulfill your business requirements, you have another option for configuring the security permissions on the certificate templates: You can add Read and Enroll permissions for users and computers.

## Adding Read and Enroll Permissions for Users and Computers

Adding Read and Enroll permissions for users and computers might be appropriate if a separate team manages your certification authority (CA) infrastructure team, and that separate team wants Configuration Manager to verify that users have a valid Active Directory Domain Services account before sending them a certificate profile to request a user certificate. For this configuration, you must specify one or more security groups that contain the users, and then grant those groups Read and Enroll permissions on the certificate templates. In this scenario, the CA administrator manages the security control.

You can similarly specify one or more security groups that contain computer accounts and grant these groups Read and Enroll permissions on the certificate templates. If you deploy a computer certificate profile to a computer that is a domain member, the computer account of that computer must be granted Read and Enroll permissions. These permissions aren't required if the computer isn't a domain member. For example, if it's a workgroup computer or personal mobile device.

Although this configuration uses another security control, we don't recommend it as a best practice. The reason is that the specified users or owners of the devices might request certificates independently from Configuration Manager and supply values for the certificate Subject that might be used to impersonate another user or device.

In addition, if you specify accounts that can't be authenticated at the time that the certificate request occurs, the certificate request will fail by default. For example, the certificate request will fail if the server that is running the Network Device Enrollment Service is in an Active Directory forest that is untrusted by the forest that contains the certificate registration point site system server. You can configure the certificate registration point to continue if an account can't be authenticated because there's no response from a domain controller. However, this isn't a security best practice.

If the certificate registration point is configured to check for account permissions and a domain controller is available and rejects the authentication request (for example, the account is locked out or has been deleted), the certificate enrollment request will fail.

#### To check for Read and Enroll permissions for users and domain-member computers

1. On the site system server that hosts the certificate registration point, create the following DWORD registry key to have a value of 0: HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheck
2. If an account can't be authenticated because there's no response from a domain controller, and you want to bypass the permissions check:

    - On the site system server that hosts the certificate registration point, create the following DWORD registry key to have a value of 1: HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\SCCM\CRP\SkipTemplateCheckOnlyIfAccountAccessDenied
3. On the issuing CA, on the **Security** tab in the properties for the certificate template, add one or more security groups to grant the user or device accounts Read and Enroll permissions.