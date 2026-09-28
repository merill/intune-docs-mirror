---
layout: Conceptual
title: Technical preview 2102 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/get-started/2021/technical-preview-2102
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
description: Learn about new features available in the Configuration Manager technical preview branch version 2102.
ms.date: 2021-02-19T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: whats-new
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 5978a560-5cf3-295f-5863-0d7d2bb4fb38
document_version_independent_id: 8cfe6ef9-0749-3cbe-d945-06ffc0355845
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/get-started/2021/technical-preview-2102.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/get-started/2021/technical-preview-2102
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/get-started/2021/technical-preview-2102.md
platformId: 3d7be6bc-5b76-b1c0-4224-a5b0f2a987a6
---

# Technical preview 2102 - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (technical preview branch)*

This article introduces the features that are available in the technical preview for Configuration Manager, version 2102. Install this version to update and add new features to your technical preview site.

Review the [technical preview](../technical-preview) article before installing this update. That article familiarizes you with the general requirements and limitations for using a technical preview, how to update between versions, and how to provide feedback.

The following sections describe the new features to try out in this version:

## Improvements to the collection relationships viewer

Starting in current branch version 2010, you can view [dependency relationships between collections](../../clients/manage/collections/view-relationships) in a graphical format. The relationships for a collection were presented as two hierarchical trees, one for dependents and the other for dependencies. In this release, you can view both dependency and dependent relationships together in a single graph. This change allows you to quickly see an overview of all the relationships of a collection at once and then drill down into specific related collections. It also includes other filtering and navigation improvements.

The following example shows the relationships for the "c1" collection in the center. It's dependent upon the collections above it, and has dependencies below it.

[![Example graph of collection relationships](media/8543508-view-collection-relationships.png)](media/8543508-view-collection-relationships.png#lightbox)

To see the relationships of another collection in the graph, select it to open a new window targeted on that collection.

Other improvements:

- There's a new **Filter** button in the upper right corner. This action lets you reduce the graph to specific relationship types: **Limiting**, **Include**, or **Exclude**.
- If you don't have permissions to all related collections, the graph includes a warning message that the graph may be incomplete.
- When the graph is wider than the window can display, use the page navigation controls in the upper left corner. The first number is the page for dependencies (below), the second number is the page for dependents (above). The window title also shows the page numbers.
- The tooltip for a collection displays the count of dependencies it has and the count of dependant collections where applicable. This count only includes unique sub-collections. The count no longer displays in the parentheses next to the collection name.
- Previously the **Back** button took you through your viewing history. Now it takes you to the previously selected collection. For example, changing pages for the current collection doesn't activate the **Back** button. When you select a new collection, you can select **Back** to return to the original collection graph.

## Improvements to BitLocker support via cloud management gateway

In current branch version 2010, you can manage BitLocker policies and escrow recovery keys over a cloud management gateway (CMG). This support included a couple of limitations.

Starting in this technical preview release, BitLocker management policies over a CMG support the following capabilities:

- Recovery keys for removable drives
- TPM password hash, otherwise known as TPM owner authorization

For more information on BitLocker management over CMG, see [Deploy BitLocker management](../../../protect/deploy-use/bitlocker/recovery-service).

## TLS certificate pinning for devices scanning HTTPS-configured WSUS servers

Further increase the security of HTTPS scans against WSUS by enforcing certificate pinning. To enable this behavior, add certificates for your WSUS servers to the new `WindowsServerUpdateServices` certificate store on your clients and enable certificate pinning through **Client Settings**. This setting ensures that your clients will only be able to communicate with WSUS when certificate pinning is successful. For more information, see [Scan changes and certificates add security for Windows devices using WSUS for updates - Microsoft Tech Community](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/scan-changes-and-certificates-add-security-for-windows-devices/ba-p/2053668).

### Try it out!

Try to complete the tasks. Then send [Feedback](/en-us/configmgr/core/understand/find-help#product-feedback) with your thoughts on the feature.

### Prerequisites

- The WSUS server must be [enabled for TLS/SSL](../../../sum/get-started/software-update-point-ssl)
- The WSUS server's certificate must be in the client's `WindowsServerUpdateServices` certificate store

### Enable or disable TLS certificate pinning for devices scanning HTTPS-configured WSUS servers

1. From the Configuration Manager console, go to **Administration** &gt; **Client Settings**.
2. Choose the **Default Client Settings** or a custom set of client settings, then select **Properties** from the ribbon.
3. Select the **Software Updates** tab in the **Client settings**
4. Choose one of the following options for the **Enforce TLS certificate pinning for Windows Update client for detecting updates**setting:
    - **No**: Don't enable enforcement of TLS certificate pinning for WSUS scanning
    - **Yes**: Enables enforcement of TLS certificate pinning for devices during WSUS scanning (default for this technical preview)

## Improvements to collection evaluation view

The following improvements were made to the collection evaluation view:

- The central administration site (CAS) now displays a summary of collection evaluation status for all the primary sites in the hierarchy
- Drill through from collection evaluation status queue to a collection
- Copy text to the clipboard from the collection evaluation page
- Configure the refresh interval for the collection evaluation statistics page

### Collection evaluation information at the CAS

Since collection evaluation happens at the primary site level, the collection evaluation view on the CAS is a summary of what's occurring on the primary sites.

There are two new tabs in the details pane of the collection view in the console. The following new tabs show collection evaluation information from all primary sites in hierarchy:

- **Evaluation (Full) In Hierarchy**
- **Evaluation (Incremental) In Hierarchy**

[![Collection evaluation tabs in the collection's details pane at the CAS](media/8787410-collection-evaluation-details-tab.png)](media/8787410-collection-evaluation-details-tab.png#lightbox)

From the **Device Collections** node at the CAS, the evaluation columns display the evaluation status from the primary site with the longest run time. The column information at the CAS for the full evaluation status could be from a different primary site than the incremental information since the longest runtime for the incremental might have occurred at a different primary.

For instance, incremental evaluation for the `All Systems` collection on the `WMII` primary site takes longer than the other primary sites. The full evaluation columns on the CAS display the information from primary site `WMI` for the `All Systems` collection in the **Device Collections** node.

[![Collection evaluation columns at the CAS with the details tab open displaying the evaluation from all primary sites](media/8787410-cas-collection-evaluation-columns.png)](media/8787410-cas-collection-evaluation-columns.png#lightbox)

### Drill through from collection evaluation queue or status view to a collection

You can now navigate to a collection in the **Assets and Compliance** workspace from a collection evaluation status view or evaluation queue in the **Monitoring** workspace. Select a collection from one of the status views or queues, then choose **View collection** from the ribbon or right-click menu to open the collection.

Navigation to the collection from queues won't occur if the collection evaluation has completed. You can only drill though from an item in a queue that's still currently running its evaluation. If the evaluation has already completed, the **View collection** action takes you to the main collection view. Drill though from the evaluation status views, **Full Evaluation Status** and **Incremental Evaluation Status**, will always take you to the collection.

[![View collection option in the ribbon of the Full Evaluation Status node](media/8787410-view-collection.png)](media/8787410-view-collection.png#lightbox)

### Configure refresh interval for the collection evaluation statistics page

You can configure a primary site's refresh interval for the **Collection Evaluation** statistics page to be between 1 minute and 1440 minutes (1 day). Typically, collection evaluation occurs over the course of seconds or minutes. However, you can change the statistics refresh to accommodate your environment. The default refresh interval is 5 minutes.

[![Refresh interval for the evaluation statistics on the primary site](media/8787410-refresh-interval.png)](media/8787410-refresh-interval.png#lightbox)

### Copy text to clipboard from collection evaluation statistics page

You can copy collection evaluation statistics as structured text to the clipboard. Use the **Copy** button in the ribbon to copy the statistics. When the text is pasted into a text editor, it's structured to make it easy to read.

[![Copy button in the ribbon for collection evaluation statistics with Notepad open to show the structured text that's copied](media/8787410-copy-statistics.png)](media/8787410-copy-statistics.png#lightbox)

### Full and incremental evaluation status nodes

The **Full Evaluation Status** and **Incremental Evaluation Status** subnodes have been readded to the **Collection Evaluation** node in the **Monitoring** workspace.

- On a primary site, **Full Evaluation Status** and **Incremental Evaluation Status** show the data for the local evaluations.
- On a CAS, **Full Evaluation Status** and **Incremental Evaluation Status** shows the data from the primary site with the longest run time.

    - Using the longest runtime for these nodes is the same logic that's used for the collection evaluation columns at the CAS.

[![Full Evaluation Status node at the CAS ](media/8787410-full-evaluation-status-node-cas.png)](media/8787410-full-evaluation-status-node-cas.png#lightbox)

## Improvements to query preview

You now have more options when using the [collection query preview](../2020/technical-preview-2008#collection-query-preview). The following improvements have been made to previewing collection queries:

- Limit the number of rows returned
    - Your limit can be between 1 to 10,000 rows. The default is 5000 rows.
- Omit duplicate rows from the result set
    - If the **Omit duplicate rows** option isn't selected, the original query statement will be executed as is, even if the query contains the word **distinct**.
    - When the **Omit duplicate rows** option is selected, if the query already contains the word **distinct**, then the query runs as it is. When the query doesn't contain the word **distinct**, it's added to the query for the preview (mean override).
- Review statistics for the query preview such as number of rows returned and elapsed time.

[![Limiting rows returned and omitting duplicate rows when previewing a quiery](media/8680235-limited-query-preview.png)](media/8680235-limited-query-preview.png#lightbox)

Note

- Elapsed times shown for the query preview may not be the same as actual execution of the target query.
- **Query execution elapsed time** and **Displaying results elapsed time** shouldn't be added for a total elapsed time since these processes run in parallel.

## Add a report as a favorite

Configuration Manager ships with several hundred reports by default, and you may have added more to that list. Instead of continually searching for reports you commonly use, based on your feedback, you can now make a report a favorite. This action allows you to quickly access it from the new **Favorites** node.

The list of favorites is per user, not per site or hierarchy.

### Prerequisites for report favorites

The version of SQL Server Reporting Services on the site's reporting service point needs to be SQL Server 2017 or later.

Note

All instances of SQL Server Reporting Services on the server need to be version 2017 or later.

### Try it out!

Try to complete the tasks. Then send [Feedback](/en-us/configmgr/core/understand/find-help#product-feedback) with your thoughts on the feature.

1. In the Configuration Manager console, go to the **Monitoring** workspace. Expand the **Reporting** node, and select either the **Reports** or **Power BI Reports** node.
2. Select a report that you frequently use. Then in the ribbon, select **Add to Favorites**. The report's icon changes to a yellow star, which indicates that it's a favorite.

    Tip

    You can select more than one report to add them all as favorites.

    To remove a report from the list of favorites, select it, and then select **Remove from Favorites**. When you remove a favorite, Configuration Manager doesn't delete the report.
3. Under the **Reporting** node, expand the new **Favorites** node. To view your list of favorites, select either the **Reports** or **Power BI Reports** node.

    Tip

    You can directly connect to your favorite reports in your browser. For example, `https://rsp.contoso.com/Reports/favorites`.

    You can manage the reports the same from the list of favorites.

## Download Power BI report templates from Community hub

Community hub now supports contributing and downloading Power BI report template files. This integration allows administrators to easily share and reuse Power BI reports. Contributing and downloading Power BI report template is also available for current branch versions of Configuration Manager. For more information, see [Power BI report templates in Community hub](../../servers/manage/powerbi-report-server#bkmk_community_hub) and [Using Community hub](../../servers/manage/community-hub).

## Change foreground color for Software Center branding

Software Center already provides various controls for you to customize the branding to support your organization's brand. For some customers, their brand color doesn't work well with the default white font color for a selected item. To better support these customers and improve accessibility, you can now configure a custom color for the foreground font.

When you customize [Software Center in client settings](../../clients/deploy/about-client-settings#software-center), there's a new option for **Foreground color for Software Center**.

![Software Center with customized branding](media/8655575-software-center-foreground-color.png)

## Changes for CMPivot

We've temporarily disabled the [Simplified CMPivot permissions requirements](technical-preview-2101#bkmk_permission) that were introduced in technical preview version 2101. If you removed the **Read** permission on **SMS Scripts** and the **default scope** permission, readd the permissions.

## Improvements to client setting for Software Center custom tabs

Technical preview version 2101 included a new client setting for displaying Software Center custom tabs. There are general improvements to this feature in this technical preview release. For information on how to try it out, see [2101 features](technical-preview-2101#bkmk_webview).

## PowerShell release notes preview

These release notes summarize changes to the Configuration Manager PowerShell cmdlets in technical preview version 2102.

For more information about PowerShell for Configuration Manager, see [Get started with Configuration Manager cmdlets](/en-us/powershell/sccm/overview).

### New cmdlets

#### Set-CMCISupportedPlatform

Use this cmdlet to configure the platforms for a configuration item.

##### Example 1: Set platform for configuration item

```powershell
$mac_ci=Get-CMConfigurationItem -Name "Mac CI"
$mac_platform1=Get-CMSupportedPlatform -Name "Mac OS X 10.8"
$mac_platform2=Get-CMSupportedPlatform -Name "Mac OS X 10.9"
$mac_platforms =$mac_platform1,$mac_platform2
$mac_platform3=Get-CMSupportedPlatform -Name "Mac OS X 10.7"
$mac_platform4=Get-CMSupportedPlatform -Name "Mac OS X 10.6"
$mac_platforms2=$mac_platform3,$mac_platform4
Set-CMCISupportedPlatform -InputObject $mac_ci -AddSupportedPlatform $mac_platforms  -RemoveSupportedPlatform $mac_platforms2
```

### Modified cmdlets

#### Add-CMFallbackStatusPoint

**Non-breaking changes**

Fixed an inconsistent parameter name.

#### Get-CMDeploymentStatusDetails

**Non-breaking changes**

- Fixed input object type validation issue for types like **SMS\_DCMDeploymentErrorStatus**, **SMS\_DCMDeploymentNonCompliantStatus**, and **SMS\_DCMDeploymentCompliantStatus**.
- Fixed output invalid class type issue by changing output object type **SMS\_AppDeploymentRequirementsNotMetStatus** to **SMS\_AppDeploymentRequirementsNotMetAssetDetails**.
- Changed the output object type from **SMS\_AppDeploymentAssetDetails** to [SMS_AppDeploymentErrorAssetDetails](../../../develop/reference/apps/sms_appdeploymenterrorassetdetails-server-wmi-class) to get more error details.
- Added an input object type **SMS\_UpdateDeploymentSummary** so that this cmdlet can get update deployment details. When passing the output of [Get-CMSoftwareUpdateDeploymentStatus](/en-us/powershell/module/configurationmanager/get-cmsoftwareupdatedeploymentstatus) to Get-CMDeploymentStatusDetails, it returns deployment details from **SMS\_SUMDeploymentAssetDetails**.

#### Get-CMSoftwareUpdateDeployment

**Non-breaking changes**

Fixed an issue when deploying updates with no package.

#### Set-CMEmailProfile

**Non-breaking changes**

- Fixed issue with **NewName** parameter when you specify `sAMAccountName` as the account user name.
- Fixed a parameter issue when resolving **DomainName**.

#### Set-CMFallbackStatusPoint

**Non-breaking changes**

Fixed an inconsistent parameter name.

## Change default maximum run time for software updates

Configuration Manager sets the following maximum run time for these categories of software updates:

- **Feature updates for Windows**: 120 minutes
- **Non-feature updates for Windows**: 60 minutes
- **Updates for Microsoft 365 Apps** (Office 365 updates): 60 minutes

All other software updates outside these categories, such as third-party updates, were given a maximum run time of 10 minutes. Starting in this technical preview, the default maximum run time for these updates is 60 minutes rather than 10 minutes.

## General known issues

### Issue with Microsoft Intune admin center notifications with version 2102

Following the release of technical preview version 2102, there's an issue with Microsoft Intune admin center notifications. You can still onboard a version 2102 site for tenant attach, but the cloud console will show an on-premises error.

To resolve this issue, update your technical preview site to version 2103.