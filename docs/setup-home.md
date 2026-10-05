# Установка на домашнем ноуте (Windows)

## 1. Клон

```powershell
git clone https://github.com/fuzlik/openclaw.git
cd openclaw
```

## 2. CLI

```powershell
& ([scriptblock]::Create((iwr -useb https://openclaw.ai/install.ps1))) -NoOnboard
```

Или Companion из Start / winget: `OpenClaw.OpenClawCompanion`.

## 3. Onboard

```powershell
openclaw onboard
```

- Mode: **local**
- Bind: **loopback**
- Auth: API-ключ (Anthropic / OpenAI / OpenRouter) — только на доме
- Daemon: да (Scheduled Task или Startup)

Workspace можно указать в этот репо: `...\openclaw\workspace`.

## 4. Telegram

В onboard или позже — канал Telegram (pairing). Gateway не открывать в LAN без необходимости.

## 5. Проверка

```powershell
openclaw --version
openclaw doctor
openclaw gateway status
openclaw dashboard
```

UI: http://127.0.0.1:18789/

## Заметки с рабочего ПК

На рабочем ноуте CLI/Companion могли ставиться для пробы — Gateway и автозапуск сняты. На работе OpenClaw не гонять.
