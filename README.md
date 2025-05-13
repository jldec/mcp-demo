# MCP Demo

Simple hosted multiplayer chat with AI and MCP tools  
Based on cloudflare/agents-starter - see [README-agent-starter.md](README-agent-starter.md)  
Minimal changes (modified .prettierrc to remove semicolons and trailing commas)

### To run locally

- `npm install`
- configure openai key in `.dev.vars`
- `npm run dev`

### TODO next

- add installable (remote) tools and remove built in tools
- replace starter UI with simple monospace style (like https://jldec.me?chat)

### Basic demo

- single multi-user persisted chat with one hardwired LLM
- add/remove/list MCP servers via tool calls
- AI answers every message
- login (hosted version only)
- use tools in chat
- persist chat

### MVP

- navigate between spaces, one chat per space
- support addressable LLM agents per space (like users)
- configure different MCP servers per agent
- user identity and authz on MCP tool calls

---

Initial stack chosen for velocity

### cloudflare agents starter

- runs on cloudflare workers
- uses cloudflare vite plugin for local dev
- uses durable objects for chat (via agents library)
- agents library also has support for building MCP servers and clients.
- https://github.com/cloudflare/agents-starter
- https://developers.cloudflare.com/agents/
- https://developers.cloudflare.com/durable-objects/#what-are-durable-objects
- https://developers.cloudflare.com/workers/vite-plugin/

### vercel AI sdk for LLM integration and MCP tools client

- https://vercel.com/blog/ai-sdk-4-2
- https://sdk.vercel.ai/docs/foundations/overview
- https://sdk.vercel.ai/docs/ai-sdk-core/tools-and-tool-calling#mcp-tools
- https://developers.cloudflare.com/workers-ai/configuration/ai-sdk/

### cloudflare zero-trust (access) no-code auth on chat UI

- https://jldec.me/blog/no-code-authentication-with-cloudflare-zero-trust-access
- https://developers.cloudflare.com/cloudflare-one/identity/

### MCP tools server hosting TBD

- for first demo, we'll probably run wasmtime in a container
- https://eunomia.dev/blog/2025/02/16/wasi-and-the-webassembly-component-model-current-status/
- may use https://fly.io or google cloud run or aws lambda or aws ecs to host the container
- alternatively could try to run rust / wasm on cloudflare workers
- https://developers.cloudflare.com/workers/languages/rust/#how-this-deployment-works
- cloudflare containers are not ready yet https://blog.cloudflare.com/cloudflare-containers-coming-2025/
- could also build MCP servers directly in JavaScript and deploy to cloudflare workers

### For MCP server auth TBD

- could use https://github.com/cloudflare/workers-oauth-provider for MCP servers hosted on cloudflare workers.

### LLM API service TBD

- this looks reasonable https://ai.google.dev/gemini-api/docs/pricing
