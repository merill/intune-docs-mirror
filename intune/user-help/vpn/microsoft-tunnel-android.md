---
layout: Conceptual
title: Use the Microsoft Tunnel client app for Android - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/user-help/vpn/microsoft-tunnel-android
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.subservice: end-user
ms.topic: end-user-help
description: Learn how to connect over VPN using Microsoft Tunnel for Android.
ms.date: 2026-05-26T00:00:00.0000000Z
ai-usage: ai-assisted
ms.reviewer: shthilla
locale: en-us
document_id: 274a2caf-a923-8c60-725e-6c79353b23a6
document_version_independent_id: 274a2caf-a923-8c60-725e-6c79353b23a6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/user-help/vpn/microsoft-tunnel-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: user-help/vpn/microsoft-tunnel-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/user-help/vpn/microsoft-tunnel-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 889380cc-a8c0-8172-c632-bf4a5550cb60
---

# Use the Microsoft Tunnel client app for Android - Microsoft Intune | Microsoft Learn

Microsoft Tunnel uses Microsoft Defender for Endpoint as The Microsoft Tunnel client app on Android.

The Microsoft Tunnel client app helps you securely and privately connect to your corporate network over a VPN. If your organization requires you to use the app, they already configured a VPN connection for your work account. To connect to the VPN, simply install the app and sign in with your work account.

## Install Microsoft Tunnel

Microsoft Defender for Endpoint is available in the Google Play store. Before heading there, check your device to see if it's already installed.

If you can’t find the app in the Play store, contact your IT support person for help.

## Connect and disconnect from VPN

1. Open Microsoft Defender for Endpoint.
2. Sign in with your work account if prompted.
3. On the **Tunnel** screen, turn the **Status** toggle on or off to connect or disconnect from the VPN.

Your organization might require you to stay connected to Microsoft Tunnel. This is known as an *always-on* connection. If this is the case, the Status toggle will appear inactive, and you won't be able to disconnect from the VPN as long as you're connected to the internet.

Your organization might also enable *Strict Tunnel Mode*. When Strict Tunnel Mode is active, all internet access is blocked if the VPN connection drops. You must wait for the VPN to reconnect before you can use the internet or apps that require network access. This behavior is expected and helps protect your organization's data.

If the toggle is stuck in the off position, select **Help** &gt; **Send logs** and report the problem to your IT support person. For more details, see the [Send logs](microsoft-tunnel-android#send-logs) section in this article.

## Connection details

The following information appears on the **Connect** screen when Tunnel is connected.

- **Uptime**: How long the VPN connection has been running.
- **Data received**: How much data has been received through the VPN connection.
- **Data sent**: How much data has been sent through the VPN connection.

Tap **Details** to see the following information:

- **Address**: The server address for your VPN connection.
- **Device-wide connection**: When turned on, all network traffic to and from your device goes through the VPN connection.
- **Apps that use Tunnel**: If apps are listed, only network traffic to and from these apps go through the VPN connection.
- **Always-on**: When turned on, Microsoft Defender for Endpoint will continuously try to establish a connection.

## App settings

From the **Connect** screen, select the **Settings** gear icon to:

- Allow/block Microsoft from collecting usage and performance data.
- Turn verbose logging on/off.

## Get help in the app

Select **Help** from the menu at the bottom of the screen to:

- Access this article.
- Send logs to IT support to report a problem.

### Send logs

Send app logs to IT support to get help with an app or connection problem.

1. Select **Help** &gt; **Send logs**.
2. Select **Send logs** again. Your logs will be sent to a Microsoft database, from which your organization can access.
3. Select **EMAIL IT SUPPORT**.
4. On the Share screen, select your mail app.
5. In the body of the email, describe the problem you experienced so that the support team has an idea of what to look for.
6. Send the email.

## About Microsoft Tunnel

Tap your profile picture, and then select **About** to view the Microsoft Tunnel privacy policy, terms of use, and third-party notices.