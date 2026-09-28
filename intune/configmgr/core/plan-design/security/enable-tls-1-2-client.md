---
layout: Conceptual
title: How to enable Transport Layer Security (TLS) 1.2 on clients - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-client
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
description: Information about how to enable TLS 1.2 for Configuration Manager clients.
ms.date: 2024-10-18T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: e9cd2b28-4c0a-2898-1a0d-b81f00313e2e
document_version_independent_id: 074ace6c-71cb-a777-e2b6-17f9fdc9241c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/security/enable-tls-1-2-client.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/security/enable-tls-1-2-client
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/security/enable-tls-1-2-client.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: f3c50c83-815e-95fe-fec2-92be1ac9ddaa
---

# How to enable Transport Layer Security (TLS) 1.2 on clients - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (Current Branch)*

When enabling TLS 1.2 for your Configuration Manager environment, start by ensuring the clients are capable and properly configured to use TLS 1.2 before enabling TLS 1.2 and disabling the older protocols on the site servers and remote site systems. There are three tasks for enabling TLS 1.2 on clients:

- Update Windows and WinHTTP
- Ensure that TLS 1.2 is enabled as a protocol for SChannel at the operating system level
- Update and configure the .NET Framework to support TLS 1.2

For more information about dependencies for specific Configuration Manager features and scenarios, see [About enabling TLS 1.2](enable-tls-1-2).

## Update Windows and WinHTTP

Windows 8.1, Windows Server 2012 R2, Windows 10, Windows Server 2016, and later versions of Windows natively support TLS 1.2 for client-server communications over WinHTTP.

Earlier versions of Windows, such as Windows 7 or Windows Server 2012, don't enable TLS 1.1 or TLS 1.2 by default for secure communications using WinHTTP. For these earlier versions of Windows, install [Update 3140245](https://support.microsoft.com/topic/update-to-enable-tls-1-1-and-tls-1-2-as-default-secure-protocols-in-winhttp-in-windows-c4bd73d2-31d7-761e-0178-11268bb10392) to enable the registry value below, which can be set to add TLS 1.1 and TLS 1.2 to the default secure protocols list for WinHTTP. With the patch installed, create the following registry values:

Important

Enable these settings on all clients running earlier versions of Windows *before* enabling TLS 1.2 and disabling the older protocols on the Configuration Manager servers. Otherwise, you can inadvertently orphan them.

Verify the value of the `DefaultSecureProtocols` registry setting, for example:

```Registry
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp\
      DefaultSecureProtocols = (DWORD): 0xAA0
HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Windows\CurrentVersion\Internet Settings\WinHttp\
      DefaultSecureProtocols = (DWORD): 0xAA0
```

If you change this value, restart the computer.

The example above shows the value of `0xAA0` for the WinHTTP `DefaultSecureProtocols` setting. [Update to enable TLS 1.1 and TLS 1.2 as default secure protocols in WinHTTP in Windows](https://support.microsoft.com/topic/update-to-enable-tls-1-1-and-tls-1-2-as-default-secure-protocols-in-winhttp-in-windows-c4bd73d2-31d7-761e-0178-11268bb10392) lists the hexadecimal value for each protocol. By default in Windows, this value is `0x0A0` to enable SSL 3.0 and TLS 1.0 for WinHTTP. The above example keeps these defaults, and also enables TLS 1.1 and TLS 1.2 for WinHTTP. This configuration ensures that the change doesn't break any other application that might still rely on SSL 3.0 or TLS 1.0. You can use the value of `0xA00` to only enable TLS 1.1 and TLS 1.2. Configuration Manager supports the most secure protocol that Windows negotiates between both devices.

If you want to completely disable SSL 3.0 and TLS 1.0, use the SChannel disabled protocols setting in Windows. For more information, see [Restrict the use of certain cryptographic algorithms and protocols in Schannel.dll](/en-us/troubleshoot/windows-server/windows-security/restrict-cryptographic-algorithms-protocols-schannel).

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