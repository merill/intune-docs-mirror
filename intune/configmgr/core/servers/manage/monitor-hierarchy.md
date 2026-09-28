---
layout: Conceptual
title: Monitor the hierarchy - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/monitor-hierarchy
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
description: Learn how to monitor your infrastructure in Configuration Manager by using the Monitoring workspace in the console.
ms.date: 2019-06-06T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 85afd381-fa95-1dae-6e51-b9d985fe2790
document_version_independent_id: 93dc189e-64ad-4140-85e0-e79d744b969e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/monitor-hierarchy.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/monitor-hierarchy
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/monitor-hierarchy.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: 7b7d9d74-d0ca-8989-4ffb-6824023177c6
---

# Monitor the hierarchy - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

To monitor your hierarchy in Configuration Manager, use the **Monitoring** workspace in the Configuration Manager console.

Note

The exception to this location is when migrating sites. Monitored this process in the **Migration** node of the **Administration** workspace. For more information, see [Operations for migrating to Configuration Manager current branch](../../migration/operations-for-migration).

Along with using the Configuration Manager console for monitoring, use the following features:

- [Introduction to reporting](introduction-to-reporting)
- [Log files](../../plan-design/hierarchy/log-files).

When you monitor sites, look for signs that indicate problems that require you to take action. For example:

- A backlog of files on site servers and site systems.
- Status messages that indicate an error or a problem.
- Failing intrasite communication.
- Error and warning messages in the system event log on servers.
- Error and warning messages in the Microsoft SQL Server error log.
- Sites or clients that haven't reported status in a long time.
- Sluggish response from the SQL Server database.
- Signs of hardware failure.

If monitoring tasks reveal any signs of problems, investigate the source of the problem. Then quickly repair it to minimize the risk of a site failure.

## Monitor common management tasks

Configuration Manager provides built-in monitoring from within the Configuration Manager console.

### Alerts

For more information, see [Monitor alerts](configure-alerts#monitor-alerts).

### Compliance settings

For more information, see [How to monitor compliance settings](../../../compliance/deploy-use/monitor-compliance-settings).

### Content

For general information about monitoring content, see [Manage content and content infrastructure](../deploy/configure/manage-content-and-content-infrastructure).

For more information about monitoring specific types of content:

- [Monitor applications](../../../apps/deploy-use/monitor-applications-from-the-console)
- [Monitor packages and programs](../../../apps/deploy-use/packages-and-programs#monitor-packages-and-programs)
- [Monitor content for software updates](../../../sum/deploy-use/monitor-software-updates#BKMK_MonitorContent)
- [Monitor content for OS deployments](../../../osd/deploy-use/monitor-operating-system-deployments#BKMK_MonitorContent)

### Endpoint Protection

For more information, see [How to monitor Endpoint Protection](../../../protect/deploy-use/monitor-endpoint-protection).

### OS deployment

For more information, see [Monitor OS deployments](../../../osd/deploy-use/monitor-operating-system-deployments).

### Monitor power management

For more information, see [How to monitor and plan for power management](../../clients/manage/power/monitor-and-plan-for-power-management).

### Monitor software metering

For more information, see [Monitor app usage with software metering](../../../apps/deploy-use/monitor-app-usage-with-software-metering).

### Monitor software updates

For more information, see [Monitor software updates](../../../sum/deploy-use/monitor-software-updates).

## Monitor the site hierarchy

The **Site Hierarchy** node of the **Monitoring** workspace provides you with an overview of your Configuration Manager hierarchy and intersite links.

Use the **Site Hierarchy** node to monitor the health of each site. Also monitor the intersite replication links and their relationship to external factors, such as a geographical location.

Both site status and intersite link status replicate as site data and not global data. When you connect your Configuration Manager console to a child primary site, you can't view the site or link status for other primary sites or their child secondary sites. For example, in a hierarchy with multiple primary sites, when you connect the console to a primary site, you can view the status of child secondary sites, the primary site, and the central administration site. From this view, you can't see the status for other sites below the central administration site.

To control the display in the **Site Hierarchy** node, use the **Configure Settings** action. The hierarchy replicates the settings that you configure in this node.

### Hierarchy diagram

The hierarchy diagram displays your sites in a topology map. Select a site, and view a status message summary from that site. Drill through to view status messages, and access the site **Properties**.

To view high-level status for a site or replication link between sites, hover your mouse pointer over the object. Replication link status doesn't replicate globally. To view the replication link details between all primary sites in a hierarchy, connect the console to the central administration site.

The following options modify the hierarchy diagram:

#### Groups

Configure the number of primary sites and secondary sites that trigger a change in the hierarchy diagram. This change in the display combines the sites into a single object. Then you see the total number of sites and a high-level rollup of status messages and site status.

#### Favorite sites

Specify individual sites to be a favorite site. A star icon identifies a favorite site in the hierarchy diagram. Favorite sites aren't combined with others sites when you use groups. They're always displayed individually.

### Geographical view

Important

Starting in August 2020, this feature is deprecated. Use the **Hierarchy Diagram** option.

The geographical view displays the location of each site on a geographical map. It only displays sites that you configure with a location. When you select a site in this view, it shows replication links to parent or child sites. Unlike the hierarchy diagram view, you can't display site status message or replication link details in this view.

Note

To use the geographical view, the computer to which your Configuration Manager console connects must have Internet Explorer installed and be able to access Bing Maps by using the HTTP protocol.

The following option modifies the geographical view:

#### Site Location

Specify a geographical location for each site using one of the following types:

- A street address
- A place name such as the name of a city
- By latitude and longitude coordinates

For example, to use the latitude and longitude of Redmond, Washington, specify **N 47 40 26.3572 W 122 7 17.4432** as the location of the site. You don't need to specify the symbols for the degree, minutes, or seconds of latitude or longitude. Configuration Manager uses Bing Maps to display the location on the geographical view. Then you can view your hierarchy with the geographical locations. This view provides insight into regional issues that might affect specific sites or intersite replication.

When you specify a location, you can use the **Location** box to search for a specific site in your hierarchy. With the site selected, enter the location as a city name or street address in the **Location** column. Configuration Manager uses Bing Maps to resolve the location.