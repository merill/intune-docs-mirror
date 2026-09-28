---
layout: Conceptual
title: Internet access requirements - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/internet-endpoints
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
description: Learn about the internet endpoints to allow for full functionality of Configuration Manager features.
ms.date: 2026-06-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 4a9e88a5-bc7d-4982-4564-ceea80bde0e7
document_version_independent_id: 817824fe-5b44-ebeb-75c4-9eeb2dfa13ce
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/network/internet-endpoints.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/network/internet-endpoints
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/network/internet-endpoints.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
platformId: 47ccf54f-0b77-2da3-78ad-e793ecc36619
---

# Internet access requirements - Configuration Manager | Microsoft Learn

Some Configuration Manager features rely on internet connectivity for full functionality. If your organization restricts network communication with the internet using a firewall or proxy device, make sure to allow these endpoints.

Configuration Manager uses the following Microsoft URL forwarding services throughout the product:

- `https://aka.ms`
- `https://go.microsoft.com`

Even if they're not explicitly listed in the following sections, you should always allow these endpoints.

## Service connection point

For more information, see [About the service connection point](../../servers/deploy/configure/about-the-service-connection-point).

These configurations apply to the server that hosts the service connection point and any firewalls between that server and the internet. Allow communication through outgoing HTTPS port **TCP 443** to the internet locations.

The service connection point supports using a web proxy with or without authentication to use these locations. For more information, see [Proxy server support](proxy-server-support).

If the Configuration Manager site fails to connect to required endpoints for a cloud service, it raises a critical status message ID 11488. When it can't connect to the service, the SMS\_SERVICE\_CONNECTOR component status changes to critical. View detailed status in the [Component Status](../../servers/manage/use-status-system#monitor-the-status-system) node of the Configuration Manager console.

Starting in version 2010, the service connection point validates important internet endpoints for [tenant attach](internet-endpoints#tenant-attach). These checks help make sure that the cloud-connected services are available. It also helps you troubleshoot issues by quickly determining if network connectivity is a problem. For more information, see [Validate internet access](../../servers/deploy/configure/about-the-service-connection-point#validate-internet-access).

The specific URLs required by the service connection point vary by Configuration Manager feature:

- [Updates and servicing](internet-endpoints#updates-and-servicing)
- [Windows servicing](internet-endpoints#windows-servicing)
- [Azure services](internet-endpoints#azure-services)
- [Microsoft Store for Business](internet-endpoints#microsoft-store-for-business)
- [Cloud services](internet-endpoints#cloud-services)
- [Configuration Manager console](internet-endpoints#configuration-manager-console)
- [Tenant attach](internet-endpoints#tenant-attach)
- [External notifications](internet-endpoints#external-notifications)

Tip

The service connection point uses the Microsoft Intune service when it connects to `go.microsoft.com` or `manage.microsoft.com`. There's a known issue in which the Intune connector experiences connectivity issues if the Baltimore CyberTrust Root Certificate isn't installed, is expired, or is corrupted on the service connection point. For more information, see [Service connection point doesn't download updates](/en-us/troubleshoot/mem/configmgr/service-connection-point-not-download-updates).

## Updates and servicing

For more information, see [Updates and servicing](../../servers/manage/updates).

Tip

Enable these endpoints for the [management insight](../../servers/manage/management-insights) rule, **Connect the site to the Microsoft cloud for Configuration Manager updates**.

- `*.akamaiedge.net`
- `*.akamaitechnologies.com`
- `*.manage.microsoft.com`
- `go.microsoft.com`
- `download.microsoft.com`
- `download.windowsupdate.com`
- `download.visualstudio.microsoft.com`
- `definitionupdates.microsoft.com`

Note

Starting March 2025, the **configmgrbits.azureedge.net** domain migrates to **configmgrbits.cdn.manage.microsoft.com**. No action is required if \*.manage.microsoft.com traffic is already allowed.

- `configmgrbits.azureedge.net`
- `configmgrbits.cdn.manage.microsoft.com`

    Important

    This Azure endpoint only supports TLS 1.2 with specific cipher suites. Make sure your environment supports these Azure configurations. For more information, see [Azure Front Door: TLS configuration FAQ](/en-us/azure/frontdoor/front-door-faq#tls-configuration).
- `cmbitsstore.blob.core.windows.net`
- `ceuswatcab01.blob.core.windows.net`
- `ceuswatcab02.blob.core.windows.net`
- `eaus2watcab01.blob.core.windows.net`
- `eaus2watcab02.blob.core.windows.net`
- `weus2watcab01.blob.core.windows.net`
- `weus2watcab02.blob.core.windows.net`
- `cmbitsstore.blob.core.windows.net`
- `umwatsonc.events.data.microsoft.com`
- `*-umwatsonc.events.data.microsoft.com`

## Windows servicing

For more information, see [Manage Windows as a service](../../../osd/deploy-use/manage-windows-as-a-service).

- `download.microsoft.com`
- `https://go.microsoft.com/fwlink/?LinkID=619849`
- `dl.delivery.mp.microsoft.com`

## Azure services

For more information, see [Configure Azure services for use with Configuration Manager](../../servers/deploy/configure/azure-services-wizard).

- `management.azure.com` (Azure public cloud)
- `management.usgovcloudapi.net` (Azure US Government cloud)

## Co-management

If you enroll Windows devices to Microsoft Intune for co-management, make sure those devices can access the endpoints required by Intune. For more information, see [Network endpoints for Microsoft Intune](/en-us/mem/fundamentals/endpoints).

## Microsoft Store for Business

If you integrate Configuration Manager with the [Microsoft Store for Business](../../../apps/deploy-use/manage-apps-from-the-windows-store-for-business), make sure the service connection point and targeted devices can access the cloud service. For more information, see [Microsoft Store for Business proxy configuration](/en-us/mem/fundamentals/endpoints).

## Delivery optimization

If you use delivery optimization, clients need to communicate with its cloud service: `*.do.dsp.mp.microsoft.com`

Distribution points that support Microsoft Connected Cache also require these endpoints.

For more information, see the following articles:

- [Delivery optimization FAQ](/en-us/windows/deployment/update/waas-delivery-optimization#frequently-asked-questions)
- [Fundamental concepts for content management in Configuration Manager](../hierarchy/fundamental-concepts-for-content-management#delivery-optimization)
- [Microsoft Connected Cache with Configuration Manager](../hierarchy/microsoft-connected-cache)

## Cloud services

For more information on the cloud management gateway (CMG), see [Plan for CMG](../../clients/manage/cmg/data-flow).

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

The CMG connection point site system supports using a web proxy. For more information on configuring this role for a proxy, see [Proxy server support](proxy-server-support#configure-the-proxy-for-a-site-system-server).

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

## Management point
Starting in version 2603, the management point requires internet access to validate Microsoft Entra tokens using Microsoft Identity Service Essentials (MISE). This requirement applies to environments that support Microsoft Entra joined users and devices, especially when using a cloud management gateway (CMG). 
Allow the management point server to access the following endpoints:

**Azure public cloud:**

- `https://login.microsoftonline.com`
- `https://sts.windows.net`

**Azure US Government cloud:**

- `https://login.microsoftonline.us`
- `https://sts.windows.net`

If the management point connects to the internet through a proxy, you must configure the proxy in the system (Local System) context. A proxy set in the site system properties or a WinHTTP-only proxy isn't used for this validation path in version 2603. For the required steps, see [Proxy server support for the management point](proxy-server-support#management-point).

For more information, see [Management point requires internet access for Microsoft Entra token validation](../changes/whats-new-in-version-2603#management-point-requires-internet-access-for-microsoft-entra-token-validation).

## Software updates

Allow the active software update point to access the following endpoints so that WSUS and Automatic Updates can communicate with the Microsoft Update cloud service:

- `http://windowsupdate.microsoft.com`
- `http://*.windowsupdate.microsoft.com`
- `https://*.windowsupdate.microsoft.com`
- `http://*.update.microsoft.com`
- `https://*.update.microsoft.com`
- `http://*.windowsupdate.com`
- `http://download.windowsupdate.com`
- `http://download.microsoft.com`
- `http://*.download.windowsupdate.com`
- `http://ntservicepack.microsoft.com`

For more information on software updates, see [Plan for software updates](../../../sum/plan-design/plan-for-software-updates).

### Intranet firewall

You might need to add endpoints to a firewall that's between two site systems in the following cases:

- If child sites have a software update point
- If there's a remote active internet-based software update point at a site

#### Software update point on the child site

- `http://<FQDN for software update point on child site>`
- `https://<FQDN for software update point on child site>`
- `http://<FQDN for software update point on parent site>`
- `https://<FQDN for software update point on parent site>`

## Manage Microsoft 365 Apps

Note

On April 21, 2020, Office 365 ProPlus was renamed to **Microsoft 365 Apps for enterprise**. For more information, see [Name change for Office 365 ProPlus](/en-us/deployoffice/name-change). You might still see references to the old name in the Configuration Manager console and supporting documentation while the console is being updated.

If you use Configuration Manager to deploy and update Microsoft 365 Apps for enterprise, allow the following endpoints:

- `officecdn.microsoft.com` to synchronize the software update point for Microsoft 365 Apps for enterprise client updates
- `config.office.com` to create custom configurations for Microsoft 365 Apps for enterprise deployments
- `https://clients.config.office.net` and `https://go.microsoft.com/fwlink/?linkid=2190568` to support deploying updates for Microsoft 365 Apps for enterprise
- `contentstorage.osi.office.net` to support the evaluation of Office add-in readiness
- `clients.config.office.net` to retrieve the names of the files needed for a particular Microsoft 365 Apps update. For more information, see [Using the Microsoft 365 Apps file list API](/en-us/office/client-developer/shared/manageability-applications-with-the-office-365-click-to-run-installer#using-the-microsoft-365-apps-file-list-api).

Your top-level site server needs access to the following endpoint to download the Microsoft Apps 365 readiness file:

- Starting March 2, 2021: `https://omex.cdn.office.net/mirrored/sccmreadiness/SOT_SCCM_AddinReadiness.CAB`
    - Location before March 2, 2021: `https://contentstorage.osi.office.net/sccmreadinessppe/sot_sccm_addinreadiness.cab`

Note

The location of this file is changing *March 2, 2021*. For more information, see [Download location change for Microsoft 365 Apps readiness file](https://techcommunity.microsoft.com/t5/configuration-manager-blog/download-location-change-for-microsoft-365-apps-readiness-file/ba-p/2110282).

## Configuration Manager console

Computers with the Configuration Manager console require access to the following internet endpoints for specific features:

Note

For push notifications from Microsoft to show in the console, the service connection point needs access to `Configmgrbits.cdn.manage.microsoft.com`. It also needs access to this endpoint for updates and servicing.

### In-console feedback

On the computer where you run the console, allow it to access the following internet endpoints to send diagnostic data to Microsoft:

- `petrol.office.microsoft.com`
- `ceuswatcab01.blob.core.windows.net`
- `ceuswatcab02.blob.core.windows.net`
- `eaus2watcab01.blob.core.windows.net`
- `eaus2watcab02.blob.core.windows.net`
- `weus2watcab01.blob.core.windows.net`
- `weus2watcab02.blob.core.windows.net`
- `umwatsonc.events.data.microsoft.com`
- `*-umwatsonc.events.data.microsoft.com`

For more information on this feature, see [Product feedback](../../understand/product-feedback).

### Community workspace

#### Documentation node

For more information on this console node, see [Using the Configuration Manager console](../../servers/manage/admin-console).

- `https://aka.ms`
- `https://raw.githubusercontent.com`

#### Community hub

For more information on this feature, see [Community hub](../../servers/manage/community-hub).

- `https://github.com`
- `https://communityhub.microsoft.com`

## Tenant attach

For more information, see [Enable tenant attach](../../../tenant-attach/device-sync-actions).

- `https://aka.ms/configmgrgateway`
- `https://*.manage.microsoft.com`*for Azure public cloud customers*
- `https://*.manage.microsoft.us`*for US Government cloud customers on version 2107 or later*
- `https://dc.services.visualstudio.com`

The service connection point makes a long standing outgoing connection to the notification service hosted on `https://*.manage.microsoft.com`. Verify the proxy used for the service connection point doesn't time out outgoing connections too quickly. We recommend 3 minutes for outgoing connections to this internet endpoint. 

If your environment has proxy rules to allow only specific certificate revocation lists (CRLs) or online certificate status protocol (OCSP) verification locations, also allow the following CRL and OCSP URLs:

- `http://crl3.digicert.com`
- `http://crl4.digicert.com`
- `http://ocsp.digicert.com`
- `http://www.d-trust.net`
- `http://root-c3-ca2-2009.ocsp.d-trust.net`
- `http://crl.microsoft.com`
- `http://oneocsp.microsoft.com`
- `http://ocsp.msocsp.com`
- `http://www.microsoft.com/pkiops`

## Endpoint analytics

For more information, see [Endpoint analytics proxy configuration](../../../../endpoint-analytics/troubleshoot#proxy-server-authentication).

### Endpoints required for Configuration Manager-managed devices

Configuration Manager-managed devices send data to Intune via the connector on the Configuration Manager role and they don't need directly access to the Microsoft public cloud.

| Endpoint | Function |
| --- | --- |
| `https://graph.windows.net` | Used to automatically retrieve settings when attaching your hierarchy to Endpoint analytics on Configuration Manager server role. For more information, see [Configure the proxy for a site system server](proxy-server-support#configure-the-proxy-for-a-site-system-server). |
| `https://*.manage.microsoft.com` | Used to synch device collection and devices with Endpoint analytics on Configuration Manager server role only. For more information, see [Configure the proxy for a site system server](proxy-server-support#configure-the-proxy-for-a-site-system-server). |

### Endpoints required for Intune-managed devices

To enroll devices to Endpoint analytics, they need to send required functional data to Microsoft public cloud. Endpoint Analytics uses the Windows client and Windows Server **Connected User Experiences and Telemetry** component (DiagTrack) to collect the data from Intune-managed devices. Make sure that the **Connected User Experiences and Telemetry** service on the device is running.

| Endpoint | Function |
| --- | --- |
| `https://*.events.data.microsoft.com` | Used by Intune-managed devices to send [required functional data](../../../../endpoint-analytics/ref-data-collection) to the Intune data collection endpoint. |

## Asset intelligence

If you use [asset intelligence](../../clients/manage/asset-intelligence/introduction-to-asset-intelligence), allow the following endpoints for the service to synchronize:

- `https://sc.microsoft.com`
- `https://ssu2.manage.microsoft.com`

## Deploy Microsoft Edge

The device running the Configuration Manager console needs access to the following endpoints for deploying Microsoft Edge:

| Location | Use |
| --- | --- |
| `https://aka.ms/cmedgeapi` | Information about releases of Microsoft Edge |
| `https://edgeupdates.microsoft.com/api/products?view=enterprise` | Information about releases of Microsoft Edge |
| `http://dl.delivery.mp.microsoft.com` | Content for Microsoft Edge releases |

## External notifications

For more information, see [External notifications](../../servers/manage/external-notifications).

The service connection point needs to communicate with the notification service, for example Azure Logic Apps. The access endpoint for the logic app typically has the following format: `https://*.<RegionName>.logic.azure.com:443`. For example: `https://prod1.westus2.logic.azure.com:443`

To get the access endpoint for the logic app, and the associated IP addresses, use the following process:

1. In the Azure portal, under **Logic Apps**, select the logic app for your notification. For more information, see [Manage logic apps in the Azure portal](/en-us/azure/logic-apps/manage-logic-apps-with-azure-portal).
2. In the app's menu, in the **Settings** section, select **Properties**.
3. View or copy the values for the **Access endpoint** and the **Access endpoint IP addresses**.

## Microsoft public IP addresses

For more information on the Microsoft IP address ranges, see [Microsoft Public IP Space](https://www.microsoft.com/download/details.aspx?id=53602). These addresses update regularly. There's no granularity by service; Any IP address in these ranges could be used.