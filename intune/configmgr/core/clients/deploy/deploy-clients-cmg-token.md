---
layout: Conceptual
title: Token-based authentication for CMG - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/deploy-clients-cmg-token
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
description: Register a client on the internal network for a unique token or create a bulk registration token for internet-based devices.
ms.date: 2025-12-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 60a7510b-10d9-e7e2-f848-d57d69d7fe10
document_version_independent_id: d4e9a557-ca23-3727-52b8-b81c6f767757
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/deploy-clients-cmg-token.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/deploy-clients-cmg-token
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/deploy-clients-cmg-token.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/1433a524-c01f-4b87-beab-670c040dea4f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/312f1f05-a431-4193-8a4d-e6245d5966de
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
platformId: a4f0f1c8-f139-07f5-2ab4-e6977c782371
---

# Token-based authentication for CMG - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The cloud management gateway (CMG) supports many types of clients, but even with [Enhanced HTTP](../../plan-design/hierarchy/enhanced-http), these clients require a [client authentication certificate](../manage/cmg/configure-authentication#pki-certificate). This certificate requirement can be challenging to provision on internet-based clients that don't often connect to the internal network, aren't able to join Microsoft Entra ID, and don't have a method to install a PKI-issued certificate.

To overcome these challenges, Configuration Manager extends its device support by issuing its own authentication tokens to devices. To take full advantage of this feature, after you update the site, also update clients to the latest version. The complete scenario isn't functional until the client version is also the latest. If necessary, make sure you [promote the new client version to production](../manage/upgrade/test-client-upgrades#promote-a-new-client-to-production).

Clients initially register for these tokens using one of the following two methods:

- Internal network
- Bulk registration

The Configuration Manager client together with the management point manage this token, so there's no OS version dependency at client level. This feature is available for any [supported client OS version](../../plan-design/configs/supported-operating-systems-for-clients-and-devices).

Note

These methods only support device-centric management scenarios.

Microsoft recommends joining devices to Microsoft Entra ID. Internet-based devices can use Microsoft Entra ID to authenticate with Configuration Manager. It also enables both device and user scenarios whether the device is on the internet or connected to the internal network. For more information, see [Install and register the client using Microsoft Entra identity](deploy-clients-cmg-azure#install-and-register-the-client-using-azure-ad-identity).

Make sure to **Enable clients to use a cloud management gateway** in the **Cloud services** group of client settings. Even with a site token, clients can't communicate with a CMG if client settings don't allow it. For more information, see [About client settings: Cloud services](about-client-settings#cloud-services).

## Internal network registration

This method requires the client to first register with the management point on the internal network. Client registration typically happens right after installation. The management point gives the client a unique token that shows it's using a self-signed certificate. When the client roams onto the internet, to communicate with the CMG it pairs its self-signed certificate with the management point-issued token.

This behavior is enabled by default on the Hierarchy.

Note

With an HTTPS management point, the client needs to first register regardless of internet/intranet management point. The client needs to present a valid PKI-issued certificate, a Microsoft Entra token, or a bulk registration token.

## Bulk registration token

If you can't install and register clients on the internal network, create a bulk registration token. Use this token when the client installs on an internet-based device, and registers through the CMG. The bulk registration token has a short-validity period, and isn't stored on the client or the site. It allows the client to generate a unique token, which paired with its self-signed certificate, lets it authenticate with the CMG.

Note

Don't confuse bulk registration tokens with those that Configuration Manager issues to individual clients. The bulk registration token enables the client to initially install and communicate with the site. This initial communication is long enough for the site to issue the client its own, unique client authentication token. The client then uses its authentication token for all communication with the site while it's on the internet. Beyond the initial registration, the client doesn't use or store the bulk registration token.

To create a bulk registration token for use during client installation on internet-based devices, complete the following actions:

1. Sign in to the top-level site server in the hierarchy with an account that is a **Full Administrator** in Configuration Manager and a member of the local Administrators group on the server.
2. Open a command prompt as an administrator.
3. Run the tool from the `\bin\X64` folder of the Configuration Manager installation directory on the site server: `BulkRegistrationTokenTool.exe`. Create a new token with the `/new` parameter. For example, `BulkRegistrationTokenTool.exe /new`. For more information, see Bulk registration token tool usage.
4. Copy the token and save it in a secure location.
5. Install the Configuration Manager client on an internet-based device. Include the client installation parameter: [`/regtoken`](about-client-installation-properties#regtoken). The following example command line includes the other required setup parameters and properties:

    `ccmsetup.exe /mp:https://CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=ABC /regtoken:eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6Ik9Tbzh2Tmd5VldRUjlDYVh5T2lacHFlMDlXNCJ9.eyJTQ0NNVG9rZW5DYXRlZ29yeSI6IlN7Q01QcmVBdXRoVG9rZW4iLCJBdXRob3JpdHkiOiJTQ0NNIiwiTGljZW5zZSI6IlNDQ00iLCJUeXBlIjoiQnVsa1JlZ2lzdHJhdGlvbiIsIlRlbmFudElkIjoiQ0RDQzVFOTEtMEFERi00QTI0LTgyRDAtMTk2NjY3RjFDMDgxIiwiVW5pcXVlSWQiOiJkYjU5MWUzMy1wNmZkLTRjNWItODJmMy1iZjY3M2U1YmQwYTIiLCJpc3MiOiJ1cm46c2NjbTpvYXV0aDI6Y2RjYzVlOTEtMGFkZi00YTI0LTgyZDAtMTk2NjY3ZjFjMDgxIiwiYXVkIjoidXJuOnNjY206c2VydmljZSIsImV4cCI6MTU4MDQxNbUwNSwibmJmIjoxNTgwMTU2MzA1fQ.ZUJkxCX6lxHUZhMH_WhYXFm_tbXenEdpgnbIqI1h8hYIJw7xDk3wv625SCfNfsqxhAwRwJByfkXdVGgIpAcFshzArXUVPPvmiUGaxlbB83etUTQjrLIk-gvQQZiE5NSgJ63LCp5KtqFCZe8vlZxnOloErFIrebjFikxqAgwOO4i5ukJdl3KQ07YPRhwpuXmwxRf1vsiawXBvTMhy40SOeZ3mAyCRypQpQNa7NM3adCBwUtYKwHqiX3r1jQU0y57LvU_brBfLUL6JUpk3ri-LSpwPFarRXzZPJUu4-mQFIgrMmKCYbFk3AaEvvrJienfWSvFYLpIYA7lg-6EVYRcCAA`

    Tip

    For more information on this command line, see [Install and register the client using Microsoft Entra identity](deploy-clients-cmg-azure#install-and-register-the-client-using-azure-ad-identity). This process is similar, just doesn't use the Microsoft Entra properties.

To verify, review the following log file for a similar entry:

```ClientLocation
Rotating internet management point, new management point [1] is: https://CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 (0) with capabilities: <Capabilities SchemaVersion ="1.0"><Property Name="SSL" Version="1" /></Capabilities>
```

To troubleshoot installation, review `%WinDir%\ccmsetup\logs\ccmsetup.log` on the client. After installation, review `%WinDir%\ccm\logs\ClientIDManagerStartup.log`.

On the server, review the following logs:

- [CMG logs](../../plan-design/hierarchy/log-files#cloud-management-gateway)
- Management point
    - CCM\_STS.log
    - MP\_RegistrationManager.log
    - ClientAuth.log

### Bulk registration token tool usage

The `BulkRegistrationTokenTool.exe` tool is in the `\bin\X64` folder of the Configuration Manager installation directory on the site server. Sign in to the site server, and run it as an administrator. It supports the following command-line parameters:

- `/?`
- `/new`
- `/lifetime`

#### `/?`

Display this usage information.

Example: `BulkRegistrationTokenTool.exe /?`

#### `/new`

Create a new bulk registration token.

Example: `BulkRegistrationTokenTool.exe /new`

The tool displays the following information:

- A GUID that the site uses to track issued tokens
- The token validity period, which is three days by default.
- The bulk registration token.

The token isn't stored on the client or the site. Make sure to copy the token from the command prompt, and store in a secure location.

#### `/lifetime`

Use with `/new` parameter to specify the token validity period of the token. Specify an integer value in minutes. The default value is 4,320 (three days). The maximum value is 10,080 (seven days).

Example: `BulkRegistrationTokenTool.exe /lifetime 4320`

### Bulk registration token management

You can see previously created bulk registration tokens and their lifetimes in the Configuration Manager console and block their usage if necessary. The site database doesn't, however, store bulk registration tokens.

### Review a bulk registration token

1. In the Configuration Manager console, go to the **Administration** workspace.
2. Expand **Security**, and select the **Certificates** node. The console lists all site-related certificates and bulk registration tokens in the details pane.
3. Select the bulk registration token to review.

You can filter or sort on the **Type** column. Identify specific bulk registration tokens based on their GUID. When you create a bulk registration token, the tool displays the GUID.

### Block a bulk registration token

1. In the Configuration Manager console, go to the **Administration** workspace.
2. Expand **Security**, select the **Certificates** node, and select the bulk registration token to block.
3. On the **Home** tab of the ribbon bar or the right-click context menu, select **Block**. To unblock previously blocked bulk registration tokens, select the **Unblock** action.

## Token Signing

The token the client gets the from the Management Point (when registered internally) or when installed using the Bulk token is signed by the *SMS Token Signing Certificate*. This is a self-signed certificate created by the Certificate Manager component using the **SMS Issuing** root certificate. The Configuration Manager-issued token includes the reference of the SMS Token Signing Certificate, apart from other auth headers when sending a request to the Management Point via the CMG.

While it's not typical that the SMS Issuing or the SMS Token Signing Certificate needs to be renewed, there are some uncertain scenarios that can require the certificate be renewed:

- Certificate is corrupted
- SMS issuing certificate is renewed
- Site operating system upgrade, where a [SHA-1 hash algorithm](/en-us/azure/security/fundamentals/ocsp-sha-1-sunset) was used to sign the certificate.

Note

If the SMS Token Signing Certificate is renewed, clients using the Configuration Manager-issued token won't be able to authenticate until the new token, signed with the newer certificate, is provided.

## Token renewal

The client renews its unique, Configuration Manager-issued token once a month, and it's valid for 90 days. A client doesn't need to connect to the internal network to renew its token. As long as the token is still valid, connecting to the site using a CMG is sufficient. If the token isn't renewed within 90 days, the client must directly connect to a management point on an internal network to receive a new token.

Note

The token will only renew during the startup of the Configuration Manager Client. Therefore, the SMS Agent Host (CCMExec) Service or the client machine must restart at least every 90 days.

You can't renew a bulk registration token. Once a bulk registration token expires, generate a new one for internet-based device registration using a CMG.