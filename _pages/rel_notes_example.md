---
title: Release Notes Sample
permalink: /rel_notes_example/
layout: single
author_profile: true
toc: true
---

**Note**: This is an example of documentation I have created for multiple organizations in the past. All product names, features, and bugs have been changed. I have changed or removed some content to obscure the organization, product, and release contents.

For more information about my process, toolchain, and challenges, see [Release Notes](./projects.md#release-notes) on the Documentation Projects page.

---

# Release Notes for ProductOne 2.1.0

## About ProductOne
*This section provides an overview of the product. This text in reused from the product overview short description provided in all documents for this product.*

ProductOne, a cloud-based smartphone application, enhances team mobility and simplifies workflows to provide efficient, reliable communication across multiple locations. With ProductOne, technicians can document customer records while receiving filtered tasks and prioritized notifications.

This ProductOne version is compatible with the latest release of the ProductTwo server architecture, which provides an Administrator Console to configure and monitor ProductOne installation and usage. For more information about ProductTwo compatibility and supported mobile devices, see the ProductOne 2.1.0 Administrator Guide.

## New Features in this Release
- **Configurable Notification Volume Control**

  ProductOne administrators can now customize the volume for default (non-critical) and critical alerts in ProductTwo. When the custom notification volume is configured, the ProductOne app plays the notification tone at the volume configured in ProductTwo instead of the device's configured volume.

  To support this new feature, we have added two new configuration options in ProductTwo: **Notification Volume: Critical** and **Notification Volume: Non-Critical**. 

  For more information about this new feature, see the "Notification Volume" topic in the ProductOne 2.1.0 User Guide.
 
  For configuration information, see the "Configuring Notification Volume" topic in the ProductTwo 2.1.0 Administrator Guide.

- **Notification Grouping per Device Settings**

  When the ProductOne app is in the foreground, device settings do not change the in-app behavior. Notifications now display as individual notifications and are no longer grouped. 
 
  This is a change from behavior seen in previous releases. Previously, notifications were grouped, which sometimes delayed high priority notification awareness.

  When the ProductOne app is in the background (e.g., the device is focused on the home screen, another app, or the lock screen), notification delivery behavior respects the device settings unless overridden through Mobile Device Management (MDM). 
 
  This is a change from behavior seen in previous releases. Previously, device settings were not respected and only the latest notification was listed, which sometimes delayed high priority notification awareness.


## Resolved Issues in this Release
This section provides a list of critical issues resolved in this release.

- The ProductOne app no longer plays the ringtone after connecting to a video call.
- Conference calls now correctly display the information for all attendees. Previously, the app was showing the details for the first 3 attendees only. 
- If a user declines a call receives a voicemail from the caller, the app now opens the Voicemail screen instead of the keypad when the user taps the voicemail notification.

## Known Issues in this Release
This section provides a list of known product defects and limitations in this product.

- Tapping a missed call notification from the device's lock screen navigates the user to the Inbox screen instead of the Recent Calls screen. There is no workaround.
- There is no call audio when both users are on a cellular network and ProductOne 2.1.0 is connected to an old ProductTwo 1.x Server.
 
   Workaround: Connect to the app through a Wi-Fi network instead of a Cellular network. If this issue is critical for your organization, contact us to upgrade the ProductTwo Server to the latest version.