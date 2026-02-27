---
name: debug-agent-threads
description: Inspection of thread history, memory, and organization-wide agent activity.
---

# Debug Agent Threads

Skill for monitoring, debugging, and analyzing Lightdash AI agent conversations and configurations.

## Purpose

Provides visibility into how agents interact with users. It allows for tracing context, identifying hallucinations, and auditing organization-wide AI settings and activity.

## Tools

Wraps the following MCP tools from the `lightdash-tools` server:

- **Conversations**:
  - `ldt__list_agent_threads`
  - `ldt__get_agent_thread`
  - `ldt__generate_agent_message`
  - `ldt__continue_agent_thread`
- **Admin & Monitoring**:
  - `ldt__list_admin_agents`
  - `ldt__list_admin_agent_threads`
  - `ldt__get_ai_organization_settings`
  - `ldt__update_ai_organization_settings`

## Safety Mode Compliance

- **Read Tools**: All `list_` and `get_` tools.
- **Write-Safe Tools**: `generate_agent_message`, `continue_agent_thread`.
- **Write-Destructive Tools**: `update_ai_organization_settings`.

## Behavior

1. **Memory Inspection**:
   - Use `ldt__get_agent_thread` to retrieve the full message history of a specific conversation.
   - Analyze the history to see if the agent is correctly utilizing its memory or if it is exceeding context window limits.
2. **Conversation Debugging**:
   - Use `ldt__generate_agent_message` to test an agent's response to a specific prompt without persisting it to a thread if needed, or `ldt__continue_agent_thread` to simulate user interaction.
3. **Organization Audit**:
   - Use `ldt__list_admin_agent_threads` to monitor activity across the entire organization.
   - Check `ldt__get_ai_organization_settings` to verify that global safety and privacy settings are correctly configured.

## Rules

- NEVER update organization-wide AI settings without explicit authorization.
- Use thread inspection to gather evidence before modifying an agent's persona or instructions.
