---
layout: Conceptual
title: Site prerequisites - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/configs/site-and-site-system-prerequisites
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
description: Learn how to configure a Windows computer as a Configuration Manager site system server.
ms.date: 2026-09-14T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 0aa9eaa7-145d-bd47-4949-de67bbc0e057
document_version_independent_id: 8d711ef0-26ae-3e74-ec89-27c2286b9619
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/plan-design/configs/site-and-site-system-prerequisites.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/plan-design/configs/site-and-site-system-prerequisites
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/plan-design/configs/site-and-site-system-prerequisites.md
cmProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/7696cda6-0510-47f6-8302-71bb5d2e28cf
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://authoring-docs-microsoft.poolparty.biz/devrel/69c76c32-967e-4c65-b89a-74cc527db725
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 1e12bcc5-fe72-343e-628d-65279a4644e6
---

# Site prerequisites - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

Windows-based computers require specific configurations to support their use as Configuration Manager site system servers.

For some products, like Windows Server Update Services (WSUS) for the software update point, you need to refer to the product documentation to identify additional prerequisites and limitations for use. Only configurations that directly apply for use with Configuration Manager are included here.

## General requirements and limitations

The following requirements apply to all site system servers:

- Each site system server must use a 64-bit OS. The only exception is the distribution point site system role, which you can install on some 32-bit operating systems.
- Site systems aren't supported on Server Core installations of any OS. An exception is that Server Core installations are supported for the distribution point. For more information, see [Supported operating systems for Configuration Manager site system servers](supported-operating-systems-for-site-system-servers).
- After a site system server is installed, it's not supported to change:

    - The domain name of the domain where the site system computer is located (also called a **domain rename**).
    - The domain membership of the computer.
    - The name of the computer.

        If you must change any of these items, first remove the site system role from the computer. Then reinstall the role after the change is complete. For changes affecting the site server, first uninstall the site. Then reinstall the site after the change is complete.
- Site system roles aren't supported on an instance of a Windows Server cluster. The only exception is the site database server. For more information, see [Use a SQL Server Always On failover cluster instance for the site database](../../servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database).

    The Configuration Manager setup process doesn't block installation of the site server role on a computer with the Windows role for Failover Clustering. SQL Server Always On availability groups require this role, so previously you couldn't colocate the site database on the site server. With this change, you can create a highly available site with fewer servers by using an availability group and a site server in passive mode. For more information, see [High availability options](../../servers/deploy/configure/high-availability-options).
- It's not supported to change the startup type or "Log on as" settings for any Configuration Manager service. If you do, you might prevent key services from running correctly.
- A best practice for security and operational resilience is to keep site system roles separate from the site server, rather than colocate them on the same computer.

## .NET version requirements

Starting in version 2303, site servers and specific site systems require Microsoft .NET Framework version 4.8 Before you run setup to install or update the site, first update .NET and restart the system.

Note

.NET Framework version 4.8 is required for the Configuration Manager 2403 upgrade.&gt; For more information, see [.NET Framework system requirements](/en-us/dotnet/framework/get-started/system-requirements).

### Site server

If the site server doesn't have any collocated roles that require .NET, it still requires .NET, but setup doesn't automatically install it. Make sure that at least .NET Framework version 4.8 is installed to the site server.

### Site systems

Important

If you're upgrading from System Center 2012 Configuration Manager R2 Service Pack 1, you need to manually verify that remote site systems have at least .NET version 4.6.2. Configuration Manager current branch setup skips the check in this scenario.

During Configuration Manager setup, if site systems have a version earlier than 4.6.2, you'll see a prerequisite check warning. This check is a warning instead of an error, because setup installs version 4.6.2. When .NET updates, it usually requires Windows to restart. Site systems send status message 4979 when a restart is required. Configuration Manager suppresses the restart; the system doesn't restart automatically.

The behavior differs for different types of site roles that require .NET:

- The following site system roles support in-place upgrade of .NET. After upgrading .NET, if a restart is required, it sends status message 4979. The role keeps running with the earlier .NET version. After Windows restarts, the role starts using the new .NET version.

    - Management point
    - Service connection point
    - Data warehouse service point
- The following site systems roles uninstall and reinstall when .NET is upgraded. During site update, site component manager removes the role, and then updates .NET. If a restart is required, it sends status message 4979. After restart, site component manager reinstalls the role with the new .NET version. The role could be unavailable while it waits for you to restart the server.

    - SMS Provider for the administration service
    - Reporting services point
    - Software update point

Note

Currently, you still need to enable the Windows feature for .NET Framework 3.5 on site systems that require it.

If site systems have at least version 4.6.2 but earlier than version 4.8, you'll also see a prerequisite check warning. Although this is a warning, .NET Framework version 4.8 or higher is ***required*** for Configuration Manager 2403 and later. Install the latest version of .NET version 4.8 to get the latest performance and security improvements. Configuration Manager setup doesn't automatically install .NET version 4.8.

Although the upgrade or installation will not be blocked if .NET Framework version 4.8 is not installed, certain roles, like the Service Connection Point and Management Point will not function properly without it

There's also a new [management insight](../../servers/manage/management-insights) to recommend site systems that don't yet have .NET version 4.8 or later.

### Managing system restarts for .NET updates

Whether you update .NET before updating the site, or set up updates it, .NET can require a restart to complete its installation. After .NET Framework is installed, it might require other updates. These updates might also require the server to restart.

If you need to manage the device restarts before you update the site, use the following recommended process:

1. Install the latest baseline .NET version. For example, install .NET version 4.8.
2. Restart the server.
3. Scan for software updates and install the latest .NET cumulative update.
4. Restart the server.
5. Update the site to the latest current branch version.

## Central administration site and primary site servers

For more information on all prerequisites including permissions, see [Prerequisites for installing a primary site or a CAS](../../servers/deploy/install/prerequisites-for-installing-sites#bkmk_PrereqPri). The following sections detail the prerequisite components that you need to install or enable.

### Windows Server roles and features for the site server

- .NET Framework 3.5
- Remote Differential Compression
- When you use a software update point on a server other than the site server, install the WSUS Administration Console on the site server.

### .NET Framework for the site server

- Enable the Windows feature for .NET Framework 3.5.
- Install a supported version of the .NET Framework. For more information, .NET version requirements.

### Windows ADK for the site server

- Before you install or upgrade a central administration site or primary site, install the version of the Windows Assessment and Deployment Kit (ADK) that's required by the version of Configuration Manager you're installing or upgrading to. For more information, see [Support for the Windows ADK](support-for-windows-adk).
- For more information about this requirement, see [Infrastructure requirements for OS deployment](../../../osd/plan-design/infrastructure-requirements-for-operating-system-deployment).

### Visual C++ Redistributable for the site server

- Starting in version 2503, Configuration Manager installs the Microsoft Visual C++ 2015-2022 redistributable package (14.40.33816.0) on each computer that installs a site server. In version 2107 and before, it installs the Visual C++ 2015-2019 version (14.28.29914.0).
- The CAS and primary sites require both the x86 and x64 versions of the applicable redistributable file.

### Microsoft ODBC Driver for SQL Server on the site server

Starting in version 2309, Configuration Manager requires the Microsoft ODBC Driver for SQL Server as a **prerequisite** when you create a **new site** or **update** an existing one. Configuration Manager doesn't manage updates for the ODBC driver. Keep it up to date on the site server.

For minimum required versions, validated versions, and versions with known blocking issues, see [Prerequisite checks - ODBC driver for SQL Server](../../servers/deploy/install/list-of-prerequisite-checks#odbc-driver-for-sql-server).

### Microsoft OLE DB Driver for SQL Server on the site server

Starting in version 2609, Configuration Manager automatically installs Microsoft OLE DB Driver for SQL Server on the site server.

### SQL Server Native Client for the site server

Starting in version 2609, Configuration Manager no longer requires SQL Server Native Client for the site server.

For version 2603 and earlier, Configuration Manager automatically installs SQL Server Native Client as a redistributable component when you install a new site. After the site is installed, Configuration Manager doesn't upgrade SQL Server Native Client. Make sure this component is up to date. For more information, see [Prerequisite checks - SQL Server Native Client](../../servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client).

## Secondary site server

### Windows Server roles and features for the secondary site server

- .NET Framework 3.5
- Remote Differential Compression

### .NET Framework for the secondary site server

- Enable the Windows feature for .NET Framework 3.5.
- Install a supported version of the .NET Framework. For more information, .NET version requirements.

### Visual C++ Redistributable for the secondary site server

- Starting in version 2107, Configuration Manager installs the Microsoft Visual C++ 2015-2019 redistributable package (14.28.29914.0) on each computer that installs a secondary site server. In version 2103 and earlier, it installs the Visual C++ 2013 version (12.0.40660.0).
- Secondary sites require only the x64 version.

### Default site system roles for the secondary site server

By default, a secondary site installs a **management point** and a **distribution point**. Make sure that the secondary site server meets the prerequisites for these site system roles.

### Microsoft ODBC Driver for SQL Server on the secondary site server

Starting in version 2309, Configuration Manager requires the Microsoft ODBC Driver for SQL Server as a **prerequisite** when you create a **new site** or **update** an existing one. Configuration Manager doesn't manage updates for the ODBC driver. Keep it up to date on the secondary site server.

For more information, see [Prerequisite checks - ODBC driver for SQL Server](../../servers/deploy/install/list-of-prerequisite-checks#odbc-driver-for-sql-server).

### SQL Server Native Client for the secondary site server

Starting in version 2609, SQL Server Native Client is no longer required.

For version 2603 and earlier, Configuration Manager automatically installs SQL Server Native Client as a redistributable component when you install a new site. After the site is installed, Configuration Manager doesn't upgrade SQL Server Native Client. Make sure this component is up to date. For more information, see [Prerequisite checks - SQL Server Native Client](../../servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client).

## Database server

### Remote Registry service for the site database server

During installation of the Configuration Manager site, enable the **Remote Registry** service on the computer that hosts the site database.

### SQL Server for the site database server

- Before you install a CAS or primary site, install a supported version of SQL Server to host the site database. For more information, see [Supported SQL Server versions](support-for-sql-server-versions).
- Before you install a secondary site:

    - You can install a supported version of SQL Server.
    - You can choose to have Configuration Manager install SQL Server Express. Make sure that the server meets the requirements to run SQL Server Express.

### Microsoft ODBC Driver for SQL Server on the database server

Starting in version 2309, Configuration Manager requires the Microsoft ODBC Driver for SQL Server as a **prerequisite** when you create a **new site** or **update** an existing one. Configuration Manager doesn't manage updates for the ODBC driver. Keep it up to date on the database server.

For more information, see [Prerequisite checks - ODBC driver for SQL Server](../../servers/deploy/install/list-of-prerequisite-checks#odbc-driver-for-sql-server).

### SQL Server Native Client for the site database server

Starting in version 2609, SQL Server Native Client is no longer required.

For version 2603 and earlier, Configuration Manager automatically installs SQL Server Native Client as a redistributable component when you install a new site. After the site is installed, Configuration Manager doesn't upgrade SQL Server Native Client. Make sure this component is up to date. For more information, see [Prerequisite checks - SQL Server Native Client](../../servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client).

## SMS Provider server

### Windows ADK for the SMS Provider

- The server where you install an instance of the SMS Provider must have a supported version of the Windows ADK. For more information, see [Support for the Windows ADK](support-for-windows-adk).
- For more information about this requirement, see [Infrastructure requirements for operating system deployment](../../../osd/plan-design/infrastructure-requirements-for-operating-system-deployment).

### Windows Server roles and features for the SMS Provider

Web Server (IIS): Every provider attempts to install the [administration service](../../../develop/adminservice/overview). This service has a dependency on IIS to bind a certificate to HTTPS port 443. Configuration Manager uses IIS APIs to check this certificate configuration. If you configure the site for [Enhanced HTTP](../hierarchy/enhanced-http), Configuration Manager uses IIS APIs to bind the site-generated certificate. Unless the server already has a PKI-based certificate, the site automatically uses the site's self-signed certificate.

### .NET Framework for the SMS Provider

If you're using the [administration service](../../../develop/adminservice/overview), the server that hosts the SMS Provider role requires .NET 4.5 or later.  Starting in version 2107, this role requires .NET version 4.6.2, and version 4.8 is recommended. For more information, .NET version requirements.

### Microsoft ODBC Driver for SQL Server on the SMS Provider

Starting in version 2309, Configuration Manager requires the Microsoft ODBC Driver for SQL Server as a **prerequisite** when you create a **new site** or **update** an existing one. Configuration Manager doesn't manage updates for the ODBC driver. Keep it up to date on the computer that hosts the SMS Provider.

For more information, see [Prerequisite checks - ODBC driver for SQL Server](../../servers/deploy/install/list-of-prerequisite-checks#odbc-driver-for-sql-server).

### Microsoft OLE DB Driver for SQL Server on the SMS Provider

Starting in version 2609, Configuration Manager automatically installs Microsoft OLE DB Driver for SQL Server on the computer that hosts the SMS Provider.

### SQL Server Native Client for the SMS Provider

Starting in version 2609, SQL Server Native Client is no longer required.

For version 2603 and earlier, Configuration Manager automatically installs SQL Server Native Client as a redistributable component when you install a new site. After the site is installed, Configuration Manager doesn't upgrade SQL Server Native Client. Make sure this component is up to date. For more information, see [Prerequisite checks - SQL Server Native Client](../../servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client).

## Data warehouse service point

For more information on the prerequisites for this role, see [The data warehouse service point](../../servers/manage/data-warehouse#prerequisites).

### .NET Framework for the DWSP

Install a supported version of the .NET Framework. For more information, .NET version requirements.

### SQL Server for the DWSP

The data warehouse database requires SQL Server 2012 or later. The edition can be Standard, Enterprise, or Datacenter. The SQL Server version for the data warehouse doesn't need to be the same as the site database server or the reporting services point.

## Distribution point

### Windows Server roles and features for the DP

- Remote Differential Compression

Note

When the distribution point transfers content, it transfers using the **Background Intelligent Transfer Service** (BITS) built into Windows. The distribution point role doesn't require the optional BITS IIS Server Extension feature to be installed, because the client doesn't upload information to it.

#### IIS configuration for the DP

- Application Development:

    - ISAPI Extensions
- Security:

    - Windows Authentication
- IIS 6 Management Compatibility:

    - IIS 6 Metabase Compatibility
    - IIS 6 WMI Compatibility

By default, IIS uses request filtering to block several file name extensions and folder locations from access by HTTP or HTTPS communication. On a distribution point, this configuration prevents clients from downloading packages with blocked extensions or folder locations. For more information, see [IIS request filtering for distribution points](../network/prepare-windows-servers#iis-request-filtering-for-distribution-points).

Distribution points require that IIS allows the following HTTP verbs:

- GET
- HEAD
- PROPFIND

### Visual C++ Redistributable for the DP

- Starting in version 2107, Configuration Manager installs the Microsoft Visual C++ 2015-2019 redistributable package (14.28.29914.0) on each computer that hosts a distribution point. In version 2103 and earlier, it installs the Visual C++ 2013 version (12.0.40660.0).
- The version that's installed depends on the computer's platform (x86 or x64).

### Add PXE support for the DP

There are two options to support PXE on a distribution point:

- Enable the Configuration Manager PXE responder without Windows Deployment Service.
- Install and configure the Windows Deployment Services (WDS) Windows Server role.

    Note

    WDS installs and configures automatically when you enable a distribution point to support PXE.

For more information, see [Install and configure distribution points](../../servers/deploy/configure/install-and-configure-distribution-points#bkmk_config-pxe).

### Add multicast support for the DP

- Install and configure the Windows Deployment Services (WDS) Windows Server role.

    Note

    WDS installs and configures automatically when you enable a distribution point to support multicast.
- Starting in version 2609, SQL Server Native Client isn't required for multicast support. For version 2603 and earlier, make sure the SQL Server Native Client is installed and up to date. For more information, see [Prerequisite checks - SQL Server Native Client](../../servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client).

## Endpoint Protection point

### Windows Server roles and features for the endpoint protection point

- .NET Framework 3.5
- Windows Defender features (Windows Server 2016 or later)

### Microsoft ODBC Driver for SQL Server on the endpoint protection point

Starting in version 2309, Configuration Manager requires the Microsoft ODBC Driver for SQL Server as a **prerequisite** when you create a **new site** or **update** an existing one. Configuration Manager doesn't manage updates for the ODBC driver. Keep it up to date on the computer that hosts the endpoint protection point.

For more information, see [Prerequisite checks - ODBC driver for SQL Server](../../servers/deploy/install/list-of-prerequisite-checks#odbc-driver-for-sql-server).

### SQL Server Native Client for the endpoint protection point

Starting in version 2609, SQL Server Native Client is no longer required.

For version 2603 and earlier, Configuration Manager automatically installs SQL Server Native Client as a redistributable component when you install a new site. After the site is installed, Configuration Manager doesn't upgrade SQL Server Native Client. Make sure this component is up to date. For more information, see [Prerequisite checks - SQL Server Native Client](../../servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client).

## Fallback status point

### Windows Server roles and features for the FSP

Depending upon the version of Windows Server, enable one of the following features:

- BITS Server Extensions and the automatically selected options
- Background Intelligent Transfer Services (BITS) and the automatically selected options

#### IIS configuration

The default IIS configuration is required with the following additions:

- IIS 6 Management Compatibility:

    - IIS 6 Metabase Compatibility

## Management point

### Windows Server roles and features for the MP

Depending upon the version of Windows Server, enable one of the following features:

- BITS Server Extensions and the automatically selected options
- Background Intelligent Transfer Services (BITS) and the automatically selected options

#### IIS configuration for the MP

- Application Development:

    - ISAPI Extensions
- Security:

    - Windows Authentication
- IIS 6 Management Compatibility:

    - IIS 6 Metabase Compatibility
    - IIS 6 WMI Compatibility

To make sure that clients can successfully communicate with a management point, make sure IIS allows the following HTTP verbs:

- GET
- POST
- CCM\_POST
- HEAD
- PROPFIND

### .NET Framework for the MP

Install a supported version of the .NET Framework. For more information, .NET version requirements.

### Microsoft ODBC Driver for SQL Server on the MP

Starting in version 2309, Configuration Manager requires the Microsoft ODBC Driver for SQL Server as a **prerequisite** when you create a **new site** or **update** an existing one. Configuration Manager doesn't manage updates for the ODBC driver. Keep it up to date on the computer that hosts the management point.

For more information, see [Prerequisite checks - ODBC driver for SQL Server](../../servers/deploy/install/list-of-prerequisite-checks#odbc-driver-for-sql-server).

### Microsoft OLE DB Driver for SQL Server on the MP

Starting in version 2609, Configuration Manager automatically installs Microsoft OLE DB Driver for SQL Server on the computer that hosts the management point.

### SQL Server Native Client for the MP

Starting in version 2609, SQL Server Native Client is no longer required.

For version 2603 and earlier, Configuration Manager automatically installs SQL Server Native Client as a redistributable component when you install a new site. After the site is installed, Configuration Manager doesn't upgrade SQL Server Native Client. Make sure this component is up to date. For more information, see [Prerequisite checks - SQL Server Native Client](../../servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client).

## Reporting services point

### .NET Framework for the RSP

Install a supported version of the .NET Framework. For more information, .NET version requirements.

### SQL Server Reporting Services for the RSP

- Install and configure at least one instance of SQL Server to support SQL Server Reporting Services.
- The instance that you use for SQL Server Reporting Services can be the same instance you use for the site database.
- The instance that you use can be shared with System Center products. The System Center products can't have restrictions for sharing the instance of SQL Server.

### Microsoft ODBC Driver for SQL Server on the RSP

Starting in version 2309, Configuration Manager requires the Microsoft ODBC Driver for SQL Server as a **prerequisite** when you create a **new site** or **update** an existing one. Configuration Manager doesn't manage updates for the ODBC driver. Keep it up to date on the computer that hosts the reporting services point.

For more information, see [Prerequisite checks - ODBC driver for SQL Server](../../servers/deploy/install/list-of-prerequisite-checks#odbc-driver-for-sql-server).

### SQL Server Native Client for the RSP

Starting in version 2609, SQL Server Native Client is no longer required.

For version 2603 and earlier, Configuration Manager automatically installs SQL Server Native Client as a redistributable component when you install a new site. After the site is installed, Configuration Manager doesn't upgrade SQL Server Native Client. Make sure this component is up to date. For more information, see [Prerequisite checks - SQL Server Native Client](../../servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client).

## Service connection point

### .NET Framework for the SCP

- Enable the Windows feature for .NET Framework 3.5.
- Install a supported version of the .NET Framework. For more information, .NET version requirements.

### Visual C++ Redistributable for the SCP

- Starting in version 2107, Configuration Manager installs the Microsoft Visual C++ 2015-2019 redistributable package (14.28.29914.0) on the service connection point. In version 2103 and earlier, it installs the Visual C++ 2013 version (12.0.40660.0).

### Microsoft ODBC Driver for SQL Server on the SCP

Starting in version 2309, Configuration Manager requires the Microsoft ODBC Driver for SQL Server as a **prerequisite** when you create a **new site** or **update** an existing one. Configuration Manager doesn't manage updates for the ODBC driver. Keep it up to date on the computer that hosts the service connection point.

For more information, see [Prerequisite checks - ODBC driver for SQL Server](../../servers/deploy/install/list-of-prerequisite-checks#odbc-driver-for-sql-server).

### SQL Server Native Client for the SCP

Starting in version 2609, SQL Server Native Client is no longer required.

For version 2603 and earlier, Configuration Manager automatically installs SQL Server Native Client as a redistributable component when you install a new site. After the site is installed, Configuration Manager doesn't upgrade SQL Server Native Client. Make sure this component is up to date. For more information, see [Prerequisite checks - SQL Server Native Client](../../servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client).

## Software update point

### Windows Server roles and features for the SUP

- .NET Framework 3.5
- The default IIS configuration is required.

### .NET Framework for the SUP

- Enable the Windows feature for .NET Framework 3.5.
- Install a supported version of the .NET Framework. For more information, .NET version requirements.

### Windows Server Update Services (WSUS) for the SUP

Install the WSUS server role. For more information, see [Plan for software updates](../../../sum/plan-design/plan-for-software-updates).

Note

When you use a software update point on a remote site system, install the WSUS Administration Console on the site server.

### Microsoft ODBC Driver for SQL Server on the SUP

Starting in version 2309, Configuration Manager requires the Microsoft ODBC Driver for SQL Server as a **prerequisite** when you create a **new site** or **update** an existing one. Configuration Manager doesn't manage updates for the ODBC driver. Keep it up to date on the computer that hosts the software update point.

For more information, see [Prerequisite checks - ODBC driver for SQL Server](../../servers/deploy/install/list-of-prerequisite-checks#odbc-driver-for-sql-server).

### SQL Server Native Client for the SUP

Starting in version 2609, SQL Server Native Client is no longer required.

For version 2603 and earlier, Configuration Manager automatically installs SQL Server Native Client as a redistributable component when you install a new site. After the site is installed, Configuration Manager doesn't upgrade SQL Server Native Client. Make sure this component is up to date. For more information, see [Prerequisite checks - SQL Server Native Client](../../servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client).

## State migration point

### Windows Server roles and features for the SMP

- .NET Framework 3.5

    - HTTP Activation (and automatically selected options)
    - ASP.NET 4.5

#### IIS configuration for the SMP

- Common HTTP Features:

    - Default Document
- Application Development:

    - ASP.NET 3.5 (and automatically selected options)
    - .NET Extensibility 3.5
    - ASP.NET 4.5 (and automatically selected options)
    - .NET Extensibility 4.5
- IIS 6 Management Compatibility:

    - IIS 6 Metabase Compatibility

### .NET Framework for the SMP

- Enable the Windows feature for .NET Framework 3.5.
- Install a supported version of the .NET Framework. For more information, .NET version requirements.

### Microsoft ODBC Driver for SQL Server on the SMP

Starting in version 2309, Configuration Manager requires the Microsoft ODBC Driver for SQL Server as a **prerequisite** when you create a **new site** or **update** an existing one. Configuration Manager doesn't manage updates for the ODBC driver. Keep it up to date on the computer that hosts the state migration point.

For more information, see [Prerequisite checks - ODBC driver for SQL Server](../../servers/deploy/install/list-of-prerequisite-checks#odbc-driver-for-sql-server).

### SQL Server Native Client for the SMP

Starting in version 2609, SQL Server Native Client is no longer required.

For version 2603 and earlier, Configuration Manager automatically installs SQL Server Native Client as a redistributable component when you install a new site. After the site is installed, Configuration Manager doesn't upgrade SQL Server Native Client. Make sure this component is up to date. For more information, see [Prerequisite checks - SQL Server Native Client](../../servers/deploy/install/list-of-prerequisite-checks#sql-server-native-client).