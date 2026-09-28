---
layout: Conceptual
title: Intune endpoint security firewall settings for Configuration Manager devices - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/ref-firewall-settings-tenant-attach
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Endpoint security firewall policy settings for tenant attached devices you manage with Configuration Manager. You can configure firewall setting after you configure tenant attach for Configuration Manager.
ms.date: 2024-08-19T00:00:00.0000000Z
ms.topic: reference
ms.reviewer: laarrizz
locale: en-us
document_id: 2f207a50-b060-5e66-1481-e81c01557578
document_version_independent_id: 2f207a50-b060-5e66-1481-e81c01557578
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/endpoint-security/ref-firewall-settings-tenant-attach.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/endpoint-security/ref-firewall-settings-tenant-attach
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/endpoint-security/ref-firewall-settings-tenant-attach.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 3fe5e4d5-a114-34e1-12b9-2ab98c5ffae2
---

# Intune endpoint security firewall settings for Configuration Manager devices - Microsoft Intune | Microsoft Learn

View the Microsoft Windows Firewall settings you can manage with the **Windows Firewall (ConfigMgr)** profile from Intune. The profile is available when you configure Intune [Firewall policy](firewall), and the policy deploys to devices you manage with Configuration Manager when you've configured the [tenant attach](../../fundamentals/tenant-attach) scenario.

## Windows Firewall

- **Certificate revocation list verification (Device)** CSP: [MdmStore/Global/CRLcheck](/en-us/windows/client-management/mdm/firewall-csp#crlcheck)

    Specify how certificate revocation list (CRL) verification is enforced.

    - **Not configured** (*default*) - Use the client default, which is to disable CRL verification.
    - **None**
    - **Attempt**
    - **Require**
- **Disable Stateful Ftp (Device)** CSP: [MdmStore/Global/DisableStatefulFtp](/en-us/windows/client-management/mdm/firewall-csp#disablestatefulftp)

    - **Not configured** (*default*)
    - **True** - Stateful FTP is disabled
    - **False** - The firewall performs stateful File Transfer Protocol (FTP) filtering to allow secondary connections.
- **Enable Packet Queue (Device)** CSP: [MdmStore/Global/EnablePacketQueue](/en-us/windows/client-management/mdm/firewall-csp#enablepacketqueue)

    Select from the following options to configure scaling for the software on the receive side for the encrypted receive and clear text forward for the IPsec tunnel gateway scenario. This ensures the packet order is preserved. By default, no options are selected.

    - **Disabled**
    - **Queue Inbound**
    - **Queue Outbound**
- **IPsec Exceptions (Device)** CSP: [MdmStore/Global/IPsecExempt](/en-us/windows/client-management/mdm/firewall-csp#ipsecexempt)

    Select from the following options to configure IPsec exceptions.

    - **Exempt neighbor discover IPv6 ICMP type-codes from IPsec**
    - **Exempt ICMP from IPsec**
    - **Exempt router discover IPv6 ICMP type-codes from IPsec**
    - **Exempt both IPv4 and IPv6 DHCP traffic from IPsec**
- **Opportunistically Match Auth Set Per KM (Device)** CSP: [OpportunisticallyMatchAuthSetPerKM](/en-us/windows/client-management/mdm/firewall-csp#opportunisticallymatchauthsetperkm)

    - **Not configured** (*default*)
    - **True**
    - **False**
- **Preshared Key Encoding (Device)** CSP: [MdmStore/Global/PresharedKeyEncoding](/en-us/windows/client-management/mdm/firewall-csp#presharedkeyencoding)

    - **Not configured** (*default*)
    - **None**
    - **UTF8**
- **Security association idle time (Device)** CSP: [MdmStore/Global/SaIdleTime](/en-us/windows/client-management/mdm/firewall-csp#saidletime)

    Specify a time in seconds between **300** and **3600**, for how long the security associations are kept after network traffic isn't seen. If you don't specify any value, the system deletes a security association after it's been idle for *300* seconds.

## Domain Profile

- **Enable Domain Network Firewall (Device)** CSP: [EnableFirewall](/en-us/windows/client-management/mdm/firewall-csp#enablefirewall)

    - **Not configured** (*default*) - The client returns to its default, which is to enable the firewall.
    - **True** - The Windows Firewall for the network type of **domain** is turned on and enforced.
    - **False** - Disable the firewall.

    When set to *True*, you can then configure the following settings for this firewall profile type:

    - **Allow Local Ipsec Policy Merge (Device)** CSP: [AllowLocalIpsecPolicyMerge](/en-us/windows/client-management/mdm/firewall-csp#allowlocalipsecpolicymerge)

        - **Not configured** (*default*)
        - **True**
        - **False** - Connection security rules from the local store are ignored and not enforced.
    - **Allow Local Policy Merge (Device)** CSP: [AllowLocalPolicyMerge](/en-us/windows/client-management/mdm/firewall-csp#allowlocalpolicymerge)

        - **Not configured** (*default*)
        - **True**
        - **False** - Firewall rules from the local store are ignored and not enforced.
    - **Auth Apps Allow User Pref Merge (Device)** CSP: [AuthAppsAllowUserPrefMerge](/en-us/windows/client-management/mdm/firewall-csp#authappsallowuserprefmerge)

        - **Not configured** (*default*)
        - **True**
        - **False**
    - **Default Inbound Action for Domain Profile (Device)** CSP: [DefaultInboundAction](/en-us/windows/client-management/mdm/firewall-csp#defaultinboundaction)

        - **Not configured** (*default*)
        - **Allow**
        - **Block**
    - **Default Outbound Action (Device)** CSP: [DefaultOutboundAction](/en-us/windows/client-management/mdm/firewall-csp#defaultoutboundaction)

        - **Allow**
        - **Block**
    - **Disable Inbound Notifications (Device)** CSP: [DisableInboundNotifications](/en-us/windows/client-management/mdm/firewall-csp#disableinboundnotifications)

        - **Not configured** (*default*)
        - **True** - The firewall won't display a notification to the user when an application is blocked from listening on a port.
        - **False** - The firewall might display a notification to the user when an application is blocked from listening on a port.
    - **Disable Stealth Mode (Device)** CSP: [DisableStealthMode](/en-us/windows/client-management/mdm/firewall-csp#disablestealthmode)

        - **Not configured** (*default*)
        - **True**
        - **False** - The server operates in stealth mode. The firewall rules used to enforce stealth mode are implementation-specific.
    - **Disable Unicast Responses To Multicast Broadcast (Device)** CSP: [DisableUnicastResponsesToMulticastBroadcast](/en-us/windows/client-management/mdm/firewall-csp#disableunicastresponsestomulticastbroadcast)

        - **Not configured** (*default*)
        - **True** - Unicast response to multicast broadcast traffic is blocked.
        - **False**
    - **Global Ports Allow User Pref Merge (Device)** CSP: [GlobalPortsAllowUserPrefMerge](/en-us/windows/client-management/mdm/firewall-csp#GlobalPortsAllowUserPrefMerge)

        - **Not configured** (*default*)
        - **True**
        - **False** - Global port firewall rules in the local store are ignored and not enforced.
    - **Shielded (Device)** CSP: [Shielded](/en-us/windows/client-management/mdm/firewall-csp#shielded)

        - **Not configured** (*default*)
        - **True** - The server blocks all incoming traffic regardless of other policy settings.
        - **False**

## Private Profile

- **Enable Private Network Firewall (Device)** CSP: [EnableFirewall](/en-us/windows/client-management/mdm/firewall-csp#enablefirewall)

    - **Not configured** (*default*) - The client returns to its default, which is to enable the firewall.
    - **True** - The Windows Firewall for the network type of **private** is turned on and enforced.
    - **False** - Disable the firewall.

    When set to *True*, you can then configure the following settings for this firewall profile type:

    - **Allow Local Ipsec Policy Merge (Device)** CSP: [AllowLocalIpsecPolicyMerge](/en-us/windows/client-management/mdm/firewall-csp#allowlocalipsecpolicymerge)

        - **Not configured** (*default*)
        - **True**
        - **False** - Connection security rules from the local store are ignored and not enforced.
    - **Allow Local Policy Merge (Device)** CSP: [AllowLocalPolicyMerge](/en-us/windows/client-management/mdm/firewall-csp#allowlocalpolicymerge)

        - **Not configured** (*default*)
        - **True**
        - **False** - Firewall rules from the local store are ignored and not enforced.
    - **Auth Apps Allow User Pref Merge (Device)** CSP: [AuthAppsAllowUserPrefMerge](/en-us/windows/client-management/mdm/firewall-csp#authappsallowuserprefmerge)

        - **Not configured** (*default*)
        - **True**
        - **False**
    - **Default Inbound Action for Private Profile (Device)** CSP: [DefaultInboundAction](/en-us/windows/client-management/mdm/firewall-csp#defaultinboundaction)

        - **Not configured** (*default*)
        - **Allow**
        - **Block**
    - **Default Outbound Action (Device)** CSP: [DefaultOutboundAction](/en-us/windows/client-management/mdm/firewall-csp#defaultoutboundaction)

        - **Allow**
        - **Block**
    - **Disable Inbound Notifications (Device)** CSP: [DisableInboundNotifications](/en-us/windows/client-management/mdm/firewall-csp#disableinboundnotifications)

        - **Not configured** (*default*)
        - **True** - The firewall won't display a notification to the user when an application is blocked from listening on a port.
        - **False** - The firewall might display a notification to the user when an application is blocked from listening on a port.
    - **Disable Stealth Mode (Device)** CSP: [DisableStealthMode](/en-us/windows/client-management/mdm/firewall-csp#disablestealthmode)

        - **Not configured** (*default*)
        - **True**
        - **False** - The server operates in stealth mode. The firewall rules used to enforce stealth mode are implementation-specific.
    - **Disable Unicast Responses To Multicast Broadcast (Device)** CSP: [DisableUnicastResponsesToMulticastBroadcast](/en-us/windows/client-management/mdm/firewall-csp#disableunicastresponsestomulticastbroadcast)

        - **Not configured** (*default*)
        - **True** - Unicast response to multicast broadcast traffic is blocked.
        - **False**
    - **Global Ports Allow User Pref Merge (Device)** CSP: [GlobalPortsAllowUserPrefMerge](/en-us/windows/client-management/mdm/firewall-csp#GlobalPortsAllowUserPrefMerge)

        - **Not configured** (*default*)
        - **True**
        - **False** - Global port firewall rules in the local store are ignored and not enforced.
    - **Shielded (Device)** CSP: [Shielded](/en-us/windows/client-management/mdm/firewall-csp#shielded)

        - **Not configured** (*default*)
        - **True** - The server blocks all incoming traffic regardless of other policy settings.
        - **False**

## Public Profile

- **Enable Public Network Firewall (Device)** CSP: [EnableFirewall](/en-us/windows/client-management/mdm/firewall-csp#enablefirewall)

    - **Not configured** (*default*) - The client returns to its default, which is to enable the firewall.
    - **True** - The Windows Firewall for the network type of **public** is turned on and enforced.
    - **False** - Disable the firewall.

    When set to *True*, you can then configure the following settings for this firewall profile type:

    - **Allow Local Ipsec Policy Merge (Device)** CSP: [AllowLocalIpsecPolicyMerge](/en-us/windows/client-management/mdm/firewall-csp#allowlocalipsecpolicymerge)

        - **Not configured** (*default*)
        - **True**
        - **False** - Connection security rules from the local store are ignored and not enforced.
    - **Allow Local Policy Merge (Device)** CSP: [AllowLocalPolicyMerge](/en-us/windows/client-management/mdm/firewall-csp#allowlocalpolicymerge)

        - **Not configured** (*default*)
        - **True**
        - **False** - Firewall rules from the local store are ignored and not enforced.
    - **Auth Apps Allow User Pref Merge (Device)** CSP: [AuthAppsAllowUserPrefMerge](/en-us/windows/client-management/mdm/firewall-csp#authappsallowuserprefmerge)

        - **Not configured** (*default*)
        - **True**
        - **False**
    - **Default Inbound Action for Public Profile (Device)** CSP: [DefaultInboundAction](/en-us/windows/client-management/mdm/firewall-csp#defaultinboundaction)

        - **Not configured** (*default*)
        - **Allow**
        - **Block**
    - **Default Outbound Action (Device)** CSP: [DefaultOutboundAction](/en-us/windows/client-management/mdm/firewall-csp#defaultoutboundaction)

        - **Allow**
        - **Block**
    - **Disable Inbound Notifications (Device)** CSP: [DisableInboundNotifications](/en-us/windows/client-management/mdm/firewall-csp#disableinboundnotifications)

        - **Not configured** (*default*)
        - **True** - The firewall won't display a notification to the user when an application is blocked from listening on a port.
        - **False** - The firewall might display a notification to the user when an application is blocked from listening on a port.
    - **Disable Stealth Mode (Device)** CSP: [DisableStealthMode](/en-us/windows/client-management/mdm/firewall-csp#disablestealthmode)

        - **Not configured** (*default*)
        - **True**
        - **False** - The server operates in stealth mode. The firewall rules used to enforce stealth mode are implementation-specific.
    - **Disable Unicast Responses To Multicast Broadcast (Device)** CSP: [DisableUnicastResponsesToMulticastBroadcast](/en-us/windows/client-management/mdm/firewall-csp#disableunicastresponsestomulticastbroadcast)

        - **Not configured** (*default*)
        - **True** - Unicast response to multicast broadcast traffic is blocked.
        - **False**
    - **Global Ports Allow User Pref Merge (Device)** CSP: [GlobalPortsAllowUserPrefMerge](/en-us/windows/client-management/mdm/firewall-csp#GlobalPortsAllowUserPrefMerge)

        - **Not configured** (*default*)
        - **True**
        - **False** - Global port firewall rules in the local store are ignored and not enforced.
    - **Shielded (Device)** CSP: [Shielded](/en-us/windows/client-management/mdm/firewall-csp#shielded)

        - **Not configured** (*default*)
        - **True** - The server blocks all incoming traffic regardless of other policy settings.
        - **False**