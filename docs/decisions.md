# Зафиксированные решения

Обновлено: 2026-10-05. Менять только по явной просьбе владельца.

| ID | Решение | Почему |
|----|---------|--------|
| D1 | Хост = **домашний** Windows-ноут | Рабочий = Alabuga + секреты + Happ; не смешивать trust-boundary |
| D2 | Рабочий ноут = **не** runtime | CLI мог остаться от пробы; daemon/автозапуск сняты |
| D3 | Этот git-репо = конфиг/docs, не форк upstream | Upstream: https://github.com/openclaw/openclaw |
| D4 | Remote: `https://github.com/fuzlik/openclaw` (private) | Аккаунт GitHub: `fuzlik` |
| D5 | Gateway: `mode=local`, `bind=loopback`, port `18789` | Не светить наружу |
| D6 | Auth gateway: token (сгенерировать локально) | Control UI / клиенты с токеном |
| D7 | Первый канал: **Telegram** (long polling) | Быстрее всего с телефона |
| D8 | DM policy: **pairing**, approve только владельца | Чужие DM не исполнять |
| D9 | Groups: requireMention / allowlist | Не болтать в чужих чатах |
| D10 | Workspace: `<repo>/workspace` | Память рядом с репо; runtime state в `~/.openclaw` |
| D11 | Модель: любой из Anthropic / OpenAI / OpenRouter — что даст владелец | Model-agnostic |
| D12 | Cursor остаётся IDE для кода/Figma/TeamStorm | OpenClaw = always-on + чаты + память |
| D13 | Не подключать Alabuga MCP/токены в OpenClaw | Корп-контур отдельно |
| D14 | Companion (Windows Hub) — опционально | CLI+Gateway достаточно; Companion = tray/UI |
| D15 | Native Windows OK; WSL2 — fallback если native daemon ломается | Docs рекомендуют WSL2 при проблемах |
| D16 | Autostart: Scheduled Task; иначе Startup `.lnk` на `~/.openclaw/gateway.cmd` | Как в docs |
| D17 | Tools: полный доступ **только дома** на личной машине | На работе — запрещено |
| D18 | Версия ориентир: OpenClaw **2026.9.x+** (stable latest) | На работе ставили 2026.9.8 |
| D19 | Язык общения с владельцем: русский | Команды/логи — как есть |
| D20 | Secrets: env или `~/.openclaw`, никогда git | `.gitignore` обязателен |

## Отвергнуто

- Shared team gateway на корп-машине
- Funnel / LAN bind без запроса
- Замена Cursor OpenClaw’ом для кодинга
