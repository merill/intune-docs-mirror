---
layout: Conceptual
title: Windows Firewall policies for Endpoint Protection - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/create-windows-firewall-policies
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
description: Learn how to create and deploy firewall policies for Endpoint Protection in System Center 2012 Configuration Manager.
ms.date: 2026-03-19T00:00:00.0000000Z
ms.subservice: protect
ms.topic: install-set-up-deploy
ms.collection: tier3
locale: en-us
document_id: 03bde475-8ae9-0a93-0392-40a48e1727f9
document_version_independent_id: 08d23476-1046-8365-f1bd-7c1025d474a5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/protect/deploy-use/create-windows-firewall-policies.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/protect/deploy-use/create-windows-firewall-policies
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/protect/deploy-use/create-windows-firewall-policies.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 166b98d2-fd15-db98-9044-6358eb40219e
---

# Windows Firewall policies for Endpoint Protection - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Firewall policies for Endpoint Protection in Configuration Manager let you perform basic Windows Firewall configuration and maintenance tasks on client computers in your hierarchy.

You can use Windows Firewall policies to perform the following tasks:

- Control whether Windows Firewall is turned on or off.
- Control whether incoming connections are allowed to client computers.
- Control whether users are notified when Windows Firewall blocks a new program.

### Prerequisites

- A site system server with the Endpoint Protection role installed.
- An Endpoint Protection Client Setting with **Manage Endpoint Protection client on client computers** set to **Yes**.

Note

It is not necessary to have **Install Endpoint Protection client** enabled in the client setting.

## Create the policy

1. In the Configuration Manager console, click **Assets and Compliance**.
2. In the **Assets and Compliance** workspace, expand **Endpoint Protection**, and then click **Windows Firewall Policies**.
3. On the **Home** tab, in the **Create** group, click **Create Windows Firewall Policy**.
4. On the **General** page of the **Create Windows Firewall Policy Wizard**, specify a name and an optional description for this firewall policy, and then click **Next**.
5. On the **Profile Settings** page of the wizard, configure the following settings for each network profile:

    - **Enable Windows Firewall**

        If **Enable Windows Firewall** is not enabled, the other settings on this page of the wizard are unavailable.
    - **Block all incoming connections, including those in the list of allowed programs**
    - **Notify the user when Windows Firewall blocks a new program**
6. On the **Summary** page of the wizard, review the actions to be taken, and then complete the wizard.
7. Verify that the new Windows Firewall policy is displayed in the **Windows Firewall Policies** list.

## To deploy a Windows Firewall policy

1. In the Configuration Manager console, click **Assets and Compliance**.
2. In the **Assets and Compliance** workspace, expand **Endpoint Protection**, and then click **Windows Firewall Policies**.
3. In the **Windows Firewall Policies** list, select the Windows Firewall policy that you want to deploy.
4. On the **Home** tab, in the **Deployment** group, click **Deploy**.
5. In the **Deploy Windows Firewall Policy** dialog box, specify the collection to which you want to assign this Windows Firewall policy, and specify an assignment schedule. The Windows Firewall policy evaluates for compliance by using this schedule and the Windows Firewall settings on clients to reconfigure to match the Windows Firewall policy.
6. Click **OK** to close the **Deploy Windows Firewall Policy** dialog box and to deploy the Windows Firewall policy.

    Important

    When you deploy a Windows Firewall policy to a collection, this policy is applied to computers in a random order over a 2 hour period to avoid flooding the network.