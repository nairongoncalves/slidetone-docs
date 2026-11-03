# SlideTone - Data Inventory

**Version:** 1.0  
**Status:** Final  
**Date:** 2026-11-03

---

# 1. Purpose

This document describes the data accessed, processed, stored, and potentially shared by the SlideTone application.

It serves as a technical reference for preparing the Privacy Policy and completing the Google Play Data Safety declaration.

---

# 2. Application Overview

SlideTone is a trombone tuning application.

The application does not require user accounts, does not operate its own backend, and does not provide cloud synchronization.

Its core tuning functionality works offline. An internet connection may be required to load advertisements.

---

# 3. Data Processed by SlideTone

## 3.1 User Profiles and Settings

- **Data involved:** User-created profiles and application preferences.
- **Purpose:** Store instrument configurations and user preferences.
- **Storage:** Locally on the user's device.
- **Transmission:** Not transmitted to SlideTone servers or synchronized with cloud services.

## 3.2 Microphone Audio

- **Data involved:** Audio captured through the device microphone.
- **Purpose:** Analyze the instrument's sound and determine its musical pitch.
- **Processing:** Real-time audio analysis.
- **Recording:** SlideTone does not record or retain audio recordings.
- **Transmission:** Audio is not uploaded to SlideTone servers.

## 3.3 Application Analytics and Diagnostics

SlideTone does not currently use first-party analytics, crash-reporting services, or telemetry systems.

No user behavior analytics or application usage telemetry is collected by SlideTone itself.

---

## 4. Third-Party Services

## 4.1 Google AdMob

SlideTone integrates Google AdMob to display advertisements in designated areas of the application.

The Google Mobile Ads SDK may process certain information to provide, measure, and improve advertising services.

Potentially processed information may include:

- Advertising identifiers.
- IP address and related technical information.
- Ad impressions and interactions.
- Diagnostic information related to advertising delivery.

**Important:** The exact data processed and the applicable disclosures must be confirmed against the final SDK integration, configuration, and Google documentation before this inventory is finalized.

SlideTone does not operate its own advertising infrastructure or independently collect advertising analytics.

## 4.2 Google User Messaging Platform (UMP)

The use of Google's User Messaging Platform (UMP), if included in the final integration, will be documented separately.

---

Its purpose, consent flows, and associated data processing must be reviewed before the privacy documentation is finalized.

# 5. Data Storage and Transmission Summary

| Data Category                   | Local Storage           | Sent to SlideTone Servers                  |
|---------------------------------|-------------------------|--------------------------------------------|
| User profiles                   | Yes                     | No                                         |
| Application settings            | Yes                     | No                                         |
| Microphone audio                | No recordings retained  | No                                         |
| First-party analytics           | Not applicable          | No                                         |
| Advertising-related information | Depends on SDK behavior | Processed by Google services as applicable |

---

# 6. Outstanding Verification

The following items must be verified before this document is considered final:

1. Confirm the exact data collected or processed by the integrated Google Mobile Ads SDK.
2. Confirm whether UMP will be used and document its consent-management behavior.
3. Verify the advertising configuration, including personalized and non-personalized advertising behavior.
4. Review the applicable LGPD and GDPR requirements.
5. Use the verified information to complete the Google Play Data Safety declaration.
6. Ensure consistency between this inventory, the public Privacy Policy, and the actual application behavior.

---

## 7. Document Status

This inventory is an initial technical draft based on the application's current architecture and confirmed behavior.

The advertising-related sections remain subject to verification after the Google AdMob SDK and any consent-management solution are integrated.

The document must be updated whenever the application's data processing practices or third-party integrations change.