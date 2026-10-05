# Runbook: установка на домашнем Windows

Исполнять по порядку. ОС: Windows 10/11, PowerShell 7 или Windows PowerShell 5.1.  
Официальные docs: https://docs.openclaw.ai/ · Install: https://docs.openclaw.ai/install · Windows: https://docs.openclaw.ai/platforms/windows

## 0. Preconditions

- Это **домашний** ПК (не Alabuga work laptop)
- Есть интернет
- Владелец рядом для: API-ключа модели + Telegram `@BotFather` token (если ещё нет)

Проверка:

```powershell
node -v   # нужно 24.16+ или 26.x; иначе installer поставит
git --version
```

## 1. Клон репо

```powershell
cd $env:USERPROFILE\Desktop   # или любая личная папка
git clone https://github.com/fuzlik/openclaw.git
cd openclaw
```

Если репо уже склонировано — `git pull`.

Создать workspace:

```powershell
New-Item -ItemType Directory -Force -Path .\workspace | Out-Null
Copy-Item -Force .\templates\workspace\* .\workspace\ -ErrorAction SilentlyContinue
```

## 2. Установка CLI

Без интерактивного onboard (его сделаем контролируемо):

```powershell
& ([scriptblock]::Create((iwr -useb https://openclaw.ai/install.ps1))) -NoOnboard
```

Обновить PATH в текущей сессии:

```powershell
$env:Path = [System.Environment]::GetEnvironmentVariable("Path","Machine") + ";" + [System.Environment]::GetEnvironmentVariable("Path","User")
openclaw --version
```

Ожидание: версия `2026.9.x` или новее.

Альтернатива: `npm install -g openclaw@latest` (см. docs; npm 12+ может требовать `--allow-scripts=openclaw`).

## 3. Секрет модели — OpenRouter (D11)

Владелец создаёт ключ: https://openrouter.ai/keys → Create Key.  
Положить в user env (не в git):

```powershell
# НЕ коммитить. Значение даёт владелец.
[System.Environment]::SetEnvironmentVariable("OPENROUTER_API_KEY", "<KEY>", "User")
# переоткрыть терминал или:
$env:OPENROUTER_API_KEY = [Environment]::GetEnvironmentVariable("OPENROUTER_API_KEY", "User")
```

Fallback (только если OpenRouter недоступен и владелец явно дал другой ключ): Anthropic / OpenAI — см. docs OpenClaw providers.

## 4. Onboard (non-interactive предпочтительно)

Подставь ключ и auth-choice. Workspace = этот репо.

```powershell
$repo = (Resolve-Path .).Path
$ws = Join-Path $repo "workspace"

openclaw onboard --non-interactive --accept-risk `
  --mode local `
  --gateway-bind loopback `
  --gateway-port 18789 `
  --install-daemon `
  --skip-channels `
  --skip-search `
  --workspace $ws `
  --agent-name main `
  --auth-choice openrouter-api-key `
  --openrouter-api-key $env:OPENROUTER_API_KEY
```

После onboard выставить primary model (если wizard не поставил):

```powershell
# в %USERPROFILE%\.openclaw\openclaw.json → agents.defaults.model.primary
# "openrouter/auto"
# опционально качество: "openrouter/~anthropic/claude-sonnet-latest"
```

Docs: https://docs.openclaw.ai/providers/openrouter

Если interactive проще для владельца: `openclaw onboard` и следовать D5–D11.

Если daemon (Scheduled Task) падает с ошибкой publication `gateway.cmd`:

1. Не паниковать — конфиг уже мог записаться в `%USERPROFILE%\.openclaw\openclaw.json`
2. Fallback автозапуск:

```powershell
$startup = [Environment]::GetFolderPath('Startup')
$w = New-Object -ComObject WScript.Shell
$lnk = $w.CreateShortcut((Join-Path $startup "OpenClaw Gateway.lnk"))
$lnk.TargetPath = "$env:USERPROFILE\.openclaw\gateway.cmd"
$lnk.WorkingDirectory = "$env:USERPROFILE\.openclaw"
$lnk.WindowStyle = 7
$lnk.Save()
```

3. Запуск сейчас:

```powershell
Start-Process -FilePath "$env:USERPROFILE\.openclaw\gateway.cmd" -WorkingDirectory "$env:USERPROFILE\.openclaw" -WindowStyle Hidden
```

4. Если native совсем плох → WSL2 path из https://docs.openclaw.ai/platforms/windows (отдельное решение владельца).

## 5. Проверка Gateway

```powershell
openclaw gateway status
# UI
Start-Process "http://127.0.0.1:18789/"
# или
openclaw dashboard
```

RPC должен быть reachable на `ws://127.0.0.1:18789`.

Токен gateway лежит в `%USERPROFILE%\.openclaw\openclaw.json` → `gateway.auth.token`.  
**Не** коммитить. Для Control UI использовать локально.

## 6. Выровнять конфиг под desired

Сверь `%USERPROFILE%\.openclaw\openclaw.json` с `config/openclaw.desired.json5`.  
Допиши недостающие поля (bind/loopback, telegram позже). Не копируй example token.

Рекомендуется урезать риск по желанию владельца через policy/tools — по умолчанию дома full OK (D17).

## 7. Telegram

См. `docs/telegram.md`.

## 8. Doctor + security

```powershell
openclaw doctor
openclaw security audit
```

## 9. Финал

Пройти `docs/verify.md`.  
Обновить `docs/status.md` (факт установки на доме).  
Коммитить в git **только** docs/templates/config-example — не runtime.

## Откат

```powershell
openclaw gateway stop
# убрать Startup lnk если создавали
Remove-Item (Join-Path ([Environment]::GetFolderPath('Startup')) "OpenClaw Gateway.lnk") -ErrorAction SilentlyContinue
# полный uninstall — по https://docs.openclaw.ai/ (Uninstall)
```
