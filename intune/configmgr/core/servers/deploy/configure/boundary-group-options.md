---
layout: Conceptual
title: Boundary group options - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/boundary-group-options
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
description: Configure boundary group options to control policy and content distribution.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: ac434113-1677-41a0-9392-0ad0deee30a2
document_version_independent_id: ababe8b3-bac4-ae31-328f-dee61096657e
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/configure/boundary-group-options.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/configure/boundary-group-options
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/configure/boundary-group-options.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
platformId: 876b1c8d-40de-9334-6ba4-c7049e5621fe
---

# Boundary group options - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

To give you more control over policy and content distribution in your environment, boundary groups include several options to configure behaviors. These settings primarily apply to downloading content from peer sources. There's also a setting for clients to prefer policy and content from cloud-based sources.

For more information on how to configure these settings, see [Configure a boundary group](boundary-group-procedures#configure-a-boundary-group).

If a device is in more than one boundary group, the following behaviors apply for these settings:

- **Allow peer downloads in this boundary group**: If it's disabled in any one boundary group, the client won't use delivery optimization.
    - **During peer downloads, only use peers within the same subnet**: If it's enabled in any one boundary group, this setting takes effect.
    - **Prefer distribution points over peers within the same subnet**: If it's enabled in any one boundary group, this setting takes effect.
- **Prefer cloud based sources over on-premises sources**: If it's enabled in any one boundary group, this setting takes effect.

## Allow peer downloads in this boundary group

This setting is enabled by default. The management point provides clients a list of content locations that includes peer sources. This setting also affects applying Group IDs for [Delivery Optimization](../../../plan-design/hierarchy/fundamental-concepts-for-content-management#delivery-optimization).

There are two common scenarios in which you should consider disabling this option:

- If you have a boundary group that includes boundaries from geographically dispersed locations such as a VPN. Two clients may be in the same boundary group because they're connected through VPN, but in vastly different locations that are inappropriate for peer sharing of content.
- If you use a single, large boundary group for site assignment that doesn't reference any distribution points.

Important

If a device is in more than one boundary group, make sure to enable this setting on all boundary groups for the device. Otherwise the client won't use delivery optimization. For example, it doesn't set the DOGroupID registry key.

## During peer downloads, only use peers within the same subnet

This setting is dependent upon the preceding option. If you enable this option, the management point only includes in the content location list peer sources that are in the same subnet as the client.

Common scenarios for enabling this option:

- Your boundary group design for content distribution includes one large boundary group that overlaps other smaller boundary groups. With this new setting, the list of content sources that the management point provides to clients only includes peer sources from the same subnet.
- You have a single large boundary group for all remote office locations. Enable this option and clients only share content within the subnet at the remote office location, instead of risking sharing content between locations.

Depending on the configuration of your network, you can exclude certain subnets for matching. For example, you want to include a boundary but exclude a specific VPN subnet. By default, Configuration Manager excludes the default Teredo subnet (`2001:0000:%`).

Note

When you [expand a stand-alone primary site](../install/prerequisites-for-installing-sites#bkmk_expand) to add a central administration site (CAS), the subnet exclusion list reverts to the default. To work around this issue, after site expansion, run the PowerShell script to customize the subnet exclusion list on the CAS.

Import your subnet exclusion list as a comma-separated subnet string. Use the percent sign (`%`) as a wildcard character. On the top-level site server, set or read the **SubnetExclusionList** embedded property for the **SMS\_HIERARCHY\_MANAGER** component in the **SMS\_SCI\_Component** class. For more information, see [SMS_SCI_Component server WMI class](../../../../develop/reference/core/servers/configure/sms_sci_component-server-wmi-class).

### Sample PowerShell script to update the subnet exclusion list

The following script is a sample way of changing this value. Append your subnets to the **PropertyValue** variable after `2001:0000:%,172.16.16.0`. It's a comma-separated string. Run this script on the top-level site server in your hierarchy.

```PowerShell
$PropertyValue = "2001:0000:%,172.16.16.0"
$PropertyName = "SubnetExclusionList"

$providerMachine = Get-WmiObject -Class "SMS_ProviderLocation" -Namespace "root\sms"

if ($providerMachine -is [system.array])
{
    $providerMachine=$providerMachine[0]
}

$SiteCode = $providerMachine.SiteCode

$component = Get-WmiObject -Query 'select comp.* from sms_sci_component comp join SMS_SCI_SiteDefinition sdef on sdef.SiteCode=comp.SiteCode where sdef.ParentSiteCode="" and comp.componentname="SMS_HIERARCHY_MANAGER"' -ComputerName $providerMachine.Machine -Namespace root\sms\site_$SiteCode
$properties = $component.props

Write-host "Updating property for site " $SiteCode

foreach ($property in $properties)
{
  if ($property.propertyname -like $PropertyName)
  {
    Write-host "Current value for SubnetExclusionList is " $property.value1
    $property.value1 = $PropertyValue
    Write-host "Updating value for SubnetExclusionList to " $property.value1
    break
  }
}

$component.props = $properties
$component.put()
```

Note

By default, Configuration Manager includes the Teredo subnet in this list. When you change the list, always read the existing value first. Append additional subnets to the list, and then set the new value.

## Prefer distribution points over peers within the same subnet

By default, the management point prioritizes peer cache sources at the top of the list of content locations. This setting reverses that priority for clients that are in the same subnet as the peer cache source.

Tip

This behavior applies to the Configuration Manager client. It doesn't apply when the task sequence downloads content. When the task sequence runs, it prefers peer cache sources over distribution points. 

## Prefer cloud based sources over on-premises sources

If you have a branch office with a faster internet link, you can prioritize cloud-based sources, which include the following locations:

- Cloud management gateway (CMG). Clients will prefer the CMG for both policy and content.
    - Starting in version 2203, this setting also applies for software update scanning. To reduce the performance impact of this change, existing clients don't automatically switch to a cloud-based software update point. For more information, see [Boundary groups and software update points](boundary-groups-software-update-points#bkmk_prefer_cmgsup).
- Microsoft Update
    - You can only use **Microsoft Update** as a source when you enable the following option in the software update deployment download settings: **If software updates are not available on distribution point in current, neighbor or site boundary groups, download content from Microsoft Updates**.