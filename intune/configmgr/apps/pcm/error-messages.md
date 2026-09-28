---
layout: Conceptual
title: Error messages - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/apps/pcm/error-messages
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
description: Learn about the error messages from Package Conversion Manager.
ms.date: 2018-08-24T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: c1131b2b-ae1b-e1f4-667c-1e728ceaee64
document_version_independent_id: 50f70dd1-3130-1e03-85ca-4f3a386deb34
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/apps/pcm/error-messages.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/apps/pcm/error-messages
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/apps/pcm/error-messages.md
cmProducts: []
platformId: 3101158c-1061-9250-ad07-ef3ecf433acb
---

# Error messages - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article describes the error messages that Package Conversion Manager displays. It also includes the possible causes of the error, and methods to correct the error. Package Conversion Manager logs error messages in **PCMTrace.log**. For more information, including how to control the verbosity level, see [Log files](troubleshoot-pcm#log-files).

#### Application creation failed with the following exception

The specified exception occurred during the submission of the application object to the Configuration Manager server.

Check your permissions in Configuration Manager, validate your connectivity, and then retry. If those actions don't fix the problem, examine the **PCMtrace.log** file (verbosity level 4) and **SMSProv.log**.

#### Conversion Error – APPLIES TO A PACKAGE TRANSFORM STATUS

A general exception occurred during the conversion of the package. Look in the **PCMtrace.log** file (verbosity level 4).

Check the user permissions for the network share (package data source), validate your connectivity, and then retry. If those actions don't fix the problem, examine the **PCMtrace.log** file (verbosity level 4).

#### Did not find a converted package and its resultant application in the workflow outputs

The application (converted package/program) was deleted.

Modify the dependent package/program to ensure that the dependent package/program exists.

#### Objects were not created successfully

There are several possible causes.

Check your permissions in Configuration Manager, validate your connectivity, and then retry. If those actions don't fix the problem, examine the **PCMtrace.log** file (verbosity level 4) and the **SMSProv.log** file.

#### Please close the wizard and resolve any issues with the selected package. See PCMTrace.Log for more details

There are several possible causes.

Check your permissions in Configuration Manager, validate your connectivity, and then retry. If those actions don't fix the problem, examine the **PCMtrace.log** file (verbosity level 4) and the **SMSProv.log** file.

#### Some Deployment Types are missing Detection Methods. All Deployment Types must have Detection Methods

Detection methods are missing from the program.

Add one or more detection methods during the **Fix and Convert** process.

#### There was an error preparing the package for conversion

There are several possible causes.

Check your permissions in Configuration Manager, validate your connectivity, and then retry. If those actions don't fix the problem, examine the **PCMtrace.log** file (verbosity level 4) and the **SMSProv.log** file.