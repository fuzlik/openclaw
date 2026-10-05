# Status

| Где | Состояние | Дата |
|-----|-----------|------|
| GitHub `fuzlik/openclaw` | private repo + docs/runbook | 2026-10-05 |
| Рабочий ноут Alabuga | проба CLI; Gateway/autostart сняты; **не целевой хост** | 2026-10-05 |
| Домашний ноут | **не установлен** — ждать выполнения `docs/runbook-home.md` | — |

## Уроки с рабочего ПК (не повторять как цель)

- Installer CLI: OK (`openclaw@2026.9.8`)
- `openclaw onboard --non-interactive` пишет конфиг/workspace
- `gateway install` / Scheduled Task на том ПК падал (`gateway.cmd` publication) — иметь Startup fallback
- Companion через winget ставился; для дома опционален
- Не держать always-on на корп-ноуте

## Модель

Выбрано: **OpenRouter** (`openrouter/auto`). Ключ ещё не создан — сделать дома на https://openrouter.ai/keys

## Следующий шаг человека

1. Аккаунт OpenRouter → Create Key → сохранить `OPENROUTER_API_KEY`
2. Telegram `@BotFather` → bot token
3. Дома: вставить `PROMPT-HOME.md` нейросети
