# scriptcue-reminders

Cloud-based reminder system for the ScriptCue organic content calendar. Runs on GitHub Actions (independent of any local machine), sends Telegram nudges at scheduled times.

## How it works
- `.github/workflows/reminder.yml` runs every 15 min (UTC) and sends any reminder in `schedule.json` whose time falls in the current window.
- `schedule.json` holds upcoming reminders: `{ "at": "<ISO8601 with offset>", "text": "<message>" }`.
- Telegram bot token + chat ID are stored as encrypted GitHub Actions **secrets** (`TELEGRAM_BOT_TOKEN`, `TELEGRAM_CHAT_ID`) — never in this repo.

## Add/change a reminder
Edit `schedule.json` and push. The next 15-min run picks it up.

## Manual test
Actions tab → "ScriptCue Reminder" → Run workflow → enter a `test_message` → it sends immediately.

_No secrets live in this repo. The Telegram bot only sends reminder messages to one chat._
