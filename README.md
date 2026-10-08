# DocNexus MCP Server

Search US healthcare providers, key opinion leaders (KOLs), executives and organizations from any AI assistant, backed by DocNexus's de-identified claims data.

This is a **hosted, remote MCP server**. There is nothing to install or run. This repository holds documentation only; the server source is not public.

- **MCP endpoint:** `https://mcp.docnexus.ai/mcp` (Streamable HTTP)
- **Website:** https://mcp.docnexus.ai
- **Registry name:** `ai.docnexus.mcp/docnexus`

## What it does

| Tool | What it answers |
|---|---|
| `lookup_values` | Resolve codes and names (specialties, conditions, procedures, drugs) before searching |
| `find_hcps` | Find providers by specialty, location, condition, procedure or drug |
| `find_kols` | Find key opinion leaders ranked by influence and activity |
| `find_executives` | Find executives at healthcare organizations |
| `hcp_claim_volume` | Top providers by claim or patient volume |
| `org_claim_volume` | Top organizations by claim or patient volume |
| `market_volume` | Market size for a condition, procedure or drug |
| `patient_volume_trend` | Patient volume over time |
| `find_referrals` | Referral network for a provider (opens in the DocNexus platform) |
| `hcp_affiliations` | Hospital, group and organization affiliations for a provider |
| `opportunity_map` | Geographic opportunity map (opens in the DocNexus platform) |
| `search` / `fetch` | Look up a provider by name or NPI and fetch the full profile |

Every tool is **read-only**. Nothing is written or changed. Results are capped at 10 rows per call, with a link to the full result in the DocNexus platform.

## Configure

You need a DocNexus account. Sign-in uses OAuth 2.0 with PKCE; your client opens a browser window the first time you connect.

### GitHub Copilot (VS Code)

Add to `.vscode/mcp.json`:

```json
{
  "servers": {
    "docnexus": {
      "type": "http",
      "url": "https://mcp.docnexus.ai/mcp"
    }
  }
}
```

Start the server from the MCP view and sign in when prompted.

### Claude

Settings → Connectors → **Add custom connector** → paste `https://mcp.docnexus.ai/mcp`.

### ChatGPT

Settings → Apps & Connectors → **Create** (Developer mode) → paste `https://mcp.docnexus.ai/mcp`, auth **OAuth**.

### Gemini CLI

```bash
gemini mcp add -t http docnexus https://mcp.docnexus.ai/mcp
gemini   # then: /mcp auth docnexus
```

### Any other MCP client

Point it at `https://mcp.docnexus.ai/mcp` with Streamable HTTP transport and OAuth. The server supports dynamic client registration, so no client ID is needed.

## Use

Ask in plain language. For example:

- "Find the top 10 cardiologists in Boston treating heart failure."
- "Who are the leading KOLs for multiple myeloma in Texas?"
- "Which organizations have the highest patient volume for knee replacement in Ohio?"
- "Show the patient volume trend for GLP-1 prescriptions over the last 3 years."
- "Look up NPI 1234567890 and list their affiliations."

## Data and privacy

Results come from de-identified claims data. No patient-level information is returned. Access is tied to your DocNexus account and its permissions.

## Support

https://mcp.docnexus.ai
