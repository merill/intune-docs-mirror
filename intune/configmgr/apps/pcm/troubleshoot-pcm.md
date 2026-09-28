---
layout: Conceptual
title: Troubleshoot Package Conversion Manager - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/pcm/troubleshoot-pcm
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
description: Learn how to troubleshoot problems with the Package Conversion Manager in Configuration Manager.
ms.date: 2018-08-24T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: troubleshooting
ms.collection: tier3
locale: en-us
document_id: 729c558a-b206-60b6-1e0d-9834506ba1fe
document_version_independent_id: 1ffd10fe-cc24-5339-ddc5-2ffe0e9d035e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/pcm/troubleshoot-pcm.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/pcm/troubleshoot-pcm
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/pcm/troubleshoot-pcm.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/540ac133-a371-4dbb-8f94-28d6cc77a70b
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/60bfc045-f127-4841-9d00-ea35495a5800
platformId: a7be345d-809a-1103-b899-d931fcc5d62a
---

# Troubleshoot Package Conversion Manager - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Use the information in this article to help you troubleshoot problems when using Package Conversion Manager.

## SMS Provider

Package Conversion Manager uses the SMS Provider. For more information, see [Plan for the SMS Provider](../../core/plan-design/hierarchy/plan-for-the-sms-provider).

If the SMS Provider isn't working properly, the Configuration Manager console including the Package Conversion Manager doesn't work.

## Package readiness

Before converting a package to an application, analyze the package using the Package Conversion Manager **Analyze** function. After the analysis, add the **Readiness** column in the **Packages** node of the Configuration Manager console. The list of packages displays one of the following readiness states of the analyzed package:

- **Automatic**: The package can be directly converted using the **Convert** function.

    Note

    An automatic conversion doesn't convert WQL queries into application requirements. Use the **Fix and Convert** process to convert these queries.
- **Manual**: The package needs some additions or changes before you can convert it using the **Fix and Convert** function.
- **Not Applicable**: The package isn't suitable for conversion. Either correct any problems with the package, or continue to deploy it as a package.
- **Error**: The package contains errors. Manually correct these errors before you can analyze and convert it.

The details pane of the **Packages** node in the Configuration Manager console shows any readiness issues. Select a package, and then select the **Summary** tab in the details pane.

## Log files

### Enable logging

When you enable logging for Package Conversion Manager, it logs all of its actions, exceptions, and errors.

To enable logging for this component in the Configuration Manager, modify **Microsoft.ConfigurationManagement.exe.Config**. By default, this configuration file is located in the following path: `C:\Program Files (x86)\Microsoft Endpoint Manager\AdminConsole\bin\Microsoft.ConfigurationManagement.exe.config`

Important

Starting in version 1910, this path changed to use the `Microsoft Endpoint Manager` folder. Make sure you don't use an older version of the file that might exist in another folder.

Insert the following **switches** and **trace** XML elements in the **system.diagnostics** element after the last **sources** element:

```XML
</sources>

    <switches>
      <add name="PcmLogging" value="3"/>
    </switches>
    <trace autoflush="true" indentsize="4">
      <listeners>
        <add name="PcmTraceListener" type="Microsoft.ConfigurationManagement.UserCentric.Logging.RolloverLogTraceListener, Microsoft.ConfigurationManagement.UserCentric.Logging" initializeData="%UserProfile%\AppData\Local\Temp\PcmTrace.log"/>
      </listeners>
    </trace>

</system.diagnostics>
```

This sample uses the file **PCMTrace.log**. This log is on the computer running the Configuration Manager console in the following path: `%UserProfile%\AppData\Local\Temp`

To configure the level of detail, change the **PcmLogging** trace switch setting. Set the this value to four levels of detail, from least detailed (`1`) to most detailed (`4`).

### SMSProv.log

In some situations, information relevant to troubleshooting the package conversion process is in the **SMSProv.log** file. This file captures information from the Configuration Manager SMS Provider.

By default, this log file is located on the Configuration Manager site server at the following path: `C:\Program Files\Microsoft Configuration Manager\Logs`

If you see one of the following error messages, the **SMSProv.log** file may contain relevant troubleshooting information:

- `The SMS Provider reported an error`
- `Generic Failure`

These error messages typically indicate that an error occurred on the site server, and that the error information wasn't sent to the Configuration Manager console.

For more information, see [Technical reference for Package Conversion Manager error messages](error-messages).

## Changing package attributes after analysis

After you analyze a package and it has a readiness state of **Automatic** or **Manual**, the conversion process might fail if you change any of the relevant attributes.

For example, you analyze a package and its readiness state is **Automatic**. Then you add another program to the package. The package conversion might fail.

If you need to make changes to a package after analysis, rerun analysis before conversion.