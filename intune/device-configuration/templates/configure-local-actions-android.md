---
layout: Conceptual
title: Configure local actions for Android devices in Microsoft Intune - Microsoft Intune | Microsoft Learn
canonicalUrl: https://learn.microsoft.com/en-us/intune/device-configuration/templates/configure-local-actions-android
author: abigail-stein2
ms.author: abigailstein
breadcrumb_path: /intune/breadcrumb/toc.json
uhfHeaderId: MSDocsHeader-Intune
feedback_system: Standard
ms.service: microsoft-intune
ms.collection:
- M365-identity-device-management
ms.subservice: configuration
description: Configure local actions in Microsoft Intune to run actions when supported events occur on managed Android devices.
ms.topic: how-to
ai-usage: ai-generated
ms.custom: msecd-doc-authoring-1030
ms.date: 2026-10-21T00:00:00.0000000Z
locale: en-us
document_id: 19816bc5-5b8b-0b6e-835f-775f5c4b088a
document_version_independent_id: 19816bc5-5b8b-0b6e-835f-775f5c4b088a
original_content_git_url: https://github.com/MicrosoftDocs/memdocs-pr/blob/live/intune/device-configuration/templates/configure-local-actions-android.md
site_name: Docs
depot_name: MSDN.memdocs
page_type: conceptual
toc_rel: ../../toc.json
pdf_url_template: https://learn.microsoft.com/pdfstore/en-us/MSDN.memdocs/{branchName}{pdfName}
feedback_product_url: ''
feedback_help_link_type: ''
feedback_help_link_url: ''
asset_id: device-configuration/templates/configure-local-actions-android
moniker_range_name: 
monikers: []
item_type: Content
source_path: intune/device-configuration/templates/configure-local-actions-android.md
cmProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/a72e95ff-4b4f-4cc1-90c6-7dcba67ff05f
spProducts:
- https://microsoft-devrel.poolparty.biz/DevRelOfferingOntology/24dc3ccd-591a-4415-a1fe-8759afafcb12
platformId: 4c29a00a-b544-b964-8144-16c560fc0272
---

# Configure local actions for Android devices in Microsoft Intune - Microsoft Intune | Microsoft Learn

Android local actions let you configure actions that run directly on managed Android devices when supported device events occur. By pairing triggers with actions, you can make devices respond to events such as a device reboot, a Managed Home Screen sign-in, or a change in the device's power connection.

You can use local actions to launch apps, send broadcasts to apps, initiate a global sign-out, or exit Managed Home Screen from kiosk mode.

## Prerequisites

- An Android device enrolled as a [dedicated device](../../device-enrollment/android/setup-dedicated) or [fully managed device](../../device-enrollment/android/setup-fully-managed).
- For activity actions, Overlay Permission (`SYSTEM_ALERT_WINDOW`) granted before you deploy the policy. For more information, see Overlay permission for foreground app launches.

## Create the profile

To configure local actions, create a device configuration profile using the **Local actions** template.

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** &gt; **Manage devices** &gt; **Configuration** &gt; **Create** &gt; **New policy**.
3. Select the following properties:

    - **Platform**: Select **Android Enterprise**.
    - **Profile type**: Select **Templates**.
    - **Template name**: Select **Local actions**.
4. Select **Create**.
5. In **Basics**, enter the following properties:

    - **Name**: Enter a descriptive name for the policy.
    - **Description**: Enter a description for the policy. This setting is optional but recommended.
    - **Profile type**: Select **Corporate owned devices**.
6. Select **Next**.
7. In **Configuration settings**, select **Enter JSON data**.
8. Paste the completed local actions JSON. Use the settings tables, schema, and examples in this article to build the JSON.
9. Select **Next**.
10. In **Scope tags** (optional), assign a scope tag to filter the policy to specific IT groups. Select **Next**.
11. In **Assignments**, select the device groups that should receive the policy. Select **Next**.
12. In **Review + create**, review the settings. Select **Create** to save and assign the policy.

Note

Local actions are only supported on an Android device enrolled as a dedicated device or fully managed device.

## Overlay permission for foreground app launches

Activity actions require Overlay Permission (`SYSTEM_ALERT_WINDOW`). Without it, foreground app launches might fail silently or behave unexpectedly.

Use OEMConfig to grant Overlay Permission to the Microsoft Intune app package, `com.microsoft.intune`. If Managed Home Screen is installed, also grant the permission to the Managed Home Screen package, `com.microsoft.launcher.enterprise`.

For Samsung, Zebra, Legacy Zebra, and Honeywell devices, see [Configure permissions for Managed Home Screen on Android Enterprise devices](configure-managed-home-screen-permissions-android) for OEMConfig instructions.

For other OEMs, use the OEM's instructions to grant Overlay Permission through OEMConfig. If the OEM doesn't support granting the permission through OEMConfig, grant it manually in the device Settings app.

## Trigger settings

A trigger defines the device event that causes one or more local actions to run.

### Supported triggers

Each trigger represents an event that occurs on the device. A configuration can contain multiple trigger-and-action bundles.

| Trigger | Value | When it fires |
| --- | --- | --- |
| Device reboot | `device_reboot` | After the device completes a reboot and the Intune app is ready. |
| Managed Home Screen sign-in | `mhs_sign_in` | When a user signs in through Managed Home Screen. |
| Global sign-out | `global_sign_out` | When global sign-out starts on the device. |
| Device plugged in | `device_plugged_in` | When the device connects to a power source, such as a charger or dock. |
| Device unplugged | `device_unplugged` | When the device disconnects from a power source. |
| Schedule | `schedule` | On the configured day and time. |

Note

The plug-in and unplug triggers are intended for use with Managed Home Screen because they require an actively running app to detect the change. To use these triggers without Managed Home Screen, make sure the Microsoft Intune app is running.

### Schedule trigger properties

If you use the `schedule` trigger, configure both schedule properties.

| Property | Value |
| --- | --- |
| `schedule_days` | A comma-separated list of day names. |
| `schedule_time` | The time in 24-hour `HH:mm` format. |

Note

Day names aren't case-sensitive. For `schedule_time`, only `:00` and `:30` minute values are supported. The schedule trigger has 30-minute precision and might run a few minutes after the configured time.

## Action settings

An action defines what the device does when its associated trigger fires.

### Supported action types

| Action type | Value | Use |
| --- | --- | --- |
| Activity | `activity` | Launch an activity in an app through an intent. |
| Broadcast | `broadcast` | Send a broadcast intent to an app. |
| Direct API | `direct_api` | Run a supported Intune device action directly. |

### Direct API actions

For a direct API action, use one of the following action values.

| Action | Value |
| --- | --- |
| Initiate global sign-out from Managed Home Screen | `mhs_sign_out` |
| Exit Managed Home Screen from kiosk mode | `exit_mhs_from_kiosk_mode` |

### Activity and broadcast action properties

Configure the properties that apply to the action type.

| Key | Type | Required | Description |
| --- | --- | --- | --- |
| `action_type` | `valueString` | Yes | The action type: `activity`, `broadcast`, or `direct_api`. |
| `package` | `valueString` | Yes for activity and broadcast intents | The target app package name. |
| `class` | `valueString` | No | The fully qualified class name of the target component. |
| `action` | `valueString` | Required for direct API actions; optional for intents | The intent action or supported direct API action to run. |
| `data_uri` | `valueString` | No | A URI for the intent data. |
| `mime_type` | `valueString` | No | The MIME type that describes the data format. |
| `flags` | `valueString` | No | A comma-separated list of supported Android intent flags. |
| `extras` | `valueBundleArray` | No | Key-value pairs that contain additional data for the receiving app. |

### Extra values

If the receiving app requires extras, add each extra to the `extras` array.

| Key | Type | Required | Description |
| --- | --- | --- | --- |
| `extra_key` | `valueString` | Yes | The key name for the extra. |
| `extra_value` | `valueString` | Yes | The value for the extra. |
| `extra_type` | `valueString` | No | The data type. Supported values are `string`, `boolean`, `integer`, `long`, `float`, and `double`. The default is `string`. |

Note

Activity and broadcast actions require an explicit target package. The target app must be installed on the device. Implicit intents are blocked, and an action fails silently if its target package isn't installed.

Note

The `data_uri` property supports the `geo`, `http`, `https`, `mailto`, and `tel` URI schemes. The `flags` property supports `FLAG_ACTIVITY_NEW_TASK`, `FLAG_ACTIVITY_CLEAR_TOP`, `FLAG_ACTIVITY_SINGLE_TOP`, `FLAG_ACTIVITY_CLEAR_TASK`, `FLAG_ACTIVITY_NO_HISTORY`, `FLAG_ACTIVITY_EXCLUDE_FROM_RECENTS`, `FLAG_ACTIVITY_NO_ANIMATION`, and `FLAG_ACTIVITY_REORDER_TO_FRONT`.

Important

Don't configure broadcast intents that target Intune management-critical apps, including Intune, Microsoft Authenticator, Company Portal, and Cloud DPC. These broadcasts are blocked. Activity intents can't target custom classes in Intune management-critical apps. For Microsoft Authenticator, Intune, Managed Home Screen, and Remote Help, you can launch the app's main screen, but you can't target a custom class.

## Local actions JSON schema

Local actions use the Android Enterprise managed configuration format. The top-level key is `com.microsoft.intune.localactions`, and its `valueBundleArray` contains the trigger-and-action bundles.

The complete schema is:

```json
{
  "kind": "androidenterprise#managedConfiguration",
  "productId": "app:com.microsoft.intune",
  "managedProperty": [
    {
      "key": "com.microsoft.intune.localactions",
      "valueBundleArray": [
        {
          "managedProperty": [
            {
              "key": "trigger",
              "valueString": ""
            },
            {
              "key": "actions",
              "valueBundleArray": [
                {
                  "managedProperty": [
                    {
                      "key": "action_type",
                      "valueString": "activity"
                    },
                    {
                      "key": "package",
                      "valueString": ""
                    },
                    {
                      "key": "class",
                      "valueString": ""
                    },
                    {
                      "key": "action",
                      "valueString": ""
                    },
                    {
                      "key": "data_uri",
                      "valueString": ""
                    },
                    {
                      "key": "mime_type",
                      "valueString": ""
                    },
                    {
                      "key": "flags",
                      "valueString": ""
                    },
                    {
                      "key": "extras",
                      "valueBundleArray": [
                        {
                          "managedProperty": [
                            {
                              "key": "extra_key",
                              "valueString": ""
                            },
                            {
                              "key": "extra_value",
                              "valueString": ""
                            },
                            {
                              "key": "extra_type",
                              "valueString": "string"
                            }
                          ]
                        }
                      ]
                    }
                  ]
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```

Replace the empty strings with the values for your trigger and actions. You can omit optional properties that you don't use. For each additional trigger, add another bundle to the top-level `valueBundleArray`.

Note

Actions run in configuration order. You can configure up to five actions for each trigger. If you configure more than five, only the first five run.

## JSON examples

Use these examples as starting points, and replace the example package, class, action, and extra values with values from the app developer.

### Launch an app after device reboot

This example launches the main activity of `com.example.safetyapp` after the device reboots. This activity action requires Overlay Permission.

```json
{
  "kind": "androidenterprise#managedConfiguration",
  "productId": "app:com.microsoft.intune",
  "managedProperty": [
    {
      "key": "com.microsoft.intune.localactions",
      "valueBundleArray": [
        {
          "managedProperty": [
            {
              "key": "trigger",
              "valueString": "device_reboot"
            },
            {
              "key": "actions",
              "valueBundleArray": [
                {
                  "managedProperty": [
                    {
                      "key": "action_type",
                      "valueString": "activity"
                    },
                    {
                      "key": "package",
                      "valueString": "com.example.safetyapp"
                    },
                    {
                      "key": "action",
                      "valueString": "android.intent.action.MAIN"
                    }
                  ]
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```

### Send a broadcast after global sign-out

This example sends a custom broadcast to an example app after global sign-out.

```json
{
     "kind": "androidenterprise#managedConfiguration",
     "productId": "app:com.microsoft.intune",
     "managedProperty": [
       {
     "key": "com.microsoft.intune.localactions",
     "valueBundleArray": [
         {
             "managedProperty": [
                 {
                     "key":"trigger",
                     "valueString": "global_sign_out"
                 },
                 {
                     "key": "actions",
                     "valueBundleArray": [
                         {
                             "managedProperty": [
                                 {
                                     "key":"action_type",
                                     "valueString": "broadcast"
                                 },
                                 {
                                     "key":"package",
                                     "valueString": "com.contoso.examplePackageName"
                                 },
                                 {
                                     "key":"class",
                                     "valueString": "com.contoso.example.fullyQualifiedClassName"
                                 },
                                 {
                                     "key":"action",
                                     "valueString": "com.contoso.example.EXAMPLE_CUSTOM_LOB_ACTION"
                                 },
                                 {
                                     "key": "extras",
                                     "valueBundleArray": [
                                         {
                                             "managedProperty": [
                                                 {"key": "extra_key",
     "valueString": "example_extra_key_1"},
                                                 {"key": "extra_value",
   "valueString": "example_extra_value_1"},
                                                 {"key": "extra_type",
"valueString": "string"}
                                             ]
                                         },
                                         {
                                             "managedProperty": [
                                                 {"key": "extra_key",
    "valueString": "example_extra_key_2"},
                                                 {"key": "extra_value",
"valueString": "true"},
                                                 {"key": "extra_type",
"valueString": "boolean"}
                                             ]
                                         }
                                     ]
                                 }
                             ]
                         }
                     ]
                 }
             ]
         }
     ]
       }
     ]
 }
```

### Run multiple actions after device reboot

This example launches two apps and sends a broadcast after the device reboots. The activity actions require Overlay Permission.

```json
{
  "kind": "androidenterprise#managedConfiguration",
  "productId": "app:com.microsoft.intune",
  "managedProperty": [
    {
      "key": "com.microsoft.intune.localactions",
      "valueBundleArray": [
        {
          "managedProperty": [
            {
              "key": "trigger",
              "valueString": "device_reboot"
            },
            {
              "key": "actions",
              "valueBundleArray": [
                {
                  "managedProperty": [
                    {
                      "key": "action_type",
                      "valueString": "activity"
                    },
                    {
                      "key": "package",
                      "valueString": "com.example.app1"
                    },
                    {
                      "key": "action",
                      "valueString": "android.intent.action.MAIN"
                    }
                  ]
                },
                {
                  "managedProperty": [
                    {
                      "key": "action_type",
                      "valueString": "activity"
                    },
                    {
                      "key": "package",
                      "valueString": "com.example.app2"
                    },
                    {
                      "key": "action",
                      "valueString": "android.intent.action.MAIN"
                    }
                  ]
                },
                {
                  "managedProperty": [
                    {
                      "key": "action_type",
                      "valueString": "broadcast"
                    },
                    {
                      "key": "package",
                      "valueString": "com.example.notifyapp"
                    },
                    {
                      "key": "action",
                      "valueString": "com.example.notifyapp.DEVICE_READY"
                    }
                  ]
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```

### Sign out of Managed Home Screen when docked

This example initiates a Managed Home Screen sign-out when the device connects to a charger or dock.

```json
{
  "kind": "androidenterprise#managedConfiguration",
  "productId": "app:com.microsoft.intune",
  "managedProperty": [
    {
      "key": "com.microsoft.intune.localactions",
      "valueBundleArray": [
        {
          "managedProperty": [
            {
              "key": "trigger",
              "valueString": "device_plugged_in"
            },
            {
              "key": "actions",
              "valueBundleArray": [
                {
                  "managedProperty": [
                    {
                      "key": "action_type",
                      "valueString": "direct_api"
                    },
                    {
                      "key": "action",
                      "valueString": "mhs_sign_out"
                    }
                  ]
                }
              ]
            }
          ]
        }
      ]
    }
  ]
}
```

### Launch an app on a schedule

This example launches a safety check-in app at 6:00 AM every weekday. This activity action requires Overlay Permission.

```json
{
    "kind": "androidenterprise#managedConfiguration",
    "productId": "app:com.microsoft.intune",
    "managedProperty": [
        {
            "key": "com.microsoft.intune.localactions",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                           "key": "trigger",
                            "valueString": "schedule"
                        },
                        {
                            "key": "schedule_time",
                            "valueString": "06:00"
                        },
                        {
                            "key": "schedule_days",
    "valueString": "monday,tuesday,wednesday,thursday,friday"
                        },
                        {
                            "key": "actions",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "action_type",
                                            "valueString": "activity"
                                        },
                                        {
                                            "key": "package",
                                            "valueString":"com.contoso.safetycheck"
                                        },
                                        {
                                            "key": "action",
"valueString":"android.intent.action.MAIN"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}
```