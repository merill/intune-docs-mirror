---
layout: Conceptual
title: How to create VPN profiles - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/create-vpn-profiles
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
description: Learn how to create VPN profiles in Configuration Manager.
ms.date: 2022-03-29T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: d13e36f4-67a2-d5e2-7117-75777bb6c681
document_version_independent_id: 817beb73-da2e-85df-bb6f-38eb8c883a7d
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/create-vpn-profiles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/create-vpn-profiles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/create-vpn-profiles.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: efb86c84-d200-a258-06d1-2331791d1d58
---

# How to create VPN profiles - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Important

Starting in version 2203, this company resource access feature is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](../plan-design/resource-access-deprecation-faq).

Configuration Manager supports multiple VPN connection types. For more information on the connection types available for the different device platforms, see [VPN profiles](vpn-profiles).

For third-party VPN connections, distribute the VPN app before you deploy the VPN profile. If you don't deploy the app, users will be prompted to do so when they try to connect to the VPN. For more information, see [Deploy applications](../../apps/deploy-use/deploy-applications).

## Create a VPN profile

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, expand **Compliance Settings**, expand **Company Resource Access**, and select the **VPN Profiles** node.
2. On the **Home** tab of the ribbon, in the **Create** group, choose **Create VPN Profile**.
3. On the **General** page of the Create VPN Profile Wizard, specify the following information:

    - **Name**: Enter a unique name to identify the VPN profile in the console.

        Note

        Don't use the following characters in the VPN profile name: `\/:*?<>|; `. The Windows VPN profile doesn't support these special characters.
    - **Description**: Optionally enter a description to provide further information about the VPN profile.
    - **VPN profile type**: Select the appropriate platform.

        If you select the **Windows 8.1** platform, you can also **Import from file**. This action imports VPN profile information from an XML file. If you select this option, the rest of the wizard simplifies to the following pages: **Supported Platforms** and **Import VPN Profile**.
4. On the **Supported Platforms** page, select the OS versions that this VPN profile supports.
5. On the **Connection** page, specify the following information:

    - **Connection type**: Choose the VPN connection type. For more information on the supported types, see [VPN profiles](vpn-profiles).
    - **Server list**: Add a new server to use for the VPN connection. Depending on the connection type, you can add one or more VPN servers and specify which server is the default.
    - **Bypass VPN when connected to company network**: Configure clients to not use the VPN when they're on your internal network. If necessary, specify a connection-specific DNS name.
6. On the **Authentication Method** page of the wizard, choose a method that's supported by the connection type. The settings and available options on this page vary depending on the selected connection type. For more information, see Authentication method reference.
7. On the **Proxy Settings** page, if your VPN uses a proxy server, select one of the options as appropriate for your environment. Then provide the configuration information for the proxy.
8. The **Applications** page only applies to Windows 10 profiles. Add desktop and universal apps that automatically connect to this VPN. The type of app determines the app identifier:

    - For a *desktop app*, provide the file path of the app.
    - For a *universal app*, provide the package family name (PFN). To learn how to find the PFN for an app, see [Find a package family name for per-app VPN](find-a-pfn-for-per-app-vpn).

    You can also configure an option so that **Only the listed apps can use this VPN**.

    Important

    Secure all lists of associated apps that you compile for configuring a per-app VPN. If an unauthorized user changes your list, and you import it to the per-app VPN app list, you potentially authorize VPN access to apps that shouldn't have access.
9. The **Boundaries** page only applies to Windows 10 profiles to configure VPN boundaries. You can add the following options:

    - **Network traffic rules**: Set the protocols, local port, remote port, and address ranges to enable for the VPN connection.

        Note

        If you don't create a network traffic rule, all protocols, ports, and address ranges are enabled. After you create a rule, only the protocols, ports, and address ranges that you specify in that rule or in additional rules are used by the VPN connection.
    - **DNS names and servers**: DNS servers that are used by the VPN connection after the device establishes the connection.
    - **Routes**: Network routes that use the VPN connection. Creation of more than 60 routes may cause the policy to fail.
10. Complete the wizard.

The new VPN profile is displayed in the **VPN Profiles** node in the **Assets and Compliance** workspace.

## Authentication method reference

Available VPN authentication methods depend on the connection type:

### Certificates

If the client certificate authenticates to a RADIUS server, like a Network Policy Server, set the Subject Alternative Name in the certificate to the User Principal Name.

Supported connection types:

- Pulse Secure
- F5 Edge Client
- Dell SonicWALL Mobile Connect
- Check Point Mobile VPN

### Username and Password

Supported connection types:

- Pulse Secure
- F5 Edge Client
- Dell SonicWALL Mobile Connect
- Check Point Mobile VPN

### Microsoft EAP-TTLS

Supported connection types:

- Microsoft SSL (SSTP)
- Microsoft Automatic
- PPTP
- IKEv2
- L2TP

### Microsoft protected EAP (PEAP

Supported connection types:

- Microsoft SSL (SSTP)
- Microsoft Automatic
- IKEv2
- PPTP
- L2TP

### Microsoft secured password (EAP-MSCHAP v2)

Supported connection types:

- Microsoft SSL (SSTP)
- Microsoft Automatic
- IKEv2
- PPTP
- L2TP

### Smart Card or other certificate

Supported connection types:

- Microsoft SSL (SSTP)
- Microsoft Automatic
- IKEv2
- PPTP
- L2TP

### MSCHAP v2

Supported connection types:

- Microsoft SSL (SSTP)
- Microsoft Automatic
- IKEv2
- PPTP
- L2TP

### Use machine certificates

Supported connection types:

- IKEv2

### Additional authentication options

When the Windows client version supports it, the option to **Configure** the authentication method is available. This option opens the Windows properties window to configure the authentication method.

Depending on the selected options, you might be asked to specify more information, for example:

- **Remember the user credentials at each logon**: User credentials are remembered so that users don't have to enter them each time they connect.
- **Select a client certificate for client authentication**: Select a previously created client SCEP certificate profile to authenticate the VPN connection. For more information, see [Create PFX certificate profiles](create-certificate-profiles).