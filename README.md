# daily-refresh

A personal homepage that shows Justin's daily morning brief — refreshed automatically every morning by a scheduled Claude task.

**Live site:** https://jthcreative.github.io/daily-refresh/

## How it works

1. A scheduled Claude Code task ("Morning brief → homepage site") fires every day at 16:00 UTC (9 AM Pacific in summer, 8 AM in winter).
2. The task runs the `/morning` skill unattended: it gathers from Google Calendar, Gmail, Google Drive, and Robinhood, then renders the brief as a single self-contained HTML page (including the extra sections: stock market analysis and LinkedIn job opportunities).
3. The task replaces `index.html` in this repo and pushes to the `claude/daily-briefing-homepage-bhj5gc` branch.
4. The GitHub Actions workflow in `.github/workflows/pages.yml` deploys the page to GitHub Pages on every push — the first run also enables Pages automatically.

No manual steps are needed each morning: just open the site.

## Files

- `index.html` — the current day's brief (overwritten daily; fully self-contained, fonts embedded)
- `.github/workflows/pages.yml` — Pages deploy workflow
- `.nojekyll` — serves the file as-is, skipping Jekyll

## Changing the schedule or content

Ask Claude in the session that manages this repo, e.g. "change the morning brief to weekdays only" or "add a weather section" — it will update the scheduled task's prompt or cron accordingly.
