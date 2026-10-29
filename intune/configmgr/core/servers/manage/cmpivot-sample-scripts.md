---
layout: Conceptual
title: CMPivot sample scripts - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/cmpivot-sample-scripts
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
description: Script samples for CMPivot in Configuration Manager.
ms.date: 2021-07-12T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: sample
ms.collection: tier3
locale: en-us
document_id: 0b5e24c0-5e1a-ef69-c899-242315f05693
document_version_independent_id: 0db69574-6a67-8952-e839-70a6ea3c3e8c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/manage/cmpivot-sample-scripts.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/manage/cmpivot-sample-scripts
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/manage/cmpivot-sample-scripts.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 11e46784-7c61-1369-c298-b64d49140c21
---

# CMPivot sample scripts - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Below are a few common query needs and how CMPivot can be used to meet them. CMPivot uses a subset of the [Kusto Query Language (KQL)](/en-us/azure/kusto/query).

## Operating system

Gets operating system information.

```kusto
// Sample query for OS information
OperatingSystem
```

## Recently used applications

The following query gets recently used applications (last 2 hours):

```kusto
CCMRecentlyUsedApplications
| where (LastUsedTime > ago(2h))
| project CompanyName, ProductName, ProductVersion, LastUsedTime
```

## Device start times

The following query shows when were the devices started in the last seven days:

```kusto
OperatingSystem
| where LastBootUpTime <= ago(7d)
| summarize count() by bin(LastBootUpTime,1d)
```

## Free disk space

The following query shows free disk space:

```kusto
LogicalDisk
| project Device, DeviceID, Name, Description, FileSystem, Size, FreeSpace
| order by DeviceID asc
```

## Device information

Show device, manufacturer, model, and OSVersion:

```kusto
ComputerSystem
| project Device, Manufacturer, Model
| join (OperatingSystem | project Device, OSVersion=Caption)
```

## Boot times for a device

Show boot times for devices:

```kusto
SystemBootData
| project Device, SystemStartTime, BootDuration, OSStart=EventLogStart, GPDuration, UpdateDuration
| order by SystemStartTime desc
```

## Authentication failures

Search the event logs for authentication failures.

```kusto
EventLog('Security')
| where  EventID == 4673
```

## ProcessModule(&lt;processname&gt;)

Enumerates all the modules (dlls) loaded by a given process. ProcessModule is useful when hunting for malware that hides in legitimate processes.

```kusto
ProcessModule('powershell')
| summarize count() by ModuleName
| order by count_ desc
```

## Antimalware software status

Gets the status of antimalware software installed on the computer gathered by the `Get-MpComputerStatus` cmdlet. The entity is supported on Windows 10 and Server 2016, or later with Defender running. |

```kusto
EPStatus
| project Device, QuickScanAge=datetime_diff('day',now(),QuickScanEndTime)
| summarize DeviceCount=count() by QuickScanAge
```

## Find BIOS Manufacturer that contains any word like Micro

```kusto
Bios
// Find BIOS Manufacturer that contains any word like Micro, such as Microsoft
| where Manufacturer like '%Micro%'
```

## Find file by its hash

Search for a file by hash.

```kusto
Device
| join kind=leftouter ( File('%windir%\\system32\\*.exe')
| where SHA256Hash == 'A92056D772260B39A876D01552496B2F8B4610A0B1E084952FE1176784E2CE77')
| project Device, MalwareFound = iif( isnull(FileName), 'No', 'Yes')
```

## Find 'Scripts' in the CCM logs in the last hour

The following query looks at events in the last 1 hour:

```kusto
CcmLog('Scripts',1h)
```

## Find information in the registry

Search for registry information.

```kusto
// Change the path to match your desired registry hive query
// The RegistryKey entity (added in version 2107) isn't supported with CMPivot for tenant attached devices.  

Registry('hklm:\SOFTWARE\Microsoft\EnterpriseCertificates\Root\Certificates\*')
RegistryKey('hklm:\SOFTWARE\Microsoft\EnterpriseCertificates\Root\Certificates\*')

RegistryKey('hklm:\SOFTWARE\Microsoft\SMS\*')
Registry('hklm:\SOFTWARE\Microsoft\SMS\*')
```