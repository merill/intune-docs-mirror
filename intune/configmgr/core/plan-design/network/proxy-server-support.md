---
layout: Conceptual
title: Proxy server support - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/network/proxy-server-support
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
description: Learn how Configuration Manager systems use proxy servers.
ms.date: 2026-06-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: c7038be9-dfd9-c75b-1224-f54a06dcef1a
document_version_independent_id: b33009c7-4ed4-21ca-d786-43f746c4a638
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/network/proxy-server-support.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/network/proxy-server-support
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/network/proxy-server-support.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68ec7f3a-2bc6-459f-b959-19beb729907d
- https://authoring-docs-microsoft.poolparty.biz/devrel/0b654e73-5728-4af3-8c2e-17bfbf4c9f23
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/90370425-aca4-4a39-9533-d52e5e002a5d
- https://authoring-docs-microsoft.poolparty.biz/devrel/11529658-843a-40bd-b2f8-5eed118be619
platformId: 9350a2ad-8f78-8407-c5ed-ba3f498c7ea6
---

# Proxy server support - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Some Configuration Manager components require connections to the internet. If your environment requires internet traffic to use a proxy server, configure these systems to use the proxy.

- A computer that hosts a site system server supports a single proxy server configuration. All site system roles on that computer share this same proxy configuration. If you need separate proxy servers for different roles or instances of a role, place those roles on separate site system servers.
- When you configure new proxy server settings for a site system server that already has a proxy server configuration, the original configuration is overwritten.
- By default, connections to the proxy use the **System** account of the computer that hosts the site system role.
- If the computer account can't authenticate, the site system server can store user credentials to connect to the proxy server. These credentials are the **site system proxy server account**.
- If you install the Configuration Manager console on administrative workstations, some connections will use the proxy configuration.

## Site system roles that use a proxy

The following site system roles connect to the internet, and if necessary, can use a proxy server:

### Asset Intelligence synchronization point

Important

Starting in November 2021, this feature of Configuration Manager is deprecated. For more information, see [Asset intelligence deprecation](../../clients/manage/asset-intelligence/deprecation).

This site system role connects to Microsoft and uses a proxy server configuration on the computer that hosts the Asset Intelligence synchronization point.

### Cloud distribution point

Note

The cloud-based distribution point (CDP) is deprecated. Starting in version 2107, you can't create new CDP instances. To provide content to internet-based devices, enable a cloud management gateway (CMG) to distribute content. For more information, see [Deprecated features](../changes/deprecated/removed-and-deprecated-cmfeatures#deprecated-features).

The cloud distribution point role runs in Microsoft Azure. You don't configure this site system role to use a proxy. Set the proxy configuration on the primary site server that manages the cloud distribution point.

For this configuration, the primary site server:

- Must be able to connect to Microsoft Azure to set up, monitor, and distribute content to the cloud distribution point.
- By default, uses the computer's **System** account to make the connection. It can also use the site system proxy server account, if necessary.
- Uses Windows web browser APIs.

### Cloud management gateway connection point

The cloud management gateway (CMG) connection point is an on-premises role that communicates with the CMG service in Azure. For more information, see [Overview of CMG](../../clients/manage/cmg/overview).

### Distribution point

If you enable a Configuration Manager distribution point for Microsoft Connected Cache, it can communicate through a proxy server for internet access starting from [Configuration Manager version 2603](../../../hotfix/2603/37426535) or after installing [KB33247081](../../../hotfix/2509/33247081). Previous releases require a direct internet connection or a proxy that supports relative URIs. For more information, see [Microsoft Connected Cache](../hierarchy/microsoft-connected-cache).

### Exchange Server connector

This site system role connects to an Exchange Server. It uses a proxy server configuration on the computer that hosts the Exchange Server connector.

### Management point
Starting in version 2603, the management point uses Microsoft Identity Service Essentials (MISE) for Microsoft Entra token validation. In environments that support Microsoft Entra joined users and devices, the management point server requires internet access to connect to Microsoft Entra authentication endpoints. For the list of endpoints to allow, see [Management point internet access requirements](internet-endpoints.md#management-point). 
Microsoft Entra token validation runs in the **system (Local System) context** using the .NET Framework HTTP stack. As a result, if the management point reaches the internet through a proxy, the proxy must be available to the Local System account through its **WinINET (Windows Internet, or Internet Options) settings**.

Important

In version 2603, the following proxy configurations are **not** used for MISE token validation:

- The proxy configured in the site system properties.
- A machine-wide WinHTTP proxy set with `netsh winhttp set proxy`.

You must configure the proxy in the **Local System account's WinINET settings** on the management point server, as described in this section.

#### Configure the system-context WinINET proxy

Use one of the following methods to set the proxy for the Local System account on the management point server:

- **Registry**: Set the following values under `HKEY_USERS\S-1-5-18\Software\Microsoft\Windows\CurrentVersion\Internet Settings`:

    - `ProxyEnable` (DWORD) = `1`
    - `ProxyServer` (String) = `<proxyservername>:<portnumber>`, for example `proxy.domain.example.com:80`
    - `ProxyOverride` (String) = optional proxy bypass list, for example `<local>`
- **Internet Options in the system context**: Open Internet Options as the Local System account and configure the LAN proxy. For example, use [PsExec](/en-us/sysinternals/downloads/psexec) to launch the browser as the system account:

    ```cmd
    PsExec.exe -i -s "C:\Program Files\Internet Explorer\iexplore.exe"
    ```

    Then go to **Internet Options** &gt; **Connections** &gt; **LAN settings** and configure the proxy server.

After you change the proxy, restart the `SMS_EXECUTIVE` service on the management point for the new setting to take effect.

#### Verify and troubleshoot

If the management point can't reach the Microsoft Entra endpoints, the `CCM_STS_ManagedBase.log` on the management point logs a `MISE12034` error with an underlying `SocketException` or `HttpRequestException`. Microsoft Entra joined clients then fail to get a token and log a transient error such as `0x87d00231` in `ClientIDManagerStartup`.

To confirm connectivity from the management point in the system context, run the following command as the Local System account (for example, using `PsExec.exe -i -s cmd`):

```powershell
Invoke-WebRequest "https://login.microsoftonline.com/<TenantID>/.well-known/openid-configuration" -UseBasicParsing
```

Note

This system-context proxy requirement is specific to version 2603. A future update is planned to let MISE token validation use the proxy configured in the site system properties.

For more information about this requirement, see [Management point requires internet access for Microsoft Entra token validation](../changes/whats-new-in-version-2603#management-point-requires-internet-access-for-microsoft-entra-token-validation).

### Service connection point

This site system role connects to the Configuration Manager cloud service to download version updates for Configuration Manager. It uses a proxy server that's configured on the computer that hosts the service connection point.

### Software update point

This site system role uses the proxy when it connects to Microsoft Update to download patches and synchronize information about updates. Like every other site system role, first configure the site system proxy settings. Then configure the following options specific to the software update point:

- **Use a proxy server when synchronizing software updates**
- **Use a proxy server when downloading content by using automatic deployment rules**

    Note

    While available for use, this setting isn't used by software update points at secondary sites.

These settings are on the **Proxy and Account Settings** tab of the software update point properties.

Note

By default, when the automatic deployment rules run, the **System** account on the site server of the site on which an automatic deployment rule was created is used to connect to the internet and download software updates. Alternatively, configure and use the site system proxy server account.

When this account cannot access the internet, software updates fail to download. The following entry is logged to **ruleengine.log**: `Failed to download the update from internet. Error = 12007.`

## Other features that use the proxy

The following features use the proxy of the site system that hosts the service connection point role: 

- [Microsoft Entra user discovery](../../servers/deploy/configure/about-discovery-methods#azureaddisc)
- [Microsoft Entra user group discovery](../../servers/deploy/configure/about-discovery-methods#bkmk_azuregroupdisco)
- [Synchronizing collection membership results to Microsoft Entra groups](../../clients/manage/collections/create-collections#bkmk_aadcollsync)

## Configure the proxy for a site system server

1. In the Configuration Manager console, go to the **Administration** workspace. Expand **Site Configuration**, and then select the **Servers and Site System Roles** node.
2. Select the site system server that you want to edit. In the details pane, right-click the **Site system** role, and select **Properties**.
3. In Site system Properties, switch to the **Proxy** tab. Configure the following proxy settings:

    - **Use a proxy server when synchronizing information from the internet**: Select this option to enable the site system server to use a proxy server.
    - **Proxy server name**: Specify the hostname or FQDN of the proxy server in your environment.
    - **Port**: Specify the network port on which to communicate with the proxy server. By default, it uses port **80**.
    - **Use credentials to connect to the proxy server**: Many proxy servers require a user to authenticate. By default, the site system server uses its computer account to connect to the proxy server. If necessary, enable this option, click **Set**, and then choose an **Existing Account** or specify a **New Account**. These credentials are the **site system proxy server account**. For more information, see [Accounts used in Configuration Manager](../hierarchy/accounts).
4. Choose **OK** to save the new proxy server configuration.

## Configuration Manager console

If you install the Configuration Manager console on an administrative workstation, some connections will use the proxy configuration. The console may fail to connect to the site because of a proxy configuration. To help troubleshoot, you can modify the console configuration file, `Microsoft.ConfigurationManagement.exe.config`. By default, this file is located in `C:\Program Files (x86)\Microsoft Endpoint Manager\AdminConsole\bin`. Open it in Windows Notepad or another XML editor.

Change this original setting:

```xml
  <system.net>
    <defaultProxy useDefaultCredentials="true" />
  </system.net>
```

Add the following element with the `defaultProxy` element: `<proxy usesystemdefault="False"/></defaultProxy>`

For example:

```xml
  <system.net>
    <defaultProxy useDefaultCredentials="true"><proxy usesystemdefault="False"/></defaultProxy>
  </system.net>
```