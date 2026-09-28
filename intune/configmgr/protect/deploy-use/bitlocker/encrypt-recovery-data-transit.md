---
layout: Conceptual
title: Encrypt recovery data over the network - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/bitlocker/encrypt-recovery-data-transit
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
description: Encrypt BitLocker recovery keys, recovery packages, and TPM password hashes over the network.
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: protect
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 231b70ad-5877-511b-6537-cfef06212452
document_version_independent_id: c0645705-33e3-b44e-31ce-b30e538bd749
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/bitlocker/encrypt-recovery-data-transit.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/bitlocker/encrypt-recovery-data-transit
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/bitlocker/encrypt-recovery-data-transit.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/37da4cc9-0cfc-42a9-ba5e-805706b01ef8
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1cfdec6-b0c3-4209-818c-736879856e0e
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3661fb96-d414-4a4e-b7ad-9370637790dd
- https://authoring-docs-microsoft.poolparty.biz/devrel/2d0723c1-cf38-4c30-ab3d-5df787b33270
platformId: f6ae8368-c750-c267-272d-5ca4a112aae9
---

# Encrypt recovery data over the network - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

When you create a BitLocker management policy, Configuration Manager deploys the recovery service to a management point. On the **Client Management** page of the BitLocker management policy, when you **Configure BitLocker Management Services**, the client backs up key recovery information to the site database. This information includes BitLocker recovery keys, recovery packages, and TPM password hashes. When users are locked out of their protected device, you can use this information to help them recover access to the device.

Given the sensitive nature of this information, you need to protect it.

Important

Starting in version 2103, the implementation of the recovery service changed. It's no longer using legacy MBAM components, but is still conceptually referred to as the *recovery service*. All version 2103 clients use the *message processing engine* component of the management point as their recovery service. They escrow their recovery keys over the secure client notification channel. With this change, you can enable the Configuration Manager site for [enhanced HTTP](../../../core/plan-design/hierarchy/enhanced-http). This configuration doesn't affect the functionality of BitLocker management in Configuration Manager.

When both the site and clients are running Configuration Manager version 2103 or later, clients send their recovery keys to the management point over the secure client notification channel. If any clients are on version 2010 or earlier, they need an HTTPS-enabled recovery service on the management point to escrow their keys.

## HTTPS certificate requirements

Note

These requirements only apply if the site is version 2010 or earlier, or if you deploy BitLocker management policies to devices with Configuration Manager client version 2010 or earlier.

Configuration Manager requires a secure connection between the client and the recovery service to encrypt the data in transit across the network. Use one of the following options:

- HTTPS-enable the IIS website on the management point that hosts the recovery service, not the entire management point role.
- Configure the management point for HTTPS. On the properties of the management point, the **Client connections** setting must be **HTTPS**.

Note

If your site has more than one management point, enable HTTPS on all management points at the site with which a BitLocker-managed client could potentially communicate. If the HTTPS management point is unavailable, the client could fail over to an HTTP management point, and then fail to escrow its recovery key.

This recommendation applies to both options: enable the management point for HTTPS, or enable the IIS website that hosts the recovery service on the management point.

### Configure the management point for HTTPS

In earlier versions of Configuration Manager current branch, to integrate the BitLocker recovery service you had to HTTPS-enable a management point. The HTTPS connection is necessary to encrypt the recovery keys across the network from the Configuration Manager client to the management point. Configuring the management point and all clients for HTTPS can be challenging for many customers.

### HTTPS-enable the IIS website

The HTTPS requirement is now for the IIS website that hosts the recovery service, not the entire management point role. This configuration relaxes the certificate requirements, and still encrypts the recovery keys in transit.

The **Client connections** property of the management point can be **HTTP** or **HTTPS**. If the management point is configured for **HTTP**, to support the BitLocker recovery service:

1. Acquire a server authentication certificate. Bind the certificate to the IIS website on the management point that hosts the BitLocker recovery service.
2. Configure clients to trust the server authentication certificate. There are two methods to accomplish this trust:

    - Use a certificate from a public and globally trusted certificate provider. Windows clients include trusted root certificate authorities (CAs) from these providers. By using a server authentication certificate that's issued by one of these providers, your clients should automatically trust it.
    - Use a certificate issued by a CA from your organization's public key infrastructure (PKI). Most PKI implementations add the trusted root CAs to Windows clients. For example, using Active Directory Certificate Services with group policy. If you issue the server authentication certificate from a CA that your clients don't automatically trust, add the CA trusted root certificate to clients.

Tip

The only clients that need to communicate with the recovery service are those clients that you plan to target with a BitLocker management policy and includes a **Client Management** rule.

## Troubleshoot the connection

On the client, use the **BitLockerManagementHandler.log** to troubleshoot this connection. For connectivity to the recovery service, the log shows the URL that the client is using. Locate an entry in the log based on the version of Configuration Manager:

- In version 2103 and later, the entry starts with `Recovery keys escrowed to MP`
- In version 2010 and earlier, the entry starts with `Checking for Recovery Service at`