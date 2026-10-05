# OpenClaw (личный)

Конфиг и runbook для **домашнего** OpenClaw. Не форк upstream.

| | |
|--|--|
| Upstream | https://github.com/openclaw/openclaw |
| Docs | https://docs.openclaw.ai/ |
| Этот remote | https://github.com/fuzlik/openclaw (private) |

## API модели (зафиксировано)

| | |
|--|--|
| Провайдер | **OpenRouter** |
| Env | `OPENROUTER_API_KEY` |
| Primary | `openrouter/auto` |
| Качество | `openrouter/~anthropic/claude-sonnet-latest` |
| Ключ | https://openrouter.ai/keys |
| Решение | `docs/decisions.md` → **D11**, детали → `docs/model.md` |

Прямой Anthropic/OpenAI — только fallback, не default.

## Дома: скажи нейросети сделать

1. Открой этот репо на **домашнем** ноуте  
2. Вставь промпт из [`PROMPT-HOME.md`](PROMPT-HOME.md)  
3. Держи рядом: **`OPENROUTER_API_KEY`** + Telegram bot token от `@BotFather`

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
| [`docs/model.md`](docs/model.md) | OpenRouter — ключ и модели |
| [`docs/owner.md`](docs/owner.md) | Кто владелец |
| [`docs/status.md`](docs/status.md) | Что уже сделано |
| [`config/openclaw.desired.json5`](config/openclaw.desired.json5) | Целевая форма конфига |
| [`templates/workspace/`](templates/workspace/) | Стартовые SOUL/USER/IDENTITY |

## Главное решение

**Runtime только дома.** Рабочий ноут Alabuga — не хост (см. decisions D1–D2).
