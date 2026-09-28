---
layout: Conceptual
title: Configuration Baseline Example 1 - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/compliance/configuration-baseline-example-1
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
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: article
ms.collection: tier3
description: This Baseline Configuration Item Instance example references an application configuration item that checks whether the Configuration Manager client and Notepad are installed on systems that are running Windows XP SP2.
locale: en-us
document_id: 80dc3090-ecbb-1832-756f-2c8d1c635391
document_version_independent_id: 1f9a679c-9a01-91e6-badd-15c71bb822cf
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/compliance/configuration-baseline-example-1.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/compliance/configuration-baseline-example-1
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/compliance/configuration-baseline-example-1.md
cmProducts: []
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 33137c07-03d8-7088-7c3b-fe53c1a3b41e
---

# Configuration Baseline Example 1 - Configuration Manager | Microsoft Learn

The following Baseline Configuration Item Instance example references an application configuration item that checks whether the Configuration Manager client and Notepad.exe are installed on systems that are running Windows XP SP2.

## Configuration Baseline Example

```xml
<?xml version="1.0" encoding="utf-8"?>

<!--
The root element for any DCM Digest document is the DesiredConfigurationDigest element referenced below.  All of the XML elements/attributes are defined in the DCM Digest schema definition namespace.
-->

<DesiredConfigurationDigest xmlns="http://schemas.microsoft.com/SystemsCenterConfigurationManager/2006/03/24/DesiredConfiguration">

<!--
Every digest must contain exactly one configuration item. Specifically one of the following: an application, operatingsystem, general or baseline.
This is a baseline configuration item.
The baseline configuration item provides a way to group other configuration items (including other baselines) for deployment to clients. Other types of configuration items cannot be directly deployed to clients, they must be referenced within a baseline configuration item, which is then deployed to clients.

The unique identify of the configuration item is the combination of the attributes AuthoringScopeID, LogicalName and Version.
Each attribute is part of the unique identity of the configuration item; the actual identity is AuthoringScopeID + LogicalName + Version.

AuthoringScopeID (string) - This attribute corresponds to the author's namespace or identity.
LogicalName (string) - This attribute identifies the configuration item within the authoring scope.
Version (string) - This attribute specifies the version of the configuration item.
-->

    <Baseline AuthoringScopeId="ScopeId_F348CC96-19CA-4F5D-9D4F-D1451B5BEB1E" LogicalName="Baseline_ab095740-707a-46b6-8408-a72be147514c" Version="1">
        <Annotation>
            <DisplayName Text="Sample Baseline" />
            <Description Text="A baseline that includes the sample CI." />
        </Annotation>

<!--
Only application and general configuration item references can be used in the RequiredItems section.

Below is a reference to an application configuration item that checks to see whether the Configuration Manager 2007 client is installed on the system. The application configuration item can be found in the Application Configuration Item Schema Example 1 (link below)
-->

        <RequiredItems>
            <ApplicationReference AuthoringScopeId="ScopeId_F348CC96-19CA-4F5D-9D4F-D1451B5BEB1E" LogicalName="Application_5cb68ff1-a234-41ed-a7d4-14174d8108b7" Version="1" />
        </RequiredItems>

<!--
Only application configuration item references can appear in ProhibitedItems.
-->

        <ProhibitedItems>
        </ProhibitedItems>

<!--
Only application configuration items can appear in OptionalItems.

Below is a reference to an application configuration item that checks to see whether Notepad.exe is installed on the system. The application configuration item can be found in the Application Configuration Item Schema Example 2 (link below)
-->

        <OptionalItems>
            <ApplicationReference AuthoringScopeId="ScopeId_F348CC96-19CA-4F5D-9D4F-D1451B5BEB1E" LogicalName="Application_171bae6f-5661-4bb8-a703-270b131e4c4c" Version="1" />
        </OptionalItems>

<!--
Only operating system configuration items can appear in OperatingSystems.
At least one of the operating systems in the referenced OperationSystem configuration items must be detected on the targeted computer.

Below is a reference to an operating system configuration item that checks to see whether Windows XP SP2 is installed on the system. The application configuration item can be found in the Operating System Configuration Item Schema Example 1 (link below)
-->

        <OperatingSystems>
            <OperatingSystemReference AuthoringScopeId="ScopeId_F348CC96-19CA-4F5D-9D4F-D1451B5BEB1E" LogicalName="OperatingSystem_8aa19644-7801-411c-a7fa-8e7a33d0d8fe" Version="3" />
        </OperatingSystems>

<!--
Only SoftwareUpdates and SoftwareUpdateBundles can appear in SoftwareUpdates. Software Updates configuration items are created and administered through the Software Updates Management feature in Configuration Manager. The Software Updates configuration items can be referenced in configuration baselines; however, they should not be directly authored via DCM or the DCM Digest.
 -->

        <SoftwareUpdates>
        </SoftwareUpdates>

<!-- Only baseline configuration item references can appear in Baselines.  References to other baselines. -->
        <Baselines>
        </Baselines>

<!--
Only references to content defined as System Definition Model language (SDM) can appear in OtherConfigurationItems.
-->

        <OtherConfigurationItems>
        </OtherConfigurationItems>

    </Baseline>
</DesiredConfigurationDigest>
```