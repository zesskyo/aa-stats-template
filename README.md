# AA No Reset stats website

Make your own stats website for All Advancements No Reset runs, like
[Zesskyo's](https://zesskyo.github.io/aa-stats-no-reset-zesskyo-log/). Everything happens on github.com,
with nothing to install.

Your website keeps only your runs. The code comes from [aa-stats](https://github.com/zesskyo/aa-stats),
so **new features show up on your site automatically** (within a day).

## Set it up (once)

1. At the top of this page, click **Use this template → Create a new repository**.
   Give it any name (e.g. `aa-stats`) and keep it **Public**.
2. In your new repository, go to **Settings → Pages** and set **Source** to **GitHub Actions**.
3. Open `site.json`, click the pencil, and put your name in:
   ```json
   {
     "siteTitle": "AA No Reset Solo",
     "siteSubtitle": "(Your Name's Log)"
   }
   ```
   Click **Commit changes**. Any other words on the site can be changed here too: copy a name from
   [text.js](https://github.com/zesskyo/aa-stats/blob/main/src/text.js), e.g. `"colTime": "Time"`.
4. Go to the **Actions** tab and wait for **Build and publish the site** to go green (about a minute).
   Your site is at `https://<your-username>.github.io/<repository-name>/`.

## Add a run

1. Open the `logs` folder, click **Add file → Upload files**, and upload the run's Hermes `play.log`
   renamed to the run number: `1.log`, then `2.log`, …
   (GitHub uploads are limited to 25 MB per file.)
2. Optional: for elytra distance, also upload the world's `stats/<uuid>.json` as `1.stats.json`.
3. Optional: add details in `runs.json`:
   ```json
   {
     "1": {
       "date": "2026-09-24",
       "seed": "-6932149389784936231",
       "video": "https://youtu.be/...",
       "notes": "Jungle spawn, good nether…",
       "intentionalDeaths": [1, 2]
     }
   }
   ```
   `intentionalDeaths` are death numbers (1st, 2nd, …) that shouldn't count as real deaths. Deaths after
   The End... Again... are counted as intentional automatically; `notIntentionalDeaths` overrides that.
   `elytraKm` sets elytra distance by hand if you don't have the stats file.

The site rebuilds by itself after every change (see the **Actions** tab).

## A run without a Hermes log

Just add it to `runs.json` with whatever you have. Everything is optional:

```json
{
  "5": {
    "time": "3:41:22",
    "date": "2025-03-14",
    "seed": "-957945081170232430",
    "hundred": true,
    "splits": {"Any%": "0:38:13", "Midgame": "1:02:49", "Endgame": "3:13:34", "Post-endgame": "3:30:00"},
    "video": "https://youtu.be/...",
    "screenshot": "screenshots/5.png",
    "notes": "Before I used Hermes."
  }
}
```

- `time` is the final IGT, like `3:41:22` or `3:41:22.629`.
- `hundred`: `true` if it was 100% (80/80, with Very Very Frightening), `false` if not. Leave it out if you don't know.
- `splits` are the times on the clock: when Any% ended, and when Midgame, Endgame and Post-endgame started.

The run shows in the runs table, the PB and on its own page. There are no graphs or stats for it,
since those come from the log. Average stats only use runs with a log.

## A screenshot as proof

For any run, with or without a log: upload the image (e.g. into a `screenshots` folder) and add
`"screenshot": "screenshots/5.png"` to that run in `runs.json`. It shows on the run's page, with a camera
button next to the run in the runs table. A link to an image (`"https://…"`) works too.

## Good to know

- **Updates:** your site rebuilds once a day with the latest code. To update right away, go to
  **Actions → Build and publish the site → Run workflow**. GitHub pauses the daily build after 60 days with
  no changes in your repository; adding a run or clicking Run workflow turns it back on.
- **Staying on one version:** in `.github/workflows/deploy.yml`, change `ref: main` to a commit from
  aa-stats.
- **Your own icons:** see the `icons` folder.
