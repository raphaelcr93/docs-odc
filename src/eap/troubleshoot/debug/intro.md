---
summary: Learn how to use the debug features provided by OutSystems to easily find and troubleshoot semantic errors in your apps.
tags: support-application_development; support-Application_Troubleshooting; support-Application_Troubleshooting-featured
locale: en-us
guid: bd64bfb4-afcf-4eb8-b87a-1923fd19524c
app_type: mobile apps, reactive web apps
---

# Debugging apps

Debug your app in ODC Studio by pausing the execution at [breakpoints](<breakpoints.md>), specific points in an app, and then running the logic step-by-step. This lets you find any issues in your logic design.

The [Debugger tab](<debugger-ui-reference.md>) shows app information like variable and runtime values. It also shows the current debugging context (current [thread](<threads.md>), event name, UI flow, screen and action, when applicable. Use the debugger commands available in the Debugger Toolbar and in the Debugger menu.

When debugging an action in your library, ensure that the app is using the most recent version, as there may be multiple versions of the library; otherwise, a warning occurs. Stepping into a Service Action from a consumer app isn't supported.

![The Debugger window](images/debugger-intro-ss.png?width=800)

## How to debug your app

To debug your app, do the following in ODC Studio:

1. Click the 1-Click Publish button to save the latest changes in the app before debugging. 

1. Set one or more [breakpoints](<breakpoints.md>) in the app you're debugging.

1. Before debugging a **native mobile app**, choose a debugging target in the [Debugger tab](<debugger-ui-reference.md>): Android, iOS, or Google Chrome which emulates a device. The section [Mobile Debugging Scenarios](<#mobile-debugging-scenarios>) includes further details about the different targets. If you're debugging a **mobile app distributed as a PWA**, select **Emulate using Google Chrome** in **Debugger** > **Debug Setup**. 

1. Start debugger by clicking the **Start Debugging** button in the [Debugger tab](<debugger-ui-reference.md>). When you're debugging mobile apps using the Google Chrome target, ODC Studio opens a dedicated Chrome browser instance for debugging only.

1. Do some tasks in the app, up to a point when the execution runs into a breakpoint and suspends.

1. When you switch to the ODC Studio window, the flow containing the element with the breakpoint shows on the canvas. ODC Studio selects the element with the breakpoint and marks is with the ![debug icon](images/overlay-active-request.png) debug icon.

1. The execution context shows in the **Threads** tab of the **Debugger** tab, marked with the ![current thread](images/overlay-active-request.png) current thread icon, showing the current execution stack of the app elements. The **Debugger** tab also shows additional information you can explore.

1. After analyzing the runtime values at that execution point, you can continue running the app by:

    * Selecting one of the commands available for advancing the execution of the application logic: ![continue icon](images/toolbar-button-continue.png) **Continue**, ![step over icon](images/toolbar-button-step-over.png) **Step Over**, ![step into button](images/toolbar-button-step-into.png) **Step Into** or ![step out button](images/toolbar-button-step-out.png) **Step Out**. The execution point advances according to the command you run.

    * Right-clicking an element on the canvas (or in the app tree) and selecting the **Continue To Here** option in the context menu. The execution continues until it reaches that element on the canvas.

## Mobile debugging scenarios { #mobile-debugging-scenarios }

There are different ways of debugging a mobile app that help you discover, understand, and fix issues. You can debug your mobile app in one of the following ways:

Emulate the mobile app using the Google Chrome browser in your PC
:   Use the Chrome browser in your PC to debug your mobile app if you don't need to execute native plugins, as the native plugins can't run in PC. This option is convenient to test the logic of the app. However, to check the performance or experience of the mobile app, test your app on a real device.
    Also consider this scenario if all the native plugins in the mobile app have action wrappers defined that return mock data when the plugin isn't available.

Install the Mobile App on a Device
:   Test the mobile app directly on a device as your users would run it. It's the best place to test the performance and experience of your app. You can do it in an iOS or Android device. Generate the native app package for your app in ODC Studio using the `Debug` (Android) or `Development` (iOS) build type, install it in the device, and follow the steps below according to your mobile device platform.

    To test a mobile app on an iOS device:
    
    1. On your **PC**, install [iTunes](<https://www.apple.com/itunes/download/>).
    2. In your **device**, turn the "Web Inspector" option **on**. For detailed instructions see [Troubleshoot Debugger Connection Issues](<troubleshoot-debugger-connection.md#web-inspector-is-not-enabled-on-your-device>).
    3. Connect your mobile device to the PC through a USB cable.
    4. In your **device**, allow the PC to debug on the device.
    
    To test a mobile app on an Android device:
    
    5. In your **device**, turn [USB debugging ON](<https://developer.android.com/studio/debug/dev-options.html#enable>).
    6. Connect your mobile device to the PC through a USB cable.
    7. In your **device**, allow the PC to debug on the device.
    
    For more help, check [Troubleshoot Debugger Connection Issues](<troubleshoot-debugger-connection.md>).

If you need to troubleshoot app crashes, a plugin or check the native code of apps, debug your apps with the mobile platform's native tools, such as Android Studio for Android and Xcode for iOS. Before debugging using the native tools, you must generate a mobile package with `Debug` (Android) or `Development` (iOS) build type.

## Working with dates and times

When debugging an app and checking the values of the Date Time data type, keep in mind the following:

* During debugging, ODC Studio shows UTC date and time in the debugger.
* In the client UI, the date and time are in the timezone of the client.
* On the server, the date and time are in the timezone of the server.