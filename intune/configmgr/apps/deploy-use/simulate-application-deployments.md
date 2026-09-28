---
layout: Conceptual
title: Simulate application deployments - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/simulate-application-deployments
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
description: Evaluate the detection method, requirements, and dependencies for a deployment type without installing the application.
ms.date: 2016-10-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 5e4a7173-631d-2113-9c94-6fbb639dfda5
document_version_independent_id: aff06fbf-dcb8-387a-772d-bb34177d3a01
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/deploy-use/simulate-application-deployments.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/deploy-use/simulate-application-deployments
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/deploy-use/simulate-application-deployments.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 722618d3-db41-f57a-bb21-25337ba69bce
---

# Simulate application deployments - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

You can use simulated deployments to test an application deployment without installing or uninstalling the application. A simulated deployment evaluates the detection method, requirements, and dependencies for a deployment type. It reports the results in the **Deployments** node of the **Monitoring** workspace. Use the procedure in this topic to simulate an application deployment in Configuration Manager.

Note

You cannot use simulated deployments for collections of mobile devices.

You cannot deploy an application with a deployment purpose of **Uninstall** if a simulated deployment of the same application is active.

## Configure a simulated application deployment

1. In the Configuration Manager console, select one of the following:

    - A collection of users.
    - A collection of devices.
    - A Configuration Manager application.
2. On the **Home** tab, in the **Deployment** group, choose **Simulate Deployment**.
3. In the Simulate Application Deployment Wizard, set the following details for your simulated deployment:

    - **Application**. Choose **Browse**, and then select the application you want to create a simulated deployment for.
    - **Collection**. Choose **Browse**, and then select the collection that you want to use for the simulated deployment.
    - **Action**. From the drop-down list, select whether you want to simulate the installation or the uninstallation of the selected application.
    - **Deploy automatically with or without user login**. If this option is checked, the clients evaluate the simulated deployment whether or not the clients are logged in.
4. Click **Next**, review the information on the **Summary** page, and then finish the wizard to create the simulated application deployment.
5. Simulated applications appear in the **Deployments** node of the **Monitoring** workspace, with a purpose of **Simulate**. For more information about how to monitor application deployments, see [Monitor applications from the Configuration Manager console](monitor-applications-from-the-console).