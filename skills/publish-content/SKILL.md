---
name: publish-content
description: Publish user-approved videos, photos, carousels and text through Welder to connected social accounts, adapting each post to the selected networks.
---

Start with `get_context` and resolve the intended accounts with `list_accounts`. Use `get_capabilities` for format, duration, image count and text limits. Work with the user's supplied content or host-created assets; Welder does not generate media.

Obtain ready media IDs through the appropriate upload workflow described in the get-started skill. A local path, chat attachment or remote URL is not a media ID. If a finalized upload is pending, report that state and wait within the tool limits; do not recreate it repeatedly.

Prepare the exact caption, account IDs, media order and relevant options. One Welder post has one caption: different captions for different networks require separate posts with separate idempotency keys. Instagram Stories require `options.instagram.kind = 'story'`; one video otherwise becomes a Reel. YouTube requires video, TikTok supports video or photos, and text-only posts require a supported network. Do not promise every format on every network.

Before posting, make the intended caption, accounts, visibility and schedule clear. An explicit request to post those exact details provides authorization; clarify missing or conflicting details. Public is the default, including TikTok when the account allows it. TikTok and YouTube AI-generated disclosures default on; use accurate user-provided provenance for overrides. Do not remove required platform disclosures.

Call `validate_post` with the exact intended payload. Resolve blocking issues before calling `create_post`. Keep a stable, non-secret `idempotency_key` for the same publishing intent and reuse it after a timeout. If the payload changes, revalidate and use a new key. Never create a new intent to retry an ambiguous provider outcome.

Use `create_post`, then `get_post` to report each target's actual status. Queued, processing and scheduled are not published. A partial result may contain both successful and failed targets: report each separately, keep successful URLs and diagnose only the failed ones. A TikTok inbox draft is not a public post. If no verified public link is returned, say so; never build one from an upload or processing ID.

Report the account, status and available link without exposing signed storage URLs. When a result is ambiguous, ask the user to check the actual account before any new publication. Uploads normally expire after seven days; scheduled posts retain their originals through the scheduled time plus seven days.
