# SlideTone - Data Inventory

**Version:** 1.1  
**Status:** Final  
**Date:** 2026-11-03

---

# 1. Purpose

This document describes the data accessed, processed, stored, and potentially shared by the SlideTone application.

It serves as a technical reference for maintaining the Privacy Policy and completing the Google Play Data Safety declaration.

---

# 2. Application Overview

SlideTone is a trombone tuning application.

The application does not require user accounts, does not operate its own backend, and does not provide cloud synchronization.

Its core tuning functionality works offline. An internet connection is required for online services such as advertisement delivery.

SlideTone is designed to minimize personal data processing. Instrument profiles contain instrument configuration information and do not require personal information about the user.

---

# 3. Data Processed and Stored by SlideTone

## 3.1 Instrument Profiles and Application Settings

- **Data involved:** User-created instrument profiles and application preferences.
- **Profile information:** Instrument family, base pitch, playing mechanism, clef, profile name, tuning reference frequency, transposition, and profile activation status.
- **Settings information:** Theme, application language, note spelling, and note display language.
- **Purpose:** Store instrument configurations and application preferences.
- **Storage:** Locally on the user's device through AsyncStorage.
- **Storage key:** `slidetone.state`.
- **Transmission:** Not transmitted to SlideTone servers or synchronized with cloud services.

Instrument profiles are not user accounts and do not require personal information such as a real name, email address, or contact details.

Users can individually delete instrument profiles through the application. However, at least one profile must remain available.

Application settings can be modified within the application, but there is currently no in-app function to reset all settings to their default values or delete all local application data.

Users can clear the application's local storage through the device's operating system settings.

Android backup and restoration behavior must be verified against the final native application configuration.

## 3.2 Microphone Audio

- **Data involved:** Audio captured through the device microphone.
- **Purpose:** Analyze the instrument's sound and determine its musical pitch.
- **Processing:** Real-time audio analysis on the device.
- **Recording:** SlideTone does not record or retain audio recordings.
- **Transmission:** Audio is not uploaded to SlideTone servers or transmitted to external audio-processing services.

Microphone access is required for the application's core tuning functionality.

## 3.3 Application Analytics and Diagnostics

SlideTone does not currently use first-party analytics, crash-reporting services, or telemetry systems.

No first-party user behavior analytics or application usage telemetry is collected by SlideTone itself.

This statement does not exclude diagnostic or usage information that may be processed by third-party SDKs.

---

# 4. Third-Party Services

## 4.1 Google AdMob

Google AdMob has been selected as SlideTone's advertising provider.

The Google Mobile Ads SDK integration is pending.

Once integrated, the SDK may process certain information to provide, measure, and improve advertising services.

Potentially processed information may include:

- Advertising identifiers and other device identifiers.
- IP address and related technical information.
- Ad impressions and interactions.
- Diagnostic information related to advertising delivery, such as application launch time, hang rate, and energy usage.

Depending on the SDK version, configuration, and applicable requirements, information may be processed for:

- Advertising delivery.
- Advertising measurement and analytics.
- Fraud prevention and security.
- Service improvement.

The exact data processed, purposes, sharing practices, and applicable disclosures must be confirmed against the final SDK integration and Google's official documentation.

SlideTone does not operate its own advertising infrastructure or independently collect advertising analytics.

## 4.2 Google User Messaging Platform (UMP)

The use of Google's User Messaging Platform (UMP) has not yet been confirmed.

If included in the final integration, its purpose, consent flows, privacy options, and associated data processing must be documented and reviewed before the privacy documentation is finalized.

---

# 5. Data Storage and Transmission Summary

| Data Category                   | Local Storage                        | Sent to SlideTone Servers | Third-Party Processing                                         |
|---------------------------------|--------------------------------------|---------------------------|----------------------------------------------------------------|
| Instrument profiles             | Yes                                  | No                        | No                                                             |
| Application settings            | Yes                                  | No                        | No                                                             |
| Microphone audio                | No recordings retained               | No                        | No                                                             |
| First-party analytics           | Not applicable                       | No                        | No                                                             |
| Advertising-related information | Depends on SDK behavior              | Not applicable            | Potentially processed by Google services after SDK integration |
| Consent-related information     | Depends on the final UMP integration | Not applicable            | Depends on the final configuration                             |

---

# 6. Data Deletion and Retention

SlideTone does not maintain its own cloud-based storage for instrument profiles or application settings.

- Individual instrument profiles can be deleted through the application's profile management controls.
- At least one instrument profile must remain available.
- Application settings do not currently have an in-app reset or complete deletion function.
- Clearing the application's local storage through the operating system may permanently remove locally stored profiles and settings.
- Uninstalling the application generally removes its local application data, but operating system backup and restoration mechanisms may affect whether data is restored after reinstallation.
- Microphone audio is analyzed in real time and is not recorded or retained by SlideTone.

Information processed by Google AdMob will be subject to Google's applicable retention and deletion practices once the SDK is integrated.

---

# 7. Outstanding Verification

The following items must be verified before this document is considered final:

1. Confirm the exact data collected or processed by the integrated Google Mobile Ads SDK.
2. Confirm whether UMP will be used and document its consent-management behavior.
3. Verify the advertising configuration, including personalized and non-personalized advertising behavior.
4. Verify the final Android backup and restoration configuration.
5. Review the applicable LGPD and GDPR requirements.
6. Use verified information to complete the Google Play Data Safety declaration.
7. Ensure consistency between this inventory, the public Privacy Policy, and the actual application behavior.

---

# 8. Document Status

This inventory is a technical draft based on the application's current architecture and confirmed behavior.

Instrument profiles and application settings are stored locally through AsyncStorage under the `slidetone.state` key.

The application supports individual profile deletion but does not currently provide an in-app function to reset settings or delete all locally stored application data.

Microphone audio is processed locally in real time and is not recorded or uploaded to SlideTone servers.

The advertising-related sections remain subject to verification after Google AdMob SDK integration and the decision regarding a consent-management solution.

The document must be updated whenever the application's data processing practices or third-party integrations change.