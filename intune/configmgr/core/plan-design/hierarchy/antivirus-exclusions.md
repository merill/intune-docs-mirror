---
layout: Conceptual
title: Antivirus exclusions - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/hierarchy/antivirus-exclusions
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
description: Learn about recommended antivirus exclusions for use when troubleshooting possible issues.
ms.date: 2019-10-31T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ROBOTS: NOINDEX
ms.collection: tier3
locale: en-us
document_id: 5b3ecde4-8b90-2e50-0ab2-c06ee7be85af
document_version_independent_id: cdaf2bd1-330c-db25-b702-a620397cdb2a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/hierarchy/antivirus-exclusions.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/hierarchy/antivirus-exclusions
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/hierarchy/antivirus-exclusions.md
platformId: 4e05c8e4-7992-5782-1a7b-edd5a45448c8
---

# Antivirus exclusions - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article contains recommendations that may help an administrator determine the cause of potential instability on a computer that is running a supported version of Configuration Manager site servers, site systems, and clients when it's used together with antivirus software.

Important

- We recommend that you temporarily apply these procedures to evaluate a system. If your system performance or stability is improved by the recommendations that are made in this article, contact your antivirus software vendor for instructions or for an updated version of the antivirus software.
- This article contains information that shows how to help lower security settings or how to temporarily turn off security features on a computer. You can make these changes to understand the nature of a specific problem. Before you make these changes, we recommend that you evaluate the risks that are associated with implementing this workaround in your particular environment.

## Possible symptoms

Antivirus real-time protection can cause many problems on Configuration Manager site servers, site systems, and clients.

The following is a non-comprehensive list of possible symptoms:

- Remote site system components aren't installed. SiteComp.log, Distmgr.log, hman.log, or other Configuration Manager log files may contain errors such as error 80070005.
- The Configuration Manager client can't be installed by using Client Push.
- Client inventory information is inaccurate, missing, or out-of-date.
- Backlogs occur in the *Install\_Directory*\Program Files\Microsoft Configuration Manager\Inboxes folders.
- Software Center is not populated by deployed software on client systems, or doesn't start. Also, the CCMRepair.log file may contain errors that resemble the following example:

> 
> Database verification failed with result: 0x80004005 but DB: C:\Windows\CCM\filename.sdf could be opened, skipping DB repair.
- Software that is deployed to clients can't be installed.
- Compliance data for software deployments is inaccurate.

## Exclusions

To prevent such problems, we recommend that you add the following real-time protection exclusions:

### Default Installation Folders

| Folder | Path |
| --- | --- |
| *ConfigMgr Installation Folder* | %ProgramFiles%\Microsoft Configuration Manager |
| *MP Installation Folder* | %ProgramFiles%\SMS\_CCM |
| *Client Installation Folder* | %Windir%\CCM |

### Folder exclusions for site servers

- *ConfigMgr Installation Folder*\Inboxes
- *ConfigMgr Installation Folder*\Logs
- *ConfigMgr Installation Folder*\EasySetupPayload

### Folder exclusions for site systems

- Management points
    - *MP installation folder*\ServiceData
    - Either of the following:
        - *ConfigMgr installation folder*\MP\OUTBOXES
        - *Installation drive*\SMS\MP\OUTBOXES
- Distribution points
    - *Client installation folder*\ServiceData
    - *ContentLib\_Drive*\SMS\_DP$
    - *ContentLib\_Drive*\SMSPKG*Drive\_Letter*$
    - *ContentLib\_Drive*\SMSPKG
    - *ContentLib\_Drive*\SMSPKGSIG
    - *ContentLib\_Drive*\SMSSIG$
- Site database servers
    - [How to choose antivirus software to run on computers that are running SQL Server](https://support.microsoft.com/en-us/help/309422)

### Folder exclusions for clients

- *Client Installation Folder*\\*.sdf
- *Client Installation Folder*\ServiceData
- C:\Windows\CCMCache
- C:\Windows\CCMSetup
- *Client Installation Folder*\Logs

### File exclusions for MPs

- POL00000.pol in
    - *MP Installation Folder*\PolReqStaging

### Process exclusions

Process exclusions are necessary only if aggressive antivirus programs consider Configuration Manager program files (.exe files) to be high-risk processes.

- *ConfigMgr Installation Folder*\bin\64\Smsexec.exe
- Either of the following processes:
    - *Client Installation Folder*\Ccmexec.exe
    - *MP Installation Folder*\Ccmexec.exe
- *Client Installation Folder*\CmRcService.exe (client-side)
- *ConfigMgr Installation Folder*\bin\64\Sitecomp.exe
- *ConfigMgr Installation Folder*\bin\64\Smswriter.exe
- *ConfigMgr Installation Folder*\bin\64\Smssqlbkup.exe, or SMS\_*SQLFQDN*\bin\x64\Smssqlbkup.exe
- *ConfigMgr Installation Folder*\bin\64\Cmupdate.exe
- *Client Installation Folder*\Ccmrepair.exe (client-side)
- %*windir*%\CCMSetup\Ccmsetup.exe (client-side)