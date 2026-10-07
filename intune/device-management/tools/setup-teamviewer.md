---
layout: Conceptual
title: Use the latest TeamViewer integration in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-management/tools/setup-teamviewer
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
ms.subservice: apps
description: Learn how to use the latest TeamViewer integration in Microsoft Intune to initiate remote assistance sessions for managed devices.
ms.date: 2026-04-07T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 78aa8637-4ce6-814b-7750-4499712e0df7
document_version_independent_id: 78aa8637-4ce6-814b-7750-4499712e0df7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-management/tools/setup-teamviewer.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-management/tools/setup-teamviewer
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-management/tools/setup-teamviewer.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: e6c562a8-cafa-43e9-19a3-da8ebaa47037
---

# Use the latest TeamViewer integration in Microsoft Intune - Microsoft Intune | Microsoft Learn

Important

A new TeamViewer remote assistance experience is available in Intune and is described in this article.

Your old TeamViewer configurations remain available in the Microsoft Intune admin center under **TeamViewer connector (old)**. To use the new experience, you must set up the new connector under **TeamViewer connector**.

If both connectors are enabled, helpdesk agents see two options when starting a remote assistance session:

- **TeamViewer (old)**: Previous remote assistance experience
- **TeamViewer**: New remote assistance experience

For information about the previous connector, see [Use TeamViewer to remotely administer Intune devices](teamviewer-legacy).

Devices managed by Microsoft Intune can be administered remotely using TeamViewer, a third-party remote assistance solution that you purchase separately. This article describes:

- How to configure the latest TeamViewer connector in the Intune admin center.
- How to start a remote assistance session on a managed device using TeamViewer.
- What data Intune shares with TeamViewer on behalf of your tenant to enable the remote assistance experience.

This feature applies to:

- Android (all enrollment options, including BYOD, COBO, COSU, COPE, AOSP, and DA)
- iOS/iPadOS
- macOS
- Windows

Note

TeamViewer isn't supported on GCC or GCC High environments.

## Prerequisites

Before you configure the TeamViewer connector in Intune, make sure these requirements are met.

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> - The administrator configuring the TeamViewer connector must have a Microsoft Intune license. You can give administrators access to Intune without them requiring an Intune license. For more information, see [Unlicensed admins](../../fundamentals/licensing#unlicensed-admin-access).
> - A TeamViewer account and license is required. Visit the [TeamViewer integration docs](https://www.teamviewer.com/en/integrations/microsoft-intune/) (opens the TeamViewer website) or contact the TeamViewer sales team for more information about account setup and required licenses.
> 

![](../../media/icons/16/rbac.svg)**Roles requirements**

> 
> To onboard TeamViewer, you must be assigned the following built-in Intune permissions:
> 
> - Remote assistance connectors/Read
> - Remote assistance connectors/Update
> 
> 
> Alternatively, you can sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the built-in **[Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)** Microsoft Entra role.

The integration supports connections to TeamViewer‑managed devices that have the TeamViewer host or full client installed and are managed by your Intune tenant. Any connection settings, policies, or TeamViewer conditional access rules you configured will also apply to connections started from the integration. For more information, see [Getting started with Intune integration](https://www.teamviewer.com/link/?url=178709) (opens the TeamViewer website).

## Configure the TeamViewer connector

To enable remote assistance through TeamViewer, an Intune administrator must configure the TeamViewer connector in the Intune admin center. This connector establishes the connection between your Intune tenant and your TeamViewer environment.

### Role-based access control

These Intune permissions allow you to delegate connector management and session initiation without granting full administrative access to Intune:

- *Remote assistance connectors/Read*: View the connector status.
- *Remote assistance connectors/Read* and *Remote Tasks/Offer Remote assistance*: View the connector status and initiate TeamViewer sessions.
- *Remote assistance connectors/Read* and *Remote assistance connectors/Update*: View and modify the connector configuration.

If a user has *read* permission without *update* permission, they can still view the connector, but they can't edit any configurations. For more information about role requirements, see [Role-based access control (RBAC) with Microsoft Intune](../../fundamentals/role-based-access-control/overview).

### Optimize setup

To ensure a seamless setup, you can configure Intune Sync in your TeamViewer company settings to match your Intune and TeamViewer device group setups. For more information, see [TeamViewer Intune Device Sync](https://www.teamviewer.com/link/?url=737977) (opens the TeamViewer website).

To get the best experience while using the integration, we recommend you enable single sign-on (SSO) between TeamViewer and the Microsoft Entra identity provider.

### Setup

Complete these steps to integrate the TeamViewer connector with Microsoft Intune.

1. Sign in to the Intune admin center as an Intune administrator or user with sufficient permissions.
2. Go to **Tenant administration** &gt; **Connectors and tokens** &gt; **TeamViewer connector**. 
    Note

    The new TeamViewer connector appears as **TeamViewer connector** in the admin center. The previous connector is now called **TeamViewer connector (old)**.
3. On the TeamViewer connector page, flip the **Turn on TeamViewer connector** toggle to **On**. This toggle enables TeamViewer as a remote assistance option for your tenant.
4. Review the Data shared with TeamViewer section later in this article to understand the data that's sent to TeamViewer when the connector is enabled.
5. The TeamViewer base URL is prefilled with `https://web.teamviewer.com/`, which is the appropriate URL for most companies. If your organization uses a specific TeamViewer region, enter the appropriate subdomain of the URL. This URL determines which TeamViewer environment Intune launches when a helpdesk user starts a remote assistance session.
6. Select **Save** to apply the configuration. When the configuration is complete, a confirmation message appears and the connector status is updated.

After the TeamViewer connector is enabled and saved:

- When authorized users select **New remote assistance session** on a device, TeamViewer is available as an option.
- Intune uses the configured TeamViewer URL each time it launches a session.
- Configuration changes and session launches are recorded in Intune audit logs for administrative visibility.

## Remotely administer a device with TeamViewer

Authorized support personnel can initiate a remote assistance session on a Microsoft Intune managed device through the Intune admin center. Session launches are recorded in the Intune audit logs.

When a support technician starts a remote assistance session via Intune and TeamViewer, the connection is established on the device using the access policies, such as the Conditional Access rules, device policies, and access control settings, defined in your TeamViewer organizational settings.

1. In the Intune admin center, go to **Devices** &gt; **All devices**.
2. Select the device that needs remote assistance, and then choose **Remote actions** &gt; **Begin a remote assistance session**.
3. Select **TeamViewer**, and then select **Continue**.
4. Intune opens a new browser tab and loads the TeamViewer URL with device identifiers. For information about these identifiers, see Data shared with TeamViewer in this article.
5. From this point on, TeamViewer handles ownership of the experience, including authentication and session management. Complete the steps as prompted.
6. Close the TeamViewer window to end the session.

## Data shared with TeamViewer

The TeamViewer integration requires Intune to exchange a limited set of data with the TeamViewer service on behalf of your tenant. Data sharing is strictly to enable the remote assistance sessions that you initiate. This section describes the type of data shared.

When a helpdesk agent launches a new remote assistance session to a device, Intune passes specific device identification data to TeamViewer as query parameters in the session URL, which includes the base URL you configured for TeamViewer.

| Data element | Description |
| --- | --- |
| Microsoft Entra device ID | A tenant-unique identifier for the device, used by TeamViewer to look up the device record. |
| Device name | The device name of the Intune-registered device, used as a fallback if the Microsoft Entra device ID is unavailable. |

## TeamViewer license and privacy terms

For the TeamViewer license and privacy terms, see:

- [TeamViewer End User License Agreement (EULA)](https://www.teamviewer.com/en/legal/eula/) (opens TeamViewer website)
- [TeamViewer Privacy Terms](https://www.teamviewer.com/en/legal/privacy-and-cookies/) (opens TeamViewer website)

## Get help

Microsoft Intune supports the setup of TeamViewer remote assistance from the Microsoft Intune admin center. After you launch a remote assistance session, the experience is owned and supported by TeamViewer.