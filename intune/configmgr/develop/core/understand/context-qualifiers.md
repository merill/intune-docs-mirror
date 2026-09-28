---
layout: Conceptual
title: Context Qualifiers - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/context-qualifiers
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
description: Use context qualifiers when you connect to the SMS Provider and with individual SMS Provider objects.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 572c173c-d830-6413-4d25-25ddbaa76f0b
document_version_independent_id: c3bf7d60-3cfe-853f-8de5-b2608afe07d3
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/understand/context-qualifiers.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/understand/context-qualifiers
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/understand/context-qualifiers.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/97159432-14a9-4307-a469-d2f2c75f0e33
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/50565c62-5f6b-4687-be38-323113c72c2e
platformId: 56fd42d0-6730-eb70-4019-2d1c14f153ef
---

# Context Qualifiers - Configuration Manager | Microsoft Learn

Context objects are used, in Configuration Manager, to provide additional information to the SMS Provider. Typically, you use context qualifiers to give the SMS Provider contextual information, such as your application's name. You can use context qualifiers when you connect to the SMS Provider and with individual SMS Provider objects.

## Managed Code

When using the managed SMS Provider libraries, you use the [ConnectionManagerBase.Context](/en-us/previous-versions/system-center/developer/cc147087%28v=msdn.10%29) property to specify context qualifiers. For more information, see [How to Add a Configuration Manager Context Qualifier by Using Managed Code](how-to-add-a-configuration-manager-context-qualifier-by-using-managed-code).

## VBScript

When using VBScript, you use the [SWBemNamedValue](/en-us/windows/win32/wmisdk/swbemnamedvalue) interface set to specify context qualifiers as a collection of named value objects. For more information, see [How to Add a Configuration Manager Context Qualifier by Using WMI](how-to-add-a-configuration-manager-context-qualifier-by-using-wmi).

## Context Qualifiers

The following table contains the context qualifiers (named values) that are used by the SMS Provider. Most qualifiers, like `SessionHandle`, are only used with specific functional areas of the SMS Provider; but `LocaleID`, `MachineName`, and `ApplicationName` are for your application's use.

| Context qualifier | Description |
| --- | --- |
| `ApplicationName` | Identifies the application that made the call. |
| `ContextHandle` | Identifies where the SMS Provider has stored your cached context qualifiers. |
| `InstanceCount` | Limits the number of instances returned from [ExecQuery](/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-execquery) and [CreateInstanceEnum](/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum). |
| `LimitToCollectionIDs` | Limits the results of a resource query to the members of the named collections. |
| `LocaleID` | Identifies the code page to use. |
| `MachineName` | Identifies which computer is running the application. |
| `QueryQualifiers` | Returns the SecurityVerbs bit flags when you execute queries against secured objects. |
| `SessionHandle` | Identifies your application's copy of the site control file to Configuration Manager. |

## ApplicationName

The `ApplicationName` context qualifier is a string value that identifies the name of the application that made the call. You should specify `ApplicationName` for your application because it is used for auditing. If you do not supply the name of your application, a value of Unknown is used. You must supply the `ApplicationName` value when you call any of the raise status message methods, such as [SMS_StatusMessage](../../reference/core/servers/manage/sms_statusmessage-server-wmi-class)::[RaiseErrorStatusMsg](../../reference/core/servers/manage/raiseerrorstatusmsg-method-in-class-sms_statusmessage), or the call will fail.

## ContextHandle

The `ContextHandle` context qualifier is a string value that identifies where the SMS Provider has stored your cached context qualifiers. The managed SMS Provider manages data transfer. When using VBScript, You can use the following steps to reduce the amount of data that is passed over the network.

1. Create [SWBemNamedValue](/en-us/windows/win32/wmisdk/swbemnamedvalue) value set.
2. Add your qualifiers to the context object. For more information, see [How to Add a Configuration Manager Context Qualifier by Using WMI](how-to-add-a-configuration-manager-context-qualifier-by-using-wmi).
3. Call the [GetContextHandle](../../reference/misc/getcontexthandle-method-in-class-sms_contextmethods) method to cache your qualifiers on the server. The SMS Provider caches the context object that you pass as a parameter of [ExecMethod](/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-execmethod) when you call [GetContextHandle](../../reference/misc/getcontexthandle-method-in-class-sms_contextmethods).
4. Remove all the qualifiers from your context object.
5. Add the `ContextHandle` qualifier and value to your context object.
6. Pass the context object on all calls to [IWbemServices](/en-us/windows/win32/api/wbemcli/nn-wbemcli-iwbemservices).

    You must call the [ClearContextHandle](../../reference/misc/clearcontexthandle-method-in-class-sms_contextmethods) method to remove your cached qualifiers before you exit your application. You can create as many `ContextHandle` values as you want, with each providing varying information for your application.

Note

After you cache your context qualifiers, you can override your cached values by adding the same context qualifiers, with different values, to your context object.

## InstanceCount

The `InstanceCount` context qualifier is an integer value that is used to limit the number of instances returned from the [ExecQuery](/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-execquery) and [CreateInstanceEnum](/en-us/windows/win32/api/wbemcli/nf-wbemcli-iwbemservices-createinstanceenum) methods. You set `InstanceCount` equal to the maximum number of instances that you want returned from the query or enumerator. For example, setting `InstanceCount` to 10 returns, at most, 10 instances.

## LimitToCollectionIDs

The `LimitToCollectionIDs` context qualifier is a string array that contains a list of `CollectionID` values. Currently, you can specify only one `CollectionID` value. You use this qualifier to limit the results of a resource query to the members of the named collection. A resource query is a query that includes classes derived from [SMS_Resource](../../reference/core/clients/manage/sms_resource-server-wmi-class) or [SMS_Group](../../reference/core/clients/manage/sms_group-server-wmi-class).

The user must have instance read resource permissions for the collection to which the resource belongs. You must use collection limiting when the user does not have class read resource rights for collections; otherwise, no data is returned. For SMS 2.0 with Service Pack 1 and later versions, this restriction applies only to classes derived from SMS\_Group.

You cannot use this qualifier when querying collections.

## LocaleID

The `LocaleID` context qualifier is a string value that accepts either a hexadecimal value or a decimal value in the form MS\x, where x is the locale ID. For example, you can enter the English `LocaleID` value as ms\0x0409 or ms\1033. The SMS Provider only accepts `LocaleID` values that use the Microsoft format. You can find a list of `locale IDs` at [Locale IDs Assigned by Microsoft](/en-us/openspecs/windows_protocols/ms-lcid).

If you need the locale for non-U.S. installations, you can get it from the [SMS_Identification Server WMI Class](../../reference/core/servers/configure/sms_identification-server-wmi-class)`LocaleID` property.

## MachineName

The `MachineName` context qualifier is a string value that identifies which computer is running the application. You should specify `MachineName` for your application because it is used for auditing. If you do not supply the computer name, a value of Unknown is used. You must supply the MachineName value when you call any of the raise status message methods, such as [SMS_StatusMessage](../../reference/core/servers/manage/sms_statusmessage-server-wmi-class)::[RaiseRawStatusMsg](../../reference/core/servers/manage/raiserawstatusmsg-method-in-class-sms_statusmessage), or the call will fail.

## QueryQualifiers

The `QueryQualifiers` context qualifier is a Boolean value that is used to return the SecurityVerbs bit flags when you execute queries against secured objects, such as [SMS_Site](../../reference/core/servers/configure/sms_site-server-wmi-class) or [SMS_Package](../../reference/core/servers/configure/sms_package-server-wmi-class). Note that using `QueryQualifiers` when querying unsecured objects generates an error. By default, SecurityVerbs flags are not returned with the query. You must create this qualifier and set its value to `true` if you want the flags returned. Not creating `QueryQualifiers` is the same as setting its value to `false`.

## SessionHandle

The `SessionHandle` context qualifier is a string value that is returned as an out parameter of the GetSessionHandle method. The string is a unique GUID that identifies your application's copy of the site control file to Configuration Manager. You should use this mechanism to modify the site control file and reduce data collisions with other applications that are modifying the site control file at the same time. If you do not supply a `SessionHandle` value, your application modifies the global copy of the site control file, which has no protection from applications overwriting each other's data.

Note

If you are using the managed SMS Provider, site control file session management is managed for you.