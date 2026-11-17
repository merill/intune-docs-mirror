---
layout: Conceptual
title: Release notes - Configuration Manager | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/install/release-notes
author: iceorbital
ms.author: acabello
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: configuration-manager
feedback_product_url: https://feedbackportal.microsoft.com/feedback/forum/4669adfc-ee1b-ec11-b6e7-0022481f8472
ms.reviewer:
- umaikhan
- brianhun
- payur
- hugowu
- qiani
description: Learn about urgent issues that aren't yet fixed in the product or covered in a Microsoft Support knowledge base article.
ms.date: 2026-11-16T00:00:00.0000000Z
ms.subservice: core-infra
ms.topic: release-notes
ms.collection: tier3
locale: en-us
document_id: bea18363-d497-9f92-2c82-e907bf385f36
document_version_independent_id: 2d62fd48-3825-1ed2-c4e4-e42ff2621b29
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/configmgr/core/servers/deploy/install/release-notes.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: configmgr/core/servers/deploy/install/release-notes
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/configmgr/core/servers/deploy/install/release-notes.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/4c50f262-d533-4ba4-9d4a-08899ec3a3d1
- https://authoring-docs-microsoft.poolparty.biz/devrel/bcbcbad5-4208-4783-8035-8481272c98b8
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/6a8c83be-f1de-4e90-bde0-bd097999a60c
- https://authoring-docs-microsoft.poolparty.biz/devrel/43b2e5aa-8a6d-4de2-a252-692232e5edc8
platformId: 6d4ce334-3afa-92d0-7981-3abf49ff1bb0
---

# Release notes - Configuration Manager | Microsoft Learn

*Applies to: Configuration Manager (current branch)*

With Configuration Manager, product release notes are limited to urgent issues. These issues aren't yet fixed in the product, or detailed in a [troubleshooting article](/en-us/troubleshoot/mem/configmgr/welcome-configuration-manager).

Feature-specific documentation includes information about known issues that affect core scenarios.

This article contains release notes for the current branch of Configuration Manager. For information on the technical preview branch, see [Technical Preview](../../../get-started/technical-preview).

For information about the new features introduced with different versions, see the following articles:

- [What's new in version 2609](../../../plan-design/changes/whats-new-version-2609)
- [What's new in version 2603](../../../plan-design/changes/whats-new-in-version-2603)
- [What's new in version 2509](../../../plan-design/changes/whats-new-in-version-2509)

Tip

You can use RSS to be notified when this page is updated. For more information, see [How to use the docs](../../../../../fundamentals/use-docs#notifications).

## Set up and upgrade

### ODBC driver version 18.7.1.1 can block site configuration before updating to 2609

*Applies to: upgrades to version 2609*

Microsoft ODBC Driver for SQL Server version [18.7.1.1](/en-us/sql/connect/odbc/windows/release-notes-odbc-sql-server-windows#187) has a known issue with Configuration Manager version 2603 and earlier that can block site configuration.

To avoid this issue, don't install ODBC driver version 18.7.1.1 before updating Configuration Manager. Use ODBC driver version [18.6.2.1](/en-us/sql/connect/odbc/windows/release-notes-odbc-sql-server-windows#186), the validated version shipped with Configuration Manager 2609, for the update. Complete the Configuration Manager update to version 2609 before you install ODBC driver version 18.7.1.1.

For more information, see [ODBC driver for SQL Server](list-of-prerequisite-checks#odbc-driver-for-sql-server).

### Configuration Manager performance counters are missing on Windows Server 2025

*Applies to: primary site servers and management points running Windows Server 2025*

On Windows Server 2025, Configuration Manager performance counter registration can fail, leaving the counters unavailable in Performance Monitor. This issue can occur after a clean installation of Windows Server 2025 or an in-place upgrade from Windows Server 2022.

**Perfsetup.log** records errors similar to the following:

```text
Error: InstallSMSObjectAndCounterKeySettingsIntoRegistry() could not get the "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\SMS_SOFTWARE_INVENTORY_PROCESSOR\Performance" registry key; error = 6 (0x6).
```

Perfsetup can also exit with code `1000`. The affected component name in the registry path can vary.

To resolve this issue, install the [update rollup for Configuration Manager version 2603 (KB39169655)](../../../../hotfix/2603/39169655) or update to Configuration Manager version 2609, which also includes this fix.

## OS deployment

### Task sequence status messages fail in the full OS with CNG/KSP boot media certificates

*Applies to: version 2609*

After you upgrade to Configuration Manager version 2609, task sequences that use boot media with an imported public key infrastructure (PKI) certificate backed by a Cryptography Next Generation (CNG) key storage provider (KSP) might fail to send status messages after restarting from Windows PE into the full Windows OS.

**smsts.log** records error `0x80072f9a` (`ERROR_WINHTTP_CLIENT_CERT_NO_ACCESS_PRIVATE_KEY`). Each failed attempt to send a status message is retried, adding delays to OS deployment. The Windows PE phase isn't affected.

To work around this issue, import the certificate's private key into a legacy cryptographic service provider (CSP), export the certificate and private key to a new Personal Information Exchange (PFX) file, and recreate the bootable media.

Use an RSA certificate with an exportable private key. Protect the PFX files and their passwords from unauthorized access.

1. Open a Command Prompt window in the folder that contains the original PFX file. Run the following command to import the certificate into the current user's **Personal** certificate store by using the **Microsoft Enhanced RSA and AES Cryptographic Provider**:

    ```console
    certutil -user -csp "Microsoft Enhanced RSA and AES Cryptographic Provider" -p "<pfxpassword>" -importPFX My boot-media-original.pfx
    ```

    Replace `<pfxpassword>` with the original PFX file's password and `boot-media-original.pfx` with its file name.
2. Run `certmgr.msc` to open the certificate management console for the current user. Expand **Personal**, and then select **Certificates**.
3. Right-click the imported certificate, select **All Tasks**, and then select **Export**. In the Certificate Export Wizard, select **Next**.
4. Select **Yes, export the private key**, and then select **Next**. Select **Personal Information Exchange - PKCS #12 (.PFX)** and **Include all certificates in the certification path if possible**, and then select **Next**.
5. Select **Password**, enter and confirm a strong password, and then select **Next**. Specify a new file name, such as `boot-media-legacy-csp.pfx`, select **Next**, and then select **Finish**.
6. Verify the exported PFX file by running the following command. Replace `<pfxpassword>` with the new PFX file's password:

    ```console
    certutil -p "<pfxpassword>" -dump boot-media-legacy-csp.pfx
    ```

    Verify that the provider is **Microsoft Enhanced RSA and AES Cryptographic Provider** before you use the certificate to create media.
7. [Create new bootable media](../../../../osd/deploy-use/create-bootable-media#process). On the **Security** page of the Create Task Sequence Media Wizard, select **Import PKI certificate** and specify the new PFX file `boot-media-legacy-csp.pfx` and its password. Use the new media for subsequent deployments.

For more information, see [certutil](/en-us/windows-server/administration/windows-commands/certutil) and [Export a certificate with its private key](/en-us/windows-server/identity/ad-cs/export-certificate-private-key).

## Content management

### Content downloads fail with HTTP 403.7 from PKI HTTPS distribution points

*Applies to: version 2609*

After you upgrade to Configuration Manager version 2609, clients and pull-distribution points might fail to download content from HTTPS distribution points that use public key infrastructure (PKI) certificates. Downloads can fail even when the downloading client or pull-distribution point has a valid client certificate.

The source distribution point's IIS log records HTTP status `403.7`. **DataTransferService.log** and, for pull-distribution points, **PullDP.log** can record error `0x80190193`. Not all downloads are affected; connections that have already negotiated a valid client certificate might succeed.

To identify whether a failed content download is affected by this issue, update the SSL settings on the affected distribution point and retry the download:

Important

This procedure briefly changes client certificate enforcement. Don't leave **Client certificates** set to **Accept**.

1. On the affected distribution point server, open **Internet Information Services (IIS) Manager** as an administrator.
2. In the **Connections** pane, expand the server, expand **Sites**, and then expand the website that hosts the distribution point virtual directories. Select **SMS\_DP\_SMSPKG$**.
3. In **Features View**, double-click **SSL Settings**.
4. On the **SSL Settings** page, verify that **Require SSL** is selected. Under **Client certificates**, select **Accept**, and then select **Apply** in the **Actions** pane.
5. Under **Client certificates**, select **Require**, and then select **Apply** in the **Actions** pane. Keep **Require SSL** selected.
6. Select the **SMS\_DP\_SMSSIG$** virtual directory and repeat steps 3 through 5.
7. Retry the previously failed content download from the same distribution point. If the download succeeds after you apply these settings, this result confirms the issue described in this release note.

This change isn't permanent. Configuration Manager reapplies the affected settings every 48 hours and when the distribution point is reconfigured or upgraded.

For more information, see [Configure client certificates in IIS](/en-us/iis/application-frameworks/scenario-build-an-aspnet-website-on-iis/configuring-step-4-configure-application-security#client-certificates).

## Client authentication and registration

### Microsoft Entra token validation fails when the management point can't access the internet

*Applies to: version 2603 and later*

Starting in version 2603, the management point uses Microsoft Identity Service Essentials (MISE) for Microsoft Entra token validation and requires internet access. This requirement affects sites configured to support Microsoft Entra joined users and devices when clients authenticate using Microsoft Entra tokens, typically through a cloud management gateway (CMG). Environments that only use on-premises Active Directory authentication without Microsoft Entra integration aren't affected.

If the management point can't reach the required endpoints, **CCM\_STS\_ManagedBase.log** on the management point records a `MiseAuthenticationTicketProviderException` with an underlying network error, for example:

```text
Microsoft.Identity.ServiceEssentials.Exceptions.MiseAuthenticationTicketProviderException: MISE12034: AuthenticationTicketProvider Name:AuthenticationTicketProvider
System.Net.Sockets.SocketException: No connection could be made because the target machine actively refused it
```

Important

The `MISE12034` exception can also occur for other reasons. Before applying this resolution, verify that the underlying exception indicates a network connectivity problem, such as a `SocketException`, `HttpRequestException`, or connection timeout.

To resolve this issue, allow the management point server to access the following Microsoft Entra authentication endpoints through the proxy and firewall in the Local System context:

- `https://login.microsoftonline.com`
- `https://sts.windows.net`

If the management point uses a proxy, configure it in the Local System context. In version 2603, the proxy set in the site system properties and a WinHTTP-only proxy (`netsh winhttp set proxy`) aren't used for this validation path.

For configuration steps and the full list of required endpoints, see [Management point proxy configuration](../../../plan-design/network/proxy-server-support#management-point) and [Management point internet access requirements](../../../plan-design/network/internet-endpoints#management-point).

### Bulk registration token verification fails after installing the version 2603 update rollup

*Applies to: version 2603 with update rollup KB39169655 installed*

After you install the [update rollup for Configuration Manager version 2603 (KB39169655)](../../../../hotfix/2603/39169655), bulk registration token verification fails on the management point for devices that aren't Microsoft Entra joined and connect through a cloud management gateway (CMG). Affected devices can't complete bulk registration through the CMG to obtain their individual Configuration Manager-issued client authentication tokens. Other CMG communication scenarios for these devices may also be affected.

This issue doesn't affect devices that use Microsoft Entra authentication or version 2603 sites that haven't installed KB39169655.

On the management point, errors similar to the following are recorded in `<MP_InstallDir>\Logs\CCM_STS.log`:

```text
ProcessRequest - Start
Incoming request URL: https://<management-point>/CCM_STS
Validated PreAuth SelfProve token. UniqueId: <client-id>. ClientKey: <public-key>
ProcessRequest - Exception: System.IO.FileLoadException:
Could not load file or assembly
'mpisapiclr, Version=5.0.9146.1045, Culture=neutral,
PublicKeyToken=31bf3856ad364e35' or one of its dependencies.
The located assembly's manifest definition does not match the assembly reference.
(Exception from HRESULT: 0x80131040)
```

To resolve this issue, install [KB40345593](../../../../hotfix/2603/40345593), which is available in **Updates and Servicing** after you install KB39169655. This update requires a [site reset](../../manage/modify-your-infrastructure#bkmk_reset) after installation, but doesn't require a computer restart.

## Collection management

### Collections based on Active Directory group membership lose members after upgrading to version 2609

*Applies to: version 2609*

After you upgrade to Configuration Manager version 2609, a full [Microsoft Entra user group discovery](../configure/about-discovery-methods#bkmk_azuregroupdisco) cycle might remove Active Directory user-group relationships from the Configuration Manager database. User collections with query-based membership rules that depend on Active Directory group membership might lose some or all members after collection evaluation. Deployments targeted to these collections might no longer reach the intended users.

To prevent further occurrences, disable [Microsoft Entra user group discovery](../configure/configure-discovery-methods#bkmk_azuregroupdisco). Disabling discovery doesn't restore user-group relationships that have already been removed.

## Software updates

### Devices continue scanning Windows Update after moving the update workload back to Configuration Manager

*Applies to: version 2503 with update rollup KB32851084 and KB36495448 installed, version 2509 with KB36495448 installed, and later releases that inherit this behavior*

After you move the **Windows Update policies** co-management workload from Intune back to Configuration Manager, devices might continue scanning Windows Update or Microsoft Update instead of WSUS, even after a machine policy cycle completes.

Starting with [KB36495448](../../../../hotfix/2509/36495448), the Configuration Manager client no longer sets or removes Windows Update scan source policies. Moving the workload slider doesn't automatically remove the Windows Update client policy state previously configured by Intune. This state can persist on the device after the Intune policy assignment is removed.

To address this issue, review the effective scan source for each update category and explicitly manage scan source policies through Group Policy or Intune. As a best practice, remove or reassign the device's Intune Windows Update client policy assignment before moving the workload back. For the cleanup procedure and alternative policy configuration, see [Moving the workload back to Configuration Manager](../../../../sum/deploy-use/integrate-windows-update-client-policies#moving-the-workload-back-to-configuration-manager).

### Reset default value of superseding age in months for software updates

*Applies to: version 2303*

Removing SUP role in Admin Console doesn't reset the superseding age property in WMI. As a result, while reconfiguring the role, the previously configured value is shown in the configuration window. This property needs to be reset to default value on role removal. For more information, see [supersedence rules for installing a software update point.](../../../../sum/get-started/install-a-software-update-point)

## Cloud services

### CMG shared key access changes

*Applies to: version 2609 updates with an existing cloud management gateway*

Version 2609 automatically disables shared key access for CMG storage. The [CMG enhanced security](../../../plan-design/changes/whats-new-in-version-2409#cmg-enhanced-security-option) workflow prepares the Azure prerequisites and configures the content uploader to use Microsoft Entra authentication instead of shared key authentication.

Before updating, consider enabling **CMG enhanced security** with an authorized Azure administrator. For a running virtual machine scale set CMG, use the following steps when the action is available:

1. In the Configuration Manager console, go to the **Administration** workspace, expand **Cloud Services**, and select **Cloud Management Gateway**.
2. Select the CMG, then select **CMG enhanced security**. For more information, see [CMG enhanced security option](../../../plan-design/changes/whats-new-in-version-2409#cmg-enhanced-security-option).
3. Select the appropriate tenant and sign in with an Azure account authorized to assign the required roles at the CMG resource group and register resource providers in the subscription. Select **Update** and verify that the workflow completes successfully.
4. Allow any resulting CMG deployment work and permission propagation to complete. Verify the server application's [Azure RBAC permissions](../../../clients/manage/cmg/configure-azure-ad#configure-azure-rbac-permissions-for-the-server-app) and the [required resource provider registration](../../../clients/manage/cmg/configure-azure-ad#configure-azure-resource-providers).

If you don't enable enhanced security before updating, the transition away from shared key access can result in either of the following scenarios. Use the symptoms and logs to identify the applicable guidance.

#### CMG update to version 2609 fails when Azure permissions or resource provider registration are missing

Existing CMG deployment updates can fail if Azure permissions or resource provider registration required for the transition are missing.

To address this failure, verify both prerequisites, even if you've run the **CMG enhanced security** workflow:

- **Azure role-assignment permissions:** **CloudMgr.log** can report HTTP `403`, `DeploymentFailed`, and a denied `Microsoft.Authorization/roleAssignments/write` action. Configure the server application's permissions as described in [Configure Azure RBAC permissions for the server app](../../../clients/manage/cmg/configure-azure-ad#configure-azure-rbac-permissions-for-the-server-app). **Contributor** alone doesn't grant role-assignment permissions.
- **Microsoft.Maintenance registration:** Verify that this resource provider is **Registered** in each subscription that hosts a CMG. Have an authorized Azure administrator complete any missing registration. For instructions, see [Configure Azure resource providers](../../../clients/manage/cmg/configure-azure-ad#configure-azure-resource-providers).

Allow permission changes and registration to complete, then verify the CMG deployment update and client communication. See [Verify CMG deployment and client communication](../../manage/checklist-for-installing-update-2609#verify-cmg-deployment-and-client-communication).

#### Content uploads to existing CMGs fail after updating to version 2609

Packages and applications might fail to upload to an existing content-enabled CMG or repeatedly retry. This scenario can affect CMGs created before version 2409 that haven't had enhanced security enabled. The site-side content uploader can continue using shared key authentication after the Azure storage account has disabled it.

Unlike the deployment update failure, content uploads can fail even when the CMG deployment update completes and the Azure prerequisites are met. Previously uploaded content isn't necessarily unavailable to clients.

**PkgXferMgr.log** can record storage account key retrieval followed by errors similar to the following:

```text
Resource Manager - Key retrieved for storage service 
Getting container Ids for StorageAccount: ...
CheckServiceStatus() failed
Failed to distribute content to the cloud DP.
Sending failed. Failure count = ...
```

The preferred workaround for an affected, running virtual machine scale set CMG is to enable **CMG enhanced security**, when the action is available, by using the procedure earlier in this section. After the workflow and any resulting deployment work complete, retry content distribution and verify successful package uploads.

Important

This workflow is expected to correct the authentication setting, but recovery hasn't been validated for every affected configuration. The action might be unavailable, including when the CMG is in an error state. If it isn't available or doesn't restore content uploads, contact Microsoft Support for recovery guidance. Don't directly modify the Configuration Manager database or re-enable shared key access in Azure.

Verify recovery through **PkgXferMgr.log** and [Monitor content you distribute](../configure/monitor-content-you-have-distributed).