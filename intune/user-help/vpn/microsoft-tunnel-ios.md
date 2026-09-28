---
layout: Conceptual
title: Use the Microsoft Tunnel app for iOS - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/vpn/microsoft-tunnel-ios
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn how to connect over VPN using Microsoft Tunnel for iOS.
ms.date: 2023-11-14T00:00:00.0000000Z
ms.reviewer: shthilla
locale: en-us
document_id: b88843d8-8fd8-2b42-81ae-f234a9a57caf
document_version_independent_id: b88843d8-8fd8-2b42-81ae-f234a9a57caf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/vpn/microsoft-tunnel-ios.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/vpn/microsoft-tunnel-ios
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/vpn/microsoft-tunnel-ios.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
platformId: 106b93a2-d62e-f9eb-6afe-2c9538682b41
---

# Use the Microsoft Tunnel app for iOS - Microsoft Intune | Microsoft Learn

Microsoft Tunnel uses Microsoft Defender for Endpoint as The Microsoft Tunnel client app on iOS.

The Microsoft Tunnel client app helps you securely and privately connect to your corporate network over a VPN. If your organization requires you to use the app, they already configured a VPN connection for your work account. To connect to the VPN, simply install the app and sign in with your work account.

## Connect and disconnect VPN

1. Open Microsoft Tunnel.
2. Sign in with your work account if prompted.
3. On the **Connect** screen, turn the **Status** toggle on or off to connect or disconnect from the VPN.

An absent **Status** toggle means that Tunnel is configured to connect automatically when certain apps are in use. To turn this functionality off, go to **Details** and turn off **Connect on demand**.

If the toggle is stuck in the off position, select **Help** &gt; **Send logs** and report the problem to your IT support person. For more details, see the [Send logs](microsoft-tunnel-ios#send-logs) section in this article.

## Connection details

The following information appears on the **Connect** screen when Tunnel is connected.

- **Uptime**: How long the VPN connection has been running.
- **Data received**: How much data has been received through the VPN connection.
- **Data sent**: How much data has been sent through the VPN connection.

Tap **Details** to see the following information:

- **Address**: The server address for your VPN connection.
- **Script/Address/Port**: These details will help IT support troubleshoot your proxy server connection, should you ever need help.
- **Device-wide connection**: When turned on, all network traffic to and from your device goes through the VPN connection.
- **Connect on demand**: When turned on, Microsoft Tunnel automatically connects when certain apps (listed under **Apps that use Tunnel**) are in use.
- **Apps that use Tunnel**: If apps are listed, only network traffic to and from these apps go through the VPN connection.

## App settings

To configure how Tunnel collects and logs data, open the **Settings** app on your device. Select **Microsoft Tunnel** to:

- Allow/block Microsoft from collecting usage and performance data.
- Turn verbose logging on/off.

## Get help in the app

Select **Help** from the menu at the bottom of the screen to:

- Access documentation (directs you to this article).
- Send logs to IT support to report a problem.

### Send logs

Send app logs to IT support to get help with an app or connection problem.

1. Select **Help** &gt; **Send logs**.
2. Select **Send logs** again. Your logs will be sent to a Microsoft database, from which your organization can access.
3. Select **Email administrator**.
4. In the body of the email, describe the problem you experienced so that the support team has an idea of what to look for.
5. Send the email.

## About Microsoft Tunnel

Select **About** to view the Microsoft Tunnel privacy policy, terms of use, and third-party notices.