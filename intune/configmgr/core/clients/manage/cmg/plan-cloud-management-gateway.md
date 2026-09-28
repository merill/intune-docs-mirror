---
layout: Conceptual
title: Plan for CMG - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/plan-cloud-management-gateway
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
description: Plan and design the cloud management gateway (CMG) to simplify management of internet-based clients.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
ms.custom: sfi-ga-nochange
locale: en-us
document_id: 07d4e4f7-68ed-e604-b577-2c18617d1c2e
document_version_independent_id: 1ce10bc0-2a6d-405a-a9ae-46adfaac8fe6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/cmg/plan-cloud-management-gateway.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/cmg/plan-cloud-management-gateway
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/cmg/plan-cloud-management-gateway.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/96f6b0a2-2fd7-4de1-936d-89ad6e0eb7cc
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/ef8b0a5a-ba0a-4ec0-8636-48246ccd954f
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
platformId: 725cea70-37d1-52aa-ddbf-a1c829fa10bb
---

# Plan for CMG - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

To simplify management of internet-based clients, first develop a plan for the cloud management gateway (CMG). Design how it fits in your environment and prepare for your implementation.

For more foundational knowledge of CMG scenarios and use cases, see [Overview of CMG](overview).

Note

Some sections that were previously in this article have moved:

- **Hierarchy design**: [CMG hierarchy design](plan-hierarchy-design)
- **Performance and scale**: [CMG performance and scale](perf-scale)

## Planning checklist

The overall CMG planning process is divided into the following parts:

- *Components and requirements*: This article summarizes the components that make up the CMG system. It also lists the system requirements.
- *Client authentication*: Determine which authentication method you'll use for clients from potentially untrusted networks.
- *Hierarchy design*: Plan where to place the CMG in your environment.
- *Supported configurations*: Understand which Configuration Manager features you can support on internet-based clients that connect to the CMG.
- *Performance and scale*: Decide how many service components you'll need to best support your number of clients.
- *Cost*: Understand the cost of the Azure-based components.

## CMG components

Deployment and operation of the CMG includes the following components:

- The **CMG cloud service** in Azure authenticates and forwards Configuration Manager client requests over the internet to the on-premises CMG connection point.
- The **CMG connection point** site system role enables a consistent and high-performance connection from the on-premises network to the CMG service in Azure. It also publishes settings to the CMG including connection information and security settings. The CMG connection point forwards client requests from the CMG to on-premises roles according to URL mappings. For example, the management point and software update point.
- The [**service connection point**](../../../servers/deploy/configure/about-the-service-connection-point) site system role runs the cloud service manager component, which handles all CMG deployment tasks. Additionally, it monitors and reports service health and logging information from Microsoft Entra ID. Make sure your service connection point is in [online mode](../../../servers/deploy/configure/about-the-service-connection-point#bkmk_modes).
- The **management point** and **software update point** site system roles service client requests per normal.
- The CMG uses a **certificate-based HTTPS** web service to help secure network communication with clients.
- **Internet-based clients** connect to the CMG to access on-premises Configuration Manager components. There are multiple options for client identity and authentication:

    - Microsoft Entra ID
    - PKI certificates
    - Configuration Manager site-issued tokens

    For more information, see [Plan for CMG client authentication](plan-client-authentication).
- The CMG creates an **Azure storage account**, which it uses for its standard operations. By default, the CMG is also content-enabled to provide deployment content to internet-based clients. This storage account doesn't support customizations, such as virtual network restrictions.

    Note

    The cloud-based distribution point (CDP) is deprecated. Starting in version 2107, you can't create new CDP instances. To provide content to internet-based devices, enable the CMG to distribute content.

## Azure Resource Manager

You create the CMG using an **Azure Resource Manager deployment**. [Azure Resource Manager](/en-us/azure/azure-resource-manager/resource-group-overview) is a modern platform for managing all solution resources as a single entity, called a [resource group](/en-us/azure/azure-resource-manager/resource-group-overview#resource-groups). When you deploy a CMG with Azure Resource Manager, the site uses Microsoft Entra ID to authenticate and create the necessary cloud resources.

Important

Starting in version 2203, the option to deploy a CMG as a **cloud service (classic)** is removed. All CMG deployments should use a virtual machine scale set. For more information, see [Removed and deprecated features](../../../plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

## Virtual machine scale sets

Note

This feature was first introduced in version 2010 as a [pre-release feature](../../../servers/manage/pre-release-features). Starting in version 2107, it's no longer a pre-release feature.

Configuration Manager doesn't enable this optional feature by default. You must enable this feature before using it. For more information, see [Enable optional features from updates](../../../servers/manage/optional-features).

Starting in version 2010, customers with a Cloud Solution Provider (CSP) subscription can deploy the CMG with a **virtual machine scale set** in Azure. This support is only if they don't currently have a CMG deployed using classic cloud services to another subscription.

Starting in version 2107, all customers can deploy a CMG with a virtual machine scale set. If you have an existing CMG deployed with the classic cloud service, **convert** the CMG to use a virtual machine scale set.

With a few exceptions, the configuration, operation, and functionality of the CMG remains the same.

- Other [Azure resource providers](configure-azure-ad#configure-azure-resource-providers) in your Azure subscription.
- Different deployment names, for example, **GraniteFalls.EastUS.CloudApp.Azure.Com** for a deployment in the **East US** Azure region. This name change can affect how you create and manage the [CMG server authentication certificate](server-auth-cert).
- The CMG connection point only communicates with the virtual machine scale set in Azure over HTTPS. It doesn't require TCP-TLS ports.

### Limitations for a CMG with a virtual machine scale set

#### Limitations with versions 2107 and later

Note

Starting in version 2111, CMG deployments with a virtual machine scale set support Azure US Government cloud environments.

- Users may experience a delay of up to three seconds for actions in Software Center.
- You can't approve/deny application requests through the CMG.
- Version 2107 doesn't support Azure US Government cloud environments.

#### Limitations with versions 2010 and 2103

- If you require more than one CMG instance, they all have to use the same deployment method.
- The supported number of concurrent client connections is 2,000 per VM instance. For more information, see [CMG performance and scale](perf-scale).
- It's only supported with a standalone primary site.
- It doesn't support Azure US Government cloud environments.
- Users may experience a delay of up to three seconds for actions in Software Center.
- Configuration Manager currently creates the Azure storage container based on the name of the resource group. Azure has different naming requirements for resource groups and storage containers. Make sure the name of the resource group for this service only has lowercase letters, numbers, and hyphens. If you have an existing resource group that doesn't work, rename it in the Azure portal, or create a new resource group.
- If you have more than one HTTPS management point, then you can't install the Configuration Manager client on devices over the internet. If you need to [Install off-premises clients using a CMG](configure-clients#install-off-premises-clients-using-a-cmg), then you can only have one HTTPS management point. You also need to enable the CMG for content.
- You can't approve/deny application requests through the CMG.

## Requirements

Tip

To clarify some Azure terminology:

- The Microsoft Entra ID *tenant* is the directory of user accounts and app registrations. One tenant can have multiple subscriptions.
- An Azure *subscription* separates billing, resources, and services. It's associated with a single tenant.

For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](/en-us/microsoft-365/enterprise/subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings).

- An **Azure subscription** to host the CMG. This subscription can be in one of the following environments:

    - Global Azure cloud
    - Azure US Government cloud

    Customers with a Cloud Service Provider (CSP) subscription need to use version 2010 or later with a **virtual machine scale set** deployment.
- Integrate the site with **Microsoft Entra ID** to deploy the service with Azure Resource Manager. For more information, see [Configure Microsoft Entra ID for CMG](configure-azure-ad).

    When you onboard the site to Microsoft Entra ID, you can optionally enable **Microsoft Entra user discovery**. It isn't required to create the CMG, but required if you plan to use Microsoft Entra authentication with hybrid identities. For more information, see [Install clients using Microsoft Entra ID](../../deploy/deploy-clients-cmg-azure) and see [About Microsoft Entra user discovery](../../../servers/deploy/configure/about-discovery-methods#azureaddisc).
- An **Azure administrator** needs to participate in the initial creation of certain components. This persona can be the same as the Configuration Manager administrator, or separate. If separate, they don't require permissions in Configuration Manager.

    - When you integrate the site with Microsoft Entra ID for deploying the CMG using Azure Resource Manager, you need a **Global Administrator**.
    - When you create the CMG, you need an account that is an **[Azure subscription Owner](/en-us/azure/role-based-access-control/built-in-roles#privileged)** and a **[Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator)**.

    Important

    The [Microsoft Entra Global Administrator](/en-us/entra/identity/role-based-access-control/privileged-roles-permissions) role is a highly privileged role and should only be used when another role can't be used. This feature requires the Global Administrator role. For other features, Microsoft recommends using roles with the fewest permissions. To learn more, see [Fundamentals of role-based administration for Configuration Manager](../../../understand/fundamentals-of-role-based-administration).
- Your user account needs to be a **Full administrator** or **Infrastructure administrator** in Configuration Manager.
- At least one on-premises Windows server to host the **CMG connection point**. You can colocate this role with other Configuration Manager site system roles.
- The **service connection point** must be in [online mode](../../../servers/deploy/configure/about-the-service-connection-point#bkmk_modes).
- Configure the **management point** to allow traffic from the CMG. It also needs to require HTTPS, or configure the site for [Enhanced HTTP](../../../plan-design/hierarchy/enhanced-http).
- A [**server authentication certificate**](server-auth-cert) for the CMG.
- CMG names need to be between 3-24 alphanumeric characters. The name must begin with a letter, end with a letter or digit, and not contain consecutive hyphens.
- **Other certificates** may be required, depending upon your client OS version and authentication model. For more information, see [Configure client authentication](configure-authentication).
- Clients must use **IPv4**.
- Make sure the following [client settings](../../deploy/about-client-settings#cloud-services) in the **Cloud services** group are enabled for devices that will use the CMG:

    - **Enable clients to use a cloud management gateway**
    - **Allow access to cloud distribution point**

    Note

    If you enable the client setting to [Download delta content when available](../../deploy/about-client-settings#allow-clients-to-download-delta-content-when-available), the content for third-party updates won't download to clients.