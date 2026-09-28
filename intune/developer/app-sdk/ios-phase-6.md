---
layout: Conceptual
title: Microsoft Intune App SDK for iOS Developer Guide - App Protection CA Support (Optional) - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/developer/app-sdk/ios-phase-6
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
manager: laurawi
author: nicholasswhite
ms.author: nwhite
ms.collection:
- M365-identity-device-management
- iOS/iPadOS
ms.reviewer: jamiesil
ms.subservice: developer
description: The Microsoft Intune App SDK for iOS lets you incorporate Intune app protection policies (also known as MAM policies) into your native iOS app. App Protection CA support (optional)
ms.date: 2025-06-12T00:00:00.0000000Z
ms.topic: reference
locale: en-us
document_id: b1a1a8b5-f68f-abc4-bf57-693d8cff0c41
document_version_independent_id: b1a1a8b5-f68f-abc4-bf57-693d8cff0c41
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/developer/app-sdk/ios-phase-6.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: developer/app-sdk/ios-phase-6
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/developer/app-sdk/ios-phase-6.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
- https://authoring-docs-microsoft.poolparty.biz/devrel/1ae5c491-970a-4062-8301-6336e69f9026
- https://authoring-docs-microsoft.poolparty.biz/devrel/a3955c7b-f5ee-420d-aff5-d7119738f38b
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
- https://authoring-docs-microsoft.poolparty.biz/devrel/f2c3e52e-3667-4e8a-bf11-20b9eaccdc8c
- https://authoring-docs-microsoft.poolparty.biz/devrel/b31948f4-2f38-404b-ac93-c3c8c5b3ae33
platformId: 1f28d7a1-4552-d6a2-b3da-dedb586e2c31
---

# Microsoft Intune App SDK for iOS Developer Guide - App Protection CA Support (Optional) - Microsoft Intune | Microsoft Learn

App Protection Conditional Access blocks access to server tokens until Intune has confirmed app protection policy has been applied. This feature requires changes to your add user flows. Once a customer enables App Protection CA, applications in that customer's tenant that access protected resources won't be able to acquire an access token unless they support this feature.

Note

This guide is divided into several distinct stages. Start by reviewing [Stage 1: Plan the Integration](ios-phase-1).

## Stage 6: App Protection CA support

## Stage Goals

- Learn about different APIs that can be used to support App Protection Conditional Access within iOS app
- Integrate App Protection Conditional Access to your app and users.
- Test the above integration with your app and users.

### Dependencies

In addition to the Intune SDK, you need these two components to enable App Protection CA in your app.

1. iOS Authenticator app
2. MSAL authentication library 1.0 or greater

### MAM-CA remediation flow

[![Diagram of MAM-CA remediation flow.](media/shared/app-ca-flow.png)](media/shared/app-ca-flow.png#lightbox)

### MAM compliance process flow

[![Diagram of MAM compliance process flow.](media/shared/mam-compliance-flow.png)](media/shared/mam-compliance-flow.png#lightbox)

### New APIs

Most of the new APIs can be found in the IntuneMAMComplianceManager.h. The app needs to be aware of three differences in behavior explained below.

| New behavior | Description |
| --- | --- |
| App → ADAL/MSAL: Acquire token | When an application tries to acquire a token, it should be prepared to receive a ERROR\_SERVER\_PROTECTION\_POLICY\_REQUIRED. The app can receive this error during their initial account add flow or when accessing a token later in the application lifecycle. When the app receives this error, it won't be granted an access token and needs to be remediated to retrieve any server data. |
| App → Intune SDK: Call remediateComplianceForIdentity | When an app receives a ERROR\_SERVER\_PROTECTION\_POLICY\_REQUIRED from ADAL, or MSALErrorServerProtectionPoliciesRequired from MSAL it should call [[IntuneMAMComplianceManager instance] remediateComplianceForIdentity] to let Intune enroll the app and apply policy. The app may be restarted during this call. If the app needs to save state before restarting, it can do so in restartApplication delegate method in IntuneMAMPolicyDelegate. remediateComplianceForIdentity provides all the functionality of registerAndEnrollAccount and loginAndEnrollAccount. Therefore, the app doesn't need to use either of these older APIs. |
| Intune → App: Delegate remediation notification | After Intune has retrieved and applied policies, it notifies the app of the result using the IntuneMAMComplianceDelegate protocol. Refer to IntuneMAMComplianceStatus in IntuneComplianceManager.h for information on how the app should handle each error. In all cases except IntuneMAMComplianceCompliant, the user won't have a valid access token. If the app already has managed content and isn't able to enter a compliant status, the application should call selective wipe to remove any corporate content. If we can't reach a compliant state, the app should display localized the error message and title string supplied by withErrorMessage and andErrorTitle. |

Example for hasComplianceStatus method of IntuneMAMComplianceDelegate

```objc
(void) accountId:(NSString*_Nonnull) accountId hasComplianceStatus:(IntuneMAMComplianceStatus) status withErrorMessage:(NSString*_Nonnull) errMsg andErrorTitle:(NSString*_Nonnull) errTitle
{
    switch(status)
    {
        case IntuneMAMComplianceCompliant:
        {
            /*
            Handle successful compliance
            */
            break;
        }
        case IntuneMAMComplianceNotCompliant:
        case IntuneMAMComplianceNetworkFailure:
        case IntuneMAMComplianceUserCancelled:
        case IntuneMAMComplianceServiceFailure:
        {
            UIAlertController* alert = [UIAlertController alertControllerWithTitle:errTitle
            message:errMsg
            preferredStyle:UIAlertControllerStyleAlert];
            UIAlertAction* defaultAction = [UIAlertAction actionWithTitle:@"OK" style:UIAlertActionStyleDefault
            handler:^(UIAlertAction * action) {exit(0);}];
            [alert addAction:defaultAction];
            dispatch_async(dispatch_get_main_queue(), ^{
            [self presentViewController:alert animated:YES completion:nil];
            });
            break;
        }
        case IntuneMAMComplianceInteractionRequired:
        {
            [[IntuneMAMComplianceManager instance] remediateComplianceForAccountId:accountId silent:NO];
            break;
        }
    }
}
```

```swift
func accountId(_ accountId: String, hasComplianceStatus status: IntuneMAMComplianceStatus, withErrorMessage errMsg: String, andErrorTitle errTitle: String) {
        switch status {
        case .compliant:
           //Handle successful compliance
        case .notCompliant, .networkFailure,.serviceFailure,.userCancelled:
            DispatchQueue.main.async {
              let alert = UIAlertController(title: errTitle, message: errMsg, preferredStyle: .alert)
                alert.addAction(UIAlertAction(title: "OK", style: .default, handler: { action in
                    exit(0)
                }))
                self.present(alert, animated: true, completion: nil)
            }
        case .interactionRequired:
            IntuneMAMComplianceManager.instance().remediateCompliance(forAccountId: accountId, silent: false)
   }
```

### MSAL/ADAL

Apps need to indicate support for App Protection CA by adding client capabilities variable to their MSAL/ADAL configuration. The following values are required: claims = {"access\_token":{"xms\_cc":{"values":["protapp"]}}}

[MSALPublicClientApplicationConfig Class Reference (azuread.github.io)](https://azuread.github.io/microsoft-authentication-library-for-objc/Classes/MSALPublicClientApplicationConfig.html#/c:objc%28cs%29MSALPublicClientApplicationConfig%28py%29clientApplicationCapabilities)

```objc
    MSALAADAuthority *authority = [[MSALAADAuthority alloc] initWithURL:[[NSURL alloc] initWithString:IntuneMAMSettings.aadAuthorityUriOverride] error:&msalError];
    MSALPublicClientApplicationConfig *config = [[MSALPublicClientApplicationConfig alloc]
                                                 initWithClientId:IntuneMAMSettings.aadClientIdOverride
                                                 redirectUri:IntuneMAMSettings.aadRedirectUriOverride
                                                 authority:authority];

    /*
     IF YOU'RE IMPLEMENTING CA IN YOUR APP, PLEASE PAY ATTENTION TO THE FOLLOWING...
    */
    // This is needed for CA!
    // This line adds an option to the MSAL token request so that MSAL knows that CA may be active
    // Without this, MSAL won't know that CA could be activated
    // In the event that CA is activated and this line isn't in place, the auth flow will fail

    config.clientApplicationCapabilities = @[@"protapp"];
```

```swift
guard let authorityURL = URL(string: kAuthority) else {
            print("Unable to create authority URL")
            return
        }
         let authority = try MSALAADAuthority(url: authorityURL)
         let msalConfiguration = MSALPublicClientApplicationConfig(clientId: kClientID,redirectUri: kRedirectUri,
                                                                  authority: authority)
        msalConfiguration.clientApplicationCapabilities = ["ProtApp"]
        self.applicationContext = try MSALPublicClientApplication(configuration: msalConfiguration)

```

To fetch the Microsoft Entra object ID for the accountId parameter of the MAM SDK compliance remediation APIs, you need to do the following steps:

- First get the homeAccountId from userInfo[MSALHomeAccountIdKey] within MSALError object sent back by MSAL when it reports ERROR\_SERVER\_PROTECTION\_POLICY\_REQUIRED to the app.
- This homeAccountId is in the format ObjectId.TenantId. Extract the ObjectId value by splitting the string on the '.' and then use that value for the accountId parameter in remediation API remediateComplianceForAccountId.

### Exit criteria

#### Configuring a test user for App Protection CA

1. Sign in with your administrator credentials to https://portal.azure.com.
2. Select **Microsoft Entra ID** &gt; **Conditional Access** &gt; **Create new policy**. Create a new Conditional Access policy.
3. Configure Conditional Access policy by setting the following items:
    - Filling in the **Name** field.
    - Enabling the policy.
    - Assigning the policy to a user or group.
4. Assign cloud apps. Select **Include** &gt; **All cloud apps**. As the warning notes, be careful not to misconfigure this setting. For example, if you excluded all cloud apps, you would lock yourself out of the console.
5. Grant access controls by selecting **Access Controls** &gt; **Grant Access** &gt; **Require app protection policy**.
6. When you're finished configuring the policy, select **Create** to save the policy and apply it.
7. Enable the policy.
8. You also need to make sure that the users are targeted for MAM policies.

#### Test cases

| Test Case | How to test | Expected Outcome |
| --- | --- | --- |
| MAM-CA always applied | Ensure the user is targeted for both App Protection CA and MAM policy before enrolling in your app. | Verify that your app handles the remediation cases described above and the app can get an access token. |
| MAM-CA applied after user enrolled | The user should be logged into the app already, but not targeted for App Protection CA. | Target the user for App Protection CA in the console and verify that you correctly handle MAM remediation |
| MAM-CA noncompliance | Setup an App Protection CA policy, but don't assign a MAM policy. | The user shouldn't be able to acquire an access token. This is useful for testing how your app handles IntuneMAMComplianceStatus error cases. |