---
layout: Conceptual
title: Common tasks for configuration baselines - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines
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
description: Learn about how to create and deploy Configuration Manager configuration baselines.
ms.date: 2021-10-05T00:00:00.0000000Z
ms.subservice: compliance
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 8a61ed6a-6614-3ff6-3651-6f69f1293008
document_version_independent_id: 05abb850-40dc-1cb0-ffe1-cc0965128d59
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/compliance/plan-design/common-tasks-for-creating-and-deploying-configuration-baselines.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: a6a31cea-ef23-8153-31f4-ea62c97d4628
---

# Common tasks for configuration baselines - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This topic contains common scenarios to help you learn about how to create and deploy Configuration Manager configuration baselines.

If you are already familiar with compliance settings, you can find detailed documentation about all the features you use in the [Create configuration baselines](../deploy-use/create-configuration-baselines) and [Deploy configuration baselines](../deploy-use/deploy-configuration-baselines) topics.

Before you start, read [Get started with compliance settings](../get-started/get-started-with-compliance-settings) to learn some basics about compliance settings, and also read [Plan for and configure compliance settings](plan-for-and-configure-compliance-settings) to implement any necessary prerequisites.

## Create a configuration baseline

In this example, you've created a configuration item for only or later PCs that run the Configuration Manager client.

This configuration item enforces a required password of at least 6 characters on Windows 10 or later PCs. The configuration item is named **Windows 10 or later password enforcement**.

Use the following procedure to learn how to add this configuration item to a configuration baseline to prepare it for deployment.

1. In the Configuration Manager console, click **Assets and Compliance** &gt; **Compliance Settings** &gt; **Configuration Baselines**.
2. On the **Home** tab, in the **Create** group, click **Create Configuration Baseline**.
3. In the **Create Configuration Baseline** dialog box, configure the following settings:

    - **Name** - Enter **Windows 10 or later passwords** (or another name of your choice)
4. Click **Add** &gt; **Configuration Items**.
5. In the **Add Configuration Items** dialog box, select the **Windows 10 or later password enforcement** configuration item that you previously created, then click **Add**.
6. Click OK to close the **Add Configuration Items** dialog box and return to the **Create Configuration Baseline** dialog box.
7. Click **OK** to close the **Create Configuration Baseline** dialog box.

    You can now see the configuration baseline in the **Configuration Baselines** node of the Configuration Manager console.

## Deploy the configuration baseline

In this example, you deploy the configuration baseline you created in the previous procedure to a collection of computers.

1. In the Configuration Manager console, click **Assets and Compliance** &gt; **Compliance Settings** &gt; **Configuration Baselines**.
2. From the list of configuration baselines, select **Windows 10 or later passwords**.
3. On the **Home** tab, in the **Deployment** group, click **Deploy**.
4. In the **Deploy Configuration Baselines** dialog box, configure the following settings:

    - **Selected configuration baselines** - Ensure that the **Windows 10 or later passwords** configuration baseline was automatically added to this list.
    - **Remediate noncompliant rules when supported** - Check this box to ensure that if the correct settings are not present on targeted devices, then they are remediated by Configuration Manager.
    - **Collection** - Click **Browse** to choose the collection of computers on which the configuration baseline is evaluated and remediated for compliance. In this example, the configuration baseline was deployed to the built-in **All Desktop and Server Clients** collection.

        Tip

        Don't worry if the collection you choose contains computers or devices that don't run Windows 10 or later. As long as you configured supported platforms in the configuration item you created, only Windows 10 or later PCs are evaluated for compliance.
    - If necessary, configure the schedule by which the configuration baseline is evaluated. Otherwise, keep the default of **7 Days**.
5. Click **OK** to close the **Deploy Configuration Baselines** dialog box and create the deployment.

    If you want to take a quick look at compliance statistics for this deployment, in the **Monitoring** workspace, click **Deployments**. At the bottom of the screen, you see a **Compliance Statistics** chart.