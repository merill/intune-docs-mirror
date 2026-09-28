---
layout: Conceptual
title: Configure 802.1x wired network settings for Apple and Windows devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-wired-networks
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
description: Create or add a wired network device configuration profile or policy using the IEEE 802.1X standard for macOS, iOS/iPadOS, Windows 10, and Windows 11 devices and computers. See the different settings, add certificates, choose an EAP type, and select an authentication method in Microsoft Intune.
ms.date: 2026-06-04T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: wicale
locale: en-us
document_id: 1328144c-3da8-ebbd-c6a4-2098adf41742
document_version_independent_id: 1328144c-3da8-ebbd-c6a4-2098adf41742
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-wired-networks.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-wired-networks
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-wired-networks.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: f8a698bb-38b0-5401-bbe9-f93041dc1f89
---

# Configure 802.1x wired network settings for Apple and Windows devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Organizations use wired networks to give network access to desktop computers and devices that must use a network cable.

Microsoft Intune includes built-in settings to configure wired networks for your iOS/iPadOS, macOS, and Windows devices. You can configure the network interface, accepted EAP types, enter server trust settings, and more.

These built-in settings can be deployed to devices in your organization using policy. When the policy is ready, it can be assigned to different users and groups. Once assigned, your users get access to your organization's wired network without configuring it themselves.

As part of your mobile device management (MDM) solution, use this feature to create 802.1x profiles to manage wired networks. Then, deploy these wired networks to your devices.

## Example scenario

You have a wired network named **Contoso wired network**. You want to set up all macOS desktops to connect to this network. Here's the process:

1. In Intune, create a wired network profile that includes the settings that connect to the **Contoso wired network**.
2. Assign the profile to a group that includes all users macOS desktop computers. For recommendations on using group types, go to [User groups vs. device groups](../assign-device-profile#user-groups-vs-device-groups).
3. On their desktops, users find the **Contoso wired network** in the list of networks. They can then connect to the network, using the authentication method of your choosing.

This article lists the steps to create a wired network profile in Intune. It also includes links that describe the different settings.

## Prerequisites

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> This feature supports the following platforms:
> 
> - iOS/iPadOS
> - macOS
> - Windows
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> - Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with an account that has the **[Policy and Profile Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** built-in role. For more information on the built-in roles, go to [Role-based access control for Microsoft Intune](../../fundamentals/role-based-access-control/overview).
> 

## Create the profile

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Enter the following properties:

    - **Platform**: Select **iOS/iPadOS**, **macOS**, or **Windows 10 and later**.
    - **Profile type**: Select **Templates** &gt; **Wired network**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the profile. Name your profiles so you can easily identify them later. For example, a good profile name is **macOS-Wired network policy**.
    - **Description**: Enter a description for the profile. This setting is optional, but recommended.
6. Select **Next**.
7. In **Configuration settings**, configure the settings, including the Extensible Authentication Protocol (EAP) type. For a list of all settings, and what they do, go to:

    - [Apple](ref-wired-network-settings-macos)
    - [Windows](ref-wired-network-settings-windows)
8. Select **Next**.
9. In **Assignments**, select the user groups or device groups that will receive your profile. For more information on assigning profiles, go to [Assign user and device profiles](../assign-device-profile).

    Select **Next**.
10. In **Review + create**, review your settings. When you select **Create**, your changes are saved, and the profile is assigned. The policy is also shown in the profiles list.

Tip

If you use certificate based authentication for your wired network profile, then deploy the wired network profile, certificate profile, and trusted root profile to the same groups. This deployment makes sure that each device can recognize the legitimacy of your certificate authority. For more information, go to [configure certificates with Microsoft Intune](../../fundamentals/certificates/overview).