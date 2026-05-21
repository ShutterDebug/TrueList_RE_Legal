# Privacy Policy for TrueList RE

*Last updated: May 16, 2026*

## Overview

TrueList RE is a Chrome extension that cross-references real estate listings on Redfin, Zillow, and Realtor.com against official county assessor public records. This policy describes what data the extension accesses and how it is handled.

---

## Data We Access

TrueList RE accesses the following data solely to provide its core functionality:

- **Page content on supported listing sites** (Redfin, Zillow, Realtor.com): The extension reads property details from the current listing page (address, square footage, price, etc.) to display alongside assessor records.
- **Property address**: Used to query public government geocoding and assessor databases to retrieve official county records for the property being viewed.
- **Property data for AI Summary**: When the AI Summary feature runs, property details — including the address, square footage, beds/baths, assessor data, price estimates, and location signals — are sent to our backend to generate a plain-language summary and look up key property insights, such as nearby amenities and road exposure. This data is used only to produce the response and is not stored by us. No personal user information (such as your identity or account details) is included.

---

## Product Analytics Telemetry

TrueList RE collects anonymous product analytics events to understand how the extension is used and to monitor its health.

**What is collected:**
- Extension open events (popup or side panel)
- UI interactions such as switching modes, expanding or collapsing sections, and opening the feedback panel
- Analysis lifecycle events: when an analysis starts, completes, fails at any step, or is manually refreshed
- AI summary outcomes: which prompt path was used, model metadata, and whether a cached result was served
- Feedback submission events (type only — not the content of feedback)
- Which county was looked up and which data sources (including location data queries) succeeded or failed
- The listing page URL, when an error occurs, to help reproduce the issue
- Comparison signals between listing data and public records (for example, whether square footage or bedroom count is inconsistent across sources), stored as derived values without raw property values, addresses, or listing URLs
- An anonymized identifier for each property analyzed — a scrambled, non-reversible code derived from the county and address — used only to count how often a property is looked up

**What is never collected:**
- Your identity, account information, or any personal details
- Property addresses or listing URLs in routine analytics events (except the listing URL when an error occurs, as noted above)
- Your browsing history or activity outside supported listing pages
- Any information used for advertising, profiling, or cross-site tracking

Analytics events are sent to PostHog using an anonymous, randomly-generated installation ID that cannot be linked to your identity. The same ID is included in events stored in our backend database (Cloudflare D1) for operational analysis — for example, understanding per-installation error rates and feature usage. Analytics events are retained for 730 days.

---

## Diagnostic Telemetry

When the extension encounters an error or a user submits feedback, TrueList RE may capture a diagnostic snapshot, including property-level data such as the listing URL, address, data source results, AI summary content, and error details. This is used solely to help reproduce and fix the issue.

Diagnostic snapshots are stored in Cloudflare D1 and retained for 180 days.

---

## User Feedback

When you voluntarily submit feedback through the extension, TrueList RE collects:

- The feedback text you provide
- The type and section of feedback
- Your email address, if you choose to provide it for follow-up
- A session identifier associated with the analysis you were viewing, to help investigate the issue
- Your anonymous installation ID (see Local Storage below)

Feedback records are stored in Cloudflare D1 and retained indefinitely to support issue triage and product improvement.

**If you include your email**, we may use it to follow up on the issue you reported — we may also link it to recent errors or events from your installation to help diagnose it. It's never shared, sold, or used for ads or marketing.

---

## Anonymized Analysis Data

We may retain de-identified data — such as derived comparison signals and AI-generated summaries — to improve product quality and reliability. This data does not include property addresses, listing URLs, or any personal user information.

---

## Third-Party Services

To retrieve public property data and generate AI summaries, the extension communicates with the following services:

**Public government services:**
- **Nominatim / OpenStreetMap** — for geocoding property addresses ([openstreetmap.org/copyright](https://www.openstreetmap.org/copyright))
- **King County GIS / eReal Property** — official King County assessor records (kingcounty.gov)
- **Snohomish, Pierce, and Kitsap County government portals** — official assessor records (respective .gov domains)
- **Overpass API** — queries nearby points of interest and road proximity using the property's coordinates. Two mirrors are used: overpass-api.de and overpass.kumi.systems (operated by FOSSGIS e.V., the German OpenStreetMap association).

**Backend and AI services:**
- **Cloudflare Workers** — our backend receives property details, uses the address to look up nearby amenities and road exposure, and distills everything into de-identified property signals. These signals — not including the property address — are then forwarded to AI providers to generate the summary.
- **Cloudflare D1** — our backend database, hosted on Cloudflare, stores analytics events, diagnostic snapshots, and user feedback (see sections above).
- **AI models (e.g. Anthropic, OpenAI)** — receive de-identified property signals from our backend to generate the plain-language summary. No personal user information is included.
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
| Road and amenity context cache (per-coordinate) | Up to 7 days (on-device only) |

---

## Local Storage

The extension uses Chrome's local storage API to save:
- **User preferences** (such as which sections are collapsed or expanded)
- **Property data cache** — listing and assessor data for the current property, cached for up to 30 minutes to avoid redundant lookups
- **AI Summary cache** — generated summaries cached locally for up to 30 minutes
- **Anonymous installation ID** — a randomly-generated ID used to deduplicate analytics events sent to PostHog and included in backend telemetry for per-installation operational analysis; not linked to your identity

All cached data is stored only on your device and is never shared.

**Road and amenity context cache** — when road proximity and nearby amenity data is successfully retrieved for a property, the result is cached locally using the property's geocoordinates (rounded to approximately 11 meters) as a cache key. This cache has a 7-day TTL. The coordinates are derived from the public listing address you chose to view, are stored only on your device, and are never stored on our servers.

---

## Changes to This Policy

This policy may be updated as new counties, features, or data practices are added. The "last updated" date at the top reflects the most recent revision.

---

## Contact

For questions or concerns, please file an issue on the [TrueList RE GitHub repository](https://github.com/ShutterDebug/TrueList_RE_Legal).
