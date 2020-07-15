![Logo](/.github/assets/logo.png)

## MoEngage Android SDK Integration

![Download](https://api.bintray.com/packages/moengage/android-sdk/moe-android-sdk/images/download.svg)

To get up and running with MoEngage on Android, there a couple of steps we will walk you through.

To enable its full functionality (like Push Notifications, InApp Messaging), there are still a couple of steps that you have to take care of in your Android app.

#### Adding MoEngage Dependency:

Along with the segment dependency add the below dependency in your build.gradle file.

```groovy
 implementation 'com.moengage:moe-android-sdk:$sdkVersion'
```
`sdkVersion` - is the latest version of the MoEngage SDK.

Once you have installed the SDK follow the below documentation to integrate the SDK

* [Initialise the SDK](https://docs.moengage.com/docs/sdk-initialization#section-sdk-configuration)

* [Install and Update Differentiation](https://docs.moengage.com/docs/sdk-initialization#section-installupdate-differentiation)

* [User Attribute Tracking](https://docs.moengage.com/docs/identifying-user)

* [Event Tracking](https://docs.moengage.com/docs/track-event)

* [Push Configuration](https://docs.moengage.com/docs/push-configuration)

* [Geo-fence Configuration](https://docs.moengage.com/docs/push-configuration#section-geofence-push)

* [Rich Landing](https://docs.moengage.com/docs/adding-rich-landing)
 
* [In-App messaging](http://docs.moengage.com/docs/configuring-in-app-nativ)
 
* [Notification Center](http://docs.moengage.com/docs/notification-center)
 
* [Advanced Configuration](https://docs.moengage.com/docs/advanced-integration)
 
* [API Reference](https://moengage.github.io/MoEngage-Android-SDK/)
 
* [GDPR Compliance](https://docs.moengage.com/docs/gdpr-compliance)
 
 
 **Note:** This sample application uses Timber for logging purposes. MoEngage SDK is not 
 dependent on this library. You need not add this library while integrating the SDK.
 
 Please replace the dummy `google-services.json` file with your actual file.

 ## Variations

 |       Sample      |                                                                          Description                                                                          |
|:-----------------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|       [master](https://github.com/moengage/Android-Sample/tree/master)      | Integration Sample where MoEngage SDK handles push token registration and push display.                                                                       |
| [app_handling_push](https://github.com/moengage/Android-Sample/tree/app_handling_push) | Integration Sample where client app handles the push token registration, push display and passes a callback to the SDK for notification received and clicked. |

## Implementation Description

- Refer to [`FirebaseReceiver.java`](https://github.com/moengage/Android-Sample/blob/app_handling_push/java-sample/src/main/java/com/moengage/sample/java/FirebaseReceiver.java) or [`FirebaseReceiver.kt`](https://github.com/moengage/Android-Sample/blob/app_handling_push/kotlin-sample/src/main/java/com/moengage/sample/kotlin/FirebaseReceiver.kt) for implementation reference of Firebase Cloud Messaging(FCM)
- Refer to [`CustomPushMessageListener.java`](https://github.com/moengage/Android-Sample/blob/app_handling_push/java-sample/src/main/java/com/moengage/sample/java/CustomPushMessageListener.java) or [`CustomPushMessageListener.kt`](https://github.com/moengage/Android-Sample/blob/app_handling_push/kotlin-sample/src/main/java/com/moengage/sample/kotlin/CustomPushMessageListener.kt) for implementation reference of Push-Amp and Push-Amp+
  - Callback for Notification Received - Override `onNotificationReceived()` to get a callback for Push-Amp payload.
  - Disable Notification Display from MoEngage - Override `isNotificationRequired()` and return false.
  - Handle redirection for Push-Amp+ - Override `onHandleRedirection()` for handling redirection for Push Amp+ campaigns.
- `SampleNotificationBuilder.java` or `SampleNotificationBuilder.kt` has sample implementation of how notification can be built and how silent push, impression should be passed to SDK.
- Refer to `onCreate()` of [`MainActivity.java`](https://github.com/moengage/Android-Sample/blob/app_handling_push/java-sample/src/main/java/com/moengage/sample/java/MainActivity.java) or [`MainActivity.kt`](https://github.com/moengage/Android-Sample/blob/app_handling_push/kotlin-sample/src/main/java/com/moengage/sample/kotlin/MainActivity.kt) for implementation of how to pass notification click to SDK.