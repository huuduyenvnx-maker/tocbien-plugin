# Tốc Biến (TocBien)

Cursor plugin that connects the agent to [tocbien.cloud](https://tocbien.cloud): create a Vietnam VPS, top up with VietQR, and put a site or app online.

This repository is **metadata only** — manifest, MCP URL, and a Vietnamese skill. It does not ship an API, database, or secrets. Auth is **Google OAuth** in Cursor (Authenticate). There is no API key to paste.

## What it includes

- Remote MCP: `https://tocbien.cloud/mcp` (HTTP, OAuth)
- Skill `tocbien`: Vietnamese flow — pick a plan, confirm price, pay, deploy, report a live URL only after the tools confirm it
- Logo: `assets/logo.png` (1024×1024)

Also listed on the official MCP Registry as [`cloud.tocbien/tocbien`](https://registry.modelcontextprotocol.io/?q=cloud.tocbien).

## Install

**Cursor Marketplace** (after listing): search **Tốc Biến** / `tocbien` → Install → Authenticate with Google.

**From this repo (local / review):**

1. Clone `https://github.com/huuduyenvnx-maker/tocbien-plugin`
2. Cursor → Settings → Plugins → add this folder, **or** Settings → MCP → add URL `https://tocbien.cloud/mcp`
3. Authenticate with Google when Cursor prompts

No environment variables. No `${API_TOKEN}`.

## How to use

Ask in Vietnamese or English, for example: “tạo máy WordPress”, “nạp VietQR”, “đưa app lên mạng”.

The skill will:

1. Ask what to run (web, WordPress, n8n, chatbot, source) and a machine name
2. Show Mach plans and wait for you to confirm (creating a VPS spends real credit)
3. If the balance is short: create a VietQR order and wait for payment
4. Deploy, then give the live URL only after `list_apps` / `list_vps` say LIVE

No-code users who are not using this plugin can still connect from the dashboard: [tocbien.cloud](https://tocbien.cloud) → Kết nối AI → copy a `tb_act_` code and paste it into the chat.

## Safety

- Creating a VPS or a top-up order moves real money. The agent must confirm with you first.
- The plugin never invents a live URL.
- If MCP tools fail twice, it stops and reports the error.

## Other clients

```bash
claude mcp add --transport http tocbien https://tocbien.cloud/mcp
codex mcp add tocbien --url https://tocbien.cloud/mcp
```

Then Authenticate / sign in with Google.

## License

MIT. Product: [tocbien.cloud](https://tocbien.cloud) · Contact: hello@tocbien.cloud
