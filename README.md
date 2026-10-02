# Welder: Social Media Manager

## You create. Your AI gets it out there.

Turn your AI assistant into your social media manager. Post the video you just made, schedule tomorrow's carousel and find what your audience responds to — all from the conversation you're already having.

### One message. Your accounts.

Ask your assistant to post a Reel, upload a Short or share your photos. Welder connects it to your TikTok, Instagram, YouTube, Threads, Bluesky and X accounts. Review the content and let your assistant handle the steps.

### Get ahead of your next post

Build a content plan with your assistant, then schedule the posts you approve up to 30 days ahead. Keep creating while Welder gets each post out at its scheduled time. Stop a pending post when plans change.

### Make more of what works

Ask which posts people responded to and what to try next. Your assistant can read available post metrics, compare measured results and turn them into your next creative brief. Read comments and prepare thoughtful replies on supported networks.

### Keep your content moving

Creators can share a finished video without switching between upload screens. Small businesses can plan a week of posts from one conversation. Social media managers can publish to the right profiles and check each result. Builders can connect an existing content workflow to their audience.

Welder provides the connection, posting, scheduling and account data. Your assistant helps prepare the content. Recurring agent tasks use your host's scheduling feature when supported and requested; Welder schedules individual posts rather than agent runs.

## Start with a goal

- “Post this video to my TikTok and Instagram with the caption we just approved.”
- “Plan next week's content for my coffee shop. Show me the posts before scheduling them.”
- “Which of my posts got the best response this month? Give me three ideas to test.”
- “Show the comments on my latest video and draft replies in my voice.”
- “Cancel tomorrow's scheduled post; the offer has changed.”

## Connect Welder

Install the plugin in your supported assistant, sign in to your existing [Welder](https://weldergtm.com) account and connect your social accounts. Publishing requires the appropriate account entitlement. Provider sign-in happens on the network's own website. You do not share social passwords with your assistant.

Chat apps provide an upload link for files on your device. Coding apps can upload files directly. Posts have one caption each; different captions for different networks are separate posts. TikTok and YouTube visibility defaults to public when the account allows it. Your assistant can use the options you approve.

Read access supports context, account lists and stored performance reports. Uploading, connecting accounts, posting, canceling and deleting require publishing access. Waiting for upload links, refreshing post metrics and reading comments also require publishing access because they may update state or consume account usage. X posting and comment reads require the appropriate X entitlement. Account and format support depend on each network's permissions. Threads is currently available to approved app testers. Some analytics and comment permissions remain unavailable; Welder identifies missing data rather than reporting it as zero. Live-post deletion is supported only on X and Bluesky with Welder's current permissions.

## Claude Code

```text
/plugin marketplace add smvls/welder-plugins
/plugin install welder-social-manager@welder-plugins
```

The Claude Directory listing is available after Anthropic review. Direct installation from this repository is a separate distribution path.

## ChatGPT and Codex

The root portable manifest and remote connection configuration package the same five workflows for supported hosts. OpenAI Directory availability follows OpenAI review. The package also includes Claude-compatible manifests.

For direct Git marketplace installation in Codex CLI:

```bash
codex plugin marketplace add smvls/welder-plugins
codex plugin add welder-social-manager@welder-plugins
```

Sign in to Welder through the host's OAuth connection flow. Direct Git installation is available separately from the reviewed OpenAI Directory listing.

For a direct remote connection, use [Welder's MCP endpoint](https://weldergtm.com/mcp) and the assistant's sign-in flow. Per-assistant setup guides are in the [Welder help center](https://weldergtm.com/docs).

## What the plugin sends and runs

This package contains readable instructions, connection metadata and brand images. It installs no executable server, lifecycle hooks or background process. On a tool call, your host sends the requested content, media references, account selection and options to Welder at `weldergtm.com`. Welder stores and processes them through its service, then sends an approved post to the selected connected social platforms through their APIs. Direct uploads go to Welder's Supabase storage through a short-lived destination returned by Welder. Welder may fetch a public HTTPS media URL when you request an import. Credentials and media upload destinations are never bundled in this repository.

Original media is normally kept for seven days; a scheduled post keeps it until seven days after its scheduled time. Post history retains the caption, metadata and one small cover image while the workspace exists. Available metrics and comments come from connected networks; their privacy policies also apply. Your assistant can use them to prepare recommendations, without guaranteed reach or growth.

[Support](https://weldergtm.com/support) · [Help](https://weldergtm.com/docs) · [Privacy](https://weldergtm.com/privacy) · [Terms](https://weldergtm.com/terms) · [Data deletion](https://weldergtm.com/data-deletion)

The package instructions and configuration are MIT licensed. Welder's name and visual identity remain the property of their owner. The hosted service and private server implementation are not distributed by this package.
