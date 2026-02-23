# Sales Outreach Agent — n8n + Claude

A fully automated sales outreach agent built with n8n and Claude. It researches leads, drafts personalized emails, enforces guardrails, routes senior contacts for human approval, and logs everything back to your CRM.

Built and shared as part of my [Building with Agentic AI](https://www.linkedin.com) newsletter series.

---

## What It Does

- Reads a leads list from Google Sheets
- Checks Airtable for prior contact history
- Researches each lead in real time using web search (Serper)
- Drafts a personalized email using Claude (Anthropic API)
- Validates email length (flags if over 150 words)
- Routes VP+ contacts to a human approval step via Slack
- Sends approved emails via Gmail
- Logs all outreach activity back to Airtable

---

## Tech Stack

| Layer | Tool |
|---|---|
| Orchestration | n8n |
| LLM | Claude (Anthropic API) |
| Lead Source | Google Sheets |
| CRM / Memory | Airtable |
| Research | Serper (Google Search API) |
| Email | Gmail |
| Approval | Slack |

---

## Getting Started

1. Clone or download this repo
2. In n8n, go to **Workflows → Import from File**
3. Upload `workflow.json`
4. Connect your credentials: Google Sheets, Airtable, Anthropic API, Serper, Gmail, Slack
5. Open the **Research & Draft Agent** node and update the system prompt with your ICP and messaging playbook
6. Run the **Manual Trigger** on a single test lead first before enabling the schedule

---

## File Structure

```
/
├── workflow.json       # n8n workflow — import this
└── README.md
```

---

## Important Before You Run

- **Strip credentials**: n8n usually handles this on export, but double-check the JSON for any API keys or account-specific IDs before sharing or deploying
- **Test on one lead first**: Run the manual trigger with a single row in your sheet before processing a full list
- **Customize the system prompt**: The quality of the email draft depends almost entirely on how well you define your ICP, tone, and messaging rules in Step 5

---

## How It Maps to Agentic Building Blocks

| Building Block | Implementation |
|---|---|
| Knowledge & Context | ICP + playbook in system prompt, live research via Serper |
| Tools | Google Sheets, Airtable, Serper, Gmail, Slack |
| Memory | Airtable contact history log |
| Guardrails | DNC check, length validation, human approval for VP+ |

---

## Questions or Feedback?

If you downloaded this and gave it a try — I'd love to hear how it went. Drop a comment on the article or reach out directly.

---

*Part of the [Building with Agentic AI](https://www.linkedin.com) series — weekly frameworks, real examples, and practical workflows. No hype.*
