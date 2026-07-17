# 2tt6

A public progress diary — old-web / neocities styled — built with plain
HTML, CSS, and JavaScript. No build step, no framework, no database.

## Pages

- **index.html** — Routine
- **affirmations.html** — Affirmations
- **calendar.html** — Calendar (diary entries, progress, photos, food, habits — all by date)
- **scoreboard.html** — "Days since..." counters
- **entry.html** — Daily entry form + code generator
- **habits.html** — Green/yellow/red colour chart of your habits over time

## The only file you edit day-to-day

**`js/data.js`** — this holds your routine, affirmations, habit definitions,
scoreboard counters, and every diary entry. It's heavily commented so it's
clear where to add/edit things. Everything else on the site is generated
automatically from this file.

## How to add a new diary entry

1. Go to your live site's **Daily Entry** page.
2. Fill out the form (diary text, progress, food, photo filenames, habit checkboxes).
3. Click **Generate Code**.
4. Copy the code block it shows you.
5. On GitHub, open `js/data.js`, click the pencil (edit) icon.
6. Paste the block inside the `ENTRIES = [ ... ]` array (add a comma after
   the previous entry if needed).
7. Commit the change. Netlify redeploys automatically within a minute or two.

## How to add a photo

1. On GitHub, go into the `images/` folder and click **Add file > Upload files**.
2. Upload your photo (e.g. `2026-07-15-progress.jpg`).
3. In your diary entry in `js/data.js`, add it to the `photos` array as
   `"images/2026-07-15-progress.jpg"`.

## How to add/edit/remove a habit

Edit the `ACTIVITIES` array in `js/data.js`. Each habit needs a `key`
(internal id), a `label` (display name), and a `type` (`"positive"`,
`"neutral"`, or `"negative"` — this controls the colour everywhere on the site).

## How to add/reset a scoreboard counter

Edit the `SCOREBOARD` array in `js/data.js`. Each card has a `label` and a
`lastDate`. When the tracked thing happens again, just update `lastDate` —
the day count recalculates itself automatically, no maths needed.

## Deploying

### 1. Put it on GitHub

- Create a new repository on GitHub (e.g. `2tt6`).
- Upload all the files/folders in this project to that repository
  (either drag-and-drop on github.com, or `git init` / `git add .` /
  `git commit` / `git push` from the command line).

### 2. Connect it to Netlify

- Go to [netlify.com](https://www.netlify.com) and sign in (you can sign
  in with your GitHub account).
- Click **Add new site > Import an existing project**.
- Choose GitHub, then select your `2tt6` repository.
- Build settings: leave the build command **empty** and set the publish
  directory to `/` (this is a static site, nothing needs to be built).
- Click **Deploy**. Netlify will give you a live URL, and will
  automatically redeploy every time you commit changes on GitHub.

### 3. (Optional) Custom domain / site name

In Netlify, go to **Site settings > Change site name** to pick a nicer
subdomain (e.g. `2tt6.netlify.app`), or attach your own custom domain
under **Domain management**.

## File structure

```
2tt6/
├── index.html          (Routine page)
├── affirmations.html
├── calendar.html
├── scoreboard.html
├── entry.html
├── habits.html
├── css/
│   └── style.css       (all styling)
├── js/
│   ├── data.js          <-- EDIT THIS ONE for day-to-day updates
│   └── main.js          (rendering logic — you shouldn't need to touch this)
├── images/               <-- upload your progress photos here
└── README.md             (this file)
```

## Notes

- Everything runs entirely in the browser — there's no server and no
  database, which is why the "Generate Code" button on the Daily Entry
  page exists: it's how new entries get turned into something you can
  commit to GitHub.
- Because it's a fully static site, it costs nothing to host on Netlify's
  free tier.
