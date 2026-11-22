---
name: deepak-breakdown-script
description: Research and write a Tech Boy Deepak case-study / business-breakdown / current-event explainer YouTube script in his exact style, in English and Telugu (Telangana Tenglish). Use whenever the user gives a topic, company, person, industry or news event for a "breakdown", "case study", "explainer" or "detailed explanation" video on this branch.
---

# Deepak Breakdown Script

Turns a topic into (1) a sourced research document and (2) a matching pair of scripts, English and Telugu. Both are written the way Tech Boy Deepak researches, structures and talks in his breakdown videos.

**Read first:** [`research/style-dna-report.md`](../../../research/style-dna-report.md), the full forensic DNA. The reference transcripts are in [`transcripts/`](../../../transcripts). Skim at least one Telugu section before writing Telugu.

## Outputs (one folder per video)

```
scripts/<NN>-<slug>/
  research.md          sourced research brief (every number: source + as-of date)
  script-english.md    English script, Indian-English spoken register
  script-telugu.md     Telugu script, same beats, same order, same numbers
  production-notes.md  title options, thumbnail idea, B-roll/on-screen text per beat, description
```

The English and Telugu scripts must have **identical beats, timestamps, numbers, examples and CTAs**. Only the language changes.

## Workflow

### 1. Scope
- Decide the format (DNA §10): case study, current-event explainer, or listicle.
- Set the runtime the user asked for. The default for a case study is 18 to 20 minutes.
- Write the one-line **paradox / central question** the whole video answers (DNA §1.1).

### 2. Research (always fresh: use web search; never rely on memory for numbers)
Gather these, following DNA §3 and the §12 research checklist:
- **Cold-open stats:** 3 to 6, very recent, with exact dates.
- **Origin story:** an exact date the presenter "still remembers".
- **Escalation chain:** dated milestones with before → after numbers, per-unit ratios, speed comparisons, superlatives.
- **Three examples per major claim.**
- **India angle:** Indian users, ₹ crore and lakh, Indian cities, companies or government programmes.
- **Historical precedent.**
- **Myth to correct.**
- **Watch-list:** 2 or 3 upcoming dates or signals.
- **Viewer takeaway.**

Parallelise research across sub-agents by sub-topic when the topic is big. Every fact needs a source URL and an as-of date. Mark anything unverified, and leave it out of the script or frame it as "reports say".

**Maths check:** recompute every derived number (ratios, % changes, ×-growth, currency conversions). DNA §11 lists his past slips. Don't repeat them.

### 3. Research document (`research.md`)
Use this structure:
1. Central question and thesis (2 lines)
2. Hook bank (best shock stats, each with a source)
3. Timeline table (date | event | number | source)
4. One section per sub-topic: facts, numbers, quotes
5. The twist(s)
6. Analogy options: Hyderabadi or Indian daily life, each with a mapping table
7. India angle
8. Myths vs reality
9. Precedent
10. Watch-list (upcoming dates)
11. Viewer takeaways
12. Uncertain / disputed (kept out of the script or hedged)
13. Sources

### 4. Beat sheet
Map the research onto the Breakdown Arc (DNA §2.1, beats B1 to B18) with a time budget (DNA §2.2). Choose:
- the single big analogy (60 to 90 s) and the short callback analogy;
- the twist line and the "X entered the story" turn;
- CTA placement: early (about 0:45) **or** mid-roll (about 48%), not both;
- the end poll (a binary question tied to the title);
- the targeted-share line and the plant/payoff pairs (every "remember this" must pay off later).

### 5. Write `script-english.md`, then `script-telugu.md`
Format for each script:
- A header table: title, format, runtime target, word count, the central question.
- Blocks with `## [mm:ss–mm:ss] Beat name`, then the spoken lines. Put `> **On screen:**` notes for numbers and visuals under the lines they go with.
- Spoken lines only: no headings read aloud, no bullet lists in speech.

**Voice rules (DNA §6):**
- **Both languages:**
  - No greeting at the start. Open on the question or shock.
  - Use more than 2 direct questions a minute; include at least one "just think once" and one quiz moment.
  - Gloss every jargon term the first time ("అంటే…" / "I mean…").
  - Package numbers as a sandwich: context → before/after → "that means" → twist.
  - Double words for emphasis ("big, big"), and ventriloquise stakeholders ("the client says…").
  - Say large Indian numbers twice ("3 lakh crore, literally three lakh crore").
  - End in reassurance and empowerment.
- **Telugu:**
  - Telangana forms (చేసినారు, వచ్చినారు, పెట్టిండు, అయితది, పోతది, తెలవంది).
  - Use the connectors అంటే, కదా, సో, అనేది and అన్నమాట at roughly his frequency (DNA §6.3).
  - Keep English nouns, verbs and numbers in Telugu script (ఇన్వెస్ట్ చేసినారు, ఫైవ్ ట్రిలియన్ డాలర్స్).
  - Put company and product names in Latin script where he would show them on screen (Tesla, SpaceX).
- **English:** Indian-English spoken register ("right?", "I mean", "basically", "here's the real twist", "you got clarity, right?"). Short spoken sentences. Keep ₹ crore and lakh.

**Length:** about 200 to 215 English words a minute of runtime; Telugu about 165 to 175 words a minute. A new beat every 60 to 75 s. Aim for 5 to 7 numbers a minute in the escalation blocks.

### 6. Production notes
- 3 title options in his pattern (DNA §9): an English title, 2 to 3 emojis, a provocative yes/no or "Why ??" question, and a promise suffix such as "| Detailed Explanation 2026".
- A thumbnail concept.
- On-screen text and B-roll for each beat.
- A description with chapters (timestamps from the beat sheet) and a sources list.

### 7. Self-review before handing over
Run the DNA §12 checklist. Also confirm:
- the English and Telugu scripts line up beat by beat;
- every number matches the research doc;
- the maths check passed;
- no future event is stated as fact;
- every plant has a payoff.

Report the runtime estimate (word count ÷ words a minute) and any facts that are still uncertain.
