# OpenClaw (личный)

Конфиг и runbook для **домашнего** OpenClaw. Не форк upstream.

| | |
|--|--|
| Upstream | https://github.com/openclaw/openclaw |
| Docs | https://docs.openclaw.ai/ |
| Этот remote | https://github.com/fuzlik/openclaw (private) |

## Дома: скажи нейросети сделать

1. Открой этот репо на **домашнем** ноуте  
2. Вставь промпт из [`PROMPT-HOME.md`](PROMPT-HOME.md)  
3. Держи рядом API-ключ модели + Telegram bot token от `@BotFather`

Агент обязан следовать [`AGENTS.md`](AGENTS.md).

## Карта docs

| Файл | Зачем |
|------|--------|
| [`AGENTS.md`](AGENTS.md) | Инструкция агенту |
| [`PROMPT-HOME.md`](PROMPT-HOME.md) | Copy-paste промпт |
| [`docs/decisions.md`](docs/decisions.md) | Зафиксированные решения |
| [`docs/runbook-home.md`](docs/runbook-home.md) | Пошаговая установка |
| [`docs/telegram.md`](docs/telegram.md) | Telegram |
| [`docs/security.md`](docs/security.md) | Границы |
| [`docs/verify.md`](docs/verify.md) | DoD / чеклист |
| [`docs/owner.md`](docs/owner.md) | Кто владелец |
| [`docs/status.md`](docs/status.md) | Что уже сделано |
| [`config/openclaw.desired.json5`](config/openclaw.desired.json5) | Целевая форма конфига |
| [`templates/workspace/`](templates/workspace/) | Стартовые SOUL/USER/IDENTITY |

## Главное решение

**Runtime только дома.** Рабочий ноут Alabuga — не хост (см. decisions D1–D2).
