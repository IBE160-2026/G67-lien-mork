---
title: "Product Brief: CV & Application Assistant for Students (working title)"
status: draft
created: 2026-09-18
updated: 2026-09-18
---

# Product Brief: CV & Application Assistant for Students (working title)

## Executive Summary

Students applying for jobs and internships face a mismatch: each posting wants a cover letter and CV tailored to its specific language and requirements, but most students write one generic version and reuse it everywhere. At the same time, AI is already deeply embedded on the other side of the hiring process — screening, ranking, and filtering applications — and students rarely get to see how that machinery actually reads what they submit.

This tool closes both gaps at once. A student uploads a CV and a job posting; the tool produces a tailored cover letter, surfaces concrete CV improvements, flags qualifications the posting wants that the CV doesn't show, and scores the result against ATS-style keyword matching — the same mechanics a real applicant-tracking system would apply. The student stays in control of how much the tool rewrites versus merely suggests, in what tone, and in what output format.

Because it stores CVs, job history, and prior applications, the product treats encrypted storage and authenticated access as foundational, not optional — this is personal data handled at a genuinely useful level of persistence (previous applications inform future ones), which is exactly the profile that needs to be built carefully from day one rather than retrofitted.

**[ASSUMPTION]** This brief assumes the project is scoped as a course/portfolio-level build (rigor appropriate to a strong student project or capstone, not an investor-grade or enterprise-compliance submission) — flag if the actual stakes are higher or lower.

## The Problem

Students applying for jobs today typically:

- Write one CV and one cover letter template, then lightly edit it per application — because tailoring each submission by hand is slow and the payoff per posting is uncertain.
- Have no visibility into *why* an application gets filtered out. Feedback, when it comes at all, is a generic rejection — not "your CV was missing X keyword" or "this posting screens on Y qualification you don't list."
- Don't know what an ATS (Applicant Tracking System) actually does with their submission. The AI systems doing the filtering are opaque to the people being filtered.
- Face this specifically as students: thin work history means every application has to work harder to connect what little experience they have to what the posting asks for — exactly the kind of gap-finding and phrasing work that's most tedious to do manually, per posting, at volume.

The cost of the status quo is applications that are technically submitted but poorly matched — both to the human reader and to the automated filter that often reads it first.

## The Solution

A tool that takes a student's CV and a target job posting and produces, per application:

- A tailored cover letter, matched to the posting's language and the student's stated tone/style preference.
- Concrete CV improvement suggestions specific to that posting.
- A gap analysis: qualifications the posting asks for that the CV doesn't currently show.
- An ATS-optimization pass — keyword/format alignment with how automated screening actually parses submissions.

Rather than a one-click "generate and submit" tool, the student stays the decision-maker: they choose how much the tool rewrites outright versus merely flags for them to address themselves, in what output format, and at what level of language/style formality. The tool's role is qualitatively closer to a coach with visibility into the filtering mechanics than a ghostwriter.

## What Makes This Different

The core mechanics here — CV/JD matching, ATS scoring, gap analysis, AI-drafted cover letters — are **not novel**. This is a crowded category: Teal, Rezi, Kickresume, Jobscan, Enhancv, and Resume Worded all do versions of this internationally, and Norwegian-market tools already exist doing largely the same thing in-language (Jobbki, Cvenn, SøknadGPT/cvcv.no). Any brief that pretends otherwise would be dishonest about the actual competitive position.

What could differentiate this tool, if pursued deliberately rather than assumed:

- **[ASSUMPTION]** A genuine pedagogical framing — not just producing output, but showing the student *how* the AI-driven filtering it's imitating actually evaluates their material (e.g., surfacing *why* a keyword matched or didn't, not just a score). If this is real, it's a meaningfully different product from "paste CV + JD → get letter," and worth designing for explicitly rather than treating as flavor text. **This needs the user's confirmation** — the brief currently can't tell whether this is core positioning or a description added after the fact.
- A trust-first data story (encrypted storage, clear retention/deletion, GDPR-aligned handling) as an explicit selling point to a student audience that is handing over CVs and application history — rather than the implicit, unstated posture most competitors take.
- **[ASSUMPTION]** Norwegian-market and/or institution-specific fit (language, local job-market conventions, possibly integration with a specific university's career services) — unconfirmed; if the target user is international/generic students rather than a Norwegian context specifically, this differentiator doesn't apply and needs to be replaced with something else.

Absent at least one of these being real and deliberately built for, this product risks being a smaller, later entrant into an already-commoditized feature set.

## Who This Serves

**Primary user: students actively job/internship hunting**, applying to multiple postings and currently reusing generic materials because per-posting tailoring is too slow to do by hand.

- **[ASSUMPTION]** Norwegian students specifically (inferred from the language of the product description and the local competitive references) — not confirmed. This materially affects scope (Norwegian-language handling, NAV/local job-market conventions, GDPR framed for a Norwegian audience) and should be confirmed before this goes further.
- **[ASSUMPTION]** No specific field of study or institution named — assumed general-purpose across disciplines unless narrowed.

Success for this user: they submit an application that is honestly stronger — more specifically matched to the posting, with real gaps identified rather than papered over — and they come away understanding *why* it's stronger, not just handing the task to a black box.

## Success Criteria

- **[ASSUMPTION — needs the user's input]** No target metrics, timeline, or definition of "done" were provided. Placeholder criteria below are inferred from the product description and should be replaced with real targets:
  - Users can go from CV + job posting to a usable tailored cover letter draft, CV suggestions, and a gap analysis in a single session.
  - Gap analysis and ATS-optimization output are accurate enough that students trust and act on them (vs. ignoring the tool after one try).
  - No qualification or experience is fabricated in generated output that isn't traceable to the source CV — this is a hard correctness bar, not an aspiration, given the hallucination risk documented across this product category.
  - Data handling (encryption, login, retention/deletion) meets a standard the user would be comfortable defending if asked directly "what happens to my CV after I upload it?"

## Scope

**In for a first version** (derived from the stated inputs/outputs):
- Input: CV upload (PDF/DOC/TXT), job posting (text or URL/paste), keywords, desired tone/style, access to the student's previous applications for context.
- Output: tailored cover letter, CV improvement suggestions, gap/missing-qualifications analysis, ATS-optimization feedback.
- Account system with login; encrypted storage for CVs and application history.

**Explicitly open — not yet decided (the user's own "decision points"):**
- **Degree of rewriting vs. suggestion**: does the tool draft full replacement text, or only flag/suggest and leave the writing to the student? This is a product-defining choice (ghostwriter vs. coach) and shouldn't default silently — it likely needs to be a setting, not a one-time architectural decision, given the "coach not ghostwriter" positioning discussed above.
- **Output file format**: DOC, Markdown, and/or PDF — which is default, which are supported at all.
- **Language/style level**: how much control the student gets over tone/formality, and in what language(s) the tool operates (relevant if Norwegian-market is confirmed).

**[ASSUMPTION] Out of scope for v1** (not stated, inferred as reasonable boundaries — needs confirmation): direct submission/auto-apply to job boards, employer-facing/recruiter-facing features, multi-language CV translation, mobile app (assumed web-first given login + storage requirements).

## Data & Privacy

Called out here as its own section because the user flagged it directly, and the research grounding this brief confirms it's load-bearing, not a checkbox:

- CVs and application history are personal data. Encrypted storage and authenticated access (both stated as requirements) are the minimum baseline, not the ceiling.
- **[ASSUMPTION — flag if Norwegian/EU users are not actually the target]** If users are in Norway/EU, GDPR applies concretely: a lawful basis (likely explicit consent), data minimization and a retention/deletion policy (not indefinite storage by default), and — if an external LLM API is used to process CVs — disclosure of that sub-processor to users.
- Open question the brief can't resolve on its own: is data retained to give the "previous applications" context feature real value (which argues for longer retention), or minimized aggressively (which argues against it)? This is a direct tension between a stated input ("tidligere søknader" / previous applications) and good data-minimization practice, and deserves a deliberate answer rather than a default.

## Vision

**[ASSUMPTION — speculative, needs the user's own view]** If this works, it becomes less a "generate my cover letter" tool and more a standing relationship a student has through their entire job search — one that gets better with each application because it has real context on what's been tried, what's landed interviews, and where the recurring gaps are. The pedagogical angle, if it's real, could extend into genuinely demystifying AI-driven recruitment for a population about to spend their whole career on the other side of these systems.

---

## Open Items for the User

This brief was drafted fast-path style — several sections carry **[ASSUMPTION]** tags where the conversation didn't yet reach an answer. Before this brief is finalized, these need real answers:

1. **Stakes** — course project, portfolio piece, pitch, or real-user aspiration? Changes how much rigor/detail this brief (and later the PRD) should carry.
2. **Target audience specificity** — Norwegian students, confirmed? Any institution or field focus?
3. **Is the pedagogical framing** ("realistic experience of how AI is used in recruitment") core positioning, or flavor text on a practical tool? This changes the differentiation story materially.
4. **Retention vs. minimization tension** on "previous applications" data — deliberate call needed.
5. Any deadline, assignment context, or specific competitor tools you're consciously reacting to.
