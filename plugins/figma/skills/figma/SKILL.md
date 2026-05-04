---
name: figma
description: Use Figma through Playbot's Figma MCP server for design inspection and design-to-code handoff without OpenAI connector login.
---

# Playbot Figma

Use this skill when the user provides a Figma URL, asks to inspect a Figma design, implement from Figma, or generate design-system guidance from Figma.

## Workflow

1. Use the `figma` MCP server tools exposed by this plugin.
2. If the MCP server reports that auth is required, tell the user to connect Figma from Playbot Plugins.
3. Do not send the user to ChatGPT or OpenAI connector setup pages.
4. Prefer precise file keys and node IDs from the user's Figma URL.
5. For design-to-code work, inspect the local codebase before generating implementation guidance.
6. Do not claim write support unless the MCP server exposes a write-capable tool.

## Auth Model

Figma auth is owned by Playbot. The plugin should use Playbot's MCP OAuth flow and should never require an OpenAI login.

## Failure Handling

- If Figma permissions are missing, ask the user to grant access to the target file or team.
- If a Playbot MCP request fails, report the returned error directly.
- If a requested capability is not exposed by the current MCP server, state the missing capability directly and continue with the closest available read-only workflow.
