---
layout: Conceptual
title: Configure proxy settings for the Intune Connector for Active Directory | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/autopilot/autopilot-hybrid-connector-proxy
author: lenewsad
ms.author: lanewsad
ms.reviewer: madakeva
manager: laurawi
ms.service: windows-client
ms.subservice: autopilot
ms.suite: ems
breadcrumb_path: /autopilot/breadcrumb/toc.json
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472
feedback_system: Standard
permissioned-type: public
uhfHeaderId: MSDocsHeader-Windows
description: Covers how to configure the Intune Connector for Active Directory to work with existing on-premises proxy servers.
ms.date: 2025-11-24T00:00:00.0000000Z
ms.collection:
- M365-modern-desktop
ms.topic: how-to
locale: en-us
document_id: 444c927b-4376-bb7f-0b52-6fabb60e4e94
document_version_independent_id: 444c927b-4376-bb7f-0b52-6fabb60e4e94
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/autopilot/autopilot-hybrid-connector-proxy.md
site_name: Docs
depot_name: MSDN.autopilot
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.autopilot/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: autopilot-hybrid-connector-proxy
moniker_range_name: 
monikers: []
item_type: Content
source_path: autopilot/autopilot-hybrid-connector-proxy.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: 14ef6cf5-8cc5-ad70-6675-1e6957e01fc7
---

# Configure proxy settings for the Intune Connector for Active Directory | Microsoft Learn

This article explains how to configure the Intune Connector for Active Directory to work with outbound proxy servers. The article is intended for customers with network environments that have existing proxies.

By default, the Intune Connector for Active Directory attempts to automatically locate a proxy server on the network using Web Proxy Auto-Discovery (WPAD). If WPAD is configured in the network, other configuration might not be required. When changes are needed, the following sections describe how to override the default settings, using [the standard .NET Framework capabilities for configuring proxy settings](/en-us/dotnet/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings). More options are described in that documentation.

For more information about how connectors work, see [Understand Microsoft Entra application proxy connectors](/en-us/azure/active-directory/manage-apps/application-proxy-connectors).

## Completely bypass outbound proxies

You can configure the connector to bypass your on-premises proxy to ensure it uses direct connectivity to the Azure services. We recommend this approach, as long as your network policy allows for it, because it means that you have one less configuration to maintain.

To disable outbound proxy usage for the connector, edit the `:ProgramFiles%\Microsoft Intune\ODJConnector\ODJConnectorEnrollmentWizard\ODJConnectorEnrollmentWizard.exe.config` file and set the default proxy to `"False"` as shown in the following code example:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>
        <defaultProxy>
            <defaultProxy enabled="False" />
        </defaultProxy>
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```

To ensure that the Connector Updater service also bypasses the proxy, make a similar change to C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>
        <defaultProxy>
            <defaultProxy enabled="False" />
        </defaultProxy>
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

Be sure to make copies of the original files, in case you need to revert to the default .config files.

Once the configuration files are modified, the Intune Connector for Active Directory service needs to be restarted.

1. Open **services.msc**.
2. Find and select the **Intune ODJConnector Service**.
3. Select **Restart**.

## Specifying an alternative proxy server

If a different proxy server needs to be used with the Intune Connector for Active Directory, for example one that bypasses authentication, the different proxy server can be specified in a similar manner. To use a different proxy, edit the `:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorEnrollmentWizard\ODJConnectorEnrollmentWizard.exe.config` file and add the proxy address and proxy port in the section shown in this code sample:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>
        <defaultProxy>
            <proxy proxyaddress="<https://PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>
        </defaultProxy>
    </system.net>
    <runtime>
        <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
            <dependentAssembly>
                <assemblyIdentity name="mscorlib" publicKeyToken="b77a5c561934e089" culture="neutral"/>
                <bindingRedirect oldVersion="0.0.0.0-2.0.0.0" newVersion="4.6.0.0" />
            </dependentAssembly>
        </assemblyBinding>
    </runtime>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="SignInURL" value="https://portal.manage.microsoft.com/Home/ClientLogon"/>
        <add key="LocationServiceEndpoint" value="RestUserAuthLocationService/RestUserAuthLocationService/ServiceAddresses"/>
    </appSettings>
</configuration>
```

To ensure that the Connector Updater service also bypasses the proxy, make a similar change to C:\Program Files\Microsoft Intune\ODJConnector\ODJConnectorSvc\ODJConnectorSvc.exe.config.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <system.net>
        <defaultProxy>
            <proxy proxyaddress="<https://PROXY ADDRESS HERE>:<PORT HERE>" bypassonlocal="True" usesystemdefault="True"/>
        </defaultProxy>
    </system.net>
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" />
    </startup>
    <appSettings>
        <add key="BaseServiceAddress" value="https://manage.microsoft.com/" />
    </appSettings>
</configuration>
```

Be sure to make copies of the original files, in case you need to revert to the default .config files.

Once the configuration files are modified, the Intune Connector for Active Directory service needs to be restarted.

1. Open **services.msc**.
2. Find and select the **Intune ODJConnector Service**.
3. Select **Restart**.