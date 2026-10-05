# Безопасность

## Trust model

Один gateway = один trust-boundary = **только владелец** (и доверенные люди, которых он явно добавит).  
OpenClaw — не multi-tenant для чужих.

## Обязательные настройки

| Параметр | Значение |
|----------|----------|
| `gateway.bind` | `loopback` |
| `gateway.mode` | `local` |
| Telegram `dmPolicy` | `pairing` |
| Groups | mention / allowlist |
| Публичный интернет | выкл, пока не попросили |

## Запрещено класть в OpenClaw / этот репо

- `Работа/_контекст/.env`, токены storm / gitlab Alabuga
- Happ / VPN конфиги
- Любые корп-пароли и cookie
- API-ключи в git (только `.env.example` без значений)

## Разрешено на домашнем хосте

- Shell / files / browser в рамках личной машины
- Telegram bot token локально
- Model API keys локально (`env` или `~/.openclaw`)

## Audit

После установки:

```powershell
openclaw doctor
openclaw security audit
```

Чинить очевидное через `openclaw doctor --fix` только если понимаешь diff.

## Инцидент

Если токен/ключ утёк в git или чат: ротация ключа у провайдера, `git filter`/новый ключ, перевыпуск Telegram bot при необходимости.
