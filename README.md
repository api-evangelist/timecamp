# TimeCamp (timecamp)

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
