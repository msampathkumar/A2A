# 2. Core Components: Skills, Cards, and Executors

An A2A agent is defined by three pillars: its skills, its identity card, and its executor logic.

## Agent Skills
An **Agent Skill** describes a specific capability or function the agent can perform.

<details>
<summary>AgentSkill Attributes</summary>

- `id`: Unique identifier.
- `name`: Human-readable name.
- `description`: Detailed explanation.
- `tags`: Categorization/discovery keywords.
- `examples`: Sample prompts.
- `input_modes` / `output_modes`: Supported Media Types.
- `security_requirements`: Mandatory security schemes.
</details>

## Agent Card
The **Agent Card** is a JSON document (`.well-known/agent-card.json`) that acts as a digital business card.

<details>
<summary>AgentCard Attributes</summary>

- `name`, `description`, `version`: Identity metadata.
- `supported_interfaces`: Ordered list of reachable endpoints/protocols.
- `capabilities`: Features like `streaming` or `extended_agent_card`.
- `default_input_modes` / `default_output_modes`: Default media handling.
- `skills`: List of supported `AgentSkill` objects.
</details>

## The Agent Executor
The **Agent Executor** bridges the A2A protocol and your custom logic. It implements the `a2a.server.agent_execution.AgentExecutor` interface, specifically handling:

- `execute()`: Manages incoming requests, processes input via `RequestContext`, and utilizes the `EventQueue` to send back task updates (status, artifacts, messages).
- `cancel()`: Handles task interruption requests.

The executor ensures the agent lifecycle (Working -> Processing -> Completed) is correctly reported to the A2A server.
