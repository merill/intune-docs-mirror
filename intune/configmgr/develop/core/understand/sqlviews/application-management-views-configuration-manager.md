---
layout: Conceptual
title: Application management views - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/application-management-views-configuration-manager
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
description: Information about application management views and application management status views.
ms.date: 2019-04-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms: 'assetid: c424bd2b-f6ea-466c-91ca-c9550d94d9db'
ms.collection: tier3
locale: en-us
document_id: ef0af943-7129-0a93-e38a-a7e1bf09fb14
document_version_independent_id: c840424d-04cb-039b-a9bb-453a3d310d0f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sqlviews/application-management-views-configuration-manager.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sqlviews/application-management-views-configuration-manager
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sqlviews/application-management-views-configuration-manager.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: fe79b97a-269d-1353-ea33-3b36df751526
---

# Application management views - Configuration Manager | Microsoft Learn

The Configuration Manager application management views can be used to query for information about applications, packages and programs, deployments, distribution points, and more. These views will most often be joined to other views by using the **AdvertisementID**, **PackageID**, or **CollectionID** columns. Many of the status views also provide information about the status for applications and deployments.

The following sections provide detailed information about application management views and application management status views.

## Application management views

The application management views are described in this section.

### v\_Advertisement

Lists information about the deployment of packages and programs, including the deployment ID (**AdvertisementID**), deployment name (**AdvertisementName**), package ID, program name, collection ID, schedule information, and more. The **v\_Advertisement** view is similar to the **v\_AdvertisementInfo** view, but with additional time and flag data. The view can be joined to other views by using the **AdvertisementID**, **PackageID**, and **CollectionID** columns.

### v\_AdvertisementInfo

Lists information about deployed packages and programs, including the deployment ID (**AdvertisementID**), deployment name (**AdvertisementName**), package ID, program name, collection ID, schedule information and more. The **v\_AdvertisementInfo** view is similar to the **v\_Advertisement** view, but with additional package data. The view can be joined to other views by using the **AdvertisementID**, **PackageID**, and **CollectionID** columns.

### v\_CurrentAdvertisementAssignments

Lists the current application deployments, by advertisement ID, and the resource ID that is assigned the advertisement. The view can be joined to other views by using the **AdvertisementID** or **ResourceID** columns.

### v\_DistributionPoint

Lists the distribution points and the application and software updates packages contained on each in the Configuration Manager site hierarchy. This view also provides the package ID, NAL path to the distribution point, site code, site name, source site, last refresh time, status, and more. The view can be joined to other views by using the **PackageID** and **ServerNALPath** columns.

### v\_DistributionPointInfo

Lists the distribution points in the Configuration Manager site hierarchy, including server name, share name, NAL path, site code, whether it is a branch distribution point, whether it is a pull distribution point and more. The view can be joined to other views by using the **ServerName** and **NALPath** columns.

### V\_MDMApplications

Lists information about applications created for mobile devices including the application name, description, publisher and more. It is unlikely that this view will be joined to other views.

### v\_OS\_Details

Lists the Configuration Manager supported platforms, including operating system, architecture, and versions, on which each specified software distribution program can run. The view contains the package ID, program name, operating system name, platform, and minimum and maximum operating system versions. The view can be joined to other views by using the **PackageID** column.

### v\_SMSPackage

Lists the packages in the Configuration Manager site hierarchy, including package ID, package name, the path of the package source files, source site, priority, package flags, last refresh time, and so forth. All packages are listed, including software deployment packages, boot image packages, and more. The view can be joined to other views by using the **PkgID** column.

### v\_Program

Lists the programs for each package in the Configuration Manager site hierarchy, including program name, package ID, program command line, dependent programs, program flags, and so forth. The view can be joined to other views by using the **PackageID** column.

### v\_UserTargetedApps

Lists each Configuration Manager application that has been deployed to a user. Includes the application ID (**CI\_ID**), the collection to which the application has been deployed (if any), and whether the application requires approval. This view can be joined to other views by using the **CI\_ID** or **CollectionID** columns.

### v\_UserTargetedClassicApps

Lists each package and program that has been deployed to users. Includes the program ID, the category, the publisher, the package and program name and more. This view can be joined to other views by using the **ProgramID**, **PackageID**, or **CollectionID** columns.

### v\_DeploymentSummary

Lists all deployments that are currently active at the site. Includes the collection to which the deployment was targeted, the name of the deployment, the deployment time, deployment statistics and more. This view can be joined to other views by using the **CollectionID** or **PackageID** columns.

### v\_ApplicationModelInfo

Lists the applications, by **CI\_ID** that have been created. Also lists the deployment type technology and any secured key for the application. This view can be joined to other views by using the **CI\_ID** column.

### v\_AppModelTargetingDeploymentInfo

No description.

### v\_AppModelTargetingInfo

No description.

### v\_Package

Returns all packages that contain content for an application, package and program, or a task sequences at this site. This view can be joined to other views by using the **PackageID** column.

### v\_ClassicAppTargetingDeploymentInfo

No description.

### v\_ClassicAppTargetingInfo

No description.

### v\_ClassicDeploymentAssetDetails

Lists information and status for standard package and program deployments by deployment ID. This includes the program name, package name, collection to which it has been deployed, and more. This view can be joined to other views by using the **DeploymentID**, **PackageID**, **CollectionID** and **DeviceID** columns.

### v\_AppDeploymentSummary

Lists deployment statistics for about Configuration Manager applications that have been deployed to clients. This includes the **CI\_ID**, target collection, localized display name, description and more. This view can be joined to other views by using the **CI\_ID**, **AssignmentID** and **TargetCollectionID** columns.

### v\_AppDTDeploymentSummary

Lists information about deployment types that have been deployed to devices, by **CI\_ID**. This includes the deployment type name, the target collection, and status information about the deployment. This view can be joined to other views by using the **CI\_ID**, **AssignmentID** and **TargetCollectionID** columns.

### v\_AppDTLaunchSummary

Lists information, by **AppCI**, about deployment types that have run on client devices. This includes the assignment ID, the collection, the deployment type technology and more. This view can be joined to other views by using the **AppCI** column.

### v\_AppEvalErrors

Lists all devices, by machine ID where the application evaluation failed, for example, if the application failed any requirements rules. This view can be joined to other views by using the **MachineID** column.

### v\_AppInTaskSequenceDeployment

Lists, by task sequence name, all deployed task sequences that contain an application deployment. This includes the collection to which the task sequence was deployed and the deployment ID. This view can be joined to other views by using the **Name** column.

### v\_AppIntentAssetData

Lists for each computer (and each user if deployed to a user), compliance state information by **AssignmentID** and Application ID (**AppCI**). State information includes **ComplianceState**, **EnforcementState**, applicability, and desired compliance state. This view can be joined to other views by using the **ID** columns and to **vAppStatSummary** by using the **AppCI** column.

### v\_AppInTSDeployment

Lists, by name, all applications that are deployed by a task sequence. This view can be joined to other views by using the **Name** column.

### v\_ApplicationAssignment

Lists detailed information about Configuration Manager application deployments, by **AssignmentID**. This includes the name of the application, the collection to which it was deployed, the creation time and more. This view is particularly useful when you want to examine the status of your **cmshort** deployments. This view can be joined to other views by using the **AssignmentID** and **CollectionID** columns.

### v\_CatalogAppModelProperties

No description.

### v\_CatalogClassicAppProperties

No description.

### v\_UserAppRequests

Lists details about users requests for applications, sorted by **CI\_UniqueID**. This includes the application ID, the name of the user requesting the application, the display name of the application and the device from which the request was made. This view can be joined to other views by using the **CI\_UniqueID**, **Unique\_User\_Name0** and **Netbios\_Name0** columns.

### v\_UserAppsLocalizedPropsForCatalog

No description.

## Application management status views

The application management status views contain status and status summary information about application deployments, applications and packages and programs. For more information about status views, see [Status and Alert Views in Configuration Manager](status-alert-views-configuration-manager). The status views that contain application management information are described in this section.

### v\_AdvertisementStatusInformation

Lists all advertisement status message IDs, the message state, and the message name, such as succeeded, expired, failed, and retrying. The view can be joined to other advertisement status views by using the **MessageID** column.

### v\_ClientAdvertisementStatus

Lists all package and program deployments with the associated status for resources that have been targeted. The view can be joined to other views by using the **AdvertisementID**, **ResourceID**, and **LastStatusMessageID** columns.

### v\_ClientOfferSummary

Lists the package and program deployments, by **OfferID**, the count of Configuration Manager client computers that have been targeted, and the count of computers reporting not started, waiting, running, retrying, failed, and succeeded status for the advertisement. The view can be joined to other views by using the **OfferID** column, which is the same as the **AdvertisementID** column in other views, and **PkgID** column, which is the same as the **PackageID** column in other views.

### v\_PackageStatus

Lists the status for all software distribution and software update deployment packages, as well as the package server location, last update time, last status and more. The view can be joined to other views by using the **PackageID** column.

### v\_PackageStatusDetailSumm

Lists all applications and packages and programs, by Package ID, the originating site code, package name, site name, source version, the date for the summary information, the targeted count for each package, and the count for installed, retrying, and failed status. The view can be joined to other views by using the **PackageID** column.

### v\_PackageStatusDistPointsSumm

Lists all packages, by package ID, and the installation status for the package source files on all associated distribution points. The view also provides information such as the site code, path to the distribution point, path to source location, time of last copy, and so on. The view can be joined to other views by using the **PackageID** and **ServerNALPath** columns.

### v\_PackageStatusRootSummarizer

Lists all applications and packages and programs, by package ID, the package name, source version, source date, the source site, size of the source files, the targeted count for each package, and the count for installed, retrying, and failed status. The view can be joined to other views by using the **PackageID** column.

### v\_PeerDPStatusInfo

Lists the peer distribution point states and associated state names. It is unlikely that this view will be joined to other views.

### v\_ProgramOffers

Lists all programs that have been deployed as part of a package and program. This is sorted by package ID and the program name. The view can be joined to other views by using the **PkgID** column.

## User device affinity views

The user device affinity views contain information about configured relationships between users and primary devices. The views that contain user device affinity information are described in this section.

### v\_UsersPrimaryMachines

Lists, by user resource ID, the primary devices for that user. This view can be joined to other views by using the **MachineID** or **UserResourceID** columns.

### v\_UserMachineIntelligence

Lists information, by resource ID about user logons to devices. This information can be used by user device affinity to create automatic affinities. The information collected includes the user name, device name, client type, number of logons, and time spent for each session. This view can be joined to other views by using the **MachineResourceID** column.

### v\_UserMachineRelation

Lists detailed information about user device relationships in the Configuration Manager site including the relationship ID, the user name, the device ID, the creation time and more. This view can be joined to other views by using the **MachineResourceID** column.

### v\_UserMachineRelationship

Lists information about users and their primary devices in the site. Includes the user name, the device resource ID, the time the relationship was created, and more. This view can be joined to other views by using the **UniqueUserName** or **MachineResourceID** columns.

### v\_UserMachineSourceRelation

Lists all user device affinity relationships, by relationship resource ID, when they were created, and who created them. This view can be joined to other views by using the **RelationshipResourceID** column.

### v\_UserMachineTypeRelation

Lists user and device relationships by relationship resource ID, relationship type, and creation time. It is unlikely that this view will be joined to other views.