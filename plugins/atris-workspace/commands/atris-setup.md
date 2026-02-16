---
description: Set up Atris authentication and connect integrations (Gmail, Calendar, Slack, Notion, Drive)
allowed-tools: Bash, Read
---

# Atris Setup

Run the following steps to bootstrap Atris for this workspace.

## Step 1: Check if Atris CLI is installed

```bash
command -v atris || npm install -g atris
```

If the install fails, tell the user to run `npm install -g atris` manually.

## Step 2: Authenticate with AtrisOS

```bash
atris whoami
```

If not logged in, run:

```bash
atris login
```

This is interactive — the user will need to complete OAuth in their browser and paste the CLI code. Guide them through it.

## Step 3: Check integration status

After login, check which integrations are connected:

```bash
TOKEN=$(node -e "console.log(require('$HOME/.atris/credentials.json').token)")

echo "=== Gmail ==="
curl -s "https://api.atris.ai/api/integrations/gmail/status" -H "Authorization: Bearer $TOKEN"

echo "\n=== Google Calendar ==="
curl -s "https://api.atris.ai/api/integrations/google-calendar/status" -H "Authorization: Bearer $TOKEN"

echo "\n=== Slack ==="
curl -s "https://api.atris.ai/api/integrations/slack/status" -H "Authorization: Bearer $TOKEN"

echo "\n=== Notion ==="
curl -s "https://api.atris.ai/api/integrations/notion/status" -H "Authorization: Bearer $TOKEN"

echo "\n=== Google Drive ==="
curl -s "https://api.atris.ai/api/integrations/google-drive/status" -H "Authorization: Bearer $TOKEN"
```

## Step 4: Connect missing integrations

For any integration that shows `"connected": false`, guide the user through the OAuth flow:

1. Call the integration's `/start` endpoint to get an auth URL
2. Have the user open the URL in their browser
3. After authorizing, confirm the connection by re-checking status

Tell the user which integrations are connected and which still need setup. They can connect more later by running `/atris-setup` again.
