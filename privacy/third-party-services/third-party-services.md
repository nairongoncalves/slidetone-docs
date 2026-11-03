# SlideTone - Third-Party Services

**Version:** 1.1  
**Status:** Final  
**Date:** 2026-11-03

---

# 1. Purpose

This document identifies the third-party services selected for integration into the SlideTone application.

It describes each service's purpose, its intended role in the application, the information it may process, and the privacy considerations associated with its use.

This document supports the preparation and maintenance of the SlideTone Privacy Policy and Google Play Data Safety declaration.

---

# 2. Third-Party Services Overview

SlideTone has selected Google AdMob as its advertising provider. Its SDK integration is pending.

Google User Messaging Platform (UMP) is under evaluation and has not been confirmed for integration.

| Provider | Service                       | Purpose                                                | Status                                      |
|----------|-------------------------------|--------------------------------------------------------|---------------------------------------------|
| Google   | Google AdMob                  | Display advertisements                                 | Selected; SDK integration pending           |
| Google   | User Messaging Platform (UMP) | Manage advertising-related privacy choices and consent | Under evaluation; integration not confirmed |

No other third-party analytics, crash-reporting, or telemetry services are currently used by SlideTone.

---

# 3. Google AdMob

## 3.1 Service Description

Google AdMob is Google's mobile advertising platform.

SlideTone has selected AdMob to display banner advertisements in designated areas of the application. Advertising is intended to help support the development and maintenance of the application while keeping its core functionality free to use.

The Google Mobile Ads SDK has not yet been integrated.

Official website: https://admob.google.com/

## 3.2 Advertising Placements

The approved advertising placements are:

- **Tuner:** One banner at the bottom of the tuner screen.
- **Instrument Catalog:** Banner advertisements displayed between instrument cards, according to the application's advertising frequency rules.
- **Instrument Details:** At most one banner after the educational content.

Advertisements are not displayed during onboarding, in user profiles, settings, the About screen, or the application menu.

SlideTone does not plan to use full-screen advertisements, forced video advertisements, or advertising formats that block the application's core functionality.

The final implementation must follow the approved Advertisement Display specification.

## 3.3 Potential Data Processing

Once integrated, the Google Mobile Ads SDK may automatically collect and share certain information from the user's device.

According to Google's published Google Play Data Safety disclosure for the Android SDK, potentially processed information may include:

| Data category                  | Description                                                                                      | Potential purpose                            |
|--------------------------------|--------------------------------------------------------------------------------------------------|----------------------------------------------|
| IP address                     | Device IP address, which may be used to estimate general location                                | Advertising, analytics, and fraud prevention |
| User interactions              | Application launches, taps, and advertising interactions, including video views where applicable | Advertising and analytics                    |
| Diagnostic information         | SDK and application performance information, such as launch time, hang rate, and energy usage    | Diagnostics and service improvement          |
| Device and account identifiers | Android Advertising ID, App Set ID, and other applicable identifiers                             | Advertising, analytics, and fraud prevention |

Google states that information collected by the Google Mobile Ads SDK is encrypted in transit using Transport Layer Security (TLS).

The Android Advertising ID is subject to applicable Android settings, user controls, and SDK configuration.

Source: https://developers.google.com/admob/android/privacy/play-data-disclosure

**Implementation note:** This table describes potential SDK data processing, not data collection already confirmed in SlideTone. The exact data processing behavior must be reviewed against the SDK version and configuration actually integrated into the application. Optional features and configuration choices may affect the applicable disclosures.

## 3.4 Data Sharing

Once integrated, information processed by the Google Mobile Ads SDK may be transmitted to Google and other advertising-related parties involved in delivering advertisements.

SlideTone does not operate its own advertising infrastructure and does not independently collect advertising analytics.

Techminds remains responsible for accurately disclosing the SDK's data processing and sharing practices, even when information is collected or processed directly by a third-party SDK.

## 3.5 User Choices and Advertising Preferences

Advertising behavior may depend on applicable privacy requirements, consent status, device settings, and the configuration of the advertising SDK.

The final implementation must ensure that advertising requests comply with applicable consent and privacy requirements.

The application must not assume that all users have consented to personalized advertising.

The public Privacy Policy must describe the advertising practices and available user choices supported by the implemented configuration.

---

# 4. Google User Messaging Platform (UMP)

## 4.1 Service Description

Google User Messaging Platform (UMP) is Google's consent-management solution for applications using Google advertising services.

It can determine whether a privacy message needs to be presented, display applicable consent forms, and provide a mechanism for users to manage their privacy choices.

Official documentation: https://developers.google.com/admob/android/privacy

## 4.2 Integration Status

UMP integration has not been confirmed for SlideTone.

Its inclusion and configuration will be evaluated as part of the advertising integration.

If adopted, the implementation must:

- Retrieve updated consent information when the application starts.
- Display privacy messages when required.
- Check whether advertising requests are permitted before requesting advertisements.
- Provide a privacy options entry point whenever required by the applicable consent configuration.

These requirements must be validated against the current UMP documentation and the final configuration.

## 4.3 Data Processing

If integrated, UMP will communicate with Google's consent-management services to retrieve and manage consent-related information.

The exact information processed and stored will depend on the final implementation and configuration.

UMP consent-management behavior must be documented separately from the data processing performed by the Google Mobile Ads SDK.

## 4.4 Regional Requirements

Consent requirements may vary depending on the user's location and the applicable privacy regulations.

SlideTone must use an appropriate consent configuration for the regions in which it is distributed.

The implementation must not assume that a single consent message or configuration is sufficient for every jurisdiction.

---

# 5. Services Not Used by SlideTone

The following third-party services are not currently used by SlideTone:

- Third-party analytics platforms.
- Third-party crash-reporting services.
- Third-party behavioral tracking platforms outside the planned advertising integration.
- Cloud-based user profile storage or synchronization services.
- External audio processing or speech recognition services.

SlideTone analyzes microphone audio locally in real time. Audio is not recorded or uploaded to SlideTone servers.

Instrument profiles and application settings are stored exclusively on the user's device through AsyncStorage.

Instrument profiles contain instrument configuration information and do not require personal information about the user.

Users can individually delete instrument profiles through the application, but at least one profile must remain available.

The application currently does not provide an in-app function to reset settings or delete all locally stored application data.

---

# 6. Developer Responsibilities

Techminds, as the SlideTone developer, is responsible for:

1. Reviewing the privacy and data-processing documentation of every integrated third-party SDK.
2. Verifying the data collected and shared by each SDK version used in the application.
3. Configuring advertising and consent-management services according to applicable privacy requirements.
4. Keeping the Privacy Policy and Google Play Data Safety declaration consistent with the application's actual behavior.
5. Reviewing third-party SDK updates for changes in data collection, permissions, or privacy practices.
6. Updating this document whenever a third-party service is added, removed, or reconfigured.

The integration of a third-party SDK does not transfer the developer's responsibility for the application's privacy disclosures.

**Privacy contact:** nairongoncalves@gmail.com

---

# 7. Outstanding Verification

The following items must be completed before this document is considered final:

- [ ] Integrate the Google Mobile Ads SDK.
- [ ] Verify the exact SDK version and its data-processing disclosures.
- [ ] Review the advertising configuration and applicable user choices.
- [ ] Decide whether Google UMP will be integrated.
- [ ] If UMP is adopted, verify its consent flows and privacy options requirements.
- [ ] Test advertising behavior under the applicable consent scenarios.
- [ ] Review the final configuration against Google Play Data Safety requirements.
- [ ] Ensure consistency with the public Privacy Policy and Data Inventory.
- [ ] Confirm that the implemented advertising behavior follows the approved Advertisement Display specification.

---

# 8. Document Status

This document describes the third-party services selected or being evaluated for SlideTone and their intended roles.

Google AdMob has been selected as the advertising provider, but its SDK integration and final configuration are pending.

Google UMP remains under evaluation and must not be considered an active application component until its integration is confirmed.

No third-party analytics, crash-reporting, or telemetry services are currently used by SlideTone.

This document must be reviewed and updated before public release and whenever the application's third-party integrations or data-processing practices change.