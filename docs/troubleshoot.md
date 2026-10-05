# Troubleshoot (дом)

| Симптом | Действие |
|---------|----------|
| `openclaw` not found | Обновить PATH; проверить `npm prefix -g` |
| ECONNREFUSED :18789 | Запустить `gateway.cmd` или `openclaw gateway`; проверить Startup/Task |
| Scheduled Task publish fail | Startup `.lnk` fallback (runbook §4) |
| Model errors | Проверить env API key; `openclaw doctor` |
| Telegram silent | `channels status --probe`; pairing approve; BotFather token |
| Native Windows pain | Рассмотреть WSL2 Gateway (docs Windows) — спросить владельца |
| Случайно на work PC | Стоп. Не ставить daemon. См. decisions D1 |

Логи: `%LOCALAPPDATA%\Temp\openclaw\` и `openclaw logs --follow`.
