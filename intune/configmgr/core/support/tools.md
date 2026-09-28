---
layout: Conceptual
title: Configuration Manager Tools - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/support/tools
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
description: Learn about the tools to help you manage and troubleshoot your Configuration Manager infrastructure.
ms.date: 2024-12-04T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: overview
ms.collection:
- tier3
- essentials-manage
locale: en-us
document_id: aa68c3c1-8f4a-5e56-0dc1-d45832598a1c
document_version_independent_id: 77c73540-9395-3fe7-71df-8e7a63ee439c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/support/tools.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/support/tools
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/support/tools.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
platformId: a5d1f08f-2dc2-4db3-d1af-a0c9eaefc214
---

# Configuration Manager Tools - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

The Configuration Manager tools primarily include client-based and server-based tools. Use these tools to help support and troubleshoot your Configuration Manager infrastructure.

These tools are included in the `CD.Latest\SMSSETUP\Tools` folder on the site server. No further installation is required. Use these versions of the tools with supported versions of Configuration Manager current branch.

All Windows operating systems listed as supported clients in [Supported operating systems for clients and devices](../plan-design/configs/supported-operating-systems-for-clients-and-devices) are supported for use with these tools.

Note

For supported versions of Configuration Manager current branch, use the versions of the tools in the CD.Latest folder on the site server. Some tools were formerly in the toolkit but not included current branch. These legacy tools are no longer supported.

## Client tools

These tools are in the `ClientTools` subfolder:

- [Client Spy](clispy): Troubleshoot issues related to software distribution, inventory, and metering
- [Deployment Monitoring Tool](deployment-monitoring-tool): Troubleshoot applications, updates, and baseline deployments
- [Policy Spy](policy-spy): View policy assignments
- [Power Viewer Tool](power-viewer-tool): View status of power management feature
- [Send Schedule Tool](send-schedule-tool): Trigger schedules and evaluations of configuration baselines

Note

The `ClientTools` folder also includes the file Microsoft.Diagnostics.Tracing.EventSource.dll. Several client tools require this library. You can't directly use it.

## Server tools

These tools are in the `ServerTools` subfolder:

- [DP Job Queue Manager](dp-job-manager): Troubleshoots content distribution jobs to distribution points
- [Collection Evaluation Viewer](ceviewer): View collection evaluation details

    Important

    Starting in Configuration Manager version 2103, this standalone tool isn't supported. The tool is no longer included with the Configuration Manager installation source. Starting in version 2010, its functionality is built-in to the console. For more information, see, [How to view collection evaluation](../clients/manage/collections/collection-evaluation-view).
- [Content Library Explorer](content-library-explorer): View contents of the content library single instance store
- [Content Library Transfer](content-library-transfer): Transfers content library between drives
- [Content Ownership Tool](content-ownership-tool): Changes ownership of orphaned packages. These packages exist in the site without an owning site server.
- [Role-based Administration and Auditing Tool](rbaviewer): Helps administrators audit roles configuration

    Note

    Starting in version 2107, RBAViewer has moved from `<installdir>\tools\servertools\rbaviewer.exe`. It's now located in the Configuration Manager console directory. After you install the console, RBAViewer.exe will be in the same directory. The default location is `C:\Program Files (x86)\Microsoft Endpoint Manager\AdminConsole\bin\rbaviewer.exe`.
- [Run Meter Summarization Tool](run-meter-summ): Run metering summarization task and analyze metering data

Note

The ServerTools folder also includes the following files:

- AdminUI.WqlQueryEngine.dll
- Microsoft.ConfigurationManagement.ManagementProvider.dll
- Microsoft.Diagnostics.Tracing.EventSource.dll

Several server tools require these libraries. You can't directly use them.

## More tools in the folder

The following tools are in the `CD.Latest\SMSSETUP\TOOLS` folder on the site server:

- [CMTrace](cmtrace): View, monitor, and analyze Configuration Manager log files.
- [CMPivot](../servers/manage/cmpivot): Use the standalone version of this tool to query real-time data from clients.
- [Update reset tool](../servers/manage/update-reset-tool): Fix issues when in-console updates have problems downloading or replicating.
- [Configuration Manager group policy administrative template](../clients/deploy/deploy-clients-to-windows-computers#configure-and-assign-client-installation-properties-by-using-a-group-policy-object): Configure and assign client installation properties by using a group policy object.
- [Content library cleanup tool](../plan-design/hierarchy/content-library-cleanup-tool): Remove orphaned content from a distribution point.
- [Extend and migrate on-premises site to Microsoft Azure](azure-migration-tool): Helps you to programmatically create Azure virtual machines (VMs) for Configuration Manager.
- [Synchronize Microsoft 365 Apps updates from a disconnected software update point](../../sum/get-started/synchronize-office-updates-disconnected) (OfflineUpdateExporter): Import Microsoft 365 Apps updates from an internet connected WSUS server into a disconnected Configuration Manager environment.
- [Configure client communication ports](../clients/deploy/configure-client-communication-ports): Reconfigure the port numbers for existing clients.
- [Service Connection Tool](../servers/manage/hierarchy-maintenance-tool-preinst.exe): Keep your site up to date when your service connection point is offline.
- [Support Center](support-center): Gather information from clients for easier analysis when troubleshooting.

    **OneTrace** is a modern log viewer with Support Center. It works similarly to CMTrace, with improvements. For more information, see [Support Center OneTrace](support-center-onetrace).
- [Send feedback that you saved for later submission](../understand/product-feedback#send-feedback-that-you-saved-for-later-submission) (UploadOfflineFeedback): Save your product feedback locally and submit it later.

## Other tools

- [Hierarchy Maintenance Tool](../servers/manage/hierarchy-maintenance-tool-preinst.exe): Use **Preinst.exe** in the `\<SiteServerName>\SMS_<SiteCode>\bin\X64\00000409` shared folder on the site server to pass commands to the hierarchy manager component.
- [Microsoft Deployment Toolkit (MDT)](../../mdt/use-the-mdt): A collection of tools, processes, and guidance for automating desktop and server OS deployments.
- [System Center Updates Publisher (SCUP)](../../sum/tools/updates-publisher): A stand-alone tool to manage and import custom software updates.
- [Package Conversion Manager](../../apps/pcm/package-conversion-manager): Convert legacy packages into applications.