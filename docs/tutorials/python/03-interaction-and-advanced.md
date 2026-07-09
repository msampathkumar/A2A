# 3. Server Interaction & Advanced Capabilities

Once your A2A server is running, you can interact with it via standard HTTP/JSON-RPC protocols or utilize more advanced streaming features.

## Starting the Server
The Python SDK uses a route factory to expose A2A services. These routes are compatible with frameworks like [Starlette](https://www.starlette.io/) or [FastAPI](https://fastapi.tiangolo.com/).

The server setup involves:
1.  **RequestHandler**: Orchestrates incoming RPC calls using your `AgentExecutor`, `TaskStore` (for state management), and `AgentCard` (for capability verification).
2.  **Routes**: `create_agent_card_routes` exposes your card at `/.well-known/agent-card.json`, while `create_jsonrpc_routes` maps RPC calls to your executor.
3.  **Run**: Use `uvicorn` or any ASGI server to host the application.

Run the Helloworld example:
```bash
python samples/python/agents/helloworld/__main__.py
```

## Interacting with the Server
Clients interact with your agent by sending JSON-RPC requests to the endpoint defined in your `AgentCard` (e.g., `http://127.0.0.1:9999/`). 

Common requests include:
- `GetAgentCard`: Retrieve identity and capability info.
- `SendMessage`: Send a request and wait for a response.
- `SendStreamingMessage`: Start a stream of responses/events.

## Advanced: Streaming & Multi-Turn
For more complex interactions—like LLM integrations—the SDK supports:
- **Streaming**: Instead of a single response, the `AgentExecutor` emits a stream of events (`TaskStatusUpdateEvent`, `TaskArtifactUpdateEvent`) over the `EventQueue`.
- **Multi-Turn**: By utilizing a persistent `TaskStore` within the `RequestHandler`, the agent maintains conversational context across multiple client messages, essential for complex task orchestration (e.g., utilizing [LangGraph](https://www.langchain.com/langgraph)).

---
*You now have a functional foundation for building and interacting with A2A-compliant agents. For further exploration, examine the `a2a-samples` directory for more advanced implementation patterns.*
