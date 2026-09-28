---
layout: Conceptual
title: Create application groups - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/create-app-groups
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
description: Create a group of applications that you can send to a user or device collection as a single deployment in Configuration Manager.
ms.date: 2022-03-11T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 8e71a2bc-fe1a-6b20-6b97-6db8768c8e42
document_version_independent_id: c42cb159-f9c6-cec3-366b-cef5e902c0d0
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/deploy-use/create-app-groups.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/deploy-use/create-app-groups
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/deploy-use/create-app-groups.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
platformId: 50df496b-5b79-aadc-bf52-1eebc1c7261f
---

# Create application groups - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Create a group of applications that you can send to a user or device collection as a single deployment. The metadata you specify about the app group is seen in Software Center as a single entity. You can order the apps in the group so that the client installs them in a specific order.

Tip

This feature was first introduced in version 1906 as a [pre-release feature](../../core/servers/manage/pre-release-features). Beginning with version 2111, it's no longer a pre-release feature.

This feature is optional in Configuration Manager, and enabled by default. For more information, see [Enable optional features from updates](../../core/servers/manage/optional-features).

## Process

1. In the Configuration Manager console, go to the **Software Library** workspace. Expand **Application Management** and select the **Application Group** node.
2. In the Create group in the ribbon, select **Create Application Group**.
3. On the **General Information** page, specify information about the app group.
4. On the **Software Center** page, include information that shows in Software Center.
5. On the **Application Group** page, select **Add**. Select one or more apps for this group. Reorder them using the **Move Up** and **Move Down** actions.
6. Complete the wizard.

Tip

To manage app groups, you need permissions on the **Application Groups** object. The permissions for most administrative operations are the same as on applications.

## Deploy

Deploy the app group using the same process as for an application. For more information, see [Deploy applications](deploy-applications). You can deploy an app group to device or user collections. Starting in version 2111, when you deploy an app group as required to a device or user collection, you can specify that it automatically uninstalls when the resource is removed from the collection. For more information, see [Implicit uninstall](uninstall-applications#implicit-uninstall).

After you deploy the group:

- If you add a new app to the group, you have to separately distribute the new app content to distribution points.
- If you modify an app in the app group, redistribute the content.

To troubleshoot an app group deployment, use the following log files on the client:

- **AppGroupHandler.log**
- **AppEnforce.log**
- **SettingsAgent.log**

## App approval

Starting in version 2111, you can use the following [app approval](app-approval) behaviors:

- Deploy an app group to a user collection and require approval.

    - A user can then request the app group in Software Center.
    - You can approve or deny the user's request for the app group.
- Deploy an app group to a device collection and require approval. The deployment is suspended on the device until you trigger installation via automation. For example, use the [Approve-CMApprovalRequest](/en-us/powershell/module/configurationmanager/approve-cmapprovalrequest) PowerShell cmdlet.
- From the Configuration Manager console, when you select a device, there's a new action in the **Device** group of the ribbon to **Install Application Group**. For more information, see [Install applications for a device](install-app-for-device).
- When you enable tenant attach, you can view status and take actions on app groups from the Microsoft Intune admin center. For more information, see [Install an application from the admin center](../../tenant-attach/applications).

## Known issues

- The following deployment options may not work: alerts, phased deployment, repair.
- You can't use application groups with the **Install Application** task sequence step.
- You can't export or import app groups.
- In version 2103 and earlier, don't include in the group any apps that require restart, or the group deployment may fail.
- In version 2107 and earlier, if you delete an app that's a part of an app group, you'll see the following warning when you next view the properties of the app group: "Unable to load information about all applications in the group." Make a small change to the app group and save it. For example, add a space to the **Administrator comments**. When you save the change, it removes the deleted app from the group. Starting in version 2111, you can't delete an app that's part of an app group.
- In most scenarios, user categories on the app group don't display as filters in Software Center. If the app group is deployed as available to a user collection, the categories display.

## PowerShell

You can create and deploy app groups using Windows PowerShell. For more information, see the following cmdlet articles:

- [Get-CMApplicationGroup](/en-us/powershell/module/configurationmanager/get-cmapplicationgroup)
- [New-CMApplicationGroup](/en-us/powershell/module/configurationmanager/new-cmapplicationgroup)
- [Remove-CMApplicationGroup](/en-us/powershell/module/configurationmanager/remove-cmapplicationgroup)
- [Set-CMApplicationGroup](/en-us/powershell/module/configurationmanager/set-cmapplicationgroup)
- [Get-CMApplicationGroupDeployment](/en-us/powershell/module/configurationmanager/get-cmapplicationgroupdeployment)
- [New-CMApplicationGroupDeployment](/en-us/powershell/module/configurationmanager/new-cmapplicationgroupdeployment)
- [Remove-CMApplicationGroupDeployment](/en-us/powershell/module/configurationmanager/remove-cmapplicationgroupdeployment)
- [Set-CMApplicationGroupDeployment](/en-us/powershell/module/configurationmanager/set-cmapplicationgroupdeployment)