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

This is scoped as a course/portfolio-level build — rigor suited to a strong student project or capstone, not an investor-grade or enterprise-compliance submission.

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

What differentiates this tool:

- **A genuine pedagogical framing, core to the product, not flavor text.** The tool doesn't just produce output — it shows the student *how* the AI-driven filtering it's imitating actually evaluates their material: surfacing *why* a keyword matched or didn't, not just a score. This is a meaningfully different product from "paste CV + JD → get letter," and is designed for explicitly rather than treated as an afterthought.
- A trust-first data story (encrypted storage, clear retention/deletion, GDPR-aligned handling) as an explicit selling point to a student audience that is handing over CVs and application history — rather than the implicit, unstated posture most competitors take.
- **Norwegian-market and institution-specific fit**: language, local job-market conventions, and a product built around Norwegian students' actual job search context, not a generic international one.

## Who This Serves

**Primary user: Norwegian students** actively job/internship hunting, applying to multiple postings and currently reusing generic materials because per-posting tailoring is too slow to do by hand. The product is built around Norwegian-language handling, NAV/local job-market conventions, and GDPR handling framed for a Norwegian audience.

General-purpose across disciplines — no specific field of study or institution is targeted.

Success for this user: they submit an application that is honestly stronger — more specifically matched to the posting, with real gaps identified rather than papered over — and they come away understanding *why* it's stronger, not just handing the task to a black box.

## Success Criteria

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
- **Language/style level**: how much control the student gets over tone/formality, and in what language(s) the tool operates.

**Out of scope for v1**: direct submission/auto-apply to job boards, employer/recruiter-facing features, multi-language CV translation, native mobile app (web-first, given login + storage requirements).

## Data & Privacy

Called out here as its own section because the user flagged it directly, and the research grounding this brief confirms it's load-bearing, not a checkbox:

- CVs and application history are personal data. Encrypted storage and authenticated access (both stated as requirements) are the minimum baseline, not the ceiling.
- Users are in Norway/EU, so GDPR applies concretely: a lawful basis (likely explicit consent), data minimization and a retention/deletion policy (not indefinite storage by default), and — if an external LLM API is used to process CVs — disclosure of that sub-processor to users.
- **Still open**: is data retained to give the "previous applications" context feature real value (which argues for longer retention), or minimized aggressively (which argues against it)? This is a direct tension between a stated input ("tidligere søknader" / previous applications) and good data-minimization practice, and deserves a deliberate answer rather than a default.

## Vision — Six Months Out

In six months, this is a tool Norwegian students actually return to across a full job search — not a one-off generator they try once, but something used application after application because it holds real context: what's been tried, what phrasing has landed interviews, where the recurring gaps are. The pedagogical angle is a visible, distinguishing part of the experience, not a footnote — using the tool teaches a student something concrete about how AI-driven recruitment actually filters their material, each time they use it. Trust in how their data is handled (encryption, clear retention, no surprise use of their CV) is part of why they keep coming back, not just the writing quality.

---

## Open Items for the User

Most assumptions from the first draft have been resolved into decisions above. Two things remain genuinely open:

1. **Retention vs. minimization tension** on "previous applications" data (see Data & Privacy) — deliberate call still needed.
2. Any deadline, assignment context, or specific competitor tools you're consciously reacting to — not yet stated.
