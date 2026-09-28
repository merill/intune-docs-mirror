---
layout: Conceptual
title: Blocking clients - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/plan/determine-whether-to-block-clients
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
description: Block client access for system security by using Configuration Manager.
ms.date: 2017-04-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 1282405a-9ec9-32e1-19a8-f2bdcff49376
document_version_independent_id: 5a23ae21-afc6-8ff6-3290-28746348d6e5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/plan/determine-whether-to-block-clients.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/plan/determine-whether-to-block-clients
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/plan/determine-whether-to-block-clients.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/aa9d0281-4c35-44bb-8c75-a0920bde2014
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/c7449412-70b0-48ea-831f-3b132eafb97e
platformId: 7b1e1d57-2ca5-ae98-e883-d5f935e1c911
---

# Blocking clients - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

If a client computer or client mobile device is no longer trusted, you can block the client in the System Center 2012 Configuration Manager console. Blocked clients are rejected by the Configuration Manager infrastructure so that they cannot communicate with site systems to download policy, upload inventory data, or send state or status messages.

You must block and unblock a client from its assigned site rather than from a secondary site or a central administration site.

Important

Although blocking in Configuration Manager can help to secure the Configuration Manager site, do not rely on this feature to protect the site from untrusted computers or mobile devices if you allow clients to communicate with site systems by using HTTP, because a blocked client could rejoin the site with a new self-signed certificate and hardware ID. Instead, use the blocking feature to block lost or compromised boot media that you use to deploy operating systems, and when site systems accept HTTPS client connections.

Clients that access the site by using the ISV Proxy certificate cannot be blocked. For more information about the ISV Proxy certificate, see the Configuration Manager Software Development Kit (SDK).

If your site systems accept HTTPS client connections and your public key infrastructure (PKI) supports a certificate revocation list (CRL), always consider certificate revocation to be the primary line of defense against potentially compromised certificates. Blocking clients in Configuration Manager offers a second line of defense to protect your hierarchy.

## Considerations for blocking clients

- This option is available for HTTP and HTTPS client connections, but has limited security when clients connect to site systems by using HTTP.
- Configuration Manager administrative users have the authority to block a client, and the action is taken in the Configuration Manager console.
- Client communication is rejected from the Configuration Manager hierarchy only.

    Note

    The same client could register with a different Configuration Manager hierarchy.
- The client is immediately blocked from the Configuration Manager site.
- Helps to protect site systems from potentially compromised computers and mobile devices.

## Considerations for using certificate revocation

- This option is available for HTTPS Windows client connections if the public key infrastructure supports a certificate revocation list (CRL).

    Mac clients always perform CRL checking and this functionality cannot be disabled.

    Although mobile device clients do not use certificate revocation lists to check the certificates for site systems, their certificates can be revoked and checked by Configuration Manager.
- Public key infrastructure administrators have the authority to revoke a certificate, and the action is taken outside the Configuration Manager console.
- Client communication can be rejected from any computer or mobile device that requires this client certificate.
- There is likely to be a delay between revoking a certificate and site systems downloading the modified certificate revocation list (CRL).
- For many PKI deployments, this delay can be a day or longer. For example, in Active Directory Certificate Services, the default expiration period is one week for a full CRL, and one day for a delta CRL.
- Helps to protect site systems and clients from potentially compromised computers and mobile devices.

    Note

    You can further protect site systems that run IIS from unknown clients by configuring a certificate trust list (CTL) in IIS.