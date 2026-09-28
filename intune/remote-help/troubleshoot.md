---
layout: Conceptual
title: Troubleshoot and monitor Remote Help for Microsoft Intune. - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/remote-help/troubleshoot
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: lenewsad
ms.author: lanewsad
ms.collection:
- M365-identity-device-management
ms.subservice: suite
description: Use the troubleshooting and monitoring information for Remote Help with Microsoft Intune to ensure healthy and successful deployment.
ms.date: 2026-08-13T00:00:00.0000000Z
ms.topic: how-to
ai-usage: ai-assisted
ms.custom: msecd-doc-authoring-1023
ms.reviewer: Karawang
locale: en-us
document_id: 4acc7992-38b2-9d95-f87d-cbd42b0602a4
document_version_independent_id: 4acc7992-38b2-9d95-f87d-cbd42b0602a4
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/remote-help/troubleshoot.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: remote-help/troubleshoot
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/remote-help/troubleshoot.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/07bb3e10-d135-43ff-bc8b-360497cb39fa
- https://authoring-docs-microsoft.poolparty.biz/devrel/5287f575-02f0-405f-92b7-800456526b0c
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/12e559b9-eaf6-4aee-9af7-62334e15f863
- https://authoring-docs-microsoft.poolparty.biz/devrel/06e86142-34c2-4b94-ab9c-9477c21f7152
platformId: da3e38d7-4305-0980-bf38-adf1bc99a944
---

# Troubleshoot and monitor Remote Help for Microsoft Intune. - Microsoft Intune | Microsoft Learn

## Monitoring and reports

You can monitor the use of Remote Help from within the Microsoft Intune admin center. For unenrolled devices, reporting on Remote Help sessions is limited.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and go to **Tenant admin** &gt; **Remote Help**.
2. On the Monitor tab, you can see a count of active sessions and historical data about past sessions.
3. On the **Remote Help sessions** tab, you can see records of past sessions, including:

    - The helper (Provider ID) and sharer (Recipient ID) of each session.
    - The device that received assistance.
    - The start and end times of the Remote Help session.
    - The type of control session: view only, full control, or unattended.

Note

- **Recipient ID** and **Recipient name** display `--` for Android Enterprise dedicated devices because these devices don't have user affinity.
- Use of the Windows elevation capability isn't reported in the Remote Help sessions report.

These logs persist for 30 days on Microsoft servers. Session content, such as screen images or keystrokes, isn't recorded. Only metadata is stored.

## Log files

Remote Help logs data during installation and during Remote Help sessions, which can be of use when investigating issues with the app.

**Installation of Remote Help** - When Remote Help installs or uninstalls, the following two logs are created in the device users' Temp folder, for example, `C:\Users\<username>\AppData\Local\Temp`. The `*` in the log file name represents a date and time stamp of when the log was created.

- Remote\_help\_\*\_QuickAssist\_Win10\_x64.msi.log
- Remote\_help\_\*.log

**Operational logs** - During use of Remote Help, operational details are logged in the Windows Event Viewer:

- Event Viewer &gt; Application and Services &gt; Microsoft &gt; Windows &gt; RemoteHelp

## Troubleshoot

Use the table in this section to troubleshoot common issues with Remote Help.

| Check if | Solution |
| --- | --- |
| Remote Help is enabled for the tenant | In the Intune admin center, go to **Tenant administration** &gt; **Remote Help** and ensure that Remote Help is enabled. It can take up to 30 minutes (or a few hours in some cases) after assigning licenses for the service to activate. |
| The helper and sharer are using supported platforms and versions | See [Plan Remote Help](plan#supported-platforms) for details. |
| The helper has the required permissions | The helper must be assigned to an Intune role with Remote Help permissions and have the "Offer remote assistance" permission. See [Assign Remote Help permissions to helpers](plan#role-based-access-control-rbac) for details. |
| The helper and sharer are signing in with organizational accounts from the same tenant | Both the helper and sharer must sign in with a Microsoft Entra account from your organization. You can't use Remote Help to assist users who aren't members of your organization. |
| The helper and sharer have network access to the required endpoints | See [Network endpoints for Remote Help](plan#network-considerations) for details. |

# [Windows](#tab/windows)
Use the table in this section to troubleshoot common issues with Remote Help on Windows devices.

| Check if | Solution |
| --- | --- |
| The device meets the requirements for Remote Help | See [Plan Remote Help](plan#supported-platforms) for details. |
| The device has network access to the required endpoints | See [Network endpoints for Remote Help](plan#network-considerations) for details. |
| The device has blocked applications from using notifications | See [Policy CSP - Notifications](/en-us/windows/client-management/mdm/policy-csp-notifications#disallowcloudnotification) for details. |
| The Intune Win32 app detection rule (if used) is correct | Incorrect version detection can cause Intune to think the app is already installed or never installed. See [Deploy Remote Help](deploy) for details. |
| The device is in *do not disturb* mode | If the device is in *do not disturb* mode, notifications for Remote Help session requests won't be shown. Disable *don't disturb* mode and try again or ask the sharer to check their notifications pane. |

#### Troubleshooting Remote Help on Windows for Microsoft Edge WebView2

You might see an error code in a dialog box if you're having trouble installing and running Remote Help. The error might be related to Microsoft Edge WebView 2, which is required to use Remote Help. Here are some error codes you might see along with a short description of the problem.

| Error Code | General Problem |
| --- | --- |
| 1001 | Remote Help failed to initialize one of its internal components. |
| 1002 | Remote Help failed to load WebView2. |
| 1003 | Remote Help failed to install WebView2. |

Use these steps to resolve these issues:

1. Ensure that Microsoft Edge is installed properly and is up to date.

Remote Help uses the Microsoft Edge browser control. If you have problems, the common troubleshooting tips here may help get Remote Help working. Learn more about [Troubleshooting tips for installing and updating Microsoft Edge.](https://support.microsoft.com/microsoft-edge/troubleshooting-tips-for-installing-and-updating-microsoft-edge-a5eceb94-c2b1-dfab-6569-e79d0250317b)

After installing or updating Microsoft Edge, try opening Remote Help again. If Remote Help doesn't run or you get an error message that Microsoft Edge WebView2 isn't installed, go to the next step.

1. Install Microsoft Edge WebView 2

Microsoft Edge WebView2 is required to use Remote Help. If you get an error message that WebView2 isn't installed when you try to open Remote Help, then [download and install Microsoft Edge WebView2](https://developer.microsoft.com/microsoft-edge/webview2/consumer/?form=MA13LH) from the Microsoft website. When WebView2 is installed, try opening Remote Help again.

Note

WebView2 should already be installed if your device is running Windows 11 or has Microsoft Edge.

# [macOS](#tab/macos)
Use the table in this section to troubleshoot common issues with Remote Help on macOS devices.

| Check if | Solution |
| --- | --- |
| Single sign-on is configured and active | If unenrolled devices support isn't enabled, the Entra Enterprise single sign-on extension must be configured and registered for Intune to be able to confirm the device is enrolled. See [Plan Remote Help](plan#prerequisites) for details. |
| The required operating system permissions for *Accessibility* and *Screen sharing* are allowed | See [Configure Remote Help](deploy?tabs=macos#configure-remote-help) for details. |
| Whether the sharer is using the native Remote Help app or the web app | The web app only allows view access, which might confuse helpers expecting control. |

# [Android](#tab/android)
Use the table in this section to troubleshoot common issues with Remote Help on Android devices.

| Check if | Solution |
| --- | --- |
| The device is enrolled in Dedicated mode. | Remote Help doesn't support other Android enrollment types. |
| The device has been newly enrolled with Intune. | On newly enrolled devices, push notifications, needed for Remote Help to receive session initiation requests, can take a while to start working. Wait for 15 minutes and try again later. |
| The Remote Help app isn't installed. | Install the app, see [Deploy Remote Help](deploy) for details. |
| All the required permissions are configured and granted for the Remote Help app. | Review and ensure that all required permissions are granted. See [Plan Remote Help](plan#prerequisites) for details. |
| The Intune app version isn't updated. | Update the Intune app to the latest version. |
| The device doesn't have access to Google services. | Remote Help requires access to Google Mobile Services to function, so make sure the device has Google services. You can do this by verifying that the Play Store is present on the device. See [Android: Google Mobile Services](https://www.android.com/gms/). |
| There's no response from the end user. | Screen Sharing and Full Control Sessions time out automatically after 5 minutes if there's no response from [Android: Google Mobile Services](https://www.android.com/gms/) on the end user device. Make sure the user accepts the prompt to start the session. |
| The device manufacturer or OS/Zebra MX/Samsung Knox version isn't supported | Make sure the device is supported. See [Plan Remote Help](plan#supported-platforms) |
| (On Samsung devices only) The Knox license on the device is expired/invalid or has network issues. | Make sure that all Knox permissions have been granted, and that the device has an active Knox license; see [License activation errors](https://configure.samsungknox.com/files/knox-configure-getting-started/Content/license-activation-errors.htm) for troubleshooting Knox activation errors. |
| (On Samsung devices only) Other apps are actively using the Samsung Knox remote desktop APIs (you're using another remote assistance app on the device). | Close or uninstall any other apps using remote viewing/control capabilities on the device. |

---

## Known Issues

# [Windows](#tab/windows)
For Windows devices, the following are known issues with Remote Help when using the remote launch feature:

- Notifications for remotely triggering a Remote Help session fail if the *Microsoft Intune Management Service* isn't running.
- After the user's device is restarted, there's a short delay for the *Microsoft Intune Management Service* to start. Either wait for the *Microsoft Intune Management Service* to start or ask the sharer to open the app and share the code.
- For newly enrolled devices, there's a 1 hour delay before the user's device begins receiving notifications when a helper initiates a session.

# [macOS](#tab/macos)
- If the sharer exits from a Remote Help session early, the helper might not be notified for 60+ seconds.
- If using Microsoft Edge, the sharer might have to sign in to Microsoft Edge before starting a session or the device reports as Unenrolled.
- Verify that your browser is up to date.
- If you're screen sharing using another application like Teams or recording during the session, it might take longer for the session to connect.

# [Android](#tab/android)
- On newly enrolled devices, push notifications, needed for Remote Help to receive session initiation requests, can take a while to start working. Wait for 15 minutes and try again later.

---

### Web app known issues

- If the sharer exits from a Remote Help session early, the helper may not be notified for 60+ seconds.
- If using Microsoft Edge, it may require the sharer to sign in to Microsoft Edge before starting a session or the device is reported as Unenrolled.
- SSO must be enabled for the tenant to use the Remote Help web app.