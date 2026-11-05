---
worth: yes
added: 2026-10-30
---
# daily duties briefing as a Hermes cron job

The `duties` skill (`~/.hermes/skills/duties/SKILL.md`, over the secretary CLI in
`~/.hermes/.local/bin`) answers on demand only. Add a Hermes cron job like `morning-digest` that
runs `SECRETARY_HOME=$HERMES_HOME/secretary secretary brief --json`, voices it per the skill, and
replies `[SILENT]` when `all_clear` is true, so quiet days send nothing. Decide whether it merges
into the morning digest or stays a separate message.
