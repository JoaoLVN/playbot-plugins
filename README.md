# Playbot Plugins

Codex-compatible marketplace for Playbot-managed plugins.

## Current Plugins

- `figma` — Figma workflows through Playbot-native MCP auth.

## Layout

- `.agents/plugins/marketplace.json` — marketplace manifest.
- `plugins/figma/.codex-plugin/plugin.json` — Figma plugin manifest.
- `plugins/figma/.mcp.json` — Playbot Figma MCP server config.
- `plugins/figma/skills/figma/SKILL.md` — Figma usage guidance.

## Auth

This repo intentionally does not include `.app.json` connector metadata. Figma auth should flow through Playbot's MCP OAuth server at `https://play.bot/api/mcp/figma`.

The Playbot API needs:

- `API_BASE_URL=https://play.bot/api`
- `FIGMA_OAUTH_CLIENT_ID`
- `FIGMA_OAUTH_CLIENT_SECRET`
- A Figma OAuth callback URL registered as `https://play.bot/api/mcp/figma/oauth/figma-callback`

## Local Testing

Point Playbot at this marketplace with:

```bash
PLAYBOT_PLUGIN_MARKETPLACE_SOURCE=https://github.com/JoaoLVN/playbot-plugins.git
```

Then open Settings → Playbot Plugins and sync/install Figma.
