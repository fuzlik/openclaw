# OpenClaw

Личный self-hosted AI-ассистент (OpenClaw Gateway).

- Сайт: https://openclaw.ai/
- Docs: https://docs.openclaw.ai/
- Upstream: https://github.com/openclaw/openclaw

## Назначение этого репо

Конфиг, skills, заметки по установке и ограничениям — **не** форк upstream.
Отделено от рабочего _контекст / TeamStorm / Alabuga.

## Роль vs Cursor

| Cursor | OpenClaw |
|--------|----------|
| Код, Figma, TeamStorm MCP | Telegram / always-on / память |
| IDE loop | Gateway вне IDE |

## Безопасность

- Один trust-boundary на gateway (только владелец).
- Не класть сюда .env, токены storm/gitlab, ключи моделей.
- Секреты только локально, в .gitignore.

## Статус

Инициализация репозитория. Установка Gateway — следующим шагом.
