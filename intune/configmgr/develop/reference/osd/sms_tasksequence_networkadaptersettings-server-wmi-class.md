---
layout: Conceptual
title: SMS_TaskSequence_NetworkAdapterSettings class - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/osd/sms_tasksequence_networkadaptersettings-server-wmi-class
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
description: Details of the SMS_TaskSequence_NetworkAdapterSettings server WMI class
ms.date: 2016-09-20T00:00:00.0000000Z
ms.subservice: sdk
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: cf0ab4b2-43a6-1195-18be-bbd2e7767470
document_version_independent_id: c7d7cba8-6183-e8ab-c8a2-f02e210b15c7
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/develop/reference/osd/sms_tasksequence_networkadaptersettings-server-wmi-class.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/develop/reference/osd/sms_tasksequence_networkadaptersettings-server-wmi-class
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/develop/reference/osd/sms_tasksequence_networkadaptersettings-server-wmi-class.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://authoring-docs-microsoft.poolparty.biz/devrel/68cb9039-df60-49b0-8ef8-89ad96497f63
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://authoring-docs-microsoft.poolparty.biz/devrel/725b6df3-93e8-472d-834e-e7e0d2953d35
platformId: de3210af-ce5b-b833-8900-9f54fa489c24
---

# SMS_TaskSequence_NetworkAdapterSettings class - Configuration Manager | Microsoft Learn

The `SMS_TaskSequence_NetworkAdapterSettings` Windows Management Instrumentation (WMI) class is an SMS Provider server class, in Configuration Manager, that specifies the settings to apply to a physical network adapter.

The following syntax is simplified from Managed Object Format (MOF) code and includes all inherited properties.

## Syntax

```
Class SMS_TaskSequence_NetworkAdapterSettings
{
      String DNSServerList[];
      Boolean EnableDHCP;
      Boolean EnableDNSRegistration;
      Boolean EnableFullDNSRegistration;
      Boolean EnableIPProtocolFiltering;
      Boolean EnableLMHOSTS;
      Boolean EnableTCPFiltering;
      Boolean EnableUDPFiltering;
      Boolean EnableWINS;
      UInt32 GatewayCostMetric;
      String Gateways[];
      UInt32 Index;
      String IPAddressList[];
      String IPProtocolFilterList[];
      String MACAddress;
      String Name;
      String SubnetMask[];
      SInt32 TCPFilterPortList[];
      UInt32 TcpipNetbiosOptions;
      SInt32 UDPFilterPortList[];
      String WINSServerList[];
};
```

## Methods

The `SMS_TaskSequence_NetworkAdapterSettings` class does not define any methods.

## Properties

`DNSServerList` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

List of Domain Name System (DNS) servers for the adapter.

`EnableDHCP` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` to enable Dynamic Host Configuration Protocol (DHCP) for the adapter.

`EnableDNSRegistration` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` to register the IP address for the adapter in DNS.

`EnableFullDNSRegistration` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` to register the IP address for the adapter in DNS under the full DNS name for the computer.

`EnableIPProtocolFiltering` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` to enable IP protocol filtering on the adapter.

`EnableLMHOSTS` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` to use local lookup files for Windows Internet Name Service (WINS) resolution.

`EnableTCPFiltering` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` to enable TCP port filtering for the adapter.

`EnableUDPFiltering` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` to enable User Datagram Protocol (UDP) port filtering for the adapter.

`EnableWINS` Data type: `Boolean`

Access type: Read/Write

Qualifiers: [not\_null]

`true` to use WINS for name resolution.

Important

WINS is a deprecated service. For more information, see [Windows Internet Name Service (WINS)](/en-us/windows-server/networking/technologies/wins/wins-top).

`GatewayCostMetric` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

List of integer cost metrics. This property is ignored unless `EnableDHCP` is set to `false`.

`Gateways` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

List of IP gateway addresses. This property is ignored unless `EnableDHCP` is set to `false`.

`Index` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Index of the network adapter settings in the array of settings. See the `Adapters` property of [SMS_TaskSequence_ApplyNetworkSettingsAction Server WMI Class](sms_tasksequence_applynetworksettingsaction-server-wmi-class).

`IPAddressList` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

List of IP addresses for the adapter. This property is ignored unless `EnableDHCP` is set to `false`.

`IPProtocolFilterList` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

Array of protocols allowed to run over IP. This property is ignored if `EnableIPProtocolFiltering` is set to `false`.

`MACAddress` Data type: `String`

Access type: Read/Write

Qualifiers: [not\_null]

Media access controller (MAC) address used to match settings to physical network adapter.

`Name` Data type: `String`

Access type: Read/Write

Qualifiers: [AllowedLen("0-255")]

Name of the network connection as it appears in the network connections control panel program. The name is between 0 and 255 characters in length.

`SubnetMask` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

List of subnet masks. This property is ignored unless `EnableDHCP` is set to `false`.

`TCPFilterPortList` Data type: `SInt32` Array

Access type: Read/Write

Qualifiers: None

Array of ports to be granted access permissions for TCP. This property is ignored if `EnableTCPFiltering` is set to `false`.

`TcpipNetbiosOptions` Data type: `UInt32`

Access type: Read/Write

Qualifiers: None

Options for NetBIOS over TCP/IP. Possible values are:

| Value | NetBIOS options |
| --- | --- |
| 0 | Use NetBIOS settings from DHCP server. |
| 1 | Enable NetBIOS over TCP/IP. |
| 2 | Disable NetBIOS over TCP/IP. |

`UDPFilterPortList` Data type: `SInt32` Array

Access type: Read/Write

Qualifiers: None

Array of ports to be granted access permissions for UDP. This property is ignored if `EnableUDPFiltering` is set to `false`.

`WINSServerList` Data type: `String` Array

Access type: Read/Write

Qualifiers: None

List of WINS server IP addresses. This property is ignored unless `EnableWINS` is set to `true`.

## Remarks

There are no class qualifiers for this class. For more information about both the class qualifiers and the property qualifiers included in the Properties section, see [Configuration Manager Class and Property Qualifiers](../misc/class-and-property-qualifiers).

## Requirements

### Runtime Requirements

For more information, see [Configuration Manager Server Runtime Requirements](../../core/reqs/server-runtime-requirements).

### Development Requirements

For more information, see [Configuration Manager Server Development Requirements](../../core/reqs/server-development-requirements).