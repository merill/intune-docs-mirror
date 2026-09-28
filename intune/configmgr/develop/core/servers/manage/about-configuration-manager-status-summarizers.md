---
layout: Conceptual
title: Configuration Manager Status Summarizers - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-configuration-manager-status-summarizers
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
description: Summarizers are summary classes that help you determine the health or status of different aspects of your Configuration Manager site.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: 1bd5ebf4-51ff-a1e2-2a5c-f26855e075b5
document_version_independent_id: c0fbdf31-4c02-a075-d30a-da9a3c783894
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/manage/about-configuration-manager-status-summarizers.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/manage/about-configuration-manager-status-summarizers
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/manage/about-configuration-manager-status-summarizers.md
cmProducts: []
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: f1aaee2b-40bd-6354-cabc-09bec5e82d66
---

# Configuration Manager Status Summarizers - Configuration Manager | Microsoft Learn

Summarizers are summary classes that help you determine the health, or status, of different aspects of your Configuration Manager site. The summaries, which are produced from status messages, states, and counts, give you a real-time view of the health of Configuration Manager sites, components, packages, and advertisements.

Status summarizer classes summarize the status message data. Most of the summarizers create two views of the messages: a site view and a site hierarchy view.

All the summaries, except site system, are event-driven summaries. They respond in real time to changes that are taking place in Configuration Manager. Only the site system status summary polls for its information, according to a schedule that you can set.

Note

The `SMS_SummarizerStatus` class can be used to identify the registered summarizers.

## Site and Component Status

These summarizers group summaries of two kinds of data: software component health and physical system health.

You can determine the overall health of your site by using the stoplight status value in the `SMS_SummarizerSiteStatus` class, or you can determine the health of your storage objects by using the `SMS_SiteSystemSummarizer` class. For more information, see [How to Determine the Health of a Configuration ManagerSite](how-to-determine-the-health-of-a-configuration-manager-site). You can access these and other classes by getting, enumerating, and querying summarizer objects. However, the `SMS_ComponentSummarizer` and `SMS_SiteDetailSummarizer` classes can only be queried — you cannot get or enumerate these objects. Your queries must include a tally interval that defines the period of time from which you want summary information. For example, the following query asks for the count informational, warning, and error messages since Monday.

```
SELECT Infos, Warnings, Errors
FROM SMS_SiteDetailSummarizer
WHERE TallyInterval = "00011280001A2000"
```

Note

You cannot add other conditions like SiteCode to the WHERE clause. Adding other conditions will generate an error.

For information about using this query, see [How to Perform a Synchronous Configuration Manager Query by Using Managed Code](../../understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-managed-code) and [How to Perform a Synchronous Configuration Manager Query by Using WMI](../../understand/how-to-perform-a-synchronous-configuration-manager-query-by-using-wmi).

For more information about using tally intervals, see [About Configuration Manager Tally Intervals](about-configuration-manager-tally-intervals).

The component summarizers track the progress of advertised programs as they are advertised and run on the client computers.

Site system and package status summaries track the state changes instead of counting the error messages. For example, site system status summaries react to changes in free disk space on a site system. If the free space falls below the threshold you set, the site system's status summary health indicator changes.

The summarizer classes are:

| Summarizer | Description |
| --- | --- |
| [SMS_ComponentSummarizer Server WMI Class](../../../reference/core/servers/manage/sms_componentsummarizer-server-wmi-class) | Represents a component summarizer that reports on the health of individual Configuration Manager components. |
| [SMS_SiteDetailSummarizer Server WMI Class](../../../reference/core/servers/manage/sms_sitedetailsummarizer-server-wmi-class) | Represents a site detail summarizer that reports on the per-site status of components and the system. |
| [SMS_SiteSystemSummarizer Server WMI Class](../../../reference/core/servers/manage/sms_sitesystemsummarizer-server-wmi-class) | Represents a site system summarizer that reports physical system health data for each system and each system role in the Configuration Manager site. |
| [SMS_SummarizerRootStatus Server WMI Class](../../../reference/core/servers/manage/sms_summarizerrootstatus-server-wmi-class) | Represents a summarizer for the overall health of the entire site hierarchy. |
| [SMS_SummarizerSiteStatus Server WMI Class](../../../reference/core/servers/manage/sms_summarizersitestatus-server-wmi-class) | Represents a summarizer for the overall health of each site. |

## Software Distribution Health

You can determine the status of advertisements and packages by using the software distribution summarizers.

### Package Summarizers

Package summarizers are used to track the progress of packages as they are moved to their assigned distribution points. For more information, see [How to Determine Package Status](how-to-determine-package-status)

Package status summaries track the state changes instead of counting the error messages. For example, The package status summaries track items such as how many clients have installed each package.

The package summarizer classes are:

| Summarizer | Description |
| --- | --- |
| [SMS_PackageStatusDetailSummarizer Server WMI Class](../../../reference/core/servers/configure/sms_packagestatusdetailsummarizer-server-wmi-class) | Tracks the progress of each package as it places the software source files on its distribution point. The reported package status is for an individual site. |
| [SMS_PackageStatusDistPointsSummarizer Server WMI Class](../../../reference/core/servers/configure/sms_packagestatusdistpointssummarizer-server-wmi-class) | Tracks the progress of loading the package source files on the distribution point. The reported package status is for an individual site. |
| [SMS_PackageStatusRootSummarizer Server WMI Class](../../../reference/core/servers/configure/sms_packagestatusrootsummarizer-server-wmi-class) | Tracks the progress of each package as it places the software source files on its distribution point. The reported package status is for all sites in the hierarchy. |