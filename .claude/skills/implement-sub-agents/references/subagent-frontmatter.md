# Sub-Agent Frontmatter

Include frontmatter at the top of each agent markdown file.

## Minimum Fields

- `name`
- `description`

## Optional Fields

- `skills`: Array of skill names to preload into the sub-agent's context.
- `model`: AI model to use (`sonnet`, `haiku`, `opus`, or `inherit`).
- `tools`: Allowlist of tools the sub-agent can use.
- `disallowedTools`: Denylist of tools to remove from inherited list.
- `permissionMode`: How to handle permission prompts (`default`, `acceptEdits`, `bypassPermissions`, etc.).
- `memory`: Persistent memory scope (`user`, `project`, or `local`).

## Guidance

- Make `description` explicit about ownership and outputs.
- Keep one role per agent file.

## Source

- https://code.claude.com/docs/en/sub-agents
