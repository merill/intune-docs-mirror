---
layout: Conceptual
title: Plan for Software Center - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/plan-design/plan-for-software-center
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
description: Decide how you want to configure and brand Software Center for users to interact with Configuration Manager.
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 7fc0e94b-db5d-0990-7a46-a5ee0f882351
document_version_independent_id: 4d3c1ed2-c620-4479-eb7c-f6b7ccd29cb0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/plan-design/plan-for-software-center.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/plan-design/plan-for-software-center
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/plan-design/plan-for-software-center.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: ce965f2b-376f-8a6c-041a-e33816f6bd64
---

# Plan for Software Center - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Users change settings, browse for applications, and install applications from Software Center. When you install the Configuration Manager client on a Windows device, it automatically installs Software Center as well.

## Configure Software Center

Important

To take advantage of new Configuration Manager features, first update clients to the latest version. While new functionality appears in the Configuration Manager console when you update the site and console, the complete scenario isn't functional until the client version is also the latest.

Use client settings to configure the appearance and behaviors of Software Center. For more information, see [Software Center client settings](../../core/clients/deploy/about-client-settings#software-center). The following list is a summary of some of the configurations:

- Change the branding of Software Center to include your organization's name, colors, and logo. For more information, see Brand Software Center.
- Configure which default tabs are visible, and add up to five custom tabs to Software Center.

    In Configuration Manager 2103 and earlier, when single sign on with multifactor authentication is used, you may not be able to sign in to custom tabs that load a website that's subject to Conditional Access policies.
- You can configure co-managed devices to use the Company Portal for both Intune and Configuration Manager apps. For more information, see [Use the Company Portal app on co-managed devices](../../comanage/company-portal).

You can allow users to set in Software Center if they regularly use the computer for work. This option configures an affinity between the user and device, which can affect some deployments. For more information, see [Link users and devices with user device affinity](../deploy-use/link-users-and-devices-with-user-device-affinity#let-users-create-their-own-device-affinities).

Be aware of the following settings for features that are no longer supported:

- The client setting **Use new Software Center** in the **Computer Agent** group is enabled by default. The previous version of Software Center is no longer supported.
- The client setting **Hide application catalog link in Software Center** in the **Software Center Customizations** is enabled by default. This link would appear on the **Installation Status** tab of Software Center. The application catalog is no longer supported.

For more information, see [Removed and deprecated features](../../core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures).

### Software Center and user-available applications

When you deploy an app with the purpose **Available** to a user collection, users can see these available applications in Software Center. This behavior provides a self-service capability for users to easily install approved software, without requiring assistance from IT staff.

Software Center gets application deployment information in policy from the management point. It uses the same management point from the assigned primary site as the Configuration Manager client. In a large environment, you can scale client communication to management points by assigning them to [boundary groups](../../core/servers/deploy/configure/boundary-groups-management-points).

Users can browse and install user-available applications on Microsoft Entra joined devices and internet-based, domain-joined devices. For more information, see [Prerequisites to deploy user-available applications](prerequisites-deploy-user-available-apps).

The site optimizes user-available deployments to reduce policy traffic between the server and clients. This behavior allows a large number of applications to be available for the user without significantly affecting performance of the overall infrastructure.

### Support for enhanced HTTP

Starting in version 2107, Software Center can take advantage of enhanced HTTP when the management point is configured for HTTP. This site configuration provides secure communication without the overhead of managing PKI certificates. When you enable the site for enhanced HTTP, Software Center prefers secure communication over HTTPS to get user-available applications from the management point.

Tip

On any version of Configuration Manager, when you configure the site or the management point to require HTTPS communication, Software Center always uses HTTPS.

To validate this behavior, on a client review the following log files:

- **CCMSDKProvider.log**: Shows the client's selection of the HTTPS endpoint on the management point. For example: `Management URL retrieved: https://...`
- **SCClient\_\*.log**: Shows the endpoint URL that the client uses to communicate with the management point, which should use HTTPS. For example: `Using endpoint Url: https://mp01.contoso.com:443/CMUserService, AAD authentication`

Note

To take full advantage of new Configuration Manager features, after you update the site, also update clients to the latest version. The complete scenario isn't functional until the client version is also the latest.

For more information on how to configure the site, see [enhanced HTTP](../../core/plan-design/hierarchy/enhanced-http).

## Brand Software Center

Change the appearance of Software Center to meet your organization's branding requirements. This configuration helps users trust Software Center.

### Configure Software Center branding

Customize the appearance of Software Center by adding your organization's branding elements:

- **Organization name**: Software Center displays this name in the top banner.
- **Color scheme**: The primary color for the banner and other elements.
- **Foreground color**: By default, when you select an item, the font color is white. Starting in version 2103, you can change this color for better visibility with certain primary colors, and better accessibility.
- **Logo for Software Center**: Your organization's logo helps users to trust Software Center.

The following image shows an example of Software Center that's customized with all four branding settings:

![Software Center with customized branding.](media/8655575-software-center-foreground-color.png)

Starting in version 2111, you can also configure a **Logo for notifications**. It's a separate image file specifically for notifications on devices running Windows 10 or later. Your organization's logo helps users to trust these notifications. When you deploy software to a client, the user sees notifications with your logo. For example:

![New software is available notification with custom logo.](media/4993167-notification-with-logo.png)

For more information, see the following articles:

- [About client settings for Software Center](../../core/clients/deploy/about-client-settings#software-center)
- [How to configure client settings](../../core/clients/deploy/configure-client-settings)

### Branding priorities

Configuration Manager applies the organization name for Software Center according to the following priorities:

1. **Software Center Customization** client setting for **Company Name**. For more information, see [About client settings: Software Center](../../core/clients/deploy/about-client-settings#software-center).
2. **Computer Agent** client setting for **Organization name**. For more information, see [About client settings: Computer agent](../../core/clients/deploy/about-client-settings#computer-agent).