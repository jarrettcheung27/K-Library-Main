**Gateway**: An **AI agent gateway** is a centralized, secure middleware layer that acts as a traffic controller, governing, monitoring, and routing communication between AI agents, LLMs, and external tools.

**Cron Jobs**: Cron is the Gateway’s built-in scheduler. It persists jobs, wakes the agent at the right time, and can optionally deliver output back to a chat.
>If you want _“run this every morning”_ or _“poke the agent in 20 minutes”_, cron is the mechanism.


**Node**：A **node** is a companion device (macOS/iOS/Android/headless) that connects to the Gateway **WebSocket** (same port as operators) with `role: "node"` and exposes a command surface (e.g. `canvas.*`, `camera.*`, `system.*`) via `node.invoke`.