# sifteriq-site

The public information site for Sifteriq: a homepage, a privacy policy and terms of service. Sifteriq itself is in private development and is not deployed. This repository holds only these static pages.

Live URL: https://abdulrahman-elsmmany.github.io/sifteriq-site/

## Files

| File | Purpose |
|---|---|
| `index.html` | Homepage: what Sifteriq does, its status, YouTube attribution and contact |
| `privacy.html` | Privacy Policy |
| `terms.html` | Terms of Service |
| `styles.css` | Shared styles (dark only, system fonts) |
| `.nojekyll` | Tells GitHub Pages to serve the files as they are, without Jekyll |
| `LAUNCH_PREREQUISITES.md` | App changes needed before the policy is accurate for other users. Listed in `.gitignore`, so it stays local; remove that line to publish it |

The pages are plain HTML and CSS: no build step, no JavaScript, no analytics, no cookies and no web fonts. Each page sets a Content Security Policy that blocks scripts. The only third-party request is the official "developed with YouTube" badge on the homepage, which loads from `developers.google.com`; the privacy policy discloses it. Links between pages are relative, because the site is served under `/sifteriq-site/`.

## Publishing on GitHub Pages

1. Create a public repository named `sifteriq-site` under the `abdulrahman-elsmmany` account and push these files to the `main` branch.
2. In the repository, open **Settings → Pages**. Under **Build and deployment**, choose **Deploy from a branch**, then `main` and `/ (root)`.
3. When the deployment finishes, check that each URL returns `200` with no redirect:

   ```sh
   curl -sI https://abdulrahman-elsmmany.github.io/sifteriq-site/ | head -1
   curl -sI https://abdulrahman-elsmmany.github.io/sifteriq-site/privacy.html | head -1
   curl -sI https://abdulrahman-elsmmany.github.io/sifteriq-site/terms.html | head -1
   ```

## Before you publish

- Confirm that every mention of Egypt is correct: "based in Egypt" (privacy policy, Who we are and Contact), the developer's computer "in Egypt" (privacy policy, `#yt-sharing` and the paragraph below the `#sharing` table), "run from Egypt" (privacy policy, International transfers) and Egyptian governing law (terms, Governing law).
- In the Supabase SQL editor, check that `select jobname, schedule, active from cron.job order by jobname;` lists `sifteriq-youtube-data-retention` and `sifteriq-prune-operational-history`, both active (the app repo's Stage P2). The privacy policy's 30-day rule (the summary, `#thirty-days` and `#retention`) and the 30-day deletion of replaced AI results and AI request records depend on these jobs. Neither job deletes saved export files or rebuilds the cached copy of the library, and the retention job keeps the IDs of replaced playlists and ended connections and the list of videos imported from them, so `#thirty-days` lists all three as "Today" exceptions. If P2 also schedules `sifteriq-library-projector`, see `LAUNCH_PREREQUISITES.md` (site status) for the sentences that can then change.
- In the Supabase dashboard, open **Authentication → Audit Logs** and check that **Write audit logs to the database** is still off, and that `select count(*) from auth.audit_log_entries;` still returns 0. Both were true on 2026-10-09. The pages say the log of account events exists only in Supabase's own service logs (`#sign-in-records`, the Account row of `#collect`, the Supabase row of `#sharing` and `#retention`). If the switch is ever turned on, change those sentences first (`LAUNCH_PREREQUISITES.md`, B7, option 2).
- In the app's `.env`, check that `OPENROUTER_MODEL` and `OPENROUTER_PROVIDERS` are unset. The privacy policy names the four model providers of the default route, Together AI, Makora, Ionstream and Parasail (`#ai-who` and `#sharing`). Production refuses any other provider, but development does not, so another model or provider list changes which providers receive data. If either is set, update those sentences first.
- The privacy policy also names the two embedding providers, DeepInfra and Nebius (`#ai-more`, `#ai-who`, the "Embedding providers" row of `#sharing` and "Copies at AI providers"). No variable changes the embedding route: it is fixed in the app's `lib/sifteriq-openrouter-config.ts` (`openRouterEmbeddingProviders`), and production refuses it unless every provider is in `policyNamedEmbeddingProviders`. Both endpoints (`deepinfra/us` and `nebius` for `qwen/qwen3-embedding-8b`) were on OpenRouter's zero-data-retention list (`GET https://openrouter.ai/api/v1/endpoints/zdr`) on 2026-10-13. If the app's route changes, update those sentences, the app's Phase 4 notice and `policyNamedEmbeddingProviders` first. `#ai-more` says that only the developer's account is offered the AI notice of 13 October 2026; remove that sentence when the app offers it to everyone.
- The privacy policy says OpenRouter sorts a small sample of requests into anonymous categories (the summary, `#ai-who`, the OpenRouter row of `#sharing` and "Copies at AI providers"). If OpenRouter confirms in writing that this is off for Sifteriq's account, change those sentences first.
- The privacy policy says the AI model providers keep nothing after responding, which every request enforces, but it does not say that OpenRouter itself keeps no prompts or outputs, because OpenRouter's account privacy settings have not been checked. To add that claim, first check in the OpenRouter dashboard that prompt and output logging is off, that the training and data-sharing opt-ins are off, and that the zero-data-retention-only switch is on if it is offered. Record the date in the app repo's `docs/setup/ENVIRONMENT_SETUP.md` (Owner checks). Then add "OpenRouter keeps no prompts or outputs for Sifteriq's account" to the summary, `#ai-who` and "Copies at AI providers".
- Open `index.html` in a browser and check that the badge is clearly readable on the dark tile. It uses the `-light.png` variant at 72 pixels tall, so its wording is about 17 pixels high. The `-dark.png` variant has dark gray text (`#282828`), which is nearly invisible on the tile. The branding page does not say which background each variant suits, and the light file was not inspected, so confirm the text is light before publishing. To avoid the request to Google, download the badge from the [YouTube Branding Guidelines](https://developers.google.com/youtube/terms/branding-guidelines), commit it here, point `src` at the local file and remove `https://developers.google.com` from the homepage's Content Security Policy, then update the "This website" section of the privacy policy.

## URLs for the YouTube API Services audit form

| Field | URL |
|---|---|
| Homepage | `https://abdulrahman-elsmmany.github.io/sifteriq-site/` |
| Privacy policy | `https://abdulrahman-elsmmany.github.io/sifteriq-site/privacy.html` |
| Terms of service | `https://abdulrahman-elsmmany.github.io/sifteriq-site/terms.html` |

Screenshot anchors in the privacy policy: `#youtube` (the YouTube section, with the Google Privacy Policy link), `#revoke`, `#delete`, `#thirty-days`, `#limited-use`, `#yt-sharing` (recipients, device storage and the privacy contact, still inside the YouTube section), `#ai-labels`, `#sharing`, `#cookies` and `#contact`. In the terms: `#youtube-terms`. Capture at 1280x720 or larger with the browser address bar visible. On the homepage, the header's Privacy Policy link and the YouTube attribution band are designed to fit in the first screen at 1280 pixels wide; use a browser window about 800 pixels tall so the page area itself is at least 720 pixels high.

## Keeping the pages accurate

Items marked **At launch** in the privacy policy describe practices that are not yet in place. A label covers everything after it, up to the end of its paragraph, list item or table cell, and any list the labelled sentence introduces. A label on a table row's heading covers the whole row. Headings are outside every label, so keep them neutral, and name the label in plain text when you explain it, as the privacy policy's callout does. Put present-tense facts before a label, never after it. The terms and the homepage have no labels; the homepage says plainly that Sifteriq is not yet available to the public. When an item ships, remove its label and update the **Last updated** date on that page; `LAUNCH_PREREQUISITES.md` lists what each remaining label waits for. The app must not open to anyone other than its developer while any label remains. If the app changes what data it uses, update the privacy policy first.
