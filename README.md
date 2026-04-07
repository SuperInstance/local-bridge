# Local Bridge
You run models locally, but they're invisible to the fleet. This bridge makes them visible.

It connects your local LLM servers (Ollama, vLLM, LM Studio) to the Cocapn Fleet, letting you use your own models alongside any other provider.

---

## Why
Agent fleets are built for closed, hosted APIs. The model on your machine is an afterthought.

This bridge does one thing: it lets the fleet discover and use your local models. No proxies, no wrapper fees.

---

## Try It
You can test the public bridge endpoint now. No signup.
**Live URL**: `https://the-fleet.casey-digennaro.workers.dev/bridge`

If you have Ollama running, you can register it in about a minute.

---

## Quick Start
1.  **Fork & clone** this repository.
2.  **Deploy** to Cloudflare Workers: `npx wrangler deploy`
3.  **Register** your local endpoint via the deployed worker's web interface.

---

## How It Works
This Cloudflare Worker is a registration hub and status tracker. It stores public model metadata and runs passive health checks. Valid endpoints are advertised to the fleet. **All inference traffic flows directly between agents and your local server**; this bridge never sees it.

## Features
*   **Runtime Support**: Works with OpenAI-compatible local runtimes (Ollama, vLLM, LM Studio).
*   **Tunnel Agnostic**: Use `cloudflared`, `ngrok`, Tailscale, or a direct public IP.
*   **Passive Health Checks**: Your server is pinged only to verify liveness.
*   **Fleet Discovery**: Registered models appear in provider lists for all agents.
*   **Zero Dependencies**: The entire worker is plain JavaScript.
*   **No Gatekeeping**: No accounts, API keys, or rate limits from the bridge.

## Limitation
Your local model must be accessible via a public endpoint. If your network or tunnel is unstable, the model may be marked offline by the fleet.

---

## What This Is Not
*   **A Proxy**: We never see your prompts or inference traffic.
*   **A Service**: This is infrastructure you own and deploy. Fork-first philosophy.

---

## Contributing
Fork the repository, adapt it for your use case, and send improvements upstream. PRs are welcome for better health checks or documentation.

---

MIT License · Superinstance & Lucineer (DiGennaro et al.)

---
<div align="center">
  <a href="https://the-fleet.casey-digennaro.workers.dev">The Fleet</a> · 
  <a href="https://cocapn.ai">Cocapn</a>
</div>