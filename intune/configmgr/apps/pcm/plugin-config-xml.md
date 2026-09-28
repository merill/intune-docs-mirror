---
layout: Conceptual
title: Plug-in configuration XML - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/pcm/plugin-config-xml
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
description: Technical reference for the XML elements of the Package Conversion Manager plug-in.
ms.date: 2018-08-24T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: reference
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 7ab2dfce-c7f3-82a5-4448-a7c582f0d98b
document_version_independent_id: b4c8839d-08b9-d3c1-7784-2d62d82fe0a7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/pcm/plugin-config-xml.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/pcm/plugin-config-xml
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/pcm/plugin-config-xml.md
platformId: 6bad0242-ad0b-daaf-8365-084356345549
---

# Plug-in configuration XML - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article describes the XML elements in the Configuration Manager configuration file (Microsoft.ConfigurationManagement.exe.config) that control the operation of the Package Conversion Manager plug-in. For more information on how to use this plug-in, see [How to use the Package Conversion Manager plug-in](how-to-use-plug-in).

## XML configuration elements

The following table describes the XML elements in the Configuration Manager configuration file that relate to the Package Conversion Manager plug-in.

| Element | Type | Description |
| --- | --- | --- |
| **PcmPlugIn** | String | The name of the script or executable to use as the Package Conversion Manager plug-in. |
| **PcmPlugInTimeoutMilliseconds** | Integer | The maximum amount of time, in milliseconds, to wait for the Package Conversion Manager plug-in script or executable to complete the processing of a package. |
| **PcmPluginExitCode** | Integer | The expected exit code from the plug-in process. This value indicates success. All other codes are considered an error. |
| **ForceRequirementsExtraction** | Boolean | Allow automatic conversion to use collection requirements associated with a package. This should only be set to True when working with a Package Conversion Manager plug-in that's designed to make decisions about which requirements to use. |

## Sample configuration XML

This section provides an example of the Package Conversion Manager configuration XML elements in the Configuration Manager configuration file, **Microsoft.ConfigurationManagement.exe.config**. By default, this file is in the following path: `C:\Program Files (x86)\Microsoft Endpoint Manager\AdminConsole\bin\Microsoft.ConfigurationManagement.exe.config`

Important

Starting in version 1910, this path changed to use the `Microsoft Endpoint Manager` folder. Make sure you don't use an older version of the file that might exist in another folder.

In the sample, the elements related to Package Conversion Manager are inside the following element: `Microsoft.ConfigurationManagement.UserCentric.Workflow.Properties.Settings`

```XML
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
...
    </Microsoft.ConfigurationManagement.AdminConsole.Properties.Settings>
    <Microsoft.ConfigurationManagement.UserCentric.Workflow.Properties.Settings>
      <setting name="DecisionVerbosity" serializeAs="String">
        <value>2</value>
      </setting>
      <setting name="PcmPlugIn" serializeAs="String">
        <value>pcmplugin.vbs</value>
      </setting>
      <setting name="PcmPlugInTimeoutMilliseconds" serializeAs="String">
        <value>10000</value>
      </setting>
      <setting name="PcmPluginExitCode" serializeAs="String">
        <value>0</value>
      </setting>
      <setting name="ForceRequirementsExtraction" serializeAs="String">
        <value>True</value >
      </setting>
    </Microsoft.ConfigurationManagement.UserCentric.Workflow.Properties.Settings>
  </applicationSettings>
...
```