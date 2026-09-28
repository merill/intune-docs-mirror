---
layout: Conceptual
title: Security and privacy for software updates - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/sum/plan-design/security-and-privacy-for-software-updates
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
description: Follow these best practices for security for software updates and learn about how Configuration Manager handles privacy information.
ms.date: 2020-09-16T00:00:00.0000000Z
ms.topic: article
ms.subservice: software-updates
ms.collection: tier3
locale: en-us
document_id: b4d907a1-963b-57fa-33ac-f9dbf08df3fd
document_version_independent_id: 797c9905-71e0-fde0-b769-85a3525f73da
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/sum/plan-design/security-and-privacy-for-software-updates.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/sum/plan-design/security-and-privacy-for-software-updates
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/sum/plan-design/security-and-privacy-for-software-updates.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/fc3f72c2-fb6f-4cea-95ee-b444e52254ee
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f12cf087-582d-48ac-a085-0c19adf1e391
platformId: 4fa20a98-db58-4d90-91a4-bf9be5c55302
---

# Security and privacy for software updates - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This topic contains security and privacy information for software updates in Configuration Manager.

## Security best practices for software updates

Use the following security best practices when you deploy software updates to clients:

- Don't change the default permissions on software update packages.

    By default, software update packages are set to allow administrators **Full Control** and users to have **Read** access. If you change these permissions, it might allow an attacker to add, remove, or delete software updates.
- Control access to the download location for software updates.

    The computer accounts for the SMS Provider, the site server, and the administrative user who will actually download the software updates to the download location require **Write** access to the download location. Restrict access to the download location to reduce the risk of attackers tampering with the software updates source files in the download location.

    In addition, if you use a UNC share for the download location, secure the network channel by using IPsec or SMB signing to prevent tampering of the software updates source files when they're transferred over the network.
- Use UTC for evaluating deployment times.

    If you use local time instead of UTC, users could potentially delay installation of software updates by changing the time zone on their computers
- Enable SSL on WSUS and follow the best practices for securing Windows Server Update Services (WSUS).

    Identify and follow the security best practices for the version of WSUS that you use with Configuration Manager.

    For more information on enabling SSL, see the [Configure a software update point to use TLS/SSL with a PKI certificate tutorial](../get-started/software-update-point-ssl).

    Important

    If you configure the software update point to enable SSL communications for the WSUS server, you must configure virtual roots for SSL on the WSUS server.
- Enable CRL checking.

    By default, Configuration Manager doesn't check the certificate revocation list (CRL) to verify the signature on software updates before they're deployed to computers. Checking the CRL each time a certificate is used offers more security against using a certificate that has been revoked, but it introduces a connection delay and incurs additional processing on the computer performing the CRL check.

    For more information about how to enable CRL checking for software updates, see [How to enable CRL checking for software updates](../get-started/manage-settings-for-software-updates#crl-checking-for-software-updates).
- Configure WSUS to use a custom website.

    When you install WSUS on the software update point, you have the option to use the existing IIS Default Web site or to create a custom WSUS website. Create a custom website for WSUS so that IIS hosts the WSUS services in a dedicated virtual website instead of sharing the same web site that is used by the other Configuration Manager site systems or other applications.

    For more information, see [Configure WSUS to use a custom web site](plan-for-software-updates#BKMK_CustomWebSite).

## Privacy information for software updates

Software updates scans your client computers to determine which software updates you require, and then sends that information back to the site database. During the software updates process, Configuration Manager might transmit information between clients and servers that identify the computer and logon accounts.

Configuration Manager maintains state information about the software deployment process. State information isn't encrypted during transmission or storage. State information is stored in the Configuration Manager database and it's deleted by the database maintenance tasks. No state information is sent to Microsoft.

The use of Configuration Manager software updates to install software updates on client computers might be subject to software license terms for those updates, which is separate from the Software License Terms for Configuration Manager. Always review and agree to the Software Licensing Terms prior to installing the software updates by using Configuration Manager.

Configuration Manager doesn't implement software updates by default and requires several configuration steps before information is collected.

Before you configure software updates, consider your privacy requirements.