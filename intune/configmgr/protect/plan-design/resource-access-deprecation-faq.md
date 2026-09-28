---
layout: FAQ
title: FAQ for resource access deprecation - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/plan-design/resource-access-deprecation-faq
summary: >
  <p><em>Applies to: Configuration Manager (current branch)</em></p>

  <p>Starting in Configuration Manager version 2103, the following company resource access <a href="../../core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures">features are deprecated</a>:<!-- 9315387 --></p>

  <ul>

  <li>Certificate profiles, including the certificate registration point site system role <!--13951253--></li>

  <li>VPN profiles</li>

  <li>Wi-Fi profiles</li>

  <li>Windows Hello for Business settings</li>

  <li>Email profiles</li>

  <li>The co-management resource access workload</li>

  </ul>

  <div class="IMPORTANT">

  <p>Important</p>

  <p>If above mentioned resource access profiles are configured in Intune, but the applicability to co-managed devices are controlled through the co-management Resource Access workload setting in Configuration Manager, post 2403 upgrade, the Resource Access workload is moved to Intune and hence all resource access profiles

  configured in Intune are now applicable and enforced to co-managed devices.</p>

  </div>

  <p>This article answers your frequently asked questions about these deprecated features.</p>
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
description: Frequently asked questions (FAQ) about the end of support for compliance settings for company resource access features.
ms.date: 2022-04-08T00:00:00.0000000Z
ms.topic: faq
ms.subservice: protect
locale: en-us
document_id: 69d7dbb1-ad01-f215-27e8-3342aa05e9f6
document_version_independent_id: 69d7dbb1-ad01-f215-27e8-3342aa05e9f6
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/plan-design/resource-access-deprecation-faq.yml
site_name: Docs
depot_name: MSDN.memdocs
page_type: faq
toc_rel: ../toc.json
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/plan-design/resource-access-deprecation-faq
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/plan-design/resource-access-deprecation-faq.yml
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/798bd9d1-9cc5-4fc7-b0e5-8699d1f6ce2a
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/eab1aabc-e18c-405b-ac29-e35eb0b15e3b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/b5dc5f65-34a8-4bfc-9917-97d1e20c88b2
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/574d2eb1-e22a-49c0-b4eb-64e86dbeee6b
platformId: 78ac41d3-d1a2-65e5-2f8b-e4129bbdf597
---

# FAQ for resource access deprecation - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Starting in Configuration Manager version 2103, the following company resource access [features are deprecated](../../core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures):

- Certificate profiles, including the certificate registration point site system role
- VPN profiles
- Wi-Fi profiles
- Windows Hello for Business settings
- Email profiles
- The co-management resource access workload

Important

If above mentioned resource access profiles are configured in Intune, but the applicability to co-managed devices are controlled through the co-management Resource Access workload setting in Configuration Manager, post 2403 upgrade, the Resource Access workload is moved to Intune and hence all resource access profiles configured in Intune are now applicable and enforced to co-managed devices.

This article answers your frequently asked questions about these deprecated features.

## What happens when you upgrade to CM 2403?

When you upgrade your Configuration Manager site to 2403, the [prerequisite checker displays an error](../../core/servers/deploy/install/list-of-prerequisite-checks#resource-access-policies-are-no-longer-supported). This blocks upgrade.

**Action required by customer:** Delete all Resource Access profiles and associated deployments and move the co-management workload for Resource Access (if co-managed) to Intune. Reevaluate the prerequisite rules, which allows you to proceed with upgrade.

After the upgrade completion, if the cloud attach wizard is configured, the Resource Access workload (configured to Intune) remains greyed out in console. If the customer isn't previously cloud attached and configures the cloud attach wizard, during or after upgrade, the Resource Access workload is defaulted to Intune and remains greyed out in the console. **Company Resource Access** node in Asset Management workspace will be removed.

## When will these features removed from Configuration Manager?

Starting in version 2203, these features will still be available in Configuration Manager, but no longer tested or supported. When you upgrade to version 2203, the [prerequisite checker displays a warning](../../core/servers/deploy/install/list-of-prerequisite-checks#resource-access-policies-are-no-longer-supported).

In version 2207, the creation of new company resource access profiles including the certificate registration point site system role is disabled. Set/New/Import type PowerShell cmdlets for Resource Access features are deprecated as well.

These features will be removed in 2403.

## If I'm still using these features, can I upgrade to version 2207?

Yes. If the site has any of these policies, the 2207 prerequisite checker will display a warning. Before you upgrade to version 2211, replace the functionality of these features, and remove the policies from the site.

If the site has the certificate registration point site system role, you also need to remove it. For more information, see [Remove a site system role](../../core/servers/deploy/install/uninstall-sites-and-hierarchies#procedure-to-remove-a-site-system-role).

## What functionality is available to replace these features?

Use Microsoft Intune to deploy resource access profiles. For more information, see [Apply features and settings on your devices using device profiles in Microsoft Intune](../../../device-configuration/overview).

Use [co-management](../../comanage/overview) to enroll Configuration Manager clients to Intune.

## What do I do if I'm deploying wi-fi profiles with Configuration Manager?

Before you upgrade to Configuration Manager version 2203, [enable co-management](../../comanage/how-to-enable), and deploy the same wi-fi profiles with Intune. For more information, see [Add and use Wi-Fi settings on your devices in Microsoft Intune](../../../device-configuration/templates/configure-wifi). If you don't take action, the existing wi-fi profiles will persist on devices but are unmanaged.

## What happens if I don't enable co-management?

If you currently use these features, they're not tested or supported in version 2203. When you upgrade to version 2207, they'll cause warning prerequisite checks. You can't create new wi-fi, VPN, Windows Hello for Business, or certificate (SCEP, PFX, or root CA) profiles for Configuration Manager clients. Any existing deployed profiles won't be removed from devices and will continue to function. These existing profiles are unmanaged. For example, when a certificate expires, Configuration Manager won't renew it.

## What happens if I've enabled co-management, but haven't switched the resource access workload?

Starting in version 2211, the prerequisite checker will display a warning for co-managed clients if the resource access workload is on Configuration Manager. If the resource access slider is towards Configuration Manager, they aren't tested or supported in version 2203. Co-management behavior is the same as if you used Configuration Manager 2111 or earlier to switch the resource access workload to Intune. This Workload slider will be disabled, and you can only use Microsoft Intune to deploy resource access profiles in upcoming Configuration Manager versions.

## What alternative options are available?

Configuration Manager version 2111 fully supports these features and is supported until June 2023. For more information, see [Supported versions](../../core/servers/manage/updates#supported-versions).