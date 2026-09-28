---
layout: Conceptual
title: Compliance settings classes - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes
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
description: Assists you in assessing computer compliance. You can also use these classes to check for compliance with software updates and security settings.
ms.date: 2019-08-02T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 1bfafc10-cbf6-d27a-f66f-a9188bc955d0
document_version_independent_id: 017ccde5-d86e-0d16-13df-6e6c28a1031a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/compliance/compliance-settings-dcm-server-wmi-classes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 97cc6a84-db62-b2fe-8ca9-c5350c3e241b
---

# Compliance settings classes - Configuration Manager | Microsoft Learn

In Configuration Manager, compliance settings server WMI classes assist you in assessing computer compliance. You can consider a number of configurations, for example, installation and configuration of the correct versions of Windows operating systems. You can also use these classes to check for compliance with software updates and security settings.

The main classes supporting the compliance settings feature are:

- [SMS_ConfigurationItem server WMI class](sms_configurationitem-server-wmi-class), representing a generic configuration item.
- [SMS_ConfigurationBaselineInfo server WMI class](sms_configurationbaselineinfo-server-wmi-class), representing information for a baseline configuration item.
- [SMS_BaselineAssignment server WMI class](sms_baselineassignment-server-wmi-class), representing an assignment of a baseline configuration item.

For more information, see [About configuration baselines and configuration items](../../compliance/about-configuration-baselines-and-configuration-items).

Note

Some of the classes for compliance settings, for example, [SMS_ConfigurationBaselineInfo server WMI class](sms_configurationbaselineinfo-server-wmi-class), are specific to baseline configuration items. Some of the classes can also be used to reference software update configuration items, although applications use the software updates feature to manipulate these items. For more information, see [About software update deployments](../../sum/about-software-updates-deployments).

The Configuration Manager server class schema is a set of WMI classes that represent the objects on a server running Configuration Manager. Each Configuration Manager class is a template for a managed object and all instances of the object use the template. Classes can contain properties and methods. The properties describe the class data, and the methods typically perform data management. For more information about developing applications using these classes, see [About Configuration Manager SDK requirements](../../core/reqs/about-configuration-manager-sdk-requirements).