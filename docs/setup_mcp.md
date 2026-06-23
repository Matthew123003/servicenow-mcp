# ServiceNow MCP Setup Checklist

## What You Need to Gather First

Before starting, have these ready:

- **Instance URL** → looks like `https://yourcompany.service-now.com`
- **Username** → your ServiceNow login username
- **Password** → your ServiceNow login password

> 💡 Ask your ServiceNow admin if you don't have these. Use a dedicated service account, not your personal login if possible.

---

## Your Project Path

/Users/matthew123003/JavaIntelliJIDEAProjects/servicenow-mcp


## Your Python Path (already confirmed)

/Users/matthew123003/JavaIntelliJIDEAProjects/servicenow-mcp/.venv/bin/python


---

## Step 1: Create the `.env` File

In the root of your project, create a file called `.env` and add:

SERVICENOW_INSTANCE_URL=https://your-instance.service-now.com
SERVICENOW_USERNAME=your-username
SERVICENOW_PASSWORD=your-password
SERVICENOW_AUTH_TYPE=basic


Replace the three values with your real credentials.

---

## Step 2: Create the Claude Desktop Config File

Open this file on your Mac (create it if it doesn't exist):

~/Library/Application Support/Claude/claude_desktop_config.json


To open it from terminal:

```bash
open -a TextEdit ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

Paste this content in exactly — replacing the three placeholder values with your real credentials:

```json
{
  "mcpServers": {
    "ServiceNow": {
      "command": "/Users/matthew123003/JavaIntelliJIDEAProjects/servicenow-mcp/.venv/bin/python",
      "args": ["-m", "servicenow_mcp.cli"],
      "env": {
        "SERVICENOW_INSTANCE_URL": "https://your-instance.service-now.com",
        "SERVICENOW_USERNAME": "your-username",
        "SERVICENOW_PASSWORD": "your-password",
        "SERVICENOW_AUTH_TYPE": "basic"
      }
    }
  }
}
```

---

## Step 3: Restart Claude Desktop

- Fully quit Claude Desktop with `Cmd + Q`
- Reopen it
- Look for the 🔨 hammer/tools icon in the chat input bar — that confirms the MCP is connected

---

## Step 4: Test It

Type this in Claude Desktop:

What ServiceNow tools do you have available?


Claude should list all the ServiceNow capabilities it can now access.

---

## Troubleshooting

| Symptom | Fix |
|---|---|
| No hammer icon in Claude | Check the JSON in `claude_desktop_config.json` for typos |
| Authentication error | Double-check instance URL starts with `https://` and credentials are correct |
| Claude says no tools found | Make sure you fully quit and reopened Claude Desktop |

