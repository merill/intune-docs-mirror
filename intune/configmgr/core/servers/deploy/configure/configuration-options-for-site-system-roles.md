---
layout: Conceptual
title: Site system role options - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/configuration-options-for-site-system-roles
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
description: Consult this article for details about Configuration Manager site system roles that are not necessarily self-explanatory.
ms.date: 2022-03-29T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 6d983f0a-277b-ee44-c995-c2c83d2ede7b
document_version_independent_id: c6cc573f-c973-60fd-67fc-e60972a17ad8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/configuration-options-for-site-system-roles.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/configuration-options-for-site-system-roles
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/configuration-options-for-site-system-roles.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: bedcf152-3e1c-1cc5-3aa6-6748f4370215
---

# Site system role options - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Most configuration options for Configuration Manager site system roles are self-explanatory or are explained in the wizard or dialog boxes when you configure them. The following sections explain site system roles whose settings might require additional information.

## Certificate registration point

Warning

Starting in version 2203, the certificate registration point is no longer supported. For more information, see [Frequently asked questions about resource access deprecation](../../../../protect/plan-design/resource-access-deprecation-faq).

For more information about how to set up the certificate registration point, see [Introduction to certificate profiles](../../../../protect/deploy-use/introduction-to-certificate-profiles).

## Distribution point

For more information about how to set up the distribution point for content deployment, see [Manage content and content infrastructure](manage-content-and-content-infrastructure).

For more information about how to set up the distribution point for PXE deployments, see [Use PXE to deploy Windows over the network](../../../../osd/deploy-use/use-pxe-to-deploy-windows-over-the-network).

For more information about how to set up the distribution point for multicast deployments, see [Use multicast to deploy Windows over the network](../../../../osd/deploy-use/use-multicast-to-deploy-windows-over-the-network).

### Install and configure IIS if required by Configuration Manager

Select this option to let Configuration Manager install and set up IIS on the site system if it's not already installed. IIS must be installed on all distribution points, and you must select this setting to continue in the wizard.

### Site system installation account

For distribution points that are installed on a site server, only the computer account of the site server is supported for use as the site system installation account. For more information, see [Accounts](../../../plan-design/hierarchy/accounts#site-system-installation-account).

## Enrollment point

Enrollment points are used to install macOS computers and enroll devices that you manage with on-premises mobile device management. For more information, see the following articles:

- [How to deploy clients to Macs](../../../clients/deploy/deploy-clients-to-macs)
- [How users enroll devices with on-premises MDM](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm)

### Allowed connections

The HTTPS setting is automatically selected and requires a PKI certificate on the server for server authentication to the enrollment proxy point, and encryption of data over SSL. For more information, see [PKI certificate requirements](../../../plan-design/network/pki-certificate-requirements).

For an example deployment of the server certificate and information about how to configure it in IIS, see [Deploying the web server certificate for site systems that run IIS](../../../plan-design/network/example-deployment-of-pki-certificates#BKMK_webserver2008_cm2012).

## Enrollment proxy point

For more information about how to set up an enrollment proxy point for mobile devices, see [How users enroll devices with on-premises MDM](../../../../mdm/deploy-use/user-enroll-devices-on-premises-mdm).

### Client connections

The HTTPS setting is automatically selected. It requires the following PKI certificates on the server:

- For server authentication to mobile devices and Mac computers that you enroll with Configuration Manager
- For encryption of data over Secure Sockets Layer (SSL)

For more information about the certificate requirements, see [PKI certificate requirements](../../../plan-design/network/pki-certificate-requirements).

For an example deployment of the server certificate and information about how to configure it in IIS, see [Deploying the web server certificate for site systems that run IIS](../../../plan-design/network/example-deployment-of-pki-certificates#BKMK_webserver2008_cm2012).

## Fallback status point

### Number of state messages and Throttle interval (in seconds)

The default settings for these options are 10,000 state messages and 3,600 seconds for the throttle interval. While these settings are sufficient for most circumstances, you might have to change them when both of the following conditions are true:

- The fallback status point accepts connections only from the intranet.
- You use the fallback status point during a client deployment rollout for many computers.

In this scenario, a continuous stream of state messages might create a backlog of state messages that causes high processor usage on the site server for a sustained period. In addition, you might not see up-to-date information about the client deployment in the Configuration Manager console and in the client deployment reports.

These fallback status point settings are designed to be set up for state messages that are generated during client deployment. The settings aren't designed to be set up for client communication issues, like when clients on the internet can't connect to their internet-based management point. Because the fallback status point can't apply these settings just to the state messages that are generated during client deployment, don't configure these settings when the fallback status point accepts connections from the internet.

Each computer that successfully installs the Configuration Manager client sends the following four state messages to the fallback status point:

- Client deployment started
- Client deployment succeeded
- Client assignment started
- Client assignment succeeded

Computers that can't be installed or that assign the Configuration Manager client send additional state messages.

For example, if you deploy the Configuration Manager client to 20,000 computers, the deployment might send 80,000 state messages to the fallback status point. Because the default throttling configuration lets 10,000 state messages to be sent to the fallback status point each 3,600 seconds (1 hour), state messages might become backlogged on the fallback status point. Also consider the available network bandwidth between the fallback status point and the site server and the processing power of the site server to process many state messages.

To help prevent these issues, consider an increase in the number of state messages and a decrease in the throttle interval.

Reset the throttle values for the fallback status point if either of the following conditions is true:

- You calculate that the current throttle values are higher than required to process state messages from the fallback status point.
- You find that the current throttle settings create high processor usage on the site server.

Don't change the settings for the fallback status point throttle settings unless you understand the consequences. For example, when you increase the throttle settings to high, the processor usage on the site server can increase to high, which slows down all site operations.