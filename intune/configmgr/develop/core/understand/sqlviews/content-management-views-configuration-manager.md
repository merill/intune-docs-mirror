---
layout: Conceptual
title: Content management views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/content-management-views-configuration-manager
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
description: Provides the tools for you to manage content files for applications, packages, software updates, and operating system deployment.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c5e4348c-f46b-4f45-35ce-618b30dc6ef9
document_version_independent_id: b6fd39a1-866c-b6b6-448d-3adb4a776b31
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/content-management-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/content-management-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/content-management-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 98786fec-b507-d21e-2b48-52f0392f331c
---

# Content management views - Configuration Manager | Microsoft Learn

Content management in Configuration Manager provides the tools for you to manage content files for applications, packages, software updates, and operating system deployment.

## Content management views

The content management views are described in the following table.

### v\_ContentDistributionReport

Lists information about the content packages sent to each distribution point together with the status of the distribution and the current state of the distribution. This view can be joined to other views by using the **PkgID** column.

### v\_ContentDistributionMessages

Lists status returned by the content distribution process for Configuration Manager content packages, by ID. Returns the ID of the content package, recent status messages, and more. This view can be joined to other views by using the **PkgID** column.

### v\_DistributionPointInfoBase

Lists detailed information about each distribution point in the site, including the server name, the NAL path, any configured share name, whether it's Internet-facing and more. This view can be joined to other views by using the **ServerName** column.

### v\_DistributionPointMessages

List information about status messages sent by packages on each distribution point in the site. This info includes the last time that status was sent and the ID of the status message that was sent. This view can be joined to other views by using the **ID**, **DPID**, or **PkgID** columns.

### v\_DistributionPoints

Lists information about each distribution point in the Configuration Manager hierarchy, including the ID, the server name that hosts the distribution point, the site code, whether it's a pull distribution point, and more. This view can be joined to other views by using the **DPID** column.

### v\_DistributionStatus

Lists each content package and the current distribution status of the package. This includes the package ID, the ID of the distribution point, the time that status was last reported and more. This view can be joined to other views by using the **PkgID** column.

### v\_DistributionPointDriveInfo

Lists information about the location and the status of content on distribution points. This info includes the site code, NAL path, drive where the content is stored, total and free space on the drive, and more. It's unlikely that this view will be joined to other views.

### v\_DPGroupContentDetails

Lists information, by group ID about the content stored on distribution point groups. This includes the group ID, content package ID, number of packages pending install, number of packages successfully installed, and more. This view can be joined to other views by using the **GroupID** or **PkgID** columns.

### v\_DPGroupContentInfo

Lists, for each distribution point, the number of content packages installed, in progress, or failed. This view can be joined to other views by using the **GroupID** column.

### v\_DPGroupMembers

Lists, by group ID, the path to each distribution point in the group. It's unlikely that this view will be joined to other views.

### v\_DPGroupPackages

Lists, by group ID, the content packages that have been deployed to each distribution point group. It's unlikely that this view will be joined to other views.

### v\_DPStatusSummary

Lists, by NAL path, the summary status of each distribution point. This includes the number of packages distributed to the distribution point, the number of content distributions installed, in progress and failed. This view can be joined to other views by using the **DPNalPath** column.

### v\_Content

Lists, by package ID, each content package at the site, including the content ID, version, size of the source files in bytes, and more. This view can be joined to other views by using the **PkgID** column.

### v\_ContDistStatSummary

Lists, by package ID, each content package at the site, with details about which distribution points have been targeted with that content, together with the last status time, number if successful, pending and failed content distributions, and more. This view can be joined to other views by using the **PkgID** column.

### v\_ContentDistribution

Lists information about the content packages, by package ID, that have been sent to distribution points. This includes the ID of the distribution point, the current state and the date of the last status summary. This view can be joined to other views by using the **PkgID** column.

### v\_ContentDistributionHighlights

This view can be joined to other views by using the **PkgID** column.

### v\_ContentDistributionReport\_DP

Lists, sorted by distribution point NA: path, the current status of each distribution point. This includes the last status time, number of packages on the distribution point, number of content distributions in progress and the number of errors. This view can be joined to other views by using the **DPNalPath** column.

### v\_ContentDistributionVersions

Lists, by package ID, the package versions on each distribution point. This includes the site code, the NAL path of the distribution point, the latest source version and state, and more. This view can be joined to other views by using the **PkgID** column.

### v\_ContentInfo

This view lists information about content associated with an application or deployment. This includes the source location of the content, information about related content and more. This view can be joined to other views by using the **Content\_ID** column.

### v\_SMS\_DistributionPointGroup

Lists all distribution point groups in the site hierarchy by **GroupID**. Contains the name of the distribution point group, who created it and when, the number of distribution points in the group and more. It's unlikely that this view will be joined to other views.