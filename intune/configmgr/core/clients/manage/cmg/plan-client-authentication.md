---
layout: Conceptual
title: CMG client authentication - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/plan-client-authentication
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
description: Plan for how clients authenticate to the cloud management gateway (CMG).
ms.date: 2021-08-02T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: f3cfa38b-3970-3565-d3f9-058963e6fc37
document_version_independent_id: 9d14699e-3e42-8b3a-5f02-aa7f1013e626
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/cmg/plan-client-authentication.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/cmg/plan-client-authentication
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/cmg/plan-client-authentication.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: e31b91e5-7f8b-e947-ca74-2f6cde88be0e
---

# CMG client authentication - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Clients that connect to a cloud management gateway (CMG) are potentially on the untrusted public internet. Because of the client's origin, they have a higher authentication requirement. There are three options for identity and authentication with a CMG:

- Microsoft Entra ID
- PKI certificates
- Configuration Manager site-issued tokens

The following table summarizes the key factors for each method:

| - | Microsoft Entra ID | PKI certificate | Site token |
| --- | --- | --- | --- |
| **ConfigMgr version** | All supported | All supported | All supported |
| **Windows client version** | Windows 10 or later | All supported | All supported |
| **Scenario support** | User and device | Device-only | Device-only |
| **Management point** | E-HTTP or HTTPS | E-HTTP or HTTPS | E-HTTP or HTTPS |

Microsoft recommends joining devices to Microsoft Entra ID. Internet-based devices can use Microsoft Entra modern authentication with Configuration Manager. It also enables both device and user scenarios whether the device is on the internet or connected to the internal network.

You can use one or more methods. All clients don't have to use the same method.

Which ever method you choose, you may also need to reconfigure one or more management points. For more information, see [Configure client authentication for CMG](configure-authentication#enable-management-point-for-https).

## Microsoft Entra ID

If your internet-based devices are running Windows 10 or later, consider using Microsoft Entra modern authentication with the CMG. This authentication method is the only one that enables user-centric scenarios. For example, deploying apps to a user collection.

First, the devices need to be either cloud domain-joined or Microsoft Entra hybrid joined, and the user also needs a Microsoft Entra identity. If your organization is already using Microsoft Entra identities, then you should be set with this prerequisite. If not, talk with your Azure administrator to plan for cloud-based identities. For more information, see [Microsoft Entra device identity](/en-us/azure/active-directory/devices/). Until that process is complete, consider token-based authentication for internet-based clients with your CMG.

There are a few other requirements, depending upon your environment:

- Enable user discovery methods for hybrid identities
- Enable ASP.NET 4.5 on the management point
- Configure client settings

For more information on these prerequisites, see [Install clients using Microsoft Entra ID](../../deploy/deploy-clients-cmg-azure).

Note

If your devices are in a Microsoft Entra tenant that's separate from the tenant with a subscription for the CMG compute resources, starting in version 2010 you can disable authentication for tenants not associated with users and devices. For more information, see [Configure Azure services](../../../servers/deploy/configure/azure-services-wizard#disable-authentication).

## PKI certificate

If you have a public key infrastructure (PKI) that can issue client authentication certificates to devices, then consider this authentication method for internet-based devices with your CMG. It doesn't support user-centric scenarios, but supports devices running any supported version of Windows.

Tip

Windows devices that are hybrid or cloud domain-joined don't require this certificate because they use Microsoft Entra ID to authenticate.

This certificate may also be required on the CMG connection point.

## Site token

If you can't join devices to Microsoft Entra ID or use PKI client authentication certificates, then use Configuration Manager token-based authentication. Site-issued client authentication tokens work on all supported client OS versions, but only support device scenarios.

If clients occasionally connect to your internal network, they're automatically issued a token. They need to communicate directly with an on-premises management point to register with the site and get this client token.

If you can't register clients on the internal network, you can create and deploy a bulk registration token. The bulk registration token enables the client to initially install and communicate with the site. This initial communication is long enough for the site to issue the client its own, unique client authentication token. The client then uses its authentication token for all communication with the site while it's on the internet.