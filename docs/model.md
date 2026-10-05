# Модель: OpenRouter

Решение: **D11** в `docs/decisions.md`.

## Зачем

- Один ключ → много моделей (Claude, Gemini, auto-router)
- `openrouter/auto` дешевле на heartbeat/простых задачах
- Официально поддержан OpenClaw: https://docs.openclaw.ai/providers/openrouter

## Что сделать владельцу (один раз)

1. Зайти на https://openrouter.ai/ — регистрация/логин  
2. https://openrouter.ai/keys → **Create Key**  
3. Пополнить баланс (credits) — без кредитов запросы не пойдут  
4. Дома в User env: `OPENROUTER_API_KEY=sk-or-...`  
5. **Не** путать с подпиской Cursor

## Onboard flag

```text
--auth-choice openrouter-api-key --openrouter-api-key $env:OPENROUTER_API_KEY
```

## Models

| Ref | Когда |
|-----|--------|
| `openrouter/auto` | default, повседневка |
| `openrouter/~anthropic/claude-sonnet-latest` | когда нужно качество Claude |

## Fallback

Прямой Anthropic/OpenAI — только если OpenRouter недоступен и владелец явно дал другой ключ.
