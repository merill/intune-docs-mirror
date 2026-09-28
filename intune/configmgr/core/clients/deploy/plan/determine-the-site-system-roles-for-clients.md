---
layout: Conceptual
title: Site system roles for clients - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/plan/determine-the-site-system-roles-for-clients
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
description: Determine site system roles for clients in Configuration Manager.
ms.date: 2022-01-04T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 1596a9e6-fe1e-5a23-99fe-ed9754a44cb1
document_version_independent_id: 3caf8813-0037-95a5-78d2-cde572dd5af7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/plan/determine-the-site-system-roles-for-clients
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: d192da7a-92d6-2506-10e0-1df803d73e05
---

# Site system roles for clients - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article can help you determine the site system roles that you need to deploy Configuration Manager clients.

For more information about where to install these roles in the hierarchy, see [Design a hierarchy of sites](../../../plan-design/hierarchy/design-a-hierarchy-of-sites).

For more information about how to install and configure these roles, see [Install site system roles](../../../servers/deploy/configure/install-site-system-roles).

## Management point

By default, all Windows client computers use a distribution point to install the Configuration Manager client. They can fall back to a management point when a distribution point is unavailable. However, you can install Windows clients on computers from an alternative source when you use the CCMSetup command-line property `/source:<Path>`. For example, you might do this action if you install clients on the internet. Another scenario is when you want to avoid sending network packets between the computer and the management point during client installation. This scenario is because a firewall blocks the required ports or because you have a low-bandwidth connection. However, all clients must communicate with a management point to assign to a site and to be managed by Configuration Manager.

For more information about client command-line properties, see [About client installation properties](../about-client-installation-properties).

When you install more than one management point in the hierarchy, clients automatically connect to one point based on their forest membership and network location. You can't install more than one management point in a secondary site.

Mac computer clients and mobile device clients that you enroll with Configuration Manager always require a management point for client installation. This management point must be in a primary site, must be configured to support mobile devices, and must accept client connections from the Internet. These clients can't use management points in secondary sites or connect to management points in other primary sites.

## Distribution point

You don't need a distribution point to install Configuration Manager clients on Windows computers. By default, Configuration Manager uses a distribution point to install the client source files on Windows computers. It can fall back to downloading these files from a management point. Distribution points aren't used to install mobile device clients that are enrolled by Configuration Manager, but are used if you install the mobile device legacy client. If you install the Configuration Manager client as part of an OS deployment, the OS image is stored and retrieved from a distribution point.

Although you might not need distribution points to install most Configuration Manager clients, you'll need them to install software such as applications and software updates on the clients.

## Fallback status point

You can use a fallback status point to monitor client deployment for Windows computers. You can also identify the Windows computer clients that are unmanaged because they can't communicate with a management point.

The following client types don't use a fallback status point:

- Mac computers
- Mobile devices that are enrolled by Configuration Manager
- Mobile devices that are managed by using the Exchange Server connector

A fallback status point isn't required to monitor client activity and client health.

The fallback status point always communicates with clients over HTTP, which uses unauthenticated connections and sends data in clear text. This behavior makes the fallback status point vulnerable to attack, particularly when it's used with internet-based client management. To help reduce the attack surface, always dedicate a server to running the fallback status point. Don't install other site system roles on the same server in a production environment.

Install a fallback status point if all the following conditions apply:

- You want client communication errors from Windows computers to be sent to the site, even if these client computers can't communicate with a management point.
- You want to use the Configuration Manager client deployment reports, which display the data that's sent by the fallback status point.
- You have a dedicated server for this site system role and have additional security measures to help protect the server from attack.
- The benefits of using a fallback status point outweigh any security risks associated with unauthenticated connections and clear text transfers over HTTP traffic.

Don't install a fallback status point if the security risks of running a website with unauthenticated connections and clear text transfers outweigh the benefits of identifying client communication problems.

## Reporting services point

Configuration Manager provides many reports to help you monitor the installation, assignment, and management of clients in the Configuration Manager console. Some of the client deployment reports require that clients are assigned to a fallback status point.

The reports aren't needed to deploy clients. You can see some deployment information in the Configuration Manager console or use the client log files for detailed information. However, the client reports provide valuable information to help monitor and troubleshoot client deployment.

## Enrollment point and enrollment proxy point

Important

With the deprecation of on-premises MDM and the Configuration Manager client for macOS, these site system roles are also deprecated. For more information, see [Removed and deprecated features for Configuration Manager](../../../plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

Configuration Manager requires the enrollment point and the enrollment proxy point to enroll mobile devices and to enroll certificates for Mac computers. You don't need these site system roles in the following situations:

- You plan to manage mobile devices by using the Exchange Server connector
- You install the mobile device legacy client
- You request and install the client certificate on Mac computers independently from Configuration Manager

## Cloud management gateway connector point

You need a cloud management gateway connector point if you're setting up a [cloud management gateway](../../manage/cmg/overview) to manage clients on the internet.