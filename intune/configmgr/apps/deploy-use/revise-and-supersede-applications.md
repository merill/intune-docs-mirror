---
layout: Conceptual
title: Revise and supersede applications - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/revise-and-supersede-applications
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
description: Learn how to work with Configuration Manager application versions and supersede applications.
ms.date: 2021-12-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 15f78008-e65f-25b5-dee8-e3d93d08bc44
document_version_independent_id: 588fa52b-956b-8142-a788-fa66dd37ebb8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/deploy-use/revise-and-supersede-applications.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/deploy-use/revise-and-supersede-applications
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/deploy-use/revise-and-supersede-applications.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 54631b1a-c6e4-03a3-9881-14a9b1d46acf
---

# Revise and supersede applications - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Learn how to work with Configuration Manager application versions and how to supersede applications with a new version.

## Revisions

When you make revisions to an application or a deployment type, Configuration Manager creates a new revision of the application. You can display the history of each application revision. You can also view its properties, restore a previous revision of an application, or delete an old revision.

### Display the history of application revisions

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Application Management**, and select the **Applications** node. Then choose the application that you want.
2. On the **Home** tab of the ribbon, in the **Application** group, select **Revision History**. This action opens the **Application Revision History** window.

### View an application revision

1. In the **Application Revision History** window, select an application revision, and then select **View**.
2. In the **Properties** dialog box, examine the properties of the selected application.

    Note

    This view of application properties is read-only.

### Restore an application revision

1. In the **Application Revision History** window, select an application revision, and then select **Restore**.
2. Select **Yes** to restore the selected application revision.

### Delete an application revision

1. In the **Application Revision History** window, select an application revision, and then select **Delete**.
2. Select **Yes** to confirm.

Important

You can only delete the current application revision after you retire the application and it has no references.

## Supersedence

Application management in Configuration Manager lets you upgrade or replace existing applications by using a supersedence relationship. When you supersede an application, you specify a new deployment type to replace the deployment type of the superseded application. You can also decide whether to upgrade or uninstall the superseded application before the client installs the superseding application. It's best to limit supersedence chains to five levels deep at a maximum.

Important

When you choose the option to uninstall the superseded deployment type, a deployment type can't be superseded by a deployment type that was deployed to a different type of collection. For example, a deployment type that was deployed to a device collection can't be superseded by a deployment type that was deployed to a user collection.

### Decide whether to upgrade or replace an application

The type of supersedence depends on whether you select the **Uninstall** option:

- If you want to update to a newer version of the same application with the same application ID, *don't* select **Uninstall**.
- If you want to change to a different application with a different application ID, select **Uninstall**. You need to remove the superseded version of the application.

### Supersede dependent applications

In this example, *main application* refers to the app that you're deploying that has the dependencies.

You can create a supersedence relationship that updates the dependent application to a new version.

1. Make sure that the new dependent application and the original dependent application are in the same dependency group of the main application.
2. Create a supersedence relationship that supersedes the original dependent application with the new dependent application.

During new installations of the main application, the client installs the new dependent application. Configuration Manager updates existing installations of the main application with the new dependent application.

The end result is that all deployments of the main application use the new dependent application.

### Further considerations

- You can specify multiple supersedence relationships for dependent applications. Configuration Manager installs the highest dependent application in the supersedence chain.
- Deploy dependent applications to the device where the main application is installed. Otherwise Configuration Manager won't install the dependent application.
- For new installations of the main application, when you have multiple dependencies, the dependency order determines which version of the dependent application gets installed.

### Specify a supersedence relationship

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Application Management**, and select the **Applications** node. Then choose the application that supersedes another application.
2. On the **Home** tab of the ribbon, in the **Properties** group, select **Properties**.
3. Switch to the **Supersedence** tab, and select **Add**.
4. For the **Superseded Application**, select **Browse**.
5. Choose the application that you want to supersede, and then select **OK**.
6. In the **Specify Supersedence Relationship** window, select the deployment type that replaces the deployment type of the superseded application.

    Note

    By default, the new deployment type doesn't uninstall the deployment type of the superseded application. This scenario is commonly used when you want to deploy an upgrade to an existing application. To remove the existing deployment type before the new deployment type is installed, select **Uninstall**. If you decide to upgrade an application, make sure that you test this in a lab environment first.
7. If you want users to still see in Software Center deployments for both applications, select the option to **Allow users to see deployments for this application and all applications that it supersedes in Software Center.**. With this option, you give users the choice to still install an older version of the app if needed. By default, this option isn't selected, so only the superseding application displays in Software Center. This option is only for available deployments to user collections.
8. Select **OK** to save your changes and close the windows.

### Display applications that supersede the current application

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Application Management**, and select the **Applications** node. Then choose the application that you want.
2. On the **Home** tab of the ribbon, in the **Properties** group, select **Properties**.
3. Switch to the **References** tab.
4. For the **Relationship type**, choose **Applications that supersede this application**.

### View supersedence relationships

1. In the Configuration Manager console, go to the **Software Library** workspace, expand **Application Management**, and select the **Applications** node. Then choose the application that you want.
2. On the **Home** tab of the ribbon, in the **Relationships** group, select **View relationships**, and then select **Supersedence**.

This action shows a graphical diagram of the relationships of the selected application to other applications. For the supersedence relationships, it shows applications that the selected application supersedes, and applications that the selected application is superseded by.

### Manage supersedence with PowerShell

You can add, view, and remove supersedence relationships using the following PowerShell cmdlets:

- [Get-CMDeploymentTypeSupersedence](/en-us/powershell/module/configurationmanager/get-cmdeploymenttypesupersedence)
- [Set-CMApplicationSupersedence](/en-us/powershell/module/configurationmanager/set-cmapplicationsupersedence)