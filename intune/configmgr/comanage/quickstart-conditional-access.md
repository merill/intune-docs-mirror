---
layout: Conceptual
title: Conditional Access with co-management - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/comanage/quickstart-conditional-access
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
description: Control user access to organizational resources based on compliance rules from Intune
ms.date: 2021-11-08T00:00:00.0000000Z
ms.subservice: co-management
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: d2b64acc-31d7-e838-285c-da552cdf5fd8
document_version_independent_id: 81368039-43fa-50a8-797b-fde31e77af06
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/comanage/quickstart-conditional-access.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/comanage/quickstart-conditional-access
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/comanage/quickstart-conditional-access.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/8b9ae643-2e85-42b8-beb2-eef4bae8c4bc
- https://authoring-docs-microsoft.poolparty.biz/devrel/63959238-cb90-4871-a33d-4a5519097e47
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c0439c36-80e3-415f-8e4c-6951e3f1b136
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/e047e27d-b5f3-43a8-b4b0-4f6dca95e7c9
- https://authoring-docs-microsoft.poolparty.biz/devrel/78d87f42-5582-4a6b-90be-7db2f12b34e6
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/2812d699-d85f-4a7f-839d-44e218b35d24
platformId: 61f590b1-2957-8869-3a87-991370dd35be
---

# Conditional Access with co-management - Configuration Manager | Microsoft Learn

Conditional Access makes sure that only trusted users can access organizational resources on trusted devices using trusted apps. It's built from scratch in the cloud. Whether you're managing devices with Intune or extending your Configuration Manager deployment with co-management, it works the same way.

In the following video, senior program manager Joey Glocke and product marketing manager Locky Ainley discuss and demo Conditional Access with co-management:

With co-management, Intune evaluates every device in your network to determine how trustworthy it is. It does this evaluation in the following two ways:

1. Intune makes sure a device or app is managed and securely configured. This check depends on how you set your organization's compliance policies. For example, make sure all devices have encryption enabled and aren't jailbroken.

    - This evaluation is pre-security breach and configuration-based
    - For co-managed devices, Configuration Manager also does configuration-based evaluation. For example, required updates or apps compliance. Intune combines this evaluation along with its own assessment.
2. Intune detects active security incidents on a device. It uses the intelligent security of [Microsoft Defender for Endpoint](/en-us/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint) and other [mobile threat defense providers](https://www.lookout.com/partners/microsoft). These partners run ongoing behavioral analysis on devices. This analysis detects active incidents, and then passes this information to Intune for real-time compliance evaluation.

    - This evaluation is post-security breach and incident-based

Microsoft corporate vice president Brad Anderson discusses Conditional Access in depth with live demos during the Ignite 2018 keynote.

Conditional Access also provides you a centralized place to see the health of all network-connected devices. You get the advantages of cloud scale, which is especially valuable for testing Configuration Manager production instances.

## Benefits

Every IT team is obsessed with network security. It's mandatory to make sure that every device meets your security and business requirements before accessing your network. With Conditional Access, you can determine the following factors:

- If every device is encrypted
- If malware is installed
- If its settings are updated
- If it's jailbroken or rooted

Conditional Access combines granular control over organizational data with a user experience that maximizes worker productivity on any device from any location.

The following video shows how Microsoft Defender for Endpoint (formerly known as Advanced Threat Protection) is integrated into common scenarios that you regularly experience:

With co-management, Intune can incorporate Configuration Manager's responsibilities for assessing your security standards compliance of required updates or apps. This behavior is important for any IT organization that wants to continue using Configuration Manager for complex app and patch management.

Conditional Access is also a critical part of developing your [Zero Trust Network](https://www.microsoft.com/security/blog/2018/06/14/building-zero-trust-networks-with-microsoft-365/) architecture. With Conditional Access, compliant device access controls cover the foundational layers of Zero Trust Network. This functionality is a large part of how you secure your organization in the future.

For more information, see the blog post on [Enhancing Conditional Access with machine-risk data from Microsoft Defender for Endpoint](https://techcommunity.microsoft.com/t5/Enterprise-Mobility-Security/Enhancing-conditional-access-with-machine-risk-data-from-Windows/ba-p/250559).

## Case studies

The IT consulting firm Wipro uses Conditional Access to protect and manage the devices used by all 91,000 employees. In a recent case study, the vice president of IT at Wipro noted:

> 
> *Achieving Conditional Access is a big win for Wipro. Now, all our employees have mobile access to information on demand.* *We enhanced our security posture and employee productivity. Now 91,000 employees benefit from highly secure access to more than 100 apps from any device, anywhere.*

Other examples include:

- Nestlé, who uses app-based Conditional Access for over 150,000 employees
- The automation software company, Cadence, who can now make sure that "only managed devices have access to Microsoft 365 Apps like Teams and the company's intranet." They can also offer their workforce "safer access to other cloud-based apps, such as Workday and Salesforce."

Intune is also fully integrated with partners like Cisco ISE, Aruba Clear Pass, and Citrix NetScaler. With these partners, you can maintain access controls based on the Intune enrollment and the device compliance state across these other platforms.

For more information, see the following videos:

- [Brad Anderson demos Conditional Access in detail](https://youtu.be/8321obNofgM?t=547)
- [More detail from Endpoint Zone 1805](https://youtu.be/f-ILlEuBFZg?t=196)

## Value proposition

With Conditional Access and ATP integration, you're fortifying a fundamental component of every IT organization: secure cloud access.

In more than 63% of all data breaches, the attackers gain access to the organization's network through weak, defaulted, or stolen user credentials. Because Conditional Access focuses on securing the user identity, it restricts credential theft. Conditional Access manages and protects your identities, whether privileged or non-privileged. There's no better way to protect the devices and the data on them.

Since Conditional Access is a core component of Enterprise Mobility + Security (EMS), there's no on-premises setup or architecture required. With Intune and Microsoft Entra ID, you can quickly configure Conditional Access in the cloud. If you're currently using Configuration Manager, you can easily extend your environment to the cloud with co-management and begin using it right now.

For more information about the ATP integration, see this blog post [Microsoft Defender for Endpoint device risk score exposes new cyberattack, drives Conditional Access to protect networks](https://www.microsoft.com/security/blog/2018/11/28/windows-defender-atp-device-risk-score-exposes-new-cyberattack-drives-conditional-access-to-protect-networks/). It details how an advanced hacker group used never before seen tools. The Microsoft cloud detected and stopped them because the targeted users had Conditional Access. The intrusion activated the device's risk-based Conditional Access policy. Although the attacker already established a foothold in the network, the exploited machines were automatically restricted from access to organizational services and data managed by Microsoft Entra ID.

## Configure

Conditional Access is easy to use when you [enable co-management](how-to-enable). It requires moving the **Compliance Policies** workload to Intune. For more information, see [How to switch Configuration Manager workloads to Intune](how-to-switch-workloads).

For more information about using Conditional Access, see the following articles:

- [Conditional Access in Microsoft Entra ID](/en-us/azure/active-directory/conditional-access/overview)
- [Use compliance policies to set rules for devices you manage with Intune](../../device-security/compliance/overview)
- [App-based Conditional Access with Intune](../../device-security/conditional-access-integration/app-based-policies)

Note

Conditional Access features become available immediately for Microsoft Entra hybrid joined devices. These features include multi-factor authentication and Microsoft Entra hybrid join access control. This behavior is because they're based on Microsoft Entra properties. To leverage configuration-based assessment from Intune and Configuration Manager, enable co-management. This configuration gives you access control directly from Intune for compliant devices. It also gives you Intune's compliance policies evaluation feature.