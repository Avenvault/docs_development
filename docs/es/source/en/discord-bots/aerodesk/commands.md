---
icon: terminal
---

# Commands

### 💻 Commands

The bot utilizes Discord's modern Slash Command architecture for clean, hidden executions.

#### `/ticketpanel`

- Permission: Admin / Owner Only
- Description: Deploys the interactive dropdown menu in the channel where the command is executed. Users interact with this panel to open their tickets based on the `categories` you defined in the config.

#### `/stats`

- Permission: Staff Role / Admin
- Description: Displays an embed containing real-time analytics pulled from your NoSQL database. Includes metrics such as:
  - Total historical tickets.
  - Currently open tickets.
  - Total automated FAQ triggers.
  - Average user review rating (stars).

