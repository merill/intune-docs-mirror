---
layout: Conceptual
title: Remote control security privacy - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/remote-control/security-and-privacy-for-remote-control
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
description: Get security and privacy information for remote control in Configuration Manager.
ms.date: 2017-04-23T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: article
ms.collection: tier3
locale: en-us
document_id: bf694edd-62a1-3293-3c56-49b392a3f223
document_version_independent_id: 9b21d943-c296-f4ed-f6e8-a10950738e63
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/clients/manage/remote-control/security-and-privacy-for-remote-control.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/clients/manage/remote-control/security-and-privacy-for-remote-control
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/clients/manage/remote-control/security-and-privacy-for-remote-control.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: af0ad1cd-0bc6-8425-2654-0e3baaf36b6a
---

# Remote control security privacy - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This topic contains security and privacy information for remote control in Configuration Manager.

## Security best practices for remote control

Use the following security best practices when you manage client computers by using remote control.

| Security best practice | More information |
| --- | --- |
| When you connect to a remote computer, do not continue if NTLM instead of Kerberos authentication is used. | When Configuration Manager detects that the remote control session is authenticated by using NTLM instead of Kerberos, you see a prompt that warns you that the identity of the remote computer cannot be verified. Do not continue with the remote control session. NTLM authentication is a weaker authentication protocol than Kerberos and is vulnerable to replay and impersonation. |
| Do not enable Clipboard sharing in the remote control viewer. | The Clipboard supports objects such as executable files and text and could be used by the user on the host computer during the remote control session to run a program on the originating computer. |
| Do not enter passwords for privileged accounts when remotely administering a computer. | Software that observes keyboard input could capture the password. Or, if the program that is being run on the client computer is not the program that the remote control user assumes, the program might be capturing the password. When accounts and passwords are required, the end user should enter them. |
| Lock the keyboard and mouse during a remote control session. | If Configuration Manager detects that the remote control connection is terminated, Configuration Manager automatically locks the keyboard and mouse so that a user cannot take control of the open remote control session. However, this detection might not occur immediately and does not occur if the remote control service is terminated. Select the action **Lock Remote Keyboard and Mouse** in the **ConfigMgr Remote Control** window. |
| Do not let users configure remote control settings in Software Center. | Do not enable the client setting **Users can change policy or notification settings in Software Center** to help prevent users from being spied on. If one user changes it, it can allow a different user on the same machine to be viewed remotely. **This setting is for the computer, not for the logged-on user**. |
| Enable the **Domain** Windows Firewall profile. | Enable the client setting **Enable remote control on clients Firewall exception profiles** and then select the **Domain** Windows Firewall for intranet computers. |
| If you log off during a remote control session and log on as a different user, ensure that you log off before you disconnect the remote control session. | If you do not log off in this scenario, the session remains open. |
| Do not give users local administrator rights. | When you give users local administrator rights, they might be able to take over your remote control session or compromise your credentials. |
| Use either Group Policy or Configuration Manager to configure Remote Assistance settings, but not both. | You can use Configuration Manager and Group Policy to make configuration changes to the Remote Assistance settings. When Group Policy is refreshed on the client, by default, it optimizes the process by changing only the policies that have changed on the server. Configuration Manager changes the settings in the local security policy, which might not be overwritten unless the Group Policy update is forced. Setting policy in both places might lead to inconsistent results. Choose one of these methods to configure your Remote Assistance settings. |
| Enable the client setting **Prompt user for Remote Control permission**. | Although there are ways around this client setting that prompts a user to confirm a remote control session, enable this setting to reduce the chance of users being spied upon while working on confidential tasks. In addition, educate users to verify the account name that is displayed during the remote control session and disconnect the session if they suspect that the account is unauthorized. |
| Limit the Permitted Viewers list. | Local administrator rights are not required for a user to be able to use remote control. |

### Security issues for remote control

Managing client computers by using remote control has the following security issues:

- Do not consider remote control audit messages to be reliable.

    If you start a remote control session and then log on by using alternative credentials, the original account sends the audit messages, not the account that used the alternative credentials.

    Audit messages are not sent if you copy the binary files for remote control rather than install the Configuration Manager console, and then run remote control at the command prompt.

## Privacy information for remote control

Remote control lets you view active sessions on Configuration Manager client computers and potentially view any information stored on those computers. By default, remote control is not enabled.

Although you can configure remote control to provide prominent notice and get consent from a user before a remote control session begins, it can also monitor users without their permission or awareness. You can configure View Only access level so that nothing can be changed on the remote control, or Full Control. The account of the connecting administrator is displayed in the remote control session, to help users identify who is connecting to their computer.

By default, Configuration Manager grants the local Administrators group Remote Control permissions.

Before you configure remote control, consider your privacy requirements.