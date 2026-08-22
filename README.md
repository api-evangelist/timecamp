# TimeCamp (timecamp)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

TimeCamp is a time tracking and timesheet platform used by teams to log billable hours, run attendance and time-off, approve timesheets, and measure productivity across projects. Its documented REST API - free on every plan, including the free tier - covers time entries, timers, tasks and projects, users and groups, attendance, approvals, tags, billing rates, expenses, and computer activity data.

**Access model:** The API is public and documented at [developer.timecamp.com](https://developer.timecamp.com/), but every call requires a TimeCamp account. Authentication uses a per-user API token (found at the bottom of Profile Settings in the app) sent as an `Authorization: Bearer <token>` header. TimeCamp states the API "is available to all subscription plans and is free of charge" - there is no separate API fee, and a free-forever plan means you can integrate without paying. Request limits are tied to your subscription plan; exceeding them returns HTTP 429. Feature coverage follows your plan: endpoints for attendance, approvals, billing rates, expenses, custom fields, and data export operate against features gated to the Starter, Premium, or Ultimate tiers.

**Surfaces:** The primary base URL is `https://app.timecamp.com/third_party/api` (the published OpenAPI also lists `https://v4.api.timecamp.com` as a production server). The developer portal is a Stoplight Elements site rendering TimeCamp's own OpenAPI 3.0 document, which is published at [developer.timecamp.com/reference/dist/api-prod.yaml](https://developer.timecamp.com/reference/dist/api-prod.yaml) and mirrored in this repository. It spans 122 paths across a stable v1 surface and a growing v3 surface. No public WebSocket API is documented.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/timecamp/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/timecamp/refs/heads/main/apis.yml)

## Tags

- Time Tracking
- Timesheets
- Productivity
- Attendance
- Project Management
- Billing

## Timestamps

- **Created:** 2026-07-11
- **Modified:** 2026-07-11

## APIs

### TimeCamp Time Entries API

Create, read, update, and delete time entries - the core timesheet records. Filter entries by date range, users, tasks, and tags, merge duplicate entries, track entry changes and deletions for sync, and pull logged time per week. A v3 surface adds permission-aware entry listing and time entry restrictions.

- **Human URL:** [https://developer.timecamp.com/#/operations/get--entries](https://developer.timecamp.com/#/operations/get--entries)
- **Base URL:** `https://app.timecamp.com/third_party/api`

#### Tags

- Time Tracking
- Time Entries
- Timesheets

#### Properties

- [Documentation](https://developer.timecamp.com/)
- [API Reference](https://developer.timecamp.com/#/operations/get--entries)
- [OpenAPI](openapi/timecamp-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/timecamp.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/timecamp.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### TimeCamp Timer API

Start, stop, and inspect running timers. A single `POST /timer` endpoint switches on an action parameter (start, stop, status), and `GET /timer_running` returns all currently running timers so integrations can mirror live tracking state.

- **Human URL:** [https://developer.timecamp.com/#/operations/post-timer](https://developer.timecamp.com/#/operations/post-timer)
- **Base URL:** `https://app.timecamp.com/third_party/api`

#### Tags

- Timer
- Time Tracking
- Real Time

#### Properties

- [API Reference](https://developer.timecamp.com/#/operations/post-timer)
- [OpenAPI](openapi/timecamp-openapi.yml)
- [Postman Collection](collections/timecamp.postman_collection.json)
- [Open Collection](collections/timecamp.opencollection.json)

### TimeCamp Tasks and Projects API

Manage the task and project tree that time is tracked against - create, update, and delete tasks, fetch task details, set task colors and tags. The v3 surface adds project listing and search, user assignment to projects, task duplication, archiving and restoring in batches, moving worklogs, and re-parenting tasks.

- **Human URL:** [https://developer.timecamp.com/#/operations/get--tasks](https://developer.timecamp.com/#/operations/get--tasks)
- **Base URL:** `https://app.timecamp.com/third_party/api`

#### Tags

- Tasks
- Projects
- Project Management

#### Properties

- [API Reference](https://developer.timecamp.com/#/operations/get--tasks)
- [OpenAPI](openapi/timecamp-openapi.yml)
- [Postman Collection](collections/timecamp.postman_collection.json)
- [Open Collection](collections/timecamp.opencollection.json)

### TimeCamp Users and Groups API

Administer the account - list all users, fetch your own profile (`/me`), invite and update users, manage per-user settings, and organize users into groups with group-level settings, schedulers, and roles and permissions.

- **Human URL:** [https://developer.timecamp.com/#/operations/get-users](https://developer.timecamp.com/#/operations/get-users)
- **Base URL:** `https://app.timecamp.com/third_party/api`

#### Tags

- Users
- Groups
- Administration

#### Properties

- [API Reference](https://developer.timecamp.com/#/operations/get-users)
- [OpenAPI](openapi/timecamp-openapi.yml)
- [Postman Collection](collections/timecamp.postman_collection.json)
- [Open Collection](collections/timecamp.opencollection.json)

### TimeCamp Attendance API

Attendance and time-off surface - pull attendance records per period, read and set per-user day types (working day, vacation, sick leave), submit attendance requests, and use the v3 endpoints for predefined holiday calendars per group and attendance calendar search.

- **Human URL:** [https://developer.timecamp.com/#/operations/get--attendance](https://developer.timecamp.com/#/operations/get--attendance)
- **Base URL:** `https://app.timecamp.com/third_party/api`

#### Tags

- Attendance
- Time Off
- Leave Management

#### Properties

- [API Reference](https://developer.timecamp.com/#/operations/get--attendance)
- [OpenAPI](openapi/timecamp-openapi.yml)
- [Postman Collection](collections/timecamp.postman_collection.json)
- [Open Collection](collections/timecamp.opencollection.json)

### TimeCamp Timesheet Approvals API

Timesheet approval workflow - fetch and create approvals for user timesheet periods, list users subject to approval, and drive the v3 flow with approval listing, status changes (single and bulk), approval activity history, messages, and reminder sending.

- **Human URL:** [https://developer.timecamp.com/#/operations/get--approval](https://developer.timecamp.com/#/operations/get--approval)
- **Base URL:** `https://app.timecamp.com/third_party/api`

#### Tags

- Approvals
- Timesheets
- Workflow

#### Properties

- [API Reference](https://developer.timecamp.com/#/operations/get--approval)
- [OpenAPI](openapi/timecamp-openapi.yml)
- [Postman Collection](collections/timecamp.postman_collection.json)
- [Open Collection](collections/timecamp.opencollection.json)

### TimeCamp Computer Activities API

Read the desktop-agent productivity data - application and website usage captured by the TimeCamp tracker - via `GET /activity`, plus v3 endpoints for sites-and-apps activity logs, activity categories, and per-group productivity classification of applications.

- **Human URL:** [https://developer.timecamp.com/#/operations/get--activity](https://developer.timecamp.com/#/operations/get--activity)
- **Base URL:** `https://app.timecamp.com/third_party/api`

#### Tags

- Productivity
- Activity Tracking
- Monitoring

#### Properties

- [API Reference](https://developer.timecamp.com/#/operations/get--activity)
- [OpenAPI](openapi/timecamp-openapi.yml)
- [Postman Collection](collections/timecamp.postman_collection.json)
- [Open Collection](collections/timecamp.opencollection.json)

### TimeCamp Tags API

Manage tag lists and tags used to slice time entries for reporting - create and update tag lists, add tags, scope tags to groups, and attach or remove tags on individual time entries and tasks.

- **Human URL:** [https://developer.timecamp.com/#/operations/get--tag_list-](https://developer.timecamp.com/#/operations/get--tag_list-)
- **Base URL:** `https://app.timecamp.com/third_party/api`

#### Tags

- Tags
- Metadata
- Time Entries

#### Properties

- [API Reference](https://developer.timecamp.com/#/operations/get--tag_list-)
- [OpenAPI](openapi/timecamp-openapi.yml)
- [Postman Collection](collections/timecamp.postman_collection.json)
- [Open Collection](collections/timecamp.opencollection.json)

### TimeCamp Billing Rates and Expenses API

Monetize tracked time - get and set billing rates per task, per user, per task-user pair, and per group, and manage expenses through the v3 endpoints including expense categories, attachments, and assigning expenses to invoices.

- **Human URL:** [https://developer.timecamp.com/#/operations/get-task-task_id-rate](https://developer.timecamp.com/#/operations/get-task-task_id-rate)
- **Base URL:** `https://app.timecamp.com/third_party/api`

#### Tags

- Billing
- Rates
- Expenses
- Invoicing

#### Properties

- [API Reference](https://developer.timecamp.com/#/operations/get-task-task_id-rate)
- [OpenAPI](openapi/timecamp-openapi.yml)
- [Postman Collection](collections/timecamp.postman_collection.json)
- [Open Collection](collections/timecamp.opencollection.json)

### TimeCamp Data Export API

Bulk reporting surface on the v3 API - request dataset exports, poll export status, check dataset availability, and download results, plus custom field templates and values that enrich exported time and project data.

- **Human URL:** [https://developer.timecamp.com/#/operations/get-data-export-exports](https://developer.timecamp.com/#/operations/get-data-export-exports)
- **Base URL:** `https://app.timecamp.com/third_party/api`

#### Tags

- Data Export
- Reporting
- Custom Fields

#### Properties

- [API Reference](https://developer.timecamp.com/#/operations/get-data-export-exports)
- [OpenAPI](openapi/timecamp-openapi.yml)
- [Postman Collection](collections/timecamp.postman_collection.json)
- [Open Collection](collections/timecamp.opencollection.json)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/timecamp)
- [Website](https://www.timecamp.com)
- [Documentation](https://developer.timecamp.com/)
- [Support](https://help.timecamp.com/help/api)
- [Pricing](https://www.timecamp.com/pricing/)
- [Blog](https://www.timecamp.com/blog/)
- [Plans](plans/timecamp-plans-pricing.yml)
- [Rate Limits](rate-limits/timecamp-rate-limits.yml)
- [Fin Ops](finops/timecamp-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
