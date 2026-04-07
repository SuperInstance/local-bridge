# Local Bridge 🛸

Register your local Ollama, vLLM, or LM Studio server with the Cocapn Fleet. Your models appear in compatible clients—no API keys, accounts, or data routing through third parties.

A public reference bridge is live at: **https://the-fleet.casey-digennaro.workers.dev/bridge**

---

## Why This Exists

You can run great models locally, but many tools require cloud API endpoints. This bridge connects your local inference server directly to the open agent ecosystem without proxying your prompts through an intermediary service.

---

## Quick Start

1.  **Fork** this repository first.
2.  Deploy to Cloudflare Workers: `npx wrangler deploy`
3.  Open your worker's URL and paste your local server's public endpoint into the form.
4.  Your model appears in fleet provider lists.

---

## How It Works

This is a stateless Cloudflare Worker. It stores transient provider metadata in KV, clearing entries after 15 minutes of inactivity. It shares only your server's public endpoint—all inference traffic flows directly from the agent to your server.

*   **Direct Connection**: Prompts and responses never pass through the bridge.
*   **OpenAI-Compatible**: Works with any local server that provides an OpenAI-compatible API.
*   **Tunnel Agnostic**: Use `cloudflared`, ngrok, Tailscale, or a direct public IP.
*   **Zero Tracking**: No accounts, API keys, or mandatory telemetry.
*   **Auditable**: ~300 lines of plain JavaScript, zero runtime dependencies.
*   **Your Control**: You manage access, rate limits, and model configuration.

---

## What Makes This Different

1.  You run your own bridge. No vendor can revoke your access.
2.  It never sees your prompts or model responses. Traffic is direct.
3.  No signup, email, or terms of service required.

---

## One Limitation

The bridge only registers your endpoint; it does not relay traffic. Your local inference server must be publicly accessible via a tunnel or public IP. The bridge also provides no authentication layer—you must secure your server separately.

---

## Contributing

This project follows the Cocapn Fleet fork-first philosophy. Fork it, modify it for your needs, and contribute stable fixes or improvements upstream via PR.

MIT License

<div style="text-align:center;padding:16px;color:#64748b;font-size:.8rem"><a href="https://the-fleet.casey-digennaro.workers.dev" style="color:#64748b">The Fleet</a> &middot; <a href="https://cocapn.ai" style="color:#64748b">Cocapn</a></div>