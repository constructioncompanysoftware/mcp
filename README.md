<p align="center">
  <img src="assets/logo.png" alt="Construction Company Software" width="96" height="96">
</p>

<h1 align="center">Construction Company Software MCP server</h1>

<p align="center">
  Connect Claude, ChatGPT, Cursor and other AI apps to your construction jobs: schedules, subs, budgets, RFIs, daily logs and punch lists.
</p>

<p align="center">
  <a href="https://www.construction-company-software.com/ai/mcp">Docs</a> ·
  <a href="https://www.construction-company-software.com">Website</a> ·
  <a href="https://www.construction-company-software.com/pricing">Pricing</a>
</p>

---

[Construction Company Software](https://www.construction-company-software.com) is construction management for US builders, remodelers and general contractors: scheduling and Gantt, texts to subs with one-tap confirm, field tools, a client portal, estimates, change orders and invoices.

**Get started:** [construction-company-software.com](https://www.construction-company-software.com): start a free 14-day trial, no card needed, then connect your AI app below.

This is a **hosted (remote) MCP server**. There is nothing to install or run: you paste one URL into your AI app and sign in.

```
https://www.construction-company-software.com/api/mcp
```

- **Transport:** Streamable HTTP
- **Auth:** OAuth 2.1 with PKCE and dynamic client registration. You sign in to Construction Company Software in a browser window; no API key to copy.
- **Plans:** works on every plan, including the [14-day free trial](https://www.construction-company-software.com/signup) (no card needed).

## Connect

### Claude (claude.ai and the desktop app)
Settings → Connectors → **Add custom connector**. Name it `Construction Company Software`, paste the URL above, click **Add**, then **Connect** and sign in.

### Claude Code
```bash
claude mcp add --transport http ccs https://www.construction-company-software.com/api/mcp
```
Then run `/mcp`, pick `ccs` and sign in.

### ChatGPT
Settings → Apps & Connectors → Advanced settings → turn on **Developer mode** (on Business/Enterprise plans an admin may need to allow it). Then **Create** a connector: paste the URL as the MCP server URL, choose **OAuth**, and click **Create**.

### Cursor
Add to `~/.cursor/mcp.json` (or `.cursor/mcp.json` in a project):
```json
{
  "mcpServers": {
    "construction-company-software": {
      "url": "https://www.construction-company-software.com/api/mcp"
    }
  }
}
```

### VS Code (GitHub Copilot)
Add to `.vscode/mcp.json`:
```json
{
  "servers": {
    "construction-company-software": {
      "type": "http",
      "url": "https://www.construction-company-software.com/api/mcp"
    }
  }
}
```

### Windsurf and other clients
Any client that supports remote MCP servers with OAuth works with the URL above. For a client that only runs local (stdio) servers, bridge it with [`mcp-remote`](https://www.npmjs.com/package/mcp-remote):
```json
{
  "mcpServers": {
    "construction-company-software": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "https://www.construction-company-software.com/api/mcp"]
    }
  }
}
```

### Scripts and automation (API key)
For scripts or clients that can't sign in, a company admin creates a key in **Settings → API & webhooks** and the client sends `Authorization: Bearer <key>`. API keys are part of the Whole Company plan (and the trial). Signing in, as above, works on every plan.

## When you sign in
1. A Construction Company Software window opens. Sign in the way you always do (password, email link, Google, two-step code).
2. If you work for more than one company, pick one.
3. Choose **Read only** (look things up) or **Read + propose changes** (also draft schedule changes and RFIs for you to approve), then click **Allow**.

The assistant acts as you: it sees only the jobs and tools you can see in the app. You can disconnect it any time in **Settings → AI & privacy**; admins can see and disconnect everyone's.

## Tools

| Tool | What it does | Changes data? |
|---|---|---|
| `list_projects` | Lists your jobs with status, dates and progress | No |
| `search` | Keyword search across jobs, tasks, contacts, files, RFIs, punch items and documents | No |
| `get_schedule` | A job's schedule: tasks, dates, dependencies and who's assigned | No |
| `critical_path` | The tasks that can't slip without moving the finish date | No |
| `float_report` | How many days of wiggle room each task has | No |
| `schedule_delays` | What's behind and how far | No |
| `sub_status` | Which subs are booked on which tasks, and whether they confirmed, declined, proposed a new date or haven't answered | No |
| `budget_status` | Budget vs. actual by cost category: committed, actual, projected, billed and projected profit | No |
| `list_rfis` | Open and answered RFIs (questions to the architect) | No |
| `daily_logs` | Daily logs in a date range: work performed, crew counts, delays, weather and notes | No |
| `punch_list` | Open punch list items by job | No |
| `list_submittals` | Product approvals (submittals) and their status | No |
| `search_documents` | Finds passages in a job's specs, drawings and RFIs, with page numbers to cite | No |
| `schedule_risks` | The next 7 days' risks: late work, unconfirmed or declined subs, weather on outdoor work, no wiggle room, overdue RFIs and punch items | No |
| `propose_schedule_changes` | Drafts a schedule change and shows what would move | Proposal only |
| `draft_rfi` | Drafts an RFI for you to review | Draft only |
| `apply_proposal` | Sends you a link to approve a proposal in the app (applies it directly only with an API key set to allow that) | Yes, after approval |

**Nothing changes until you approve it.** When you ask "push drywall on the Lee job two days", the assistant creates a proposal and gives you a link. You review what moves and tap **Approve** in the app. Text hidden in a note, RFI or document can't trick the assistant into changing your schedule.

## Example prompts
- "What's on the critical path for the Lee kitchen?"
- "Which subs haven't confirmed for next week?"
- "Summarize yesterday's daily logs across all jobs."
- "Push drywall on the Lee job two days for the failed inspection."
- "Draft an RFI asking the architect about the window header size on the Patel addition."

## Privacy and security
- What the server returns goes to the AI app you connected, under that app's own terms. Choose **Read only** if the assistant should only look things up.
- AI features, the MCP server included, only work while AI is turned on for your company (**Settings → AI & privacy**).
- Privacy policy: https://www.construction-company-software.com/privacy
- Report a security issue: see [SECURITY.md](SECURITY.md).

## Support
- Docs: https://www.construction-company-software.com/ai/mcp
- Help center: https://www.construction-company-software.com/help
- Email: support@construction-company-software.com

## About this repository
The server is hosted by Construction Company Software; this repository holds its public listing: this README, the [`server.json`](server.json) entry for the [official MCP Registry](https://registry.modelcontextprotocol.io), and the logo. Issues and suggestions are welcome.

## License
The contents of this repository are [MIT licensed](LICENSE). The hosted service is covered by the [Terms of Service](https://www.construction-company-software.com/terms).
