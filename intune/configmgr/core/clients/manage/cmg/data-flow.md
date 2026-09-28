---
layout: Conceptual
title: Data flow for CMG - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/cmg/data-flow
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
description: Understand how data flows between components of the cloud management gateway (CMG), including network ports and internet endpoints.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 47475d69-7187-22d4-fe47-874a7a74df82
document_version_independent_id: ff5c3e09-2bbd-50bf-387d-ef8becb67b99
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/cmg/data-flow.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/cmg/data-flow
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/cmg/data-flow.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/1ae5c491-970a-4062-8301-6336e69f9026
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/f2c3e52e-3667-4e8a-bf11-20b9eaccdc8c
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
platformId: 067eff10-120d-c38d-ec4f-a1b74afe01b6
---

# Data flow for CMG - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use this article to understand how data flows between components of the cloud management gateway (CMG). It requires specific network ports and internet endpoints to function. You don't need to open any inbound ports to your on-premises network. The service connection point and CMG connection point site system roles start all communication with Azure and the CMG. These two roles need to create outbound connections to the Microsoft cloud. The service connection point deploys and monitors the service in Azure, so needs to be online. The CMG connection point connects to the CMG to manage communication between the CMG and on-premises site system roles.

## Data flow diagram

The following diagram is a basic, conceptual data flow for the CMG:

![Data flow diagram for cloud management gateway (CMG).](media/cmg-data-flow.svg)

1. The service connection point connects to Azure over HTTPS port 443. It authenticates using Microsoft Entra ID. The service connection point deploys the CMG in Azure. The CMG creates the HTTPS service using the server authentication certificate.
2. The CMG connection point connects to the CMG in Azure. It holds the connection open, and builds the channel for future two-way communication.

    - When you deploy the CMG as a virtual machine scale set, this flow is over HTTPS.
    - If you deploy the CMG as a classic cloud service, it first tries TCP-TLS. If that connection fails, it switches to HTTPS.

    For more information, see Note 2: CMG connection point HTTPS ports for one VM.
3. The client connects to the CMG over HTTPS port 443. It authenticates using Microsoft Entra ID, the client authentication certificate, or a site-issued token.

    Note

    If you enable the CMG to serve content, the client connects directly to Azure blob storage over HTTPS port 443. For more information, see Content data flow.
4. The CMG forwards the client communication over the existing connection to the on-premises CMG connection point. You don't need to open any inbound firewall ports.
5. The CMG connection point forwards the client communication to the on-premises management point and software update point.

For more information when you integrate with Microsoft Entra ID, see [Configure Azure services: Cloud management data flow](../../../servers/deploy/configure/azure-services-wizard#cloud-management-data-flow).

### Content data flow

When a client uses a CMG as a content location:

1. The management point gives the client an access token along with the list of content sources. This token is valid for 24 hours, and gives the client access to the cloud-based content source.
2. The management point responds to the client's location request with the *service name* of the CMG. This property is the same as the common name of the server authentication certificate.

    If you're using your domain name, for example, `WallaceFalls.contoso.com`, then the client first tries to resolve this FQDN. Clients use the CNAME alias in your domain's internet-facing DNS to resolve the Azure deployment name.
3. The client next resolves the *deployment name* to a valid IP address. This response is handled by Azure's DNS.
4. The client connects to the CMG. Azure load balances the connection to one of the VM instances. The client authenticates itself using the access token.
5. The CMG authenticates the client's access token, and then gives the client the exact content location in Azure storage.
6. If the client trusts the CMG's server authentication certificate, it connects to Azure storage to download the content.

When distributing content to CMG:

1. SMS\_DISTRIBUTION\_MANAGER (Distmgr) Creates request to distribute content to CMG.
2. SMS\_PACKAGE\_TRANSFER\_MANAGER (PkgXfermgr) gets send request and starts upload process by copying the package to Temp share location.
3. SMS\_PACKAGE\_TRANSFER\_MANAGER (PkgXfermgr) acquires access token for CMG storage.
4. SMS\_PACKAGE\_TRANSFER\_MANAGER (PkgXfermgr) uploads content to CMG storage.

## Required ports

This table lists the required network ports and protocols. The *Client* is the device that starts the connection, requiring an outbound port. The *Server* is the device that accepts the connection, requiring an inbound port.

| Client | Protocol | Port | Server | Description |
| --- | --- | --- | --- | --- |
| Service connection point | HTTPS | 443 | Azure | CMG deployment |
| CMG connection point (virtual machine scale set) | HTTPS | 443 | CMG service | Protocol to build CMG channel to only one VM instance ^Note 2^ |
| CMG connection point (virtual machine scale set) | HTTPS | 10124-10139 | CMG service | Protocol to build CMG channel to two or more VM instances ^Note 3^ |
| CMG connection point (classic cloud service) | TCP-TLS | 10140-10155 | CMG service | Preferred protocol to build CMG channel ^Note 1^ |
| CMG connection point (classic cloud service) | HTTPS | 443 | CMG service | Fall back protocol to build CMG channel to only one VM instance ^Note 2^ |
| CMG connection point (classic cloud service) | HTTPS | 10124-10139 | CMG service | Fall back protocol to build CMG channel to two or more VM instances ^Note 3^ |
| Client | HTTPS | 443 | CMG | General client communication |
| Client | HTTPS | 443 | Blob storage | Download cloud-based content |
| CMG connection point | HTTPS or HTTP | 443 or 80 | Management point | On-premises traffic, port depends upon management point configuration |
| CMG connection point | HTTPS or HTTP | 443 or 80 / 8530 or 8531 | Software update point | On-premises traffic, port depends upon software update point configuration |
| Site Server | HTTPS | 443 | Blob storage | Distributing content to CMG |

### Notes on ports

#### Note 1: CMG connection point TCP-TLS ports

These ports only apply when you deploy the CMG as a **cloud service (classic)**, which was the only method available in version 2006 and earlier.

The CMG connection point first tries to establish a long-lived TCP-TLS connection with each CMG VM instance. It connects to the first VM instance on port 10140. The second VM instance uses port 10141, up to the 16th on port 10155. A TCP-TLS connection has the best performance, but it doesn't support internet proxy. If the CMG connection point can't connect via TCP-TLS, then it falls back to HTTPS^Note 2^.

#### Note 2: CMG connection point HTTPS ports for one VM

If you deploy the CMG in a **virtual machine scale set**, the CMG connection point only communicates with the service in Azure over HTTPS. It doesn't require TCP-TLS ports to build the CMG communication channel.

For a CMG deployed as a classic cloud service, it only uses this port if the TCP-TLS connection fails. If the CMG connection point can't connect to the CMG via TCP-TLS^Note 1^, it connects to the Azure network load balancer over HTTPS 443. This behavior is only for one VM instance.

#### Note 3: CMG connection point HTTPS ports for two or more VMs

If there are two or more VM instances, the CMG connection point uses HTTPS 10124 to the first VM instance, not HTTPS 443. It connects to the second VM instance on HTTPS 10125, up to the 16th on HTTPS port 10139.

## Internet access requirements

If your organization restricts network communication with the internet using a firewall or proxy device, you need to allow the CMG connection point and service connection point to access internet endpoints.

For more information, see [Internet access requirements](../../../plan-design/network/internet-endpoints#cloud-services).

This section covers the following features:

- Cloud management gateway (CMG)
- Microsoft Entra integration
- Microsoft Entra ID-based discovery
- Cloud distribution point (CDP)

    Note

    The cloud-based distribution point (CDP) is deprecated. Starting in version 2107, you can't create new CDP instances. To provide content to internet-based devices, enable the CMG to distribute content.

The following sections list the endpoints by role. Some endpoints refer to a service by `<prefix>`, which is the prefix name of the CMG. For example, if your CMG is `GraniteFalls.WestUS.CloudApp.Azure.Com`, then the actual storage endpoint is `GraniteFalls.blob.core.windows.net`.

Tip

To clarify some terminology:

- CMG *service name*: The common name (CN) of the CMG server authentication certificate. Clients and the CMG connection point site system role communicate with this service name. For example, `GraniteFalls.contoso.com` or `GraniteFalls.WestUS.CloudApp.Azure.Com`.
- CMG *deployment name*: The first part of the service name plus the Azure location for the cloud service deployment. The cloud service manager component of the service connection point uses this name when it deploys the CMG in Azure. The deployment name is always in an Azure domain. The Azure location depends upon the deployment method, for example:

    - Virtual machine scale set: `GraniteFalls.WestUS.CloudApp.Azure.Com`
    - Classic deployment: `GraniteFalls.CloudApp.Net`

This article uses examples with a virtual machine scale set as the recommended deployment method in version 2107 and later. If you use a classic deployment, note the difference as you read this article and configure internet access.

### Service connection point for cloud services

For Configuration Manager to deploy the CMG service in Azure, the service connection point needs access to:

- Specific Azure endpoints, which are different per environment depending upon the configuration. Configuration Manager stores these endpoints in the site database. Query the **AzureEnvironments** table in SQL Server for the list of Azure endpoints.
- Azure services:

    - `management.azure.com` (Azure public cloud)
    - `management.usgovcloudapi.net` (Azure US Government cloud)
- For Microsoft Entra user discovery: Microsoft Graph endpoint `https://graph.microsoft.com/`

### CMG connection point for cloud services

The CMG connection point needs access to the following endpoints:

| Type | Azure public cloud | Azure US Government cloud |
| --- | --- | --- |
| *Service* name | `<prefix>.<region>.cloudapp.azure.com` | `<prefix>.usgovcloudapp.net` |
| Storage endpoint 1 | `<prefix>.blob.core.windows.net` | `<prefix>.blob.core.usgovcloudapi.net` |
| Storage endpoint 2 | `<prefix>.table.core.windows.net` | `<prefix>.table.core.usgovcloudapi.net` |
| Key vault | `<prefix>.vault.azure.net` | `<prefix>.vault.usgovcloudapi.net` |

The CMG connection point site system supports using a web proxy. For more information on configuring this role for a proxy, see [Proxy server support](../../../plan-design/network/proxy-server-support#configure-the-proxy-for-a-site-system-server).

The CMG connection point only needs to connect to the CMG service endpoints. It doesn't need access to other Azure endpoints.

### Configuration Manager client for cloud services

Any Configuration Manager client that needs to communicate with a CMG needs access to the following endpoints:

| Type | Azure public cloud | Azure US Government cloud |
| --- | --- | --- |
| *Deployment* name | `<prefix>.<region>.cloudapp.azure.com` | `<prefix>.usgovcloudapp.net` |
| Storage endpoint | `<prefix>.blob.core.windows.net` | `<prefix>.blob.core.usgovcloudapi.net` |
| Microsoft Entra endpoint | `login.microsoftonline.com` | `login.microsoftonline.us` |

### Configuration Manager console for cloud services

Any device with the Configuration Manager console needs access to the following endpoints:

| Type | Azure public cloud | Azure US Government cloud |
| --- | --- | --- |
| Microsoft Entra endpoints | `login.microsoftonline.com``aadcdn.msauth.net``aadcdn.msftauth.net` | `login.microsoftonline.us` |

## HTTP headers and verbs

Any networking device that manages communication between the client, the CMG, and the on-premises site systems has to allow the following HTTP headers and verbs. If these items are blocked, it will affect client communication through the CMG.

### HTTP headers

- Range:
- CCMClientID:
- CCMClientIDSignature:
- CCMClientTimestamp:
- CCMClientTimestampsSignature:

### HTTP verbs

- HEAD
- CCM\_POST
- BITS\_POST
- GET
- PROPFIND