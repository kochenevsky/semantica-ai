# Semantica AI — MCP Server

> Track and grow your brand visibility across AI assistants: ChatGPT, Perplexity, Claude, Gemini, Grok, DeepSeek, YandexGPT, and more.

**Semantica AI** is an AI visibility analytics platform. This MCP server gives AI assistants (Claude, Cursor, Windsurf, etc.) direct access to Semantica's analytics — so you can monitor brand mentions in LLM responses, run visibility scans, analyze competitors, track publications, and get actionable GEO/AEO insights, all from your AI chat.

🌐 **Website:** [ai-semantica.com](https://ai-semantica.com)  
📖 **MCP Docs:** [ai-semantica.com/ru/mcp](https://ai-semantica.com/ru/mcp)

---

## Quickstart

This is a **remote HTTP/SSE server** — no installation required. Just add the endpoint to your MCP client config.

### Claude Desktop / Cursor / Windsurf

```json
{
  "mcpServers": {
    "semantica-ai": {
      "url": "https://ai-semantica.com/mcp",
      "transport": "sse",
      "headers": {
        "Authorization": "Bearer YOUR_API_KEY"
      }
    }
  }
}
```

Get your API key at [ai-semantica.com](https://ai-semantica.com) after signing up.

> **New user?** Connect without `Authorization` first and use the `onboarding_*` tools to register and set up your project directly from chat.

---

## What You Can Do

### 🔍 Visibility Scans

Run scans to see how often and where your brand appears in AI-generated responses.

| Tool | Description |
|------|-------------|
| `create_scan` | Start a new brand visibility scan across AI providers (ChatGPT, Claude, Perplexity, Gemini, Grok, DeepSeek, YandexGPT, GigaChat, and more) |
| `list_scans` | List all scans with pagination |
| `get_scan` | Get full results of a scan — mention rates, per-provider breakdown, citations, raw AI responses |

### 📊 Analytics & Metrics

Dig into the data behind your AI visibility.

| Tool | Description |
|------|-------------|
| `get_visibility_metrics` | Brand visibility scores and trends over time, broken down by AI provider |
| `get_scan_results_bi` | Detailed per-prompt results for BI/reporting (mention flag, sentiment, no_company_mention flag) |
| `get_projects_summary` | High-level summary across all projects: total scans, prompts, last scan date |
| `get_zero_click_positions` | Your brand's estimated rank in ordered lists inside AI answers (zero-click report) |

### 📄 Mentioned Pages

See which of your pages are cited by AI assistants.

| Tool | Description |
|------|-------------|
| `get_mentioned_pages` | Pages from your domain (or a competitor's) cited in AI responses, sorted by frequency |
| `get_mentioned_pages_occurrences` | Detailed occurrences of a specific URL or domain in AI responses with prompt context |

### 🏆 Competitor Analysis

Understand how competitors appear in AI responses vs. your brand.

| Tool | Description |
|------|-------------|
| `analyze_competitor_sentiment` | Average sentiment scores per competitor across given scans |

### 📰 Publications

Track which articles and pages influence AI responses about your brand.

| Tool | Description |
|------|-------------|
| `list_publications` | List tracked publications for a project |
| `add_publication` | Add a publication URL to tracking |
| `delete_publication` | Remove a publication from tracking |
| `list_publication_mentions` | See how tracked publications are mentioned in AI responses |

### 📁 Projects

Manage monitoring projects for different websites or clients.

| Tool | Description |
|------|-------------|
| `list_projects` | List your projects (or a client's projects if agency) |
| `get_project` | Get details of a specific project |
| `list_all_projects` | Get all projects: your own + all agency clients' combined |

### 🏢 Agency Tools

For agencies managing multiple client accounts.

| Tool | Description |
|------|-------------|
| `list_agency_clients` | List all clients in your agency account |
| `resolve_agency_client_id_by_email` | Look up a client's user ID by email |
| `get_client_projects` | List projects for a specific agency client |
| `get_client_scans` | List scans for a specific agency client |

---

## 🚀 Onboarding (Register & Set Up from Chat)

You can register a new Semantica AI account and set up your first project entirely from the AI chat — no browser needed.

**Connect without `Authorization` header to start:**

```json
{
  "mcpServers": {
    "semantica-ai": {
      "url": "https://ai-semantica.com/mcp",
      "transport": "sse"
    }
  }
}
```

Then ask your AI assistant: *"Help me set up Semantica AI"* and follow the wizard.

### Registration

| Tool | Description |
|------|-------------|
| `onboarding_wizard_overview` | Get the full step-by-step wizard overview |
| `onboarding_request_email_code` | Send a 6-digit verification code to your email |
| `onboarding_verify_email_code` | Verify the email code |
| `onboarding_register` | Create your Semantica AI account (returns `accessToken`) |
| `onboarding_whoami` | Check the currently authenticated user profile |

### Project Setup

| Tool | Description |
|------|-------------|
| `onboarding_get_wizard_context` | Check if an onboarding project exists, subscription status, account profile |
| `onboarding_validate_site` | Validate your domain before creating a project |
| `onboarding_set_account_type` | Set account type: `business` or `agency` |
| `onboarding_save_geo_analytics` | Link a GEO analytics service to your account (optional) |
| `onboarding_detect_languages` | Auto-detect your site's languages |
| `onboarding_generate_topics` | Generate topic categories for visibility tracking |
| `onboarding_generate_prompts` | Generate search prompts grouped by topics |
| `onboarding_get_scan_setup_info` | Get scan limits and available AI provider config |
| `onboarding_start_scan` | Create a project and run the first visibility scan |
| `onboarding_get_scan` | Poll scan status and results |

### Billing

| Tool | Description |
|------|-------------|
| `onboarding_get_billing_plans` | Get available plans with pricing |
| `onboarding_start_trial` | Activate a 3-day free trial |
| `onboarding_subscription_checkout_url` | Get a Stripe checkout URL for `basic` or `advanced` plan |
| `onboarding_complete` | Mark onboarding as completed |

---

## Example Prompts

Once connected, you can ask your AI assistant:

- *"Run a visibility scan for example.com and show me the results"*
- *"What are my visibility metrics for the last 30 days?"*
- *"Which pages from my site are being cited in ChatGPT responses?"*
- *"Compare my brand sentiment vs. competitor X in AI responses"*
- *"Show me which publications are influencing my brand's AI visibility"*
- *"List all zero-click positions where AI answers queries without citing anyone"*
- *"List all my agency clients and their projects"*
- *"Help me register on Semantica AI and set up my first project"*

---

## Authentication

All requests (except registration tools) require a valid API key passed as a Bearer token in the `Authorization` header.

```
Authorization: Bearer YOUR_API_KEY
```

Sign up at [ai-semantica.com](https://ai-semantica.com) to get your API key.

---

## Transport

| Property | Value |
|----------|-------|
| Protocol | HTTP/SSE (Server-Sent Events) |
| Type | Remote (no local installation needed) |
| Base URL | `https://ai-semantica.com/mcp` |

---

## AI Providers Supported

`chatgpt` · `claude` · `perplexity` · `gemini` · `grok` · `deepseek` · `yandexgpt` · `yandexaio` · `google_aio` · `gigachat`

---

## Links

- 🌐 [Website](https://ai-semantica.com)
- 📖 [MCP Documentation](https://ai-semantica.com/ru/mcp)
- 📬 Support: mail@ai-semantica.com
