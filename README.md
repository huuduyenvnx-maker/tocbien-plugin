# Tốc Biến (TocBien)

Plugin for **Claude Code, Cursor and ChatGPT** that connects the agent to [tocbien.cloud](https://tocbien.cloud): create a Vietnam VPS, top up with VietQR, and put a site or app online.

This repository is **metadata only** — manifest, MCP URL, and a Vietnamese skill. It does not ship an API, database, or secrets. Auth is **OAuth 2.1**: your AI app opens the Tốc Biến sign-in page (Google, or email + password), you click **Cho phép** (Allow), done. There is no API key to paste.

## What it includes

- Remote MCP: `https://tocbien.cloud/mcp` (Streamable HTTP, OAuth 2.1 + PKCE, dynamic client registration)
- Skill `tocbien`: Vietnamese flow — pick a plan, confirm price, pay, deploy, report a live URL only after the tools confirm it
- Logo: `assets/logo.png` (1024×1024)

Also listed on the official MCP Registry as [`cloud.tocbien/tocbien`](https://registry.modelcontextprotocol.io/?q=cloud.tocbien).

## Install

**Claude Code** — as a plugin:

```
/plugin marketplace add https://github.com/huuduyenvnx-maker/tocbien-plugin.git
/plugin install tocbien@tocbien
```

or just the MCP server:

```bash
claude mcp add --transport http tocbien https://tocbien.cloud/mcp
```

Then run `/mcp`, pick `tocbien` → **Authenticate**. Before you sign in the status is "Needs authentication" — that is expected.

**Cursor** — Marketplace (after listing): search **Tốc Biến** / `tocbien` → Install → sign in when prompted. From this repo: Settings → Plugins → add this folder, **or** Settings → MCP → add URL `https://tocbien.cloud/mcp`.

**ChatGPT** — Settings → Apps & Connectors → Advanced → Developer mode → Create: URL `https://tocbien.cloud/mcp`, authentication **OAuth**. Then connect and sign in.

**Codex**:

```bash
codex mcp add tocbien --url https://tocbien.cloud/mcp
```

No environment variables. No `${API_TOKEN}`.

## How to use

Ask in Vietnamese or English, for example: “tạo máy WordPress”, “nạp VietQR”, “đưa app lên mạng”.

The skill will:

1. Ask what to run (web, WordPress, n8n, chatbot, source) and a machine name
2. Show Mach plans and wait for you to confirm (creating a VPS spends real credit)
3. If the balance is short: create a VietQR order and wait for payment
4. Deploy, then give the live URL only after `list_apps` says LIVE

No-code users who are not using this plugin can still connect from the dashboard: [tocbien.cloud](https://tocbien.cloud) → Kết nối AI → copy a `tb_act_` code and paste it into the chat.

## Safety

- Creating a VPS or a top-up order moves real money. The agent must confirm with you first — `create_vps`, `deploy_app` and `deploy_code` are marked destructive so the client asks before running them.
- The plugin never invents a live URL.
- If MCP tools fail twice, it stops and reports the error.
- Revoke access any time at tocbien.cloud → Kết nối AI.

## License

MIT. Product: [tocbien.cloud](https://tocbien.cloud) · Contact: hello@tocbien.cloud
