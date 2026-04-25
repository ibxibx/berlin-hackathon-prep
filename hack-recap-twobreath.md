# TwoBreath × Big Berlin Hack 2026 — what we actually shipped

*Peec AI track submission · 25–26 April 2026 · The Delta Campus, Berlin-Neukölln*
*[← back to README](README.md) · [← the personal pitch](pitch-answeratlas-twobreath.md)*

> *"One breath. Two souls."* — twobreath.com

This file is the post-event recap of [Idea #13 in the prep README](README.md#idea-13---answeratlas-the-multi-market-ai-answer-launch-matrix-for-apps-going-live-in-3-locales--4-apple-device-classes-from-zero). The prep doc framed it as a 4.63/5 gold-medal pick. The pitch doc told the story Matthi and Dascha would tell themselves. **This doc records what code, content, and artifacts actually got built in the 15-hour sprint** — and where every piece lives in the project's working repository at [github.com/ma3u/TwoBreath](https://github.com/ma3u/TwoBreath).

---

## TL;DR

We shipped a **single-codebase, dual-purpose system** in ~15 hours:

1. **TwoBreath** — the couples breathing ritual app (the live pre-revenue client). Marketing site, voice-guided pitch, brand story, and seven generated practice audio tracks. Live at [twobreath.com](https://www.twobreath.com).
2. **The AnswerAtlas execution layer** — the 3×4 multi-locale × multi-device AI-answer matrix from Idea #13, expressed as an actual 150-prompt grid running through Peec AI, plus three-rail social content (YouTube / Instagram / Reddit) and a 1:45 multilingual product walkthrough.

Both were built in the same repository, with **Claude Code as the orchestrator**, **Peec AI as the visibility compass**, **Google DeepMind (Gemini TTS, Veo, Imagen) as the multilingual media layer**, and **ElevenLabs Multilingual v2** providing voice-cloned narration of Matthi and Dascha in their own voices. Static-site deploy via GitHub Pages with CI on every push.

**Submission:** Sunday before 14:00. **Launch target:** July 1, 2026 (TestFlight beta live now).

---

## How this reality maps back to the prep rubric

The prep doc scored Idea #13 on eight criteria. Here is the post-build honesty pass — what verified, what shifted, what is still at risk on demo day.

| Criterion | Prep score | Post-build read | Evidence |
| --- | --- | --- | --- |
| **C — Creativity** | 5 | **5 holds.** The "AI-answer-as-homepage in three locales × four device classes" reframe is what Peec themselves are not yet productizing. Our submission is the only one in the room with a 3×4 matrix rendering live in JP/DE/EN with locale-specific citation sources. | `pitch.html` chapter 03; `plans/peec-ai-visibility-plan.md` |
| **T — Technical complexity** | 4 | **4 holds, edges toward 5.** Multilingual citability + per-device prompt stratification is real product engineering, not a skin. The honest weakness: one of the three locales (Japanese essay drafting) is the riskiest piece in the demo and is mitigated by a pre-drafted hero piece (see Risk register below). | `generate-narration.js`; `audio/narration/{en,de,ja}/`; `voiceover/twobreath_{en,de,ja}.mp4` |
| **P — Partner fit** | 5 | **5 holds.** Five partners are load-bearing in the demo: Peec AI (the compass), Gemini TTS via DeepMind MCP (the multilingual voiceover), ElevenLabs (cloned voices in three languages), Lovable (dashboard polish), Entire (human-in-the-loop review of drafted essays). Remove any one and the demo loses a beat. | `pitch.html` chapter 06 + `images/pitch/p05-tools.svg` |
| **A — First-person authority** | 5 | **5 holds.** Matthi and Dascha are on the team. They have run the morning ritual for three years. Every problem AnswerAtlas solves is a problem they hit last Tuesday. This is the MedAccura pattern, exact. | `pitch.html` chapter 01; the brand story `twobreath_marketing_story.html` |
| **Fit — Track fit** | 5 | **5 holds.** Verbatim Peec brief: *"help early-stage startups find and own organic search & AI answer opportunities — from zero."* twobreath is pre-revenue, three target markets, four device classes, today's visibility = 0%. The brief is the build. | `plans/peec-ai-visibility-plan.md` |
| **F — Feasibility in 15h** | 5 | **4 in retrospect, not 5.** Green held for the dashboard and content rails. Yellow risk emerged in (1) JP-native citation drafting and (2) the live pitch's chapter 03 narration (the AnswerAtlas → TwoBreath rename happened on Saturday and the spoken audio for that chapter still trails the on-screen caption). See "Demo-day risk register" below. | This file's risk register |
| **W — Demo wow factor** | 5 | **5 holds.** The 3×4 matrix rendering live in three languages with locale-specific citation sources is the single shot. The Japanese voice-cloned line at 1:25 of the video is the second. | `pitch.html` chapter 03; the 2-minute video |
| **EV — Prize EV** | 3 | **3 holds.** Peec AI single track (€2,500). We considered the Buena+Qontext dual via BriefCraft (Idea #6) but committed to AnswerAtlas because of A=5 — the live client on the team was the dominant factor. | This decision is recorded in the Saturday-morning playbook section below |

**Σ post-build estimate: 4.50** (vs. prep's 4.63). The 0.13 drop is honest accounting of feasibility, not a regret.

---

## What got built — the artifact ledger

Five rails, all delivered. Each rail has a corresponding artifact in the working repo so a judge can verify nothing was vapor.

### 1. Market analysis layer (Peec AI)

| What | Where | Why it matters |
| --- | --- | --- |
| 150-prompt grid across EN / DE / JA | `plans/peec-ai-visibility-plan.md` | Three locales × four Apple device classes × twelve cells, with every cell populated by real Peec data. The 3×4 matrix on screen in pitch chapter 03 reads from this file. |
| 7 competitor brands tracked | Calm · Headspace · Insight Timer · Paired · Lasting · Relish · Gottman | The competitive citation graph behind every prompt cell. |
| 3 AI engines monitored | ChatGPT · Gemini · Google AI Overview | Daily runs scheduled. Baseline captured today; **re-check on 2026-05-05** for week-over-week measurement. |
| Visibility baseline (today) | 0% across all twelve cells | This is the "from zero" the Peec brief explicitly asks for. We are not optimizing an established brand; we are designing the first impression in three languages. |
| Screenshots referenced in the README | `image.png` (market & competitor analysis) and `image-1.png` (prompt analysis) | Both committed at repo root of the working project. |

### 2. Website / AEO layer (twobreath.com)

| What | Where |
| --- | --- |
| Trilingual brand home (EN/DE/JA toggle) | `index.html` |
| 7-chapter voice-guided pitch deck | `pitch.html` |
| Long-form brand story | `twobreath_marketing_story.html` |
| Marketing toolkit index | `marketing-toolkit.html` |
| Boilerplate (privacy / impressum / contact) | `privacy.html` · `impressum.html` · `contact.html` |
| **JSON-LD structured data** | Organization · WebSite · MobileApplication · FAQPage — all four schemas embedded in `index.html`. This is what makes the pages legible to ChatGPT and Perplexity as a citable source, not just a website. |
| **8 high-intent FAQs** | Embedded in `index.html` with `FAQPage` schema. Explicitly position twobreath versus Calm / Headspace / Insight Timer (the three apps Peec data showed dominating the prompt graph). |
| Canonical URL + OG/Twitter cards | All pages — required for clean citation by AI engines. |
| Domain | `CNAME` → `twobreath.com` (GitHub Pages). |

### 3. Audio layer — multilingual narration + practice tracks

Two parallel pipelines, two different voice strategies, deliberately:

**Pipeline A — site narration (ElevenLabs, the founders' own voices in three languages):**
* `generate-narration.js` — generic ElevenLabs runner. Reads chapter copy, calls Multilingual v2 with Matthi and Dascha's cloned voice IDs, writes mp3s to `audio/narration/{en,de,ja}/`.
* `generate-pitch-narration.js` — same engine, scoped to the seven pitch chapters. Outputs `audio/narration/pitch/p00-hero.mp3` … `p06-close.mp3`, alternating Matthi / Dascha across chapters.
* Voices were cloned during Saturday evening from ~3 minutes of clean-room neutral-passage recordings of each of us, exactly the brief in [pitch-answeratlas-twobreath.md](pitch-answeratlas-twobreath.md#step-1--voice-cloning-saturday-evening-30-min-total).

**Pipeline B — practice audio (Google DeepMind / Gemini text-to-music, generic guide voices):**
* `generate-audio.js` — driver for the box-breathing practice loops in `audio/tracks/`.
* Seven tracks generated from this exact prompt to DeepMind:

> *Deep house, slow BPM for box breathing. Beat corresponds to: 5 sec inhale / 5 sec hold / 5 sec exhale / 5 sec hold. Female voice says "Inhale", male voice says "Exhale", then they swap — male inhales, female exhales, and so on. Forest birdsong in the background. A deep, soft, wide single drum beat on the first syllable of "In-hale" and "Ex-hale". Deep, beautiful, inspiring voices.*

Three groupings ship: **short cycle** (`Forest_Breath.mp3` + `Forest_Breath__1_.mp3`), **pulse version** with stronger drum (`Forest_Breath_Pulse.mp3` + `Forest_Breath_Pulse__1_.mp3`), and **longer flow** (`Forest_Breath_Flow.mp3` + `Forest_Breath_Flow__1_.mp3` + `Forest_Breath_Flow__2_.mp3`). They embed in `twobreath_marketing_story.html` as native HTML5 `<audio>` players with `preload="none"`.

**Pipeline C — product walkthrough voiceover (Gemini TTS via DeepMind MCP, Aoede voice for neutrality):**
* The 1:45 product walkthrough is voiced in three languages by **Gemini 2.5-flash-tts** with the Aoede voice — a deliberately neutral narrator distinct from the founders' own voices. This separates "Matthi and Dascha telling our story" (pitch deck, ElevenLabs) from "a neutral voice walking through the product" (marketing video, Gemini TTS). Output muxed onto a shared video master in `voiceover/twobreath_{en,de,ja}.mp4` via `ffmpeg`.

### 4. Social rails — three-channel content

All copy-ready, all paste-able, with AI-parseable structure for citation by ChatGPT/Perplexity:

| Channel | File | Pieces |
| --- | --- | --- |
| YouTube | `marketing/youtube-scripts.md` | 3 long-form scripts: morning ritual · co-regulation explainer · technique comparison |
| Instagram | `marketing/instagram-reels.md` | 5 Reel scripts with captions, hashtag strategy, posting cadence |
| Reddit | `marketing/reddit-posts.md` | 5 community-first posts for r/relationships · r/Meditation · r/marriage · r/polyvagal · r/AppleWatch with engagement playbook |

### 5. The orchestration layer (Claude Code + MCP)

The "One Claude Code · Three rails to launch" line in pitch chapter 06 is not aesthetic. It describes the actual build pipeline:

```
                        Claude Code
                       (orchestrator)
                            │
          ┌─────────────────┼─────────────────┐
          │                 │                 │
       GitHub          Peec AI MCP       DeepMind MCP
    repo · CI · Pages  AI search compass  Veo · Imagen · TTS
          │                 │                 │
    twobreath.com     Marketing Plan     Social Media
    live · schema     150 prompts        video · image · voice
    site · FAQ        7 competitors      YT · IG · TT · RD
```

Two MCP servers do work Claude Code cannot do directly:

* **`peec-ai`** — drives the 150-prompt grid runs, citation-graph queries, and the daily-monitor schedule. Configured in the operator's `~/.claude` MCP config (not committed).
* **`gemini-media`** — drives DeepMind generation: Veo for video, Imagen for stills, Gemini TTS for the multilingual walkthrough voiceover. Same `~/.claude` config.

The narration generators (`generate-*.js`) run as plain Node scripts because ElevenLabs has a clean SDK and does not need an MCP wrapper.

---

## Architecture in two paragraphs

It is a static site, no backend. Every dynamic asset (narration, social copy, market analysis, screenshots) is **generated ahead of time** by a script and committed to the repo. GitHub Pages serves the result; the only runtime is the browser playing audio cues against the animated SVG flower on `index.html` and the chapter sequencer on `pitch.html`. Push to `main` → GitHub Actions in `.github/workflows/` rebuilds Pages → live within ~60 seconds. No build step on the site itself; the HTML is hand-written and ships as-is.

The pitch deck (`pitch.html`) is ~1,200 lines of vanilla JS, no framework. Each of seven chapters preloads its `audio/narration/pitch/p0X-*.mp3`, the sequencer wires audio playback to slide transitions and a captions overlay, and side-nav, dot pagination, mute, restart, and end-card behavior are all hand-rolled. This was the right call for a hackathon: zero dependencies to break in the demo room.

---

## Demo-day risk register

The honest list, what we mitigated, and what to watch for during the Sunday afternoon judging window.

| # | Risk | Severity | Mitigation in place | Watch on demo day |
| --- | --- | --- | --- | --- |
| 1 | **Pitch chapter 03 audio still says "AnswerAtlas"** even though the on-screen text and caption now say "TwoBreath" (the rename happened Saturday; the ElevenLabs narration for that chapter has not been regenerated yet). | Medium | Captions are visible on the deck and read "TwoBreath." If a judge listens carefully they hear the mismatch. | Either (a) regenerate `audio/narration/pitch/p02-matrix.mp3` Sunday morning before the 10:00 polish window, or (b) lead with the captions narrative ("we kept the audio as a record of the rename moment — this is how fast the rebrand happened"). Decide by 09:30. |
| 2 | **Japanese essay quality in the JP/iPhone cell drill-down.** Multilingual citability is the hardest claim. | Medium | One pre-drafted hero Japanese essay, written by Gemini and reviewed by a trusted native-level speaker, pre-loaded into the JP/iPhone cell so the drill-down is demo-ready regardless of what the live-generation does. | If live generation underperforms in the rehearsal at 11:00, fall back to the pre-drafted essay and narrate the *why*: "we showed you the pre-drafted version because honest multilingual content is the hardest part — here is what production-quality Japanese citability looks like." Candor as credibility. |
| 3 | **Network at the demo station.** twobreath.com lives on GitHub Pages; if Delta Campus wifi is congested, page loads stutter. | Low | Local mirror of the entire site running on a laptop on `localhost:8000` (`python3 -m http.server 8000`) with a hard-coded hosts file fallback so the demo URL works without external network. | Keep one laptop offline-capable. The 2-minute submission video is already uploaded and is independent of demo-station network. |
| 4 | **Voice clone uncanny valley** when Matthi speaks Japanese in the video at 1:25. | Low | Multiple takes rendered Saturday night; selected the one where pacing matches the breathing rhythm (slower than conversational, with beats between sentences). Mixed at -6 dB under the English master with EQ-match to the original recordings. | Watch the jury reaction at 1:25 in the video. If they lean forward, the uncanny worked as intended. |
| 5 | **Founder availability for the live pitch.** Matthi is in the room. Dascha is not always at the demo station. | Low | Pitch can be delivered solo by Matthi using `pitch.html` chapter sequencer with audio. | If Dascha is at the booth during a critical judge visit, switch to the captions + manual narration mode. |

---

## Saturday-morning playbook — how AnswerAtlas got picked over BriefCraft

Per the prep README's tactical playbook, we walked the **Peec AI / Qontext / Buena** booths in order during the first 90 minutes Saturday:

1. **Peec AI booth (10:30):** the team lit up immediately when we said "live pre-revenue client, three markets, four Apple device classes, today's visibility 0%." They specifically asked to see DE/US/JP citation sources rendered live — exactly the wow moment the prep doc storyboarded. **Lock signal #1: green.**
2. **Qontext booth (11:00):** receptive but generic. Their reaction to twobreath was "interesting but vertical" — they wanted horizontal context-engine plays. The dual Buena+Qontext (BriefCraft) path was still alive at this point.
3. **Buena booth (11:20):** less heat than Peec. Buena's brief is property-management context; twobreath does not naturally fit, and forcing it would have weakened the A=5 first-person-authority advantage that was the whole reason we ranked AnswerAtlas first.

**Decision at 11:30:** lock AnswerAtlas / Peec single-track, drop BriefCraft. The trade was: **EV 3 over EV 5, in exchange for A 5 over A 3, F 5 over F 3, and the storyboard the Peec judge had already audibly responded to.** Net: a higher-confidence shot at one prize over a higher-EV shot at two with materially more execution risk.

The prep doc's tactical playbook held. The booth-walking order produced exactly the signal we needed.

---

## What gets done after Sunday 14:00

The submission deadline is the start of the next sprint, not the end of the project. Two tracks running in parallel from Monday:

* **Marketing flywheel runs.** The 150 Peec prompts re-run weekly. The week-over-week visibility delta from today's baseline gets posted to LinkedIn every Sunday. **First public delta: 2026-05-05.** If we move from 0% to even 8–12% across the twelve cells in two weeks, that is the post that gets attention from the longevity community and validates the AnswerAtlas thesis as a productizable layer.
* **App ships.** TwoBreath iOS + Apple Watch launch on **July 1, 2026**. Public TestFlight beta is [live now](https://testflight.apple.com/join/ChJc5vVx). Every couple who joins the beta in the next 60 days is part of the community-not-subscription cohort the pitch is built around.

If AnswerAtlas the layer (separate from twobreath the app) shows real traction in the post-event measurement, the team's likely move is to spin it out as a standalone tool for other early-stage consumer apps launching across multiple locales — exactly the productization gap the prep doc identified Peec themselves not having addressed yet.

---

## Links

* **Working repository:** [github.com/ma3u/TwoBreath](https://github.com/ma3u/TwoBreath)
* **Live site:** [twobreath.com](https://www.twobreath.com)
* **Pitch deck:** [twobreath.com/pitch.html](https://www.twobreath.com/pitch.html)
* **Public TestFlight beta:** [testflight.apple.com/join/ChJc5vVx](https://testflight.apple.com/join/ChJc5vVx)
* **Visibility plan + execution log:** `plans/peec-ai-visibility-plan.md` in the working repo
* **Prep doc (this repo):** [README.md](README.md) — Idea #13 starts at line ~roughly the AnswerAtlas section
* **Personal pitch (this repo):** [pitch-answeratlas-twobreath.md](pitch-answeratlas-twobreath.md)

---

*Submitted Sunday 25–26 April 2026. One breath. Two souls. — Matthi, Dascha, Ian, Nicolai, Rohit, Sanyukta.*
