# Telegram

Docs: https://docs.openclaw.ai/channels/telegram · Setup: https://docs.openclaw.ai/channels/telegram/setup

## Цель

Бот в Telegram → OpenClaw Gateway. DM только после pairing владельца.

## Шаги

### 1. Создать бота (владелец, вручную)

1. Telegram → `@BotFather` (точно этот handle)
2. `/newbot` → имя и username
3. Сохранить token (`123456:ABC...`)

Токен **не** коммитить. Можно в user env: `TELEGRAM_BOT_TOKEN`.

### 2. Добавить канал

```powershell
openclaw channels add --channel telegram --token $env:TELEGRAM_BOT_TOKEN
```

Или руками в `%USERPROFILE%\.openclaw\openclaw.json`:

```json5
{
  channels: {
    telegram: {
      enabled: true,
      botToken: "<FROM_ENV_OR_LOCAL>",
      dmPolicy: "pairing",
      groups: { "*": { requireMention: true } },
    },
  },
}
```

Предпочтение: token через env / tokenFile, не plaintext в git.

### 3. Gateway должен быть запущен

```powershell
openclaw channels status --probe
```

### 4. Pairing

1. Владелец пишет боту любое сообщение в Telegram
2. На ПК:

```powershell
openclaw pairing list telegram
openclaw pairing approve telegram <CODE>
```

Код живёт ~1 час.

### 5. Groups (опционально, позже)

- Privacy mode BotFather: `/setprivacy` — если нужны все сообщения группы
- Allowlist group id + allowFrom user id
- По умолчанию: requireMention

## Не делать

- Не ставить `dmPolicy: open` без явной просьбы
- Не шарить bot token
- Webhook наружу не нужен (long polling default)
