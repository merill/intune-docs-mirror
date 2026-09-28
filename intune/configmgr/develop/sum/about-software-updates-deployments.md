---
layout: Conceptual
title: Software Updates Deployments - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/sum/about-software-updates-deployments
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
ms.date: 2016-12-30T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
description: Learn about how to create software update deployments using the Configuration Manager SDK interfaces to deliver updates to client computers.
locale: en-us
document_id: f6a6183c-e5f1-e0a5-e675-4301b813025a
document_version_independent_id: 300939de-0c78-a94e-8130-ec84644f3f34
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/sum/about-software-updates-deployments.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/sum/about-software-updates-deployments
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/sum/about-software-updates-deployments.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: edf4c196-01d3-43b8-b5f1-347f6d19feb5
---

# Software Updates Deployments - Configuration Manager | Microsoft Learn

Software updates are delivered to client computers in Configuration Manager by creating software update deployments. It is a multistep process to create software update deployments by using the Configuration Manager SDK interfaces. A basic approach to deploying software updates, by using the Configuration Manager SDK interfaces, is outlined below.

For more information about software updates, see [Deploy and manage software updates](../../sum/understand/software-updates-introduction).

Note

Deleting updates or update bundles is not supported by the Configuration Manager SDK.

Select which software updates to install. This can be something such as running a query to identify which updates should be installed.

For information about queries that use criteria, such as selecting software updates for a specific knowledge base article, or selecting software updates that are a specific severity level, see [How to Enumerate Updates Matching a Specific Criteria](how-to-enumerate-updates-matching-a-specific-criteria).

Obtain the configuration item identification (CI\_ID) values. The CI\_ID value identifies the software updates information across several classes. For the purposes of using the Configuration Manager SDK interfaces, the CI\_ID value is vital.

The CI\_ID value is a property of several classes and can be readily identified by using the [SMS_SoftwareUpdate](../reference/sum/sms_softwareupdate-server-wmi-class) class.

For more information about a number of queries that include the CI\_ID, see [How to Enumerate Updates Matching a Specific Criteria](how-to-enumerate-updates-matching-a-specific-criteria).

Download the software update content. Software update content must be downloaded manually. To identify which contents must be downloaded, query the [SMS_CIToContent](../reference/sum/sms_citocontent-server-wmi-class) class and obtain the list of `ContentID` properties that match the specific language criteria. After you have the list of `ContentID` properties, you can obtain the associated download URL and the related properties for the content files from the [SMS_CIContentFiles](../reference/sum/sms_cicontentfiles-server-wmi-class) class by using the `ContentID` properties you obtained earlier.

Create a software updates deployment package. The software updates deployment package holds the software updates content. For information about creating a deployment package, see [How to Create a Deployment Package](how-to-create-a-deployment-package).

Add update content to the software updates package. After a software updates deployment package has been created, software updates contents can be added to the package by using the [AddUpdateContent](../reference/sum/addupdatecontent-method-in-class-sms_softwareupdatespackage) method in the [SMS_SoftwareUpdatesPackage](../reference/sum/sms_softwareupdatespackage-server-wmi-class) class. For information about adding software updates content to a deployment package, see [How to Add Updates to a Deployment Package](how-to-add-updates-to-a-deployment-package).

Create a software updates deployment to distribute the software updates. Distribute software updates by creating a software updates deployment. For information about the process for creating a software updates deployment, see [How to Configure and Deploy Updates](how-to-configure-and-deploy-updates).