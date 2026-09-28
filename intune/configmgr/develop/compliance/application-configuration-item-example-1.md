---
layout: Conceptual
title: Application Configuration Item Example 1 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/application-configuration-item-example-1
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
description: The Application Configuration Item Instance example determines whether the Configuration Manager client is installed on the system by using Microsoft Windows Installer-based detection.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: 8a1066c9-48dc-4cda-be06-745471137974
document_version_independent_id: ebc4bbe1-91cb-4c71-74b3-7a3c47f2ffc1
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/compliance/application-configuration-item-example-1.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/compliance/application-configuration-item-example-1
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/compliance/application-configuration-item-example-1.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 4832d609-4481-07f5-ad14-5712560fe2b2
---

# Application Configuration Item Example 1 - Configuration Manager | Microsoft Learn

The following Application Configuration Item Instance example determines whether the Configuration Manager client is installed on the system by using Microsoft Windows Installer-based detection.

## Application Configuration Item Example

```xml
<?xml version="1.0" encoding="utf-8"?>

<!--
The root element for any DCM Digest document is the DesiredConfigurationDigest element referenced below.  All of the XML elements/attributes are defined in the DCM Digest schema definition namespace.
-->

<DesiredConfigurationDigest xmlns="http://schemas.microsoft.com/SystemsCenterConfigurationManager/2006/03/24/DesiredConfiguration">

<!--
Every DCM Digest must contain exactly one configuration item. Specifically one of the following: an application, operatingsystem, general or baseline.
This digest defines an application configuration item.

The unique identity of the configuration item is the combination of the attributes AuthoringScopeID, LogicalName and Version.
Each attribute is part of the unique identity of the configuration item; the actual identity is AuthoringScopeID + LogicalName + Version.

AuthoringScopeID (string) - This attribute corresponds to the author's namespace or identity.
LogicalName (string) - This attribute identifies the configuration item within the authoring scope.
Version (string) - This attribute specifies the version of the configuration item.
-->

    <Application AuthoringScopeId="ScopeId_F348CC96-19CA-4F5D-9D4F-D1451B5BEB1E" LogicalName="Application_5cb68ff1-a234-41ed-a7d4-14174d8108b7" Version="1" Is64Bit="false">
        <Annotation>
            <DisplayName Text="Configuration Manager Client" />
            <Description Text="Configuration Manager Client (Windows Installer-based detection)" />
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
This application is discovered via Windows Installer-based discovery. If it does exist (is discovered) the system then discovers the parts and settings. Finally, the system evaluates the rules (if any) defined against the part property values and the setting values.
-->

        <MsiDiscoveryInfo IsPerUser="false" ProductCode="{D7D7EE27-817F-481D-865F-F5755FA89E2E}" Version="4.00.5507.0000" />

    </Application>
</DesiredConfigurationDigest>
```