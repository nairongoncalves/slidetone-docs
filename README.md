# SlideTone - Privacy Documentation

Source of truth for how **SlideTone** accesses, processes, stores, and discloses information.

**Application:** SlideTone - precision trombone tuner  
**Developer:** Techminds  
**Privacy contact:** nairongoncalves@gmail.com  
**Baseline:** 2026-11-03

SlideTone is local-first. Tuning runs on the device, profiles and settings stay on the device, and the app does not require an account or cloud sync. The only planned off-device processing is advertising through Google services. These documents describe that boundary and the disclosures required before release.

Implementation and store declarations must follow this tree. When the application changes how data is processed, update the affected documents in the same change.

---

## Map

| Document                                                                     | Audience              | Owns                                                     |
|------------------------------------------------------------------------------|-----------------------|----------------------------------------------------------|
| [Privacy Policy (en-US)](privacy/privacy-policy/en-US.md)                    | Users                 | Public explanation of practices, rights, and contact     |
| [Política de Privacidade (pt-BR)](privacy/privacy-policy/pt-BR.md)           | Users                 | Portuguese public policy; must stay equivalent to en-US  |
| [Data Inventory](privacy/data-safety/data-inventory.md)                      | Engineering           | What the app and its SDKs access, store, and transmit    |
| [Google Play Data Safety](privacy/data-safety/google-play-data-safety.md)    | Release               | Internal worksheet for the Play Console Data Safety form |
| [Third-Party Services](privacy/third-party-services/third-party-services.md) | Engineering / release | Each external service, its purpose, and its data role    |
| [Consent Management](privacy/consent/consent-management.md)                  | Engineering           | Advertising consent requirements and expected states     |
| [User Privacy Rights](privacy/consent/user-rights.md)                        | Engineering / support | Rights and how privacy requests are handled              |

The two privacy-policy files are the only documents intended for publication. The rest are internal references used to keep the public policy and the store declaration accurate.

---

## Authority

```text
Data Inventory            →  what is actually processed
        ↓
Third-Party Services      →  who else processes it, and why
        ↓
Consent Management        →  how advertising choices are obtained and honored
User Privacy Rights       →  how requests about that processing are handled
        ↓
Privacy Policy (en-US)    →  public statement; pt-BR must match
Google Play Data Safety   →  store declaration; must match the public policy
```

When documents disagree, use this order:

| Concern                                                    | Wins                                                                                                                         |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------|
| Whether a category is accessed, stored, or sent off-device | [Data Inventory](privacy/data-safety/data-inventory.md), checked against the running app                                     |
| Which SDK processes a category, and for what purpose       | [Third-Party Services](privacy/third-party-services/third-party-services.md), checked against the integrated SDK version     |
| Consent flow, regional rules, and error behavior           | [Consent Management](privacy/consent/consent-management.md)                                                                  |
| How a user request is answered                             | [User Privacy Rights](privacy/consent/user-rights.md)                                                                        |
| Wording shown to users                                     | [Privacy Policy (en-US)](privacy/privacy-policy/en-US.md); [pt-BR](privacy/privacy-policy/pt-BR.md) must say the same thing  |
| Answers submitted in Play Console                          | [Google Play Data Safety](privacy/data-safety/google-play-data-safety.md), after it matches the policy and the shipped build |

A document header marked Final does not override a section that still lists open verification. Advertising disclosures stay provisional until the SDK integration and consent configuration are confirmed.

---

## Current baseline

These facts are consistent across the tree and should not be contradicted in copy or in the store form:

- No user account, registration, or cloud sync.
- Instrument profiles and app settings are stored only on the device.
- Microphone audio is analyzed in real time for pitch. It is not recorded, retained, or uploaded.
- No first-party analytics, crash reporting, or telemetry.
- Core tuning works offline. A network connection is needed only for advertising.
- **Google AdMob** is the selected ad provider. SDK integration is still pending.
- **Google User Messaging Platform (UMP)** is under evaluation and is not an implemented component.
- Approved ad placements, once integrated: one banner at the bottom of the tuner, banners between instrument-catalog cards, and at most one banner after instrument-details content. No ads in onboarding, profiles, settings, About, or the menu. No full-screen or forced-video ads.

Data expected to need a Play Data Safety declaration comes from the Google Mobile Ads SDK (approximate location derived from IP, app interactions, diagnostics, and device or other IDs). On-device profiles, settings, and microphone audio are not expected to be declared as collected, provided they never leave the device.

---

## How to start

| Audience | Start here |
| -------- | ---------- |
| Publishing the policy | [en-US](privacy/privacy-policy/en-US.md) and [pt-BR](privacy/privacy-policy/pt-BR.md). Confirm both describe the same practices, then publish them at the Privacy Policy URL used in the stores. |
| Filling in Play Console | [Google Play Data Safety](privacy/data-safety/google-play-data-safety.md), using the [inventory](privacy/data-safety/data-inventory.md) and [third-party services](privacy/third-party-services/third-party-services.md) as evidence. Complete the form only after the production SDK version is known. |
| Integrating ads | [Third-Party Services](privacy/third-party-services/third-party-services.md) for placements and data categories, then [Consent Management](privacy/consent/consent-management.md) for the request sequence. Do not request ads before the required consent update finishes, and do not treat a failed consent load as consent. |
| Handling a privacy email | [User Privacy Rights](privacy/consent/user-rights.md). Answer what SlideTone itself processes. Point the requester to Google when the data is held by AdMob. |

---

## Before release

Do not treat the advertising sections as closed until these are done:

1. Integrate the Google Mobile Ads SDK and record the exact version.
2. Decide whether UMP is included. If it is, configure regional messages and a privacy-options entry point.
3. Re-check SDK data categories against Google's current Play data disclosure.
4. Align the [inventory](privacy/data-safety/data-inventory.md), [Data Safety worksheet](privacy/data-safety/google-play-data-safety.md), and both privacy-policy languages with that result.
5. Confirm the target age group and any Families or children's-privacy limits before ads ship.
6. Submit the Play Console form only after it matches the shipped build and the public policy URL.

Review this tree again whenever a permission, SDK, ad placement, storage path, or regional requirement changes.