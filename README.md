# Print Buddy Notify

Notifications for Printer Buddy: a message when a print starts, pauses, finishes or fails, when a printer goes
offline or Klipper shuts down, and when the AI sees a problem. Installed and updated by Printer Buddy's `install.sh`.

## Services

| Service | Level |
|---|---|
| ntfy | basic, advanced |
| Discord | basic, advanced |
| Telegram | advanced |
| Pushover | advanced |
| Email (SMTP) | advanced |

The level is Printer Buddy's `PB_NOTIFY` setting (installer: Notifications). Telegram, Pushover and email settings are
ignored while the level is basic.

## Events

started, paused, resumed, finished, failed, cancelled, offline (a printer dropped out mid-print), shutdown (Klipper
shut down), plus AI alerts. Advanced also sends progress updates every 10, 20, 25, 33 or 50% (default 25%; 0 turns them off).

## Settings

Services, events, the snapshot and the progress step are saved in Printer Buddy (Settings → Alerts). A snapshot is
attached by default. `NTFY_URL`, `NTFY_TOKEN`, `DISCORD_WEBHOOK` and `NOTIFY_EVENTS` set the defaults.

## Packages

`tiers.json` builds `print-buddy-notify-basic.tar.gz` and `print-buddy-notify-advanced.tar.gz`. Both hold `pb_notify`;
the level only changes how it behaves. The installer extracts `pb_notify/__init__.py` as `app/core/notify.py`.
A nightly build runs every day at 06:00 (UTC), and a `v*` tag publishes a stable release into the Printer Buddy repo.
