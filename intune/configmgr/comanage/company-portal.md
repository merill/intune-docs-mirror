---
layout: Conceptual
title: Apps in Company Portal - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/comanage/company-portal
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
description: Provide a consistent user experience for co-managed devices to use the Company Portal app.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: co-management
ms.topic: how-to
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: bea9c9b0-1c73-0c06-fc2a-644da3c15b92
document_version_independent_id: 8ff9df61-61d6-8d70-55e3-50172c179c53
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/comanage/company-portal.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/comanage/company-portal
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/comanage/company-portal.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 38a45f18-7343-56e1-0126-f1f400686950
---

# Apps in Company Portal - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Starting in version 2006, the Company Portal app is now the cross-platform app portal experience for Microsoft Intune family of products. By configuring co-managed devices to also use the Company Portal app, you can provide a consistent user experience on all devices.

The Company Portal supports the following actions:

- Launch the Company Portal app on co-managed devices and sign in with Microsoft Entra single sign-on (SSO).
- View available and installed Configuration Manager apps in the Company Portal alongside Intune apps.
- Install available Configuration Manager apps from the Company Portal and receive installation status information.

[![Company Portal with app from Configuration Manager.](media/3601237-company-portal.png)](media/3601237-company-portal.png#lightbox)

The behavior of the Company Portal depends upon your co-management workload configuration:

| Workload | Setting | Behavior |
| --- | --- | --- |
| Client apps | **Configuration Manager** | You can see only Configuration Manager client apps |
| Client apps | **Pilot Intune** or **Intune** | You can see both Configuration Manager and Intune client apps |
| Office Click-to-run apps | **Configuration Manager** | You can see only Configuration Manager Office click-to-run apps |
| Office Click-to-run apps | **Pilot Intune** or **Intune** | You can see only Intune Office click-to-run apps |

For more information, see the following articles:

- [Diagram for app workloads](workloads#diagram-for-app-workloads)
- [How to switch Configuration Manager workloads to Intune](how-to-switch-workloads)

## Prerequisites

- Configuration Manager current branch version 2006 or later ^(See FAQ)^
- Company Portal app version 11.0.8980.0 or later

    Note

    Starting with Configuration Manager 2107 and Company Portal app version 11.0.12141.0, when you enable the site for [Enhanced HTTP](../core/plan-design/hierarchy/enhanced-http), the Company Portal prefers secure communication over HTTPS with the management point that's configured for HTTP. On any version of Configuration Manager, when you configure the site or the management point to require HTTPS communication, Company Portal always uses HTTPS.
- Windows 10 version 1803 or later:

    - Enrolled to [co-management](how-to-enable)
    - Access to [internet endpoints for Intune](../../fundamentals/endpoints)
- The user accounts that sign in to these devices require the following configurations:

    - A Microsoft Entra identity
    - Assigned an Intune license

## Configure and deploy

### Configuration Manager client settings

To make sure that users only receive notifications from Company Portal, configure Configuration Manager client settings. In the **Software Center** group of device settings, change **Select the user portal** to **Company Portal**.

For more information on client settings, see the following articles:

- [How to configure client settings](../core/clients/deploy/configure-client-settings)
- [About client settings](../core/clients/deploy/about-client-settings#software-center)

### Deploy the Company Portal app

- Users can manually install the Company Portal app from the [Microsoft Store](https://www.microsoft.com/p/company-portal/9wzdncrfj3pz?activetab=pivot:overviewtab).
- To require the app on co-managed devices, the deployment process depends upon the state of the [Client apps](workloads#client-apps) co-management workload:

    - If the client apps workload is with Configuration Manager, [create and deploy an application with Configuration Manager](../apps/get-started/create-and-deploy-an-application).
    - If the client apps workload is with Intune, you can deploy it via Configuration Manager or [add the Company Portal app by using Microsoft Intune](../../app-management/deployment/add-company-portal-windows).

For more information on branding the Company Portal for your organization, see [How to customize the Intune Company Portal app](../../app-management/configuration/configure-company-portal).

## Use the Company Portal

1. Launch the Company Portal from the Start menu. The currently signed-in user is automatically signed in to the Company Portal based on their Microsoft Entra identity.
2. Select the **Apps** page. You should see Configuration Manager apps in the list.
3. Select one of the apps deployed from Configuration Manager.

    - The **Overview** tab shows details about the app, such as size, version, and date published.
    - To see that Configuration Manager is the management service for this app, switch to the **Additional information** tab.
    - To install the app, select **Install**. The Company Portal shows installation status, and you'll see a notification when it completes.
    - If the app is already installed, select **Uninstall** to remove the app.
    - Select the ellipsis (`...`) for additional actions, such as **Repair** and **Share**.

        [![Configuration Manager app with details in Company Portal.](media/3601237-company-portal-app-details.png)](media/3601237-company-portal-app-details.png#lightbox)
    - After you install a Configuration Manager web app, select the ellipsis menu, then select **Open in Browser** to launch the web app.
    - If a Configuration Manager application fails to install with a known error code, select the failed status link to search on the error code.

If you change the client setting for Company Portal, when a user selects a Configuration Manager notification, it launches the Company Portal. If the notification is for a scenario the Company Portal doesn't support, selecting the notification launches Software Center.

To help troubleshoot issues with installation of Configuration Manager apps, go to the **Help & Support** section in Company Portal. When you use the **Get help** option, you can send Configuration Manager log files as part of the request.

## Frequently asked questions (FAQ)

### I'm using Configuration Manager version 2002, why is the new Company Portal showing Configuration Manager apps?

Company Portal version 11.0.8980.0 or later shows Configuration Manager-deployed applications for all co-managed clients that use it. Configuration Manager version 2006 is the prerequisite because it adds the client setting to control notifications. If you install the Company Portal on a co-managed device of a earlier version or don't configure the client setting, it causes behavior that may be confusing to users. Notifications from Configuration Manager launch Software Center, while notifications from Intune launch the Company Portal.

Microsoft recommends:

- Use Company Portal version 11.0.8980.0 or later on co-managed clients running Configuration Manager version 2006 or later.
- Configure the client setting **Select the user portal** to **Company Portal**

### Can I use the Company Portal to deploy software updates?

The Company Portal supports software updates. For more information, see: [Introduction to software updates in Configuration Manager](../sum/understand/software-updates-introduction).

### Can users repair, uninstall, and update Configuration Manager apps in Company Portal?

Yes. If you configure the Configuration Manager app to support these additional actions, Company Portal supports repair, uninstall, and update.

## Known issues

The following features of Software Center aren't currently available in the Company Portal:

- Some app information, for example if a restart is required or the estimated time to install
- [App groups](../apps/deploy-use/create-app-groups)

Other known issues:

- When you search Company Portal, Intune apps always display before Configuration Manager apps.