# AA No Reset stats website

Make your own stats website for 1.16.1 All Advancements Runs, like
[Zesskyo's AA No Reset Log](https://zesskyo.github.io/aa-stats-no-reset-zesskyo-log/): splits, a progress graph for every run,
average stats, and a Compare page. It's free, runs on GitHub, and needs nothing installed.

Your website only ever holds your runs. The code comes from [aa-stats](https://github.com/zesskyo/aa-stats),
so **new features show up on your site automatically**.

## Set it up (about 5 minutes, once)

1. **Copy this template.** At the top of this page click **Use this template → Create a new repository**.
   Pick any name (it becomes part of your site's address, e.g. `aa-stats`) and keep it **Public**.
2. **Turn on the website.** In your new repository go to **Settings → Pages**, and under
   **Build and deployment → Source** choose **GitHub Actions**.
3. **Build it for the first time.** Go to the **Actions** tab, click **Build and publish the site** on the left,
   then **Run workflow → Run workflow**. Wait for the green tick (about a minute).
4. **Open your site** at `https://<your-username>.github.io/<repository-name>/`
   (also shown under **Settings → Pages**).
5. **Click "Set up this site"** on the welcome card. It walks you through:
   - **Signing in**: you make a GitHub token that can only save to this one repository and paste it in once.
     The steps are on screen. The token stays in your browser, and only you can edit your site.
   - **Naming your site**: type your title and subtitle, e.g. *AA No Reset Solo* and *(Your Name's Log)*.
   - **Adding your first run** (see below).

That's it. From then on everything happens on your site.

## Add, edit and delete runs

Signed in on your site, click **+ Add run** at the top:

- **With a Hermes log:** drop in the run's `play.log`. The date, time, 100% and deaths are read from it.
  Tick the deaths that were on purpose, and add a seed, video, screenshot or notes.
- **Without a log** (older runs, or not played with Hermes): fill in whatever you have, like the final time,
  whether it was 100%, splits and the date. It all shows on the site; the graphs need a log.
- **Proof:** a video link, a screenshot, or both.
- **Elytra distance:** type it in, or pick the world's `stats/<uuid>.json` file.

Click **Save**, and the site updates by itself about a minute later. Every run's page has an **Edit** button,
which also lets you delete it. **Site settings** (at the bottom of the site) changes the title later on.

Visitors only see a small "Owner sign in" link. Without your token, GitHub won't let anyone else save.

## Good to know

- **Updates:** your site rebuilds once a day with the latest code, and whenever you save something.
  To update right away: **Actions → Build and publish the site → Run workflow**. GitHub pauses the daily build
  after 60 days without changes; saving a run or clicking Run workflow starts it again.
- **Signing in on another device or browser:** GitHub only shows a token once, so make another one the same way
  and sign in with it there.
  To stop a token working, delete it under GitHub **Settings → Developer settings → Personal access tokens**.
- **Undo:** every save is a normal change in this repository, so anything can be undone from its history.
- **Staying on one version of the code:** in `.github/workflows/deploy.yml`, change `ref: main` to a commit
  from aa-stats.

## Doing it by hand (optional)

Everything the site saves is a plain file in this repository, so you can also edit them on github.com:

- `site.json`: the title and subtitle. Any other wording on the site can be changed here too: copy a name from
  [text.js](https://github.com/zesskyo/aa-stats/blob/main/src/text.js), e.g. `"colTime": "Time"`.
- `logs/<N>.log`: the Hermes log for run N (uploads on github.com are limited to 25 MB; the site has no limit).
  `logs/<N>.stats.json`: the world's stats file, for elytra distance.
- `screenshots/`: screenshots.
- `runs.json`: details for each run, for example:
  ```json
  {
    "1": {
      "date": "2026-09-24",
      "seed": "-6932149389784936231",
      "video": "https://youtu.be/...",
      "screenshot": "screenshots/1.png",
      "notes": "Jungle spawn, good nether…",
      "intentionalDeaths": [1, 2]
    },
    "2": {
      "time": "3:41:22",
      "hundred": true,
      "splits": {"Any%": "0:38:13", "Midgame": "1:02:49", "Endgame": "3:13:34", "Post-endgame": "3:30:00"}
    }
  }
  ```
  - `intentionalDeaths` lists death numbers (1st, 2nd, …) that were on purpose. Deaths after The End... Again...
    count as on purpose automatically, and `notIntentionalDeaths` overrides that.
  - `time`, `hundred` and `splits` are only for runs without a log.
  - Splits are the time on the clock: when Any% ended, and when Midgame, Endgame and Post-endgame started.
- `icons/`: a `.png` with the same name as a built-in icon
  ([list](https://github.com/zesskyo/aa-stats/tree/main/icons)) replaces it on your site.
