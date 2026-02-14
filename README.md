# OpenHearth — Group-Native AI Assistant

<p align="center">
  <a href="https://github.com/kylebeee/openhearth/releases"><img src="https://img.shields.io/github/v/release/kylebeee/openhearth?include_prereleases&style=for-the-badge" alt="GitHub release"></a>
  <a href="https://discord.gg/openhearth"><img src="https://img.shields.io/badge/Discord-Join-5865F2?logo=discord&logoColor=white&style=for-the-badge" alt="Discord"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=for-the-badge" alt="MIT License"></a>
</p>

**OpenHearth** is a group-native AI assistant built for multi-party coordination. It connects your group across WhatsApp, Telegram, Slack, Discord, Signal, iMessage, and more — with built-in member identity, privacy layers, and configurable autonomy.

Where most AI assistants are single-user, OpenHearth is designed from the ground up for **families, teams, and communities**. The Hearth system gives every member a persistent identity across channels, enforces privacy boundaries, and lets the group control how autonomous the assistant can be in different domains.

[Docs](https://docs.openhearth.ai) · [Getting Started](https://docs.openhearth.ai/start/getting-started) · [Discord](https://discord.gg/openhearth)

---

## Hearth — Group Coordination

The Hearth subsystem is what makes OpenHearth group-native:

- **Member Identity** — Each person gets a stable identity across all channels. Message from WhatsApp, reply on Telegram — OpenHearth knows it's you.
- **Privacy Layers** — Context is scoped as `public`, `subgroup`, `private`, or `agent-inferred`. Private DM content is never attributed in group contexts.
- **Communication Principles** — OpenHearth is infrastructure, not an intermediary. It aggregates group state and provides structured tools (polls, schedules, checklists) instead of playing telephone between members.
- **Configurable Autonomy** — Set per-domain autonomy levels: `passive`, `suggest`, `ask-first`, or `autonomous`. Let it handle scheduling autonomously but only suggest for spending.
- **Agent Tools** — `hearth_members`, `hearth_member_info`, `hearth_context_check`, `hearth_context_note`

---

## Quick Start

```bash
# Install
npm install -g openhearth
# or: pnpm add -g openhearth

# Run the onboarding wizard
openhearth onboard

# Start the gateway
openhearth gateway start
```

The wizard walks you through setting up channels, workspace, and your first Hearth group.

---

## Supported Channels

| Channel         | Status    |
| --------------- | --------- |
| WhatsApp        | Stable    |
| Telegram        | Stable    |
| Discord         | Stable    |
| Slack           | Stable    |
| Signal          | Stable    |
| iMessage        | Stable    |
| Google Chat     | Stable    |
| Microsoft Teams | Stable    |
| Matrix          | Extension |
| IRC             | Extension |
| WebChat         | Built-in  |

Plus voice on macOS/iOS/Android and a live Canvas UI.

---

## Architecture

```
Channels (WhatsApp, Telegram, ...)
    ↓
  Gateway (routing, sessions, message processing)
    ↓
  Hearth (member identity, privacy, autonomy)
    ↓
  Agent (LLM, tools, skills, memory)
```

The Gateway is the control plane. Hearth sits between inbound messages and the agent, resolving member identity, classifying privacy layers, and injecting group context into the system prompt.

---

## Configuration

Minimal `openhearth.json`:

```json
{
  "hearth": {
    "enabled": true,
    "groups": {
      "whatsapp:group:GROUPID@g.us": {
        "name": "Family",
        "members": [
          {
            "name": "Kyle",
            "role": "owner",
            "timezone": "America/Chicago",
            "identities": [
              { "channel": "whatsapp", "id": "15551234567" },
              { "channel": "telegram", "username": "kyle" }
            ]
          }
        ],
        "privacy": {
          "defaultLayer": "public",
          "domainRules": [
            { "domain": "health", "layer": "private" },
            { "domain": "finances", "layer": "private" }
          ]
        },
        "autonomy": {
          "domains": [
            { "domain": "scheduling", "level": "autonomous" },
            { "domain": "spending", "level": "ask-first" }
          ]
        }
      }
    }
  }
}
```

---

## Development

```bash
git clone https://github.com/kylebeee/openhearth.git
cd openhearth
pnpm install
pnpm build
pnpm test
```

Requires Node.js >= 22.12.0 and pnpm.

---

## Forked From

OpenHearth is forked from [OpenClaw](https://github.com/openclaw/openclaw) by Peter Steinberger. OpenClaw is an excellent single-user AI gateway — OpenHearth extends it with group-native coordination features.

---

## License

MIT — see [LICENSE](LICENSE).
