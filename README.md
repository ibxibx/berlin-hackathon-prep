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

## Competition tracks we're targeting

The Big Berlin Hack has a two-stage format. Nine finalist teams advance - one per track. **Pick the right track and you are competing against ~30 other teams for a finalist slot; pick wrong and you waste the 15 hours.**

These are the three track prizes we are targeting, plus Wildcard as our escape hatch:

### Track 1: Buena - The Context Engine (prize: EUR 2,500)

> *"Build a self-updating Context Markdown File per property - a living document every AI agent can use, sourced from ERPs, email, Slack, PDFs, and more."*

What the brief is really asking: solve the cold-start problem for any AI that serves the property-management industry. Every new property starts with zero context; Buena wants a system that ingests all the scattered signals and produces a structured, human-readable Markdown brief any downstream agent can read.

Why we can win this: property is a messy, document-heavy, email-heavy vertical where AI agents genuinely struggle. A team that ships a working demo with real ingestion from 3+ messy sources wins on technical depth alone.

### Track 2: Qontext - Context Layer for AI (prize: 1g real gold bar per team member + private dinner)

> *"Most AI systems still reconstruct company reality at runtime: they pull scattered facts from mail, CRM, policies, tickets, docs, and chat, then hope the prompt is good enough. That does not scale. Build the context layer that fixes it."*

What the brief is really asking: the horizontal version of Buena's vertical ask. Not property-specific - any company, any data surface. The bar is higher because the problem is bigger.

Why we can win this: this is the richest prize (real gold, literal gold, plus a dinner that is effectively a partnership conversation). The overlap with Buena is significant, which means one well-architected project could plausibly address both briefs with different demos.

### Track 3: Peec AI - Marketer-in-a-Box (prize: EUR 2,500)

> *"Use Peec AI's competitive visibility data to help early-stage startups find and own organic search & AI answer opportunities - from zero."*

What the brief is really asking: help founders with no existing SEO/AEO presence figure out which ChatGPT / Perplexity / Gemini prompts to win, what content to create to win them, and how to sequence the work when they have no marketing team.

Why we can win this: the brief is very specific to early-stage startups starting from zero, which is most of the people in the room. Existing tools (Peec AI itself, Otterly, AIclicks, Scrunch) are built for established marketing teams. The "from zero" wedge is genuinely open.

### Track 4: Wildcard (prize: direct qualification to the Finalist Stage)

> *"Build whatever you want. Seriously."*

Why we keep it in scope: for ideas where the Berlin-relevant, life-improving framing is too strong to give up (HireSignal, StandUpAgent, JobMatch Reverse). Wildcard has one finalist slot and is probably the most competitive field, but the qualification is automatic - we do not need to beat 8 other teams per track, we need to beat all other wildcards for that one slot.

### The strategic choice

**Priority 1:** An idea that plausibly fits both Buena AND Qontext (so we can pitch it into whichever track has less competition when we see the field on Sunday morning).

**Priority 2:** A Peec AI-specific idea that is genuinely new versus what Peec itself already sells.

**Priority 3:** A Wildcard idea backed by Ian's first-person authority (JobMatch Reverse especially).

---

## Shortlisted ideas (analyzed in detail)

The jury scores on **creativity, technical complexity, and effective use of partner tech**. Since only one team per track wins, every idea below declares explicitly which track it is pitching into. Tags: **[Wildcard]** | **[Buena]** | **[Qontext]** | **[Buena+Qontext]** | **[Peec AI]**.

Each idea is scored 1-5 on: creativity, technical complexity, partner-fit, first-person authority, and track-fit. Anything below 4/5 average is cut. Legend for feasibility dots: green = feasible in 15-18h, yellow = tight but doable, red = only if a teammate has prior art in the exact stack.

### Idea 1 - HireSignal: Job description -> realistic skills interview in 5 minutes

> Recruiter or hiring manager pastes a job description. Agent generates a *specific*, *hands-on*, adaptively difficult interview (not generic STAR-question fluff) in the candidate's browser. As the candidate answers via voice, difficulty adjusts live. At the end, recruiter gets a structured signal report - not a yes/no - scoring on the actual skills the JD implied.

**Track:** Wildcard - build whatever you want; we compete against all other Wildcards for one auto-finalist slot.

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

**Track:** Wildcard - build whatever you want; we compete against all other Wildcards for one auto-finalist slot.

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

**Track:** Wildcard - build whatever you want; we compete against all other Wildcards for one auto-finalist slot.

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

### Idea 4 - CasaContext: the living brief every property AI agent starts from

> Every property in a manager's portfolio has scattered context - the tenancy history buried in email, the maintenance log in a shared drive, the noise complaint from the neighbor in Slack, the meter reading photo on someone's phone. Every new AI agent built for that property has to re-discover all of it. CasaContext is the self-updating Markdown brief for each property: one living document that ingests from email threads, Slack channels, PDF tenancy agreements, meter-reading photos, and property-management ERP exports, and keeps itself current. Any AI agent, any human team member, same starting point.

**Track:** Buena - direct answer to the brief. This is the exact Context Markdown File the track is asking for.

**Partner tech (all load-bearing):**
- **Gemini 3** - multimodal ingestion: reads PDFs, emails, Slack exports, images of meter readings and damage photos; produces structured Markdown with headings, key facts, and a change log
- **Tavily** - enriches with public context (building year of construction, district characteristics, Mietspiegel bracket)
- **Qontext** - stores the evolving context layer so every agent query gets a consistent view without re-reading raw sources each time
- **Entire** - human-in-the-loop review flow for sensitive updates (e.g. a tenant dispute flagged requires the property manager to approve before it goes into the shared context)
- **Lovable** - the portfolio dashboard where the property manager sees all Context Markdown Files side by side

**The wow moment:** On stage, drop a messy folder into the system: 40 emails about one Berlin flat, 3 PDFs (Mietvertrag, Betriebskostenabrechnung, Hausordnung), a Slack export with a month of maintenance chatter, and 8 photos. Ninety seconds later: a beautifully structured, human-readable Markdown brief for that property that reads like a junior property manager spent 3 hours writing it. Then change one Slack message, rerun: the brief updates just the affected section and shows the diff.

**Technical complexity:** Very high. Multimodal ingestion + deduplication + structured-output generation + incremental updates (not full regenerations) + audit trail. This is the hardest problem the track posed.

**Feasibility in 15-18h:** Yellow. Pre-curate a realistic demo dataset on Saturday evening; the ingestion pipeline is the risk. Scope to 3 Berlin flats.

**Why we can win this track:** The brief specifically calls for "sourced from ERPs, email, Slack, PDFs, and more." Teams that ship 2 of those 5 sources lose to a team that ships all 5 with visible quality. Breadth of ingestion is the differentiator.

**Scores:** Creativity 4/5, Complexity 5/5, Partner fit 5/5, First-person authority 3/5, Track fit 5/5
**Average: 4.4/5**

---

### Idea 5 - TurnoverBrief: the 10-minute tenant handover that used to take 3 days

> When a tenant moves out and a new one moves in, the property manager has to rebuild the entire knowledge package: what's broken, what was fixed, which neighbor complains about noise, which boiler quirk nobody wrote down, which key opens which back gate. Currently it takes days of email archaeology. TurnoverBrief auto-generates a complete structured handover document between tenancies: outgoing tenant's known issues extracted from their communications, unresolved maintenance items, neighbor dynamics, "things to tell the new tenant on day one," and a week-1 follow-up checklist for the property manager.

**Track:** Buena - same Context Markdown File thesis, but focused on the turnover moment where the context problem is most acute.

**Partner tech (all load-bearing):**
- **Gemini 3** - long-context summarization of an entire tenancy's worth of email + maintenance records into a 2-page brief with no lost facts
- **Tavily** - fetches current market rent comparisons so the handover brief includes a price recommendation for the next tenancy
- **Qontext** - the structured context that feeds into the document, so updates to one field propagate
- **telli** - places the optional outgoing-tenant exit interview as a 5-minute voice call, transcribes the gold nuggets straight into the brief
- **Lovable** - the property-manager-facing app

**The wow moment:** On stage, feed in a full tenancy's email thread (messy, 2 years worth) plus a 90-second voice clip of the outgoing tenant saying "oh and the boiler makes a weird noise on cold mornings, but if you press reset twice it's fine." The brief assembles in real time: a cleanly-sectioned Markdown document that explicitly captures the boiler quirk as a "unwritten knowledge" section the new tenant will thank the landlord for.

**Technical complexity:** High. Long-context reasoning + voice interview integration + structured extraction with zero hallucination on factual claims is the core engineering.

**Feasibility in 15-18h:** Green. Narrower scope than CasaContext; the telli voice-exit-interview is a dramatic demo centerpiece.

**Why we can win this track:** Turnover is a crisp, well-defined moment where the pain is maximum. A demo that compresses "3 days of email archaeology" into "10 minutes of AI-generated clarity" with a voice-call integration is memorable where generic context engines are forgettable.

**Scores:** Creativity 5/5, Complexity 4/5, Partner fit 5/5, First-person authority 3/5, Track fit 5/5
**Average: 4.4/5**

---

### Idea 6 - BriefCraft: one context engine, two submissions (Buena AND Qontext)

> BriefCraft is deliberately designed to submit to both tracks. The core engine is domain-agnostic: point it at any company's scattered sources (mail, Slack, Drive, CRM, PDFs, ticketing system) and it produces a living Markdown "operating manual" any AI agent can read as its starting context. For the Buena submission, we demo it on property management. For the Qontext submission, we demo it on a B2B SaaS company's sales operation. Same engine, two tailored demos.

**Track:** Buena + Qontext (dual submission) - the richest strategic bet. Qontext prize is 1g gold per member + private dinner; Buena is EUR 2,500. Both achievable with one codebase.

**Partner tech (all load-bearing):**
- **Qontext** - the context layer itself, obviously load-bearing for the Qontext track
- **Gemini 3** - multimodal ingestion across all source types, structured summarization, incremental update detection
- **Tavily** - enrichment from public web for any mentioned entity (company, person, regulation, market)
- **Entire** - human review of the auto-generated context with edit-and-approve flow
- **Pioneer by Fastino Labs** - the system learns which summary sections that specific company cares most about, so outputs adapt per-customer

**The wow moment:** Run ONE ingest job on stage over a mixed-domain dataset. Pop up two dashboards side by side: left shows a Buena-flavored property brief, right shows a Qontext-flavored sales-account brief, generated from fundamentally different source data. Judges from both sponsor booths see their brief render live.

**Technical complexity:** Very high. The hard part is genuinely generalizing across domains - you cannot hardcode property-specific schemas. Pioneer's self-training angle is the elegant answer: the system learns each company's preferred context shape from a few examples.

**Feasibility in 15-18h:** Yellow. More ambitious than CasaContext alone but the marginal cost of the second demo is small if the engine is genuinely domain-agnostic. The strategic upside is enormous: two prize shots from one build.

**Why we can win BOTH tracks:** Buena's brief is a specific instance of Qontext's brief. A team that builds the general solution can tailor a property demo for Buena and a B2B-sales demo for Qontext on the same engine. Most teams will build vertical-specific solutions that cannot cross over. We compete in both pools.

**Risk:** The dual-submission ambition could become a scope trap. Mitigation: lock the core engine by Sunday 02:00; the "second demo" is 90 minutes of Lovable work on Sunday morning.

**Scores:** Creativity 5/5, Complexity 5/5, Partner fit 5/5, First-person authority 3/5, Track fit 5/5 (double)
**Average: 4.6/5**

---

### Idea 7 - IncidentFile: the property-incident context bundle that writes itself in 60 seconds

> Water damage happens in a Berlin flat. Right now, the property manager has to: photograph the damage, write up what happened, find the tenancy file, figure out which insurance policy covers it, identify the tradespeople who can fix it, and start 4 parallel conversations. IncidentFile is triggered by one voice note from the tenant ("the kitchen ceiling is leaking, I think from the neighbor above") and auto-generates a complete incident package: the incident description, the relevant tenancy and policy excerpts, photo uploads organized, insurance claim draft pre-filled, 3 recommended tradespeople matched to the damage type, and a proposed communication plan.

**Track:** Buena (primary) + Qontext (secondary if we pitch the context-bundle angle)

**Partner tech (all load-bearing):**
- **Gemini 3** - multimodal: voice note + damage photos into a structured incident record; reads the relevant policy PDF and extracts coverage clauses
- **Qontext** - the property context (who the tenant is, which policy covers this building, maintenance history) feeds the incident package so nothing starts from zero
- **Tavily** - live lookup of tradespeople in the right Berlin Bezirk with the right specialty, current availability, recent review signals
- **telli** - dispatches the outbound call to the top-ranked tradesperson to get a site-visit slot
- **Entire** - the property manager approves the auto-generated insurance claim before it is sent

**The wow moment:** A teammate voice-notes a fake incident: "hi it's flat 3B, there's water coming through the kitchen ceiling, I think the upstairs neighbor has a leak." Sixty seconds later on the manager dashboard: complete incident file with the right policy page highlighted, claim draft pre-filled with amount estimate, two tradespeople ringing in parallel on telli to see who can come first, and a drafted message to the upstairs neighbor. All from one voice note.

**Technical complexity:** High. Multimodal input + policy document RAG + real-time dispatch + document drafting + multi-party orchestration.

**Feasibility in 15-18h:** Yellow. Tight but doable; the insurance-policy RAG is the piece to prototype first.

**Why we can win this track:** Incidents are Buena's high-value moment - when the property manager desperately needs structured context RIGHT NOW. A demo that compresses 4 hours of first-response work into 60 seconds of AI-orchestrated output is exactly the "living document every AI agent can use" thesis made dramatic.

**Scores:** Creativity 5/5, Complexity 5/5, Partner fit 5/5, First-person authority 3/5, Track fit 5/5
**Average: 4.6/5**

---

### Idea 8 - DealMemory: the B2B sales context layer that survives rep turnover

> When a B2B sales rep leaves, their pipeline knowledge goes with them. The new rep inherits 40 accounts, each with scattered history across email, calls, CRM notes, product documents, and Slack channels. Weeks of context-building. DealMemory auto-generates and maintains a living Markdown brief per account - the champion at the customer, the specific objections they have raised, the product features they mentioned caring about, the stakeholder map with relationship quality, the competitive context - so a new rep is effective on day 3, not week 12.

**Track:** Qontext - pure expression of the "scattered facts to structured context" brief, in a B2B sales vertical that every startup understands.

**Partner tech (all load-bearing):**
- **Qontext** - the context layer, literal track partner
- **Gemini 3** - long-context synthesis across 2 years of email threads, 30 call recordings, 200 Slack messages, CRM notes, proposal documents
- **Tavily** - enriches accounts with current public signals (recent funding, org changes, new product launches, news)
- **ai|coustics** - cleans recorded sales-call audio (often poor quality) so transcription is reliable
- **Entire** - the rep reviews and corrects the auto-generated account brief; corrections feed back into the system's understanding of what "good" looks like

**The wow moment:** On stage, ingest one synthetic B2B account: 50 emails + 4 call recordings + CRM export + 80 Slack messages. Forty-five seconds later: a structured account brief where every claim links back to a specific source. Change the account to a different industry; the brief adapts (the "competitive context" section looks different for healthcare SaaS than for devtools).

**Technical complexity:** Very high. The grounding problem (every fact in the brief must be traceable to a source) is the hard engineering. Sales context is richer and messier than property context.

**Feasibility in 15-18h:** Yellow. The demo data assembly is non-trivial; we pre-seed a realistic synthetic account on Saturday evening.

**Why we can win this track:** B2B sales is a problem 90 percent of the jury understands intimately (every sponsor has salespeople; several are growth-stage companies who have lost reps). The emotional pitch writes itself: "we all know what it feels like when a rep leaves with your best account in their head."

**Scores:** Creativity 4/5, Complexity 5/5, Partner fit 5/5, First-person authority 4/5, Track fit 5/5
**Average: 4.6/5**

---

### Idea 9 - SupportCore: the customer-support context layer that actually remembers

> Customer-support AI agents hallucinate because they reconstruct company reality at runtime from scattered docs, tickets, and policies. Every query is a cold start. SupportCore is the context layer feeding every support agent, human or AI: product documentation parsed into canonical facts, historical ticket resolutions distilled into a playbook, policy edge cases documented as "what to say when X," and per-customer history layered on top. When a ticket comes in, the AI agent gets a pre-assembled context bundle specific to that customer and that issue, rather than attempting to pull everything from scratch.

**Track:** Qontext - the canonical expression of the track brief. "AI systems reconstruct company reality at runtime. That does not scale. Build the context layer that fixes it." This idea is almost the brief verbatim.

**Partner tech (all load-bearing):**
- **Qontext** - the layer itself
- **Gemini 3** - ingests documentation, ticket history, policy documents into a structured fact base; reasons about which facts are relevant for a given incoming ticket
- **Tavily** - live product status, current outages, recent changelog, used when relevant to a live ticket
- **Pioneer by Fastino Labs** - the system learns per-customer nuances (this enterprise customer always needs the SLA explanation; this SMB never does)
- **Aikido** - security framing is real here because support context contains PII; demoing access controls correctly adds credibility

**The wow moment:** On stage, show two AI support agents side by side answering the same incoming ticket. Left agent: vanilla RAG over docs, hallucinates a non-existent feature. Right agent: SupportCore-backed, answers correctly with a link to the exact policy clause AND the context that this specific customer is on the enterprise plan. The jury sees the hallucination happen in real time.

**Technical complexity:** Very high. Per-customer context stratification + grounded generation + security boundaries is a serious engineering stack.

**Feasibility in 15-18h:** Yellow. The "two agents side by side" demo framing is the crucial piece; lock that storyboard Saturday evening.

**Why we can win this track:** The demo explicitly shows the failure mode Qontext describes in their brief ("reconstruct reality at runtime, hope the prompt is good enough"). A team that LITERALLY SHOWS the problem happening and THEIR solution preventing it is the most on-brief possible submission.

**Scores:** Creativity 4/5, Complexity 5/5, Partner fit 5/5, First-person authority 3/5, Track fit 5/5
**Average: 4.4/5**

---

### Idea 10 - AnsweredFromZero: the founder-solo AI-search growth agent

> A pre-revenue founder has a website, a product, and no idea which 50 ChatGPT/Perplexity prompts would send them their first 100 customers if they could win them. Existing AI-visibility tools (including Peec itself) are built for marketing teams with established content engines; they tell you your rank against competitors and what content to create. A founder alone does not have a content engine. AnsweredFromZero is a week-one agent: founder types in their product and ideal customer. Agent generates the 50 most commercially-valuable prompts to target, drafts the first piece of content for each (ranked by lowest-competition-first), queues the publishing schedule, and uses Peec's visibility data to check every 48 hours which ones are landing.

**Track:** Peec AI - direct hit on "help early-stage startups find and own organic search and AI answer opportunities FROM ZERO." The "from zero" framing in the brief is the strategic wedge.

**Partner tech (all load-bearing):**
- **Peec AI** - the visibility data itself: which prompts mention this startup, which mention competitors, which are completely open territory
- **Gemini 3** - generates the founder's ICP and product context into a prompt tree; drafts content tuned to be citable by ChatGPT/Perplexity
- **Tavily** - checks existing web results for each targeted prompt so the content is genuinely differentiated, not duplicate
- **Lovable** - the founder-facing dashboard
- **Entire** - founder approves each drafted piece before publishing

**The wow moment:** A teammate plays a real pre-revenue founder. Enters product (say, "an AI tool for translating legal contracts into plain language for small business owners"). Ninety seconds later: 50 ranked prompts, first 5 content pieces drafted, a publish queue for the next 2 weeks, and the projected visibility curve based on Peec's data showing which prompts a founder can realistically win in 30 days versus which take 6+ months.

**Technical complexity:** High. The prompt-opportunity discovery + content-draft-that-is-actually-citable + sequencing-for-a-solo-founder is real product thinking, not generic SEO.

**Feasibility in 15-18h:** Green. Peec's data is accessible as the track partner; most of the work is prompt engineering + a sharp dashboard.

**Why we can win this track:** The brief says "from zero" and most teams will default to "improve visibility for an established brand" because that is what every existing tool does. Solving the cold-start specifically, with a concrete 50-prompt output and sequenced drafts, is the distinctive answer.

**Scores:** Creativity 5/5, Complexity 4/5, Partner fit 5/5, First-person authority 4/5, Track fit 5/5
**Average: 4.6/5**

---

### Idea 11 - CitationForge: get cited by ChatGPT without writing your own content

> A startup that cannot invest in content can still get cited by AI engines - IF they appear on the third-party sources that ChatGPT and Perplexity already trust. CitationForge identifies, for a given startup's category, exactly which third-party sources (Reddit threads, G2/Capterra listings, niche Substacks, industry wikis, YouTube channels) are cited most often when the models answer the target prompts - and generates the specific, credible outreach a founder can send to each source to be included. Not "please link to me," but "here is a precise paragraph I can contribute that fills a gap in your existing article on X."

**Track:** Peec AI - uses Peec's source-citation data as the core input. This is what Peec already measures but nobody has turned into an actionable outreach engine.

**Partner tech (all load-bearing):**
- **Peec AI** - the citation-source data: which third-party URLs feed the models for a given category
- **Tavily** - fetches the full content of each cited third-party source so we can find contribution-worthy gaps
- **Gemini 3** - reads each source, identifies specific gaps the startup could plausibly fill, drafts a credible contribution paragraph + outreach email
- **Entire** - founder approves every outreach email (critical: bad outreach burns goodwill)
- **Lovable** - the dashboard with a prioritized list of "if you win these 10 citations, your visibility in ChatGPT on these 8 prompts will roughly double"

**The wow moment:** On stage, a founder's domain goes in. Forty-five seconds later: a ranked list of 10 specific Reddit threads / G2 comparison pages / niche blogs where this startup could credibly contribute - with the exact paragraph drafted for each, and a personalized outreach email to the page owner. The judge from Peec AI sees their own data being used in a way that is clearly novel.

**Technical complexity:** High. The gap-identification + contribution-drafting that is credible (not spammy) is the genuine product craft.

**Feasibility in 15-18h:** Green. Most of it is prompt engineering + a good list UI.

**Why we can win this track:** Peec's existing product tells you your visibility. The next step - what do I actually do about it - is explicitly where they are directing teams ("help startups OWN opportunities"). Turning their data into outreach is the natural extension they have not built themselves.

**Scores:** Creativity 5/5, Complexity 4/5, Partner fit 5/5, First-person authority 4/5, Track fit 5/5
**Average: 4.6/5**

---

### Idea 12 - PromptTerritory: the month-by-month prompt-claiming roadmap

> Knowing the 50 prompts you want to win does not tell a founder in which order to fight for them. Some prompts are crowded with established competitors; some are wide open but have thin search volume; some are rising fast and will be contested in 3 months. PromptTerritory is a strategic sequencer: it uses Peec's competitive visibility data plus query-volume signals to produce a month-by-month roadmap of which prompt territory to claim first, second, third. Each month's batch is a "push" with drafted content, outreach plan, and measurable visibility targets. Miss a month, the plan reshuffles.

**Track:** Peec AI - strategic planning layer built on Peec's competitive data.

**Partner tech (all load-bearing):**
- **Peec AI** - competitive visibility rankings per prompt; trend direction over time
- **Tavily** - query-volume proxy signals from public web searches; adjacent topic discovery
- **Gemini 3** - strategic reasoning: sequencing, dependency detection between prompts, opportunity scoring
- **Qontext** - the startup's claimed-territory state across months so the plan adapts to what has actually been won
- **Lovable** - the roadmap visualization

**The wow moment:** On stage, two founders with similar products start with the same 50-prompt list. One follows the default alphabetical order. The other follows PromptTerritory's sequencing. Six-month simulation: the PromptTerritory founder has roughly 3x the visibility by month 6 because they claimed the easy-uncontested prompts first, built citation authority, then attacked the competitive ones from strength.

**Technical complexity:** Medium-high. The sequencing algorithm is the intellectual core; the data integration is moderate.

**Feasibility in 15-18h:** Green. Heavy on prompt engineering and simulation visualization; light on novel engineering.

**Why we can win this track:** Strategic sequencing of limited marketing resources is exactly what a resource-constrained early-stage startup needs and exactly what Peec's existing dashboards do not deliver. The "claim this territory first, that one in month 3" framing is visually memorable in a way generic visibility dashboards are not.

**Scores:** Creativity 4/5, Complexity 4/5, Partner fit 5/5, First-person authority 4/5, Track fit 5/5
**Average: 4.4/5**

---

### Summary ranking

| # | Idea | Track | Score | Why it ranks here |
|---|---|---|---|---|
| 6 | **BriefCraft** - domain-agnostic context engine | Buena + Qontext (dual) | **4.6** | Two prize shots from one build; Qontext is the richest prize; most strategic EV. |
| 7 | **IncidentFile** - property incident in 60 seconds | Buena | **4.6** | Most dramatic single demo moment; hits Buena's highest-value operational moment. |
| 8 | **DealMemory** - B2B sales context layer | Qontext | **4.6** | Every sponsor feels the "rep quit, knowledge left with them" pain; emotional pitch lands. |
| 10 | **AnsweredFromZero** - founder solo growth agent | Peec AI | **4.6** | Direct hit on "from zero" framing; most teams will default to established-brand angle. |
| 11 | **CitationForge** - third-party citation outreach | Peec AI | **4.6** | Turns Peec's data into action Peec itself has not built; judges will see their own data used novel-ly. |
| 4 | **CasaContext** - living property Markdown brief | Buena | 4.4 | Breadth of ingestion (5+ source types) is the differentiator; the purest read of the brief. |
| 5 | **TurnoverBrief** - tenant handover auto-brief | Buena | 4.4 | Crisp demo with a voice-interview punchline; narrower scope than CasaContext. |
| 9 | **SupportCore** - customer support context layer | Qontext | 4.4 | "Two agents side by side, one hallucinates" is a memorable demo; on-brief verbatim. |
| 12 | **PromptTerritory** - prompt-claiming roadmap | Peec AI | 4.4 | Sequencing is strategic, but demo is more chart than narrative. |
| 1 | **HireSignal** - JD to adaptive skills interview | Wildcard | 4.8 | Ian's strongest personal story; but Wildcard is one finalist slot against all other Wildcards. |
| 3 | **JobMatch Reverse** - candidate-first platform | Wildcard | 5.0 | Max first-person authority for Ian; multimodal credential reasoning is a 2026-capability flex. |
| 2 | **StandUpAgent** - async voice standup | Wildcard | 4.2 | Kept for safety; lower jury differentiation. |

Note: Wildcard ideas have higher raw averages but lower effective probability of winning, because Wildcard has one finalist slot against all other Wildcard submissions (probably the biggest pool). The track ideas have lower raw averages but compete against a smaller, more specific pool per track.

### The meta-observation

**The biggest strategic insight of this pass:** the tracks specified the game board. Buena and Qontext are near-duplicate briefs (vertical vs horizontal context engine). This means **BriefCraft (idea 6) is almost strictly dominant** as long as we can execute the dual submission without scope collapse. One codebase, two prize pools, two shots at a finalist slot.

**Peec AI track has the cleanest "from zero" wedge.** Every existing AI-visibility tool is built for established marketing teams. The brief explicitly says "early-stage startups from zero." Ideas 10 and 11 (AnsweredFromZero and CitationForge) solve for founders, not CMOs. The jury from Peec AI will recognize immediately what is being built.

**Wildcard is the hardest competition pool but retains Ian's first-person authority advantage.** JobMatch Reverse remains a strong personal-story pick. If the team has 4+ members and can plausibly run two parallel workstreams, one person can pre-prototype a Wildcard submission alongside the main track pitch - but this is a risky scope expansion.

**Tiebreaker rule:** when scores are tied, pick the idea whose 2-minute video can show the jury their own brief text being solved on screen. CasaContext, IncidentFile, BriefCraft, and SupportCore all pass this test most directly. Peec ideas pass it second-best. Wildcards are farther from any brief text.

### Strong recommendation

Lock the decision among these three options:

1. **BriefCraft (idea 6)** - highest strategic EV. Dual submission; Qontext prize is the most valuable; Buena prize is a backup. Execution risk is highest because of ambition, but the team composition can handle it if we have 3-4 people.

2. **IncidentFile (idea 7)** - single-track focus on Buena with the most dramatic demo moment. Easier to execute well; narrower upside (one prize pool).

3. **AnsweredFromZero (idea 10)** - Peec AI-only, lowest execution risk, still hits a Euro 2,500 prize with a crisp demo. Good choice if the team wants one clean win over a strategic gamble.

**Tactical playbook for Saturday morning:** in the first 90 minutes at the venue, we walk the Qontext and Buena sponsor booths. If both sponsors say "we want to see integrations with X and Y real source types" in a way that is compatible, lock BriefCraft. If the briefs drift apart in conversation, commit to IncidentFile (Buena only) and do not look back.

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
