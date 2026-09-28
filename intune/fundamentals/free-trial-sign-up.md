---
layout: Conceptual
title: Sign Up for Microsoft Intune Free Trial Setup Guide - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/fundamentals/free-trial-sign-up
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
ms.subservice: fundamentals
description: Sign up for a Microsoft Intune free trial and configure your tenant. Learn the setup process, prerequisites, and how to configure domain names. Start evaluating Intune today.
ms.date: 2026-01-27T00:00:00.0000000Z
ms.topic: how-to
ms.reviewer: tycast
locale: en-us
document_id: 244b9ccf-0339-2be6-56df-6c57a9394877
document_version_independent_id: 244b9ccf-0339-2be6-56df-6c57a9394877
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/fundamentals/free-trial-sign-up.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: fundamentals/free-trial-sign-up
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/fundamentals/free-trial-sign-up.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/57eae307-c3a1-4cac-b645-1a899934bac8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/ee561821-1ac7-45a8-9409-6ba5eb7a5b97
platformId: a9f1198f-774f-dc4d-d4df-d72c4f99809c
---

# Sign Up for Microsoft Intune Free Trial Setup Guide - Microsoft Intune | Microsoft Learn

Sign up for a Microsoft Intune free trial to evaluate mobile device management for your organization. In this article, you learn how to sign up for a free trial, create a new tenant, set up Intune, and prepare your environment for testing.

This article is [part of an Evaluate and Try series](try-overview) that helps you evaluate Microsoft Intune's capabilities.

When you complete the signup process, you automatically create a new tenant. A tenant is a dedicated instance of Microsoft Entra ID that hosts your Intune subscription. After creating the tenant, you can add users and groups, and assign licenses to users.

The free trial is an Enterprise Mobility + Security (EMS) subscription, which includes Microsoft Entra ID P1 or P2 and Microsoft Intune. After the free trial is configured, you can [confirm your free trial licenses](licensing#confirm-your-licenses).

You also get access to the following admin centers, which are used by Intune admins:

- **Microsoft Intune admin center** ([https://intune.microsoft.com](https://intune.microsoft.com/)) - Intune admins use this admin center to manage devices, apps, and policies. You can explore the [Intune features and capabilities](what-is-intune).
- **Microsoft 365 admin center** (https://admin.microsoft.com) - Add and manage users, if you don't use Microsoft Entra ID for this task. You can also manage other aspects of your account, including billing and support.

## Prerequisites

Before you set up Microsoft Intune, review the following requirements:

![](../media/icons/16/devices.svg)**Device platform requirements**

> 
> - [Supported operating systems and browsers](ref-supported-platforms)
> 

![](../media/icons/16/network-connectivity.svg)**Network and connectivity requirements**

> 
> - [Network endpoints for Microsoft Intune](endpoints)
> 

Important

On October 15, 2024, Microsoft began enforcement of the Azure sign-in requirement to use multifactor authentication (MFA). When enforced, MFA is required for all users who sign-in to Intune admin center regardless of any roles they have or don't have. The MFA requirements also apply to services that you access through the admin center, like Windows 365 Cloud PC, and to use of the Microsoft Azure portal and Microsoft Entra admin center. MFA requirements don't apply to end users who access applications, websites, or services hosted on Azure where those users don't sign-in to the admin center.

The requirement to sign-in using MFA applies to all Intune subscriptions, including free trial subscriptions. The prerequisites and process required to configure MFA depend on the MFA method you choose to use for your tenant. Shortly after MFA is enabled for a tenant, subsequent sign-in attempts require the user to complete setup for using the configured MFA solution.

To learn more about the MFA requirement, see [Planning for mandatory multifactor authentication for Azure and admin portals](/en-us/entra/identity/authentication/concept-mandatory-multifactor-authentication) in the Microsoft Entra documentation.

In the Microsoft Entra planning article, you'll find guidance and resources to help you [Prepare for multifactor authentication](/en-us/entra/identity/authentication/concept-mandatory-multifactor-authentication#prepare-for-multifactor-authentication), including methods to configure MFA including but not limited to:

- Conditional Access policies
- The *MFA Wizard for Microsoft Entra ID* from the Microsoft 365 admin center
- Entra ID *security defaults*

## Sign up for a free trial

The Intune trial is free for 30 days. If you have an existing work or school account, you can **sign in** with that account and add Intune to your subscription. Or, you can **sign up** for a new account. If you sign up for a new account, you can't combine the new account with an existing work or school account.

To sign up for the Microsoft Intune free trial, use the following steps:

1. Go to the [Microsoft Intune Plan 1 Trial setup account page](https://go.microsoft.com/fwlink/?linkid=2019088).
2. Enter your email address and select **Next**.

    If you already have an account set up with another Microsoft service using your email address, you can sign in with this same account for the Intune trial. Or, you can create a new account. These steps assume you're creating a new account.

    [![Screenshot of the Microsoft Intune set up account page for a free trial- Enter email.](media/free-trial-sign-up/sign-up-for-intune-01.png)](media/free-trial-sign-up/sign-up-for-intune-01.png#lightbox)
3. Select **Set up account** to create a new account.

    [![Screenshot of the Microsoft Intune set up account page for a free trial - Set up account.](media/free-trial-sign-up/sign-up-for-intune-02.png)](media/free-trial-sign-up/sign-up-for-intune-02.png#lightbox)
4. Add your name, phone number, company name, company size, and region. Review the remaining information and select **Next**.

    [![Screenshot of the Microsoft Intune set up account page for a free trial - Add account details.](media/free-trial-sign-up/sign-up-for-intune-03.png)](media/free-trial-sign-up/sign-up-for-intune-03.png#lightbox)
5. Select **Send verification code** to verify the phone number you added.

    [![Screenshot of the Microsoft Intune set up account page for a free trial -  Send verification code.](media/free-trial-sign-up/sign-up-for-intune-04.png)](media/free-trial-sign-up/sign-up-for-intune-04.png#lightbox)
6. Enter the verification code you receive on your mobile device, and then select **Verify**.

    [![Screenshot of the Microsoft Intune set up account page for a free trial -  Verify code.](media/free-trial-sign-up/sign-up-for-intune-05.png)](media/free-trial-sign-up/sign-up-for-intune-05.png#lightbox)
7. Add your **Username** and **Domain name** for your trial that represents your business or organization. Your name added before `.onmicrosoft.com`. Select **Save** to check availability. Select **Next** to continue. If you like, you can change this domain name to your custom domain name later.

    [![Screenshot of the Microsoft Intune set up account page for a free trial -  Sign in.](media/free-trial-sign-up/sign-up-for-intune-06.png)](media/free-trial-sign-up/sign-up-for-intune-06.png#lightbox)
8. Add a payment method. Your card is only used for verification purposes and won't be charged unless you buy something.

    [![Screenshot of the Microsoft Intune set up account page for a free trial -  Add payment method.](media/free-trial-sign-up/sign-up-for-intune-06a.png)](media/free-trial-sign-up/sign-up-for-intune-06a.png#lightbox)
9. After your account is created, you see your user name. Use this user name to sign in to Intune. You also receive an email message that includes your account information at the email address that you provided during the sign-up process. This email confirms your subscription is active.

    [![Screenshot of the Microsoft Intune set up account page for a free trial -  Confirmation details.](media/free-trial-sign-up/sign-up-for-intune-07.png)](media/free-trial-sign-up/sign-up-for-intune-07.png#lightbox)

    Note

    If you select **Get Started**, the **Microsoft 365 admin center** opens. If you select **Manage your subscription**, you see **Your products** and can view details about your Microsoft Intune Trial subscription.

## Sign in to the Intune admin center and create your admin team

If you're not already signed in to the admin center, sign in now:

1. Open your web browser and go to **https://intune.microsoft.com**.
2. Use the same user ID that you used to sign in. The user ID looks similar to `yourID@yourdomain.onmicrosoft.com`.

    [![Screenshot of the Microsoft Intune admin center sign in page.](media/free-trial-sign-up/azure-portal-signin.png)](media/free-trial-sign-up/azure-portal-signin.png#lightbox)

To get the user ID, refer to the email message you received after signing up for the trial.

Tip

When working with Microsoft Intune, you get better results by using a browser in regular mode, rather than private mode.

### Assign built-in roles to your admin team

Intune uses role-based access control (RBAC) to manage permissions.

The account that creates the subscription is assigned the Microsoft Entra [Global Administrator role](/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator). This built-in role is a privileged Microsoft Entra role and has more permissions than needed for most Intune tasks.

We suggest that you sign out of the Global Administrator role account and sign in with an account that's needed for the Intune task.

There are built-in roles specifically created and used to manage Intune. Your goal is to use the least privilege role that can perform the necessary tasks. For this series of articles, the following built-in roles are needed:

| Role | Description |
| --- | --- |
| **[Domain Name Administrator role](/en-us/entra/identity/role-based-access-control/permissions-reference#domain-name-administrator)** | A Microsoft Entra role that can add and verify custom domain names in your tenant. This role is only used if you configure a custom domain name in this series, which is optional. |
| **[Intune Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)** | A Microsoft Entra role that has full access to all features in Microsoft Intune. You can use this account to set up Intune and set up Automatic Enrollment for Windows devices. |
| **[User Administrator](/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator)** | A Microsoft Entra role that can create and manage user accounts and groups in Intune and Microsoft 365. |
| **[Application Manager](role-based-access-control/ref-built-in-roles#application-manager)** | An Intune role that can add and manage apps in Intune. |
| **[Intune Role Administrator](role-based-access-control/ref-built-in-roles#intune-role-administrator)** | An Intune role that can create and manage custom roles and add users to Intune roles. |
| **[Policy and Profile Manager](role-based-access-control/ref-built-in-roles#policy-and-profile-manager)** | An Intune role that can create and manage Intune policies, including compliance, device configuration, and most enrollment policies. |

If many admins are testing Intune, then assign their accounts to only the roles they need. For example, if an admin is only responsible for adding and managing apps, assign that admin only to the **Application Manager** role.

- To assign built-in roles to your admin team, see [Assign Microsoft Intune roles for role-based access control](role-based-access-control/assign-role).

For more information about Intune built-in roles, see:

- [Role-based access control (RBAC) with Microsoft Intune](role-based-access-control/overview)
- [Built-in role permissions for Microsoft Intune](role-based-access-control/ref-built-in-roles)

## Confirm the MDM authority

By default, the Mobile Device Management (MDM) authority is set when you create your free trial. You can confirm that the MDM authority is set by using the following steps:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) as the **Intune Administrator** Microsoft Entra role
2. Select **Tenant administration**.
3. View the tenant details. The **MDM authority** should be set to **Microsoft Intune**.

If you see an orange banner that states you didn't set the MDM authority, you can activate it now. The mobile device management (MDM) authority setting determines how you manage your devices. Set the MDM authority before users can enroll devices for management.

### Set the MDM authority to Intune

1. If the MDM authority isn't set, sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) as the **Intune Administrator** Microsoft Entra role.
2. Select the orange banner to open the **Mobile Device Management Authority** setting. The orange banner appears only if you didn't set the MDM authority.

    You can confirm the MDM Authority is set using the steps in Confirm the MDM authority (in this article).
3. If your MDM Authority isn't set, under **Choose MDM Authority**, set your MDM authority to **Intune MDM Authority**.

    [![Screenshot of the Microsoft Intune choose MDM Authority page.](media/free-trial-sign-up/choose-mdm-authority.png)](media/free-trial-sign-up/choose-mdm-authority.png#lightbox)

For more information about the MDM authority, see [Set the mobile device management authority](setup-mdm-authority).

## Configure your custom domain name (optional)

If your organization has its own custom domain that you want to use without **.onmicrosoft.com**, you can change it in the Microsoft 365 admin center. Use the following steps to add, verify, and configure your custom domain name.

Important

You can't rename or remove the initial **onmicrosoft.com** part of the domain name. However, you can add, verify, or remove *custom* domain names used with Intune to keep your business identity clear. For more information, see [Configure a custom domain name](configure-custom-domain).

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) as the **Domain Name Administrator** Microsoft Entra role.
2. In the navigation pane, choose **Setup**.
3. In the **Sign-in and security** section, select **Get your custom domain set up**.
4. Select **Get started** to set up your custom domain.
5. Enter your domain name and select **Use this domain**.

    [![Screenshot of Microsoft 365 admin center - Add domain.](media/free-trial-sign-up/domain-custom-add.png)](media/free-trial-sign-up/domain-custom-add.png#lightbox)
6. Verify that you're the owner of the domain that you entered. Select the method that you'll use to verify your domain.

    ![Screenshot of Microsoft 365 admin center - Verify domain ownership.](media/free-trial-sign-up/domain-custom-verify.png)

    Note

    For TXT record verification details, see [Create DNS records at any DNS hosting provider for Microsoft 365](/en-us/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider).