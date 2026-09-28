---
layout: FAQ
title: Diagnostic and usage data FAQ - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/diagnostics/frequently-asked-questions
summary: >
  <p><em>Applies to: Configuration Manager (current branch)</em></p>

  <p>This article provides answers to frequently asked questions about diagnostic and usage data in Configuration Manager.</p>
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
description: Frequently asked questions about diagnostic and usage data for Configuration Manager
ms.date: 2021-12-01T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: faq
locale: en-us
document_id: 67741c7d-3871-af6a-f304-2138e1f27977
document_version_independent_id: 0b5352f4-840d-618f-f4c2-37d6ab33509b
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/diagnostics/frequently-asked-questions.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: faq
toc_rel: ../../toc.json
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/diagnostics/frequently-asked-questions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/diagnostics/frequently-asked-questions.yml
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/486161dc-fa28-4625-9b1c-1a21d690bc8d
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/5dd28c86-729c-4723-ab5a-57e26fcec2a8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: a364d30a-6f56-3b9a-049e-be7c90c8ddb3
---

# Diagnostic and usage data FAQ - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article provides answers to frequently asked questions about diagnostic and usage data in Configuration Manager.

## Can I turn off diagnostic and usage data?

To help manage when the site sends data, use the service connection point in offline mode. Then use the service connection tool to manually send data. For more information, see the following articles:

- [About the service connection point](../../servers/deploy/configure/about-the-service-connection-point)
- [Use the service connection tool](../../servers/manage/use-the-service-connection-tool)

To support new versions of Windows and cloud services like Microsoft Intune, you need to update the current branch of Configuration Manager on a regular basis. Microsoft requires at least the basic level of diagnostic and usage data. This data is used to keep the product up to date, improve the update experience, and improve the quality and security of the product.

No data is sent to the service when the service connection point is in offline mode. When you switch to online mode or use the service connection tool, it sends data to the service to check for updates.

You can also choose the level of data that Configuration Manager collects. For more information, see [Levels of diagnostic usage data](levels-overview).

## What is the data retention period?

Microsoft stores Configuration Manager diagnostic and usage data for one year.

## Is diagnostics and usage data sent when setup runs?

No. Diagnostics and usage data is only sent after the site is installed and operational.

## How frequently is the data sent?

The SQL Server stored procedures run every seven days from the date you installed the site.

- In online mode, the service connection point uploads the data after the queries run.
- In offline mode, you use the service connection tool to upload the data. (The data isn't initially available for offline use until seven days after you install the site.)

## Can the data be used to form a network map?

No. This data doesn't include any network details, such as IP addresses or detailed geographic information. For more information, see [Diagnostic and usage data for supported versions](levels-of-diagnostic-usage-data-collection).

The data does include time zone information from each site. This information can provide insight into the broad geolocation and global dispersion of sites in a hierarchy.

## Can you see data in custom SQL Server tables?

No. Configuration Manager collects diagnostics and usage data via SQL Server stored procedures. These stored procedures run against default product tables in the database. All of these SQL Server tables are prefixed with **TEL\_**. As part of the SQL Server schema detection query, all table names are hashed for comparison against the known defaults. This behavior determines that custom tables exist in the database. The presence of custom tables informs Microsoft that you extended the database schema from the default. It doesn't include any of the data stored within those tables.

## Can you see other databases?

No. The stored procedures to collect data are limited to the Configuration Manager site database. Microsoft can't see the names of other databases, or any data in other databases.

## Is any data sent to other integrated cloud services?

Yes, when you integrate those services with Configuration Manager. As part of the interaction with any cloud service, Configuration Manager sends some data to that service. This data is specific to that cloud service, and separate from Configuration Manager diagnostics and usage data. For more information on the specific data used in the interaction with another cloud service, see the documentation for that service.

For example, the following cloud services are a part of Microsoft Intune family of products:

- [Tenant attach data collection](../../../tenant-attach/data-collection)
- [Endpoint analytics data collection](../../../../endpoint-analytics/ref-data-collection)
- [Privacy and personal data in Intune](/en-us/mem/intune-service/protect/privacy-personal-data)
- [Windows Autopilot requirements](/en-us/windows/deployment/windows-autopilot/windows-autopilot-requirements)

## Does Configuration Manager collect any personal data?

No. Configuration doesn't collect or transmit any personal data or customer data. It's an on-premises product that you directly deploy, manage, and operate. The diagnostics and usage data that Microsoft collects improves the installation experience, quality, and security of future releases.

For more information about Configuration Manager data, see [Levels of diagnostic usage data](levels-overview).