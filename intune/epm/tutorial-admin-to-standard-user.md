---
layout: Conceptual
title: Use Endpoint Privilege Management to transition users from administrator to standard user - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/epm/tutorial-admin-to-standard-user
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
description: Understand the steps and phases for using Endpoint Privilege Management to transition users from administrators to standard users.
ms.date: 2025-09-10T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: a78a470b-1eef-e945-0c5b-08a29d7c2390
document_version_independent_id: a78a470b-1eef-e945-0c5b-08a29d7c2390
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/epm/tutorial-admin-to-standard-user.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: epm/tutorial-admin-to-standard-user
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/epm/tutorial-admin-to-standard-user.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: 79287083-21c7-8bd0-94f4-c4831a1236b9
---

# Use Endpoint Privilege Management to transition users from administrator to standard user - Microsoft Intune | Microsoft Learn

A common scenario for customers who want to use Endpoint Privilege Management is to reduce the number of local administrators in their environment. This scenario adheres to the Zero Trust principle of least privilege. This document steps through the steps a customer could follow to use EPM to move users from administrators to standard users with minimal disruption.

## Phase 1: Auditing

Regardless of whether you're migrating from another endpoint privilege management product or starting fresh, we recommend enabling auditing as the first step. Enabling auditing enables the EPM client and devices to send diagnostic data to Intune, where it can be viewed in various reports. Gathering this elevation data provides insights into which processes users are seeking to elevate, and help to identify common patterns. Ideally, these align to your personas, such as developers, IT support technicians, etc. The deployment of this policy for auditing is seamless, and can be targeted to a group of users or devices of your choosing, as per any regular Intune policy assignment.

Note

Once enabled, usage data can take 24 hrs to be returned and for the Intune portal reports to be updated. Depending on usage patterns, you might want to view reporting data over a period of many weeks to gather a better understanding of your environment.

**Steps to create the policy:**

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint Security** &gt; **Endpoint Privilege Management** &gt; **Policies**
3. Select **Create Policy**. Enter the following details:
    - **Platform:** Windows
    - **Profile:** Elevation settings policy
4. Select **Create**
5. Provide name for the policy, such as: EPM settings policy – Audit only
6. Select **Next**
7. Expand the 'Privilege management elevation client settings' section and ensure the following values are set:
    - **Endpoint Privilege Management:** Enabled
    - **Default elevation response:** Not Configured
    - **Send elevation data for reporting:** Yes
    - **Reporting scope:** Diagnostic data and all endpoint elevations
8. Select **Next**
9. Leave the **Scope tags** and select **Next**
10. Add a group of devices or users that you want to target the policy to
11. Select **Next**
12. Select **Create** to create the policy

**To confirm that the rule is functioning as expected:**

- Sign in to the Windows device with the standard user credentials.
- **Start** &gt; **Run** &gt; **Services.msc** &gt; Ok
- Check that the *'Microsoft EPM Agent Service'* is present, Running, and set to Automatic startup type.
- Close the Services snap-in.
- **Start** &gt; **Run** &gt; `C:\Program Files\` &gt; Ok
- Verify that there's a folder called: *Microsoft EPM Agent*

**After 24 hrs or more have passed:**

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint Security** &gt; **Endpoint Privilege Management** &gt; **Reports**
3. Select **Elevation report**
4. Review the details of the elevation report

Identify groups of users (ideally aligning with the personas you identified earlier) who have similar elevation requirements. Identifying both usage patterns and user groups assists with subsequent steps.

Tip

This report includes some default Windows processes in the File column (for example `C:\Windows\System32\Dism\dismhost and c:\Windows\System32\conhost.exe`) which can be ignored.

## Phase 2: Persona identification

Using user personas in the design of Microsoft Intune Endpoint Privilege Management (EPM) policies is a strategic way to align elevation settings and rules with real-world user needs.

### What Are User Personas in EPM?

User personas are data-driven representations of different user types within your organization. Each persona reflects a group of users with similar roles, responsibilities, and application needs.

Example persona mapping:

| Persona Type | Example Roles | Elevation Strategy | Default Elevation |
| --- | --- | --- | --- |
| Power Users | IT Support Technicians, IT Power Users | Automatic elevation for defined rules | Deny all requests |
| Developers | Engineering | Automatic elevation for defined low risk apps; User justified for higher risk apps | Support Approved |
| Standard Users | Finance, HR | Automatic elevation for defined rules | Deny all requests or support approved |

### How do personas help design elevation settings and rules?

Mapping out the user needs allows you to define elevation strategy for each user cohort.

## Phase 3: Create rules

EPM rules consist of two fundamental elements: a detection and an elevation action.

Detections are defined as the set of attributes used to identify an application or binary. These attributes include file name, file version, and signature properties. Elevation actions are the resulting elevation that occurs after an application or binary is detected.

### Best practices

- Use strong attributes or multiple attributes to increase detection strength.
- Either a file hash or certificate is mandatory.

For more security recommendations, see [Security Recommendations](deployment-planning#security-recommendations).

### Steps to create a rule using elevation report data

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint Security** &gt; **Endpoint Privilege Management** &gt; **Policies**
3. Select **Elevation report**
4. Select an application or process (for example. `C:\Program Files\Notepad++\`)
5. Select **Create a rule with these details**:
    - Create a new policy
    - **Type:** User-confirmed
    - **Child process behavior:** Require rule to elevate
    - **Require the same file path as this elevation:** selected
6. Select **OK**
7. Provide a Policy name (for example `EPM rule – Notepad++ User Confirmed`)
8. Select **Yes**
9. Navigate to the list of EPM policies and select the policy
10. Under **Assignments**, select **Edit**
11. Select **Add groups**
12. Assign to a group (for example Developers)
13. **Select**, **Review**, and **Save**

For more details on creating a rule, see [Create elevation rules](create-elevation-rules).

### Confirm the rule is functioning

- Sign in to the Windows device with standard user credentials.
- Right-click the application (for example `Notepad++`) and select **'Run with elevated access'**
- On the Endpoint Privilege Management pop-up, select **Continue**
- Verify the application launches with elevated permissions

## Phase 4: Remove local admin rights

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Endpoint Security** &gt; **Account protection**
3. Select Create Policy:

    - **Platform:** Windows
    - **Profile:** Local user group membership
4. Provide name for the policy (for example `Remove local admin rights (developers)`)
5. Select Add:

    - **Local group**: Administrators
    - **Group and user action**: Add (Replace)
    - **User selection type:** Manual
6. Select **users(s)**
7. Add the two Security Identifiers (SIDs) for:

    - Global Administrator
    - Microsoft Entra Joined Device Local Administrator

> 
> Use Lusrmgr.msc on an Entra-joined device to find SIDs starting with S-1-12-1-
8. Assign to a group (for example `Developers`)
9. Select **Save**

For more information on the Local Users and Groups profiles, see [Account protection](../device-configuration/endpoint-security/account-protection)

## Phase 5: Monitoring

- Regularly review elevation reports
- Add unmanaged elevations to rules or deny them
- Monitor support-approved requests for delays or patterns
- Update rules when file versions or certs change
- Retire or tighten outdated rules