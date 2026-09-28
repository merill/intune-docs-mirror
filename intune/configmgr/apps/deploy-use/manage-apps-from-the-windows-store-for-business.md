---
layout: Conceptual
title: Microsoft Store apps - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/manage-apps-from-the-windows-store-for-business
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
description: Manage and deploy apps from the Microsoft Store for Business and Education with Configuration Manager.
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 766b1855-dc0a-3664-5d0f-184a34998900
document_version_independent_id: d459b52e-76bb-1af1-6c99-4cd0b7e3f11e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/deploy-use/manage-apps-from-the-windows-store-for-business.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/deploy-use/manage-apps-from-the-windows-store-for-business
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/deploy-use/manage-apps-from-the-windows-store-for-business.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 9a0ab858-85f1-d741-5f27-fb59b21ac953
---

# Microsoft Store apps - Configuration Manager | Microsoft Learn

Important

Starting in November 2021, this feature of Configuration Manager is [deprecated](../../core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). For more information, see [Update to Intune integration with the Microsoft Store on Windows](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/update-to-endpoint-manager-integration-with-the-microsoft-store/bc-p/3592470).

The [Microsoft Store for Business and Education](/en-us/microsoft-store/) is where you find and acquire Windows apps for your organization. When you connect the store to Configuration Manager, you then synchronize the list of apps you've acquired. View these apps in the Configuration Manager console, and deploy them like you deploy any other app.

## Online and offline apps

The Microsoft Store for Business and Education supports two types of app:

- **Online**: This license type requires users and devices to connect to the store to get an app and its license. Devices running Windows 10 or later should be Microsoft Entra joined or Microsoft Entra hybrid joined. They can also be [Microsoft Entra registered](/en-us/entra/identity/devices/concept-device-registration).
- **Offline**: This type lets you cache apps and licenses to deploy directly within your on-premises network. Devices don't need to connect to the store or have a connection to the internet.

For more information, see the [Microsoft Store for Business and Education overview](/en-us/mem/configmgr/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

### Summary of capabilities

Configuration Manager supports managing Microsoft Store for Business and Education apps on devices running Windows 10 or later with the Configuration Manager client. Configuration Manager offers the following capabilities for online and offline apps:

| Capability | Offline apps | Online apps |
| --- | --- | --- |
| Synchronize app data to Configuration Manager(synchronization occurs every 24 hours) | Yes | Yes |
| Create Configuration Manager applications from store apps | Yes | Yes |
| Support for free apps from the store | Yes | Yes |
| Support for paid apps from the store | No | Yes^Note 1^ |
| Support required deployments to user or device collections | Yes | Yes |
| Support available deployments to user or device collections | Yes | Yes |
| Support line-of-business apps from the store | Yes | Yes |
| Provision a store app for all users on a device^Note 2^ | Yes | Yes |

#### Note 1: Online licensed apps version requirement

To deploy online licensed apps to Windows devices with the Configuration Manager client, they need to be running a supported version of Windows 10 or later.

#### Note 2: Provision Windows app packages for all users on a device

For more information, see [Create Windows applications](../get-started/creating-windows-applications#bkmk_provision).

### Deploying online apps using the Microsoft Store for Business and Education to devices that run the Configuration Manager client

Before deploying Microsoft Store for Business and Education apps to devices that run the full Configuration Manager client, consider the following points:

- For full functionality, devices need to be running a supported version of Windows 10 or later.
- Register or join devices to the same Microsoft Entra tenant where you registered the Microsoft Store for Business and Education as a management tool.
- When the local Administrator account signs in on the device, it can't access Microsoft Store for Business and Education apps.
- Devices need a live internet connection to the Microsoft Store for Business and Education. For more information including proxy configuration, see [Prerequisites](../../../app-management/deployment/add-microsoft-store).

## Set up synchronization

When you synchronize the list of Microsoft Store for Business and Education apps that your organization acquired, you see these apps in the Configuration Manager console.

Connect your Configuration Manager site to Microsoft Entra ID and the Microsoft Store for Business and Education. For more information and details of this process, see [Configure Azure services](../../core/servers/deploy/configure/azure-services-wizard). Create a connection to the **Microsoft Store for Business** service.

Make sure the service connection point and targeted devices can access the cloud service. For more information, see [Prerequisites for Microsoft Store for Business and Education - Proxy configuration](../../../app-management/deployment/add-microsoft-store).

### Supplemental information and configuration

On the **App** page of the Azure Services Wizard, first configure the **Azure environment** and **Web app**. Then read the **More Information** section at the bottom of the page. This information includes the following other actions in the Microsoft Store for Business and Education portal:

- Configure Configuration Manager as the store management tool. For more information, see [Configure management provider](/en-us/windows/client-management/azure-active-directory-integration-with-mdm).
- Enable support for offline licensed apps. For more information, see [Distribute offline apps](/en-us/microsoft-store/distribute-offline-apps).
- Acquire at least one app. For more information, see [Find and acquire apps](/en-us/microsoft-store/find-and-acquire-apps-overview).

On the **Configurations** page of the Azure Services Wizard, specify the following information:

- **Path to Microsoft Store for Business app content storage**: Specify a shared network path, including a folder. For example, `\\server\share\folder`. When the site server syncs with the store, it caches content in this location. When you create an application in Configuration Manager, the site server copies the app content from this local cache to the site's content library.
- **Selected languages**: Select the languages to sync from the store and display to users in Software Center. For example, if the user configures Windows for German, then Software Center shows German strings for the store app. This behavior requires that language to be synchronized, and to exist for the specific application.
- **Default language**: If the user's language is unavailable, select a default language to use.

Note

Configuration Manager doesn't synchronize the app icon from the store. If you need an icon to display for this app in Software Center, manually add it in the app properties. For more information, see [Manually specify application information](create-applications#bkmk_manual-app).

## Create and deploy the app

After synchronization, create and deploy the Microsoft Store for Business and Education apps similar to any other Configuration Manager application.

1. In the **Software Library** workspace of the Configuration Manager console, expand **Application Management**, then select the **License Information for Store Apps** node.
2. Choose the app you want to deploy, then select **Create Application** in the ribbon.

The site creates a Configuration Manager application containing the Microsoft Store for Business and Education app.

Then deploy and monitor this application as you would any other Configuration Manager application. For more information, see the following articles:

- [Deploy applications](deploy-applications)
- [Monitor applications from the console](monitor-applications-from-the-console)

## Manage the app

In the **Software Library** workspace, expand **Application Management**, then select the **License Information for Store Apps** node.

For each store app you manage, view the following information about the app:

- App name
- App platform
- The number of licenses for the app that you own
- The number of available licenses

After deploying online apps, any updates to that app come directly from the Microsoft Store. Furthermore, Configuration Manager doesn't check version compliance of online apps, just that Windows reports the app as installed.

When deploying offline apps to Windows devices with the Configuration Manager client, don't allow users to update applications external to Configuration Manager deployments. Control of updates to offline apps is especially important in multi-user environments such as classrooms. One option to disable the Microsoft Store is by using [group policy](/en-us/windows/configuration/stop-employees-from-using-microsoft-store#block-microsoft-store-using-group-policy).

After the Microsoft Store for Business and Education administrator acquires an offline app, don't publish the app to users via the store. This configuration makes sure that users can't install or update online. Users only receive offline app updates via Configuration Manager.