---
layout: Conceptual
title: Reporting Status Messages from Clients - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/servers/manage/about-reporting-status-messages-from-configuration-manager-clients
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
description: You can raise Configuration Manager client status messages in the Windows event log by using a compiled Managed Object Format (MOF) file on client computers.
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: concept-article
ms.collection: tier3
locale: en-us
document_id: ede8752b-e513-4542-ff32-b051b19eeea0
document_version_independent_id: 76fdac42-6e24-025d-bf65-51ca7df4fd8f
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/core/servers/manage/about-reporting-status-messages-from-configuration-manager-clients.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/core/servers/manage/about-reporting-status-messages-from-configuration-manager-clients
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/core/servers/manage/about-reporting-status-messages-from-configuration-manager-clients.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/2bb407c5-c939-4f7a-9174-27da19279675
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/6eda2a8b-e231-4335-b766-c055ea6025a6
platformId: 0f2bcec7-5327-3780-f2b0-12886cf35b19
---

# Reporting Status Messages from Clients - Configuration Manager | Microsoft Learn

You can raise Configuration Manager client status messages in the Windows event log by using a compiled Managed Object Format (MOF) file on client computers. This can be useful for administrators who are managing servers with System Center Operations Manager. A Configuration Manager status message that is raised by the Configuration Manager client can be caught by the Operations Manager agent on the same computer, which in turn raises an Operations Manager alert for the Configuration Manager status message.

The following example MOF file shows how to raise Configuration Manager program status messages:

```
#pragma namespace("\\\\.\\root\\ccm\\policy\\machine\\requestedconfig")
instance of CCM_EventForwarder_Configuration
{
    InstanceID = "SmsSoftwareDistribution.EventLog";
    Name = "SmsEventLogForwarder";
    PolicyID = "SomePolicyID";
    PolicyInstanceID = "SomePolicyInstance";
    PolicyRuleID = "SomeRuleID";
    PolicySource = "Local";
    PolicyVersion = "1";
        QueryList           = {
                            "SELECT * FROM SoftDistProgramStartedEvent",
                            "SELECT * FROM SoftDistProgramCompletedSuccessfullyEvent",
                            "SELECT * FROM SoftDistProgramCompletedSuccessfulMIFEvent",
                            "SELECT * FROM SoftDistProgramErrorEvent",
                            "SELECT * FROM SoftDistProgramErrorMIFEvent",
                            "SELECT * FROM SoftDistProgramExceededTime",
                            "SELECT * FROM SoftDistProgramPrelimSuccessEvent",
                            "SELECT * FROM SoftDistProgramUnexpectedRebootEvent",
                            "SELECT * FROM SoftDistWarningProgramErrorEvent"
                            };
};
```