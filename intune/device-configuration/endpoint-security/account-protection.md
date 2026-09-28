---
layout: Conceptual
title: Manage account protection settings with endpoint security policies in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/account-protection
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
description: Use Microsoft Intune endpoint security account protection policies to protect the identity and accounts of users.
ms.date: 2025-10-01T00:00:00.0000000Z
ms.topic: article
ms.reviewer: juidaewo
locale: en-us
document_id: 88302c01-2e60-1818-752a-70ed14e5b6ad
document_version_independent_id: 88302c01-2e60-1818-752a-70ed14e5b6ad
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/endpoint-security/account-protection.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/endpoint-security/account-protection
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/endpoint-security/account-protection.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/e0ffb20c-01c6-407b-a9bd-29111652a1dc
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/3904bce4-d817-48cf-85fd-b6146fca83b7
platformId: c8b9f980-75fb-c0d1-260f-5f024ff695bc
---

# Manage account protection settings with endpoint security policies in Microsoft Intune - Microsoft Intune | Microsoft Learn

Use Intune endpoint security policies for account protection to protect the identity and accounts of your users and manage the built-in group memberships on devices.

Important

In July 2024, the following Intune profiles for identity protection and account protection were deprecated and replaced by a new consolidated profile named *Account protection*. This newer profile is found in the account protection policy node of endpoint security, and is the only profile template that remains available to create new policy instances for identity and account protection. The settings from this new profile are also available through the settings catalog.

Any instances of the following older profiles that you have created remain available to use and edit:

- **Identity protection** – previously available from *Devices* &gt; *Configuration* &gt; *Create* &gt; *New Policy* &gt; *Windows 10 and later* &gt; *Templates* &gt; *Identity Protection*
- **Account protection (Preview)** – previously available from *Endpoint Security* &gt; *Account protection* &gt; *Windows 10 and later* &gt; *Account protection (Preview)*

Find the endpoint security policies for Account protection under *Manage* in the **Endpoint security** node of the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).

## Prerequisites for Account protection profiles

- To support the *Account protection* profile, devices must run Windows.
- To support the *Local user group membership* profile, devices must run Windows 10 20H2 or later, or Windows 11.
- To support the \*Local admin password solution (Windows LAPS), see [Prerequisites](../../device-security/laps/overview#prerequisites) in *Microsoft Intune support for Windows LAPS*.

Important

On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

## Role-based access controls (RBAC)

For guidance on assigning the right level of permissions and rights to manage Intune account protection profiles, see [Role-based access control for endpoint security](manage-policies#role-based-access-control-for-endpoint-security).

## Account protection profiles

To configure account protection profiles, in the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) go to **Endpoint Security** &gt; **Account protection** &gt; **Create Policy**\*. For *Platform* select **Windows**, and then choose from the following Profiles:

Profiles:

- **Account protection** – Settings for account protection policies help you to protect user credentials. The account protection policy focuses on *device-scoped* and *user-scoped* settings for Windows Hello for Business, and on Credential Guard. Credential Guard is part of Windows identity and access management.

    - *Windows Hello for Business* replaces passwords with strong two-factor authentication on PCs and mobile devices.
    - *Credential Guard* helps protect credentials and secrets that you use with your devices.

    To learn more, see [Identity and access management](/en-us/windows/security/identity-protection) in the Windows identity and access management documentation.

    The settings in this profile are also available in the [Settings catalog](../settings-catalog/).
- **Local admin password solution (Windows LAPS)** - Use this profile to configure Windows LAPS on devices. Windows LAPS allows for the management of a single local administrator account per device. Intune policy can specify which local admin account it applies to by use of the policy setting *Administrator Account Name*.

    For more information in using Intune to manage Windows LAPS, see:

    - Learn about [Intune support for Windows LAPS](../../device-security/laps/overview).
    - [Manage LAPS policy](../../device-security/laps/deploy-policy)
- **Local user group membership** – Use this profile to add, remove, or replace members of the built-in local groups on Windows devices. For example, the Administrators local group has broad rights. You can use this policy to edit the Admin group's membership to lock it down to a set of exclusively defined members.

    Use of this profile is detailed in the following section, Manage local groups on Windows devices.

## Manage local groups on Windows devices

Use the *Local user group membership* profile to manage the users that are members of the built-in local groups on devices that run Windows 10 [20H2 and later](/en-us/windows/client-management/mdm/policy-csp-localusersandgroups#localusersandgroups-policies), and Windows 11 devices.

Tip

To learn more about support for managing administrator privileges using Microsoft Entra groups, see [Manage administrator privileges using Microsoft Entra groups](/en-us/azure/active-directory/devices/assign-local-admin#manage-administrator-privileges-using-microsoft-entra-groups-preview) in the Microsoft Entra documentation.

Note

Microsoft Entra groups deployed to a device with this policy don't apply to remote desktop connections. To control remote desktop permissions for Microsoft Entra joined devices, you need to add the individual user's SID to the appropriate group.

### Configure the profile

Use the *Local user group membership* profile to manage the local group membership on devices through the Windows [Policy CSP - LocalUsersAndGroups](/en-us/windows/client-management/mdm/policy-csp-localusersandgroups?WT.mc_id=Portal-fx). The CSP documentation includes more details on how configurations apply, and an FAQ about the use of the CSP.

When you configure this profile, on the *Configuration settings* page you can create multiple rules to manage which built-in local groups you want to change, the group action to take, and the method to select the users.

![Screen shot of the Configuration settings page for configuring the profile.](media/account-protection/create-profile.png)

The following are the configurations you can make:

- **Local group**: Select one or more groups from the drop-down. These groups all apply the same *Group and user action* to the users you assign. You can create more than one grouping of local groups in a single profile and assign different actions and groups of users to each grouping of local groups.

Note

The list of local groups is limited to the six built-in local groups which are guaranteed to be evaluated at logon, as referenced in the [How to manage the local administrators group on Microsoft Entra joined devices](/en-us/azure/active-directory/devices/assign-local-admin#manage-administrator-privileges-using-microsoft-entra-groups-preview) documentation.

- **Group and user action**: Configure the action to apply to the selected groups. This action applies to the users you select for this same action and grouping of local accounts. Actions you can select include:

    - **Add (Update)**: Adds members to the selected groups. The group membership for users that aren't specified by the policy aren't changed.
    - **Remove (Update)**: Remove members from the selected groups. The group membership for users that aren't specified by the policy aren't changed.
    - **Add (Replace)**: Replace the members of the selected groups with the new members you specify for this action. This option works in the same way as a Restricted Group and any group members that aren't specified in the policy are removed.

Caution

If the same group is configured with both a Replace and Update action, the Replace action wins. This is not considered a conflict. Such a configuration can occur when you deploy multiple policies to the same device, or when this CSP is also configured by use of Microsoft Graph.
- **User selection type**: Choose how to select users. Options include:

    - **Users**: Select the users and user groups from Microsoft Entra ID. (Supported for Microsoft Entra joined devices only).
    - **Manual**: Specify Microsoft Entra users and groups manually, by username, domain\username, or the groups security identifier (SID). (Supported for Microsoft Entra joined and Microsoft Entra hybrid joined devices).
- **Selected user(s)**: Depending on your selection for *User selection type*, use one of the following options:

    - **Select user(s)**: Select the users and user groups from Microsoft Entra.
    - **Add user(s)**: This option opens the **Add users** pane where you can then specify one or more user identifiers as they appear on a device. You can specify the user by *security identifier (SID)*, *Domain\username*, or by *Username*.

        ![Screen shot of the Add users page in the Intune admin center.](media/account-protection/add-user.png)

Choosing the Manual option can be helpful in scenarios where you want to manage your on-premises Active Directory users from Active Directory to a local group for a Microsoft Entra hybrid joined device. The supported formats of identifying the user selection in order of most to least preferred is through the SID, domain\username, or member's username. Values from Active Directory must be used for hybrid joined devices, while values from Microsoft Entra ID must be used for Microsoft Entra join. Microsoft Entra group SIDs can be obtained using [Graph API for Groups](/en-us/graph/api/resources/group?view=graph-rest-1.0#json-representation&amp;preserve-view=true).

### Conflicts

If policies create a conflict for a group membership, the conflicting settings from each policy aren't sent to the device. Instead, the conflict is reported for those policies in the Microsoft Intune admin center. To resolve the conflict, reconfigure one or more policies.

### Reporting

As devices check in and apply the policy, the admin center displays the status of the devices and users as successful or in error.

Because the policy can contain multiple rules, consider the following points:

- When Intune processes the policy for devices, the per-setting status view displays a status for the group of rules as if it's a single setting.
- Each rule in the policy that results in an error is skipped, and not sent to devices.
- Each rule that is successful is sent to devices to be applied.