# TikTok MCP Directory Submission Checklist

## Metadata

- Registry name: `com.52choujiang/tiktok-insights`
- Future registry name: `com.socialdatax/tiktok-insights`
- Version: `0.1.7`
- Endpoint: `https://mcp.socialdatax.com/tiktok/mcp`
- Auth: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Website and API Key access: <https://socialdatax.com/ai?from=github>
- Transport: hosted `streamable-http`; command/stdio fallback uses `mcp-remote`
- License: MIT for public documentation and configuration examples only
- Product: `SocialDataX` / `社媒数据助手`
- 15 public tools are listed in `server-card.json`.

## Safety and publication checks

- No real API Key, private backend code, production configuration, internal sample, or account data is present.
- Hosted `0.1.7`, 15 tools and authenticated tools/list verified on 2026-10-08; version and endpoint match this public repository. Live user search returned 10 accounts and user profile lookup succeeded.
- The hosted card must expose `tiktok_search_posts`, `tiktok_get_post_detail_by_url`, `tiktok_get_post_comments_by_url`, and `tiktok_get_user_info_by_profile_url`.
- The hosted card exposes `tiktok_search_users`; its public response must use `tiktok_id` and exclude internal protocol identifiers.
- The hosted card must expose `tiktok_submit_video_speech_text_by_url`, `tiktok_submit_video_speech_text_by_aweme_id`, and `tiktok_get_video_speech_text_job`.
- This listing advertises only the current public allowlist; internal or draft tools are excluded.
- Search and list calls pass the opaque `page_token` returned by the service for continuation.
- `examples/codex_config.toml` uses `bearer_token_env_var = "SOCIALDATAX_API_KEY"`.
- `examples/cursor_mcp.json` uses the remote URL and `${env:SOCIALDATAX_API_KEY}`.
- `mcp.json` and `examples/claude_desktop_config.json` are explicit `mcp-remote` fallbacks.
- Validate JSON and the official Registry file before submission; do not treat a hosted server card as a Registry publication.

## Required files

`README.md`, `LICENSE`, `server-card.json`, `mcp.json`, `glama.json`, all files under `examples/`, and `assets/logo.png`.

- Version `0.1.5` added `tiktok_search_suggestions(keyword)`, returning `items[].text` without pagination.
- `tiktok_search_users(keyword, page_token)` returns public user profiles without internal protocol identifiers.
- Official Registry `0.1.7` is published and verified active/latest on 2026-10-08.

User search and profile responses omit unknown verification, privacy and account counts; known `false` and `0` values are preserved. These fields are optional; callers must not interpret omission as a negative or zero.
