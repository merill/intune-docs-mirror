---
layout: Conceptual
title: What's new in version 2603 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/whats-new-in-version-2603
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
description: Get details about changes and new capabilities introduced in version 2603 of Configuration Manager current branch.
ms.date: 2026-08-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ms.collection: tier3
locale: en-us
document_id: 7a8e4919-f740-2759-4274-083403ac7bfa
document_version_independent_id: 7a8e4919-f740-2759-4274-083403ac7bfa
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/changes/whats-new-in-version-2603.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/changes/whats-new-in-version-2603
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/changes/whats-new-in-version-2603.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: f4c2f8bc-7533-48a5-6603-cd2b166fdae0
---

# What's new in version 2603 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Update 2603 for Configuration Manager current branch is available as an in-console update. Apply this update on sites that run version 2409 or later.

Always review the latest checklist for installing this update. For more information, see [Checklist for installing update 2603](../../servers/manage/checklist-for-installing-update-2603). After you update a site, also review the [Post-update checklist](../../servers/manage/checklist-for-installing-update-2603#post-update-checklist).

To take full advantage of new Configuration Manager changes, after you update the site, also update clients to the latest version. New functionality appears in the Configuration Manager console when you update the site and console, but the complete scenario isn't functional until the client version is also the latest.

## General enhancements

As part of Microsoft's Secure Future Initiative (SFI) the 2603 version of Configuration Manager continues to focus on security, quality, and infrastructure modernization. For more information, see the [Microsoft Trust Center](https://www.microsoft.com/trust-center/security/secure-future-initiative). For a list of significant customer-reported issues resolved in this release, see the [Summary of changes in Configuration Manager version 2603](../../../hotfix/2603/37426535) knowledge base article.

### Security improvements for Network Access Account

This update enhances security by improving access controls for the Network Access Account (NAA). Access to NAA information is now restricted to supported OSD media task sequence scenarios by enforcing additional permission requirements and removing legacy access paths to reduce exposure and align with least privilege principles. For more information, see [KB 37447175](../../../hotfix/2503/37447175).

### Weak ciphers disabled on Cloud Management Gateway

Weak DHE (Diffie-Hellman Ephemeral) cipher suites are now disabled on Cloud Management Gateway (CMG) instances. Only TLS 1.3 (AES\_256\_GCM, AES\_128\_GCM) and TLS 1.2 ECDHE ciphers remain enabled, improving the security posture of CMG connections.

Additionally, the `EnableCertPaddingCheck` registry keys are now set by default on CMG Virtual Machine Scale Set instances to mitigate CVE-2013-3900 (WinVerifyTrust Signature Validation Vulnerability).

### SQL Server 2025 support

SQL Server 2025 (RTM) is now a supported database platform for Configuration Manager sites, including the central administration site, primary sites, and secondary sites. SQL Server 2025 Express is also supported for secondary sites. The recommended database compatibility level for SQL Server 2025 is 160. For more information, see [Support for SQL Server versions](../configs/support-for-sql-server-versions).

### SQL Server Native Client dependency removed

All Configuration Manager components and site roles are updated to remove the dependency on the deprecated SQL Server Native Client (sqlncli.msi). Customers can now safely uninstall sqlncli from site systems. The product no longer includes sqlncli.msi in its redistributables.

### SQL Server Management Objects updated

The Microsoft SQL Server Management Objects and Microsoft System CLR Types for SQL Server are updated from the deprecated SQL Server 2014 versions to the SQL Server 2025 versions (SMO 17). The `SQLSysClrTypes.msi` and `SharedManagementObjects.msi` files are no longer included in the Configuration Manager redistributable files. After updating to version 2603, customers can safely uninstall these legacy MSI packages. The required files are now included in the Configuration Manager installation package.

### PKI certificate support for site system-to-SQL Server communication

Added support and testing for PKI certificates used in site system-to-SQL Server communication. This includes proper handling of certificate trust, private key access, and BitLocker Management portal registry thumbprint configuration.

### ARM64 support improvements

- The `Import-CMDriver` PowerShell cmdlet now correctly includes ARM64 platform support when importing drivers from INF files. Previously, ARM64 was filtered out from the Supported Platforms list.
- Client push installation (CcmSetup) no longer fails with error code `0x80070643` on Windows 11 ARM64 devices when upgrading from ConfigMgr 2409 or 2503.

### Cloud Management Gateway improvements

- The `New-CMCloudManagementGateway` PowerShell cmdlet now allows combining the `-IsUsingExistingGroup $true` parameter with `-ServerAppClientId`, enabling automated CMG deployment into existing Azure resource groups without requiring interactive credentials.
- CMG deployment error handling is improved to capture and display detailed Azure error response information when Attribute-Based Access Control (ABAC) conditions block role assignments.
- The CMG outbound traffic alert and "Total Outbound data" metric now work correctly for CMGv2 (Azure Virtual Machine Scale Sets-based) deployments.

### Updated Feedback experience

The Configuration Manager console In-App Feedback feature is updated to support the new OCV Feedback SDK with authenticated submissions. Both authenticated and offline feedback submission modes are supported.

### Deprecated and removed features

- An internal service required for device compliance checks will be deprecated in October 2026. Following the deprecation, compliance checks in Software Center may fail in co-managed environments where the Compliance workload is managed by Intune. To prevent this issue, apply this update before October 2026.
- The deprecated Asset Intelligence synchronization point site role is removed from the site roles selection UI.
- The Software Update Health Troubleshooting Dashboard is hidden in this release due to performance issues in large environments.

## New requirements

### Management point requires internet access for Microsoft Entra token validation

Starting in version 2603, the management point uses Microsoft Identity Service Essentials (MISE) for Microsoft Entra token validation. This change requires the management point server to have internet access. In previous versions, the management point could function without internet access.

This requirement applies to environments that meet the following conditions:

- The site is configured to support Microsoft Entra joined users and devices
- Clients authenticate using Microsoft Entra tokens, typically through a cloud management gateway (CMG)

Note

Environments that only use on-premises Active Directory authentication without Microsoft Entra integration aren't affected by this requirement.

#### Identify the issue

If the management point server can't reach the required endpoints, the `CCM_STS_ManagedBase.log` on the management point logs a `MiseAuthenticationTicketProviderException` with an underlying network error. Look for the `SocketException` or `HttpRequestException` that indicates a network connectivity failure, for example:

```text
Microsoft.Identity.ServiceEssentials.Exceptions.MiseAuthenticationTicketProviderException: MISE12034: AuthenticationTicketProvider Name:AuthenticationTicketProvider
System.Net.Sockets.SocketException: No connection could be made because the target machine actively refused it
```

Important

The `MISE12034` exception can also appear for other reasons. This section specifically addresses the case where the underlying exception indicates a network connectivity problem, such as `SocketException`, `HttpRequestException`, or a connection timeout. Verify that the error message points to a network access issue before applying the resolution below.

#### Resolution: Allow access to Azure authentication endpoints

Ensure that the management point server can connect to Microsoft Entra authentication endpoints in the system context. Allow the following URLs through the proxy and firewall:

- `https://login.microsoftonline.com`
- `https://sts.windows.net`

If the management point server uses a proxy, you must configure the proxy in the system (Local System) context. The proxy set in the site system properties and a WinHTTP-only proxy (`netsh winhttp set proxy`) aren't used for this validation path in version 2603. For the required configuration steps, see [Management point proxy configuration](../network/proxy-server-support#management-point).

For a full list of required endpoints, see [Management point internet access requirements](../network/internet-endpoints#management-point).