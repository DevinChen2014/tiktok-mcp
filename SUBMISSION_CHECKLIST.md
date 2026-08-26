# TikTok MCP Directory Submission Checklist

## Metadata

- Registry name: `com.52choujiang/tiktok-insights`
- Future registry name: `com.socialdatax/tiktok-insights`
- Version: `0.1.4`
- Endpoint: `https://mcp.socialdatax.com/tiktok/mcp`
- Auth: `Authorization: Bearer <SOCIALDATAX_API_KEY>`
- Website and API Key access: <https://socialdatax.com/ai?from=github>
- Transport: hosted `streamable-http`; command/stdio fallback uses `mcp-remote`
- License: MIT for public documentation and configuration examples only
- Product: `SocialDataX` / `社媒数据助手`
- current 13 public tools are listed in `server-card.json`.

## Safety and publication checks

- No real API Key, private backend code, production configuration, internal sample, or account data is present.
- Before deployment, `server-card.json` and `registry/tiktok/server.json` use version `0.1.4`; after deployment, verify the hosted server card uses the same version and endpoint.
- The hosted card must expose `tiktok_search_posts`, `tiktok_get_post_detail_by_url`, `tiktok_get_post_comments_by_url`, and `tiktok_get_user_info_by_profile_url`.
- The hosted card must expose `tiktok_submit_video_speech_text_by_url`, `tiktok_submit_video_speech_text_by_aweme_id`, and `tiktok_get_video_speech_text_job`.
- This listing advertises only the current public allowlist; internal or draft tools are excluded.
- Search and list calls pass the opaque `page_token` returned by the service for continuation.
- `examples/codex_config.toml` uses `bearer_token_env_var = "SOCIALDATAX_API_KEY"`.
- `examples/cursor_mcp.json` uses the remote URL and `${env:SOCIALDATAX_API_KEY}`.
- `mcp.json` and `examples/claude_desktop_config.json` are explicit `mcp-remote` fallbacks.
- Validate JSON and the official Registry file before submission; do not treat a hosted server card as a Registry publication.

## Required files

`README.md`, `LICENSE`, `server-card.json`, `mcp.json`, `glama.json`, all files under `examples/`, and `assets/logo.png`.
