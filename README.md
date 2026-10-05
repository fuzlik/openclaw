# OpenClaw

Личный self-hosted AI-ассистент (OpenClaw Gateway).

- Сайт: https://openclaw.ai/
- Docs: https://docs.openclaw.ai/
- Upstream: https://github.com/openclaw/openclaw

## Где ставить

**Домашний ноут** — основной хост (Gateway + Telegram + always-on).  
**Рабочий ноут (Alabuga)** — не использовать: корп-контур, Happ/VPN, секреты TeamStorm.

Это репо — конфиг и заметки. Runtime живёт в `~/.openclaw` на домашней машине.

## Роль vs Cursor

| Cursor (работа) | OpenClaw (дом) |
|--------|----------|
| Код, Figma, TeamStorm MCP | Telegram / always-on / память |
| IDE loop | Gateway вне IDE |

## Безопасность

- Один trust-boundary на gateway (только ты).
- Не класть сюда `.env`, токены storm/gitlab, ключи моделей.
- Секреты только локально на домашнем ноуте.

## Быстрый старт дома

См. [docs/setup-home.md](docs/setup-home.md).
