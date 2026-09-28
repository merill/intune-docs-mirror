---
layout: Conceptual
title: Create a JSON file for custom compliance settings in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/compliance/create-custom-json
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
- compliance
- sub-device-compliance
ms.subservice: protect
description: Create the JSON file that defines custom settings and values for use with device compliance policies in Intune.
ms.date: 2025-08-15T00:00:00.0000000Z
ms.topic: concept-article
ms.reviewer: ilwu
locale: en-us
document_id: 8f2b342b-90d7-904e-d3ab-4659307f6198
document_version_independent_id: 8f2b342b-90d7-904e-d3ab-4659307f6198
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/compliance/create-custom-json.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/compliance/create-custom-json
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/compliance/create-custom-json.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 6b5150e3-df24-a3a3-db96-85b81c01688b
---

# Create a JSON file for custom compliance settings in Microsoft Intune - Microsoft Intune | Microsoft Learn

To support [custom settings for compliance](custom-settings) for Microsoft Intune, create a JSON file that identifies the settings and value pairs you want to use for custom compliance. The JSON defines what a discovery script evaluates for compliance on the device.

Include the JSON file in a compliance policy when you configure a policy to assess custom compliance settings.

## Requirements

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> - Linux:
>     - Ubuntu Desktop, version 24.04 LTS or 26.04 LTS
>     - RedHat Enterprise Linux 9 or 10
>     - macOS
> - Windows
> 

A correctly formatted JSON file must include the following information:

- **SettingName** - The name of the custom setting to use for base compliance. This name is case-sensitive.
- **Operator** - Represents a specific action that's used to build a compliance rule. For options, see the list of supported operators in this article.
- **DataType** - The type of data that you can use to build your compliance rule. For options, see the following list of *supported DataTypes*.
- **Operand** - Represents the values that the operator works on.
- **MoreInfoURL** - A URL that device users can view and use to learn more about the compliance requirement if their device is noncompliant for a setting. You can also use this URL to link to instructions to help users bring their device into compliance for this setting.
- **RemediationStrings** - Information that shows in the Company Portal when a device is noncompliant to a setting. This information helps users understand the remediation options to bring a device to a compliant state. There must be at least one string for the language `en_US`. You can add other remediation string languages as needed, as demonstrated in the example provided later in this article.

Your policy can be up to 100 KB and include 100 rules.

**Supported operators**:

- IsEquals
- NotEquals
- GreaterThan
- GreaterEquals
- LessThan
- LessEquals

**Supported DataTypes**:

- Boolean
- Int64
- Double
- String
- DateTime
- Version

**Supported Languages**:

- cs\_CZ
- da\_DK
- de\_DE
- el\_GR
- en\_US
- es\_ES
- fi\_FI
- fr\_FR
- hu\_HU
- it\_IT
- ja\_JP
- ko\_KR
- nb\_NO
- nl\_NL
- pl\_PL
- pt\_BR
- ro\_RO
- ru\_RU
- sv\_SE
- tr\_TR
- zh\_CN
- zh\_TW

For more information, see [Available languages for Windows](/en-us/windows-hardware/manufacture/desktop/available-language-packs-for-windows).

## Example JSON file

```json
{
"Rules":[
    {
       "SettingName":"BiosVersion",
       "Operator":"GreaterEquals",
       "DataType":"Version",
       "Operand":"2.3",
       "MoreInfoUrl":"https://bing.com",
       "RemediationStrings":[
          {
             "Language":"en_US",
             "Title":"BIOS Version needs to be upgraded to at least 2.3. Value discovered was {ActualValue}.",
             "Description": "BIOS must be updated. Please refer to the link above"
          },
          {
             "Language":"de_DE",
             "Title":"BIOS-Version muss auf mindestens 2.3 aktualisiert werden. Der erkannte Wert lautet {ActualValue}.",
             "Description": "BIOS muss aktualisiert werden. Bitte beziehen Sie sich auf den obigen Link"
          }
       ]
    },
    {
       "SettingName":"TPMChipPresent",
       "Operator":"IsEquals",
       "DataType":"Boolean",
       "Operand":true,
       "MoreInfoUrl":"https://bing.com",
       "RemediationStrings":[
          {
             "Language": "en_US",
             "Title": "TPM chip must be enabled.",
             "Description": "TPM chip must be enabled. Please refer to the link above"
          },
          {
             "Language": "de_DE",
             "Title": "TPM-Chip muss aktiviert sein.",
             "Description": "TPM-Chip muss aktiviert sein. Bitte beziehen Sie sich auf den obigen Link"
          }
       ]
    },
    {
       "SettingName":"Manufacturer",
       "Operator":"IsEquals",
       "DataType":"String",
       "Operand":"Microsoft Corporation",
       "MoreInfoUrl":"https://bing.com",
       "RemediationStrings":[
          {
             "Language": "en_US",
             "Title": "Only Microsoft devices are supported.",
             "Description": "You are not currently using a Microsoft device."
          },
          {
             "Language": "de_DE",
             "Title": "Nur Microsoft-Geräte werden unterstützt.",
             "Description": "Sie verwenden derzeit kein Microsoft-Gerät."
          }
       ]
    }
 ]
}
```