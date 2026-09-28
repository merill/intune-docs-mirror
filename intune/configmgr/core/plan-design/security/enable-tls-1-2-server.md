---
layout: Conceptual
title: Enable TLS 1.2 on servers - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-server
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
description: Information about how to enable Transport Layer Security (TLS) 1.2 for Configuration Manager site servers and remote site systems.
ms.date: 2024-06-20T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: b6cf928e-5f22-82a4-1abe-ea3e28d6369d
document_version_independent_id: f7696046-487d-945d-278c-fc12c25ecd84
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/security/enable-tls-1-2-server.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/security/enable-tls-1-2-server
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/security/enable-tls-1-2-server.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: cfa77c09-77e2-2c8e-cfd3-03a843bdb7b5
---

# Enable TLS 1.2 on servers - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (Current Branch)*

When enabling TLS 1.2 for your Configuration Manager environment, start with [enabling TLS 1.2 for the clients](enable-tls-1-2-client) first. Then, enable TLS 1.2 on the site servers and remote site systems second. Finally, test client to site system communications before potentially disabling the older protocols on the server side. The following tasks are needed for enabling TLS 1.2 on the site servers and remote site systems:

- Ensure that TLS 1.2 is enabled as a protocol for SChannel at the operating system level
- Update and configure the .NET Framework to support TLS 1.2
- Update SQL Server and client components
- Update Windows Server Update Services (WSUS)

For more information about dependencies for specific Configuration Manager features and scenarios, see [About enabling TLS 1.2](enable-tls-1-2).

## Ensure that TLS 1.2 is enabled as a protocol for SChannel at the operating system level

For the most part, protocol usage is controlled at three levels, the operating system level, the framework or platform level, and the application level. TLS 1.2 is enabled by default at the operating system level. Once you ensure that the .NET registry values are set to enable TLS 1.2 and verify the environment is properly utilizing TLS 1.2 on the network, you may want to edit the `SChannel\Protocols` registry key to disable the older, less secure protocols. For more information on disabling TLS 1.0 and 1.1, see [Configuring Schannel protocols in the Windows Registry](/en-us/dotnet/framework/network-programming/tls#configuring-schannel-protocols-in-the-windows-registry).

## Update and configure the .NET Framework to support TLS 1.2

### Determine .NET version

First, determine the installed .NET versions. For more information, see [Determine which versions and service pack levels of .NET Framework are installed](/en-us/troubleshoot/dotnet/framework/determine-dotnet-versions-service-pack-levels).

### Install .NET updates

Install the .NET updates so you can enable strong cryptography. Some versions of .NET Framework might require updates to enable strong cryptography. Use these guidelines:

- NET Framework 4.6.2 and later supports TLS 1.1 and TLS 1.2. Confirm the registry settings, but no additional changes are required.

    Note

    Starting in version 2107, Configuration Manager requires Microsoft .NET Framework version 4.6.2 for site servers, specific site systems, clients, and the console. If possible in your environment, install the latest version of .NET version 4.8.
- Update NET Framework 4.6 and earlier versions to support TLS 1.1 and TLS 1.2. For more information, see [.NET Framework versions and dependencies](/en-us/dotnet/framework/migration-guide/versions-and-dependencies).
- If you're using .NET Framework 4.5.1 or 4.5.2 on Windows 8.1, Windows Server 2012 R2, or Windows Server 2012, it's highly recommended that you install the latest security updates for the .Net Framework 4.5.1 and 4.5.2 to ensure TLS 1.2 can be enabled properly.

    For your reference, TLS 1.2 was first introduced into .Net Framework 4.5.1 and 4.5.2 with the following hotfix rollups:

    - For Windows 8.1 and Server 2012 R2: [Hotfix rollup 3099842](https://support.microsoft.com/topic/hotfix-rollup-3099842-for-the-net-framework-4-5-2-and-the-net-framework-4-5-1-on-windows-7b629c7e-bea4-4838-2512-e22e8bad368a)
    - For Windows Server 2012: [Hotfix rollup 3099844](https://support.microsoft.com/topic/hotfix-rollup-3099844-for-the-net-framework-4-5-2-4-5-1-and-4-5-on-windows-ee48ac0d-79be-28f7-563d-e7bd46040dd3)

### Configure for strong cryptography

Configure .NET Framework to support strong cryptography. Set the `SchUseStrongCrypto` registry setting to `DWORD:00000001`. This value disables the RC4 stream cipher and requires a restart. For more information about this setting, see [Microsoft Security Advisory 296038](/en-us/security-updates/SecurityAdvisories/2015/2960358).

Make sure to set the following registry keys on any computer that communicates across the network with a TLS 1.2-enabled system. For example, Configuration Manager clients, remote site system roles not installed on the site server, and the site server itself.

For 32-bit applications that are running on 32-bit OSs and for 64-bit applications that are running on 64-bit OSs, update the following subkey values:

```Registry
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v2.0.50727]
      "SystemDefaultTlsVersions" = dword:00000001
      "SchUseStrongCrypto" = dword:00000001
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\v4.0.30319]
      "SystemDefaultTlsVersions" = dword:00000001
      "SchUseStrongCrypto" = dword:00000001
```

For 32-bit applications that are running on 64-bit OSs, update the following subkey values:

```Registry
[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v2.0.50727]
      "SystemDefaultTlsVersions" = dword:00000001
      "SchUseStrongCrypto" = dword:00000001
[HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\v4.0.30319]
      "SystemDefaultTlsVersions" = dword:00000001
      "SchUseStrongCrypto" = dword:00000001
```

Note

The `SchUseStrongCrypto` setting allows .NET to use TLS 1.1 and TLS 1.2. The `SystemDefaultTlsVersions` setting allows .NET to use the OS configuration. For more information, see [TLS best practices with the .NET Framework](/en-us/dotnet/framework/network-programming/tls).

## Update SQL Server and client components

Microsoft SQL Server 2016 and later support TLS 1.1 and TLS 1.2. Earlier versions and dependent libraries might require updates. For more information, see [KB 3135244: TLS 1.2 support for Microsoft SQL Server](https://support.microsoft.com/topic/kb3135244-tls-1-2-support-for-microsoft-sql-server-e4472ef8-90a9-13c1-e4d8-44aad198cdbe).

Secondary site servers need to use at least SQL Server 2016 Express with Service Pack 2 (13.2.50.26) or later.

### SQL Server Native Client

Note

[KB 3135244](https://support.microsoft.com/topic/kb3135244-tls-1-2-support-for-microsoft-sql-server-e4472ef8-90a9-13c1-e4d8-44aad198cdbe) also describes requirements for SQL Server client components.

Make sure to also update the SQL Server Native Client to at least version SQL Server 2012 SP4 (11.\*.7001.0). This requirement is a [prerequisite check (warning)](../../servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client).

Configuration Manager uses SQL Server Native Client on the following site system roles:

- Site database server
- Site server: central administration site, primary site, or secondary site
- Management point
- Device management point
- State migration point
- SMS Provider
- Software update point
- Multicast-enabled distribution point
- Asset Intelligence update service point
- Reporting services point
- Enrollment point
- Endpoint Protection point
- Service connection point
- Certificate registration point
- Data warehouse service point

## Enable TLS 1.2 at-scale using Automanage Machine Configuration and Azure Arc

Automatically configures TLS 1.2 across both client and server for machines running in Azure, on-prem, or multi-cloud environments. To get started configuring TLS 1.2 across your machines, [connect them to Azure using Azure Arc-enabled servers](/en-us/azure/azure-arc/servers/learn/quick-enable-hybrid-vm), which comes with the Machine Configuration prerequisite by default. Once connected, TLS 1.2 can be configured with point-and-click simplicity by deploying the built-in policy definition in Azure Portal: [Configure secure communication protocols (TLS 1.1 or TLS 1.2) on Windows servers](https://ms.portal.azure.com/#view/Microsoft_Azure_Policy/PolicyDetailBlade/definitionId/%2Fproviders%2FMicrosoft.Authorization%2FpolicyDefinitions%2F828ba269-bf7f-4082-83dd-633417bc391d). The policy scope can be assigned at the subscription, resource group, or management group level, as well as exclude any resources from the policy definition.

After the configuration has been assigned, the compliance status of your resources can be viewed in detail by navigating to the Guest Assignments page and scoping down to the impacted resources.

For a detailed, step-by-step tutorial, see [Consistently upgrade your server TLS protocol using Azure Arc and Automanage Machine Configuration](https://techcommunity.microsoft.com/t5/azure-arc-blog/consistently-upgrade-your-server-tls-protocol-using-azure-arc/ba-p/3664217).

## Update Windows Server Update Services (WSUS)

TLS 1.2 is supported by default for WSUS on all [currently supported version](/en-us/windows-server/get-started/windows-server-release-info) of Windows Server.

To support TLS 1.2 in earlier versions of WSUS, install the following update on the WSUS server:

- For WSUS server that's running Windows Server 2012, install [update 4022721](https://support.microsoft.com/topic/june-27-2017-kb4022721-preview-of-monthly-rollup-16a4b074-5202-c1c3-2c8a-34c1edd452f8) or a later rollup update.
- For WSUS server that's running Windows Server 2012 R2, install [update 4022720](https://support.microsoft.com/topic/june-27-2017-kb4022720-preview-of-monthly-rollup-b98970bb-6f11-46c3-8681-a6b85d5d8eb4) or a later rollup update.

Note

On October 10th, 2023, Windows Server 2012 and Windows Server 2012 R2 entered the Extended Support Updates phase. Microsoft will no longer provide support for Configuration Manager site servers or roles installed to these Operating Systems. For more information, see **[Extended Security Updates and Configuration Manager](/en-us/mem/configmgr/core/plan-design/configs/supported-operating-systems-for-clients-and-devices)**.