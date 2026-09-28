---
layout: Conceptual
title: Language packs - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/language-packs
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
description: Learn about the language support available in Configuration Manager.
ms.date: 2021-04-05T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: e63ece79-8521-a14a-30a5-83adda51ff5c
document_version_independent_id: b6d978eb-0260-e717-be3b-490602c93480
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/install/language-packs.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/install/language-packs
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/install/language-packs.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
platformId: f7f7c8df-71cd-905a-0565-8e7eb74afe76
---

# Language packs - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article provides technical details about language support in Configuration Manager. Configuration Manager site servers and clients are considered language-neutral. Add support for display languages by installing **server language packs** or **client language packs** at a central administration site and at primary sites. You select the server and client languages to support at a site from the available language pack files during the site installation process.

Install multiple languages at each site. You only need to install the languages that you use.

- Each site supports multiple languages for Configuration Manager consoles.
- Add support for only the client languages that you want to support by installing individual client language packs at each site.

When you install support for a language that matches the following components:

- The display language of a computer: Both the Configuration Manager console and the client user interface that runs on that computer display information in that language.
- The language preference that's in use by the web browser of a computer: Connections to web-based information display in that language. For example, SQL Server Reporting Services.

When you run Configuration Manager setup, it downloads language pack files as part of the prerequisites and redistributable files. You can also use the [setup downloader](setup-downloader) to download these files before you run setup.

## Server languages

Use the following table to map a locale ID to a language that you want to support on servers. For more information about locale IDs, see [Locale IDs assigned by Microsoft](/en-us/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c).

| Server language | Locale ID (LCID) | Three-letter code |
| --- | --- | --- |
| English (default) | 0409 | ENU |
| Chinese (Simplified) | 0804 | CHS |
| Chinese (Traditional, Taiwan) | 0404 | CHT |
| Czech | 0405 | CSY |
| Dutch - Netherlands | 0413 | NLD |
| French | 040c | FRA |
| German | 0407 | DEU |
| Hungarian | 040e | HUN |
| Italian - Italy | 0410 | ITA |
| Japanese | 0411 | JPN |
| Korean | 0412 | KOR |
| Polish | 0415 | PLK |
| Portuguese - Brazil | 0416 | PTB |
| Portuguese - Portugal | 0816 | PTG |
| Russian | 0419 | RUS |
| Spanish - Spain | 0c0a | ESN |
| Swedish | 041d | SVE |
| Turkish | 041f | TRK |

## Client languages

Use the following table to map a locale ID to a language that you want to support on client computers. For more information about locale IDs, see [Locale IDs assigned by Microsoft](/en-us/openspecs/windows_protocols/ms-lcid/a9eac961-e77d-41a6-90a5-ce1a8b0cdb9c).

| Client language | Locale ID (LCID) | Three-letter code |
| --- | --- | --- |
| English (default) | 0409 | ENG |
| Chinese -Simplified | 0804 | CHS |
| Chinese (Traditional, Taiwan) | 0404 | CHT |
| Czech | 0405 | CSY |
| Danish | 0406 | DAN |
| Dutch - Netherlands | 0413 | NLD |
| Finnish | 040b | FIN |
| French | 040c | FRA |
| German | 0407 | DEU |
| Greek | 0408 | ELL |
| Hungarian | 040e | HUN |
| Italian - Italy | 0410 | ITA |
| Japanese | 0411 | JPN |
| Korean | 0412 | KOR |
| Norwegian | 0414 | NOR |
| Polish | 0415 | PLK |
| Portuguese (Brazil) | 0416 | PTB |
| Portuguese (Portugal) | 0816 | PTG |
| Russian | 0419 | RUS |
| Spanish - Spain | 0c0a | ESN |
| Swedish | 041d | SVE |
| Turkish | 041f | TRK |

### Mobile device client languages

When you add support for mobile device languages, all supported mobile device client languages are included. You can't select individual language packs for mobile device support.

## Identify installed language packs

To identify the language packs that are installed on a computer that runs the Configuration Manager client, look for the locale ID (LCID) of the installed language packs in the computer's registry. This information is available at the following registry path:

`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCMSetup\InstalledLangs`

Customize hardware inventory to collect this information. Then build a custom report to view the language details. For more information about collecting custom hardware inventory, see [How to configure hardware inventory](../../../clients/manage/inventory/configure-hardware-inventory). For more information, see [Create reports](../../manage/operations-and-maintenance-for-reporting#create-reports).