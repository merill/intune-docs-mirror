---
layout: Conceptual
title: Service connection point - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point
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
description: Learn about this Configuration Manager site system role, and understand and plan for its range of uses.
ms.date: 2021-10-12T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 519cef62-a212-4f56-1b48-5761b186ce6f
document_version_independent_id: 2b9cf41f-3900-387e-72bf-ef96cdf9875f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/about-the-service-connection-point
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/about-the-service-connection-point.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
platformId: 57840bf8-fc74-0000-461e-d548f0200f35
---

# Service connection point - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The service connection point is a site system role that provides several important functions for the hierarchy. Before you set up the service connection point, understand and plan for its range of uses. Planning for usage might affect how you set up this site system role:

- Download updates that apply to your Configuration Manager infrastructure. Only relevant updates for your infrastructure are made available based on usage data you upload.
- Upload usage data from your Configuration Manager infrastructure. You can control the level or amount of detail that you upload. For more information, see [Usage data levels and settings](../install/setup-reference#bkmk_usage).
- Deploy a [cloud management gateway](../../../clients/manage/cmg/overview) in Azure
- Synchronize apps from the [Microsoft Store for Business and Education](../../../../apps/deploy-use/manage-apps-from-the-windows-store-for-business)
- Discover users and groups in [Microsoft Entra ID](about-discovery-methods#azureaddisc)

Each hierarchy supports a single instance of this role. It can only be installed at the top-tier site of your hierarchy, which is a central administration site (CAS) or stand-alone primary site. If you expand a stand-alone primary site to a larger hierarchy, uninstall this role from the primary site, and then install it at the CAS.

## Modes of operation

The service connection point supports two modes of operation:

- **Online**: The service connection point automatically checks every 24 hours for updates. It downloads new updates that are available for your current infrastructure and product version to make them available in the Configuration Manager console.
- **Offline**: The service connection point doesn't connect to the Microsoft cloud service. To manually import available updates, use the [service connection tool](../../manage/use-the-service-connection-tool).

### Change mode

If you change between online or offline modes after you install the service connection point, restart the **SMS\_DMP\_DOWNLOADER** thread of the SMS\_Executive service. Restarting this thread makes the change become effective. To restart this thread, use the Configuration Manager Service Manager.

Tip

You can also restart the SMS\_Executive service for Configuration Manager, which restarts most site components. Alternatively, wait for a scheduled task like a site backup, which stops and restarts the SMS\_Executive service for you.

To use the Configuration Manager Service Manager to restart the SMS\_DMP\_DOWNLOADER thread:

1. In the Configuration Manager console go to the **Monitoring** workspace, expand **System Status**, and select the **Component Status** node. In the ribbon, choose **Start**, and then select **Configuration Manager Service Manager**.
2. In the service manager navigation pane, expand the site, expand **Components**, and then choose the component that you want to restart: **SMS\_DMP\_DOWNLOADER**.
3. Go to the **Component** menu, and choose **Query**.
4. Confirm the current status of the component. Then go to the **Component** menu, and choose **Stop**.
5. **Query** the component again to confirm that it stopped. Then choose the **Start** component action to restart it.

## Remote site system requirements

When you install the service connection point on a site system server that's remote from the site server, configure one of the following requirements:

- The computer account of the site server must be a local admin on the computer that hosts a remote service connection point.

    or
- Set up the site system server that hosts this role with a [site system installation account](../../../plan-design/hierarchy/accounts#site-system-installation-account). The distribution manager on the site server uses the site system installation account to transfer updates from the service connection point.

## Internet access requirements

If your organization restricts network communication with the internet using a firewall or proxy device, you need to allow the service connection point to access internet endpoints.

For more information, see [Internet access requirements](../../../plan-design/network/internet-endpoints). Other Configuration Manager features may require additional endpoints from the service connection point.

These configurations apply to the server that hosts the service connection point and any firewalls between that server and the internet. Allow communication through outgoing HTTPS port **TCP 443** to the internet locations.

The service connection point supports using a web proxy with or without authentication to use these locations. For more information, see [Proxy server support](../../../plan-design/network/proxy-server-support).

If the Configuration Manager site fails to connect to required endpoints for a cloud service, it raises a critical status message ID 11488. When it can't connect to the service, the SMS\_SERVICE\_CONNECTOR component status changes to critical. View detailed status in the [Component Status](../../manage/use-status-system#monitor-the-status-system) node of the Configuration Manager console.

Starting in version 2010, the service connection point validates important internet endpoints for [tenant attach](../../../plan-design/network/internet-endpoints#tenant-attach). These checks help make sure that the cloud-connected services are available. It also helps you troubleshoot issues by quickly determining if network connectivity is a problem. For more information, see [Validate internet access](about-the-service-connection-point#validate-internet-access).

The specific URLs required by the service connection point vary by Configuration Manager feature:

- [Updates and servicing](../../../plan-design/network/internet-endpoints#updates-and-servicing)
- [Windows servicing](../../../plan-design/network/internet-endpoints#windows-servicing)
- [Azure services](../../../plan-design/network/internet-endpoints#azure-services)
- [Microsoft Store for Business](../../../plan-design/network/internet-endpoints#microsoft-store-for-business)
- [Cloud services](../../../plan-design/network/internet-endpoints#cloud-services)
- [Configuration Manager console](../../../plan-design/network/internet-endpoints#configuration-manager-console)
- [Tenant attach](../../../plan-design/network/internet-endpoints#tenant-attach)
- [External notifications](../../../plan-design/network/internet-endpoints#external-notifications)

Tip

The service connection point uses the Microsoft Intune service when it connects to `go.microsoft.com` or `manage.microsoft.com`. There's a known issue in which the Intune connector experiences connectivity issues if the Baltimore CyberTrust Root Certificate isn't installed, is expired, or is corrupted on the service connection point. For more information, see [Service connection point doesn't download updates](/en-us/troubleshoot/mem/configmgr/service-connection-point-not-download-updates).

## Validate internet access

If you use tenant attach, starting in version 2010, the service connection point now checks important internet endpoints. These checks help make sure that the cloud-connected services are available. It also helps you troubleshoot issues by quickly determining if network connectivity is a problem.

For the list of internet endpoints, see the following section of the **Internet access requirements** article: [Tenant attach](../../../plan-design/network/internet-endpoints#tenant-attach).

For more details, review the **EndpointConnectivityCheckWorker.log** file on the service connection point.

A failure isn't always determined by the HTTP status code, but if there's network connectivity to an endpoint. The following scenarios can cause a check to fail:

- Network connection timeout
- SSL/TLS failure
- Unexpected status code:

    | Status code | Description | Possible reason |
    | --- | --- | --- |
    | 407 | Proxy authentication required | May indicate a proxy issue |
    | 408 | Request timeout | May indicate a proxy issue |
    | 426 | Upgrade required | May indicate a TLS misconfiguration |
    | 451 | Unavailable for legal reasons | May indicate a proxy issue |
    | 502 | Bad gateway | May indicate a proxy issue |
    | 511 | Network authentication required | May indicate a proxy issue |
    | 598 | Network read timeout error | Not RFC compliant, but used by some proxy servers to indicate a network timeout |
    | 599 | Network connection timeout error | Not RFC compliant, but used by some proxy servers to indicate a network timeout |

There are also the following status messages for the **SMS\_SERVICE\_CONNECTOR** component:

| Message ID | Severity | Notes |
| --- | --- | --- |
| 11410 | Informational | All checks are successful |
| 11411 | Warning | One or more non-critical failures occurred |
| 11412 | Error | One or more critical failures occurred |

## Install

When you run **Setup** to install the top-tier site of a hierarchy, you can install the service connection point.

After setup runs, or if you're reinstalling the role, use the **Add Site System Roles** wizard or the **Create Site System Server** wizard. (Only install the service connection point on the top-tier site of your hierarchy.) For more information, see [Install site system roles](install-site-system-roles).

## Move the role

There are several scenarios in which you may need to move the service connection point to another server:

- [Recovery](../../manage/recover-sites)
- [Site server high availability](site-server-high-availability)
- [Site expansion](../install/setup-wizard-central-primary#expand-a-stand-alone-primary-site)

After you move the service connection point, check all site functions. For example, you may need to renew the secret key for any connections to Microsoft Entra tenants. For more information, see [Renew secret key](azure-services-wizard#bkmk_renew).

## Console notifications for the service connection point

Occasionally, the Configuration Manager console may give you a [notification](../../manage/admin-console-notifications) about your service connection point. The notification asks you to restart the SMS\_EXECUTIVE service on the server that hosts the service connection point. This notification occurs because a configuration change was made by Microsoft on the services that your service connection point connects to. Features of Configuration Manager that rely on these services may not function for your site properly until the SMS\_EXECUTIVE service is restarted.

## Log files

To view information about uploads to Microsoft, view the **Dmpuploader.log** on the server that runs the service connection point. For download progress of updates, view the **Dmpdownloader.log**. For the complete list of logs related to the service connection point, see [Log files - Service connection point](../../../plan-design/hierarchy/log-files#BKMK_WITLog).