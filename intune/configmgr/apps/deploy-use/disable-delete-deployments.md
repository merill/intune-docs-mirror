---
layout: Conceptual
title: Disable and delete app deployments - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/disable-delete-deployments
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
description: If you want to stop the deployment of an application, you can either disable it temporarily or delete it entirely.
ms.date: 2021-04-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: be2f216e-a209-dbd8-9604-b6481044c651
document_version_independent_id: 628cbfe6-ab38-49f4-49c8-25930753b28b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/deploy-use/disable-delete-deployments.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/deploy-use/disable-delete-deployments
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/deploy-use/disable-delete-deployments.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/43093068-2dda-408b-b3fe-dfd705c84f78
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/e453d60d-ba7e-43bc-8028-ec38e6b62512
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: e9cbc463-9a49-6104-789e-9583416cd072
---

# Disable and delete app deployments - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

If you want to stop the deployment of an application, you can either disable it temporarily or delete it entirely.

Important

Neither of these actions by themselves cause an instant change on the client. You can use [client notifications](../../core/clients/manage/client-notification#client-notification) or other automation tools to quickly request that clients refresh policy. But that still doesn't guarantee that a client won't run a deployment.

Make sure you carefully plan app deployments. [Simulate](simulate-application-deployments) more complex deployments. When you deploy to a query-based collection, use [query results preview](../../core/clients/manage/collections/create-collections#bkmk-query) to make sure you understand the scope of the query.

## Disable

Starting in version 2103, you can disable application deployments. Other objects already have similar behaviors:

- Software update deployments: Disable the deployment
- Phased deployments: Suspend the phase
- Package: Disable the program
- Task sequence: Disable the task sequence
- Configuration baseline: Disable the baseline

For device-based deployments, when you disable the deployment or object, use the client notification action to **Download Computer Policy**. This action immediately tells the client to update its policy from the site. If the deployment hasn't already started, the client receives the updated policy that the object is now disabled.

For user-based deployments, the user needs to sign out of Windows. Policy updates when they sign in to Windows, or every 24 hours by default.

Note

You can't disable an available deployment of an application to a user collection. You can only disable required deployments to user collections, or both type of deployments to device collections. The following table summarizes the supported scenarios to disable app deployments:

| Deployment purpose | Device collection | User collection |
| --- | --- | --- |
| Required | Yes | Yes |
| Available | Yes | No |

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Application Management**, and select the **Applications** node.
2. Select an app that you've deployed. In the details pane, switch to the **Deployment** tab.
3. Select a deployment. In the ribbon, on the **Deployment** tab, select **Disable**.
4. For a device-based deployment, note the name of the collection in **Collection** field of the deployment.

    Tip

    When you select the deployment, press **CTRL** + **C**. This keyboard shortcut copies the values of the current columns for the selected deployment.
5. Switch to the **Assets and Compliance** workspace, select the **Device Collections** node, and locate the target collection for the deployment. The quickest method is to search for the collection name as previously noted. You may need to select the option in the ribbon to search **All subfolders**.
6. Select the target collection for the deployment. In the ribbon, in the **Collection** group, select **Client Notification** and choose the **Download Computer Policy** action.

To enable the deployment, repeat this process but select the **Enable** action on the application deployment.

Note

When you select a deployment, you can use the **Collection** action to change to the **Assets and Compliance** workspace. But the current collection view doesn't support client notification actions.

## Delete

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Application Management**, and select either the **Applications** or **Application Groups** node.
2. Select the application or application group that includes the deployment you want to delete.
3. Switch to the **Deployments** tab of the details pane, and select the deployment.
4. In the ribbon, on the **Deployment** tab in the **Deployment** group, select **Delete**.

When you delete an application deployment, any instances of the application that clients have already installed aren't removed. To remove these applications, deploy the application to computers to **Uninstall**. If you delete an application deployment, the application is no longer visible in Software Center. The same behavior happens when you remove a resource from the target collection for the deployment.

When you delete a deployment, you remove the policy that deploys an application to a specific collection. This action doesn't delete the collection, any deployment types, or the application itself.