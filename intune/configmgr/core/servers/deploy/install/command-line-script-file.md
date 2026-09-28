---
layout: Conceptual
title: Unattended setup script file keys - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/command-line-script-file
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
description: Specify the keys and values in the INI installation script file for an unattended setup of Configuration Manager.
ms.date: 2022-02-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: reference
ms.collection: tier3
locale: en-us
document_id: 6418cabb-2c24-d1d8-4dd5-b92389921178
document_version_independent_id: feaed85c-1bec-4921-5278-8acf70bb13c5
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/install/command-line-script-file.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/install/command-line-script-file
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/install/command-line-script-file.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/c6f99e62-1cf6-4b71-af9b-649b05f80cce
- https://authoring-docs-microsoft.poolparty.biz/devrel/1e69816a-aaaa-474e-a36f-3ec7790fadc3
- https://authoring-docs-microsoft.poolparty.biz/devrel/cbe4ca68-43ac-4375-aba5-5945a6394c20
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/3f56b378-07a9-4fa1-afe8-9889fdc77628
- https://authoring-docs-microsoft.poolparty.biz/devrel/ae012320-d2b3-47d8-abdc-898a64d069a9
- https://authoring-docs-microsoft.poolparty.biz/devrel/ced846cc-6a3c-4c8f-9dfb-3de0e90e2742
platformId: 3faf145d-5d55-ca7e-334b-09217db6154b
---

# Unattended setup script file keys - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

This article defines all of the keys and values to specify in the `.ini` installation script file. Use this file with the `/SCRIPT` command-line option to do an unattended installation or recovery of a Configuration Manager site. The tables in this article show:

- The available setup script keys and their corresponding values
- If they're required
- Which type of installation they're used for
- A short description of the key

For more information, see the following articles:

- [Command-line overview](use-a-command-line-to-install-sites)
- [Setup command-line options](command-line-options-for-setup)

Specify the section names in square brackets (`[]`): `[<Section name>]`. For example, `[Identification]`.

When you provide values for keys, the name of the key must be followed by an equal sign (`=`) and the value for the key: `<Key name>=<Value>`. For example, `CDLatest=1`. Make sure the keys are under the appropriate section.

Each section and each value needs to be unique in a single script. For example, there can only be one `[Identification]` section and only one `Action` key.

## Supported actions

A script is primarily defined by the `Action` key in the `Identification` section. The following list includes all of the currently supported actions for running setup unattended:

- `InstallCAS`: Install a central administration site (CAS)
- `InstallPrimarySite`: Install a primary site
- `ManageLanguages`: Add or remove client and server languages
- `RecoverPrimarySite`: Recovery a primary site
- `RecoverCCAR`: Recover a CAS

## Install a site

### `Identification` section for site install

Depending upon the type of site you're installing, include the following keys with the appropriate values in the `Identification` section:

| Key name | Required | Values | Details |
| --- | --- | --- | --- |
| `Action` | Yes | - `InstallPrimarySite`- `InstallCAS` | - Install a primary site.- Install a central administration site (CAS) |
| `CDLatest` | Yes ^2^ | `1`: Setup runs from CD.Latest | When you run setup from the [`CD.Latest` folder](../../manage/the-cd.latest-folder), include this key and value. This value tells setup that you're using media from `CD.Latest`. |

#### Note 2: `CDLatest` required

The `CDLatest` key is only required when you run setup from the `CD.Latest` folder to install a *primary site* or a *central administration site*. For more information, see [About the command-line script file](use-a-command-line-to-install-sites#about-the-command-line-script-file).

### `Options` section for site install

Include the following keys in the **Options** section to install a site:

| Key name | Required | Values | Details |
| --- | --- | --- | --- |
| `ProductID` | Yes | - `xxxxx-xxxxx-xxxxx-xxxxx-xxxxx`: A valid product key with dashes- `Eval`: Install the evaluation version | The type of license to install. |
| `SiteCode` | Yes | Three character code, for example `XYZ` | The three-character site code that uniquely identifies the site in the hierarchy. |
| `SiteName` | Yes | A site name | The friendly name for this site to help identify it. |
| `SMSInstallDir` | Yes | Local directory path | The installation folder for the Configuration Manager program files. |
| `SDKServer` | Yes | SMS Provider FQDN | The FQDN of the first server to host the SMS Provider. |
| `PrerequisiteComp` | Yes | - `0`: Download- `1`: Already downloaded | Specify whether prerequisite files have already been downloaded. If you use a value of `0`, setup downloads the files. |
| `PrerequisitePath` | Yes | Local directory path | The path to the prerequisite files. Depending on the `PrerequisiteComp` value, setup uses this path to store downloaded files or to locate previously downloaded files. |
| `AdminConsole` | Yes | - `0`: Don't install- `1`: Install | Specify whether to install the Configuration Manager console on the site server. |
| `JoinCEIP` | Yes | `0` | While support for the Customer Experience Improvement Program (CEIP) was removed from the product, this key is still required. |
| `MobileDeviceLanguage` | Yes | - `0`: Don't install- `1`: Install | Specify whether the mobile device client languages are installed. |

When you install a site, you can also specify the keys to manage languages, such as `AddServerLanguages` or `AddClientLanguages`. For more information, see `Options` section for languages.

The following keys in the `Options` section are specific to a *primary site*:

| Key name | Required | Values | Details |
| --- | --- | --- | --- |
| `ManagementPoint` | No | MP FQDN | The FQDN of the server that will host the first management point (MP) site system role. |
| `ManagementPointProtocol` | No | `HTTPS` or `HTTP` | The protocol to use for the MP. |
| `DistributionPoint` | No | DP FQDN | The FQDN of the server that will host the first distribution point (DP) site system role. |
| `DistributionPointProtocol` | No | `HTTPS` or `HTTP` | The protocol to use for the DP. |
| `DistributionPointInstallIIS` | No | - `0`: Don't install- `1`: Install | Specify whether to install IIS on the DP. |
| `RoleCommunicationProtocol` | Yes | `EnforceHTTPS` or `HTTPorHTTPS` | Specify whether to configure all site systems to accept only HTTPS communication from clients, or to configure the communication method for each site system role. When you select `EnforceHTTPS`, clients need a valid public key infrastructure (PKI) certificate for client authentication. |
| `ClientsUsePKICertificate` | Yes | - `0`: Don't use- `1`: Use | Specify whether clients will use a client PKI certificate to communicate with site system roles. |
| `UseFQDN` | No | - `0`: Don't use- `1`: Use | Specify whether the site systems' FQDN is for use on the internet. |
| `ParentSiteCode` | No | Site code | When you're adding a child primary site to an existing hierarchy, specify the site code of the CAS. |
| `ParentSiteServer` | No | FQDN | When you're adding a child primary site to an existing hierarchy, specify the FQDN of the CAS server. |

### `SQLConfigOptions` section for site install

Include the following keys in the `SQLConfigOptions` section to install a site:

| Key name | Required | Values | Details |
| --- | --- | --- | --- |
| `SQLServerName` | Yes | FQDN of SQL Server | The name of the server or clustered instance that's running SQL Server to host the site database. |
| `DatabaseName` | Yes | Name orInstance\Name | The name of the SQL Server database to create or use. If it's on the default instance, just specify the database name. Otherwise specify the instance and name. |
| `SQLServerPort` | No | Port number | The port that SQL Server uses. By default, it uses 1433. |
| `SQLSSBPort` | No | Port number | The SQL Server Service Broker (SSB) port. By default, SSB uses TCP port 4022. |
| `SQLDataFilePath` | No | Local directory path | An alternate location to create the database .mdb file. |
| `SQLLogFilePath` | No | Local directory path | An alternate location to create the database .ldf log file. |
| `AGBackupShare` | No | Network share path | The network location for sharing database backups when creating the site database in an Availability Group. The backup share is only needed if automatic seeding is not set. |

### `CloudConnectorOptions` section for site install

Include the following keys in the `CloudConnectorOptions` section to install a site:

| Key name | Required | Values | Details |
| --- | --- | --- | --- |
| `CloudConnector` | Yes | - `0`: Don't install- `1`: Install | Specify whether to install a service connection point (SCP) at this site. Because you can only install the SCP at the top-tier site of a hierarchy, set this value to `0` for a child primary site. |
| `CloudConnectorServer` | Yes\* | SCP FQDN | The FQDN of the server that will host the SCP role. \* Only required when `CloudConnector` equals `1`. |
| `UseProxy` | Yes\* | - `0`: No proxy- `1`: Use proxy | Specify whether the SCP uses a proxy server. \* Only required when `CloudConnector` equals `1`. |
| `ProxyName` | Yes\* | Proxy FQDN | The FQDN of the proxy server that the SCP uses. \* Only required when `UseProxy` equals `1`. |
| `ProxyPort` | Yes\* | Port number | The port number of the proxy server that the SCP uses. \* Only required when `UseProxy` equals `1`. |

### `SABranchOptions` section for site install

Include the following keys in the `SABranchOptions` section to install a site:

| Key name | Required | Values | Details |
| --- | --- | --- | --- |
| `SAActive` | Yes | - `0`: You don't have SA- `1`: SA is active | Specify if you have active Software Assurance (SA). For more information, see [Product and licensing FAQ](../../../understand/product-and-licensing-faq). |
| `CurrentBranch` | Yes | - `0`: Install the LTSB- `1`: Install current branch | Specify whether to use Configuration Manager current branch or long-term servicing branch (LTSB). For more information, see [Which branch of Configuration Manager should I use?](../../../understand/which-branch-should-i-use) |
| `SAExpiration` | No | Date | The date when SA expires, used as a convenient reminder of that date. For more information, see [Licensing and branches](../../../understand/learn-more-editions). |

### `HierarchyExpansionOption` section for site expansion

When you're installing a CAS to expand a standalone primary site into a hierarchy, use the following keys in the `HierarchyExpansionOption` section:

| Key name | Required | Values | Details |
| --- | --- | --- | --- |
| `CCARSiteServer` | No | CAS FQDN | The FQDN of the CAS that a primary site attaches to when it joins the Configuration Manager hierarchy. Specify the CAS during setup. |
| `CASRetryInterval` | No | Minutes | If the connection to the CAS fails, the primary site waits this number of minutes, and then reattempts the connection. |
| `WaitForCASTimeout` | No | `0` to `100` | The maximum timeout value in minutes for a primary site to connect to the CAS. |
| `UseDistributionView` | No | - `0`: Don't enable- `1`: Enable | Specify whether to use [distributed views](../../../plan-design/hierarchy/database-replication#distributed-views) to optimize database replication. |
| `JoinPrimarySiteName` | No | Site server FQDN | The FQDN of the primary site server to expand. |

## Manage languages

### `Identification` section for languages

Include the following key in the `Identification` section to manage languages:

| Key name | Required | Values | Details |
| --- | --- | --- | --- |
| `Action` | Yes | `ManageLanguages` | Manages the server, client, and mobile client language support at a site. |

### `Options` section for languages

Include the following keys in the `Options` section to manage languages:

| Key name | Required | Values | Details |
| --- | --- | --- | --- |
| `AddServerLanguages` | No | ^See note 1^ | The server languages that will be available for the Configuration Manager console, reports, and other objects. |
| `AddClientLanguages` | No | ^See note 1^ | The languages that will be available to client computers. |
| `DeleteServerLanguages` | No | ^See note 1^ | The languages to remove. They'll no longer be available for the Configuration Manager console, reports, and other objects. |
| `DeleteClientLanguages` | No | ^See note 1^ | The languages to remove, and which will no longer be available to client computers. English is available by default, you can't remove it. |
| `MobileDeviceLanguage` | Yes | - `0`: Don't install- `1`: Install | Specify whether the mobile device client languages are installed. |
| `PrerequisiteComp` | Yes | - `0`: Download- `1`: Already downloaded | Specify whether prerequisite files have already been downloaded. For example, if you use a value of `0`, setup downloads the files. |
| `PrerequisitePath` | Yes | Local directory path | The path to the prerequisite files. Depending on the `PrerequisiteComp` value, setup uses this path to store downloaded files or to locate previously downloaded files. |
| `ResetSecSiteLangs` | No | - `0`: Don't reset- `1`: Reset | Reset the language packs installed at a secondary site. |

#### Note 1: Supported language values

Use the *three-letter code* for the [server languages](language-packs#server-languages) or [client languages](language-packs#client-languages) that Configuration Manager supports. For example, to add support for German on the client, specify the following key and value pair: `AddClientLanguages=DEU`

English (`ENG`) is available by default. You don't have to add it, and you can't remove it.

## Recover a site

### `Identification` section for site recovery

Depending upon the type of site you're recovering, include the following keys with the appropriate values in the `Identification` section:

| Key name | Required | Values | Details |
| --- | --- | --- | --- |
| `Action` | Yes | - `RecoverPrimarySite`- `RecoverCCAR` | - Recover a primary site- Recover a CAS |
| `CDLatest` | Yes ^3^ | `1`: Setup runs from CD.Latest | When you run setup from the [CD.Latest folder](../../manage/the-cd.latest-folder), include this key and value. This value tells setup that you're using media from CD.Latest. |

#### Note 3: `CDLatest` required

The `CDLatest` key is only required when you run setup from the `CD.Latest` folder to recover a site. For more information, see [About the command-line script file](use-a-command-line-to-install-sites#about-the-command-line-script-file).

### `RecoveryOptions` section for site recovery

Include the following keys in the `RecoveryOptions` section to recover a site:

| Key name | Required | Values | Details |
| --- | --- | --- | --- |
| `ServerRecoveryOptions` | Yes | - `1`: Site server and SQL Server- `2`: Site server only- `4`: SQL Server only | What components to recover. ^See note 4^ |
| `DatabaseRecoveryOptions` | Yes\* | - `10`: Restore from backup- `20`: Manually recovered- `40`: Create new database- `80`: Skip | Specify how setup recovers the site database in SQL Server. \* Only required when `ServerRecoveryOptions` is `1` or `4`. |
| `ReferenceSite` | Yes\* | FQDN | The reference primary site that the CAS uses to recover global data. \* Only required when `DatabaseRecoveryOptions` is `40`. ^See note 5^ |
| `SiteServerBackupLocation` | No | Directory path | The path to the site server backup set. If you don't specify a value, setup reinstalls the site without restoring it from a backup set. |
| `BackupLocation` | Yes\* | Directory path | The path to the site database backup set. \* Required when `ServerRecoveryOptions` is `1` or `4`, and `DatabaseRecoveryOptions` is `10`. |

#### Note 4: `ServerRecoveryOptions` value notes

- `1` or `2`: To recover the site by using a site backup, specify a value for `SiteServerBackupLocation`. If you don't specify a value, setup reinstalls the site without restoring it from a backup set.
- `4`: The `BackupLocation` key is required when you configure a value of `10` for the `DatabaseRecoveryOptions` key, which is to restore the site database from backup.

#### Note 5: `ReferenceSite` value notes

- If the database backup is older than the change-tracking retention period, or when you recover the site without a backup, specify the reference primary site that the CAS uses to recover global data.
- When you don't specify a reference site, and the backup is older than the change-tracking retention period, all primary sites are reinitialized with the restored data from the CAS.
- When you don't specify a reference site, and the backup is within the change-tracking retention period, only changes that are made after the backup are replicated from primary sites. When there are conflicting changes from different primary sites, the CAS uses the first one that it receives.

### `Options` section for site recovery

Many of the keys in the `Options` section are also required for site recovery. For more information, see `Options` section for site install. The following table summarizes the keys in the `Options` section for site recovery:

| Key name | Required | Comment |
| --- | --- | --- |
| `ProductID` | Yes |  |
| `SiteCode` | Yes | Use the same site code that it used before the failure. |
| `SiteName` | No |  |
| `SMSInstallDir` | Yes |  |
| `SDKServer` | Yes | Use the same server that hosted this role before the failure. |
| `PrerequisiteComp` | Yes |  |
| `PrerequisitePath` | Yes |  |
| `AdminConsole` | Yes\* | \* Only required when `ServerRecoveryOptions` is `1` or `2`. |
| `JoinCEIP` | Yes |  |

### `SQLConfigOptions` section for site recovery

Many of the keys in the `SQLConfigOptions` section are also required for site recovery. For more information, see `SQLConfigOptions` section for site install. The following table summarizes the keys in the `SQLConfigOptions` section for site recovery:

| Key name | Required | Comment |
| --- | --- | --- |
| `SQLServerName` | Yes | Use the same server that hosted the site database before the failure. |
| `DatabaseName` | Yes | Use the same database name that was used before the failure. |
| `SQLSSBPort` | Yes | Use the same port that was used before the failure. |
| `SQLDataFilePath` | No |  |
| `SQLLogFilePath` | No |  |

### `CloudConnectorOptions` section for site recovery

Many of the keys in the `CloudConnectorOptions` section are also required for site recovery. For more information, see `CloudConnectorOptions` section for site install. The following table summarizes the keys in the `CloudConnectorOptions` section for site recovery:

| Key name | Required | Comment |
| --- | --- | --- |
| `CloudConnector` | Yes |  |
| `CloudConnectorServer` | Yes\* | \* Only required when `CloudConnector` equals `1`. |
| `UseProxy` | Yes\* | \* Only required when `CloudConnector` equals `1`. |
| `ProxyName` | Yes\* | \* Only required when `UseProxy` equals `1`. |
| `ProxyPort` | Yes\* | \* Only required when `UseProxy` equals `1`. |

### `HierarchyExpansionOption` section for site recovery

Many of the keys in the `HierarchyExpansionOption` section are also required for site recovery. For more information, see `HierarchyExpansionOption` section for site install. The following table summarizes the keys in the `HierarchyExpansionOption` section for site recovery:

| Key name | Required | Comment |
| --- | --- | --- |
| `CCARSiteServer` | Yes\* | \* Only required if the primary site was attached to a CAS before the failure. |
| `CASRetryInterval` | No |  |
| `WaitForCASTimeout` | No |  |

## Examples

### Example script to install a primary site

```ini
[Identification]
Action=InstallPrimarySite
CDLatest=1

[Options]
ProductID=Eval
SiteCode=XYZ
SiteName=Contoso eval site
SMSInstallDir=D:\Program Files\Microsoft Configuration Manager
SDKServer=cmsite.contoso.com
PrerequisiteComp=0
PrerequisitePath=C:\Sources\Redist
AdminConsole=1
JoinCEIP=0
ManagementPoint=cmsite.contoso.com
ManagementPointProtocol=HTTP
DistributionPoint=cmsite.contoso.com
DistributionPointProtocol=HTTP
DistributionPointInstallIIS=1
RoleCommunicationProtocol=HTTPorHTTPS
ClientsUsePKICertificate=0
MobileDeviceLanguage=0

[SQLConfigOptions]
SQLServerName=cmsql.contoso.com
SQLServerPort=1433
DatabaseName=CM_XYZ
SQLSSBPort=4022
SQLDataFilePath=E:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\DATA\
SQLLogFilePath=E:\Program Files\Microsoft SQL Server\MSSQL15.MSSQLSERVER\MSSQL\DATA\

[CloudConnectorOptions]
CloudConnector=1
CloudConnectorServer=cmsite.contoso.com
UseProxy=0

[SABranchOptions]
SAActive=1
CurrentBranch=1
```