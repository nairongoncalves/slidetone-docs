# SlideTone - Consent Management

**Version:** 1.0  
**Status:** Final  
**Date:** 2026-11-03

---

# 1. Purpose

This document defines the consent-management principles and requirements for the SlideTone application.

It describes how privacy choices related to advertising must be handled, how consent requirements are determined, and how users should be able to manage their applicable privacy preferences.

This document serves as a technical and operational reference for the advertising integration, privacy implementation, and public Privacy Policy.

---

# 2. Scope

This document applies to:

- Google AdMob and its advertising-related data processing.
- Google User Messaging Platform (UMP), if adopted.
- Advertising consent and privacy choices.
- Regional privacy requirements applicable to SlideTone users.

It does not cover general application settings or user-created instrument profiles, which are stored locally and are unrelated to advertising consent.

---

# 3. Current Implementation Status

The following implementation status applies:

| Component                   | Status                                      |
|-----------------------------|---------------------------------------------|
| Google AdMob                | Selected; SDK integration pending           |
| Google UMP                  | Under evaluation; integration not confirmed |
| Consent messages            | Not configured                              |
| Privacy options entry point | Not implemented                             |
| Advertising consent flow    | Pending implementation                      |

Until the integration is completed, no consent-management behavior should be considered implemented or verified.

----

# 4. Consent Management Principles

SlideTone must follow these principles:

## 4.1 Regional Compliance

Consent requirements must be determined according to the user's location and the privacy regulations applicable to that user.

The application must not assume that the same consent requirements apply worldwide.

Relevant regulations may include:

- Brazil's General Data Protection Law (LGPD).
- The European Union's General Data Protection Regulation (GDPR).
- Other applicable regional privacy and electronic communications regulations.

## 4.2 Informed Choices

When a consent message is required, users must receive clear and understandable information about:

- Why advertising is displayed.
- Which third-party services are involved.
- What categories of information may be processed.
- Whether personalized advertising is involved.
- Which privacy choices are available.

Consent interfaces must not use misleading wording or design patterns that pressure users into accepting optional data processing.

## 4.3 Respect for User Choices

The application must respect the user's applicable privacy choices when making advertising requests.

It must not request personalized advertising when the required consent or legal basis is absent.

## 4.4 Transparency

The public Privacy Policy must accurately describe the advertising and consent-management practices implemented in the application.

---

# 5. Google User Messaging Platform (UMP)

## 5.1 Purpose

If adopted, Google UMP will be used to manage applicable advertising consent requirements.

Its responsibilities may include:

- Retrieving updated consent information.
- Determining whether a privacy message must be displayed.
- Presenting applicable consent forms.
- Updating consent status.
- Determining whether advertising requests are permitted.
- Providing access to privacy options when required.

Official documentation:

https://developers.google.com/admob/android/privacy

## 5.2 Consent Information Update

When the application starts, the consent-management implementation must retrieve updated consent information before requesting advertisements.

The implementation must follow Google's recommended UMP workflow.

If a consent form is required and available, it must be presented at the appropriate point in the application lifecycle.

## 5.3 Consent Form Availability

The application must handle the following situations:

- A consent form is required and successfully loaded.
- No consent form is required.
- A consent form cannot be loaded because of a network or service error.
- Updated consent information cannot be retrieved.

An error retrieving consent information must not be interpreted as user consent.

The application must follow the SDK's documented behavior and applicable privacy requirements when handling these situations.

## 5.4 Privacy Options

If the final UMP configuration requires a privacy options entry point, SlideTone must provide an accessible way for users to reopen the relevant privacy choices.

The entry point should be available from an appropriate application location, such as Settings.

It must not be hidden behind advertising interactions or made unnecessarily difficult to find.

---

# 6. Advertising Request Requirements

Before requesting advertisements, SlideTone must evaluate the current consent-management state and applicable SDK requirements.

The implementation must:

1. Complete the required consent information update.
2. Present any required consent form.
3. Check whether the SDK permits advertising requests.
4. Configure advertising requests according to the user's applicable privacy choices.
5. Avoid requesting personalized advertising when the necessary consent or other applicable legal basis is absent.

The absence of a consent form does not automatically mean that personalized advertising is permitted.

Advertising requests must follow the final AdMob and UMP configuration and the applicable regional requirements.

---

# 7. Consent States and Error Handling

The implementation must distinguish between consent-management states.

The following logical states are recommended for application-level handling:

| State               | Description                                                   | Expected behavior                                       |
|---------------------|---------------------------------------------------------------|---------------------------------------------------------|
| Not initialized     | Consent information has not yet been retrieved                | Do not initiate advertising requests prematurely        |
| Updating            | Consent information is being retrieved                        | Wait for the required consent workflow                  |
| Consent required    | A consent form must be presented                              | Load and present the applicable form                    |
| Consent obtained    | The required consent process has been completed               | Follow the resulting advertising permissions            |
| No consent required | No consent form is required for the current configuration     | Follow the SDK's returned advertising permissions       |
| Error               | Consent information or a required form could not be retrieved | Apply the documented SDK behavior; never assume consent |

These are logical application-level states, not necessarily the exact status names exposed by the UMP SDK.

---

## 8. User Privacy Rights

Users must be able to exercise applicable privacy rights under the regulations governing their personal information.

Depending on the applicable legal requirements, these rights may include:

- Access to personal information.
- Correction of inaccurate information.
- Deletion of personal information.
- Information about data processing and sharing.
- Withdrawal or modification of consent.
- Other applicable privacy rights.

Requests involving information processed by Google services may need to be handled through Google's privacy mechanisms, depending on the nature of the information and the applicable legal responsibilities.

The public Privacy Policy must explain how users can contact the application developer regarding privacy-related requests.

---

## 9. Data Storage and Consent Information

The application must distinguish between locally stored application preferences and consent information managed by third-party SDKs.

User profiles and application settings remain stored exclusively on the device.

Consent information may be stored or processed by Google services and SDK components according to their documented behavior.

The implementation must not claim that all consent information is stored exclusively on the device unless this has been verified.

---

## 10. Offline Behavior

SlideTone's core tuning functionality must remain available offline.

Because advertising and consent-management services may require an internet connection, the application must handle unavailable network connections gracefully.

In particular:

- Failure to retrieve advertising content must not prevent access to the tuner.
- Failure to load a consent form must not be interpreted as consent.
- The application must follow the documented SDK behavior for unavailable consent information.
- No advertising-related network failure should interrupt microphone capture or tuner operation.

---

## 11. Security and Privacy Requirements

The consent-management implementation must:

- Use supported and maintained SDK versions.
- Follow Google's official integration recommendations.
- Avoid storing unnecessary personal information.
- Avoid bypassing or manipulating consent status.
- Respect the applicable advertising restrictions.
- Ensure that consent-related interfaces are accessible and understandable.

Consent-related information must not be used for purposes unrelated to the disclosed processing.

---

## 12. Outstanding Implementation Tasks

The following items must be completed before this document is considered final:

- [ ] Confirm whether Google UMP will be integrated.
- [ ] Review the current UMP compatibility and integration requirements for the selected React Native advertising SDK.
- [ ] Configure the appropriate regional privacy messages.
- [ ] Determine the applicable consent requirements for Brazil and other target markets.
- [ ] Implement the consent information update workflow.
- [ ] Implement required consent forms.
- [ ] Implement the privacy options entry point if required.
- [ ] Ensure advertising requests respect the resulting consent state.
- [ ] Test consent behavior with different regional and network scenarios.
- [ ] Verify that consent errors do not interrupt core application functionality.
- [ ] Update the public Privacy Policy and Google Play Data Safety declaration.

---

## 13. Document Status

This document defines the intended consent-management requirements for SlideTone.

Google AdMob has been selected, but the advertising SDK has not yet been integrated.

Google UMP remains under evaluation and must not be represented as an implemented component until its integration is confirmed.

All implementation requirements must be verified against the final SDK versions, configuration, and applicable privacy regulations before the document is approved.