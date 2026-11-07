# on-demand-game-server

On-demand Valheim and Enshrouded server on Clouding.io, controlled from Telegram.

- `/start <game>` from Telegram wakes the server
- It saves, backs up and archives itself when nobody is playing
- One server, one game at a time, switchable from the bot

## Status

Phase 1. See [docs/plan.md](docs/plan.md) for architecture, costs and decisions, and the [milestones](../../milestones) for progress.

## Technologies

| Area | Technology |
|---|---|
| Cloud | Clouding.io (cloud servers, REST API) |
| OS | Ubuntu Server LTS |
| Containers | Docker, Docker Compose |
| Game servers | SteamCMD, Wine/Proton (Enshrouded) |
| Automation | Bash, systemd services and timers |
| Bot | Python, Telegram Bot API, Clouding API |
| Hardware | Raspberry Pi Zero W |
| Networking | DuckDNS (dynamic DNS), Clouding firewall, Steam A2S queries |
| Monitoring (optional) | Dynatrace (OneAgent, log ingestion, metrics API, Workflows) |

## Structure

| Folder | Runs on | Contents |
|---|---|---|
| `bot/` | Raspberry Pi Zero W | Telegram bot |
| `server/` | Clouding server (Ubuntu + Docker) | Game containers, boot, idle, backup and archive scripts |
| `dynatrace/` | Dynatrace | Workflow definitions (optional) |
| `docs/` | — | Plan, setup guides, troubleshooting |

## Games

| Game | Ports (UDP) |
|---|---|
| Valheim | 2456–2458 |
| Enshrouded | 15636–15637 |

## Acknowledgements

Planned and built with the help of [Claude](https://claude.ai) by Anthropic, used for architecture design, cost analysis and documentation.
