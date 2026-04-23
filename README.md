# Big Berlin Hack 2026 - Team Prep & Idea Shortlist

**Event:** Big Berlin Hack by {Tech: Europe} × CODE University × The Delta Campus
**Dates:** 25-26 April 2026
**Location:** The Delta Campus, Berlin-Neukölln
**Prize pool:** €50K+
**Team size:** up to 5 (we plan for 2-4)
**Our real build window:** Saturday night → Sunday ~14:00 submission deadline ≈ **~14-16h of actual coding**

> ⚠️ We are **not** working the full 36h. This single constraint drives every decision in this document.

---

## Table of Contents

1. [Why this repo exists](#why-this-repo-exists)
2. [What the jury actually rewards](#what-the-jury-actually-rewards)
3. [Case study: why MedAccura won in January 2026](#case-study-why-medaccura-won-in-january-2026)
4. [Our strategic filter: the 15-hour rule](#our-strategic-filter-the-15-hour-rule)
5. [Partner tech stack - what's on the table](#partner-tech-stack--whats-on-the-table)
6. [Shortlisted ideas (analyzed in detail)](#shortlisted-ideas-analyzed-in-detail)
7. [How we'll pick the final idea](#how-well-pick-the-final-idea)
8. [Team roles & division of labor](#team-roles--division-of-labor)
9. [Timeline: Saturday night → Sunday 14:00](#timeline-saturday-night--sunday-1400)
10. [Submission checklist](#submission-checklist)

---

## Why this repo exists

This repo is our **pre-hackathon war room**. The goal is to walk into the Delta Campus on Saturday already knowing:

- What we're building and why it fits the judging criteria
- Which 3+ partner tools we're using and how they compose
- Who's doing what in the first 2 hours vs the last 2 hours
- What our 2-minute demo video is going to show

Because the rules require a **brand-new project started at the event**, we cannot pre-write code. But we absolutely can (and should) pre-write **decisions** - the team that shows up with fuzzy intent and 14h of coding time loses to the team that shows up with a sharp wedge and the same 14h.

---

## What the jury actually rewards

From the January 2026 edition at Delta Campus (source: Gründerszene / Business Insider coverage by Leandra Finke), the jury scored 27 submitted projects on three things:

| Criterion | What it actually means | How we target it |
|---|---|---|
| **Creativity** | A non-obvious angle on a real problem. Not "another chatbot." | Pick a problem the team has *lived experience* with. MedAccura won because a practicing doctor was on the team. |
| **Technical complexity** | Real plumbing visible under the hood - not just a Lovable front-end calling one API. | Mandatory: at least one non-trivial data/retrieval/agent layer (RAG, multi-step agent, tool-calling, voice pipeline, etc.) |
| **Effective use of partner tech** | Bonus points for using partner tools *well*, not decoratively. | Use 3+ partner techs where each one is **load-bearing** - if you remove it, the demo breaks. |

The judges' literal praise for MedAccura: *"This project stands out for its great technical depth, realized in a very short time, with really great results that can make the world a better place - especially hospitals."* Memorize the shape of that sentence. That's what we're aiming to trigger.

---

## Case study: why MedAccura won in January 2026

**The team:** Led by Tim Schwarz, a practicing doctor. Second hackathon for him.

**The product:** An AI agent for hospital clinicians. Doctors face hundreds of pages of medical guidelines (PDFs) and have to stay current while juggling patients. MedAccura ingested all the guideline PDFs and let clinicians query them via ChatGPT / OpenAI, returning the exact relevant passages on demand.

**Why it won - decomposed:**

### 1. Creativity score: high, but not because it was flashy

It wasn't a novel AI technique. RAG over PDFs is a solved pattern in 2026. The creativity was in the **problem selection**: picking a domain where the asymmetry between "information available" and "information accessible during a stressful shift" is enormous, and where the wow moment ("I found the right protocol in 4 seconds instead of 20 minutes") is immediately legible to non-experts on the jury.

**Takeaway for us:** Creativity != novelty of tech. Creativity = a problem framing the jury hasn't heard 8 times that same day.

### 2. Technical complexity score: high, for pragmatic reasons

A working RAG pipeline in 36h (and we only have ~15h) that actually returns correct, cited passages from long PDFs is harder than it looks:

- PDF parsing of medical guidelines (tables, footnotes, multi-column layouts)
- Chunking strategy that preserves clinical context
- Embedding + vector search
- Prompt engineering that forces citation of source passage
- A UI that surfaces the source so a doctor can verify

That's 5 real engineering decisions, each of which can fail. Demonstrating that *all five work* in a 2-minute video reads as technical depth - even though none of the individual pieces are research-grade.

### 3. Partner tech fit: clean and load-bearing

They used OpenAI (reasoning / synthesis) as the core. The other required 2 of 4 tools were absorbed into the pipeline. Nothing was decorative. **Every partner tech earned its keep in the demo.**

### 4. The hidden 4th criterion: domain credibility in the pitch

A doctor on stage saying "I face this problem every week in the ER" is unbeatable demo framing. The jury's "make the world a better place, especially hospitals" line is a direct response to that framing.

**Takeaway for us:** Whoever pitches must have or convincingly borrow **first-person authority** over the problem. If nobody on the team lives the pain, don't pick that problem.

---

## Our strategic filter: the 15-hour rule

Teams that stay all 36h have a real advantage on depth. We don't have that. So we need to win on **problem selection + ruthless scope**, not stamina.

Every idea in the shortlist below has been stress-tested against five questions:

1. **Can a 2-4 person team ship a *working* demo in 14-16h?** Not a mockup - a demo where the judge watches one input go in and one useful output come out on a real laptop at the demo station.
2. **Does it have one undeniable "wow" moment?** The 2-minute video must have a single shot where the jury audibly reacts.
3. **Can 3+ partner techs be load-bearing, not decorative?** (See table below.)
4. **Does at least one team member have first-person authority on the pain point?** If no, drop it.
5. **Is there a believable "this could be a company" story?** The jury is staffed by sponsors; several are VCs. MedAccura's team said they'd keep working on it post-event. That line matters.

Any idea that fails #1 or #2 is an **automatic reject** regardless of how cool it sounds.

---

## Partner tech stack - what's on the table

From the Big Berlin Hack poster and the Luma event page. The rule is typically "use at least 3 of N partner tools." Here's how we're thinking about each:

### Core model / reasoning layer
| Partner | What it is | How we'd use it |
|---|---|---|
| **Google DeepMind (Gemini 3)** | Frontier multimodal reasoning model | Primary brain for any agent / reasoning task. Long context + vision makes it strong for document-heavy or screenshot-in workflows. |
| **Pioneer by Fastino Labs** | Small models that train themselves on your data | Pairs beautifully with a domain-specific vertical (fine-tune on the specific corpus, let Gemini handle orchestration). |

### Agent / orchestration layer
| Partner | What it is | How we'd use it |
|---|---|---|
| **Entire** | Developer platform for agent ↔ human collaboration | When the agent needs a human in the loop - approvals, edits, handoffs. Excellent for any workflow automation pitch. |
| **Qontext** | Context layer for AI (think: shared memory / structured context) | Any time you need the agent to remember across steps or share state between multiple tools. Load-bearing in multi-agent setups. |

### Data / retrieval / search
| Partner | What it is | How we'd use it |
|---|---|---|
| **Tavily** | Real-time web search, extraction, research API | Essential for any "up-to-date info" angle - news, regulations, competitor data, market signals. |

### Voice / audio
| Partner | What it is | How we'd use it |
|---|---|---|
| **Gradium** | Real-time voice AI (TTS + STT) | Any phone/voice-first interface. Pairs insanely well with telli for inbound/outbound call demos. |
| **ai\|coustics** | Real-time audio intelligence / enhancement | Clean up real-world audio before it hits the model. Useful for any voice demo recorded in a noisy hackathon room. |
| **telli** | AI-handled customer calls | Prebuilt calling infrastructure. Dramatic demos: "watch the AI handle this real phone call live." |

### Frontend / UI
| Partner | What it is | How we'd use it |
|---|---|---|
| **Lovable** | Build apps and websites by chatting with AI | Our frontend lever. Stops the front-end from eating 6h of our 15h. |
| **Hera** | AI motion designer | If we want the demo video itself to look polished without a designer on the team. |

### Security
| Partner | What it is | How we'd use it |
|---|---|---|
| **Aikido** | Secure everything | Only load-bearing if our pitch is explicitly security/compliance. Otherwise skip - don't tack it on. |

### Vertical track partners (bonus prize categories)
| Partner | Domain | Strategic value |
|---|---|---|
| **Buena** | Property / real-estate operations | Dedicated track prize. Huge opportunity if we pick a property-ops idea. |
| **Inca** | Agentic AI for insurance | Dedicated track. Insurance claims / underwriting automation is a natural fit. |
| **Reonic** | AI OS for renewable installers | Dedicated track. Great for solar/heat-pump installer workflow automation. |
| **Peec AI** | AI search analytics (how your brand shows up in ChatGPT/Perplexity) | Dedicated track. Marketing / SEO angle. |

> **Strategic observation:** Picking an idea that aligns with a **vertical track partner** gives us two shots - the main prize AND the track-specific prize. This is probably the single highest-EV move available to us.

---

## Shortlisted ideas (analyzed in detail)

Each idea is scored 1-5 on the five strategic filters. Anything below 4/5 average is cut. These 12 ideas are the survivors of a larger filter, now rebuilt around a single lens: **urgent daily problems where AI can create visible impact AND a credible business**.

The jury at Big Berlin Hack is staffed by sponsors, several of whom are active investors. The ideas below are picked so that the 2-minute video doubles as an investor teaser: each one names a specific paying customer, a wedge, and a clean partner-tech composition.

Legend for difficulty dots: green = feasible in 15h, yellow = tight but doable with discipline, red = only if a teammate has prior art in the exact stack.

### Idea 1 - HireSignal: Job description -> realistic skills interview in 5 minutes

> Recruiter or hiring manager pastes a job description. Agent generates a *specific*, *hands-on*, adaptively difficult interview (not generic STAR-question fluff) in the candidate's browser. As the candidate answers via voice, difficulty adjusts live. At the end, recruiter gets a structured signal report - not a yes/no - scoring on the actual skills the JD implied.

**Partner tech (all load-bearing):**
- **Gemini 3** - JD decomposition into a skill tree, adaptive question generation, scoring
- **Gradium** - real-time voice for the candidate-facing interview
- **ai|coustics** - clean up home-office audio (this directly affects perceived interview quality)
- **Qontext** - candidate-session memory for adaptive difficulty
- **Lovable** - both dashboards (recruiter + candidate)

**The wow moment:** Paste a real Anthropic or Neo4j job description (both relevant to Ian's network). Two minutes later, a judge takes the live interview themselves on stage. At the end, the dashboard scores them in real time on the specific skills.

**Technical complexity:** High. Adaptive questioning is non-trivial, and doing it in real time over voice is a visible engineering feat.

**Feasibility in 15h:** Tight. We constrain to technical JDs only (narrower question space) to make the adaptive loop tractable.

**First-person authority:** Ian is literally job-hunting right now and is evaluating how to signal skills to hiring managers. This idea has the strongest first-person authority of the list for you specifically, and the pitch writes itself: "I got tired of shallow interviews eight weeks into my job search, so we built the thing we wished existed on both sides."

**Scores:** Creativity 4/5 - Complexity 5/5 - Partner fit 5/5 - First-person authority 5/5 - Company story 5/5
**Average: 4.8/5 (top-ranked)**

---

### Idea 2 - StandUpAgent: The async daily standup that actually writes itself

> Every team member sends a 30-second voice note to a number at any point in the morning. The agent transcribes, deduplicates (yes, you already mentioned the Stripe issue yesterday), cross-references GitHub / Linear / Jira activity, and publishes a single structured standup summary to Slack - with blockers highlighted and @-mentions for anyone whose work is blocking someone else.

**Partner tech (all load-bearing):**
- **Gradium** - the voice interface (STT + optional TTS nudge if you forgot to submit)
- **ai|coustics** - cleans up voice notes recorded on the train
- **Gemini 3** - synthesis + cross-referencing + deduplication
- **Qontext** - week-over-week memory so "still blocked on the thing from yesterday" resolves correctly
- **Tavily** - fetch GitHub/Linear activity for the cross-reference

**The wow moment:** Three team members record voice notes *during the pitch*. Thirty seconds later, a beautifully formatted standup appears in Slack on the big screen, with one blocker correctly flagged and one automatically-resolved "this was fixed yesterday" call-out.

**Technical complexity:** Medium-high. The interesting engineering is the cross-reference + dedup, not the voice part.

**Feasibility in 15h:** Very feasible. Lots of prior art in the voice-to-summary space, which is why we need to make the cross-reference angle the differentiator.

**Risks:** The jury may have seen "AI standup" before. Differentiation has to come from the *specificity* of the output (real PR numbers, real blocker graph) not from the concept.

**Scores:** Creativity 3/5 - Complexity 4/5 - Partner fit 5/5 - First-person authority 5/5 - Company story 4/5
**Average: 4.2/5**

---

### Idea 3 - JobMatch Reverse: for people locked out of the job market, not the other way around

> Most job platforms optimize for employer search. JobMatch Reverse optimizes for the candidate who is unemployed, long-term out of work, or recently migrated. User uploads whatever they have - a CV in Farsi, a photo of a foreign certificate, a voice note describing past work. Agent extracts real skills, translates credentials into German-market equivalents, and produces a ranked list of *specific open roles they have a realistic shot at today*, plus the 1-2 skills that would unlock 10x more roles with a free course link attached.

**Theme:** Employment access, economic exclusion, credential recognition

**Partner tech (all load-bearing):**
- **Gemini 3** - multimodal CV + certificate extraction, skill mapping, long-context matching against live job boards
- **Tavily** - live scrape of Bundesagentur fuer Arbeit, StepStone, LinkedIn public listings
- **Qontext** - stores the candidate's skill graph across sessions so follow-ups get smarter
- **Gradium** - voice interface for users who can't type well in German
- **Lovable** - the candidate dashboard

**The wow moment:** A teammate drops in a photo of a real Ukrainian engineering diploma + a 30-second voice note in broken German describing 8 years of experience. Ninety seconds later: 12 ranked Berlin roles with realistic match scores, one-click CV tailored per role, and "add PostgreSQL in 3 weeks via this free course to unlock 47 more roles."

**Technical complexity:** High. Multimodal + translation + credential-equivalence reasoning + live market scraping + ranking.

**Feasibility in 15h:** Yellow. Pre-scrape 200 live Berlin job listings on Saturday night so the demo is fast. Credential-equivalence logic is the interesting engineering.

**Business potential:** Paid by integration employers (diversity hiring quotas, Bundesagentur contracts), refugee NGOs, corporate CSR budgets. Market parallel: Handshake for students, Welcome.US for refugees. Germany has no equivalent.

**First-person authority:** Maximum for Ian. Currently job-hunting in Berlin, has lived the "my skills don't map cleanly to German job posts" frustration, and WorkScanAI is literally the employer-side inverse of this.

**Scores:** Creativity 5/5, Complexity 5/5, Partner fit 5/5, First-person authority 5/5, Business story 5/5
**Average: 5.0/5**

---

### Idea 4 - TriageLine: WhatsApp-first multilingual symptom triage

> In Berlin, hundreds of thousands of residents don't have a Hausarzt and can't easily get one. A user sends symptoms to a WhatsApp number in any form - text, voice, or a photo of a rash or eye. Agent runs a safe structured triage in the user's language (Turkish, Arabic, Ukrainian, Russian, English, German), outputs a clear next step - "ER now", "GP within 3 days", "self-care, here's what to watch for" - and for urgent cases calls KV-116117 or finds an open walk-in clinic in real time.

**Theme:** Treatment access, healthcare inequality, language barriers

**Partner tech (all load-bearing):**
- **Gemini 3** - multimodal (text + voice + image) + multilingual safety-critical reasoning
- **Gradium** - voice input/output for users who can't read well in any written language
- **ai|coustics** - cleans symptom voice notes recorded in noisy home conditions
- **telli** - makes the outbound triage booking call to 116117 or walk-in clinics
- **Tavily** - live walk-in clinic availability

**The wow moment:** Send a WhatsApp voice note in Turkish describing chest pain and nausea. Twenty seconds later, the system replies in Turkish: "this is potentially a cardiac event, calling 116117 for you now" - and you hear the agent place the call live.

**Technical complexity:** Very high - safety-critical multilingual medical reasoning with voice + vision + phone dispatch. Jury will respect this.

**Feasibility in 15h:** Yellow. Scope to 3 languages and 5 symptom categories. The safety framing (clear "not a doctor" disclaimer, always defaults to escalation on ambiguity) is critical and must be on-screen in the demo.

**Business potential:** Paid by public health authorities (Senatsverwaltung fuer Gesundheit, equivalents in other cities), by NGOs serving migrant health, by employers providing health benefits. Adjacent market: Babylon Health, Ada Health - both have grown into major businesses.

**Safety note:** The demo must foreground the safety disclaimer; the jury's January winner built in healthcare and the jury rewarded responsibility, not just cleverness.

**Scores:** Creativity 5/5, Complexity 5/5, Partner fit 5/5, First-person authority 3/5, Business story 5/5
**Average: 4.6/5**

---

### Idea 5 - BreathRoute: Berlin's real air-quality routing for people who can't just "go outside"

> Berlin has wildly uneven air quality between streets a block apart. For a kid with asthma, an elderly person with COPD, or someone in their third trimester, "nice day for a walk" is not a universal statement. BreathRoute takes your personal risk profile (asthma, COPD, pregnancy, heart disease) and gives you two outputs: (1) a 1-5 "go outside today" score for your exact postcode, and (2) a walking, cycling, or Kinderwagen-compatible route that minimizes your specific exposure - around that one construction site on Karl-Marx-Strasse, away from the A100 when wind comes from the south.

**Theme:** Environmental health, chronic respiratory illness, pregnancy safety

**Partner tech (all load-bearing):**
- **Gemini 3** - multimodal reasoning over air quality sensor data + weather + traffic patterns + the user's health profile, personalized explanation
- **Tavily** - live scrape of Berlin's UBA air-quality stations, Senatsverwaltung construction permits (huge particulate source), traffic data
- **Gradium** - voice output for elderly users; voice input for "how is my breathing right now, should I go to my doctor"
- **Qontext** - longitudinal tracking of your exposure days, flags when cumulative PM2.5 exposure crosses thresholds that matter for your condition
- **Lovable** - the map dashboard

**The wow moment:** On stage, drop a Berlin postcode and pick "6-year-old with mild asthma." Thirty seconds later: the block-by-block AQI map, today's "go outside" score of 3/5, and three alternative routes from this address to the nearest Spielplatz color-coded by cumulative PM2.5 exposure. The best route is 4 minutes longer and reduces exposure by 62 percent.

**Technical complexity:** High. Fine-grained air-quality interpolation + medical-condition-specific thresholds + route optimization under a non-standard cost function is real engineering.

**Feasibility in 15h:** Yellow. UBA sensor data is public; the interpolation between sparse sensors is the interesting bit. Scope to one Berlin Bezirk for the demo.

**Why it's life-improving in Berlin:** Berlin has roughly 170,000 children with asthma, 60,000 residents with COPD, and 35,000 pregnancies per year. None of them currently get personalized exposure guidance. Air-quality apps show a single number for the whole city, which is medically useless.

**Scores:** Creativity 5/5, Complexity 5/5, Partner fit 4/5, First-person authority 3/5, Life-impact 5/5
**Average: 4.4/5**

---

### Idea 6 - FirstFour: live CPR coaching while the Notarzt is still on its way

> Berlin's ambulance arrival time has stretched past 12 minutes in many districts. Cardiac arrest survival drops roughly 10 percent for every minute without CPR. The first four minutes are when bystanders decide whether someone lives. FirstFour is a WhatsApp/phone line that takes over the moment you call 112: parallel to the dispatcher, it calmly voice-coaches you through CPR using the phone's camera to check your hand position and compression depth, talks you through AED retrieval, and keeps you from panicking. When the Notarzt arrives, it hands off a 60-second structured summary of what happened - compressions given, breathing status, estimated time down.

**Theme:** Emergency response, cardiac arrest survival, bystander CPR

**Partner tech (all load-bearing):**
- **Gemini 3** - multimodal: watches your hands via phone camera while coaching your voice, judges compression depth and rate, detects if the patient is breathing
- **Gradium** - calm, clear voice coaching under extreme user stress (voice quality matters more here than almost anywhere)
- **ai|coustics** - cleans up frantic home audio so the system can hear the patient's breathing and your questions
- **telli** - the phone line itself, and the handoff call to arriving paramedics
- **Qontext** - keeps track of what's been done so the handoff summary is accurate

**The wow moment:** Live on stage, a teammate pretends their colleague collapsed. They call the demo number on speakerphone. The agent's voice coaches them through the first 90 seconds: "kneel beside them, hands one on top of the other on the breastbone, push hard and fast, I'll count with you, one, two, three, four..." At 90 seconds a "paramedic arrives" and the agent immediately generates a spoken handoff summary on the line.

**Technical complexity:** Very high. Voice + vision + real-time coaching under stress + calm-but-urgent persona + clean handoff. Safety-critical by definition.

**Feasibility in 15h:** Yellow. The phone camera + Gemini vision on hand position is the hard part; we demo this with a pre-recorded compressions clip if live vision is not reliable enough.

**Why it's life-saving in Berlin:** Berlin has roughly 8,000 out-of-hospital cardiac arrests per year. Current bystander-CPR rate is under 40 percent. Every point of improvement is lives saved. This is not a business pitch; it is a "build it because someone in Berlin dies every week who should not have" pitch.

**Safety framing:** Demo must include the 112-first disclaimer, the "hand off to dispatcher instantly, do not replace" disclaimer, and the "all suggestions follow ERC 2025 guidelines" credibility line.

**Scores:** Creativity 5/5, Complexity 5/5, Partner fit 5/5, First-person authority 3/5, Life-impact 5/5
**Average: 4.6/5**

---

### Idea 7 - SafeWord: discreet help when you can't say what's happening

> A domestic abuse victim often cannot say what is happening to them. The Hilfetelefon is overwhelmed and phone-only. SafeWord is a voice-first agent that looks and sounds like anything else - a food delivery app, a weather check-in, a fake language-learning lesson - chosen by the user in advance. Saying a specific phrase ("I'd like the vegetarian option tonight") triggers a silent workflow: precise location captured, Berlin-specific safe-house availability queried in real time, a trusted contact notified, and if needed police dispatched with a precise description of the situation the victim has pre-written in safe moments. The interface stays innocent the whole time.

**Theme:** Domestic violence, acute personal safety, coercive control

**Partner tech (all load-bearing):**
- **Gemini 3** - natural-sounding cover conversation that can run for minutes while doing work in the background
- **Gradium** - voice that can match the cover persona (food delivery, friend, meditation app)
- **Tavily** - live Berlin safe-house availability (Frauenhaus beds are scarce and change hourly), nearest police station, open counseling services right now
- **telli** - places the notification call to a trusted contact or emergency services, speaking the pre-written situation description on the victim's behalf
- **Qontext** - the victim's pre-written "escape plan" maintained privately and available the second the safe word fires

**The wow moment:** On stage, a teammate opens what looks like a meditation app, says "I want to try the calming breath exercise for tonight." The app replies calmly about breathing. Meanwhile, on a second screen, the operator dashboard shows: GPS locked, Frauenhaus Spandau has 1 bed, trusted contact notified by SMS, outbound call to a listed friend ready to dial. The victim's interface never breaks character.

**Technical complexity:** High. Dual-track conversation (innocent foreground + urgent background) + trigger detection without false positives + real-time Frauenhaus capacity queries.

**Feasibility in 15h:** Yellow. The cover-app illusion is the visible engineering feat. Scope to one cover persona and Berlin-only safe-house list for the demo.

**Why it's life-saving in Berlin:** Berlin records over 16,000 domestic-violence cases per year and the numbers are rising. The Hilfetelefon receives hundreds of thousands of calls nationally per year and cannot reach everyone; many victims can never call openly. Covert help is an unmet need that existing systems cannot serve because they require the victim to speak freely.

**Safety and ethics framing:** Demo must discuss the false-positive risk, the trusted-contact safeguard, and the collaboration model with Berlin Frauennotrufe. This is the kind of idea that wins a jury precisely because the team has thought hard about the failure modes.

**Scores:** Creativity 5/5, Complexity 5/5, Partner fit 5/5, First-person authority 2/5, Life-impact 5/5
**Average: 4.4/5**

---

### Idea 8 - HeatGuard: the Berlin heatwave safety net for people who have nobody

> Berlin's 2024 and 2025 summers had documented excess deaths during heatwaves, concentrated among isolated elderly residents in top-floor flats without cooling. Current "heatwave warnings" on weather apps do nothing for someone who does not check weather apps. HeatGuard is different: during forecast heat emergencies, it calls registered at-risk residents proactively with a 2-minute voice check ("how are you feeling, have you drunk water today, do you have a fan running"), dispatches volunteer checkers to anyone who does not answer two calls in a row, and coordinates with Berlin's Kuehlraum network so the system actually suggests a cool refuge the person can walk to.

**Theme:** Climate health, elder isolation, heat-related mortality

**Partner tech (all load-bearing):**
- **telli** - the core. Warm outbound calls to elderly residents who cannot install apps.
- **Gradium** - natural voice conversation that does not sound robotic (elderly users hang up on robot voices fast)
- **ai|coustics** - elderly phones are often poor quality; audio cleanup is load-bearing
- **Gemini 3** - distress detection from voice (slurred speech, confusion, weakness = possible heatstroke), conversational check-in flow, dispatch decision
- **Tavily** - live Berlin Kuehlraum / cooling-center availability, weather forecasts, subway stations used as informal cool spaces
- **Qontext** - keeps the resident's profile (top-floor yes/no, medications that affect heat response, mobility)

**The wow moment:** Live on stage, simulate a 38-degree day. A teammate plays an 83-year-old in a top-floor Neukoelln flat. The agent calls, has a warm 90-second conversation, picks up subtle confusion in the person's voice, and immediately dispatches a volunteer ("we would like to send someone round to check on you within the hour") while listing two cool spaces within walking distance.

**Technical complexity:** Medium-high. Voice-quality distress detection is the technical flex; the orchestration layer is also non-trivial.

**Feasibility in 15h:** Green. Most components are straightforward; the distress-detection prompt is the one piece to iterate on.

**Why it's life-saving in Berlin:** Heat mortality is rising every year. Berlin's demographic skew means the number of isolated elderly in heat-vulnerable housing is growing. This problem gets worse, not better.

**Scores:** Creativity 4/5, Complexity 4/5, Partner fit 5/5, First-person authority 3/5, Life-impact 5/5
**Average: 4.2/5**

---

### Idea 9 - MindBridge: psychiatric help available tonight, matched to who will actually take you

> Berlin's psychiatric emergency system is gridlocked. Walking into a Klinik often means a multi-hour wait followed by a referral you cannot get for six weeks. In acute mental health crisis, six weeks might as well be six years. MindBridge is a voice-first agent that triages the user's current state, queries real-time availability across Berlin's crisis services - Krisendienst, Sozialpsychiatrischer Dienst, specific private practices that take walk-ins, specialized services for LGBTQ+ / migrant / young adults - and finds the closest place that has capacity tonight and will see the user without a Hausarzt referral. If nothing is available in person, it matches to an online therapist who can see them in the next 4 hours.

**Theme:** Mental health access, crisis care, psychiatric emergency

**Partner tech (all load-bearing):**
- **Gemini 3** - safe triage of mental-health state (never diagnostic; always refers), multi-criterion matching against service capacity
- **Gradium** - voice-first interaction because users in crisis often cannot navigate text interfaces
- **ai|coustics** - cleans crisis-state audio (tears, rapid breathing, background noise)
- **Tavily** - live capacity scraping across Krisendienst, Jugend-KJP, Frauenkrisentelefon, specialist LGBTQ+ and migrant services
- **telli** - calls the identified service on the user's behalf to hold an appointment slot while the user is still on the line
- **Qontext** - keeps the journey state across nights so a user returning in a week does not start from zero

**The wow moment:** Live, a teammate says calmly, "I haven't slept in four days and I'm scared of what I'm thinking about." The agent responds warmly, asks two safety-triage questions, finds three services taking walk-ins this evening within 20 minutes transit, calls the best-matched one to hold a slot, and returns to the user with the address, contact name, and transit route - all in under 2 minutes.

**Technical complexity:** Very high. Safety-critical triage + real-time capacity + empathic tone + live outbound coordination call. This is as technically deep as MedAccura was.

**Feasibility in 15h:** Yellow. The live-capacity data is the hardest piece; scope the demo to 5 Berlin services with simulated-live availability backing onto real phone numbers.

**Why it's life-saving in Berlin:** Berlin has one of the highest rates of young-adult mental health crises in Germany. Waiting lists are documented to be 12+ weeks for standard psychotherapy. Crisis services exist but their availability is opaque. People suffer avoidably in the gap.

**Safety framing:** Demo must foreground Berliner Krisendienst as the primary escalation, include a clear "if you are in immediate danger, 112 is the answer" disclaimer, and show the always-on suicide-prevention protocol.

**Scores:** Creativity 5/5, Complexity 5/5, Partner fit 5/5, First-person authority 3/5, Life-impact 5/5
**Average: 4.6/5**

---

### Idea 10 - PillPath: the polypharmacy safety check your GP doesn't have time to do

> Many elderly Berliners take 7+ prescription medications - one from the cardiologist, one from the diabetologist, three from the GP, two over-the-counter. Nobody is looking at the whole picture. Dangerous interactions are a leading cause of avoidable hospital admissions in over-75s. PillPath lets the patient or a family member photograph every medication box they have. The agent extracts all drugs, cross-references every pairwise interaction against current clinical databases, flags dangerous combinations in plain language ("your blood thinner and the new pain medicine together triple your bleeding risk"), and generates a one-page summary the patient can bring to their next GP visit.

**Theme:** Medication safety, elderly care, polypharmacy-related hospital admissions

**Partner tech (all load-bearing):**
- **Gemini 3** - multimodal: photographs of medication boxes to structured drug list, pairwise and n-way interaction reasoning, plain-language explanation at the user's reading level
- **Tavily** - live clinical interaction databases (ABDA-Datenbank, Rote Liste), drug-safety bulletins from BfArM, recall notices
- **Gradium** - voice output because reading small text is hard for elderly users; voice input for listing symptoms
- **Qontext** - the medication list maintained longitudinally so every new prescription gets checked against what's already there
- **Lovable** - the dashboard and the GP-visit handout

**The wow moment:** On stage, a teammate piles 8 real (empty) medication boxes on a table and photographs them together. Ninety seconds later: complete drug list extracted, two critical interactions flagged in red with plain-language explanations, one moderate interaction in amber, and a one-page printable summary for the next GP visit. A judge who is a doctor will gasp.

**Technical complexity:** High. The multimodal extraction from cluttered photographs + the n-way interaction reasoning (not just pairwise) is genuinely hard.

**Feasibility in 15h:** Green. Interaction databases are accessible; the photo extraction is the one piece to prototype early. Pre-test with 5 real medication sets.

**Why it's life-saving in Berlin:** Medication-interaction-related hospital admissions in Germany are estimated at over 250,000 per year in elderly patients. A single good polypharmacy review prevents on average 2-3 admissions per patient per year. This is a massive, measurable, unmet need.

**Scores:** Creativity 5/5, Complexity 5/5, Partner fit 4/5, First-person authority 3/5, Life-impact 5/5
**Average: 4.4/5**

---

### Idea 11 - GoldenPath: getting to the RIGHT hospital in the therapeutic window

> For a stroke, you have roughly 4.5 hours from symptom onset to get tPA thrombolysis. For a heart attack, roughly 90 minutes for stenting. The closest hospital is often NOT the right hospital - only some Berlin hospitals are certified stroke units, only some run 24/7 cath labs. Ambulances usually route correctly, but Ubers, family members driving, and people who walk into the wrong ER waste the therapeutic window. GoldenPath is called by a family member when they recognize symptoms ("my mother's face is drooping and she can't raise her left arm"). It confirms stroke vs non-stroke in 30 seconds, identifies the nearest certified stroke unit with current bed availability, dispatches an ambulance, and if the family is already driving, redirects them AND calls the receiving hospital ahead to prep the team.

**Theme:** Cardiovascular emergency, therapeutic window, hospital routing

**Partner tech (all load-bearing):**
- **Gemini 3** - multimodal symptom triage (voice description + optional video of the person's face for facial-droop detection), real-time routing reasoning
- **Gradium** - calm voice guidance for the panicking family member
- **ai|coustics** - cleans frantic-car or frantic-home audio
- **telli** - parallel calls: 112, redirect family driving, warn receiving hospital team
- **Tavily** - live bed/team availability across Berlin stroke units and cath labs (this data exists in hospital systems; Berlin has been working on a central registry)
- **Qontext** - keeps the event state as it unfolds so any handoff has complete context

**The wow moment:** Live on stage, a teammate panicked: "my father just started slurring his words and his right arm fell down when I asked him to raise it." The agent responds calmly in 5 seconds: "this is a possible stroke. I have already called 112. The best hospital for you is Charite Campus Benjamin Franklin, not the closer one - they are certified and have capacity. Do not drive; ambulance will be 8 minutes. Here is what to do while you wait." Simultaneously, the operator dashboard shows: 112 called, Charite CBF notified, family GPS tracked.

**Technical complexity:** Very high. Safety-critical multimodal triage + multi-party phone orchestration + live hospital data.

**Feasibility in 15h:** Yellow. Hospital bed data is the risk; we fake-live it for the demo but frame it as a public data gap we would work to close post-hackathon.

**Why it's life-saving in Berlin:** Stroke is a leading cause of disability in Germany. Treatment delays translate directly to lifelong disability. The routing-to-right-hospital gap is real and documented; Berlin's stroke registry work is public policy.

**Scores:** Creativity 5/5, Complexity 5/5, Partner fit 5/5, First-person authority 2/5, Life-impact 5/5
**Average: 4.4/5**

---

### Idea 12 - FoundSafe: the first 24 hours when a vulnerable adult goes missing

> When a person with dementia, a mental-health episode, or a cognitive disability wanders off in Berlin, the first 24 hours are decisive. Right now, the family's response is phone calls and panic. Police get involved but have limited resources for non-criminal missing persons. FoundSafe coordinates the first-24-hour response: it ingests everything the family can give (last seen where, photo, clothing, medical needs, places the person feels safe), alerts a verified volunteer network in the precise Berlin neighborhood, queries hospital admissions and police checkpoints for matching persons, and acts as a single coordinator so the family does not have to call 30 places while losing their mind.

**Theme:** Dementia care, mental health crisis, missing vulnerable adults

**Partner tech (all load-bearing):**
- **Gemini 3** - multimodal profile building (photo + description + medical needs), continuous matching against reports
- **Tavily** - live queries against hospital admission notices, police missing-persons channels, BVG lost-and-found, homeless outreach logs
- **telli** - the coordination calls - checking with hospitals, shelters, known safe spots, family members
- **Gradium** - the distressed family member can give everything they know by voice in one go instead of filling forms
- **Qontext** - the live search state: who's been called, what's been checked, when the last lead was, preventing the family from re-covering the same ground

**The wow moment:** Live on stage, a teammate plays a daughter whose 78-year-old father with early dementia left the flat in Pankow 2 hours ago. She tells the agent everything by voice in 60 seconds. The operator dashboard lights up: photo distributed to 14 volunteers in 800-meter radius around last-seen location, 3 hospitals called, BVG alerted, U-Bahn stations flagged, family's phone ringtone set to escalate on any match. She does not make a single other call herself.

**Technical complexity:** High. The orchestration + volunteer-network coordination + live multi-source querying under emotional pressure is the engineering.

**Feasibility in 15h:** Yellow. The volunteer network is the policy question; for the demo, "14 volunteers notified" is a simulated geo-targeted push.

**Why it's life-improving in Berlin:** Berlin has a significant and rising population with dementia (estimated 60,000+ in the Berlin region) and a large homeless / mental-health crisis population. Missing-person episodes are more common than anyone realizes. Current response is amateur-hour by default.

**Scores:** Creativity 5/5, Complexity 4/5, Partner fit 5/5, First-person authority 2/5, Life-impact 5/5
**Average: 4.2/5**

---

### Summary ranking

| # | Idea | Theme | Score | Why it ranks here |
|---|---|---|---|---|
| 3 | **JobMatch Reverse** - candidate-first job platform | Employment access, Ian's authority | **5.0** | Max first-person authority for Ian; multimodal credential reasoning is a genuine 2026-capability demo. |
| 1 | **HireSignal** - JD to adaptive skills interview | Hiring fairness, Ian's authority | 4.8 | Strongest personal story + voice + adaptive reasoning is a real technical flex. |
| 4 | **TriageLine** - multilingual WhatsApp triage | Healthcare access | 4.6 | Safety-critical multilingual health reasoning; Berlin's underserved non-German-speaking population is enormous. |
| 6 | **FirstFour** - live CPR coaching during 112 call | Cardiac arrest survival | 4.6 | Directly life-saving, visible on-stage demo, and the vision-on-hands coaching is a flag-planting 2026 capability. |
| 9 | **MindBridge** - psychiatric help tonight matcher | Mental health crisis | 4.6 | Safety-critical; addresses a well-documented Berlin crisis-care gap; emotional-narrative pitch lands hard. |
| 5 | **BreathRoute** - personalized air-quality routing | Environmental health | 4.4 | Affects hundreds of thousands of Berliners with respiratory conditions; personalization is the wedge existing apps miss. |
| 7 | **SafeWord** - discreet domestic-abuse help | Personal safety | 4.4 | Dual-track conversation is a genuinely novel interaction pattern; solves a problem current systems structurally cannot. |
| 10 | **PillPath** - polypharmacy interaction checker | Medication safety, elderly | 4.4 | Massive measurable impact on avoidable hospital admissions; multimodal extraction is the demo moment. |
| 11 | **GoldenPath** - stroke/cardiac hospital routing | Therapeutic-window emergency | 4.4 | Routes patients to the RIGHT hospital, not the closest; jury's medical judge will immediately understand the impact. |
| 2 | **StandUpAgent** - async voice standup | Universal dev pain | 4.2 | Kept for team-familiarity fallback; weaker jury differentiation. |
| 8 | **HeatGuard** - heatwave check-in network | Climate health, elderly | 4.2 | Climate-adjacent angle appeals to younger jury members; telli's canonical use case. |
| 12 | **FoundSafe** - missing vulnerable adult coordinator | Dementia, crisis response | 4.2 | Emotional narrative + multi-source orchestration; harder to scope for a clean 2-minute demo. |

### The meta-observation

**Every idea in the new top tier (5.0 / 4.8 / 4.6 / 4.6 / 4.6) passes the "does this save or materially improve Berlin lives?" test.** The framing for the 2-minute video should be a real Berlin scenario, told in first person when possible ("my grandmother lives in a top-floor flat in Wedding..." or "last August, I called 112 for a neighbor and the dispatcher was overwhelmed..."), not a product pitch.

**The shift in this pass:** previous iterations leaned on existing business analogs for credibility. That framing is dropped. Every idea here is justified by the Berlin-specific problem it solves and by a 2026-AI capability (multimodal reasoning on photos/video/voice, parallel phone orchestration, real-time multi-source data synthesis) that would not have been possible 18 months ago. The jury will recognize this; it is exactly the flavor MedAccura won on in January.

**Tiebreaker rule:** when scores are tied, prefer the idea where the team can credibly demonstrate the "wow moment" live on stage in under 2 minutes, with a visible before/after and a palpable human stake. By that rule the practical shortlist is:

- **FirstFour** (cardiac arrest coaching) - highest emotional stakes, hardest technical flex, visibility of multimodal vision+voice
- **MindBridge** (mental health tonight) - safety-critical reasoning + live outbound coordination
- **GoldenPath** (stroke/cardiac routing) - the doctor-judge test: would a physician immediately say "I need this in my ER"
- **PillPath** (polypharmacy) - most tractable in 15h; huge measurable impact

If Ian's first-person authority angle carries weight for the team, **JobMatch Reverse** and **HireSignal** remain the personal-story choices.

**Strong recommendation:** Lock the decision between **FirstFour**, **MindBridge**, and **JobMatch Reverse**. FirstFour for maximum jury impact and technical showcase. MindBridge for mission depth. JobMatch Reverse for execution reliability and Ian's first-person story.

---

## How we'll pick the final idea

### Pre-event (this week)

1. Share this README with every team member.
2. Each person picks their top 2 and scores on the same five-criterion rubric.
3. **45-minute call** where we converge on top 2.
4. For each of the top 2, do a 30-minute "demo video walkthrough" exercise: one person narrates what the 2-minute submission video shows, shot by shot. **If we can't narrate a compelling video now with no code, we can't make one in 15h with code.**
5. Pick 1 primary + 1 backup.

### At the event (Saturday morning)

- Confirm the sponsor briefings align with our assumptions about what each partner tool can do. If something we assumed is wrong (e.g. telli doesn't support outbound to Germany), pivot to the backup *in the first 90 minutes*, not at hour 8.
- Matchmake aggressively. If someone at the event has exactly the domain authority our idea needs (a nurse for a health idea, a landlord for TenantTriage), **invite them onto the team**. Teams of 4-5 out-deliver teams of 2 in the final 3 hours.

### The irreversible decision deadline

**By Saturday 20:00 (7h before we actually start coding), the idea is locked.** No pivots after that unless something is literally on fire.

---

## Team roles & division of labor

A 2-person team is viable. A 3-person team is ideal. A 4-person team is excellent if the communication overhead is managed. Suggested roles:

| Role | What they own | Headcount |
|---|---|---|
| **Lead / Architect** | Idea coherence, end-to-end demo, submission video script, pitch. Also owns the Gemini / agent reasoning layer. | 1 (Ian suggested) |
| **Backend / Data** | Tavily queries, data pipelines, any RAG, API glue, telli/Gradium integration if voice. | 1 |
| **Frontend / UX** | Lovable-driven UI, demo polish, recording the submission video with Hera if time allows. | 1 |
| **Domain / Pitch** | Owns the problem framing, talks to sponsor mentors, writes the pitch deck, narrates the video. Does light frontend or data work as bandwidth allows. | 1 (critical if the pitch needs domain credibility - see MedAccura) |

### Ian's stack fits these slots cleanly

Given Ian's Next.js / FastAPI / Claude-or-Gemini integration experience plus the WorkScanAI muscle memory for ingestion + agent orchestration, **Lead / Architect** is the natural slot - with the option to float into Backend if a teammate has stronger product-design chops.

### Tooling expectations on the day

- Desktop Commander MCP + Claude in Chrome MCP are force multipliers - walk teammates through these in the first hour. File edits, git ops, browser automation for testing all run through them.
- Git repo: one of us creates the repo at 10:30 (right after kickoff briefing), branch = `main`, no PR workflow, just direct commits. Hackathon mode, not production.
- Decision log: pinned Discord thread or a `DECISIONS.md` in the repo - every non-trivial fork gets one line. When the 2am exhaustion hits, this is how we avoid re-litigating.

---

## Timeline: Saturday night → Sunday 14:00

### Saturday (pre-night)

| Time | What's happening | Our move |
|---|---|---|
| 10:00 | Doors open, networking | Arrive, set up, scope out sponsor mentors for the tools we want to use |
| 10:30 | Opening & matchmaking | If our team isn't full, recruit. Target: domain-authority teammate if our idea needs one. |
| 12:30 | Lunch | **Idea locked by now.** Eat fast. |
| 13:00-19:00 | Most teams start building | We're still planning and skeleton-scaffolding. Don't panic. |
| 19:00 | Dinner | Last checkpoint before the real sprint. Eat, then begin the actual build. |
| 20:00 | **Idea lock hard deadline** | If still flip-flopping, commit to the highest-scoring option. No more debate. |

### Saturday night → Sunday (the real ~15h sprint)

| Time | Goal | Output |
|---|---|---|
| 20:00-22:00 | **Skeleton + partner integrations smoke-tested** | Each of the 3+ partner APIs returns a real response. No UI yet. |
| 22:00-00:00 | **Happy-path end-to-end** | One input goes in, one usable output comes out - even if ugly. |
| 00:00-02:00 | **The "wow moment" works** | The single demo-video shot is reliable and reproducible. |
| 02:00-04:00 | Sleep rotation. At least 2 people sleep 3-4h. Nobody codes on no sleep past this point. |
| 04:00-07:00 | **Second pass on core + edge cases** | Demo doesn't break on the second run. |
| 07:00-10:00 | Everyone back. **Polish pass.** | UI cleanup via Lovable, copy polish, error handling on the demo path. |
| 10:00-12:00 | **Record the 2-minute submission video** | Multiple takes. Best take wins. |
| 12:00-13:30 | Buffer for technical issues + upload | Submit **early**, not at 13:59. |
| 14:00 | **Submission deadline** | Don't be the team that missed it. The article noted some teams didn't submit in time. |
| 15:30 | Finalists announced (3 teams) | - |
| 16:00 | Finalist pitches (5 min each) | If we're here, pitch rehearsal happens during the 15:00 wait. |
| 17:30 | Award ceremony | - |

### The 3 rules we will not break

1. **No new features after 02:00.** After 2am we only polish what works.
2. **No debugging during the video recording window (10:00-12:00).** If something breaks at 10:30, we cut it from the demo and record without it.
3. **Submit by 13:30.** One hour of buffer before the 14:00 deadline is non-negotiable.

---

## Submission checklist

Exactly what the jury sees. Nothing more, nothing less.

- [ ] **2-minute video** (hard ceiling). Shows: the problem, the wow moment (single clean shot), partner tools credited visibly, one sentence on "what we'd do next."
- [ ] **Working demo URL** (Lovable / Vercel / wherever). Reliable on Sunday afternoon network conditions.
- [ ] **GitHub repo** public with a README that credits every partner tool used.
- [ ] **One-slide deck** for the optional live pitch if we make finalists.
- [ ] **Team names + contact** on the submission form.
- [ ] **Partner tools list** explicitly listed - judges give bonus points for effective use; make it easy for them to check.

### The 2-minute video skeleton

- 0:00-0:15 - The problem, told as a first-person story. Not "businesses face a challenge in..." - **"Last Tuesday I was..."**
- 0:15-0:30 - What we built, in one sentence. Show the name and logo.
- 0:30-1:30 - The demo. One continuous shot if possible. This is where the wow moment lives.
- 1:30-1:45 - Which partner tools and how each one is load-bearing (one sentence each).
- 1:45-2:00 - What this becomes if we keep building. **Include the "we're keeping going after the hackathon" line.** MedAccura did this, and the jury responded.

---

## Appendix: what we learned from the January 2026 edition

Source: Leandra Finke's coverage in Gründerszene / Business Insider, 27 January 2026.

- **105 participants from 600 applicants** - ~6x oversubscribed. Expect similar at Big Berlin Hack.
- **27 projects submitted** out of ~30 teams - some didn't finish. Being in the "submitted" cohort already filters you into the top 90%.
- The jury evaluated on **creativity + technical complexity**, with **bonus points for effective partner tech use**. This exact rubric is the one we're optimizing for.
- The winner's jury citation emphasized **"great technical depth realized in a very short time"** and **real-world impact** - framing that rewards working software over slideware.
- Organizer Bela Wiertz's on-the-ground philosophy: *"The goal isn't maximum complexity - it's joy in the product. It's allowed to be light as long as it works."* We take this seriously. Don't over-engineer.
- The winning team explicitly said they'd **continue the project after the event**. Jury likes signals of durability.

---

## Contact

Ian - Full-stack / project lead
🌐 [ianworks.dev](https://ianworks.dev)
💼 [linkedin.com/in/avoiann](https://linkedin.com/in/avoiann)
💻 [github.com/ibxibx](https://github.com/ibxibx)

Berlin AI/tech community: GlobalAI Berlin, AgentCon Berlin 2026.

---

**See you at Delta Campus, 25 April. 🚀**
