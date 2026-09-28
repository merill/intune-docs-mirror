---
layout: Conceptual
title: Conditional Actions - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/console/conditional-actions
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
description: Learn how to display Configuration Manager actions by specified conditions such as regular expressions, method calls, or security permissions.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: f9437296-5065-5cc8-cbb6-99e98251324c
document_version_independent_id: 526e3371-462c-b8b7-f174-5c77bc85dda2
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/console/conditional-actions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/console/conditional-actions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/console/conditional-actions.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/8b896464-3b7d-4e1f-84b0-9bb45aeb5f64
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/12ed19f9-ebdf-4c8a-8bcd-7a681836774d
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/b1d2d671-9549-46e8-918c-24349120dbf5
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3a764584-4f97-452b-8f1d-36f19b12f6ae
platformId: e025a64e-29d4-af1b-feff-29b6ac063bbe
---

# Conditional Actions - Configuration Manager | Microsoft Learn

Configuration Manager actions can be displayed according to specified conditions. The conditions are defined by the following:

- Regular expressions
- Method calls
- Security permissions

## Regular Expressions

Regular expressions allow you to apply string-based search patterns. The following elements specify a regular expression for an action:

| Element | Description |
| --- | --- |
| `MatchPattern` | Specifies the pattern to search for. |
| `MatchValueToTest` | Specifies the value to compare against. The value following `##Sub` is a property on the selected object. The property must not be lazy and must exist on the select object. |

The following action displays a dialog box whenever the specified pattern (MS\_ASYNC\_RAS) matches the selected object's `AddressType` property:

```
<ActionDescription ActionVerb="Properties" Class="ShowDialog">  <ShowOn>  <string>DefaultContextualTab</string> <!-- Show on Ribbon -->           <string>ContextMenu</string> <!-- Show on Context Menu -->   </ShowOn>  <MatchPattern>MS_ASYNC_RAS</MatchPattern>
 <MatchValueToTest>##SUB:AddressType##</MatchValueToTest>
 <DialogId>AsyncRasSenderAddress</DialogId></ActionDescription>
```

## Method Calls

An action can be shown depending on the result of a method call. The `ActionDescription` child element `ActionStateAssembly` defines the assembly, type, and method to be called. If the method returns `true`, the action is shown; if the method returns `false`, the action is hidden.

The following XML calls a method named `EnableDecrementPriorityMenu` in the assembly AdminUI.Addresses.dll:

```
<ActionDescription>
 <ShowOn>
    <string>DefaultContextualTab</string> <!-- Show on Ribbon -->         <string>ContextMenu</string><!-- Show on Context Menu --> </ShowOn> <ActionStateAssembly>
  <Assembly>AdminUI.Addresses.dll</Assembly>   <Type>Microsoft.ConfigurationManagement.AdminConsole.Addresses.AddressUtilityClass</Type>
  <Method>EnableDecrementPriorityMenu</Method> </ActionStateAssembly>
</ActionDescription>
```

The method is implemented in a .NET Framework assembly with the following signature:

`public static bool EnableDecrementPriority(object sender, ScopeNode scopeNode, ActionDescription action, ResultObjectBase resultObject)`

For more information about calling methods in a .NET Framework assembly, see [Configuration Manager AssemblyType Action](assemblytype-action).

## Security Permissions

You can restrict the availability of an action by applying security restrictions to the selected object or object class.

### Object Instance Permissions

You can restrict the availability of an action by applying required permissions to the selected object. In the following XML example, the following elements specify the instance permissions for the selected object:

| Element | Description |
| --- | --- |
| `InstancePermissions` | The parent element to the list of instance permissions. |
| `SecurityFlagsDetailDescription` | The security flags that must be set for the action to work. |

In the following XML example, the `Delete` action for a selected object is available only if the user has modify permissions:

```
<ActionDescription ActionVerb="Delete" Class="Default" SelectionMode="Both" InstanceDependsOn="SMS_Site">
<ShowOn> <string>DefaultContextualTab</string> <!-- Show on Ribbon -->    <string>ContextMenu</string> <!-- Show on Context Menu --></ShowOn><InstancePermissions><SecurityFlagsDetailDescription BitName="Modify" BitValue="2" DependsOn="1" /></InstancePermissions>
</ActionDescription>
```

### Object Class Permissions

You can use the `ClassPermissions` element to set the object class permissions required for an action. [ActionSecurityDescription](/en-us/previous-versions/system-center/developer/cc147257%28v=msdn.10%29) describes the object class and the required permissions for that object class. The following XML example describes the permissions required for SMS collections:

```
<ClassPermissions> <ActionSecurityDescription ClassObject="SMS_Collection" RequiredPermissions="1280" />
</ClassPermissions>
```

### Permission Values

The permission values for the [RequiredPermissions](/en-us/previous-versions/system-center/developer/cc146816%28v=msdn.10%29) attribute are the same as for the [SecurityFlagsDetailDescription](/en-us/previous-versions/system-center/developer/cc147286%28v=msdn.10%29) class and are as follows:

| Permission | Values | Depends on |
| --- | --- | --- |
| Read | 1 | None |
| Modify | 2 | 1 |
| Delete | 4 | 1 |
| Distribute | 8 | 1 |
| CreateChild | 16 | 1 |
| RemoteControl | 32 | None |
| Advertise | 64 | 1 |
| ModifyResource | 128 | 1 |
| Administer | 256 | 7 |
| DeleteResource | 512 | 1 |
| Create | 1024 | None |
| ViewCollectedFiles | 2048 | 1 |
| ReadResource | 4096 | 1 |
| Delegate | 8192 | None |
| Meter | 16384 | 1 |
| ManageSqlCommand | 32768 | 1 |
| ManageStatusFilter | 65536 | 1 |
| ManageFolder | 131072 | 1 |
| NetworkAccess | 262144 | 1 |
| ImportMachineEntry | 524288 | 1 |
| CreateMediaCertificate | 1048576 | 1 |
| ModifyCollectionSetting | 2097152 | 1 |
| ManageOsdCertificate | 4194304 | 1 |