# Changes to the Privacy Policy and Terms

## 19 October 2026: rewrite for Sifteriq as it works now (material change)

Effective 2 November 2026. Until then the versions effective 8 October 2026 apply. Every account, the developer's included, is asked to accept the new pages, and to agree to the updated AI notice in the app before Sifteriq sends anything to an AI provider again.

### Why

The pages described an older Sifteriq: an AI "triage" ranker, AI duplicate checks, a removal preference and decisions-file uploads, none of which exist any more. Since then Sifteriq has moved to one ranking system, added Groups with two new AI recipients, an in-app player with watch progress, and monthly AI budgets, and moved saved views and snoozes into the account. A new recipient and new kinds of data are a material change, so this version gives 14 days' notice and asks everyone to accept it again.

### Privacy Policy

- **AI processing, step by step.** `#ai-sent` now lists each request and its recipient: video summaries, the goal profile and ranking (Together AI, Makora, Ionstream or Parasail), and embeddings (DeepInfra or Nebius), with the exact fields each one sends and what is never sent. The old AI triage, its per-batch goal and the AI duplicate check are gone.
- **Groups (new).** `#ai-groups` describes how Sifteriq finds saved videos that cover the same thing: which fields go to TypeSafe (Typesafe AI, Inc., United States) and to Microsoft Azure (Microsoft Corporation; Azure endpoints in the United States, the European Union or an unstated region), what is stored (each answer with a hash of its input, and the pairs decided), for how long (28 days after the earlier fetch of the two videos, and with the videos), the worker's temporary files and when they are deleted, and the small pair-picking model fitted once on the developer's own library. TypeSafe and Azure are added to `#ai-who`, `#sharing` (new "Groups providers" row), `#transfers` and "Copies at AI providers".
- **Playing videos in Sifteriq (new).** `#yt-player` describes YouTube's embedded player in privacy-enhanced mode, what YouTube may collect, the watch progress Sifteriq keeps (deleted 28 days after it was last saved), and that videos made for kids are never played or recorded. YouTube's player is added to `#sharing`, `#cookies` and `#dnt`.
- **Your activity.** Watch progress, snoozes, saved views (stored with the account, up to 12 per page, with any channel filter removed on Clear library, disconnect and the 28-day rule), your choices in Groups and about duplicate copies, and duplicate copies found by fixed rules without AI, each with its retention.
- **Monthly AI budgets (new).** `#ai-budgets`: each account has monthly AI budgets; a request over budget is not sent and the step pauses. AI request records hold usage and cost only, no text, for 30 days.
- **Corrections.** Removed: the removal preference, decisions-file uploads, counts of failed AI attempts, stored provider raw responses, and the sentence that offered the AI features only to the developer's account. YouTube quota use is kept 90 days. Public video details now list the embeddable and made-for-kids status. Browser storage lists the watch check-in keys and no longer lists saved views or snoozes.
- **Kept.** Every "At launch" item that depends on hosting (database region, hosting provider and its logs, HTTPS, export files within 24 hours, deletion after a revoke or account switch, Takeout limited to Watch Later and playlists, Limited Use, transfer terms).

### Terms of Service

- `#service` describes the AI features, Groups and the in-app player.
- `#youtube-terms` says YouTube's terms cover videos played in Sifteriq, with YouTube's player shown unchanged.
- `#ai` ("AI features") covers summaries, fit labels, rankings, goal profiles and Groups, their limits, and the AI notice that is asked for again when a recipient is added.
- `#fees` ("Fees and AI budgets") explains the monthly AI budgets.
- Acceptable use and accounts forbid getting around the AI budgets; `#termination` and `#disclaimers` mention the AI providers.

### Homepage

- The "How it works" and "Your data" cards describe ranking by goal, Groups and the in-app player instead of AI triage.
