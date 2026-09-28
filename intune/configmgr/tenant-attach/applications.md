---
layout: Conceptual
title: Tenant attach - Applications in the admin center - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/applications
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
description: Install applications for uploaded Configuration Manager devices from the admin center.
ms.date: 2022-07-11T00:00:00.0000000Z
ms.topic: install-set-up-deploy
ms.subservice: core-infra
ms.collection: tier3
ms.custom: sfi-image-nochange
locale: en-us
document_id: 7e36d4b3-74d9-5258-134b-dcd174e49b91
document_version_independent_id: a9cbafe1-e6da-a7fe-fbad-26e1bc5a4227
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/tenant-attach/applications.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/tenant-attach/applications
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/tenant-attach/applications.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 1e2a3cc7-3060-0e26-d549-224689271f33
---

# Tenant attach - Applications in the admin center - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Microsoft Intune family of products is an integrated solution for managing all of your devices. Microsoft brings together Configuration Manager and Intune into a single console called **Microsoft Intune admin center**. From the Microsoft Endpoint Management admin center, you can initiate an application install in real time for a tenant attached device.

[![Screenshot of applications in Microsoft Intune admin center.](media/6024389-tenant-attach-application-list.png)](media/6024389-tenant-attach-application-list.png#lightbox)

Note

Starting in version 2111, this behavior also supports [application groups](../apps/deploy-use/create-app-groups#app-approval). When this article refers to an *application*, it also applies to app groups.

## Prerequisites

- All of the prerequisites for [Tenant attach: ConfigMgr client details](client-details#prerequisites).
- An application that meets one of the following requirements: 
    - Is deployed to the device
    - Is deployed to a user that's logged in to the device, primary user of the device, and applications previously installed for the user
        - When you have a large number of device available applications, using the **An administrator must approve a request for this application on the device** on application deployments is recommended. For more information, see Display all applications for a device in the admin center.

## Permissions

The user account needs the following permissions:

- The **Read** permission for the device's **Collection**in Configuration Manager.
    - Apply the permission to both targeted device collections and targeted user collections.
- The **Read** permission for **Application** in Configuration Manager.
- The **Approve** permission for **Application** in Configuration Manager.
- An [Intune role](../../fundamentals/role-based-access-control/overview) assigned to the user

## Application status

You can filter the application list based on the status. The application status can be one of the following labels:

- **Available**: The application has never been installed on the device.
- **Installed**: The application is installed on the device.
- **Installing**: The application is currently installing.
- **Install requested**: The installation has been requested, but the client hasn't acknowledged the request yet.
    - If the device is offline, the install request will be acknowledged once it comes back online and receives the policy.
- **Failed**: The application installation failed.
- **Requirements not met**: The application requirements haven't been met.
- **Not installed**: The application isn't currently installed. Typically this status is seen if a different deployment or a user removed the application.
- **Restart pending**: The application is installed but needs a restart to complete.
- **Required**: Installation is required for the application

## Deploy an application to a device

1. In a browser, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** then **All Devices**.
3. Select a device that is synced from Configuration Manager via [tenant attach](device-sync-actions).
4. Select **Applications**.
5. Select the application and choose **Install**.

You can export all of the data currently in the view into a .csv file. At the top of the page, select the **Export** option to create the file. If the view exceeds 500 rows, only the first 500 are exported.

## Deploy an application to a user

User available applications appear in the **Applications** node for a ConfigMgr device. The list of applications available for the device also includes applications deployed to the device's currently logged on user.

Deploying applications to a user has the following limitations:

- Multi-user session scenarios aren't supported.
- Microsoft Entra joined devices aren't currently supported.
    - Devices that are both domain joined and Microsoft Entra joined are supported.

## Uninstall, repair, re-evaluate, or reinstall an application

Administrators can do the following actions for applications in the Microsoft Intune admin center:

- **Uninstall** an application
- **Repair** installation of an application
- **Re-evaluate** the application installation status
- **Reinstall** an application has replaced **Retry installation**

[![Screenshot of application installation options in the Microsoft Intune admin center](media/7979972-application-repair.png)](media/7979972-application-repair.png#lightbox)

### Prerequisites to uninstall, repair, reinstall, or re-evaluate an application

- Install the latest version of the Configuration Manager client
- Targeted clients need to be online
- To uninstall an application:
    - The application must have at least one [deployment type](../apps/deploy-use/create-applications#start-the-create-deployment-type-wizard) with the uninstall command defined
    - Required deployments of the application can't be targeted to the client
    - The application must currently be installed on the device
- To repair an application:
    - The application must have at least one [deployment type](../apps/deploy-use/create-applications#start-the-create-deployment-type-wizard) with the repair command defined
    - The application must currently be installed on the device

#### Uninstall, repair, reinstall, or re-evaluate an application

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Devices** then **All Devices**.
3. Select a device that is synced from Configuration Manager via [tenant attach](device-sync-actions).
4. Choose **Applications**.
5. Select the application then one of the following actions you want to perform on the device:
    - **Reinstall**
    - **Re-evaluate**
    - **Uninstall**
    - **Repair**

## Display all applications for a device in the admin center

The **Applications** view for a tenant attached device in Microsoft Intune admin center displays more applications from Configuration Manager. This improvement allows you to review when application installations are expected to occur on a device. Displayed applications include applications that are:

- Deployed to the device
- Deployed to a user that's logged in to the device, primary user of the device, or was previously installed.

![Screenshot showing details about required deadlines for applications in Microsoft Intune admin center](media/8795301-display-required-app.png)

The option, **An administrator must approve a request for this application on the device**, is no longer required to be set on the device available deployment for applications to be listed in the admin center. However, we recommend using the **An administrator must approve a request for this application on the device** option on application deployments when you have a large number of device available applications. By using this option, it defers targeting a new policy to the client until installation is initiated by the admin. By not targeting a large number of application policies to the client, it increases the performance of the site servers and the client. For more information about determining installation behavior, see When will the application install on the device?.

### Review status of an application

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. From **Devices** &gt; **All devices**, choose a device managed by **ConfigMgr**.
3. Select **Applications** then select an application that has a **Status** of **Required**.
4. Review the details of the schedule for the installation of the application.

## What applications and actions are available for my version of Configuration Manager?

The displayed application and available actions are dependent on the version of Configuration Manager. Use the chart below to help determine what applications and actions are available in the admin center:

| Configuration Manager version | Applications displayed | Available actions |
| --- | --- | --- |
| Configuration Manager version 2010 with devices running client versions before 2010 | Device-available applications with the **An administrator must approve a request for this application on the device** option set on the deployment.  All user-available applications | Install  Reinstall |
| Configuration Manager version 2010 with devices running 2010 client versions | Device-available applications with the **An administrator must approve a request for this application on the device** option set on the deployment.  All user-available applications | Install  Reinstall  Re-evaluate  Uninstall  Repair |
| Configuration Manager version 2103 with devices running 2006 or earlier client versions | All applications targeted to the device  All user targeted applications related to the device. For example, applications targeted to the logged in user, primary user, and applications previously installed for the user are displayed. | For user and device-available applications with the **An administrator must approve a request for this application on the device** option set on the deployment:  Install Reinstall All other applications display status but no actions are available |
| Configuration Manager version 2103 with devices running 2010 or later client versions | All applications targeted to the device  All user targeted applications related to the device. For example, applications targeted to the logged in user, primary user, and applications previously installed for the user are displayed | Install  Reinstall  Re-evaluate  Uninstall  Repair |

## When will the application install on the device?

Use the following table to determine installation behavior on the device when you install an app from the admin center:

| Deployment options | Client requires policy sync before installation | Client must be online to queue the installation |
| --- | --- | --- |
| Device required | Yes | Yes |
| Device available | Yes | Yes |
| Device requires approval | No | No  The installation will occur when the client next comes online |
| User required | Yes | Yes |
| User available | No | No  The installation will occur when the client next comes online |
| User requires approval | No | No  The installation will occur when the client next comes online |

## Known issues

### Superseded applications are displayed

Superseded applications will display on the **Applications** page. However, the superseding application will be installed on the device. For instance, `ApplicationA` is superseded by `ApplicationB`. An administrator selects `ApplicationA` for installation on the device. `ApplicationB` is installed on the device.