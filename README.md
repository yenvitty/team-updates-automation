# Team Updates Automation

> Sanitized n8n workflow for automating daily team progress updates and dashboard generation.

[![n8n Workflow](https://img.shields.io/badge/n8n-Workflow-blue?style=flat-square)](https://n8n.io)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)
[![Node.js](https://img.shields.io/badge/Node.js-18+-green?style=flat-square)](https://nodejs.org)

## Features

- **Daily Update Form**: Interactive HTML form for team members to submit daily progress (tasks, pending uploads, notes).
- **Team Dashboard**: Real-time aggregated view of all team members' updates.
- **Google Sheets Integration**: Automatic storage and retrieval of updates.
- **Google Chat Notifications**: Scheduled reminders and status updates via Google Chat.
- **GitLab Integration**: Automatic fetching of commit history per user.
- **Dark/Light Theme**: Toggle between themes with CSS variables.
- **Responsive Design**: Works on desktop and mobile devices.

## Architecture

```
┌─────────────────┐     ┌──────────────────┐     ┌─────────────────┐
│  Webhook Trigger │────▶│  n8n Workflow     │────▶│  Google Sheets  │
│  (Form/Dashboard)│     │  (Orchestrator)   │     │  (Storage)      │
└─────────────────┘     └──────────────────┘     └─────────────────┘
                                │
                                ├────▶ Google Chat (Notifications)
                                │
                                └────▶ GitLab API (Commit History)
```

## Prerequisites

- [n8n](https://n8n.io) instance (self-hosted or cloud)
- Google Sheets API credentials
- Google Chat Webhook URL
- GitLab API token (optional, for commit history)
- Node.js 18+ (for local testing)

## Setup

1. **Import the Workflow**

   Open your n8n instance and import `workflow.json`:

   ```
   File > Import from File > workflow.json
   ```

2. **Configure Credentials**

   Update the following credentials in the imported workflow:

   | Connection | Description | Placeholder |
   |---|---|---|
   | Google Sheets | Sheet ID and service account credentials | `YOUR_SHEET_ID` |
   | Google Chat | Webhook URL for notifications | `YOUR_CHAT_WEBHOOK_URL` |
   | GitLab | API token for commit history | `YOUR_GITLAB_TOKEN` |

3. **Update Webhook URLs**

    Replace all instances of `${N8N_BASE_URL}/webhook/...` with your n8n webhook URLs.

4. **Activate the Workflow**

   Toggle the workflow switch to `Active` in n8n.

## Schedule

| Trigger | Time (IST) | Purpose |
|---|---|---|
| Evening Reminder | 6:30 PM | Remind team to submit updates |
| Dashboard Update | 8:00 PM | Generate daily dashboard |
| Yesterday Summary | 9:45 AM | Send previous day's summary |

## License

Distributed under the MIT License. See [LICENSE](LICENSE) for more information.

## Target Roles

- **Engineering Managers**: Monitor team progress and identify blockers.
- **Team Leads**: Track individual contributions and pending uploads.
- **Developers**: Submit daily updates and view team dashboard.
- **QA/Testers**: Track testing progress and pending uploads.

## Disclaimer

This is a sanitized version of the original workflow. All sensitive credentials, webhook URLs, and personal data have been removed. Configure the workflow with your own credentials before use.
