---
layout: Conceptual
title: SMS Provider Fundamentals - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sms-provider-fundamentals
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
description: Use the SMS Provider to access and modify Configuration Manager data. It is a WMI provider that can be accessed through either WMI or managed classes.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 51e06fda-d037-b661-c079-c82dfc0d9586
document_version_independent_id: 49615e49-1448-a011-c2c9-02ed64e92ff5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/sms-provider-fundamentals.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/sms-provider-fundamentals
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/sms-provider-fundamentals.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: 76c8e996-6aac-0de2-3c21-1c979af645de
---

# SMS Provider Fundamentals - Configuration Manager | Microsoft Learn

You use the SMS Provider to access and modify Configuration Manager data. The SMS Provider is a Windows Management Instrumentation (WMI) provider that can be accessed through either WMI or managed classes.

## WMI Architecture

WMI is designed to function as a middle layer, by serving as a standard interface between management applications and the systems that they manage.

### WMI Object Model

Management applications and scripts work with WMI through the WMI Object Model. The object model defines the programming interface to WMI.

For more information about WMI, see [Windows Management Instrumentation](/en-us/windows/win32/wmisdk/wmi-start-page).

The main elements of the WMI Object Model are shown in the following table:

| Element | Description |
| --- | --- |
| Locator | Used to locate a WMI Service that is running on a local or remote computer. |
| Service object | Represents an actual connection to a WMI provider. This is the main point of contact to WMI programs. |
| Objects | A managed object is a logical or physical enterprise component, such as a hard drive, network adapter, database system, operating system, process, or service. A managed object communicates with WMI through a WMI provider. |
| Events | Used to track changes to WMI objects at run time. Events can be captured as objects and then manipulated in the same ways that any other objects, except that they cannot be changed or saved in WMI. |
| Properties | Supplies descriptive or operational information about an object. For example, a `Win32_DiskDrive` object includes a property called `InterfaceType`, which might have the value of IDE for your C: drive. Properties can also be set to particular values, if the property is changeable. Setting `InterfaceType` to SCSI is not appropriate, because the only way to change the actual interface type is to replace the controller card. However, you can set a share name to a different value. |
| Methods | Actions that you can execute on objects. For example, a `Win32_Directory` object includes a method called `Compress()` that allows the contents of a folder to be compressed in the same way as compressing the contents by using the Windows graphical user interface. |
| Qualifiers | Characteristics of objects, properties, and methods. For example, a qualifier for a property might indicate that it is read-only, or it might list the allowable values for the property. A qualifier for an object might be that it is read-only. |

## Schema

WMI objects are described by classes, providing definitions of their properties, attributes, and other information. These classes are organized into an inheritance hierarchy supporting object associations and grouped by areas of interest, such as networking, applications, and systems. Each area of interest represents a schema, which is a subset of the information that is available about the managed environment.

For more information, see the [Schema overview](configuration-manager-schema-overview).

For information about accessing the SMS Provider using WMI, see [WMI Configuration Manager Provider Fundamentals](wmi-configuration-manager-provider-fundamentals)

## WMI and .NET Framework applications

Configuration Manager has a .NET Framework library, Microsoft.ConfigurationManager.ManagementProvider, that wraps WMI and allows you to write managed applications.

For information about accessing the SMS Provider by using .NET Framework, see [.NET Managed Configuration Manager Provider Fundamentals](managed-sms-provider-fundamentals-in-configuration-manager)

You can also use the .NET Framework WMI management namespace System.Management, but this does not provide any Configuration Manager-specific interfaces. It is, however, the recommended way to use managed code on a Configuration Manager client.