# Atris Workspace Plugin

Brings Atris CLI skills into the Cowork desktop app.

## Setup

1. Install this plugin in Cowork
2. Run `/atris-setup` to authenticate and connect integrations
3. Start using skills — they trigger automatically based on your requests

## Included Skills (16)

- **atris**: Atris workflow enforcement for repos using atris/ (MAP, TODO, journal, features, plan-do-review, anti-slop)
- **autopilot**: PRD-driven autonomous execution - give it a task, it loops until done Triggers on "autopilot", "autonomous", "get it done", "finish this", "ship it"
- **backend**: Backend architecture policy
- **calendar**: Google Calendar integration via AtrisOS API
- **atris**: Codebase intelligence — generates structured navigation maps with file:line references so agents stop re-scanning the same files every session
- **copy-editor**: Detects AI writing patterns and fixes them
- **design**: Frontend aesthetics policy
- **drive**: Google Drive integration via AtrisOS API
- **email-agent**: Gmail integration via AtrisOS API
- **memory**: Search and reason over Atris journal history
- **meta**: Metacognition skill for AI agents
- **notion**: Notion integration via AtrisOS API
- **skill-improver**: Audit and improve Claude skills against the Anthropic skill guide
- **slack**: Slack integration via AtrisOS API
- **slides**: Google Slides integration via AtrisOS API
- **writing**: Essay writing skill

## Requirements

- [Atris CLI](https://www.npmjs.com/package/atris) (`npm install -g atris`)
- AtrisOS account (free at https://atris.ai)

## Learn More

- Docs: https://github.com/atrislabs/atris
- CLI help: `atris help`
