---
layout: Conceptual
title: Network endpoints for US government deployments - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/endpoints-us-government
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
description: See the list of US government endpoint URLs that Intune needs and requires. Allow the ports, IP addresses, and endpoint URLs in your proxy server configuration.
ms.date: 2025-12-15T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: srink, davidra
locale: en-us
document_id: 3365a730-be2d-c928-aa98-1d0f3e0a4154
document_version_independent_id: 3365a730-be2d-c928-aa98-1d0f3e0a4154
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/endpoints-us-government.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/endpoints-us-government
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/endpoints-us-government.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b5e53e15-0a76-4936-b270-8b2badca62ac
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6908a4c7-0b59-4f8b-a00e-59c83ae0a04a
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: e6ddd0b4-d162-c138-0c1f-b3aeb19d249c
---

# Network endpoints for US government deployments - Microsoft Intune | Microsoft Learn

This article lists the US Government, US Government Community (GCC) High, and Department of Defense (DoD) endpoints needed for proxy settings in your Intune deployments.

## Before you begin

- To manage devices behind firewalls and proxy servers, you must enable communication for Intune.

    - The proxy server must support **HTTP (80)** and **HTTPS (443)**. Intune clients use both protocols.
    - For some tasks (like downloading software updates), Intune requires unauthenticated proxy server access to `manage.microsoft.us`.
- You can modify proxy server settings on individual client computers. You can also use Group Policy settings to change settings for all client computers located behind a specified proxy server.
- Managed devices require configurations that let **All Users** access services through firewalls.
- The inspection of SSL traffic is not supported on `*.manage.microsoft.us` or `has.spserv.microsoft.com` endpoints.

For more information about Windows auto-enrollment and device registration for US government customers, see [Set up automatic enrollment for Windows](../device-enrollment/windows/enable-automatic-mdm).

## Ports and IP addresses list

The following table lists the service endpoints, IP addresses, and ports that the Intune client accesses.

Intune endpoints also use Azure Front Door for communicating with the Intune service. Intune specific endpoints are referenced by `AzureFrontDoor.MicrosoftSecurity` in the JSON file. For the complete list of all services that utilize Azure Front Door and instructions to use the JSON file, see [Azure Front Door IP Ranges and Service Tags](https://www.microsoft.com/download/details.aspx?id=57063).

| Endpoint | IP address |
| --- | --- |
| \*.manage.microsoft.us | 52.227.99.114  20.141.108.112  13.72.17.166  52.126.185.115  52.227.211.91  23.97.10.212  52.227.29.124  52.247.174.16  52.227.29.244  52.227.208.144  52.227.1.233  20.141.104.221  52.247.134.218  20.141.78.227  13.77.236.201  62.10.86.128/25  62.10.87.128/25  20.159.110.0/25  20.159.111.0/25 Azure Front Door:51.54.53.136/29  51.54.114.160/29  62.11.173.176/29 |
| enterpriseregistration.microsoftonline.us | 13.72.188.239  13.72.55.179 |

## US Government customer designated endpoints

- Azure portal: `https://portal.azure.us/`
- Microsoft 365: `https://portal.office365.us/`
- Intune Company Portal: `https://portal.manage.microsoft.us/`
- Microsoft Intune admin center: `https://intune.microsoft.us/`

## Network requirements for PowerShell scripts and Win32 apps

If you're using Intune to deploy PowerShell scripts or Win32 apps, you also need to grant access to endpoints in which your tenant currently resides.

| Azure Scale Unit (ASU) | Storage name | CDN |
| --- | --- | --- |
| FXPASU01 | sovereignprodimedataprisovereignprodimedatasecsovereignprodimedatahotfix | imeswdsc-afd-pri.manage.microsoft.comimeswdsc-afd-sec.manage.microsoft.comimeswdsc-afd-hotfix.manage.microsoft.com |

For diagnostic data used to monitor the health of the client side components:

- `*.events.data.microsoft.com`

## Microsoft Defender for Endpoint

For more information about configuring Defender for Endpoint connectivity, see [Connectivity Requirements](../device-security/microsoft-defender/security-settings-management#connectivity-requirements).

To support Defender for Endpoint security settings management, allow the following hostnames through your firewall.

For communication between clients and the cloud service:

- `*.dm.microsoft.us` - The use of a wildcard supports the cloud-service endpoints that are used for enrollment, check-in, and reporting, and which can change as the service scales.

    Important

    SSL Inspection is not supported on endpoints required for Microsoft Defender for Endpoint.

## Microsoft Intune Endpoint Privilege Management

To support Endpoint Privilege Management, allow the following hostnames through your firewall.

For communication between clients and the cloud service:

- `*.dm.microsoft.us` - The use of a wildcard supports the cloud-service endpoints that are used for enrollment, check-in, and reporting, and which can change as the service scales.

    Important

    SSL Inspection isn't supported on endpoints required for Endpoint Privilege Management.

For more information, see the [Overview of Endpoint Privilege Management](../epm/overview).

## Partner service endpoints that Intune depends on

- Azure AD Sync service: `https://syncservice.gov.us.microsoftonline.com/DirectoryService.svc`
- Evo STS: `https://login.microsoftonline.us`
- Directory Proxy: `https://directoryproxy.microsoftazure.us/DirectoryProxy.svc`
- Azure AD Graph: `https://directory.microsoftazure.us` and `https://graph.microsoftazure.us`
- MS Graph: `https://graph.microsoft.us`
- ADRS: `https://enterpriseregistration.microsoftonline.us`
- Experimentation and Configuration Service (ECS): `*.ecs.gov.teams.microsoft.us`

## Windows Push Notification Services

On Intune-managed devices managed by using Mobile Device Management (MDM), Windows Push Notification Services (WNS) is required for device actions and other immediate activities. For more information, see [Enterprise Firewall and Proxy Configurations to Support WNS Traffic](/en-us/windows/uwp/design/shell/tiles-and-notifications/firewall-allowlist-config)

## Apple dependencies

For information about Apple specific endpoints, see the following resources:

- [Use Apple products on enterprise networks](https://support.apple.com/HT210060)
- [TCP and UDP ports used by Apple software products](https://support.apple.com/HT202944)
- [About macOS, iOS/iPadOS, and iTunes server host connections and iTunes background processes](https://support.apple.com/HT201999)
- [If your macOS and iOS/iPadOS clients aren't getting Apple push notifications](https://support.apple.com/HT203609)