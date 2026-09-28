---
layout: Conceptual
title: Plan and Prepare for Endpoint Privilege Management Deployment - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/epm/deployment-planning
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.reviewer: mikedano
ms.subservice: suite
description: Plan your Endpoint Privilege Management deploying by understanding requirements, fundamentals, and security recommendations.
ms.date: 2026-01-26T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 09329aeb-dc7c-6d88-9ade-6cdd5ad66e72
document_version_independent_id: 09329aeb-dc7c-6d88-9ade-6cdd5ad66e72
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/epm/deployment-planning.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: epm/deployment-planning
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/epm/deployment-planning.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/19ec6774-09b8-473e-a17e-b17b518bbad7
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ade36b61-c646-4bd8-87ee-f3a843461962
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: 4c61009c-d834-1911-7163-5095d00803c7
---

# Plan and Prepare for Endpoint Privilege Management Deployment - Microsoft Intune | Microsoft Learn

This article covers the information required to plan for Endpoint Privilege Management (EPM) deployment including requirements, important concepts, security recommendations, and role based access control.

## Planning Checklist

- Review technical and licensing prerequisites in your tenant.
- Define your target user personas to enable you to build rules with logical grouping on these personas.
- Ensure you have a good understanding of elevation settings and elevation rules policies, including:
    - Default elevation settings and diagnostic data collection.
    - Defining elevation files using file hash, metadata, or certificates.
    - How certificate rules can allow any app signed by that certificate to elevate. Exercise caution for vendors who might sign all their apps with the same certificate.
    - Rules argument support, and child process behavior options.
    - Elevation types.
    - How rule conflicts are handled when you have overlapping rule assignments.
- Find the right balance between security and flexibility for your organization and user personas.
- Ensure you have a robust rollout strategy. This includes stakeholder management, end user communication and training plans, and monitoring.

## Prerequisites

![](../media/icons/16/licensing.svg)**Licensing requirements**

> 
> This feature requires a subscription in addition to Microsoft Intune Plan 1 or Plan 2. For licensing options, see [Microsoft Intune plans and pricing](https://aka.ms/MicrosoftIntunePricing) and [Microsoft 365 Security Enterprise Plans](https://www.microsoft.com/security/pricing/enterprise-plans).

![](../media/icons/16/devices.svg)**Device platform requirements**

> 
> Endpoint Privilege Management supports the following operating systems:
> 
> - Windows 11, version 24H2
> - Windows 11, version 23H2 (22631.2506 or later) with [KB5031455](https://support.microsoft.com/topic/october-31-2023-kb5031455-os-builds-22621-2506-and-22631-2506-preview-6513c5ec-c5a2-4aaf-97f5-44c13d29e0d4)
> - Windows 11, version 22H2 (22621.2215 or later) with [KB5029351](https://support.microsoft.com/topic/august-22-2023-kb5029351-os-build-22621-2215-preview-9af25662-083a-43f5-b3a7-975fe25cc692)
> - Windows 11, version 21H2 (22000.2713 or later) with [KB5034121](https://support.microsoft.com/topic/january-9-2024-kb5034121-os-build-22000-2713-f5847e32-0b71-4151-8190-54d3e36386f0)
> - Windows 10, version 22H2 (19045.3393 or later) with [KB5030211](https://support.microsoft.com/topic/september-12-2023-kb5030211-os-builds-19044-3448-and-19045-3448-c0dee353-f025-4f03-bcc1-336f74fb992c)
> - Windows 10, version 21H2 (19044.3393 or later) with [KB5030211](https://support.microsoft.com/topic/september-12-2023-kb5030211-os-builds-19044-3448-and-19045-3448-c0dee353-f025-4f03-bcc1-336f74fb992c)
> 
> 
> Endpoint Privilege Management supports the following virtual platforms:
> 
> - Azure Virtual Desktop (AVD) single-session virtual machines (VMs)
> - Windows 365
> 
> 
> Important
> 
> On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.
> 
> Important
> 
> - Elevation settings policies report as 'not applicable' for devices that don't run a supported operating system version.
> - Endpoint Privilege Management is only compatible with 64-bit Operating System Architectures, including Arm64.
> 

![](../media/icons/16/configuration.svg)**Device configuration requirements**

> 
> To use Endpoint Privilege Management, devices must be:
> 
> - Microsoft Entra joined *or* Microsoft Entra hybrid joined
> - Enrolled in Intune *or* Microsoft Configuration Manager [co-managed](../configmgr/comanage/overview) (no workload requirements)
> 
> 
> Devices must also have clear line of sight (without SSL-Inspection) to the [required endpoints](../fundamentals/endpoints#microsoft-intune-endpoint-privilege-management) for Endpoint Privilege Management.

![](../media/icons/16/cloud.svg)**Cloud requirements**

> 
> Specialty device management is supported in the following cloud environments:
> 
> - Public cloud
> - Sovereign cloud environments:
>     - U.S. Government Community Cloud (GCC) High
>     - U.S. Department of Defense (DoD)
> 

For more information, see [Microsoft Intune for US Government GCC service description](../fundamentals/government-service).

## Important concepts for Endpoint Privilege Management

When you configure the *elevation settings* and *elevation rules* policies that were mentioned previously, there are some important concepts to understand ensuring you configure EPM to meet the needs of your organization. Before you widely deploy EPM, the following concepts should be well understood as well as the effect they have on your environment:

- **Run with elevated access** - A right-click context menu option that appears when EPM is activated on a device. When this option is used, the devices elevation rules policies are checked for a match to determine if, and how, that file can be elevated to run in an administrative context. If there's no applicable elevation rule, then the device uses the default elevation configurations as defined by the elevation settings policy.
- **File elevation and elevation types** – EPM allows users without administrative privileges to run processes in the administrative context. When you create an elevation rule, that rule allows EPM to proxy the target of that rule to run with administrator privileges on the device. The result is that the application has *full administrative* capability on the device.

Except for *Elevate as current user*, EPM uses a *virtual account* to elevate processes. This isolates elevated actions from the user's profile, reducing exposure to user-specific data and lowering the risk of privilege escalation.

When you use Endpoint Privilege Management, there are a few options for elevation behavior:

- **Automatic**: For automatic elevation rules, EPM *automatically* elevates these applications without input from the user. Broad rules in this category can have widespread impact to the security posture of the organization.
- **User confirmed**: With user confirmed rules, end users use a new right-click context menu *Run with elevated access*. User confirmed rules can also require validation with authentication or business justification. Requiring validation provides an extra layer of protection by making the user acknowledge the elevation.
- **Elevate as current user**: This type of elevation runs the elevated process under the signed-in user's own account, preserving compatibility with tools and installers that rely on the active user profile. This requires the user to enter their credentials for Windows Authentication. This preserves the user's profile paths, environment variables, and personalized settings. Because the elevated process maintains the same user identity before and after elevation, audit trails remain consistent and accurate.

    However, because the elevated process inherits the user's full context, this mode introduces a broader attack surface and reduces isolation from user data.

    Key considerations:

    - Compatibility need: Use this mode only when virtual account elevation causes application failures.
    - Scope tightly: Limit elevation rules to trusted binaries and paths to reduce risk.
    - Security tradeoff: Understand that this mode increases exposure to user-specific data.

    Tip

    When compatibility isn't an issue, prefer a method that uses the virtual account elevation for stronger security.
- **Deny**: A deny rule identifies a file that EPM blocks from running in an elevated context. Deny rules can ensure that known files or potentially malicious software can't be run in an elevated context.
- **Support approved**: For support approved rules, end users must submit a request to run an application with elevated permissions. Once the request is submitted, an administrator can approve the request. Once the request is approved, the end user is notified that they can retry the elevation on the device. For more information about using this rule type, see [Support approved elevation requests](manage-support-approvals)

Note

Each elevation rule can also set the elevation behavior for child processes that the elevated process creates.

- **Child process controls** - When processes are elevated by EPM, you can control how the creation of child processes is governed by EPM, which allows you to have granular control over any subprocesses that might be created by your elevated application.
- **Client-side components** – To use Endpoint Privilege Management, Intune provisions a small set of components on the device that receive elevation policies and enforces them. Intune provisions the components only when an elevation settings policy is received, and the policy expresses the intent to *enable* Endpoint Privilege management.
- **Managed elevations vs unmanaged elevations** – These terms might be used in our reporting and usage data. These terms refer to the following descriptions:

    - **Managed elevation**: Any elevation that Endpoint Privilege Management facilitates. Managed elevations include all elevations that EPM ends up facilitating for the standard user. These managed elevations could include elevations that happen as the result of an elevation rule or as part of default elevation action.
    - **Unmanaged elevation**: All file elevations that happen without use of Endpoint Privilege Management. These elevations can happen when a user with administrative rights uses the Windows default action of *Run as administrator*.

## EPM Policies

✅ Understand EPM policy types

Endpoint Privilege Management uses two policy types that you configure to manage how a file elevation request is handled. Together, the policies configure the behavior for file elevations when standard users request to *run with administrative privileges*.

These policies are:

- Elevation settings policy
- Elevation rules policy

EPM also supports a reusable settings group to store publisher certificates that can be referenced across multiple rules or rules policies.

## Policy conflict handling for Endpoint Privilege Management

✅ Learn about policy conflicts

Except for the following situations, conflicting policies for EPM are handled like any other [policy conflict](../device-configuration/troubleshoot-device-profiles#conflicts).

**Windows elevation settings policy**:

When a device receives two separate elevation settings policies with conflicting values, the EPM client reverts to the default client behavior until the conflict is resolved.

Note

If *Enable Endpoint Privilege Management* is in conflict, the default behavior of the client is to *Enable* EPM.

**Windows elevation rules policy**:

If a device receives two rules targeting the same application, both rules are consumed on the device. When EPM goes to resolve rules that apply to an elevation, it uses the following logic:

- Rules with an *elevation type* of *Deny* always take precedence, and the file elevation is denied.
- Rules deployed to a user take precedence over rules deployed to a device.
- Rules with a hash defined are always deemed the most *specific* rule.
- If more than one rule applies (with no hash defined), the rule with the most defined attributes wins (most *specific*).
- If applying the proceeding logic results in more than one rule, the following order determines the elevation behavior: *User confirmed*, *Elevate as current user*, *Support approved*, and then *Automatic*.

Note

If a rule doesn't exist for an elevation and that elevation was requested through the *Run with elevated access* right-click context menu, then the *Default Elevation Behavior* is used.

## Endpoint Privilege Management and User Account Control

✅ Understand interaction between EPM and User Account Control

Endpoint Privilege Management and Windows built-in user account control (UAC) are separate features with different functionality.

When moving users to run as standard users and utilizing Endpoint Privilege Management, you might choose to change the default UAC behavior for standard users. This change can reduce confusion when an application requires elevation and create a better end user experience. Examine [behavior of the elevation prompt for standard users](/en-us/windows/security/identity-protection/user-account-control/user-account-control-security-policy-settings#user-account-control-behavior-of-the-elevation-prompt-for-standard-users) for more information.

Note

Endpoint Privilege Management doesn't interfere with user account control actions (or UAC) that are run by an Administrator on the device.

## Security recommendations

✅ Understand the most secure way to use EPM

To help ensure a secure deployment of Endpoint Privilege Management, consider these recommendations when configuring elevation behavior and rules.

### Set a secure default elevation response

Set the [default elevation response](manage-elevation-settings#about-windows-elevation-settings-policy) to **Require support approval** or **Deny** rather than **Require user confirmation**. These options ensure that elevation is controlled with predefined rules for known binaries, reducing the risk of users elevating arbitrary or potentially malicious executables.

### Require file path restrictions in all rule types

When [configuring an elevation rule](create-elevation-rules#create-elevation-rules-policy), specify a required **File path**. While the *file path* is optional, it can be an important security check for rules that use automatic elevation or wildcard-based attributes when the path points to a location that standard users can't modify, such as a secured system directory. Use of a secured file location helps prevent executables or their dependent binaries from being tampered with or replaced before elevation.

This recommendation applies to rules created [automatically](create-elevation-rules#automatically-configure-elevation-rules-for-windows-elevation-rules-policy) based on details from the [Elevation report](monitor-reports) or [support approved](manage-support-approvals) request, and for elevation rules that you create [manually](create-elevation-rules#manually-configure-elevation-rules-for-windows-elevation-rules-policy).

Important

Files located on network shares aren't supported and shouldn't be used in rule definitions.

### Differentiate installer and runtime elevation

Be intentional about elevation for installer files versus application runtime. Elevation for installers should be tightly controlled to prevent unauthorized software installations. Runtime elevation should be minimized to reduce the overall attack surface.

### Apply stricter rules to high-risk applications

Use more restrictive elevation rules for applications with broader access or scripting capabilities, such as web browsers and PowerShell. For PowerShell, consider using script-specific rules to ensure only trusted scripts are allowed to run with elevated privileges.

### Start fresh, even when migrating from a third-party product

EPM operates differently to third-party products and as a result, we recommended starting with an audit policy. Then, you can create new rules from reports and take advantage of *support approved* elevation when a file doesn't have a rule but a user needs to elevate that file to get their job done.

## Role-based access controls for Endpoint Privilege Management

✅ Learn how to delegate access to EPM

To manage Endpoint Privilege Management, your account must be assigned an Intune role-based access control (RBAC) role that includes the following permission with sufficient rights to complete the desired task:

- **Endpoint Privilege Management Policy Authoring** – This permission is required to work with policy or data and reports for Endpoint Privilege Management, and supports the following rights:

    - View Reports
    - Read
    - Create
    - Update
    - Delete
    - Assign
- **Endpoint Privilege Management Elevation Requests** - This permission is required to work with support approved elevation requests that are submitted by users for approval, and supports the following rights:

    - View elevation requests
    - Modify elevation requests

You can add this permission with one or more rights to your own custom RBAC roles, or use a built-in RBAC role dedicated to managing Endpoint Privilege Management:

- **Endpoint Privilege Manager** – This built-in role is dedicated to managing Endpoint Privilege Management in the Intune console. This role includes all rights for *Endpoint Privilege Management Policy Authoring* and *Endpoint Privilege Management Elevation Requests*.
- **Endpoint Privilege Reader** - Use this built-in role to view Endpoint Privilege Management policies in the Intune console, including reports. This role includes the following rights:

    - View Reports
    - Read
    - View elevation requests

In addition to the dedicated roles, the following built-in roles for Intune also include rights for *Endpoint Privilege Management Policy Authoring*:

- **Endpoint Security Manager** - This role includes all rights for *Endpoint Privilege Management Policy Authoring* and *Endpoint Privilege Management Elevation Requests*.
- **Read Only Operator** - This role includes the following rights:

    - View Reports
    - Read
    - View elevation requests

For more information, see [Role-based access control for Microsoft Intune](../fundamentals/role-based-access-control/overview).

## EpmTools PowerShell module

✅ Learn how to use the EPM PowerShell module

Each device that receives Endpoint Privilege Management policies installs the EPM Microsoft Agent to manage those policies. The agent includes the *EpmTools* PowerShell module, a set of cmdlets that you can import to a device. You can use the cmdlets from EpmTools to:

- Diagnose and troubleshoot issues with Endpoint Privilege Management.
- Get File attributes directly from a file or application for which you want to build a detection rule.

### Install the EpmTools PowerShell module

The EPM Tools PowerShell module is available from any device that has received EPM policy. To import the EpmTools PowerShell module:

```powershell
Import-Module 'C:\Program Files\Microsoft EPM Agent\EpmTools\EpmCmdlets.dll'
```

Note

Windows on Arm64 requires the use of Windows PowerShell x64.

Following are the available cmdlets:

- **Get-Policies**: Retrieves a list of all policies received by EPM for a given 'PolicyType' ('ElevationRules' or 'ClientSettings').
- **Get-DeclaredConfiguration**: Retrieves a list of WinDC documents that identify the policies targeted to the device.
- **Get-DeclaredConfigurationAnalysis**: Retrieves a list of WinDC documents of type MSFTPolicies and checks if the policy is already present in Epm Agent (Processed column).
- **Get-ElevationRules**: Query the EpmAgent lookup functionality and retrieves rules given lookup and target. Lookup is supported for FileName and CertificatePayload.
- **Get-ClientSettings**: Process all existing client settings policies to display the effective client settings used by EPM.
- **Get-FileAttributes**: Retrieves File Attributes for an .exe file and extracts its Publisher and CA certificates to a set location that can be used to populate Elevation Rule Properties for a particular application.

For more information about each cmdlet, review the **readme.md** file from the *EpmTools* folder on the device.