---
layout: Conceptual
title: Audit CIS Benchmarks with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-security/security-baselines/cis-audit-baseline
author: aanavath
ms.author: aanavath
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
ms.collection:
- M365-identity-device-management
- sub-secure-endpoints
ms.subservice: protect
description: Create a CIS audit profile in Microsoft Intune, assign it to Windows devices, review per-setting results, and export audit findings.
ms.date: 2026-11-12T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-generated
ms.custom: msecd-doc-authoring-1032
locale: en-us
document_id: b567b858-600e-5157-5865-eb38cd6600ac
document_version_independent_id: b567b858-600e-5157-5865-eb38cd6600ac
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-security/security-baselines/cis-audit-baseline.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-security/security-baselines/cis-audit-baseline
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-security/security-baselines/cis-audit-baseline.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
platformId: ad37a02f-e016-c7e5-a07e-7fc1d86342dc
---

# Audit CIS Benchmarks with Microsoft Intune - Microsoft Intune | Microsoft Learn

Use the Center for Internet Security (CIS) audit baseline in Microsoft Intune to assess Windows 11 devices against the CIS Microsoft Intune for Windows 11 Benchmark. Create an audit profile, assign it to device groups, and review the results to identify configuration gaps.

CIS auditing is in public preview. It's audit-only: assigning the profile doesn't configure settings or remediate findings.

Before you begin, review the tenant, license, device, and permission requirements in Prerequisites.

## Prerequisites

Before you create an audit profile, confirm the following requirements:

- **Tenant and license:** An Intune tenant with [Microsoft Intune Advanced Analytics](../../advanced-analytics/).
- **Devices:** Windows 11 devices [enrolled in Intune](../../device-enrollment/enroll-devices). For co-managed devices, set the **Device configuration** workload to **Pilot Intune** or **Intune**.
- **Permissions:** To create and manage audit profiles, use an Intune role with the following permissions:

    - **Organization** &gt; **Read**.
    - **Security baselines** &gt; **Assign**, **Create**, **Delete**, **Read**, and **Update**.
    - **Device configurations** &gt; **View Reports** to view audit reports.

    The [Endpoint Security Manager](../../fundamentals/role-based-access-control/ref-built-in-roles#endpoint-security-manager) built-in role includes the profile-management permissions. You can also add permissions to a [custom role](../../fundamentals/role-based-access-control/create-custom-role). Your role also needs access to the relevant [scope tags](../../fundamentals/role-based-access-control/scope-tags) and target device groups.

## Create and assign a CIS audit profile

The preview uses version **5.0.0** of the **CIS Microsoft Intune for Windows 11 Benchmark (Audit Only)**. This is the Intune-specific benchmark, not the separate Windows 11 Enterprise benchmark.

The profile audits **404 settings** in one combined profile covering **Level 1**, **Level 2**, and **BitLocker-related checks**. You can't select a level, select individual settings, or change the expected values in the profile.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Go to **Endpoint security** &gt; **Security baselines**.
3. Select **CIS Microsoft Intune for Windows 11 Benchmark (Audit Only)**, and then select **Create profile**.
4. On **Basics**, enter a descriptive **Name**, such as *CIS audit - Windows clients*. Optionally, enter a **Description**.
5. On **Configuration settings**, review the audit scope. This profile audits the benchmark settings; you don't configure their values here.
6. On **Scope tags**, add tags to control which administrators can access the profile.
7. On **Assignments**, select the device groups to audit.
8. On **Review + create**, review the profile and select **Create**.

Initial audit results can take **24 hours or longer** to appear after assignment. Policy deployment and audit reporting are separate steps. Successful profile deployment alone isn't an audit result.

## Review CIS audit results

Use **Audit report** to review benchmark findings. The standard configuration baseline reports, such as **Device and user check-in status**, **Device assignment status**, and **Per setting status**, aren't the audit-results view.

1. Go to **Endpoint security** &gt; **Security baselines** and select **CIS Microsoft Intune for Windows 11 Benchmark (Audit Only)**.
2. Select the profile you assigned.
3. Open **Audit report** and generate the report. When a report already exists, use **Generate again** to refresh it with the latest available data.
4. Use **Search** to find a setting. Review its name, **Reference Id**, and **Success devices** count.
5. Select the device-count link for a setting to open the device results. Review the audit status and last check-in information for the devices you're investigating.

### Interpret the results

Audit results describe a device's result for a particular benchmark check:

- **Pass:** The observed device configuration meets the checked recommendation.
- **Fail:** The observed device configuration doesn't meet the checked recommendation.

An evaluation error isn't a failed benchmark check. Don't count an error or a missing result as evidence that the device passes or fails.

Results aren't real-time. Review the report's generated timestamp and device check-in information when you interpret a finding. Generating a report doesn't mean every targeted device has returned a new evaluation.

The audit report shows the pass or fail result of each check but doesn't display the actual configuration value on the device.

## Export audit results

Export results when you need to review findings outside the admin center.

1. Open the profile's **Audit report**.
2. Select **Export** and save the exported results.

For general guidance on programmatic report exports, see [Export Intune reports using Microsoft Graph APIs](../../device-management/reports/export-graph-apis). That article describes the export mechanism, not a CIS-specific request or permission set.