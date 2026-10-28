# AA No Reset Stats Website

Template for a stats website of Minecraft 1.16.1 All Advancements runs, like [Zesskyo's AA No Reset Log](https://zesskyo.github.io/aa-stats-no-reset-zesskyo-log/).

- The code comes from [aa-stats](https://github.com/zesskyo/aa-stats): new features reach your site automatically (daily build).
- Changes: [aa-stats CHANGELOG](https://github.com/zesskyo/aa-stats/blob/main/CHANGELOG.md)

## Setup

1. **Use this template › Create a new repository.** Any name (it's in the site's address), **Public**.
2. **Settings › Pages › Source:** GitHub Actions.
3. **Actions › Build and publish the site › Run workflow.** Wait for the green tick.
4. Open `https://<your-username>.github.io/<repository-name>/`.
5. **Set up this site** on the welcome card:
   - Sign in with a GitHub token that can only change this repository (steps on screen; stored in your browser only)
   - Name the site
   - Add your first run

## Runs

Signed in, **+ Add run**:

- **From a world:** drop the world folder. The log, ghost file and stats are read from it: date, time, 100%, deaths, seed.
  - Tick the deaths that were on purpose; add proof and notes.
  - The seed is asked for only if the log hasn't got it (`/seed` before leaving the world puts it there).
  - Hermes **0.14+** logs biomes. Older runs: the seed and ghost file let the biomes be worked out.
- **Manual** (no log): final time, 100%, splits, date. No graphs.
- **Proof:** a video link, or a screenshot (link or upload).
- **Save:** the run's page opens straight away; the site rebuilds for everyone in a minute or two.
- **Edit / delete:** *Edit* on the run's page.
- **Site settings** (bottom of the site): title, subtitle, colours.

## Files

- `logs/`: each run's `play.log`, ghost file and stats (`<number>.log`, `.ghost`, `.stats.json`)
- `runs.json`: details per run (date, seed, video, notes, …)
- `site.json`: title, subtitle, colours, any of the site's words
- `icons/`: your own icons (optional)
