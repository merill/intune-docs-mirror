---
layout: Conceptual
title: Site administration views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/site-admin-views-configuration-manager
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
description: Information such as the site code, Configuration Manager version, and the location of the SMS provider.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: ede3e859-ca4c-9a9d-0bf1-ec509a4055a7
document_version_independent_id: 51f4987d-272c-0e93-a6e9-a735b3d754d6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/site-admin-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/site-admin-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/site-admin-views-configuration-manager.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: 34477c82-8501-60fd-acb9-4ffef9fd38db
---

# Site administration views - Configuration Manager | Microsoft Learn

The Configuration�Manager site views contain information such as the site code, Configuration Manager version, the location of the SMS provider, site server name, site system names, site boundary information, and more. There are also status views that contain information about sites, site systems, and components. The site and site status views will most often be joined to other views by using the **SiteCode** or **ServerName** columns.

The following sections provide detailed information about site views and site status views.

## Site views

The site views contain information about the Configuration Manager site and are described in this section.

### v\_BoundarySiteCode

Lists each boundary in the Configuration Manager hierarchy together with the site code associated with that boundary. This view can be joined to other views by using the **BoundaryID** column.

### v\_BoundarySiteSystems

BoundaryIDServerNALPathSiteSystemName

### v\_Identification

Lists information about each site in the hierarchy, including site code, site name, Configuration Manager version, Configuration Manager build number, service account name, where the SMS provider is located, site server name, and language. The view can be joined to other views by using the **ThisSiteCode** column.

### v\_LocalizedNameLookup

Lists the matching English view column names to a string resource in a resource DLL that contains the localized version of the name. It is unlikely that this view will be joined to other views.

### v\_LocalizedNameValue

Lists the matching English name to the localized name. It is unlikely that this view will be joined to other views.

### v\_LocalizedSettingType

Lists the matching English view setting type with the localized name for the setting type. It is unlikely that this view will be joined to other views.

### v\_ServerComponents

Lists the components for each site, such as SMS\_EXECUTIVE, SMS\_SITE\_CONTROL\_MANAGER, and so on. The site code, server name, and Configuration Manager components are listed. The view can be joined to other views by using the **SiteCode**, **MachineName**, or **ComponentName** columns.

### v\_Site

Lists information about each site in the Configuration Manager hierarchy, including site code, site name, site version, site server name, installation directory, and more. The view can be joined to other views by using the **SiteCode** or **ServerName** columns.

### v\_SoftwareConversionRules

Lists all software inventory names that are to be converted to a standard name. For example, software that is inventoried with the manufacturer name of Microsoft or Microsoft Corp. is converted to a display name of Microsoft Corporation. It is unlikely that this view will be joined to other views.

### v\_SupportedPlatforms

Lists the supported operating systems, including operating system platform, minimum and maximum version, and operating system name. This list is used by a number of Configuration Manager operations. It is unlikely that this view will be joined to other views.

### v\_SystemResourceList

Lists all site system locations for each site in the Configuration Manager hierarchy. The NAL path, resource type, site code, site system role name, and site system computer name are listed. The view can be joined to other views by using the **SiteCode**, **ServerName**, or **NALPath** columns.

### v\_SiteAndSubsites

List information about each site in the hierarchy, including the site code, site name, site type, build number, site server name and more. This view can be joined to other views by using the **SiteCode** and **ServerName** columns.

## Site status views

The site status views contain status and status summary information about Configuration Manager components, site servers, site systems, and so on. For more information about the status views, see [Status and Alert Views in Configuration Manager](status-alert-views-configuration-manager). The status views that contain site information are described in this section.

### v\_ComponentSummarizer

Lists summary status information for all Configuration Manager components for different intervals. The view also provides the site code, server name, component name, the count of information, warning, and error messages, and so on. The information in this view contains the same information that is displayed in the **Component Status** node of the Configuration Manager console, but the view contains information for all display intervals. The value in the **Status** column provides the current status for the component. A value of 0 indicates that the component is OK, a value of 1 indicates a warning state for the component, and a value of 2 indicates a critical state for the component. The view can be joined to other views by using the **SiteCode**, **MachineName**, and **ComponentName** columns.

### v\_ServerMessageStatistics

Lists the site system servers, the associated site code, when the last heartbeat occurred, and how long the heartbeat took to process. The view can be joined to other views by using the **ServerName** column.

### v\_SiteDetailSummarizer

Lists status summary information for all Configuration Manager sites, by site code, for different intervals. The view also provides the site name, site version, interval, the count of information, warning, and error messages, and so on. The information in this view contains the same information that is displayed in the **Site Status** node of the Configuration Manager console, but the view contains information for all display intervals. The view can be joined to other views by using the **SiteCode** column. The value in the **Status** column provides the current status for the site. A value of 0 indicates that the site is OK, a value of 1 indicates a warning state for the site, and a value of 2 indicates a critical state for the site.

### v\_SiteSystemSummarizer

Lists status summary information for all Configuration Manager sites systems for different intervals. The view also provides the object location, the site role for the site system, total disk space, free disk space, and percentage of free disk space for the site system, the time of the last status reported, and whether the site system is available. The information in this view contains the same information that is displayed in the **Site System Status** node of the Configuration Manager console. The view can be joined to other views by using the **SiteCode** column.

### v\_SummarizerSiteStatus

Lists the site summary status, which is the same status displayed for the *&lt;site code&gt;* - *&lt;site name&gt;* node of the Configuration Manager console. The view can be joined to other views by using the **SiteCode** column.