---
title: Changelog
---

# Changelog

This changelog was assembled from the repository's git history. The project does not currently use annotated release tags, so entries below are grouped by date-based milestones and major change windows rather than formal versions.

## 2026-08-12

### Changed
- Updated community calendar event forms to use the viewer's local timezone for start and end time entry.
- Improved Neon sync production diagnostics by logging organization id and submitted search fields when Neon rejects a search request.

### Fixed
- Fixed recurring event exception writes so single-occurrence updates and cancellations do not depend on a missing production `ON CONFLICT` constraint.
- Added a database repair SQL script to deduplicate recurring event exceptions and restore the intended unique index.
- Fixed recurring event weekday controls to start with Sunday.
- Fixed calendar event list and detail views so event times display in the viewer's local timezone instead of the event author's timezone.
- Fixed a reported single-occurrence recurring event update case where the event could save successfully but still show an "Error updating event" toast.
- Fixed Neon account detail throttling failures by adding request throttling and retry handling for 429 responses.

## 2026-08-10

### Added
- Added JoynAMS user synchronization support.

## 2026-07-29

### Changed
- Upgraded Next.js and hardened the SSO login flow.

## 2026-07-27

### Added
- Added Degnon IDP SSO authentication.

## 2026-07-24

### Added
- Added a community-wide comment email notification toggle.
- Added Neon account exclusion handling for user sync automation criteria.

## 2026-07-08

### Changed
- Updated Neon expired-member sync to use the membership grace cutoff.

## 2026-07-07

### Added
- Added email delivery logging.

### Changed
- Routed notification emails through SES with failure logging.

## 2026-06-15

### Fixed
- Fixed MemberClicks account sync to honor organization search criteria during synchronization.

## 2026-06-03 to 2026-06-04

### Changed
- Updated calendar event email templates and removed duplicated date/time copy from those messages.
- Updated backend notification settings.

### Fixed
- Fixed scheduled posts appearing in digest activity.
- Fixed a calendar hydration issue.

## 2026-06-02

### Changed
- Reconciled digest subscriptions from organization defaults.

### Fixed
- Fixed notification recipient and digest subscription edge cases.

## 2026-05-15

### Added
- Added timezone information to event forms.

## 2026-05-06

### Added
- Added per-community digest subscriptions.
- Added community guidelines agreement requirements for posts and comments.

## 2026-05-01

### Changed
- Updated user sync and community member search behavior.

## 2026-04-30

### Fixed
- Fixed rich text editor modal popup behavior.

## 2026-04-27

### Added
- Added recurring community events, including recurrence rules, occurrence editing, and recurrence-aware event display.
- Added user salutation synchronization and display support.

### Fixed
- Fixed calendar event dialog overflow.

## 2026-04-17

### Added
- Added Member Intel activity synchronization.

## 2026-04-10

### Changed
- Replaced Quill with Jodit for rich text editing while preserving legacy content styling.
- Removed Quill packages and retained legacy content styles.

## 2026-04-08

### Fixed
- Fixed unsubscribe redirects to preserve the tenant host.
- Fixed unsubscribe route behavior so user subscription updates are applied correctly.

## 2026-03-30

### Added
- Added unit test coverage for Neon sync regression cases.

### Changed
- Unified Neon sync field updates and preserved custom roles during synchronization.

### Fixed
- Fixed Neon custom-field fallback behavior so existing custom fields and roles are preserved when upstream field definitions are unavailable.

## 2026-03-27

### Added
- Added private message updates, including private message email notifications.
- Added a scheduled post view for community admins.
- Added profile image support to user information returned by the app.

### Changed
- Updated email notification rules to respect admin subscription preferences.

### Fixed
- Fixed worker relative path errors.
- Fixed private message form type-only import issues.

## 2026-03-19

### Fixed
- Fixed email brand logo sizing and null alt text handling for legacy email clients.

## 2026-03-16

### Changed
- Updated the MemberClicks background sync worker.
- Applied linting fixes.

## 2026-03-13

### Fixed
- Fixed additional calendar event errors after the initial rollout.

## 2026-03-12

### Added
- Added a community calendar view inside each community.
- Added community event creation, editing, and deletion flows.
- Added calendar event API routes and supporting data model updates.
- Added event email notifications for published and updated community events.
- Added `.ics` calendar file generation and download support for community events.
- Added a table of contents to digest emails.
- Added an integration data section.

### Changed
- Aligned Neon sync flows and refresh behavior.
- Renamed digest-related folders as part of the email template updates.

### Fixed
- Fixed community sync refresh issues.
- Fixed community search filter behavior.
- Fixed calendar event errors, including query-related failures immediately after the initial rollout.

## 2026-03-02 to 2026-03-04

### Changed
- Moved the digest worker back into the application runtime.
- Tuned worker heartbeat logging to reduce noisy error reporting.
- Updated configuration for Degnon API calls.
- Rotated AWS mail token and related key configuration.

### Fixed
- Restored the digest worker after a temporary removal.
- Added guards and streaming support around digest worker execution to improve reliability.

## 2026-02-23 to 2026-02-28

### Added
- Added hardening to the digest email worker.
- Added process diagnostics, heartbeat reporting, and task-failure admin notifications for worker operations.

### Changed
- Updated worker concurrency and build/postinstall behavior for worker deployment.
- Removed committed worker build artifacts and ignored generated `dist-worker` output.

### Fixed
- Fixed comment and post pagination issues.
- Fixed image drag-and-drop behavior in the rich text editor.
- Fixed an infinite failed-worker loop.
- Fixed a rich text editor regression.

## 2026-02-03 to 2026-02-11

### Added
- Added post scheduling.
- Added Quill content block styling support for comments and email rendering.

### Changed
- Updated MC frontend sync behavior, including array-field handling and rate-limit waiting.
- Updated authentication and subscription description flows.
- Updated notifications so subscribed users receive post and comment emails more consistently.
- Improved text editor behavior and scrolling.

### Fixed
- Fixed comment email notification handling.
- Removed verbose sync logging after troubleshooting.

## 2026-01-09 to 2026-01-30

### Added
- Added multi-file uploads for posts.
- Added post titles to email subject lines.
- Added private-message hardening and comment block styling updates.
- Added Neon account ID support in custom field mappings.

### Changed
- Moved account syncs into an external worker.
- Moved digest sending into background processing.
- Updated email templates and a tenant redirect.
- Removed image insertion from the text editor menu as part of UX cleanup.

### Fixed
- Investigated and corrected subscription inversion issues during Neon sync.
- Added logging around sync processes to troubleshoot integration problems.

## 2025-10-23 to 2025-12-11

### Added
- Added user avatar editing.
- Added an admin link for EULA maintenance.
- Added Google Tag Manager.

### Changed
- Performed incremental Next.js 16 migration work.
- Continued Tailwind and shadcn UI refactors across the app.
- Restored HTML parsing support after a temporary removal.

### Fixed
- Fixed form type errors introduced during upload logic changes.
- Improved security and community/post count behavior.
- Prepared the app for alpha testing and production builds.

## 2025-01-29 to 2025-07-17

### Added
- Added a user guide link in navigation.
- Added member directory export capability.
- Added user AMS sync.

### Changed
- Updated cookie management for subscription edits.
- Soft-deprecated the `sync-frontend` API flow.
- Updated member counts to exclude admins.

### Fixed
- Sanitized HTML comments to improve safety.
- Improved email query handling.

## 2024-02-20 to 2024-12-16

### Added
- Added MC SSO implementation.
- Added tenant styling and search improvements.
- Added member directory export support.

### Changed
- Added MUI boilerplate during the UI foundation phase.

### Fixed
- Included assorted bug fixes during early productionization.

## 2023-10-03 to 2023-12-13

### Added
- Initial Next.js application scaffold.
- Basic CRUD flows.
- User authentication.
- File uploads, role identification, shared hooks, user management, and search.
- Tenant styling, search updates, breadcrumbs, TinyMCE support, and info-page image uploads.
- Vercel configuration for deployment.

### Changed
- Refactored the initial application structure after project bootstrap.

### Fixed
- Included incremental fixes and polish during the first implementation cycle.
