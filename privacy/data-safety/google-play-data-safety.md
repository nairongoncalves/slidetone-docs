# SlideTone - Google Play Data Safety

**Version:** 1.0  
**Status:** Final  
**Date:** 2026-11-03

---

# 1. Purpose

This document defines the data collection, sharing, and security information required to complete and maintain the Google Play Data Safety section for the SlideTone application.

It serves as an internal reference for:

- Identifying data collected or transmitted by the application.
- Identifying data collected by integrated third-party SDKs.
- Determining applicable data categories and processing purposes.
- Reviewing data-sharing and security practices.
- Maintaining consistency between the Google Play declaration and the public Privacy Policy.

This document is not a substitute for the official Google Play Console Data Safety form.

---

# 2. Application Overview

SlideTone is a trombone tuning application.

The application follows a local-first architecture:

- No user account or registration is required.
- User profiles and application settings are stored exclusively on the user's device.
- No cloud synchronization is provided.
- Microphone audio is analyzed locally in real time.
- Audio is not recorded or uploaded to SlideTone servers.
- No first-party analytics, crash-reporting, or telemetry services are currently used.
- Google AdMob has been selected as the advertising provider, but its SDK integration is pending.

The application's core tuning functionality works offline. An internet connection is required for advertising services.

---

# 3. Google Play Data Safety Principles

The Google Play Data Safety declaration must reflect the actual behavior of the complete application, including all integrated libraries and SDKs.

According to Google Play's guidelines:

- Data transmitted off the user's device by the application or its SDKs must be considered.
- Data transmitted to third-party servers must be considered, even when the developer does not receive it.
- Data processed exclusively on the user's device and never transmitted off-device does not need to be declared as collected.
- Ephemerally processed data must still be considered when completing the form, even when it qualifies for an exemption from disclosure in the public Data Safety section.
- Data collected or processed pseudonymously must also be considered.

Official documentation:

https://support.google.com/googleplay/android-developer/answer/10787469

---

# 4. Data Categories and Processing

## 4.1 User Profiles and Application Settings

| Attribute                          | Description                                                          |
|------------------------------------|----------------------------------------------------------------------|
| Data                               | User-created profiles and application preferences                    |
| Storage                            | Local device storage                                                 |
| Transmission                       | Not transmitted                                                      |
| Purpose                            | Core application functionality                                       |
| Data Safety collection declaration | Not required, provided the information remains exclusively on-device |

User profiles and application settings are stored exclusively on the user's device.

SlideTone does not transmit this information to its own servers or synchronize it with cloud services.

## 4.2 Microphone Audio

| Attribute                          | Description                                                     |
|------------------------------------|-----------------------------------------------------------------|
| Data                               | Audio captured through the device microphone                    |
| Processing                         | Local, real-time audio analysis                                 |
| Recording                          | No audio recordings are retained                                |
| Transmission                       | Not uploaded to SlideTone servers                               |
| Purpose                            | Detect musical pitch                                            |
| Data Safety collection declaration | Not required, provided audio is processed exclusively on-device |

Microphone audio is used exclusively for the tuning functionality.

The application does not record or transmit microphone audio to external servers.

The Android microphone permission is required to access the audio input.

## 4.3 Advertising-Related Data - Google AdMob

Google AdMob is the selected advertising provider.

The Google Mobile Ads SDK automatically collects and shares certain information according to Google's published Android SDK data disclosure.

The following categories must be evaluated for the final Data Safety declaration:

| Google SDK information                                         | Potential Google Play data category                              | Processing purposes                              |
|----------------------------------------------------------------|------------------------------------------------------------------|--------------------------------------------------|
| Device IP address                                              | Approximate location, depending on how it is used and classified | Advertising, analytics, fraud prevention         |
| Application launches, taps, and advertising interactions       | App interactions                                                 | Advertising, analytics, fraud prevention         |
| SDK and application performance information                    | Diagnostics                                                      | Analytics, fraud prevention, service improvement |
| Android Advertising ID, App Set ID, and applicable identifiers | Device or other IDs                                              | Advertising, analytics, fraud prevention         |

**Important:** The categories above are preliminary mappings. The final classification must follow the current Google Play data-type definitions and the actual SDK behavior.

Official Google documentation:

https://developers.google.com/admob/android/privacy/play-data-disclosure

## 4.4 Advertising Data Processing Details

The Google Mobile Ads SDK may automatically collect and share information for:

- Advertising delivery.
- Advertising measurement.
- Analytics.
- Fraud prevention and abuse detection.

Google documents that the SDK encrypts collected user data in transit using Transport Layer Security (TLS).

Android Advertising ID collection is optional and may be affected by application configuration and Android privacy settings.

Optional SDK features may introduce additional data-processing activities and must be reviewed before release.

## 4.5 Consent-Related Information - Google UMP

Google User Messaging Platform (UMP) is under evaluation.

Its integration has not been confirmed.

If adopted, its data-processing behavior must be reviewed and included in the Data Safety assessment where applicable.

No final disclosure should be made based solely on the assumption that UMP will be integrated.

---

# 5. Preliminary Data Safety Assessment

The following table summarizes the current assessment.

| Data category        | SlideTone processing                           | Third-party processing                | Declaration status          |
|----------------------|------------------------------------------------|---------------------------------------|-----------------------------|
| User profiles        | Local only                                     | None identified                       | No collection expected      |
| Application settings | Local only                                     | None identified                       | No collection expected      |
| Microphone audio     | Local real-time processing                     | None identified                       | No collection expected      |
| Approximate location | No direct location feature                     | Potentially inferred from IP by AdMob | Verify final classification |
| App interactions     | No first-party analytics                       | AdMob                                 | Expected to be declared     |
| Diagnostics          | No first-party crash reporting or telemetry    | AdMob                                 | Expected to be declared     |
| Device or other IDs  | No first-party identifier collection confirmed | AdMob                                 | Expected to be declared     |

This assessment is preliminary and must be reviewed after the advertising SDK is integrated.

---

# 6. Data Collection and Sharing

## 6.1 First-Party Collection

SlideTone does not currently operate backend services or first-party analytics infrastructure.

The application does not collect user profiles, settings, or microphone audio on remote servers.

## 6.2 Third-Party Collection

The Google Mobile Ads SDK may collect information automatically when advertising services are initialized and used.

The developer must account for this processing even when the information is transmitted directly to Google or other advertising-related parties.

## 6.3 Data Sharing Classification

The Google Play Data Safety form distinguishes data collection from data sharing.

The final declaration must evaluate:

- Which information is transmitted off-device.
- Which parties receive the information.
- Whether the information is transferred to a service provider acting on behalf of the developer.
- Whether Google or other advertising-related parties process information for their own purposes.
- Whether any applicable Google Play sharing exceptions apply.

The final declaration must not automatically classify every SDK transmission as either sharing or exempt from sharing without reviewing the applicable definitions.

---

# 7. Security Practices

## 7.1 Encryption in Transit

Google states that user data collected by the Google Mobile Ads SDK is encrypted in transit using TLS.

The application-level Data Safety answer regarding encryption in transit must be evaluated across all data transmitted off the user's device by the application and its SDKs.

The developer must verify that every applicable transmission is encrypted before declaring that all user data is encrypted in transit.

## 7.2 Local Data Storage

User profiles and application settings are stored locally on the user's device.

SlideTone does not maintain a remote database containing this information.

## 7.3 Microphone Data

Microphone audio is analyzed locally in real time and is not uploaded to SlideTone servers.

---

# 8. Data Deletion

SlideTone does not provide user accounts or a cloud-based profile database.

User-created profiles and application settings can be managed locally through the application. Removing application data or uninstalling the application may remove locally stored information.

Information processed by Google advertising services may be subject to Google's own retention, privacy, and deletion mechanisms.

The final Data Safety declaration must accurately reflect the deletion mechanisms available for information collected by the application and its third-party SDKs.

The absence of user accounts does not automatically mean that all third-party data can be deleted through uninstalling the application.

---

# 9. Advertising and Target Audience Considerations

The final Data Safety declaration must be consistent with the application's declared target audience and advertising configuration.

Before release, the development team must verify:

- The target age groups selected in Google Play Console.
- Whether the application is subject to Google Play Families requirements.
- Whether any advertising restrictions apply to the declared audience.
- Whether the advertising SDK configuration complies with the applicable requirements.
- Whether additional privacy disclosures are necessary for users in specific jurisdictions.

Official documentation:

https://support.google.com/googleplay/android-developer/answer/9867159

---

# 10. Google Play Console Declaration Checklist

The following items must be reviewed when completing the official Data Safety form.

## 10.1 Data Collection

- [ ] Review all application permissions and their actual use.
- [ ] Review all integrated native and React Native SDKs.
- [ ] Identify all data transmitted off-device.
- [ ] Confirm whether any optional SDK features introduce additional collection.
- [ ] Evaluate the applicable data categories.
- [ ] Verify whether any data is processed ephemerally.
- [ ] Confirm that local-only data is not incorrectly declared as collected.

## 10.2 Data Sharing

- [ ] Identify all third parties receiving application data.
- [ ] Review Google AdMob's data-sharing practices.
- [ ] Evaluate applicable Google Play service-provider exceptions.
- [ ] Verify whether any additional advertising partners receive information.
- [ ] Complete the data-sharing questions accurately.

## 10.3 Security

- [ ] Verify encryption in transit for all applicable data transmissions.
- [ ] Confirm local data-storage behavior.
- [ ] Review applicable data-deletion mechanisms.
- [ ] Confirm whether users can request deletion of applicable data.

## 10.4 Advertising and Consent

- [ ] Complete Google AdMob SDK integration.
- [ ] Verify the final SDK version.
- [ ] Review the SDK's latest Data Safety disclosure.
- [ ] Decide whether Google UMP will be integrated.
- [ ] Verify applicable regional consent requirements.
- [ ] Confirm the final advertising configuration.

## 10.5 Publication

- [ ] Complete the Data Safety form in Google Play Console.
- [ ] Review all answers against the actual production application.
- [ ] Verify consistency with the public Privacy Policy.
- [ ] Confirm that the public Privacy Policy URL is accessible.
- [ ] Review the declaration whenever the application's data-processing practices change.

---

# 11. Maintenance and Updates

This document must be reviewed whenever:

- A new SDK or third-party service is integrated.
- An existing SDK is upgraded.
- Application permissions change.
- New categories of data are accessed or processed.
- Data transmission or storage behavior changes.
- Advertising configuration changes.
- Google Play Data Safety requirements are updated.

The development team is responsible for keeping this document, the public Privacy Policy, and the Google Play Data Safety declaration consistent.

---

# 12. Document Status

This document represents the preliminary Data Safety assessment for SlideTone.

The application currently stores user profiles and settings locally and processes microphone audio exclusively on-device.

Google AdMob has been selected, but its SDK integration and final configuration are pending.

The final Google Play Data Safety declaration must be completed only after reviewing the actual production SDK versions, configuration, and data-processing behavior.

This document must be updated before the public release and whenever the application's data practices change.