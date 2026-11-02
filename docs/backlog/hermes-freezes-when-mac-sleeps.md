---
worth: yes
where: docker-compose.yaml:3
added: 2026-11-02
---
# Hermes freezes mid-run when the MacBook sleeps

Hermes runs in Docker on a MacBook that sleeps after 1 min idle (`pmset sleep 1` on AC and battery,
mostly on battery overnight). Cron jobs fire during a ~25s DarkWake; when the Mac re-sleeps the VM
freezes, and on wake the Codex stream is dead → `waiting for model response` /
`session_turn_lease_lost`, plus Telegram DNS errors. `duties-brief` (~13s) usually fits in the wake
window; `morning-digest` (minutes of web search) failed every run 2026-10-30..11-02, e.g. 11-02 started
13:25:15, Mac slept 13:25:35, woke 13:42:03, job failed 13:43:12 (`pmset -g log` vs
`~/.hermes/logs/agent.log`).

Fix: move the gateway to an always-on host (small VPS or home mini-server) with `~/.hermes` copied over.
Stopgap, not a fix: `sudo pmset -c sleep 0` with the Mac on charge and the lid open overnight.
