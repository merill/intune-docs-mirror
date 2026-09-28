---
layout: Conceptual
title: Support for Active Directory domains - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/support-for-active-directory-domains
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
description: Learn about the requirements for a Configuration Manager site system in an Active Directory domain.
ms.date: 2019-10-22T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: c8831f24-3e8d-6f9d-66bc-3b22e296dd28
document_version_independent_id: 221f3393-0ce1-ef40-0aad-09c1778e1922
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/configs/support-for-active-directory-domains.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/configs/support-for-active-directory-domains
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/configs/support-for-active-directory-domains.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
platformId: da0e0ef2-7c9b-df30-e1ec-42f6547101a9
---

# Support for Active Directory domains - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

All Configuration Manager site systems must be members of a supported Active Directory domain. Configuration Manager client computers can be domain members or workgroup members.

## Requirements and limitations

- Domain membership also applies to site systems that support internet-based client management in a perimeter network. (These networks are also known as a DMZ, demilitarized zone, and screened subnet).
- It's not supported to change the following configurations for a computer that hosts a site system role:

    - Domain membership, including if you remove a site system from the domain, and then rejoin the same domain.
    - Domain name
    - Computer name

    Before making these changes, uninstall the site system role. To make these changes to a site server, uninstall the site first. You can also consider creating a [site server in passive mode](../../servers/deploy/configure/site-server-high-availability) to help manage this change on a site server.
- Configuration Manager supports domain and forest functional level of Windows Server 2008 R2 or later.

## Disjoint namespace

You can install Configuration Manager site systems and clients in a domain that has a *disjoint namespace*.

In a disjoint namespace, the primary DNS suffix of a computer doesn't match the Active Directory DNS domain name of that computer. Another disjoint namespace scenario occurs if the NetBIOS domain name of a domain controller doesn't match the Active Directory DNS domain name.

### Disjoint scenarios

The following sections identify the supported scenarios for a disjoint namespace.

#### Scenario 1

The primary DNS suffix of the domain controller differs from the Active Directory DNS domain name. Computers that are members of the domain can be either disjoint or not disjoint.

The domain controller is disjoint in this scenario. Computers that are members of the domain, such as site servers and computers, can have a primary DNS suffix that either matches:

- The primary DNS suffix of the domain controller
- The Active Directory DNS domain name

#### Scenario 2

A member computer in an Active Directory domain is disjoint, even though the domain controller isn't disjoint.

In this scenario, the primary DNS suffix of a site system differs from the Active Directory DNS domain name. The primary DNS suffix of the domain controller is the same as the Active Directory DNS domain name. Member computers that are Configuration Manager clients can have a primary DNS suffix that either matches:

- The primary DNS suffix of the disjoint site system server
- The Active Directory DNS domain name

### Configure disjoint namespace

To allow a computer to access domain controllers that are disjoint, change the **msDS-AllowedDNSSuffixes** Active Directory attribute on the domain object container. Add both DNS suffixes to the attribute.

To make sure that the *DNS suffix search list* contains all the DNS namespaces in the organization, configure the search list for each computer in the disjoint domain. Include the following suffixes in the list of namespaces:

- The primary DNS suffix of the domain controller
- The DNS domain name
- Any additional namespaces for other servers that Configuration Manager might communicate with

You can use group policy to configure the **Domain Name System (DNS) suffix search** list.

Important

When you reference a computer in Configuration Manager, enter the computer by using its primary DNS suffix. This suffix should match the fully qualified domain name that's registered as the **dnsHostName** attribute in the Active Directory domain and the service principal name that's associated with the system.

## Single label domains

Configuration Manager supports site systems and clients in a single label domain when the following criteria are met:

- Configure the single label domain in Active Directory Domain Services with a disjoint DNS namespace that has a valid top-level domain.

    **For example:** The single label domain of Contoso is configured to have a disjoint namespace in DNS of contoso.com. When you specify the DNS suffix in Configuration Manager for a computer in the Contoso domain, you specify "Contoso.com" and not "Contoso".
- The distributed component object model (DCOM) connections between site servers in the system context must be successful by using Kerberos authentication.