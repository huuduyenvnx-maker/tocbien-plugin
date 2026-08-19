# Tốc Biến — plugin MCP

Gói **metadata** để gắn MCP Tốc Biến vào Cursor / Claude Code. Không chứa API, không chứa khóa.

- MCP: `https://tocbien.cloud/mcp` (OAuth Google, không nhét token)
- Dân no-code: vào [tocbien.cloud](https://tocbien.cloud) → Kết nối AI → lấy mã `tb_act_` rồi dán. Plugin này nằm cửa **nâng cao**.

## Cài local (trước khi lên store)

**Cursor:** Settings → MCP → thêm URL trên, hoặc deeplink trong dashboard (Nâng cao).

**Claude Code:**

```bash
claude mcp add --transport http tocbien https://tocbien.cloud/mcp
```

Rồi Authenticate Google. Hoặc `/plugin marketplace add <owner>/tocbien-plugin` sau khi repo này public.

**Codex:**

```bash
codex mcp add tocbien --url https://tocbien.cloud/mcp
```

## Nộp store (chủ sản phẩm)

1. Tách thư mục này thành repo GitHub **public** (đừng đẩy cả monorepo Tốc Biến — có secret).
2. Cursor: [cursor.com/marketplace/publish](https://cursor.com/marketplace/publish) — dán link repo.
3. Claude Code community: [claude.com/docs/plugins/submit](https://claude.com/docs/plugins/submit) — cùng repo. Official Anthropic list không xin được.
4. MCP Registry: **đã live** — `cloud.tocbien/tocbien` ([registry](https://registry.modelcontextprotocol.io/?q=cloud.tocbien)). Xác thực DNS TXT trên `tocbien.cloud`. Khóa ký ở `.secrets/key.pem`, không commit.

**Không nộp:** Claude Connectors Directory, ChatGPT Apps — Claude/OpenAI gọi MCP từ cloud của họ, khóa AI Tốc Biến ghim ASN+JA4 → dễ kẹt khi tiêu tiền.

## File

| File | Việc |
|---|---|
| `.cursor-plugin/plugin.json` + `mcp.json` | Cursor Marketplace |
| `.claude-plugin/plugin.json` + `.mcp.json` + `marketplace.json` | Claude Code plugin / marketplace riêng |
| `skills/tocbien/SKILL.md` | Skill tiếng Việt |
| `server.json` | Official MCP Registry |
| `assets/logo.png` | Logo |

MIT. Sản phẩm: [tocbien.cloud](https://tocbien.cloud)
