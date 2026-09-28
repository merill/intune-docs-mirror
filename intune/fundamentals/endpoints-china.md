---
layout: Conceptual
title: Network endpoints for China deployments - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/endpoints-china
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Review China endpoints for Intune.
ms.date: 2025-06-09T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: srink
locale: en-us
document_id: 2da01b22-18b0-4a11-a30a-1b9dc14e85b1
document_version_independent_id: 2da01b22-18b0-4a11-a30a-1b9dc14e85b1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/endpoints-china.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/endpoints-china
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/endpoints-china.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b5e53e15-0a76-4936-b270-8b2badca62ac
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/6908a4c7-0b59-4f8b-a00e-59c83ae0a04a
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 4415531f-9d4f-2991-a7f1-60e9271b01ac
---

# Network endpoints for China deployments - Microsoft Intune | Microsoft Learn

This page lists the China endpoints that are needed for proxy settings in your Intune deployments.

To manage devices behind firewalls and proxy servers, you must enable communication for Intune.

- The proxy server must support both **HTTP (80)** and **HTTPS (443)** because Intune clients use both protocols
- For some tasks (like downloading software updates), Intune requires unauthenticated proxy server access to manage.microsoft.com

You can modify proxy server settings on individual client computers. You can also use Group Policy settings to change settings for all client computers located behind a specified proxy server.

Managed devices require configurations that let **All Users** access services through firewalls.

For more information about Windows auto-enrollment and device registration for U.S. customers, see [Windows auto enrollment and device registration](../device-enrollment/windows/create-cname-autodiscovery#windows-auto-enrollment-and-device-registration).

Note

Intune endpoints also use *Azure Front Door* for communicating with the Intune service. The IP ranges for Intune are added to the following table. Intune specific endpoints are referenced in the JSON file by the name `AzureFrontDoor.Frontend`. Refer to the Azure Front Door and Service Tags documentation for the complete list of all services that utilize Azure Front Door and instructions for using the JSON file. [Azure Front Door IP Ranges and Service Tags](https://www.microsoft.com/download/details.aspx?id=57062)

The following tables list the ports and services that the Intune client accesses:

| **Endpoint** | **IP address** |
| --- | --- |
| \*.manage.microsoftonline.cn | 40.73.38.143139.217.97.8152.130.80.2440.73.41.16240.73.58.153139.217.95.85  143.64.196.128/25  40.162.2.128/25  139.219.250.128/25  163.228.221.128/25 Azure Front Door Endpoints:52.131.21.32/2952.131.149.32/29143.64.194.48/29159.27.145.240/29159.27.248.128/292159.27.255.224/29163.228.60.104/29163.228.102.88/29163.228.195.128/29163.228.218.208/292404:7940:1::5e0/1232404:7940:101::5e0/1232404:7940:201::5e0/1232404:7940:301::5e0/1232406:e500:2402:1::480/1232406:e500:2602:1::480/123 |

## Intune customer designated endpoints in China

- Azure portal: `https:\//portal.azure.cn/`
- Microsoft 365: `https:\//portal.partner.microsoftonline.cn/`
- Intune Company Portal: `https:\//portal.manage.microsoftonline.cn/`
- Microsoft Intune admin center: `https:\//intune.microsoftonline.cn/`

## Network requirements for PowerShell scripts and Win32 apps

If you're using Intune to deploy PowerShell scripts or Win32 apps, you also need to grant access to endpoints in which your tenant currently resides.

| Azure Scale Unit (ASU) | Storage name | CDN |
| --- | --- | --- |
| CNPASU01 | sovereignprodimedataprisovereignprodimedatasecsovereignprodimedatahotfix | imeswdsc-afd-pri.manage.microsoft.comimeswdsc-afd-sec.manage.microsoft.comimeswdsc-afd-hotfix.manage.microsoft.com |

## Network requirements for macOS app and script deployments

If you're using Intune to deploy apps or scripts on macOS, you also need to grant access to endpoints in which your tenant currently resides.

| Azure Scale Unit (ASU) | Storage Name | CDN |
| --- | --- | --- |
| CNPASU01 | macsidecarapmacsidecarprodap | macsidecarap.manage.microsoft.com |

## Partner service endpoints

Intune operated by 21Vianet depends on the following partner service endpoints:

- Azure AD Sync service: `https://syncservice.partner.microsoftonline.cn/DirectoryService.svc`
- Evo STS: `https://login.chinacloudapi.cn/`
- Azure AD `Graph: https://graph.chinacloudapi.us`
- MS Graph: `https://microsoftgraph.chinacloudapi.cn`
- ADRS: `https://enterpriseregistration.partner.microsoftonline.cn`
- Experimentation and Configuration Service (ECS): `https://mooncake.ecs.office.com`

## Windows Push Notification Services

On Intune-managed devices managed by using Mobile Device Management (MDM), Windows Push Notification Services (WNS) is required for device actions and other immediate activities. For more information, see [Enterprise Firewall and Proxy Configurations to Support WNS Traffic](/en-us/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)

## Apple dependencies

For information about Apple specific endpoints, see the following resources:

- [Use Apple products on enterprise networks](https://support.apple.com/HT210060)
- [TCP and UDP ports used by Apple software products](https://support.apple.com/HT202944)
- [About macOS, iOS/iPadOS, and iTunes server host connections and iTunes background processes](https://support.apple.com/HT201999)
- [If your macOS and iOS/iPadOS clients aren't getting Apple push notifications](https://support.apple.com/HT203609)