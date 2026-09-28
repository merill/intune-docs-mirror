---
layout: Conceptual
title: WMI Provider Fundamentals - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/wmi-configuration-manager-provider-fundamentals
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
description: Windows Script Host-based applications and scripts work in Windows Management Instrumentation (WMI) through the WMI Object Model, which defines the programming interface to WMI.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 767f8b72-9a93-1c1a-3dda-514fd231630b
document_version_independent_id: c5e09288-f330-a195-1f98-2f6423a686d8
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/wmi-configuration-manager-provider-fundamentals.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/wmi-configuration-manager-provider-fundamentals
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/wmi-configuration-manager-provider-fundamentals.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3a4bfd6d-e566-e7b9-208d-a6fb03fe27ea
---

# WMI Provider Fundamentals - Configuration Manager | Microsoft Learn

Windows Script Host-based applications and scripts work in Windows Management Instrumentation (WMI) through the WMI Object Model, which defines the programming interface to WMI. A number of WMI object types are used when manipulating Configuration Manager objects. For more information about the WMI Object Model, see [Windows Management Instrumentation](/en-us/windows/win32/wmisdk/wmi-start-page).

In simple Configuration Manager scripts, you use the following WMI object types:

- `SWbemLocator`
- `SWbemServices`
- `SWbemObjectSet`
- `SWbemObject`

Note

Understanding WMI Query Language (WQL) queries is very important for identifying which Configuration Manager objects you want to read. WQL statements allow you to retrieve Configuration Manager objects that are based on SQL-like queries. For example, the following WQL statement is used to identify all Windows Server 2003 systems:

`SELECT * FROM SMS_FullCollectionMembership WHERE CollectionID='SMS000FS'`

For more information about using VBScript and WMI, see [Objects overview](configuration-manager-objects-overview).

## SWbemLocator

The [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices)object is used to create an authenticated connection to the SMS Provider. You use the [ConnectServer](/en-us/windows/win32/wmisdk/swbemlocator-connectserver) method to make the connection to the SMS Provider. This method is particularly useful if you need to pass user credentials to a remote Configuration Manager server during connection. You can also use the Windows Script Host [GetObject](/en-us/previous-versions/windows/internet-explorer/ie-developer/windows-scripting/8ywk619w%28v=vs.84%29) method to create an authenticated connection. The type of object that is returned by `GetObject` depends on the parameters that are passed to it. See [How to Connect to a Configuration Manager Provider Using Managed Code](how-to-connect-to-an-sms-provider-by-using-managed-code) and [How to Connect to a Configuration Manager Provider Using WMI](how-to-connect-to-an-sms-provider-in-configuration-manager-by-using-wmi) for examples that show how to use either `SWbemLocator` or `GetObject` in your connection script.

## SWbemServices

The [SWbemServices](/en-us/windows/win32/wmisdk/swbemservices) object represents an authenticated connection to a SMS Provider, and it is the object that you use to retrieve Configuration Manager objects. You receive an `SWbemServices` object as the return value of the `SWbemLocator` function `ConnectServer` or, alternatively, as the return value when the `GetObject` method is used to connect to the SMS Provider. `SWbemServices` has several methods, but you use only the [Get](/en-us/windows/win32/wmisdk/swbemservices-get), [ExecQuery](/en-us/windows/win32/wmisdk/swbemservices-execquery), and [InstancesOf](/en-us/windows/win32/wmisdk/swbemservices-instancesof) methods for retrieving objects.

`Get` returns a single instance of a Configuration Manager object (`SWbemObject`). `ExecQuery` and `InstancesOf` return Configuration Manager objects in a collection (`SWbemObjectSet`) of Configuration Manager objects.

## SWbemObjectSet

The [SWbemObjectSet](/en-us/windows/win32/wmisdk/swbemobjectset) object represents a collection of Configuration Manager objects. You can use it to enumerate through the collection and read individual instances of the Configuration Manager object (`SWbemObject`) that you are interested in. You typically get a `SWbemObjectSet` object returned to you from the `SWbemServices` retrieval functions.

## SWbemObject

The [SWbemObject](/en-us/windows/win32/wmisdk/swbemobject) object allows you to access the properties and other information for a Configuration Manager object.