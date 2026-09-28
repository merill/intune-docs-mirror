---
layout: Conceptual
title: Install applications for a device - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/install-app-for-device
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
description: Use Configuration Manager to immediately install an application to a device without a collection.
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 4922f55e-e8f9-19b3-f7e1-20305c29f2b0
document_version_independent_id: 8fcf314b-7839-f81c-2943-5a1f50b44c76
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/deploy-use/install-app-for-device.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/deploy-use/install-app-for-device
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/deploy-use/install-app-for-device.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 03f7e952-d118-9f91-c82f-835781860cb0
---

# Install applications for a device - Configuration Manager | Microsoft Learn

From the Configuration Manager console you can install applications to a device in real time. This feature can help reduce the need for separate collections for every application.

Note

Starting in version 2111, this behavior also supports [application groups](create-app-groups#app-approval). When this article refers to an *application*, it also applies to app groups.

## Prerequisites

- Enable the [optional feature](../../core/servers/manage/optional-features)**Approve application requests for users per device**.
- [Deploy the application](deploy-applications) as *Available* to a device collection.

    - On the **Deployment Settings** page of the deployment wizard, select the following option: **An administrator must approve a request for this application on the device**.

        Note

        With these deployment settings, no policy is sent to the client. The app isn't shown as available in Software Center, and a user can't install the app with this deployment. After you use this action to install the app, the user can run it, and see its installation status in Software Center.
- Your user account needs the following permissions:

    - **Application**: Read, Approve
    - **Collection**: Read, Read Resource, Modify Resource, View Collected File

    For example, the **Application Administrator** built-in role has these permissions.

Tip

In a hierarchy, wait for application and deployment information to replicate to the primary site to which the target client is assigned.

## Process

1. In the Configuration Manager console, go to the **Assets and Compliance** workspace, and select the **Devices** node. Select the target device, and then select the **Install application** action in the ribbon. Starting in version 2111, select the **Install Application Group** action for an app group.
2. Select one or more applications from the list. The list only shows applications that you already deployed with the prerequisite settings.

This action triggers the installation of the selected pre-deployed applications on the device.

To see status of the approval request, in the **Software Library** workspace, expand **Application Management**, and select the **Application Requests** node.

Monitor the app installation the same as usual in the **Deployments** node of the **Monitoring** workspace.