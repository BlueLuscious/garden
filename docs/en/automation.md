# Repository Automation

Repository workflows and the configuration needed to use them.

## Discord notifications

[Garden Discord Notifications](../../.github/workflows/discord.yaml) reports commits, branch
creation through push, branch deletion and pull-request activity. The workflow owns exact filters.

Set the repository Actions secret `GARDEN_DISCORD_WEBHOOK` to the complete Discord webhook URL.
Without an available secret, notifications are skipped.

After integration into `master`, check an eligible run under **Actions → Garden Discord
Notifications** and confirm the message in Discord. A successful run may have skipped the send.

Notifications are operational automation, not a build or verification gate.
