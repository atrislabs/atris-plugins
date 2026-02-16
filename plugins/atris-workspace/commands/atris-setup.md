---
name: atris-setup
description: Set up Atris authentication for integration skills (email, calendar, drive, slack, notion, slides)
---

# Atris Setup

This command helps you connect to AtrisOS so integration skills (email, calendar, drive, etc.) can work.

## Steps

1. **Check if already authenticated:**

```bash
if [ -f ~/.atris/credentials.json ]; then
  echo "Already authenticated with AtrisOS"
  cat ~/.atris/credentials.json | python3 -c "import sys,json; d=json.load(sys.stdin); print(f'User: {d.get(\"email\", \"unknown\")}')" 2>/dev/null || echo "Credentials file exists"
  exit 0
fi
```

2. **If not authenticated, guide the user:**

Tell the user:
- Open https://atris.ai/auth/cli in their browser
- Sign in with their Google account
- Copy the CLI code shown on the page
- Paste it back here

3. **Exchange the code for credentials:**

Once the user provides the code, run:

```bash
curl -s -X POST https://api.atris.ai/auth/cli/exchange \
  -H "Content-Type: application/json" \
  -d "{\"code\": \"USER_CODE_HERE\"}" \
  -o /tmp/atris_auth.json

mkdir -p ~/.atris
mv /tmp/atris_auth.json ~/.atris/credentials.json
echo "Authenticated successfully!"
```

4. **Verify by checking available integrations:**

```bash
TOKEN=$(cat ~/.atris/credentials.json | python3 -c "import sys,json; print(json.load(sys.stdin)['access_token'])")
curl -s https://api.atris.ai/integrations/status \
  -H "Authorization: Bearer $TOKEN"
```

Show the user which integrations are connected and which need to be set up at https://atris.ai/integrations.

## Notes

- No CLI install needed — this works entirely through the API
- Credentials are stored locally at ~/.atris/credentials.json
- Integration skills (email, calendar, drive, slack, notion, slides) require authentication
- Writing/design/backend skills work without authentication
