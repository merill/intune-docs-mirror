---
layout: Conceptual
title: OS Configuration Item Example 1 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/operating-system-configuration-item-example-1
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
description: Example 1 for Operating System Configuration Item
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 71c9a4b7-73f5-c677-b137-20cef740448f
document_version_independent_id: ac992e47-3ad4-7aeb-744f-42469c02ed50
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/compliance/operating-system-configuration-item-example-1.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/compliance/operating-system-configuration-item-example-1
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/compliance/operating-system-configuration-item-example-1.md
cmProducts: []
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 40326d16-c9c3-0de5-6ed6-f2135a4cb2f2
---

# OS Configuration Item Example 1 - Configuration Manager | Microsoft Learn

In Configuration Manager, the following Operating System Configuration Item Schema example checks for Windows XP SP2.

## Operating System Configuration Item Example

```xml
<?xml version="1.0" encoding="utf-8"?>

<!--
The root element for any DCM Digest document is the DesiredConfigurationDigest element referenced below.  All of the XML elements/attributes are defined in the DCM Digest schema definition namespace.
-->

<DesiredConfigurationDigest xmlns="http://schemas.microsoft.com/SystemsCenterConfigurationManager/2006/03/24/DesiredConfiguration">

<!--
Every DCM Digest must contain exactly one configuration item. Specifically one of the following: an application, operatingsystem, general or baseline.
This digest defines an operating system configuration item.

The unique identify of the configuration item is the combination of the attributes AuthoringScopeID, LogicalName and Version.
Each attribute is part of the unique identity of the configuration item; the actual identity is AuthoringScopeID + LogicalName + Version.

AuthoringScopeID (string) - This attribute corresponds to the author's namespace or identity.
LogicalName (string) - This attribute identifies the configuration item within the authoring scope.
Version (string) - This attribute specifies the version of the configuration item.
-->

    <OperatingSystem AuthoringScopeId="ScopeId_F348CC96-19CA-4F5D-9D4F-D1451B5BEB1E" LogicalName="OperatingSystem_c745714d-1063-4dec-8447-a9414ec030e7" Version="1">
        <Annotation>
            <DisplayName Text="My WinXp SP2 Operating System CI" />
            <Description Text="Simple Operating System detection." />
        </Annotation>

<!--
There are no parts defined for this configuration item.
Parts are physical things with fixed lists of properties.Mandatory element tag for the section of the DCM Digest used to define Object parts, including:
File
Folder
Assembly (registered in the Global Assembly Cache (GAC))
RegistryKey
-->

        <Parts>
            <ParentReferences />
        </Parts>

<!--
There are no settings defined for this configuration item.
Settings are configurable name/value pairs which influence the behavior of hardware and software. DCM can discover settings using any of the supported providers, including:
Registry
WMI (WQL query)
Microsoft SQL Server (SQL query)
Active Directory (LDAP)
XML (XPath query)
IIS Metabase
Script (JScript/VBScript/PowerShell)
-->

        <Settings>

<!--
RootComplexSetting is the root container for all settings. Every configuration item has one of these, even if there are no actual settings defined.
-->
            <RootComplexSetting />

        </Settings>

<!--
OperatingSystem identifies how to determine whether or not this operating system exists on the system. If it does exist (is discovered), then the system discovers the parts and settings. Finally, the system evaluates the rules(if any) defined against the part property values and the setting values.
-->
        <OperatingSystemDiscoveryInfo BuildVersion="2600" MajorVersion="5" MinorVersion="10" ServicePackMajorVersion="2" ServicePackMinorVersion="0" />
    </OperatingSystem>
</DesiredConfigurationDigest>
```