---
layout: Conceptual
title: Create a Windows Network Boundary profile in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/create-network-boundary-windows
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Add a Windows Network Boundary policy to Windows devices using Microsoft Intune. Add trusted sites, trusted domains, IPv4 and IPv6 ranges, and proxy servers to a device configuration policy. Microsoft Defender Application Guard in Microsoft Edge trusts sites in this boundary.
ms.date: 2025-02-19T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: mikedano
locale: en-us
document_id: 511a5ed9-ebbc-6c27-f356-3111fde378f8
document_version_independent_id: 511a5ed9-ebbc-6c27-f356-3111fde378f8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/create-network-boundary-windows.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/create-network-boundary-windows
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/create-network-boundary-windows.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c671beaa-a830-4c9f-aceb-97379ee031ca
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8921374c-4dbe-4ed0-b011-a39e18bfbd98
platformId: 85179d1e-8548-c698-c5f3-df6f86772aa9
---

# Create a Windows Network Boundary profile in Microsoft Intune - Microsoft Intune | Microsoft Learn

When using Microsoft Defender Application Guard and Microsoft Edge, you can protect your environment from sites that your organization doesn't trust. This feature is called a network boundary.

In a network boundary, you can add network domains, IPV4 and IPv6 ranges, proxy servers, and more. Microsoft Defender Application Guard in Microsoft Edge trusts sites in this boundary.

In Intune, you can create a network boundary profile, and deploy this policy to your devices.

For more information on using Microsoft Defender Application Guard in Intune, go to [Windows client settings to protect devices using Intune](../endpoint-security/ref-endpoint-protection-settings-windows#microsoft-defender-application-guard).

This feature applies to:

- Windows devices enrolled in Intune

This article shows you how to create the profile, and add trusted sites.

## Before you begin

- Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).
- This feature uses the [NetworkIsolation CSP](/en-us/windows/client-management/mdm/policy-csp-networkisolation).

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **Windows 10 and later**.
    - **Profile type**: Select **Templates** &gt; **Network boundary**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your policies so you can easily identify them later. For example, a good profile name is **Windows-Contoso network boundary**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, configure the following settings:

    - **Import**: This option lets you import a `.csv` file with your network boundary details.
    - **Boundary type**: This setting creates an isolated network boundary. Sites in this boundary are considered trusted by Microsoft Defender Application Guard. Your options:

        - **IPv4 range**: Enter a comma-separated list of IPv4 ranges of devices in your network. Data from these devices is considered part of your organization, and is protected. These locations are considered a safe destination for organization data to be shared to.
        - **IPv6 range**: Enter a comma-separated list of IPv6 ranges of devices in your network. Data from these devices is considered part of your organization, and is protected. These locations are considered a safe destination for organization data to be shared to.
        - **Cloud resources**: Enter a pipe-separated (`|`) list of organization resource domains hosted in the cloud that you want protected.
        - **Network domains**: Enter a comma-separated list of domains that create the boundaries. Data from any of these domains is sent to a device, is considered organization data, and is protected. These locations are considered a safe destination for organization data to be shared to. For example, enter `contoso.sharepoint.com, contoso.com`.
        - **Proxy servers**: Enter a comma-separated list of proxy servers. Any proxy server in this list is at the internet-level, and not internal to the organization. For example, enter `157.54.14.28, 157.54.11.118, 10.202.14.167, 157.53.14.163, 157.69.210.59`.
        - **Internal proxy servers**: Enter a comma-separated list of internal proxy servers. The proxies are used when adding **Cloud resources**. They force traffic to the matched cloud resources. For example, enter `157.54.14.28, 157.54.11.118, 10.202.14.167, 157.53.14.163, 157.69.210.59`.
        - **Neutral resources**: Enter a list of domain names that can be used for work resources or personal resources.
    - **Value**: Enter your list.
    - **Auto detection of other enterprise proxy servers**: **Disable** prevents devices from automatically detecting proxy servers that aren't in the list. The devices accept the configured list of proxies. When set to **Not configured** (default), Intune doesn't change or update this setting.
    - **Auto detection of other enterprise IP ranges**: **Disable** prevents devices from automatically detecting IP ranges that aren't in the list. The devices accept the configured list of IP ranges. When set to **Not configured** (default), Intune doesn't change or update this setting.
8. Select **Next**.
9. In **Scope tags** (optional), assign a tag to filter the profile to specific IT groups, such as `US-NC IT Team` or `JohnGlenn_ITDepartment`. For more information about scope tags, go to [Use role-based access control (RBAC) and scope tags for distributed IT](../../fundamentals/role-based-access-control/scope-tags).

    Select **Next**.
10. In **Assignments**, select the users or user group that will receive your profile. For more information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
11. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

The next time each device checks in, the policy is applied.