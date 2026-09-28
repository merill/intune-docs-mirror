---
layout: Conceptual
title: Microsoft Intune Enterprise Application Management - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/app-management/deployment/enterprise-app-management
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- FocusArea_Apps_EAC
ms.reviewer: dguilory
ms.subservice: suite
description: Learn about Enterprise App Management and the Enterprise App Catalog in Microsoft Intune.
ms.date: 2026-06-03T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: 63dcddbd-498d-178a-421c-b36c4cd26f76
document_version_independent_id: 63dcddbd-498d-178a-421c-b36c4cd26f76
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/app-management/deployment/enterprise-app-management.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: app-management/deployment/enterprise-app-management
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/app-management/deployment/enterprise-app-management.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4b132a0c-342a-42eb-91ff-8159e1ed413d
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/f2b71146-ce8e-46a8-9965-8aa8b3aa8235
platformId: a950b253-8844-4ed9-96bb-af2980c294fd
---

# Microsoft Intune Enterprise Application Management - Microsoft Intune | Microsoft Learn

Microsoft Intune Enterprise App Management enables you to easily discover and deploy applications and keep them up to date from the Enterprise App Catalog. The Enterprise App Catalog is a collection of prepared Microsoft and non-Microsoft applications. These apps are Win32 apps that are [prepared as Win32 apps](create-win32-package) and hosted by Microsoft.

## Prerequisites

![](../../media/icons/16/cloud.svg)**Cloud requirements**

> 
> - Public cloud
> - Sovereign cloud environments:
>     - U.S. Government Community Cloud (GCC) High
>     - U.S. Department of Defense (DoD)
> 

![](../../media/icons/16/licensing.svg)**Licensing requirements**

> 
> This feature requires a subscription in addition to Microsoft Intune Plan 1 or Plan 2. For licensing options, see [Microsoft Intune plans and pricing](https://aka.ms/MicrosoftIntunePricing) and [Microsoft 365 Security Enterprise Plans](https://www.microsoft.com/security/pricing/enterprise-plans).

![](../../media/icons/16/devices.svg)**Device platform requirements**

> 
> The Enterprise App Catalog is available for Windows apps.
> 
> On October 14, 2025, [Windows 10 reached end of support](/en-us/lifecycle/announcements/windows-10-end-of-support) and won't receive quality and feature updates. Windows 10 is an **allowed** version in Intune. Devices running this version can still enroll in Intune and use eligible features, but functionality won't be guaranteed and can vary.

## Benefits of Enterprise App Management

The Enterprise App Management provides the following benefits:

- **Streamlined app management**: You can save time and reduce complexity by streamlining the app management process. Discover and add apps directly from the Intune console.
- **Stay current with updates**: You're able to keep apps up-to-date by easily creating apps for the new versions of products as they're available in the catalog. Use the **Enterprise App Catalog apps with updates** report.
- **Windows Autopilot integration**: Enterprise App Catalog apps are supported with Windows Autopilot. Microsoft Intune Enterprise App Management enables IT admins to easily manage applications from the Enterprise App Catalog. Using Windows Autopilot, you can select blocking apps from the Enterprise App Catalog in the Enrollment Status Page (ESP) and the Device Preparation Page (DPP) profiles. This feature allows you to update apps more easily without needing to update those profiles with the latest versions.

When you add an Enterprise App Catalog app, Intune prefills the following installation details:

- Commands to install and uninstall the app
- Time required to install the app
- Option to allow app uninstallation by the end user
- Installation and device restart behavior
- Return codes to indicate post-installation behavior
- Whether to install the app for system or user

Microsoft Intune prefills the detection rules that devices must meet before the app is installed:

- File size
- File version
- Registry

Also, Intune prefills the requirements that devices must meet before the app is installed:

- Windows OS architecture required
- Minimum OS required

Important

Microsoft recommends using the prepopulated fields containing specific commands and rules, however you can modify the prepopulated fields if needed.

You can also configure app specific rules used to detect the presence of the Enterprise App Catalog app. You can choose to either manually configure the detection rules or use a custom script to detect the presence of the app before installing the app.

## Self-updating apps

The Enterprise App Catalog includes apps that self update. Intune ensures the app is at least at a target minimum version, and considers the app installed if the detected version of the app is at or above the minimum version. Self-updating apps update on client devices based on the vendor's process. Intune reports the version of the app detected on the device.

Important

Self-updating apps might require that your tenant has network rules configured to allow an update from the app vendor.

## Auto-update for Enterprise App Catalog apps

You can automatically keep Enterprise App Catalog apps up to date with Microsoft Intune. When auto-update is enabled for an Enterprise App Catalog app with a required assignment, Intune detects when a newer version is available in the catalog and automatically updates the app on targeted devices. You don't need to create a new app or configure a supersedence relationship for each update.

Auto-update helps you:

- Simplify app lifecycle management by removing manual packaging and supersedence steps.
- Reduce operational overhead at scale by eliminating the long tail of update maintenance.
- Keep devices secure with reliable, timely application updates.

**Requirements and scope:**

- Auto-update applies to Enterprise App Catalog apps only.
- Auto-update applies to apps with a **Required** assignment. Apps assigned as **Available for enrolled devices** continue to use the existing update workflow.
- Supported on Windows 10 and Windows 11 devices.

To learn how to enable auto-update when you add or edit an Enterprise App Catalog app, see [Step 6: Assignments](add-enterprise-catalog-app#step-6-assignments).

Note

If you prefer to review updates before they're applied, you can continue to use [Guided update supersedence](update-enterprise-supersedence) instead of enabling auto-update.

### Limitations and known issues

Before you enable auto-update for an Enterprise App Catalog app, review the following limitations.

#### No rollback or automatic uninstall remediation

Auto-update apps don't provide rollback or automatic uninstall remediation. If a version must be removed or remediated from devices, you must take manual action outside the auto-update flow (for example, by assigning an **Uninstall** intent or deploying a remediation script).

#### Malicious version revocation

If Microsoft detects a malicious app version in the Enterprise App Catalog, Microsoft removes the app from the catalog and posts a notification in the Microsoft Intune admin center. You're still responsible for identifying impacted devices and taking remediation action.

#### Catalog cache lag

Enterprise App Catalog data is cached for up to one hour, so the catalog might show an outdated version during that window. If a version is revoked because of a security issue, devices can remain exposed for up to one hour before the updated catalog state is reflected. Microsoft notifies customers when a revocation occurs, but you're responsible for identifying devices with the revoked version and remediating them.

#### No rollout rings or phased deployment

Auto-update doesn't support rollout rings or deployment plans for staged update deployment. When a new version is available, it goes out to all targeted devices at the same time rather than through phased deployment groups.

#### Reporting reflects latest state only

Auto-update app reporting stores only the latest reported state per device. If a device reports enforcement or detection activity, the app install status reflects the current reported state. Intune doesn't retain a full history of prior version states or prior actions at the device level.

#### Version changes during device processing

Devices might report that they attempted an auto-update action (enforcement or detection) and return status after that action. If the app version changes while devices are still processing, reporting can show status for devices at different points in the update flow. Not all devices check in after the latest version is released.

#### Not supported as a blocking app in ESP or Autopilot device preparation

You can't add an auto-update Enterprise App Catalog app as a blocking app in the Enrollment Status Page (ESP) or Autopilot device preparation.

#### Conflicts with other app types

Auto-update apps can conflict with other app types that target the same app. This conflict scenario isn't supported. For example, if a line-of-business app assignment installs version 2 while an auto-update app manages the same app, devices can enter a race condition where the installed version changes between the two versions. To avoid conflicts, manage each app through a single deployment type.

## Frequently asked questions (FAQ)

### How can I request to add an application to the Enterprise App Catalog?

We added a category to the [Microsoft Feedback Portal](https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472) that allows you to submit application requests, suggest changes, and share any other feedback about Enterprise application management. We recommend you filter the feedback portal under **Categories** by selecting **Enterprise App Management (Intune add-on)** to successfully route your requests and feedback.

To request adding an application to the Enterprise app catalog use the [Microsoft Feedback Portal](https://feedbackportal.microsoft.com/feedback/forum/ef1d6d38-fd1b-ec11-b6e7-0022481f8472). The feedback portal gives Microsoft the ability to communicate with you on the status of your request and other communication about your request.

Include the following details when requesting to add an application:

- Application publisher
- Application name
- Download URL

Important

Enterprise application management doesn't support the addition of applications that are behind a paywall or sign in screen.

You can also upvote an application previously submitted by someone else. Applications with large numbers of votes receive the most consideration and effort to be added to the catalog. However, priority depends on complexity of the applications mechanics.

Important

Microsoft makes no guarantee, express or implied, with respect to adding a requested app to the Enterprise App Catalog. After Microsoft reviews the submission form, the app might be added. Microsoft doesn't offer or assume any Service Level Agreement (SLA) or timeline regarding adding an app to the Enterprise App Catalog.

### Where are the devices downloading the app content from?

Microsoft hosts the applications in Microsoft storage accessible through `*.manage.microsoft.com`. For the full list of network requirements, see [Network endpoints for Microsoft Intune](../../fundamentals/endpoints?tabs=north-america).

### Is Microsoft providing security around any of the content provided in the Enterprise App Catalog?

Microsoft doesn't assert compliance, authorization, authenticity, or integrity for apps distributed via Intune. Customers are responsible for ensuring that apps meet their requirements.

### What app installer types are in the Enterprise App Catalog?

The apps currently provided in the Enterprise application catalog are Windows Win32 applications (exe and msi).

### How can Microsoft detect if an application from the Enterprise App Catalog is in use?

At this time, Intune provides no running application detection.

### What are the Service Level Objectives for when an app update is available in the catalog?

Service Level Objectives (SLOs) define target timelines for making app updates available in the Enterprise App Catalog between when Microsoft receives them to when they're made available in the Enterprise App Catalog. Unlike Service Level Agreements (SLAs), SLOs are guidelines, not guarantees that allow customers to plan typical app update processing timelines.

The SLO measurement window starts at ingestion, the point when the app update is first received from the data source and logged in the EAM system.

#### App Update Process Flow

1. **Ingestion** – App update is received by Microsoft
2. **Automated Validation** – Compatibility and compliance checks
3. **Manual Validation** - More testing if needed
4. **Catalog Availability** – App update published to Enterprise App Catalog

#### Automated Validation

Most apps undergo automated validation checks.

- Target: 80–90% of app updates are processed and available in the Intune portal within 24 hours of ingestion.

#### Manual Validation Apps

If an app fails automated checks, it moves to manual validation and requires more testing. Updates requiring manual testing and approval are completed within seven days.

#### Exception Handling

- High-usage or critical apps that fail automated validation are prioritized for expedited processing (goal of 48 hours.)
- Apps that fail both automated and manual validation don't meet SLO and are flagged as unsupported.

### How many applications are in the catalog?

For a complete list of applications, see [Apps available in the Enterprise App Catalog](enterprise-app-management#apps-available-in-the-enterprise-app-catalog).

### How can working with the applications in Enterprise App Catalog be automated?

You can use Microsoft's Graph API to work with applications in Enterprise App Catalog. For more information, see [Working with Intune in Microsoft Graph](/en-us/graph/api/resources/intune-graph-overview).

### Will Enterprise catalog apps automatically update to a new version when a new version is available in the Enterprise app catalog?

Yes, when auto-update is enabled. For Enterprise App Catalog apps with a **Required** assignment, you can turn on auto-update so Intune applies new versions from the catalog automatically. For more information, see Auto-update for Enterprise App Catalog apps.

If auto-update isn't enabled, available updates are shown in Intune by selecting **Apps** &gt; **Enterprise App Catalog apps with updates**. In that case, the updates aren't applied automatically and you create a new app with a supersedence relationship. For more information, see [Guided update supersedence](update-enterprise-supersedence).

### Can you get licensed applications from this catalog?

Yes. You can get licensed applications from the Enterprise App Catalog, although you're responsible for purchasing the license from the vendor and distributing it to your organization. Intune doesn't perform a license check on Enterprise App Catalog apps.

### Can Enterprise App Management be purchased standalone?

Yes. Enterprise App Management can be purchased as a standalone SKU or as part of the Microsoft Intune Suite.

### Can Enterprise App Management be used with Microsoft Configuration Manager?

Enterprise App Management is only provided by Microsoft Intune. Configuration Manager doesn't directly support Enterprise App Management apps. However, co-managed clients can get Enterprise App Catalog apps when targeted from Microsoft Intune.

### What happens if an app is removed from the Enterprise App Catalog?

Occasionally, app vendors might request removal of their applications from the Enterprise App Catalog. When this happens:

- **Existing deployments remain unaffected**: Apps that are already deployed to your tenant and user devices continue to function normally.
- **No new deployments**: You can't deploy new instances of the removed app from the Enterprise App Catalog.
- **Alternative solutions**: For future deployments, work directly with the app vendor or use traditional Win32 app deployment methods.

### Does Enterprise App Management use **Winget**?

No. Enterprise App Catalog apps are directly installed by the Intune management extension (IME).

### How do I update my Enterprise App Catalog app?

For applications that don't update themselves, you can view the upgrades that are available for the Enterprise App Management (EAM) app via supersedence.

### After several hours, what can I do if my app continues to show that it isn't ready and that the requested content is still being prepared?

If the app content isn't synced after several hours, delete the app and try again.

### Is there an Intune report available to view details about the Enterprise App Catalog apps for a specific device?

Yes, the Managed Apps report provides a report of apps on a specific device that are currently installed, not installed, or available for install. For the device, the report provides details about the application, version, resolved intent, and installation status. For more information about this report, see [Managed Apps report](../../device-management/reports/overview#managed-apps-report-operational).

## Apps available in the Enterprise App Catalog

There are various applications available in the Enterprise App Catalog. To view the current application list in [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), see [Add a Windows catalog app (Win32) to Intune](add-enterprise-catalog-app#add-a-windows-catalog-app-win32-to-intune).

More apps are available on an ongoing basis in the Enterprise App Catalog.

Note

**think-cell apps removed from Enterprise App Catalog**: At the request of think-cell, their applications are removed from the Enterprise App Catalog. This removal **does not affect** existing think-cell installations in your tenant or on user devices. Customers who currently have think-cell apps deployed through the Enterprise App Catalog can continue to manage these installations normally.

The following table of Enterprise Apps is available within Intune:

| Apps |
| --- |
| 3CX Desktop App |
| 3CXPhone for Windows |
| 3DF Zephyr Free |
| 3DxWare 10 |
| 4K Video Downloader |
| 4K Video Downloader+ |
| 7-Zip |
| 8x8 Work |
| AbaClient |
| Able2Extract Professional |
| Acro Software CutePDF Writer |
| ActiveState Software Komodo Edit |
| ActiveState Software Komodo IDE |
| Adobe AIR |
| Agent Ransack |
| AIMP |
| Air Explorer |
| Aircall for desktop |
| AirParrot 2 |
| Akiflow |
| alfaview |
| Allway Sync |
| ALLPlayer |
| Altova XMLSpy Enterprise 2023 |
| Amazon AWS Command Line Interface |
| Amazon AWS Tools for Windows |
| Amazon AWS VPN Client |
| Amazon Corretto 18 |
| Amazon Corretto JDK 8 |
| Amazon Corretto JDK 11 |
| Amazon Corretto JDK 15 |
| Amazon Corretto JDK 16 |
| Amazon Corretto JDK 17 |
| Amazon Corretto JDK 19 |
| Amazon DCV Client |
| Amazon Kindle |
| Amazon Redshift ODBC driver |
| Amazon WorkSpaces |
| Android Studio 2022 |
| Android Studio 3 |
| Android Studio 4 |
| AnyBurn |
| AnyDesk |
| AnyLogic Professional |
| AnyLogic University |
| Anywhere365 Integrator |
| App Dynamic AirServer Universal |
| Appgate SDP Client |
| Apple iTunes |
| Aptakube |
| Araxis Merge |
| ArcticLine Software Jet Screenshot |
| Arduino IDE |
| Articulate 360 |
| Articulate Replay 360 |
| Articulate Studio 360 |
| Artweaver Free |
| ASAP Utilities |
| ASUS Remote Drive |
| Astute Manager |
| Atlassian Companion |
| Atlassian Confluence |
| Atomi Systems ActivePresenter |
| Atostek ID |
| Audacity |
| Autodesk Access |
| Autodesk Design Review 2018 |
| Autodesk Identity Manager |
| Autodesk Interoperability Tools |
| Autodesk Single Signon Component |
| AVer Information A+ Suite |
| AVS Image Converter |
| AVS Media Player |
| AWS SAM command line interface |
| AWS Session Manager Plugin |
| AxCrypt |
| Axel Rietschin Software Developments FastPictureViewer Professional |
| Axure RP |
| Azure Functions Core Tools |
| Bambu Studio |
| BandiView |
| Beam Studio |
| Beats Winlogbeat |
| Belgium e-ID viewer |
| Beyond Compare |
| Beyond Identity |
| BleachBit |
| Blender |
| Blender Foundation Blender |
| BlueJeans 2 |
| Box CLI |
| Box Drive |
| Brady Workstation |
| BREAK PRO |
| Bria Enterprise |
| Bridge Designer 2016 |
| BrightAuthor connected |
| BrowserStackLocal |
| Bulk Crap Uninstaller |
| Bullzip PDF to Word |
| BurnAware Free |
| Burp Suite Community Edition |
| Burp Suite Professional Edition |
| Business Tax Software BLR |
| Bytello Share |
| Calibrite Profiler |
| Camtasia Studio 2018 |
| Camtasia Studio 2019 |
| Caphyon Advanced Installer |
| Capture One 20 |
| Capture One 22 |
| Cato Client |
| Causasoft ExhibitManager |
| Certify The Web |
| Charles |
| Chatbox |
| Chef Workstation for Windows |
| Cisco Jabber 14 |
| Cisco Jabber 15 |
| Cisco JVDI Agent 12 |
| Cisco JVDI Agent 14 |
| Cisco JVDI Agent 15 |
| Cisco Webex Meetings |
| Cisco Webex Productivity Tools |
| Cisco WebEx Recorder and Player |
| Cisco WebEx Recording Editor |
| Cisco Webex Teams |
| Citrix Receiver |
| Citrix Workspace app |
| Citrix Workspace app LTSR |
| Class |
| Classic Shell |
| ClassPoint |
| ClipboardFusion |
| ClockAssist |
| Clockify |
| Cloud Drive Mapper |
| CloudCompare |
| Cloudflare WARP |
| CloudShow |
| CMake |
| CodeMeter Runtime Kit |
| Colour Contrast Analyser |
| ComponentAgro CHECK PC2Web |
| CPU-Z |
| Creative Force Kelvin |
| Creative Force Triad |
| Crestron AirMedia app |
| Crestron AirMedia Peripheral Installer |
| CrisisGo App |
| Cryptomator |
| Cube Browser |
| CutePDF Writer |
| Cyberduck CLI |
| Dane Prairie Systems Win2PDF |
| Datadog Agent |
| DataGrip 1.0 |
| DataGrip 2016.3 |
| DataGrip 2020.3 |
| DataGrip 2021.1 |
| DataGrip 2021.2 |
| DataGrip 2021.3 |
| DataGrip 2022.1 |
| DataGrip 2022.2 |
| DataGrip 2024 |
| DataGrip 2024.1 |
| DataSpell |
| David Kocher Cyberduck |
| DAX Studio |
| DB Browser for SQLite |
| DBeaver Community |
| DBeaver Enterprise |
| DBeaver Lite |
| DBeaver Ultimate |
| DbVisualizer |
| Dedoose Desktop App |
| Defraggler |
| Delinea Connection Manager |
| Dell Command Update |
| Dell Command Update (Windows Universal Application) |
| Dell Display Manager |
| Dell EMC System Update |
| Dell Peripheral Manager |
| Dell SupportAssist |
| Devolutions Launcher |
| Devolutions Remote Desktop Manager |
| Devolutions Remote Desktop Manager Agent |
| Devolutions Workspace |
| DevPod |
| digiSeal Reader |
| DiRoots ProSheets |
| Directory Opus |
| DisplayLink Dock Driver |
| Ditto Connect |
| dnGrep |
| Docker Desktop |
| docuPrinter LT |
| docuPrinter PRO |
| docuPrinter TSE |
| Draftable Desktop |
| draw.io Desktop |
| DroidCam Client |
| dRofus |
| Druva inSync |
| Duo Desktop |
| DYMO ID |
| Eclipse Temurin JDK with Hotspot 8 (LTS) |
| Eclipse Temurin JDK with Hotspot 11 (LTS) |
| Eclipse Temurin JDK with Hotspot 12 |
| Eclipse Temurin JDK with Hotspot 15 |
| Eclipse Temurin JDK with Hotspot 16 |
| Eclipse Temurin JDK with Hotspot 17 (LTS) |
| Eclipse Temurin JDK with Hotspot 18 |
| Eclipse Temurin JDK with Hotspot 19 |
| Eclipse Temurin JDK with Hotspot 20 |
| Eclipse Temurin JDK with Hotspot 21 |
| Eclipse Temurin JDK with Hotspot 22 |
| Eclipse Temurin JDK with Hotspot 23 |
| Eclipse Temurin JRE with Hotspot 8 (LTS) |
| Eclipse Temurin JRE with Hotspot 11 (LTS) |
| Eclipse Temurin JRE with Hotspot 12 |
| Eclipse Temurin JRE with Hotspot 15 |
| Eclipse Temurin JRE with Hotspot 16 |
| Eclipse Temurin JRE with Hotspot 17 (LTS) |
| Eclipse Temurin JRE with Hotspot 18 |
| Eclipse Temurin JRE with Hotspot 19 |
| Eclipse Temurin JRE with Hotspot 20 |
| Eclipse Temurin JRE with Hotspot 22 |
| Eclipse Temurin JRE with Hotspot 23 |
| Egnyte Connect Desktop App |
| Egnyte WebEdit |
| Elgato Stream Deck |
| Elevate UC |
| Encrypt.me |
| Endnote 20 |
| Endnote X8 |
| Endnote X9 |
| Enpass |
| EnterpriseDB Corporation PostgreSQL 12 |
| ESET Endpoint Antivirus V9 |
| ESET Endpoint Antivirus V10 |
| ESET Endpoint Antivirus V12 |
| ESET Endpoint Encryption |
| ESET Endpoint Security V9 |
| ESET Endpoint Security V12 |
| Evernote |
| exacqVision Client |
| EZB Systems UltraISO |
| FactSet Workstation |
| FastPictureViewer Professional |
| FastStone Soft Capture |
| FastStone Soft Image Viewer |
| FastStone Soft Photo Resizer |
| FileZilla |
| Filius |
| FlashFXP |
| FlexWhere for Desktop |
| Forté Agent |
| Fortify |
| Foxit PDF Editor 11 |
| Foxit PDF Editor 12 |
| Foxit PDF Editor 13 |
| Foxit PDF Editor 2024 |
| Foxit PDF Editor Pro 11 |
| Foxit PDF Editor Pro 11 (Multi-Language) |
| Foxit PDF Editor Pro 13 |
| Foxit PDF Reader |
| Foxit PhantomPDF 10 |
| Foxit PhantomPDF Pro 10 |
| Foxit PhantomPDF Pro 10 (Multi-Language) |
| Frame App |
| Free Countdown Timer |
| FreeCAD |
| Front Desktop |
| FTP Rush v3 |
| Fusion 2025 |
| Fuzzy Lookup Add-In For Excel |
| FXHOME HitFilm Express |
| Gadwin PrintScreen |
| Gadwin PrintScreenPro |
| Gadwin ScreenRecorder |
| Galaxy Modeler |
| Garden Gnome Package Viewer |
| Garmin BaseCamp |
| Garmin Express |
| General Workings Streamlabs OBS |
| Genesys Cloud |
| Genesys Cloud Background Assistant |
| GeoGebra 5 |
| GeoGebra 6 |
| Geomilieu |
| Gephi |
| GIMP |
| Git |
| GitHub CLI |
| GnuPG VS-Desktop |
| GoAnywhere OpenPGP Studio |
| Golden 6 |
| Golden 7 |
| Golden 8 |
| GoLand 2017.3 |
| GoLand 2021.1 |
| GoLand 2022.2 |
| GoLand 2024 |
| GoodSync 12 |
| GoodSync Personal |
| Google Ads Editor |
| Google Backup and Sync |
| Google Chrome for Business |
| Google Chrome Remote Desktop Host |
| Google Credential Provider for Windows |
| Google Drive |
| Google Drive File Stream |
| Google Go Programming Language 1.16 |
| Google Go Programming Language 1.17 |
| Google Go Programming Language 1.18 |
| Google Go Programming Language 1.19 |
| Google Go Programming Language 1.20 |
| Google Go Programming Language 1.21 |
| Google Go Programming Language 1.22 |
| Google Web Designer |
| GoTo Connect |
| Gpg4win |
| GraphDB Desktop |
| Graphviz |
| grepWin |
| gsudo |
| HandBrake |
| Hanword HWP document converter for Microsoft Word 2016 |
| HashTools |
| HeidiSQL |
| HIPIN v4 |
| Horizon Collaborate |
| HP Client Management Script Library |
| HP Prime Virtual Calculator |
| Huddle Desktop |
| HWMonitor |
| IAP Desktop |
| Ibis Calculeren voor Bouw |
| Ibis Calculeren voor Infra |
| IBM Aspera Connect |
| IBM Semeru Runtime Open Edition JDK 8 (LTS) |
| IBM Semeru Runtime Open Edition JDK 11 (LTS) |
| IBM Semeru Runtime Open Edition JDK 16 |
| IBM Semeru Runtime Open Edition JDK 17 (LTS) |
| IBM Semeru Runtime Open Edition JDK 18 |
| IBM Semeru Runtime Open Edition JDK 19 |
| IBM Semeru Runtime Open Edition JDK 20 |
| IBM Semeru Runtime Open Edition JDK 22 |
| IBM Semeru Runtime Open Edition JRE 8 (LTS) |
| IBM Semeru Runtime Open Edition JRE 11 (LTS) |
| IBM Semeru Runtime Open Edition JRE 17 (LTS) |
| IBM Semeru Runtime Open Edition JRE 18 |
| IBM Semeru Runtime Open Edition JRE 19 |
| IBM Semeru Runtime Open Edition JRE 20 |
| IBM Semeru Runtime Open Edition JRE 22 |
| IcedTea-Web |
| ImageGlass |
| iMazing Converter |
| Image-Line Software FL Studio |
| ImpExpPro |
| Infix PDF Editor |
| Inkscape |
| Inmatrix Zoom Player Max |
| Install4j |
| Intermedia Unite |
| IrfanView |
| IronPython |
| IronPython 2.7 |
| IsoBuster |
| iZotope RX Advanced 10 |
| Jabra Direct |
| JAM Software TreeSize Free |
| JAWS 2025 |
| JetBrains dotUltimate 2022 |
| JetBrains dotUltimate 2023 |
| JetBrains dotUltimate 2024 |
| JetBrains ReSharper 2023.1 |
| Joplin |
| JProfiler |
| BCF Manager for Tekla |
| KDiff3 |
| KeePass Password Safe (Classic Edition) |
| KeePassXC |
| Keeper |
| KeeWeb |
| Kerio Connect |
| KeyShot Studio |
| KeyStore Explorer |
| KNIME Analytics Platform |
| Kobo |
| Kodu Game Lab |
| Konnekt |
| Kotobee Author |
| Kotobee Reader |
| Kovid Goyal Calibre |
| KPN Desktop Integratie |
| Kreya |
| Krisp |
| Krita |
| Lansweeper |
| Lark Deployment Tool |
| Laserbox basic |
| LastPass |
| LEGO Education SPIKE |
| Lenovo Accessories and Display Manager |
| Lenovo Quick Clean |
| Lens Desktop |
| Liberica JDK |
| Lifelong Kindergarten Group Scratch |
| LINQPad 5 |
| LiquidFiles Outlook Plugin |
| Liquit Workspace Agent 3 |
| Local Administrator Password Solution |
| Logi Tune |
| Logitech Bolt |
| Logitech Camera Settings |
| Logitech Options |
| Logitech Presentation |
| Logitech SetPoint |
| Logitech Sync App |
| LogMeIn Client |
| LogMeIn GoToMeeting IT Installer |
| LogMeIn GoToMeeting multi-build Installer |
| LogMeIn Hamachi |
| LogMeIn Host |
| LogMeIn RemotelyAnywhere |
| LucaNet.Excel-Add-In |
| LucidLink Classic |
| Luna Modeler |
| Macrobond |
| Macrobond Viewer |
| Mail Viewer |
| Malwarebytes |
| MariaDB Server 10.2 |
| MariaDB Server 10.3 |
| MariaDB Server 10.4 |
| MariaDB Server 10.5 |
| MariaDB Server 10.6 |
| MariaDB Server 10.7 |
| MariaDB Server 10.9 |
| MatterControl |
| Mattermost Desktop |
| Maxcut |
| MAXQDA 2020 Reader |
| Memento Desktop Edition |
| Mendeley Desktop |
| Mendeley Reference Manager |
| Mendix 9 |
| Mersive Solstice Client |
| Meta Quest Developer Hub |
| Meta Spark Player |
| Meteor Modeler |
| Microsoft .NET Core 2.2 |
| Microsoft .NET Desktop Runtime 6.0 |
| Microsoft .NET Desktop Runtime 7.0 |
| Microsoft .NET Runtime 6.0 |
| Microsoft .NET Runtime 7.0 |
| Microsoft .NET SDK 9.0 |
| Microsoft Access Database Engine 2016 |
| Microsoft Active Directory Rights Management Service Client |
| Microsoft Analysis Management Objects |
| Microsoft Analysis Services ADOMD.NET |
| Microsoft Analysis Services OLE DB Provider |
| Microsoft ASP.NET Core Runtime 5.0 |
| Microsoft ASP.NET Core Runtime 6.0 |
| Microsoft ASP.NET Core Runtime 7.0 |
| Microsoft Azure CLI |
| Microsoft Azure Connected Machine Agent |
| Microsoft Azure Data CLI |
| Microsoft Azure Data Studio |
| Microsoft Azure Information Protection client |
| Microsoft Azure PowerShell |
| Microsoft Azure Storage Explorer |
| Microsoft Bot Framework Composer |
| Microsoft Bot Framework Emulator |
| Microsoft Defender for Endpoint plug-in for WSL |
| Microsoft Deployment Toolkit (8456) |
| Microsoft Enterprise Mode Site List Manager |
| Microsoft ODBC Driver 13 for SQL Server |
| Microsoft ODBC Driver 17 for SQL Server |
| Microsoft OLE DB Driver 18 for SQL Server |
| Microsoft On-premises data gateway |
| Microsoft OneNote |
| Microsoft Power BI Desktop |
| Microsoft PowerShell Core |
| Microsoft PowerToys |
| Microsoft Purview Information Protection client |
| Microsoft Remote Desktop WebRTC Redirector |
| Microsoft Remote Help |
| Microsoft Skype for Desktop |
| Microsoft Skype TX |
| Microsoft SQL Server 2012 Express with Advanced Services |
| Microsoft SQL Server 2012 Native Client |
| Microsoft SQL Server 2014 Express LocalDB |
| Microsoft SQL Server 2016 Report Builder |
| Microsoft SQL Server 2017 Express Advanced Edition |
| Microsoft SQL Server 2017 for Microsoft Windows Latest Cumulative Update |
| Microsoft SQL Server 2017 Reporting Services |
| Microsoft SQL Server 2022 Express Edition |
| Microsoft SQL Server Management Studio 20 |
| Microsoft Surface Data Eraser |
| Microsoft Surface Diagnostic Toolkit for Business |
| Microsoft System CLR Types for SQL Server 2014 |
| Microsoft Universal Print Connector |
| Microsoft Visio 2016 Viewer |
| Microsoft Visual C++ 2005 Redistributable |
| Microsoft Visual C++ 2008 Redistributable |
| Microsoft Visual C++ 2012 Redistributable |
| Microsoft Visual C++ 2015-2022 Redistributable |
| Microsoft Visual Studio 2010 Tools for Office Runtime |
| Microsoft Visual Studio 2022 Community |
| Microsoft Visual Studio 2022 Enterprise |
| Microsoft Visual Studio 2022 Professional |
| Microsoft Visual Studio Code |
| Microsoft Visual Studio Team Explorer 2022 |
| Microsoft Windows Admin Center |
| Microsoft Windows Assessment and Deployment Kit (ADK) for Windows 10 update 1607 |
| Microsoft Windows Assessment and Deployment Kit (ADK) for Windows 10 update 1803 |
| Microsoft Windows Assessment and Deployment Kit (ADK) for Windows 10 update 1809 |
| Microsoft Windows Assessment and Deployment Kit (ADK) for Windows 10 update 1903 |
| Microsoft Windows Assessment and Deployment Kit (ADK) for Windows 10 update 2004 |
| Microsoft Windows Assessment and Deployment Kit (ADK) for Windows 11 |
| Microsoft Windows PE add-on for ADK for Windows 10 update 1809 |
| Microsoft Windows PE add-on for ADK for Windows 11 |
| Mitel miCollab |
| Mobirise |
| Mocha TN3270 |
| Mocha TN3812 |
| Mocha TN5250 |
| monday |
| MongoDB Compass |
| MongoDB Compass Isolated Edition |
| MongoDB Compass Readonly Edition |
| Moon Modeler |
| MOOS Project Viewer |
| Morphic |
| Mozilla Firefox |
| Mozilla Firefox ESR 102 |
| Mozilla Firefox ESR 115 |
| Mozilla FrontMotion Firefox Community Edition |
| Mozilla FrontMotion Firefox Community Edition ESR |
| Mozilla SeaMonkey |
| Mozilla Thunderbird |
| mPollux DigiSign Client |
| MSEndpointMgr Intune Debug Toolkit |
| MSIX Core |
| Multilogin |
| MuseScore 3 |
| MuseScore Studio 4 |
| Nagstamon |
| NAPS2 |
| NCPA |
| Nessus Agent 10 |
| NetBird |
| NetLogo |
| NetSetMan |
| NETworkManager |
| New Relic Infrastructure Agent |
| Nextcloud |
| NextivaONE |
| Nitro Pro 11 |
| Nitro Pro 13 (Retail) |
| Node.js 15 |
| Node.js 17 |
| Node.js 18 LTS |
| Node.js 19 |
| Node.js 20 LTS |
| Node.js 21 |
| Node.js 22 LTS |
| NoMachine |
| NoMachine Enterprise Client |
| NoMachine Enterprise Desktop |
| NoMachine Fonts Others |
| NordLayer |
| Notepad++ |
| NV Access NVDA |
| NVIDIA GeForce Experience |
| NVivo 12 |
| NVivo 13 |
| NWEA Secure Testing Browser |
| Obsidian |
| ocenaudio |
| Oh My Posh |
| OnSIP |
| OpenAudible |
| OpenDNS Umbrella Roaming Client |
| OpenJDK 11 |
| OpenJDK 16 |
| OpenJDK 17 |
| OpenJDK 21 |
| OpenLens |
| OpenShot Video Editor |
| OpenVPN |
| OpenVPN Connect |
| OpenWebStart |
| Oracle Java Runtime Environment Version 8 |
| Oracle Java SE Development Kit 17 |
| Oracle Java SE Development Kit 23 |
| Oracle MySQL Connector Net 8.0 |
| Oracle MySQL Connector NET 9 |
| Oracle MySQL Installer 8 for Windows |
| OrcaSlicer |
| ownCloud Desktop Client |
| Pandoc |
| PaperCut MF |
| PaperCut Mobility Print |
| PaperCut NG |
| Paperpile |
| Parallels Client 18 |
| Parallels Client 19 |
| Parallels Toolbox |
| Password Safe 3 |
| Path Copy Copy |
| Pausit Launcher |
| PDF Studio |
| PDF Studio Viewer |
| PDF24 Creator |
| PDFCreator |
| pdfFiller |
| PDFgear |
| PDFsam Basic |
| PDFsam Visual |
| PDF-Tools |
| PDF-XChange PRO |
| PeaZip |
| PerformanceTest |
| Perky Duck |
| Pexip |
| Pexip Infinity Connect |
| pgAdmin 4 |
| PicPick |
| Pidgin |
| Piriform CCleaner |
| Piriform CCleaner Slim |
| PL SQL Developer 15 |
| PLEdit 7 |
| PlanGrid |
| Plex Media Player |
| Plex Media Server |
| Poll Everywhere |
| Poly Lens Desktop App |
| Power BI ALM Toolkit |
| Preform |
| PrinterLogic Printer Installer Client |
| Private Internet Access |
| PrivadoVPN |
| proCertum SmartSign SimplySign Desktop |
| Project Plan 365 |
| Project Viewer 365 |
| Proton VPN |
| PRTG Desktop |
| PSPad |
| Publish or Perish |
| Puppet Development Kit |
| Publisher Select 3 |
| Putty |
| PuTTY CAC |
| Python 3.7 |
| Python 3.8 |
| Python 3.9 |
| Python 3.10 |
| Python 3.11 |
| Python 3.12 |
| Python 3.13 |
| QGIS |
| QGIS LTR |
| QNAP Qsync |
| Qurentis |
| R for Windows |
| RadiAnt DICOM viewer |
| Rainmeter |
| Rancher Desktop |
| Rarlab WinRAR |
| Raspberry Pi Imager |
| RBTools |
| Red Hat OpenJDK |
| Red Hat OpenJDK JRE |
| ReluxDesktop |
| Remote Ripple |
| RenderDoc |
| REAPER |
| REV Hardware Client |
| RingCentral App |
| RingCentral Phone |
| Robo 3T |
| RoboForm |
| Rocket.Chat |
| Royal TS 5 |
| Royal TS 6 |
| Royal TS 7 |
| RStudio 1.4 |
| RStudio 2022 |
| RStudio 2023 |
| Rstudio 2024 |
| RustDesk |
| RVTools |
| Salesforce CLI sf v2 |
| Samsung Smart Switch |
| Samsung Smart View |
| Saola Animate |
| ScaleFT |
| Screen InStyle |
| ScreenBeam Conference |
| ScreenCloud Player |
| ScreenToGif |
| Sejda PDF Desktop |
| SelfGuide Recorder |
| SharePoint Online Management Shell |
| Shotcut |
| SHOTPlus 6 |
| SHOTPlus Tunnel |
| SHOTPlus Underground |
| SideQuest |
| Signiant App |
| Simon Tatham Putty |
| Simple Sticky Notes |
| Simplenote |
| Sketchup Pro 2024 |
| Sketchup Pro 2025 |
| Skillbrains LightShot |
| Slido |
| SMath Studio |
| SmartFTP Client |
| Smartsheet desktop app |
| SnapCAD |
| SnapGene Viewer |
| Snagit 2018 |
| Snagit 2019 |
| Snagit 2020 |
| Snagit 2021 |
| Snagit 2023 |
| Snagit 2024 |
| Snapform Viewer |
| Snapmaker Luban |
| SnelStart |
| SoapUI |
| Softerra LDAP Administrator |
| Softerra LDAP Browser |
| Softland doPDF |
| SolarWinds Orion SDK |
| SonicWall Connect Tunnel |
| SonicWall NetExtender |
| Sophos Connect |
| South River Technologies WebDrive |
| Spark AR Player for Desktop |
| Splashtop Business |
| Squirrels Reflector 3 |
| Squirrels Reflector 4 |
| SRWare Iron |
| Steam |
| Stellarium |
| Storyboarder |
| Striata Reader |
| SuperOffice WebTools |
| SURF eduVPN Client |
| SURFdrive |
| Symphony Desktop Application |
| SyncBackFree |
| SyncBackPro |
| Synology Cloud Station Backup |
| Synology Cloud Station Drive |
| Synology Drive Client |
| Synology Evidence Integrity Authenticator |
| Sysprogs SmarTTY |
| Tabular Editor 2 |
| TablePlus |
| Tableau Desktop 2022 |
| Tableau Prep Builder 2022 |
| Tableau Prep Builder 2023 |
| Tailscale |
| Talkdesk |
| TDP SecureAnyBox Agent |
| TDP SecureAnyBox Launcher |
| TeamCity |
| TeamDrive |
| TeamSpeak client |
| TeamViewer Host |
| TED Notepad |
| TELUS Business Connect Phone |
| Temperature Technology T-TEC |
| Teracopy for Windows |
| TextExpander |
| TGRMN Software Bulk Rename Utility |
| The Document Foundation LibreOffice 6.2 |
| The Document Foundation LibreOffice 6.3 |
| The Document Foundation LibreOffice 6.4 |
| The Document Foundation LibreOffice 7.4 |
| The Document Foundation LibreOffice 7.4 Help Pack |
| The Document Foundation LibreOffice 7.5 |
| The Document Foundation LibreOffice 7.5 Help Pack |
| The Document Foundation LibreOffice 7.5 SDK |
| The Document Foundation LibreOffice 24 |
| The Document Foundation LibreOffice 24 Help Pack |
| ThinkPad TrackPoint Keyboard II Software |
| Thonny |
| Thycotic Application Control Agent |
| Thycotic Directory Services Agent |
| Thycotic Local Security Agent |
| Tidio |
| TightVNC |
| TI-Nspire CX CAS Student Software |
| TI-Nspire CX Premium Teacher Software |
| TI-SmartView CE-T |
| Topaz SigPlusExtLite |
| TortoiseGit |
| TortoiseSVN |
| TortoiseSVN ipv6 |
| TortoiseHg |
| TransIP STACK |
| Tribler |
| Trimble Connect |
| TSPrint Client |
| Turbo Studio |
| Turbo.net Desktop |
| TurboVNC |
| Typora |
| UEStudio |
| UltraCompare |
| UltraFinder |
| UltraFTP |
| Ultimaker Cura |
| UltraMon |
| UltraVNC |
| UltraViewer |
| UNIVERGE BLUE CONNECT |
| Unity Hub |
| UrBackup Client |
| Vagrant |
| VariCAD |
| VariCAD Viewer |
| VeraCrypt |
| VEXcode IQ 3 |
| VEXcode V5 |
| VideoScribe |
| Vim |
| Visual Paradigm Project Viewer |
| VMware Horizon Client 4.5 |
| VMware Horizon Client 4.6 |
| VMware Horizon Client 4.7 |
| VMware Horizon Client 4.8.1 |
| VMware Horizon Client 5.0 |
| VMware Horizon Client 5.2 |
| VMware Horizon Client 5.3 |
| VMware Horizon Client 5.4.2 |
| VMware Horizon Client 5.4.3 |
| VMware Horizon Client 5.5 |
| VMware Horizon Client 2006 |
| VMware Horizon Client 2012 |
| VMware Horizon Client 2103 |
| VMware Horizon Client 2209 |
| VMware Horizon View Client 3.5 |
| VMware Horizon View Client 5.4 |
| voidtools Everything |
| voidtools Everything Lite |
| VSCodium |
| Waterfox |
| Waterfox Classic |
| Wazuh Agent |
| Webstorm 2022.2 |
| WebStorm 2024 |
| Western Digital Dashboard |
| Wildix Collaboration |
| Win10Pcap |
| Wind Financial Terminal |
| WinDirStat |
| Windows 10 Codec Pack |
| WinMerge |
| WinSCP |
| WireGuard |
| Wireshark 4.4 |
| WiX Toolset 3 |
| WizTree |
| Wrike |
| Xamarin Mono for Windows |
| Xink Client AD |
| XMind 2020 |
| XMind 2021 |
| XMind 2022 |
| XMind Ltd XMind 2020 |
| XMind Ltd XMind 2021 |
| XnSoft XnConvert |
| XnSoft XnShell |
| XnSoft XnView Extended |
| XnSoft XnView Minimal |
| XnSoft XnView MP |
| XnSoft XnView Standard |
| Yubico Authenticator |
| Yubico PIV Tool |
| YubiKey Manager CLI |
| ZAC |
| ZBrush |
| Zeal |
| Zello |
| Zivver Office Plugin |
| Zoho WorkDrive |
| Zoom Client for Meetings |
| Zoom Player |
| Zoom Player Max |
| Zoom Plugin for Microsoft Outlook |
| Zoom Plugin for Skype for Business |
| Zoom Plugin for Windows Virtual Desktop Client |
| Zoom Rooms |
| Zoom VDI Universal Plugin |
| Zorus Archon Agent |
| Zotero |
| Zscaler Client Connector 3.6 |
| Zscaler Client Connector 3.9 |
| Zscaler Client Connector 4.0 |
| Zscaler Client Connector 4.1 |
| Zscaler Client Connector 4.3 |
| Zscaler Client Connector for VDI |
| Zulip |
| Zulu JDK 6 (LTS) |
| Zulu JDK 7 (LTS) |
| Zulu JDK 8 (LTS) |
| Zulu JDK 9 (STS) |
| Zulu JDK 10 (STS) |
| Zulu JDK 11 (LTS) |
| Zulu JDK 12 (STS) |
| Zulu JDK 13 (MTS) |
| Zulu JDK 15 (MTS) |
| Zulu JDK 16 (STS) |
| Zulu JDK 17 (LTS) |
| Zulu JDK 18 (STS) |
| Zulu JDK 20 (STS) |
| Zulu JRE 7 (LTS) |
| Zulu JRE 8 (LTS) |
| Zulu JRE 11 (LTS) |
| Zulu JRE 12 (STS) |
| Zulu JRE 13 (MTS) |
| Zulu JRE 15 (MTS) |
| Zulu JRE 17 (LTS) |