---
layout: Conceptual
title: Delete issued PKI certificates with Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/cloud-pki/delete-ca
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: paolomatarazzo
ms.author: paoloma
ms.collection:
- M365-identity-device-management
- certificates
ms.reviewer: wicale
ms.subservice: suite
description: Delete certificates issued via Microsoft Intune cloud PKI.
ms.date: 2024-12-06T00:00:00.0000000Z
ms.topic: how-to
locale: en-us
document_id: becc979e-e60d-6c5c-6b07-554253cd9b8c
document_version_independent_id: becc979e-e60d-6c5c-6b07-554253cd9b8c
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/cloud-pki/delete-ca.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: cloud-pki/delete-ca
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/cloud-pki/delete-ca.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/68e4b2d8-b70c-4019-b49a-d1f8881e2aea
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/67b2ba1a-6f74-4044-a48a-f0f8ad076b8f
platformId: a079c1d4-52e3-f94a-bf52-0302681ad9ee
---

# Delete issued PKI certificates with Microsoft Intune - Microsoft Intune | Microsoft Learn

Delete an issuing and root certification authority (CA) from the Microsoft Cloud PKI service in Microsoft Intune. You can use the following actions in the Microsoft Intune admin center to manage certification authorities (CAs) in your tenant:

- Pause CA - Pause the CA to stop use of it.
- Revoke CA - Revoke all active leaf certificates and then revoke the CA.
- Delete CA - Delete and remove the CA from Microsoft Intune.

A root CA can't be deleted until all anchored issuing CAs are deleted. If you change your mind after you pause a CA, you can unpause it to resume use. However, revoking and deleting a CA are permanent actions and can't be undone.

This article describes how to delete an issuing CA and root CA from Microsoft Intune using the available actions in the admin center.

## Role-based access requirements

These administrator roles can delete CAs in the Microsoft Intune admin center:

- Intune Administrator, a built-in Microsoft Entra role
- Custom Intune role, assigned the following Intune permissions:
    - Read CAs
    - Disable and reenable CAs
    - Revoke issued leaf certificates

## Delete issuing CA

Permanently remove an issuing CA from Microsoft Intune. If you're trying to delete a root CA, complete these steps first to delete the issuing CA anchored to it.

1. Go to **Tenant administration** &gt; **Cloud PKI**.
2. Select an active issuing CA from the list of available CAs. Selecting a CA opens its available actions.
3. Select **Pause**.

    ![Cloud PKI CA properties page with Pause action highlighted.](media/delete-ca/delete.png)
4. Select **Pause** again when prompted to confirm.

    Note

    After you pause an issuing CA:

    - It can't issue leaf certificates.
    - It continues to respond to certificate revocation list (CRL) requests and AIA requests.
5. Go back to your list of CAs and choose **Refresh**. Then look under the **Status** column to confirm that the issuing CA is paused.

    ![Cloud PKI CA list with Status column showing paused state.](media/delete-ca/delete-2.png)
6. Select the paused CA to open all available options again. Two new options appear:

    - **Resume**: This option unpauses the CA and makes it active again.
    - **Revoke**: This option revokes the issuing CA.
7. Select **Revoke**.

    Tip

    For this action to work, all active leaf certificates belonging to the CA must already be revoked. For more information and steps, see Revoke active leaf certificates in this article.

    ![Cloud PKI CA properties page with Revoke action highlighted.](media/delete-ca/delete-3.png)
8. Select **Revoke** again when prompted to confirm.

    Important

    This action can't be undone.

    Note

    After you revoke an issuing CA:

    - It continues to respond to CRL and AIA requests.
    - It's no longer trusted to the relying parties performing a trust chain operation.
    - The CRL of the root CA shows that the issuing CA cert is revoked.
    - All existing leaf certificates issued by the CA stop being authenticated.
9. Go back to your list of CAs and choose **Refresh**. Then look under the **Status** column to confirm that the issuing CA is revoked.

    ![Cloud PKI CA list with Status column showing revoked state.](media/delete-ca/delete-4.png)
10. Select the revoked CA to open all available options again.
11. The option to delete the CA should be available now. Select **Delete** to remove the CA from Microsoft Intune.

    ![Cloud PKI CA properties page with Delete action highlighted for an issuing CA.](media/delete-ca/delete-5.png)
12. Select **Delete** again when prompted to confirm.

    Important

    This action can't be undone.
13. Go back to your list of CAs and choose **Refresh**. Confirm that the issuing CA no longer appears in the list.

## Delete root CA

Permanently remove a root CA from Microsoft Intune.

Tip

Delete all anchored issuing CAs before you delete the root CA.

1. Go to **Tenant administration** &gt; **Cloud PKI**.
2. Select a root CA from the list of available CAs. Selecting a CA opens its available actions.

    ![Cloud PKI CA list with a root CA selected.](media/delete-ca/delete-6.png)
3. Select **Delete** to remove the CA from Microsoft Intune.

    ![Cloud PKI CA properties page with Delete action highlighted for the root CA.](media/delete-ca/delete-8.png)
4. Select **Delete** again when prompted to confirm.

    Important

    This action can't be undone.
5. Go back to your list of CAs and choose **Refresh**. Confirm that the root CA no longer appears in the list.

## Revoke active leaf certificates

When trying to revoke an issuing CA, it's important to revoke all of its active leaf certificates first. You can revoke one leaf certificate at a time from an issuing CA, or you can bulk revoke leaf certificates.

### Revoke a leaf certificate

1. In the Microsoft Intune admin center, go to **Tenant administration** &gt; **Cloud PKI**.
2. Select an issuing CA.
3. Choose **View all certificates**.
4. Select an active leaf certificate, and then choose **Revoke**. Repeat this step on every remaining leaf certificate.

### Revoke all leaf certificates

You can use the sample PowerShell script in this section to revoke all leaf certificates belonging to a CA. The script retrieves information from your Microsoft Intune tenant about Microsoft Cloud PKI, and revokes leaf certificates for an issuing CA in your tenant.

- The script retrieves all leaf certificates and performs the revoke action on each one.
- The script prompts you, as the admin, to confirm that you want to revoke all leaf certificates.
- The script has an optional configuration you can include that sends a confirmation prompt for each certificate. The section in the script is commented-out in the sample, so add it back in if you want to run that part.

#### Important

Use this script with caution. You can't undo the revoke action for any of the leaf certificates.

- Review the sample script before running it to better understand how it works, and to consider how it impacts your tenant.
- Run the sample script in a nonproduction or test tenant account first.

The script installs the Microsoft Graph PowerShell module, *Microsoft.Graph*. The device that's running the script must have administrative privileges to successfully install the module.

The `Connect-MgGraph` command must be issued by an administrator who has permission to revoke leaf certificates on the issuing CA.

The CA ID is required to run the script. To find this information in the admin center:

1. Go to **Tenant administration** &gt; **Cloud PKI**.
2. Select an issuing CA.
3. Look at the browser URL to find the CA ID. The hyphenated alphanumeric string at the end of the URL is the CA ID. For example, in the following URL, the CA ID is **f12345-acf1-12ab-1b2a-1a1234567a89**:

    `https://intune.microsoft.com/#view/Microsoft_Intune_DeviceSettings/CaDetails.ReactView/id/f12345-acf1-12ab-1b2a-1a1234567a89`

#### Sample script

Run the sample PowerShell script from an administrative workstation. To run it, you must have the following Intune permissions:

- Read CAs
- Revoke issued leaf certificates

```powershell
 param (
    [string]$caId = $(Read-Host "Input CaId")
    )

Install-Module Microsoft.Graph

Connect-MgGraph -Scopes "DeviceManagementConfiguration.ReadWrite.All"

Start-Transcript -Path ".\RevokeAllLeafCerts_$($caId)_$(Get-Date -f 'yyyyMMdd-HHmmss').txt"

### Get all leaf certs
$leafCerts = Invoke-MgGraphRequest -Method GET -Uri "https://graph.microsoft.com/beta/devicemanagement/cloudCertificationAuthority/$caId/cloudCertificationAuthorityLeafCertificate"

# Prompt user to confirm data cleanup
$confirmAllDelete = $(Write-Host "Are you 100% sure you want to revoke all $($leafCerts.value.count) certificates for CA $($caId)?" -ForegroundColor Yellow; Write-Host '[Y] Yes' -NoNewline; Write-Host ' [N] No' -ForegroundColor Yellow -NoNewline;
Read-Host " ")

if ($confirmAllDelete.ToLower() -ne "y" -and $confirmAllDelete.ToLower() -ne "yes") {
    Write-Host "Aborted"
    Stop-Transcript
    exit
}

# Iterate on retrieved leaf certs and revoke
foreach ($leafCert in $leafCerts.value)
{
    Write-Host ""
    if ($leafCert.certificateStatus.ToLower() -eq "revoked") {
         Write-Host "LeafCert id: $($leafCert.id), thumbprint: $($leafCert.thumbprint) is already revoked. Skipping"
         continue
    }

    Write-Host "Revoking leafCert id: $($leafCert.id), thumbprint: $($leafCert.thumbprint)"

    # Uncomment next five lines to prompt for each cert
    # $confirmCertDelete = $(Write-Host "Are you sure you want to revoke leafCert id: $($leafCert.id), thumbprint: $($leafCert.thumbprint), $($leafCert.certificateStatus)?" -ForegroundColor Yellow; Write-Host '[Y] Yes' -NoNewline; Write-Host ' [N] No' -ForegroundColor Yellow -NoNewline; Read-Host " ")
    # if ($confirmCertDelete.ToLower() -ne "y" -and $confirmCertDelete.ToLower() -ne "yes") {
    #     Write-Host "Skipping"
    #     continue
    # }

    $currentCertId = $($leafCert.id)
    $revokeParams = @{ "leafCertificateId" = $($leafCert.id) }

    Invoke-MgGraphRequest -Method POST -Uri "https://graph.microsoft.com/beta/devicemanagement/cloudCertificationAuthority/$caId/revokeLeafCertificate" -Body ($revokeParams|ConvertTo-Json) -ContentType "application/json"
}

```