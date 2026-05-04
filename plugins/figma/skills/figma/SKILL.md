---
name: figma
description: Use Figma through Playbot's Figma MCP server for design inspection, design-to-code handoff, Code Connect, design-system work, and Figma file updates without OpenAI connector login.
---

# Playbot Figma

Use this skill when the user provides a Figma URL, asks to inspect a Figma design, implement from Figma, create or update Figma files, work with Code Connect, or generate design-system guidance from Figma.

## Workflow

1. Use the `figma` MCP server tools exposed by this plugin.
2. If the MCP server reports that auth is required, tell the user to connect Figma from Playbot Plugins.
3. Do not send the user to ChatGPT or OpenAI connector setup pages.
4. Prefer precise file keys and node IDs from the user's Figma URL.
5. For design-to-code work, inspect the local codebase before generating implementation guidance.
6. For write operations, explain the intended Figma change before calling a write-capable tool.

## Auth Model

Figma auth is owned by Playbot. The plugin should use Playbot's MCP OAuth flow and should never require an OpenAI login.

## Failure Handling

- If Figma permissions are missing, ask the user to grant access to the target file or team.
- If the Playbot Figma MCP server is unavailable, report that Playbot Figma backend support is not reachable.
- If a requested capability is not exposed by the current MCP server, state the missing capability directly and continue with the closest available read-only workflow.
