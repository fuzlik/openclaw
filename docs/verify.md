# Verify — Definition of Done

Отметь `[x]` после проверки на домашнем ноуте.

## CLI / runtime

- [ ] `openclaw --version` показывает 2026.9+ (или новее stable)
- [ ] Конфиг существует: `%USERPROFILE%\.openclaw\openclaw.json`
- [ ] `gateway.mode` = `local`, `gateway.bind` = `loopback`, port `18789`
- [ ] Gateway running: `openclaw gateway status` без ECONNREFUSED
- [ ] Autostart: Scheduled Task **или** Startup `OpenClaw Gateway.lnk`
- [ ] http://127.0.0.1:18789/ открывается (Control UI)

## Model

- [ ] `OPENROUTER_API_KEY` задан (User env или локальный `.env` вне git)
- [ ] Primary: `openrouter/auto` (или явно задокументирован Claude-ref)
- [ ] В Control UI / TUI тестовое сообщение получает ответ модели

## Telegram

- [ ] `openclaw channels status --probe` — telegram OK
- [ ] Pairing одобрен для владельца
- [ ] Сообщение с телефона получает ответ

## Repo / secrets

- [ ] `git status` в репо **без** `.env`, без скопированного `openclaw.json` с токенами
- [ ] Workspace = `<repo>/workspace` (или явно задокументировано иначе)
- [ ] `docs/status.md` обновлён фактом «установлено дома»

## Security

- [ ] `openclaw doctor` без критичных blocker’ов (или зафиксированы известные)
- [ ] Gateway не слушает LAN/публичный интерфейс
- [ ] Нет Alabuga-токенов в конфиге OpenClaw

## Отчёт владельцу (шаблон)

```
OpenClaw: <version>
Gateway: ok @ 127.0.0.1:18789
Autostart: task|startup|manual
Model: <provider>
Telegram: paired|pending
Осталось вручную: <...>
```
