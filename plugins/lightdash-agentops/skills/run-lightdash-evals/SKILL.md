---
name: run-lightdash-evals
description: Orchestrate evaluation runs and test case management for Lightdash agents.
---

# Run Lightdash Evaluations

Skill for managing and executing evaluations for Lightdash AI agents.

## Purpose

Enables the "Eval-Driven Development" workflow by providing tools to create evaluation suites, append test cases (prompts), execute evaluation runs, and analyze the results.

## Tools

Wraps the following MCP tools from the `lightdash-tools` server:

- `ldt__list_agent_evaluations`
- `ldt__get_agent_evaluation`
- `ldt__create_agent_evaluation`
- `ldt__update_agent_evaluation`
- `ldt__append_agent_evaluation_prompts`
- `ldt__run_agent_evaluation`
- `ldt__list_agent_evaluation_runs`
- `ldt__get_agent_evaluation_run_results`
- `ldt__delete_agent_evaluation`

## Safety Mode Compliance

- **Read Tools**: `list_agent_evaluations`, `get_agent_evaluation`, `list_agent_evaluation_runs`, `get_agent_evaluation_run_results`.
- **Write-Safe Tools**: `create_agent_evaluation`, `update_agent_evaluation`, `append_agent_evaluation_prompts`, `run_agent_evaluation`.
- **Write-Destructive Tools**: `delete_agent_evaluation`.

## Behavior

1. **Test Case Management**:
   - Use `ldt__append_agent_evaluation_prompts` to add 20-50 diverse test cases representing real-world user queries.
   - Organize evaluations by agent or project to maintain clarity.
2. **Execution**:
   - Trigger a run using `ldt__run_agent_evaluation`.
   - Monitor the progress using `ldt__list_agent_evaluation_runs`.
3. **Analysis**:
   - Once a run is complete, fetch the detailed results via `ldt__get_agent_evaluation_run_results`.
   - Identify patterns in failures (e.g., specific dimensions or metrics that the agent struggles with).

## Rules

- ALWAYS create or update an evaluation suite before deploying major changes to an agent's prompt.
- NEVER delete an evaluation suite without explicit confirmation.
- Use the `agent-tuner` sub-agent to automatically process evaluation results for improvement.
