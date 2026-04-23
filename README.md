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

Each idea is scored 1-5 on the five strategic filters. These 12 ideas survived an initial filter of ~30 candidates. The original shortlist was dominated by SaaS/dev-tool angles; on Ian's direction we replaced six of them with ideas targeting more acute daily problems - access to medicines and treatment, joblessness and discrimination in hiring, income inequality, and food/water accessibility. Two original ideas (HireSignal, StandUpAgent) were retained.

Legend for difficulty dots: 🟢 feasible in 15h · 🟡 tight but doable with discipline · 🔴 only if a teammate has prior art in the exact stack

---

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

### Idea 3 - MedBridge: Find the medicine you can actually get (and afford) today

> Patient or caregiver enters the drug name on their prescription. Agent checks live pharmacy stock across the city, flags shortages, finds approved generic equivalents and their price delta, checks whether the patient's insurance covers each option, and - if everything is out of stock - calls pharmacies directly to ask about expected restock. For expensive drugs, surfaces patient-assistance programs the patient qualifies for.

**Theme:** Disease / access to medicines

**Partner tech (all load-bearing):**
- **Tavily** - real-time pharmacy stock lookups and patient-assistance program discovery
- **Gemini 3** - parses prescriptions (photo OK), reasons about generic equivalence and insurance eligibility
- **telli** - phones pharmacies to confirm stock when web data is stale
- **Gradium** - voice-first entry point for elderly caregivers who won't type drug names
- **Lovable** - frontend

**The wow moment:** Jury member photographs a (fake) prescription. In 45 seconds: "In-stock at 3 pharmacies within 2 km; one generic equivalent saves EUR 42 and is on your Techniker Krankenkasse formulary; click to hear the call confirming stock at Apotheke am Hermannplatz."

**Technical complexity:** High. OCR, drug knowledge base, insurance-formulary reasoning, live calling. Multi-agent.

**Feasibility in 15h:** Tight. We ship with 20 hand-curated drugs and 5 Berlin pharmacies for the demo, explicitly label it as the "pilot dataset." Judges understand scope caveats.

**Risks:** Pharmacy data is private/scraped; pitch must say "with pharmacy partnerships, this scales." Don't oversell.

**Scores:** Creativity 5/5 - Complexity 5/5 - Partner fit 5/5 - First-person authority 3/5 (strong if a teammate has a chronically-ill family member) - Company story 5/5
**Average: 4.6/5**

---

### Idea 4 - TriageLine: WhatsApp-first symptom triage for people without a family doctor

> In Berlin, 200k+ people don't have a Hausarzt and can't get one. A user sends symptoms to a WhatsApp number - text, voice, or photo. The agent runs a structured triage interview in their language (including Turkish, Arabic, Ukrainian, Russian), outputs a clear next step ("this needs the ER now" / "book a GP within 3 days" / "can wait, here's self-care"), and - for urgent cases - calls KV 116117 or finds an open walk-in clinic right now.

**Theme:** Disease / access to treatment

**Partner tech (all load-bearing):**
- **Gemini 3** - multilingual triage reasoning, image understanding (rash photos, injury photos)
- **Gradium** - voice notes in any language, replies by voice
- **ai|coustics** - cleans noisy voice notes from parents with crying kids
- **telli** - calls KV 116117 or the nearest walk-in to check wait times
- **Tavily** - live walk-in clinic availability across Berlin

**The wow moment:** Live WhatsApp demo. A "worried parent" sends a voice note in Turkish describing a child's symptoms. 20 seconds later: triage result in Turkish, and if urgent, the demo shows a live call being placed to a clinic asking about wait times.

**Technical complexity:** High. Safety-critical triage requires defensible reasoning. Show that you use established triage protocols (Manchester Triage System) as grounding, not raw LLM guessing. This detail alone moves the jury.

**Feasibility in 15h:** Tight but doable. Use Twilio/WhatsApp Business sandbox, skip the mass onboarding flow.

**Risks:** Medical liability language must be handled carefully in the pitch. Do not claim "diagnosis" - claim "routing."

**Scores:** Creativity 5/5 - Complexity 5/5 - Partner fit 5/5 - First-person authority 4/5 (common Berlin reality) - Company story 5/5
**Average: 4.8/5 (tied top-ranked)**

---

### Idea 5 - JobMatch Reverse: For people locked out of the job market, not the other way around

> Most job platforms optimize for employer search. JobMatch Reverse optimizes for the candidate who is unemployed, long-term jobless, or recently migrated. User uploads whatever they have (a CV in Farsi, a photo of a certificate, a voice note describing past work). Agent extracts real skills, translates credentials, maps them to German-market equivalents, and produces a ranked list of *specific job openings they have a realistic shot at today* - plus the 1-2 skills that would unlock 10x more roles with a free course link.

**Theme:** Joblessness / poverty / unfairness

**Partner tech (all load-bearing):**
- **Gemini 3** - multimodal (photo of certificate, PDF CV, voice in any language) -> structured skills
- **Tavily** - live job board scraping (Bundesagentur fuer Arbeit, Indeed DE, LinkedIn)
- **Qontext** - user profile that grows as they interact
- **Gradium** - voice-first for people who can't navigate forms in German
- **Lovable** - ultra-simple UI (assume low digital literacy)

**The wow moment:** Live demo with a fake applicant: a 52-year-old former Syrian pharmacist. Photo of their diploma goes in. 60 seconds later: 8 matched openings in Berlin/Brandenburg, an honest "your German is your bottleneck, here are 3 free B1 courses starting next week," and one "you qualify as a Pharmareferent via this Anerkennung pathway most people don't know about."

**Technical complexity:** High. Credential recognition in the German context is genuinely hard - this is the differentiation.

**Feasibility in 15h:** Tight. Scope: 3 source countries, 50 occupations. Demo-complete.

**First-person authority:** Ian is in job search himself; WorkScanAI already analyzes job descriptions for AI-automatability. The inverse (analyze a candidate and map to jobs) is a natural port.

**Scores:** Creativity 5/5 - Complexity 5/5 - Partner fit 5/5 - First-person authority 5/5 - Company story 5/5
**Average: 5.0/5 (top-ranked)**

---

### Idea 6 - BenefitFinder: The missing EUR 3,000 you haven't claimed

> Research in Germany says billions in welfare benefits go unclaimed every year because the rules are too complex (Wohngeld, Kinderzuschlag, Bildungspaket, Buergergeld top-ups, energy relief, regional programs). User answers 5 questions by voice. Agent figures out which federal, state, and city-level benefits they qualify for, totals the annual sum, pre-fills every form, and books the Termine.

**Theme:** Income inequality / poverty / unfairness

**Partner tech (all load-bearing):**
- **Gemini 3** - reasoning over benefit-eligibility rules (these are gnarly if-then trees)
- **Tavily** - live regulation changes (rules shift yearly; static systems rot fast)
- **Qontext** - household situation maintained across months
- **telli** - books Termine at Jobcenter / Wohngeldstelle / Familienkasse
- **Gradium** - voice-first, because the target users are exactly the ones who struggle with forms
- **Lovable** - absolute simplicity in the UI

**The wow moment:** 5 voice questions answered in 90 seconds. Output: "Your household qualifies for EUR 2,860/year you're not currently receiving. Here are the 3 applications pre-filled as PDFs and 2 Termine I just booked for you."

**Technical complexity:** High. The eligibility rule engine is the real work; it's exactly the kind of thing that looks like magic when demoed.

**Feasibility in 15h:** Tight. Ship with 5 benefits covered (Wohngeld + Kinderzuschlag + Buergergeld top-up + BaFoeG + local Berlin Familienpass). Label the scope.

**Risks:** Legal accuracy. Pitch says "assist, not advise" - always points the user to the official decision.

**Scores:** Creativity 5/5 - Complexity 5/5 - Partner fit 5/5 - First-person authority 3/5 - Company story 5/5
**Average: 4.6/5**

---

### Idea 7 - RentShield: Know exactly what your landlord is overcharging you

> Tenant uploads their rental contract (photo or PDF). Agent extracts rent, warmth, Nebenkosten, apartment size, year of build, district. Cross-references the official Mietspiegel and similar current listings. Returns a brutal one-pager: "your rent is EUR 187/month above the legal Mietspiegel for this apartment class; here is the exact paragraph of BGB to cite; here is a ready-to-send Mietminderung letter; a lawyer can win this in Berlin with ~85% success rate."

**Track fit:** Buena (property track)

**Theme:** Income inequality / unfairness (rent is the single biggest lever on working-class income in Berlin)

**Partner tech (all load-bearing):**
- **Gemini 3** - contract OCR + extraction + legal reasoning over BGB + Mietspiegel
- **Tavily** - live comparable listings, current Mietspiegel, jurisprudence updates
- **Buena** - track partner; their property data is exactly the reference layer we need
- **Lovable** - frontend
- **Entire** - human-in-the-loop when the contract is ambiguous (a real tenant lawyer reviews the edge cases in the dashboard)

**The wow moment:** Drop in a real Berlin rental contract. 40 seconds later: "You are paying EUR 2,244/year above the legal limit. Here is your pre-drafted Mietminderung. Total recoverable for the last 3 years: EUR 6,732."

**Technical complexity:** High. Mietspiegel parsing and BGB reasoning is non-trivial; the output being legally-citable (not just vibes) is the defining engineering bar.

**Feasibility in 15h:** Tight. Scope to Berlin only (Mietspiegel varies by city).

**Risks:** "Not legal advice" disclaimer front and center. Frame as "prep your case, then see a lawyer."

**Scores:** Creativity 5/5 - Complexity 5/5 - Partner fit 5/5 - First-person authority 5/5 (every Berliner has a rent story) - Company story 5/5
**Average: 5.0/5 (tied top-ranked)**

---

### Idea 8 - FoodReach: Redirect tonight's restaurant surplus to the people who need it most

> Restaurants, bakeries, and supermarkets throw away ~1/3 of their stock every evening. Food banks and shelters can't plan around ad-hoc donations. FoodReach is a two-sided agent: restaurants send a voice note at closing time ("we have 8 kg bread, 20 pastries, salads until 10 pm"), agent auto-matches to the nearest food bank/shelter with capacity and the right dietary mix, and calls a volunteer driver via telli to pick up and deliver. No app installation for the donor side - just a phone number.

**Theme:** Food accessibility

**Partner tech (all load-bearing):**
- **Gradium + ai|coustics** - voice note intake from noisy restaurant kitchens
- **Gemini 3** - matches inventory (halal? allergen-free? refrigerated?) to demand
- **telli** - dispatches volunteer drivers via automated call
- **Tavily** - live food-bank capacity across Berlin
- **Qontext** - tonight's matching is informed by last week's patterns

**The wow moment:** Live during the pitch, someone records a "surplus" voice note. Within 60 seconds the big screen shows: matched recipient (Laib und Seele Kreuzberg), volunteer driver called and confirmed, pickup ETA 22 min. The call recording plays.

**Technical complexity:** Medium-high. The matching is the interesting piece; the voice pipeline is straightforward.

**Feasibility in 15h:** Very feasible. The 2-sided nature is handleable because one side (the donor) is just a phone number.

**Risks:** Hygiene/legal compliance for food redistribution in Germany (Lebensmittelrecht). Acknowledge in pitch; lean on existing partnerships like Die Tafel.

**Scores:** Creativity 5/5 - Complexity 4/5 - Partner fit 5/5 - First-person authority 3/5 - Company story 5/5
**Average: 4.4/5**

---

### Idea 9 - WaterWise: Satellite-driven drought early warning for smallholder farms

> Smallholder farmers in drought-prone regions lose harvests because they don't know water stress is coming until crops visibly fail. WaterWise takes a farm's coordinates, pulls Sentinel-2 satellite imagery weekly, combines with local weather + soil data, and sends a voice message in the farmer's language: "your north field will be water-stressed in 8 days; here's the irrigation priority order; here's a subsidy program you qualify for if you install drip irrigation."

**Theme:** Water accessibility / food security

**Partner tech (all load-bearing):**
- **Gemini 3** - satellite image interpretation + reasoning + multilingual voice generation
- **Tavily** - weather forecasts, soil datasets, subsidy program scraping
- **Gradium** - voice delivery in the farmer's language (literacy often limited)
- **telli** - optional inbound line for farmers to ask follow-up questions
- **Pioneer by Fastino Labs** - small model fine-tuned on regional crop-stress patterns

**The wow moment:** Pin a real farm coordinate on a map. Zoom in, show Sentinel imagery. Gemini annotates water-stress regions. A voice message plays in Swahili / Hausa / Hindi.

**Technical complexity:** High. Geospatial ML plus multilingual voice plus actionable recommendation.

**Feasibility in 15h:** Tight. Use free Sentinel Hub API, pre-cache imagery for 5 demo farms.

**Risks:** Looks "too global" for a Berlin hackathon; pitch must tie it to an EU-funded programme or African diaspora in Berlin.

**Scores:** Creativity 5/5 - Complexity 5/5 - Partner fit 4/5 - First-person authority 2/5 (unless someone on team has ag background) - Company story 4/5
**Average: 4.0/5**

---

### Idea 10 - WageWatch: Know your real market rate before you sign

> Job-seeker pastes an offer. Agent pulls live comparable salaries from public sources (Kununu, Glassdoor, StepStone, LinkedIn salary data), adjusts for role, years of experience, city, company size, and reports: "your offer is 12% below market median for your profile; here are the 3 highest-leverage things to ask for in negotiation based on what this company has conceded in past hires." Optional voice role-play: the agent plays the recruiter, you practice the negotiation call.

**Theme:** Income inequality / unfairness in hiring

**Partner tech (all load-bearing):**
- **Gemini 3** - salary benchmarking reasoning, negotiation coaching
- **Tavily** - live salary data scraping
- **Gradium** - voice role-play for negotiation practice
- **ai|coustics** - clean up the user's practice audio so the feedback is accurate
- **Peec AI** - (track partner) track how your "salary + role" profile shows up in AI career-advice answers
- **Qontext** - progress tracking across multiple offers/negotiations

**The wow moment:** Live negotiation role-play on stage. Judge reads an offer letter aloud. Agent plays recruiter. Judge practices "I was hoping for more." Agent counters. At the end: a scorecard showing where the judge left money on the table.

**Technical complexity:** Medium-high. The role-play voice agent is the flex.

**Feasibility in 15h:** Very feasible. Voice role-play is exactly what Gradium + Gemini 3 are built for.

**First-person authority:** Ian is job-searching and knows the Berlin salary landscape; this is natural authority.

**Scores:** Creativity 4/5 - Complexity 4/5 - Partner fit 5/5 - First-person authority 5/5 - Company story 5/5
**Average: 4.6/5**

---

### Idea 11 - CareCall: Weekly check-in calls for isolated elderly patients with chronic illness

> Elderly patients with diabetes, heart failure, or COPD decompensate between GP visits because nobody is watching. CareCall auto-dials the patient weekly (voice-first, no app), asks a structured 5-minute protocol matched to their condition ("how's your breathing today on a scale of 1-10; did you take your evening meds; have you weighed yourself"), flags any red flags for their GP or community nurse, and - critically - just talks with them for a minute because loneliness itself is a health risk.

**Theme:** Disease / treatment access / loneliness

**Partner tech (all load-bearing):**
- **telli** - the outbound call infrastructure (this is literally telli's core product)
- **Gradium** - warm, elderly-appropriate voice
- **ai|coustics** - cleans up patient audio (hearing aids, background TV)
- **Gemini 3** - protocol adherence + red-flag detection + empathetic conversation
- **Entire** - nurse in the loop for anything flagged yellow or red
- **Qontext** - longitudinal patient state across weeks

**The wow moment:** Live call during the pitch to a fake elderly "patient" (ideally a teammate's grandparent pre-recorded). The agent conducts the check-in warmly and professionally. At the end, the dashboard flags one red signal and auto-creates a nurse task.

**Technical complexity:** High. The bar for a system that talks to vulnerable elderly people is rightly high. Show you thought about safety.

**Feasibility in 15h:** Very feasible. telli is literally built for this exact use case.

**Risks:** Medical-device regulatory framing. Pitch as "augmentation of existing care, not replacement."

**Scores:** Creativity 4/5 - Complexity 5/5 - Partner fit 5/5 - First-person authority 4/5 (everyone has an elderly relative) - Company story 5/5
**Average: 4.6/5**

---

### Idea 12 - TapCheck: Is your tap water actually safe right now?

> User scans their building address or postcode. Agent pulls live water-quality reports from the local utility, cross-references recent incidents (boil-water notices, lead advisories, contamination warnings), checks whether the building's piping era suggests lead risk (German buildings pre-1973 are the risk class), and returns a plain-language answer: "safe to drink today, boil-water notice in effect 2 km north is not affecting your address, your building is 1962 so get a Trinkwasseranalyse in the next 6 months." Historical data surfaces inequality: who lives in the buildings where the answer is "not safe"?

**Theme:** Water accessibility / environmental justice

**Partner tech (all load-bearing):**
- **Tavily** - live utility reports, building age data, news of incidents
- **Gemini 3** - synthesizes across sources, plain-language output in any language
- **Gradium** - voice-first for people who won't read a dashboard
- **Qontext** - per-address monitoring over time
- **Lovable** - mapping UI

**The wow moment:** Live demo: pin a Neukoelln address on a map. 20 seconds later: status + historic timeline + a comparison showing "in this district, 34% of buildings have outdated piping vs 8% in Dahlem." The inequality surface is the wow.

**Technical complexity:** Medium-high. Data aggregation is the work; the inequality visualization is the differentiator.

**Feasibility in 15h:** Feasible. Berlin-only scope. Pre-cache utility data.

**Risks:** Alarmism is easy. Framing must be "empower, not panic."

**Scores:** Creativity 5/5 - Complexity 4/5 - Partner fit 4/5 - First-person authority 2/5 - Company story 4/5
**Average: 3.8/5**

---

### Summary ranking

| # | Idea | Theme / Track | Score | Why it ranks here |
|---|---|---|---|---|
| 5 | **JobMatch Reverse** - candidate-first job platform | Joblessness / Ian's authority | **5.0** | Maximum first-person authority for Ian; natural WorkScanAI inverse; huge TAM. |
| 7 | **RentShield** - Mietspiegel enforcement | Income inequality / Buena track | **5.0** | Track prize shot + every Berliner has felt this + legal-grade output is unforgettable demo. |
| 1 | **HireSignal** - JD -> adaptive skills interview | Ian's authority | **4.8** | Strongest personal story + voice+adaptive is a genuine technical flex. |
| 4 | **TriageLine** - WhatsApp symptom triage | Treatment access | **4.8** | Safety-critical health tech; multilingual is killer in Berlin context. |
| 3 | **MedBridge** - medicine + pharmacy routing | Medicine access | 4.6 | Real problem with billions in scope; dramatic live-call demo. |
| 6 | **BenefitFinder** - unclaimed welfare | Income inequality | 4.6 | German welfare system is notoriously complex; "we found you EUR 2,860" pitch line is unbeatable. |
| 10 | **WageWatch** - negotiation coach | Income inequality / Ian's authority | 4.6 | Voice role-play demo is a proven jury-pleaser; Ian has authority. |
| 11 | **CareCall** - elderly chronic-illness check-ins | Disease / loneliness | 4.6 | telli's core use case; emotional pitch lands hard. |
| 8 | **FoodReach** - restaurant surplus routing | Food access | 4.4 | Two-sided but asymmetric; the live dispatch demo is visible impact. |
| 2 | **StandUpAgent** - async voice standup | Universal dev pain | 4.2 | Universal relatability; weaker jury differentiation. |
| 9 | **WaterWise** - drought early warning | Water / food security | 4.0 | Strong problem, harder to pitch as "Berlin-relevant." |
| 12 | **TapCheck** - tap-water safety scanner | Water access | 3.8 | Interesting inequality angle but demo less dramatic than peers. |

### The meta-observation

**Two ideas now tie at 5.0/5: JobMatch Reverse and RentShield.** Both have maximal first-person authority (for Ian personally on JobMatch, for any Berlin resident on RentShield), both have dramatic before/after demos, both tie directly into welfare-impact framing the jury explicitly rewarded in January. RentShield additionally pulls a track prize (Buena).

**The top tier (5.0 / 5.0 / 4.8 / 4.8)** is now all humanitarian-leaning. If creativity + complexity + partner fit are tied, the tiebreaker is the 2-minute video's opening line - the first-person story. Pick the idea whose opening line the team can tell truthfully.

**Strong humanitarian narrative alignment:** Google DeepMind (a primary sponsor) has publicly backed "AI for good" initiatives like the Norrsken Fixathon. Humanitarian framing is unlikely to be penalized by this jury; it is plausibly rewarded.

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
