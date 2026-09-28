---
layout: Conceptual
title: Monitor client deployment status - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/deploy/monitor-client-deployment-status
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
description: Monitor client deployment status in Configuration Manager.
ms.date: 2017-04-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 50b807f8-4db6-27d9-a988-65b858b1f90e
document_version_independent_id: f974ac97-5068-fb73-432b-5d465bf5207f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/deploy/monitor-client-deployment-status.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/deploy/monitor-client-deployment-status
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/deploy/monitor-client-deployment-status.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 3ca750db-5241-209e-4145-da7350fd8d21
---

# Monitor client deployment status - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Deploying clients across your site takes time and some installations are not successful the first time. The Configuration Manager console provides a way to keep an eye on client deployments within a collection by reporting client deployment status in real time.

Note

The best and most reliable way to monitor client deployment is with the Configuration Manager console (as described in this article). The **Client Status** section of the **Monitoring** workspace in the console provides client deployment status accurately and in real time. You can monitor client deployments with other tools, such as Server Manager in Windows Server or System Center Operations Manager, but you may receive alarms from normal client installation activity. Because of how the client installation program (CCMSetup.exe) runs in various environments, these other tools may generate false alarms and warnings that do not accurately reflect the state of client deployments.

In the **Monitoring** workspace of the console, you can monitor the following statuses for client deployments taking place within a collection that you specify:

- Compliant
- In progress
- Not compliant
- Failed
- Unknown

    Configuration Manager reports on deployments for production clients or pre-production clients. The Configuration Manager console also provides a chart of failed client deployments over a specified period of time to help you determine if actions you to take to troubleshoot deployments are improving the deployment success rate over time.

## To monitor client deployments

- In the Configuration Manager console, click **Monitoring** &gt; **Client Status**.
- Click **Production Client Deployment** or **Pre-production Client Deployment** depending on the version of client you want to monitor.
- Review the charts of client deployment status and client deployment failure.
- If you want to change the scope of the report, click **Browse...** and choose a different collection.

    To learn more about pre-production client deployments, see [How to test client upgrades in a pre-production collection](../manage/upgrade/test-client-upgrades).

    Note

    The deployment status on computers hosting site system roles in a pre-production collection may be reported as **Not compliant** even when the client was successfully deployed. When you promote the client to production, the deployment status is reported correctly.

    To monitor the status of deployed clients, see [How to monitor clients](../manage/monitor-clients)

    You can use Configuration Manager reports to find out more information about the status of clients in your site. For more information about how to run reports, see [Introduction to reporting](../../servers/manage/introduction-to-reporting).