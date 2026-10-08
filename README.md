# TikTok MCP

This public listing provides connection metadata and client examples for the hosted SocialDataX TikTok MCP service. The implementation is privately hosted; this directory contains public connection materials only.

## Service

- Hosted MCP endpoint: `https://mcp.socialdatax.com/tiktok/mcp`
- Hosted transport: `streamable-http`
- Authentication: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Product: `SocialDataX` / `社媒数据助手`
- Website and API Key access: <https://socialdatax.com/ai?from=github>
- Registry name: `com.52choujiang/tiktok-insights`
- Future registry name: `com.socialdatax/tiktok-insights`
- Current public capability version: `0.1.7` (15 tools; hosted server card and authenticated tools/list verified on 2026-10-08)
- Official Registry latest verified version: `0.1.5`. Publication of `0.1.7` returned a gateway timeout on 2026-10-08; confirmation is pending.

## Scope

Use this service for public TikTok user search, post search, video or image details, first-level comments, comment replies, creator profiles, creator posts, and video speech-to-text transcript. It does not provide account login, posting, editing, liking, commenting, following, or other account actions.

## Tools

| Tool | Purpose |
| --- | --- |
| `socialdatax_get_points_balance` | Query the current API Key account's SocialDataX points balance / 积分余额、剩余积分或点数. |
| `tiktok_search_suggestions` | Get search-box suggestions for a keyword; reuse `text` in post search. No pagination. |
| `tiktok_search_users` | Search public TikTok users with a non-empty keyword such as `teamtrump` or `campinglife`; reuse a non-empty result `items[*].tiktok_id` with the user tools and continue with the opaque `page_token`. |
| `tiktok_search_posts` | Search public video and image posts; use when a search term is available, and continue with `page_token`. |
| `tiktok_get_post_detail_by_url` | Read video or image details from a post URL. |
| `tiktok_get_post_comments_by_post_id` | Read first-level comments from a post ID. |
| `tiktok_get_post_comments_by_url` | Read first-level comments from a post URL. |
| `tiktok_get_post_comment_replies` | Read replies from a post ID and first-level comment ID. |
| `tiktok_get_user_info_by_tiktok_id` | Read creator info from a TikTok ID. |
| `tiktok_get_user_info_by_profile_url` | Read creator info from a profile URL. |
| `tiktok_get_user_posts_by_tiktok_id` | Read creator posts from a TikTok ID. |
| `tiktok_get_user_posts_by_profile_url` | Read creator posts from a profile URL. |
| `tiktok_submit_video_speech_text_by_url` | Submit video speech-to-text transcript work from a TikTok video URL. |
| `tiktok_submit_video_speech_text_by_aweme_id` | Submit video speech-to-text transcript work from a TikTok video ID. |
| `tiktok_get_video_speech_text_job` | Check a TikTok transcript job by `job_id`. |

When a post URL, post ID, TikTok ID, or profile URL is already available, use the corresponding detail, comment, creator, or creator-post tool instead of searching again.

## Quick Start

Use the hosted endpoint directly when the client supports authenticated `streamable-http`:

```json
{
  "mcpServers": {
    "socialdatax-tiktok": {
      "type": "streamable_http",
      "url": "https://mcp.socialdatax.com/tiktok/mcp",
      "headers": {"Authorization": "Bearer <SOCIALDATAX_API_KEY>"}
    }
  }
}
```

For command/stdio-only clients, use `npx -y mcp-remote https://mcp.socialdatax.com/tiktok/mcp --header "Authorization: Bearer <SOCIALDATAX_API_KEY>"`. See the files in [examples](examples/).

Request or manage API access at <https://socialdatax.com/ai?from=github>. Never commit a real API Key.

User search and profile responses omit unknown verification, privacy and account counts; known `false` and `0` values are preserved. These fields are optional; callers must not interpret omission as a negative or zero.
