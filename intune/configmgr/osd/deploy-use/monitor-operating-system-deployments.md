---
layout: Conceptual
title: Monitor operating system deployments - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/osd/deploy-use/monitor-operating-system-deployments
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
description: To help you to monitor operating system deployment objects, the Configuration Manager console provides alerts, reports, and various status indicators.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: osd
ms.topic: how-to
ms.collection: tier3
locale: en-us
document_id: 354ed71d-c365-3ab6-75c2-f640d08922c8
document_version_independent_id: 2562287b-1b0a-001a-5a08-d5ffa307e587
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/osd/deploy-use/monitor-operating-system-deployments.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/osd/deploy-use/monitor-operating-system-deployments
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/osd/deploy-use/monitor-operating-system-deployments.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: db6dd154-99a6-4834-8ac5-a0b9920150e2
---

# Monitor operating system deployments - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Configuration Manager console provides the following ways to help you monitor operating system deployment objects.

## Alerts for operating system deployments

You can configure an alert in the task sequence deployment settings to notify administrative users when compliance levels for the deployment are below the configured percentage.

After you configure the alert settings, if the specified conditions occur, Configuration Manager generates an alert. You can review task sequence deployment alerts at the following locations:

1. Review recent alerts in the **Operating Systems** node in the **Software Library** workspace.
2. Manage the configured alerts in the **Alerts** node in the **Monitoring** workspace.

## Task sequence deployment status

After you deploy a task sequence, you can monitor the deployment status. Use the following procedure to monitor the deployment status for a task sequence.

#### To monitor deployment status

1. In the Configuration Manager console, click **Monitoring**.
2. In the Monitoring workspace, click **Deployments**.
3. Click the task sequence for which you want to monitor the deployment status.
4. On the **Home** tab, in the **Deployment** group, click **View Status**.

Tip

- When an upgrade is initiated, status message 52200 is generated. This contains the user that did the upgrade.
- Starting in version 2203, you can perform client notification actions, including **Run Scripts**, from the **Deployment Status** view.Use the right-click menu on either a group of clients in a **Category** or a single client in the **Asset details** pane to display the client notification actions.

## Operating system deployment reports

There are many predefined operating system deployment reports available. They are organized in several categories and can be used to report on specific information about state migration and task sequence deployments. In addition to using the preconfigured reports, you can also create custom software update reports according to the needs of your enterprise. For more information, see [Operations and maintenance for reporting](../../core/servers/manage/operations-and-maintenance-for-reporting).

## Monitor content

You can monitor content in the Configuration Manager console to review the status for all package types in relation to the associated distribution points. This can include the content validation status for the content in the package, the status of content assigned to a specific distribution point group, the state of content assigned to a distribution point, and the status of optional features for each distribution point (content validation, PXE, and multicast).

### Content status monitoring

The **Content Status** node in the **Monitoring** workspace provides information about content packages. You can review general information about the package, distribution status for the package, and detailed status information about the package. Use the following procedure to view content status.

#### To monitor content status

1. In the Configuration Manager console, click **Monitoring**.
2. In the Monitoring workspace, expand **Distribution Status**, and then click **Content Status**. The packages are displayed.
3. Select the package for which to view detailed status information.
4. On the **Home** tab, click **View Status**. Detailed status information for the package is displayed.

### Distribution point group status

The **Distribution Point Group Status** node in the **Monitoring** workspace provides information about distribution point groups. You can review general information about the distribution point group, such as distribution point group status and compliance rate, as well as detailed status information for the distribution point group. Use the following procedure to view distribution point group status.

#### To monitor distribution point group status

1. In the Configuration Manager console, click **Monitoring**.
2. In the monitoring workspace, expand **Distribution Status**, and then click **Distribution Point Group Status**. The distribution point groups are displayed.
3. Select the distribution point group for which to view detailed status information.
4. On the **Home** tab, click **View Status**. Detailed status information for the distribution point group is displayed.

### Distribution point configuration status

The **Distribution Point Configuration Status** node in the **Monitoring** workspace provides information about the distribution point. You can review which attributes are enabled for the distribution point, such as the PXE, Multicast, and content validation. You can also view detailed status information for the distribution point. Use the following procedure to view distribution point configuration status.

#### To monitor distribution point configuration status

1. In the Configuration Manager console, click **Monitoring**.
2. In the monitoring workspace, expand **Distribution Status**, and then click **Distribution Point Configuration Status**. The distribution points are displayed.
3. Select the distribution point for which to view distribution point status information.
4. In the results pane, click the **Details** tab. Status information for the distribution point is displayed.