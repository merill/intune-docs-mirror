---
layout: Conceptual
title: Device Management Server WMI Classes - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/mdm/device-management-server-wmi-classes
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
description: Device management server Windows Management Instrumentation (WMI) classes in Configuration Manager assist in assessment of computer compliance considering a number of mobile device configurations.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 45411397-d923-e7fa-8b94-22a3a741d038
document_version_independent_id: d1df26cf-b83a-014c-12af-3f8b998e2f98
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/mdm/device-management-server-wmi-classes.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/mdm/device-management-server-wmi-classes
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/mdm/device-management-server-wmi-classes.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 264289f1-c603-0f90-dd76-985b80d7fd9d
---

# Device Management Server WMI Classes - Configuration Manager | Microsoft Learn

Device management server Windows Management Instrumentation (WMI) classes in Configuration Manager assist in assessment of computer compliance considering a number of mobile device configurations.

The Configuration Manager server class schema is a set of WMI classes that represent the objects found on a server that is running Configuration Manager. Each Configuration Manager class is a template for a managed object and all instances of the object use the template. Classes can contain properties and methods. The properties describe the class data and the methods typically perform data management. For more information about developing applications using these classes, see [About Configuration Manager SDK Requirements](../../core/reqs/about-configuration-manager-sdk-requirements).

## Mobile Device Management Classes

- [SMS_DeviceEnrollmentProfile Server WMI Class](sms_deviceenrollmentprofile-server-wmi-class)
- [SMS_DeviceMethods Server WMI Class](sms_devicemethods-server-wmi-class)
- [SMS_DeviceSettingItem Server WMI Class](sms_devicesettingitem-server-wmi-class)
- [SMS_DeviceSettingPackage Server WMI Class](sms_devicesettingpackage-server-wmi-class)
- [SMS_DeviceSettingPackageItem Server WMI Class](sms_devicesettingpackageitem-server-wmi-class)

## Remarks

Configuration Manager uses its device management functionality for mobile devices. It uses a special type of configuration item to represent a set of mobile device settings to apply to a mobile device. The device setting configuration item can only be distributed by using a device setting package that is accessible in the Configuration Package wizard in the Configuration Manager console. Source locations are defined automatically when creating the package.

Note

Mobile devices do not have domain accounts and therefore do not recognize access account restrictions.