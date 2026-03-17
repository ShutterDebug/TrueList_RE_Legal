# Privacy Policy for TrueList RE

*Last updated: March 2026*

## Overview

TrueList RE is a Chrome extension that cross-references real estate listings on Redfin, Zillow, and Realtor.com against official county assessor public records. This policy describes what data the extension accesses and how it is handled.

---

## Data We Access

TrueList RE accesses the following data solely to provide its core functionality:

- **Page content on supported listing sites** (Redfin, Zillow, Realtor.com): The extension reads property details from the current listing page (address, square footage, price, etc.) to display alongside assessor records.
- **Property address**: Used to query public government geocoding and assessor databases to retrieve official county records for the property being viewed.
- **Aggregated property data for AI Summary**: When the AI Summary feature runs, aggregated property details (address, square footage, beds/baths, assessor data, price estimates, and location signals) are sent to our backend service to generate a plain-language summary. No personal user data (such as identity or account information) is included.

---

## Product Analytics Telemetry

TrueList RE collects anonymous product analytics events to understand how the extension is used and to monitor its health.

**What is collected:**
- Extension open events (popup or side panel)
- UI interactions such as switching modes, expanding or collapsing sections, and opening the feedback panel
- Analysis lifecycle events: when an analysis starts, completes, fails, or is manually refreshed
- AI summary outcomes: which prompt path was used, model metadata, and whether a cached result was served
- Feedback submission events (type only — not the content of feedback)
- Which county was looked up and which data sources succeeded or failed

**What is never collected:**
- Your identity, account information, or any personal details
- Property addresses or listing URLs in analytics events
- Your browsing history

Analytics events are sent to PostHog using an anonymous, randomly-generated installation ID that cannot be linked to your identity. Selected events are also stored in our backend database (Cloudflare D1) for operational analysis. Analytics events are retained for 730 days.

This data is never sold or used for advertising, profiling, or any purpose beyond operating and improving the extension.

---

## Diagnostic Telemetry

When the extension encounters an error or a user submits feedback, TrueList RE may capture a diagnostic snapshot to help investigate the issue. This can include property-level data such as the listing URL, address, data source results, AI summary content, and any error details from the failed lookup.

This data is only captured when an error occurs or when a user explicitly submits feedback.

Diagnostic snapshots are stored in Cloudflare D1 and retained for 180 days. They are used solely to reproduce and fix issues, and are never sold, used for advertising or profiling, or used for any purpose other than improving the extension.

---

## User Feedback

When you voluntarily submit feedback through the extension, TrueList RE collects:

- The feedback text you provide
- The type and section of feedback
- Your email address, if you choose to provide it for follow-up
- A session identifier associated with the analysis you were viewing, to help investigate the issue

Feedback records are stored in Cloudflare D1 and retained indefinitely to support issue triage and product improvement. Your email address, if provided, is used only to follow up on the specific issue you reported and is never sold or used for any other purpose. Feedback may be analyzed to improve product features, quality, and user experience.

---

## Anonymized Analysis Data

We may retain de-identified analysis data, such as AI-generated summaries and derived signals, to improve product quality and system performance. This data does not include property addresses, listing URLs, or any personal user information.

We may also analyze anonymized AI outputs and associated feedback to improve model quality and reliability.

---

## Data We Do NOT Collect

- TrueList RE does not collect personal information about users, except for an email address you voluntarily provide when submitting feedback (see User Feedback above).
- No browsing history outside supported listing pages is collected or stored.
- TrueList RE does not track users across sites. No advertising, profiling, or cross-site tracking of any kind is used.
- Property addresses and listing URLs are never included in routine analytics events.

---

## Third-Party Services

To retrieve public property data and generate AI summaries, the extension communicates with the following services:

**Public government services:**
- **Nominatim / OpenStreetMap** — for geocoding property addresses ([openstreetmap.org/copyright](https://www.openstreetmap.org/copyright))
- **King County GIS / eReal Property** — official King County assessor records (kingcounty.gov)
- **Snohomish, Pierce, and Kitsap County government portals** — official assessor records (respective .gov domains)
- **Overpass API** — queries nearby points of interest and road proximity using the property's coordinates (overpass-api.de)

**Backend and AI services:**
- **Cloudflare Workers** — our AI Summary backend runs on Cloudflare's edge infrastructure. Aggregated property data is sent here to generate summaries.
- **Cloudflare D1** — our backend database, hosted on Cloudflare, stores analytics events, diagnostic snapshots, and user feedback (see sections above).
- **AI models (e.g. Anthropic, OpenAI)** — our backend forwards aggregated property data to third-party AI providers to generate the plain-language summary. No personal user data (such as identity or account information) is included in these requests.
- **PostHog** — receives anonymous product analytics events (see Product Analytics Telemetry above). PostHog does not receive diagnostic snapshots or feedback content.

Please refer to the respective privacy policies of these services for details on how they handle requests.

---

## Data Retention

| Data | Retention |
|---|---|
| Product analytics events | 730 days |
| Diagnostic snapshots | 180 days |
| User feedback | Indefinite |
| Local property and AI summary cache | Up to 30 minutes (on-device only) |

---

## Local Storage

The extension uses Chrome's local storage API to save:
- **User preferences** (such as which sections are collapsed or expanded)
- **Property data cache** — listing and assessor data for the current property, cached for up to 30 minutes to avoid redundant lookups
- **AI Summary cache** — generated summaries cached locally for up to 30 minutes
- **Anonymous installation ID** — a randomly-generated ID used to deduplicate analytics events sent to PostHog; not linked to your identity

All cached data is stored only on your device and is never shared.

---

## Changes to This Policy

This policy may be updated as new counties, features, or data practices are added. The "last updated" date at the top reflects the most recent revision.

---

## Contact

For questions or concerns, please file an issue on the [TrueList RE GitHub repository](https://github.com/ShutterDebug/TrueList_RE_Legal).
