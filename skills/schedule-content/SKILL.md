---
name: schedule-content
description: Build a reviewable social content schedule, schedule approved posts through Welder, and cancel pending posts without duplicating content.
---

Call `get_context`, `list_accounts` and `list_posts` before changing a schedule. Reuse the user's existing uploads with `list_media` when appropriate. A planning request produces a plan; it does not authorize posting. Resolve audience, selected profiles, content and cadence only where the user has left them unspecified.

For each approved post, resolve the intended local time and timezone into an ISO-8601 timestamp with an offset. Use the user's timezone, including daylight saving on the scheduled date. Clarify genuinely ambiguous phrases such as 'tomorrow at 8' when the timezone or morning/evening is unknown. Welder accepts individual posts up to 30 days ahead; a repeated calendar beyond that needs the host's scheduling capability, not an invented recurrence field.

Review existing scheduled posts to avoid duplicates. Follow the publish-content workflow for media, target selection, disclosures and validation. Pass `schedule_at` in the approved `create_post` payload and assign a stable idempotency key per intended post. Separate network-specific captions into separate posts. If some items fail validation, explain which can be scheduled and which need correction rather than quietly changing the user's brief.

Confirm persistence with `get_post` or `list_posts`. Report each post's caption summary, selected accounts, local date/time/timezone, ID and actual state. A queued scheduled post is not live. Welder exposes schedules in post history; do not promise a calendar or a recurring scheduler that the product does not provide.

To stop a named pending post, identify its ID and use `cancel_post`. Cancellation affects only targets that have not started publishing. Check the result and explain any targets that are already publishing or published. Cancel does not delete a live copy. When rescheduling is requested, first confirm the old pending targets were canceled, then validate and create the replacement with a new intent key.

For requested recurring host tasks, preserve the user's exact accounts, cadence, authorization and content rules. Check fresh account/plan state on every run. Do not turn a recurring performance report into blanket permission to publish.
