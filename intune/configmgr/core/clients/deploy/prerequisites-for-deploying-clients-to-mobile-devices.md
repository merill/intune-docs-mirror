---
layout: Conceptual
title: Mobile device client prerequisites - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/prerequisites-for-deploying-clients-to-mobile-devices
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
description: Learn about the prerequisites for deploying the Configuration Manager client to mobile devices.
ms.date: 2022-01-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 60b754c5-6295-5de8-3b60-73c12b2c26a1
document_version_independent_id: 2db3a54e-8f2f-f774-0312-8700196c8d91
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/prerequisites-for-deploying-clients-to-mobile-devices.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/prerequisites-for-deploying-clients-to-mobile-devices
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/prerequisites-for-deploying-clients-to-mobile-devices.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/7cbaac1e-1137-4825-819f-cd751d73c036
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/eda7d4a5-11e2-4d6f-b379-0d496f2a17a5
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: 4053f343-f097-54d7-4096-47f6cda01dca
---

# Mobile device client prerequisites - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

On-premises MDM and the Configuration Manager client for macOS are both [deprecated](../../plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

Migrate management of macOS and mobile devices to Microsoft Intune. For more information, see [Supported clients and devices](../../plan-design/configs/supported-operating-systems-for-clients-and-devices#mac-computers).

Deploying Configuration Manager clients in your environment has the following external dependencies and dependencies within the product.

For more information on the minimum hardware and OS requirements for the Configuration Manager client, see [Supported configurations](../../plan-design/configs/supported-configurations).

Note

The software version numbers shown in this article only list the minimum version numbers required.

When you install the Configuration Manager client on mobile devices and enroll them, use this information to determine the prerequisites.

## Dependencies external to Configuration Manager

- A Microsoft enterprise certification authority (CA) with certificate templates to deploy and manage the certificates required for mobile devices.

    The issuing CA must automatically approve certificate requests from the mobile device users during the enrollment process.

    For more information about the certificate requirements, see [Security and privacy for certificate profiles](../../../protect/plan-design/security-and-privacy-for-certificate-profiles).
- A security group that contains the users that can enroll their mobile devices.

    This security group is used to configure the certificate template that is used during mobile device enrollment.
- Optional but recommended: a DNS alias (CNAME record) named **ConfigMgrEnroll**. Configure this alias for the server name of the enrollment proxy point.

    This DNS alias is required to support automatic discovery for the enrollment service. If you don't configure this DNS record, users must manually specify the name of the enrollment proxy point as part of the enrollment process.
- Site system role dependencies for the computers that run the enrollment point and the enrollment proxy point.

    For more information, see [Supported operating systems for site system servers](../../plan-design/configs/supported-operating-systems-for-site-system-servers).

## Configuration Manager dependencies

For more information, see [Determine the site system roles for clients](plan/determine-the-site-system-roles-for-clients).

- Management point configurations:

    - HTTPS client connections
    - Enabled for mobile devices
    - An internet FQDN
    - Accept client connections from the internet
- Enrollment point and enrollment proxy point

    An enrollment proxy point manages enrollment requests from mobile devices and the enrollment point completes the enrollment process. The enrollment point must be in the same Active Directory forest as the site server, but the enrollment proxy point can be in another forest.
- Client settings for mobile device enrollment

    Configure client settings to allow users to enroll mobile devices and configure at least one enrollment profile.
- Reporting services point

    The reporting services point is an optional, but recommended site system role. It can display reports related to mobile device enrollment and client management. For more information, see [Introduction to reporting](../../servers/manage/introduction-to-reporting).
- To configure enrollment for mobile devices, your account needs the following security permissions:

    - To add, modify, and delete the enrollment site system roles: **Modify** permission for the **Site** object.
    - To configure client settings for enrollment: Default client settings require **Modify** permission for the **Site** object, and custom client settings require **Client agent** permissions.

    The **Full Administrator** default security role includes the required permissions to configure the enrollment site system roles.
- To manage enrolled mobile devices, your account needs the following security permissions:

    - To wipe or retire a mobile device: **Delete resource** for the **Collection** object.
    - To cancel a wipe or retire command: **Delete resource** for the **Collection** object.
    - To allow and block mobile devices: **Modify resource** for the **Collection** object.
    - To remote lock, or reset the passcode on a mobile device: **Modify** resource for the **Collection** object.

    The **Operations Administrator** default security role includes the required permissions to manage mobile devices.

For more information about how to configure security permissions, see [Fundamentals of role-based administration](../../understand/fundamentals-of-role-based-administration) and [Configure role-based administration](../../servers/deploy/configure/configure-role-based-administration).

## Firewall requirements

Intervening network devices such as routers and firewalls, and Windows Firewall if applicable, must allow the traffic associated with mobile device enrollment.

- Between mobile devices and the enrollment proxy point: HTTPS (by default, TCP 443)
- Between the enrollment proxy point and the enrollment point: HTTPS (by default, TCP 443)

If you use a proxy web server, configure it for SSL tunneling. SSL bridging isn't supported for mobile devices.