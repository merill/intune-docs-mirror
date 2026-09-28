---
layout: Conceptual
title: Management tasks for applications - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/management-tasks-applications
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
description: Manage Configuration Manager applications and deployment types.
ms.date: 2021-04-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: b667f4d5-997d-1c88-a543-69d88fec7899
document_version_independent_id: 39a62f5e-2f44-280b-26ca-44b60c478d03
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/deploy-use/management-tasks-applications.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/deploy-use/management-tasks-applications
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/deploy-use/management-tasks-applications.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: a34fab4d-748e-59f8-3b87-6d0bd37e24fe
---

# Management tasks for applications - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use the information in this article to help you manage Configuration Manager applications and deployment types.

For more information on how to create applications and deployment types, see [Create applications](create-applications).

Important

Depending on the type of application or deployment type, some management options might not be available.

## Manage applications

In the **Software Library** workspace, expand **Application Management**, and select the **Applications** node. Select the application to manage, and then choose a management task in the ribbon.

### Manage access accounts

Use this action to control access to the associated content on distribution points.

When you **Add** an account:

1. Specify one of the following account types:

    - **User**: Any account that Windows can authenticate.
    - **Guest**: An unauthenticated user.
    - **Administrator**: An account that Windows recognizes as an administrator.
    - **Windows User**: A specific user account. It can either be from a local machine or Active Directory.
2. Specify one of the following access rights:

    - **No access**: Explicitly block the specified account type from accessing the content associated with this application.
    - **Read**
    - **Change**
    - **Full control**

By default, the **Administrator** type has **Full control** access, and the **User** type has **Read** access.

### Create prestaged content file

Prestaged content files help you to manage the delivery of content to remote distribution points. When scheduling and throttling options don't provide a valid solution for the remote distribution point, you can prestage the content.

For more information, see [Deploy and manage content](../../core/servers/deploy/configure/deploy-and-manage-content#bkmk_prestage).

### Revision history

View and manage the revisions to this application. For more information, see [How to revise and supersede applications](revise-and-supersede-applications#revisions).

### Update statistics

Updates the information that's displayed in the **Deployments** node of the **Monitoring** workspace about the deployments of this application. For more information, see [Monitor applications from the Configuration Manager console](monitor-applications-from-the-console).

### Create deployment type

Add a new deployment type to the selected application. For more information, see [Create deployment types for the application](create-applications#bkmk_create-dt).

### Convert to .MSIX

Convert an existing Windows Installer (.msi) application to the MSIX format. For more information, see [Support for MSIX format](../get-started/creating-windows-applications#bkmk_msix).

### Reinstate

If you previously retired an application, use this action to reinstate it. When you reinstate a retired app, you can then deploy it again.

### Retire

When you retire an application, it's no longer available for deployment. Configuration Manager doesn't delete the application and any deployments. If the app was installed on clients, Configuration Manager doesn't remove the app. Configuration Manager deletes any revisions to the app after 60 days in retirement.

Before you delete an application:

1. Retire the application.
2. Delete all deployments.
3. Remove references to the application by other deployments
4. Delete all of the application's revisions.

For more information, see [Revise and supersede applications](revise-and-supersede-applications).

### Export

Export the selected applications to a .zip file that you can archive or import to another site. If you choose to export application content, Configuration Manager creates a folder with the content.

You can export:

- Application dependencies
- Supersedence relationships and conditions
- Content for the application and its dependencies

To automate this process, use the following Configuration Manager PowerShell cmdlets:

- [Export-CMApplication](/en-us/powershell/module/configurationmanager/export-cmapplication)
- [Import-CMApplication](/en-us/powershell/module/configurationmanager/import-cmapplication)

For more information, see [Import and export applications](import-export-applications).

### Copy (application)

Duplicate the application to create a new one. This action is useful to test something or when you need to create a similar application. The site creates a new application, and appends **-copy** to the name. While the site copies most of the metadata to the new application, it doesn't copy any deployments.

### Delete (application)

Delete the currently selected applications.

You can't delete an application if any of the following conditions are true:

- Other applications are dependent on it
- It has an active deployment
- It has dependent task sequences

Before you delete an application, retire it.

### Simulate deployment

Test the results of an application deployment to computers without installing or uninstalling it. For more information, see [Simulate application deployments](simulate-application-deployments).

### Deploy

Deploy the selected application to a collection of computers. For more information, see [Deploy applications](deploy-applications).

### Create phased deployment

Phased deployments automate a coordinated, sequenced rollout of software across multiple collections. For example, deploy software to a pilot collection, and then automatically continue the rollout based on success criteria. For more information, see [Create phased deployments](../../osd/deploy-use/create-phased-deployment-for-task-sequence?toc=/mem/configmgr/apps/toc.json&amp;bc=/mem/configmgr/apps/breadcrumb/toc.json).

### Distribute content

Copy the content for the selected application to distribution points. For more information, see [Distribute content](../../core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute).

### Move

Move the selected application to another folder in the **Applications** node.

### Set security scopes

Select the security scopes for the selected application. For more information, see [Security scopes](../../core/understand/fundamentals-of-role-based-administration#security-scopes).

### Categorize

Administrative categories help you organize apps in the Configuration Manager console. You can add the **Administrative categories** column to the **Applications** node.

With this action, you can:

- Quickly add the selected app to an administrative category.
- Clear all categories on the current app.
- Select **Manage categories** to create, rename, or delete categories.

You can also manage categories on the application properties, **General information** tab.

Tip

To help users find apps by category in Software Center, define **user categories** for your apps. You can add these categories on the application properties, **Software Center** tab.

### View relationships

Show a graphical diagram of the relationships of the selected applications to other applications. Choose one of the following relationship types:

- **Dependency**: Shows applications that are dependent on the selected application and the applications that the selected application depends on. For more information, see [Deployment type Dependencies](create-applications#bkmk_dt-depend).
- **Supersedence**: Shows applications that the selected application supersedes, and applications that the selected application is superseded by. For more information, see [Supersedence](revise-and-supersede-applications#supersedence).
- **Global Conditions**: Shows the global conditions that this application references. For more information, see [Create global conditions](create-global-conditions).

### Properties

Display and edit the metadata for this application.

## Manage deployment types

In the **Software Library** workspace, expand **Application Management**, and select the **Applications** node. Select the application with the deployment type that you want to manage. In the details pane, switch to the **Deployment Types** tab. Select the deployment type that you want to manage, and then choose a management task from the **Deployment Type** tab of the ribbon.

### Increase priority

Increase the priority of the selected deployment type. The Configuration Manager client evaluates deployment types in order. If the device meets the deployment type's requirements, it runs the deployment type. Then the client doesn't evaluate any further deployment types on the priority list.

### Decrease priority

Lower the priority of the selected deployment type.

### Copy (deployment type)

Duplicate the deployment type to create a new one. This action is useful to test something or when you need to create a similar deployment type. The site creates a new deployment type on the same application, and appends **-copy** to the name.

### Delete (deployment type)

Delete the selected deployment type. You can't delete a deployment type if it's referenced by a deployment type in another application.

To delete a deployment type:

1. Remove all dependencies from other deployment types.
2. Remove previous revisions of all applications that have a deployment type that references this deployment type.

### Update content

Refresh the content for the selected deployment type. When you refresh the content of a deployment type, the site creates a new revision of the application. This behavior might cause client devices to update with the new application content.