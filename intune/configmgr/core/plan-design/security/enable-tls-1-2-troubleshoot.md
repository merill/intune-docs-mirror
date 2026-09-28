---
layout: Conceptual
title: Common issues when enabling TLS 1.2 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/security/enable-tls-1-2-troubleshoot
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
description: Describes common issues when enabling Transport Layer Security (TLS) 1.2
ms.date: 2021-05-04T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: troubleshooting
ms.collection: tier3
locale: en-us
document_id: 7cbe4a4a-6e34-dd2d-9b7c-e2db56b1a608
document_version_independent_id: 31cee73d-5adf-1e8b-4de7-e201f0d24a92
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/security/enable-tls-1-2-troubleshoot.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/security/enable-tls-1-2-troubleshoot
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/security/enable-tls-1-2-troubleshoot.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 60b1d1aa-e9a0-1985-386d-39d42fdffdcd
---

# Common issues when enabling TLS 1.2 - Configuration Manager | Microsoft Learn

This article provides advice for common issues that occur when you enable TLS 1.2 support in Configuration Manager.

## Unsupported platforms

The following client platforms are supported by Configuration Manager but aren't supported in a TLS 1.2 environment:

- Apple OS X
- Windows devices managed with on-premises MDM

## Reports don't show in the console

If reports don't show in the Configuration Manager console, make sure to update the computer on which you're running the console. [Update the .NET Framework](enable-tls-1-2-client#bkmk_net), and enable strong cryptography.

## FIPS security policy enabled

If you enable the FIPS security policy setting for either the client or a server, Secure Channel (Schannel) negotiation can cause them to use TLS 1.0. This behavior happens even if you disable the protocol in the registry.

To investigate, enable Secure Channel event logging, and then review Schannel events in the system log. For more information, see [Restrict the use of certain cryptographic algorithms and protocols in Schannel.dll](/en-us/troubleshoot/windows-server/windows-security/restrict-cryptographic-algorithms-protocols-schannel).

## SQL Server communication failure

If SQL Server communication fails and returns an **SslSecurityError** error, verify the following settings:

- [Update .NET Framework](enable-tls-1-2-server#bkmk_net), and enable strong cryptography on each machine
- [Update SQL Server](enable-tls-1-2-server#bkmk_sql) on the host server
- [Update SQL Server client components](enable-tls-1-2-server#bkmk_sql-client) on all systems that communicate with SQL. For example, the site servers, SMS provider, and site role servers.

## Configuration Manager client communication failures

If the Configuration Manager client doesn't communicate with site roles, verify that you [updated Windows](enable-tls-1-2-client#bkmk_winhttp) to support TLS 1.2 for client-server communication by using WinHTTP. Common site roles include distribution points, management points, and state migration points.

## Reporting services point fails and returns an expected error

If the reporting services point doesn't configure reports, check the **SRSRP.log** for the following error entry:

`The underlying connection was closed:``An expected error occurred on a receive.`

To resolve this issue, follow these steps:

1. [Update .NET Framework](enable-tls-1-2-client#bkmk_net), and enable strong cryptography on all relevant computers.
2. After you install any updates, restart the SMS\_Executive service.

## Service connection point upload failures

If the service connection point doesn't upload data to SCCMConnectedService, [update the .NET Framework](enable-tls-1-2-server#bkmk_net), and enable strong cryptography on each computer. After you make the changes, remember to restart the computers.

## Configuration Manager console displays Intune onboarding dialog box

If the Intune onboarding dialog box appears when the console tries to connect to the Microsoft Intune admin center, [update the .NET Framework](enable-tls-1-2-client#bkmk_net), and enable strong cryptography on each computer. After you make the changes, remember to restart the computers.

## Configuration Manager console displays failure to sign in to Azure

When you try to create applications in Microsoft Entra ID, if the Azure Services onboarding dialog box immediately fails after you select **Sign in**, [update the .NET Framework](enable-tls-1-2-server#bkmk_net), and enable strong cryptography. After you make the changes, remember to restart the computers.

## Configuration Manager cloud services and TLS 1.2

The Azure virtual machines used by the cloud management gateway support TLS 1.2. Supported client versions automatically use TLS 1.2.

The **SMSAdminui.log** may contain an error similar to the following example:

```Log
Microsoft.ConfigurationManager.CloudBase.AAD.AADAuthenticationException
Service returned error. Check InnerException for more details
at Microsoft.ConfigurationManager.CloudBase.AAD.AADAuthenticationContext.GetAADAuthResultObject
...
Microsoft.IdentityModel.Clients.ActiveDirectory.AdalServiceException
Service returned error. Check InnerException for more details
at Microsoft.IdentityModel.Clients.ActiveDirectory.AuthenticationContext.RunAsyncTask
...
System.Net.WebException
The underlying connection was closed: An unexpected error occurred on a receive.
at System.Net.HttpWebRequest.GetResponse
```

In the System EventLog, SChannel EventID 36874 may be logged with the following description: `An TLS 1.2 connection request was received from a remote client application, but none of the cipher suites supported by the client application are supported by the server. The TLS connection request has failed.`