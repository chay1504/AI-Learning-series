# Style DNA Research Report: Tech Boy Deepak, AI Learning Series

**For:** the channel team, and anyone briefing a writer on scripts in Deepak's voice.
**Status:** 2026-11-08. Built from Days 6–8.
**Detail files:**
- [`dna-parts/01-structure-pacing-depth.md`](dna-parts/01-structure-pacing-depth.md) covers segment maps, timings, the teaching loop and depth.
- [`dna-parts/02-voice-language-analogies.md`](dna-parts/02-voice-language-analogies.md) covers code-mixing, dialect, the full phrase table, the analogy catalogue and a sample paragraph.

**Related files:** [`dl-content-research.md`](dl-content-research.md) (Days 21–28 content) and [`../coverage/topics-covered.md`](../coverage/topics-covered.md).

**Quote keys:** `D7 [10:42]` means Day 7, the caption block starting at 10:42. Quotes are glossed in English. The Telugu wording is given where the exact words matter.

---

## 1. Executive summary: 10 traits that make a script "sound like Deepak"

1. **Fixed bookends.** Every video opens with *"Hey guys, welcome (back) to AI Learning Series Day N"*. Every video closes with *"Thank you so much (for watching), signing off, Tech Boy Deepak."*
2. **Classroom mechanics.** He reads a formal English definition from the screen and says *"రాసుకోండి"* (write it down). That happens about every 3–4 minutes. Notes go in the description, or "by tonight".
3. **One teaching loop for every concept.** Definition → "అంటే…" paraphrase → "ఇంకా సింపుల్ గా చెప్పాలి అంటే…" → everyday example → step-by-step visual → term drill → a doubt he raises himself → *"Simple, this is X."*
4. **Telugu grammar, English content words.** Every technical term stays in English and is never translated. Verbs are built from an English stem plus చేయ్/అవ్వు: *predict చేస్తది, confuse అవ్వద్దు*.
5. **Telangana colloquial Telugu.** He uses *-తది* endings (చేస్తది, ఉంటది) about 85% of the time. Other markers: చూసినం, చదివిండు, వచ్చినాయి. The slang is light, and he never uses రా/బ్రో/మామ.
6. **Three particles carry the delivery:** **సో**, **అంటే**, **అన్నమాట**. Together they come to about 9 per minute.
7. **Student life and Indian money.** His examples come from pass/fail, marks, hours studied, attendance, ₹ and lakhs, and shop prices. **One student example is reused and extended across days.**
8. **A reassuring big brother.** He says *"అస్సలు భయపడకండి"* (don't be scared at all) and *"don't get confused"*. He admits it took him 2–3 days to learn this. He corrects his own slips on camera, and the tone stays honest.
9. **Depth is limited, and he says so.** Each video gets at most one worked formula, with assumed numbers you can check on a calculator. Anything deeper is named and deferred: *"ఇంత డెప్త్ గా మాథ్స్ లోకి వెళ్ళట్లేదు… ఆగం అవుతారు"* (we're not going this deep into maths yet; you'd get flustered).
10. **Fixed engagement beats.** A mid-roll that opens *"Sorry for interrupting the video in the middle…"*. About 1.5 rhetorical questions per minute, each with the tag *కదా*. A quiz or comparison table near the end. Catch-up nudges at the start and the end.

---

## 2. Evidence base and caveats

| Day | Video | Analysed? |
|---|---|---|
| 1 | What is RAG? | No. YouTube blocked automated transcript access |
| 2 | AI vs ML vs DL | No (blocked) |
| 3 | How does AI actually learn? | No (blocked) |
| 4 | Build your first ML project (student pass/fail) | No (blocked) |
| 6 | Classification vs Regression (~16:45) | **Yes** |
| 7 | Decision Tree, Logistic Regression, SVM (~25:50) | **Yes** |
| 8 | K-Means, Hierarchical, DBSCAN (~24:00) | **Yes** |

- **Sample size.** 3 of the 7 shared videos (about 66 minutes) were analysed. Day 5 was not among the links we received. All three analysed videos are **ML-algorithm episodes**, so the patterns may differ for intro episodes (Days 1–3) and project episodes (Day 4).
- **Captions are machine-generated.** We used Telugu ASR plus YouTube's auto-English. Spellings like మిషన్/మెషీన్ are recogniser noise. The English track adds words he does not say; "basically" is the clearest case. Phrase counts are accurate to about ±10%, but the rankings hold.
- **Timestamps** mark the start of a caption block, so the real moment can be up to about 60 seconds later. Part 01 uses English-track blocks and Part 02 uses Telugu-track blocks, so the same line can carry slightly different times in the two files.
- **Earlier episodes are inferred, not seen.** The pass/fail model was built in an earlier episode. The coverage map says Day 4; the Day 6 recap calls it "the last video". Treat anything about Days 1–5 as inference.

---

## 3. The DNA, by parameter

### 3.1 Video architecture and timing
**Rule:** 18–25 minutes, three concepts, about 175 English-equivalent words per minute (wpm), with the same skeleton every time.

| Block | Time | Share |
|---|---|---|
| Welcome → recap → agenda → reassure/notes | 0:00–~2:00 | 9–17% |
| Concept 1 | ~6 min | |
| Mid-roll CTA | 40–50 s | lands at 35–46% |
| Concepts 2 and 3 | 5–7 min each (up to ~10 if maths-heavy) | |
| Compare table or quiz | ~1 min | |
| Recap + outro | ~1–1.5 min | |

**Evidence:** Logistic regression ran about 10.5 minutes, about 5 of them on one worked example (D7 [08:25–19:15]). Sub-types got 30–45 seconds each (D6 [04:25–06:00]).
**Apply:** Budget about 3,500 English-equivalent words (about 3,100 Telugu-script words) for 20 minutes. Give a headline concept 5–7 minutes, a sub-type 30–45 seconds, and a name-drop about 25 seconds.

### 3.2 Opening formula
**Rule:** The welcome names the day number. Then a recap, a **numbered agenda**, *"Let's dive into the video"*, and a reassurance. The first definition comes by about 2:00.
**Evidence:**
- "Hey guys, welcome back to AI Learning Series Day 8. We've already reached Day 8." (D8 [00:00])
- "First, the Decision Tree… Second is Logistic Regression. Third is Support Vector Machine." He writes this with a pen (D7 [00:20]).
- "Don't be afraid at all… you yourself will say, 'This is very easy, anna; we thought this was hard.'" (D7 [00:50])

**Apply:** Use the welcome line, a one-line headline promise, "First… Second… Third…", then *"Let's dive into the video"*. An optional 10–20 second subscribe pitch can go before the welcome (D7) or right after the agenda (D6). Keep the reassurance and the *నోట్స్ రాసుకోండి* cue before Concept 1. "No formal intro today" still means he does the recap and the agenda (D7).

### 3.3 Recap and continuity
**Rule:** Open with a recap, either an inventory list or a taxonomy walk (AI → ML → Supervised/Unsupervised → today's branch). Add a "watch the previous videos" nudge in the opening and again in the outro. Reuse the running examples.
**Evidence:**
- "If you haven't watched it, watch the last video. You might forget, so we need to revise." (D7 [01:02])
- "only six videos are done… you can cover them all if you sit for one day" (D6 [15:55])
- Promises he has kept: the decision tree was previewed in D6 and taught in D7.

**Apply:** In every new script:
- Call back to the **student pass/fail model** (study hours, sleep, attendance; "Student D" from D7).
- Walk the taxonomy down to today's topic.
- Pay off at least one open promise. Precision/recall, the maths of MAE/MSE, and "AI tools" are still open from D6.

### 3.4 Per-concept teaching loop
**Rule:** Announce → (contrast with the last concept) → **definition on screen + "write it down"** → unpack the name → unpack 1–3 keywords → everyday example → visual walk-through → term drill → anticipated doubt → *"Simple, this is X"* → (defer the deeper part). He states each idea 3–4 times.
**Evidence:**
- "It's in the name itself, 'Decision Tree'… trees have branches, right?" (D7 [02:19])
- "a question should arise in all of your minds… why does [logistic *regression*] come under classification?" (D7 [08:25])
- "Simple, this is what we call a decision tree." (D7 [07:33])

**Apply:** Definition first, example second. The formal English definition stays short and on screen; the explanation around it is in Telugu. End each concept on a one-liner using the "…చేసేదే X" pattern ("the thing that does … is X").

### 3.5 Board, pen and notes behaviour
**Rule:** Show slide definitions, then draw his **own pen diagram** beside the slide, point with the cursor, and use a live demo where possible. He says openly where the material came from (GPT, NotebookLM, "the notes I brought").
**Evidence:**
- "I will also draw a diagram on the side to explain it" (D7 [05:30])
- "I am using GPT for reference" (D7 [13:10])
- "I used NotebookLM… but I won't present it like a lecture" (D8 [02:20])
- Live SVM website demo (D7 [22:10])

**Apply:** For each concept, specify in the script (a) the definition card, (b) what he draws by hand, step by step, and (c) one demo or animation per video if one exists. Tie "take notes" prompts to definitions, formulas and term names only, never to examples. Promise notes "in the description".

### 3.6 Depth calibration (maths, jargon, code)
**Rule:**
- **Maths:** at most one worked formula per video, with assumed weights and toy numbers. He says: "Don't worry about the math… let's learn slowly."
- **Jargon:** English term + full form + verbatim English definition + Telugu paraphrase. He then either tells viewers they can forget the term or flags it as "very important terminology".
- **Code:** only as an on-screen "run it in Colab" artefact. He never walks through it line by line.

**Evidence:**
- σ(z) = 1/(1+e^(−z)) for Student D: z = 2.4 → 0.917 → pass. He adds: "these are the illustrative values… The machine will calculate it on its own." (D7 [13:10–18:30])
- Gini and entropy get only "pause the screen and write down" (D7 [07:55]).
- MAE/MSE are named only: "I am not going too deep into the math just yet" (D6 [11:15]).

**Apply:** See §4. When you stop, **give the reason** (*ఆగం అవుతారు*, "you'll get flustered") and promise a later video.

### 3.7 Example universe and analogy style
**Rule:**
- About 45% of examples come from student/exam life and about 20% from Indian money (₹, lakhs, square yards). The rest are spam email, animals, fruit (mango), and one physical metaphor per mechanism (tree, magnet, radar, twins, corner).
- Toy rows are named A–F and use round numbers.
- Second person: "*you* want to buy a house".
- Each leaf gets a common-sense reason: "fail, because he didn't study".

**Evidence:**
- "just like we say that getting more than 36 marks in exams is a pass, this is similar" (D7 [10:00])
- "treated C2 like a magnet" (D8 [05:50])
- "don't think this is the exact technical example" (D8 [01:01], the disclaimer on the twins analogy)

**Apply:** Reuse the student, the spam email, the house and the spenders before inventing anything new. Add **one** new feature per video. Disclaim loose analogies. Cricket and movies would fit the persona, but they are **not attested**, so use them sparingly. Never use $, miles or Western defaults.

### 3.8 Language mix and dialect
**Rule:**
- Telugu syntax, case endings and particles, with English nouns, adjectives and verb stems. About 30–45% of tokens are English (60%+ while he reads definitions).
- Telangana forms are the default: *-తది*, *-ఇనాం/-ఇనం*, *-ఇండు*, *-ఇనాయి*, ఎట్లా, లేకుంటే. Standard *-తుంది* appears about 1 time in 6.
- Spoken English is limited to single words, read-out definitions and stock lines.

**Evidence:**
- "ఒక క్యాటగిరీని ప్రిడిక్ట్ చేసేదే క్లాసిఫికేషన్" (the thing that predicts a category is classification) (D6 [03:52])
- "లెస్ దన్ టూ అవర్స్… ఫెయిల్ పక్కా ఫెయిల్" (less than two hours… fail, definitely fail) (D7 [06:27])

**Apply:**
- Write Telugu in Telugu script and English terms in **Latin script**, e.g. "ఈ model ఏం చేస్తది అంటే…". Use ASR-style transliteration only if TTS needs it.
- Never coin Telugu terms for ML concepts (no యంత్ర అభ్యాసం).
- Use slang (ఆగం, ఎమ్మటే, మూలకు, పక్కా) at most once per video.

### 3.9 Signature phrases and fillers (trimmed; full table of 56 in Part 02)

| Phrase | Use | ≈ per 20 min |
|---|---|---|
| **సో** | starts sentences, transitions | 68 |
| **అంటే** | "meaning…"; the hinge of every explanation | 65 |
| **అన్నమాట** | closes explanatory sentences ("you see") | 53 |
| మనం / మన | inclusive "we / our" | 44 |
| **వచ్చేసి** | lists and values: "ఫస్ట్ వన్ వచ్చేసి…", "z వాల్యూ వచ్చేసి 2.4" | 25 |
| **కదా** | "…right?" tag | 14 |
| X అంటే ఏంటి(ది)? | self-posed question | 9 |
| **సింపుల్** / అంతే సింపుల్ / ఏం లేదు చాలా సింపుల్ | comfort word | 9 |
| ఫర్ ఎగ్జాంపుల్ … అనుకుందాం | sets up an example | 5 |
| దీన్నే X అంటాం అన్నమాట | "this is what we call X" | 10 |
| ఇంకా సింపుల్ గా చెప్పాలి అంటే | "to put it more simply" | 2–3 |
| రాసుకోండి / నోట్స్ | "write it down" / "notes" | 5 + 4 |
| గుర్తుపెట్టుకోండి | "remember this" | 5 |
| కన్ఫ్యూజ్ అవ్వద్దు | guard at look-alike pairs | 2 |
| పేర్లోనే ఉంది కదా | "it's in the name" | 1–2 |
| *Stock English:* "Let's dive into the video", "That's it for the day", "Sorry for interrupting…" | segment markers | 1 each |

**Not his words:** "basically" (it comes from the translator), మస్తు, బ్రో, రా, మామ. **"అన్న/అన్నా" appears only in viewers' reported speech to him.** He never calls viewers that.

### 3.10 Tone and persona
**Rule:**
- A warm senior or big brother who learns alongside the viewers.
- Before any difficulty, he voices the viewer's fear in their own words and then flips it.
- He is honest about difficulty, and the humour is mild and situational.

**Evidence:**
- "when I attended the class, it took me two to three days" (D7 [25:00])
- "it's not as easy as you might think" (D6 [10:15])
- "The handwriting with this pen isn't coming out right, so ignore that" (D7 [00:20])

**Apply:**
- Include one humility or honesty beat per video, and say "you" and "we" throughout.
- Don't make him slick or infallible, but don't script confusion either.
- Never talk down to viewers. Even caveats are framed kindly.

### 3.11 Engagement devices and CTA
**Rule:**
- The mid-roll follows one shape: apology → like / three dots → "hype" / subscribe → why ("reaches beginners like you") → one statistic or piece of social proof → straight back to content.
- Ongoing devices: rhetorical Q&A ("What do you think? Yes…"), *కదా* tags, "I hope you understood", at least one comment prompt, and a quiz or comparison near the end.

**Evidence:**
- "90% of our viewers are not subscribed" (D6 [01:20]; D8 [11:05])
- "200,000 members gave it a hype" (D6 [06:20])
- "Is it classification or regression? Test it in 30 seconds" (D6 [14:30])

**Apply:**
- Place the mid-roll at 35–45% of the runtime, even if it lands mid-concept, as it did in D7.
- Close with one comment-quiz question per video.
- Write about 1.5 rhetorical questions per minute.

### 3.12 Closing formula
**Rule:**
- **Fixed:** "That's it for the day/video" → recap of the topics placed in the taxonomy → the sign-off line, verbatim.
- **Rotating (pick 2–3):** notes, homework (Colab, a website, the quiz), catch-up FOMO, a share request, a tease.

**Evidence:**
- "All these are in machine learning, in unsupervised learning, under clustering… Our team will share the notes with you by tonight… signing off, Tech Boy Deepak." (D8 [23:15])

**Apply:** The outro should run 45–80 seconds. His teases are weak today: only D6 has one, and he never names the next topic. **Naming the next day's topic is a cheap upgrade that stays in character.**

---

## 4. The depth dial

### 4.1 What is in and out of depth, from his own ML videos

| IN (he does this) | OUT (named and deferred, or skipped) |
|---|---|
| One formula read aloud, assumed numbers, calculator check (sigmoid, Student D) | How weights are learned, cost functions, log-odds |
| Arithmetic on 3–6 toy rows (accuracy 90/100, residual 55L − 50L, K-means means) | Precision/recall maths, confusion matrix, R², MSE formula |
| Vocabulary with one-line meanings (root/leaf node, hyperplane, margin, centroid, Epsilon) | Gini/entropy maths, linkage criteria, core/border points, the C parameter |
| Visual intuition plus a live demo (SVM kernels) | Kernel maths, distance metrics, choosing K (elbow) |
| "Generalises to 10 features: w10·x10" said in one line | Matrix or vector notation, calculus of any kind |
| Code shown on screen as homework | Line-by-line code walkthroughs |

**The test:** could a Class 10 student check it on a phone calculator? If yes, it is in. If no, name it, explain in one line why we're skipping it, and defer it.

### 4.2 Translating the dial to deep learning (Days 21–28)

Full lesson content is in [`dl-content-research.md`](dl-content-research.md). This table applies only his depth level.

| Topic | IN at his depth | OUT (name it at most) | Hook in his style |
|---|---|---|---|
| **Neuron** | inputs × weights + bias → activation → output. Redo Student D (4 hrs, 80%, w = 0.8/0.04, b = −4 → z = 2.4 → 0.917) | Biology detail, vector notation | "Remember Student D from Day 7? ఆ calculation నే ఒక neuron అన్నమాట." Logistic regression is one neuron |
| **Activation** | Sigmoid squashes any number into 0–1. ReLU = "negative అయితే 0, లేకుంటే అదే number". Why it's needed: without it, stacked layers collapse into one straight line | Derivatives of activations, tanh/softmax maths, vanishing gradients (one sentence at most) | "పేర్లోనే ఉంది కదా": it decides whether the neuron "activates"; the 36/35-marks pass-line idea |
| **Loss** | One "wrongness score". Marks: (actual − predicted)², e.g. 70 vs 62 → 64. Pass/fail: −ln(prob given to the right answer). Student D passed: −ln 0.917 ≈ 0.09. If he had failed: −ln 0.083 ≈ 2.49 | Deriving cross-entropy, likelihood | The answer key from supervised learning: "మనం model కి answer leak చేసినం కదా, now we check how wrong it was" |
| **Gradient descent** | The loss as a valley. Slope = direction. Update in words: new weight = old − (learning rate × slope). One step with illustrative numbers (0.8 − 0.1×0.5 = 0.75). Learning rate too big/too small | Partial derivatives, convexity, Adam internals, the (p − y)·x derivation | Walking down a hill in fog, one step at a time (disclaim it as loose) |
| **Backprop** | The error flows backwards along the same wires. A weight's blame ∝ the error × the input it carried. Say "chain rule" once. "Backprop calculates, gradient descent updates" | Chain-rule algebra, computational graphs, autodiff | Exam paper returned with marks cut: we trace back which answer cost marks |

**Rules that carry over:**
- One worked numeric pass per video.
- Weights are always called "assumed / illustrative; the machine calculates them itself".
- Reassure before any maths.
- A *కన్ఫ్యూజ్ అవ్వద్దు* guard at every look-alike pair: parameter vs hyperparameter, epoch vs iteration, loss vs accuracy, gradient descent vs backprop.

---

## 5. Scriptwriter's checklist (one page)

**Structure**
- [ ] The first sentence is "Hey guys, welcome (back) to AI Learning Series Day N". The last line is "Thank you so much (for watching), signing off, Tech Boy Deepak."
- [ ] Recap (inventory or taxonomy walk) + a callback to the running student example + a catch-up nudge, all within the first ~1:10.
- [ ] Numbered agenda ("First… Second… Third…") + "Let's dive into the video". First definition by about 2:00.
- [ ] 3 concepts. About 175 English-equivalent wpm (20 min ≈ 3,500 words).
- [ ] Mid-roll CTA at 35–45% of the runtime, opening "Sorry for interrupting…".
- [ ] Compare table or quiz near the end. Recap placed in the taxonomy. 2–3 rotating outro items. Next topic named.

**Teaching**
- [ ] Every concept: definition card + "రాసుకోండి" → అంటే paraphrase → "ఇంకా సింపుల్ గా…" → example → visual steps → term drill → anticipated doubt → "Simple, this is X."
- [ ] A notes prompt every 3–4 minutes, tied to definitions, formulas or terms only.
- [ ] A hand-drawn diagram specified for each concept. One demo or animation if one exists.
- [ ] At most one worked formula, with assumed round numbers you can check on a calculator. Everything deeper is named and deferred, with a reason.
- [ ] Reassurance before Concept 1 and before any maths.

**Voice**
- [ ] Telugu grammar, English terms in Latin script, no Telugu coinages for ML terms.
- [ ] *-తది* endings by default. Telangana past forms. Slang at most once.
- [ ] సో / అంటే / అన్నమాట present throughout, plus వచ్చేసి for lists and కదా for tags.
- [ ] Examples are student/exam life, ₹ and lakhs. Toy rows named A–E. No Western defaults.
- [ ] One humility or honesty beat. No రా/బ్రో/మామ. No "basically". He never calls viewers "అన్నా".
- [ ] At least one comment prompt and about 1.5 rhetorical questions per minute.

**Accuracy**
- [ ] Every on-screen definition is checked against a standard source. AI-generated slides are fact-checked.
- [ ] Every number is recomputed. The dataset is identical everywhere it appears.
- [ ] Loose analogies are disclaimed ("దీన్నే exact example అనుకోకండి").
- [ ] None of the §6 errors is repeated. Recaps of earlier days state the corrected version.

---

## 6. Known accuracy issues in past explanations, and the policy

Gathered from Part 01 §9.5, `dl-content-research.md`, and our own spot-checks of the Day 6–8 transcripts.

| # | Where | What was said | Correct version | Fix in future scripts |
|---|---|---|---|---|
| 1 | D6 [13:19] | Logistic regression listed "in regression", then corrected in the same breath | It is a classification algorithm with a misleading name | Introduce it as classification first, then the name paradox |
| 2 | D7 [08:25] | "the output in logistic regression is always zero or one… only probability" | The sigmoid outputs a **probability between 0 and 1**. The **threshold** turns it into class 0 or 1 | State both layers: probability → threshold → class |
| 3 | D7 [11:55] | e = "2.717", later 2.718 | e ≈ 2.718. Write the formula as σ(z) = 1 / (1 + e^(−z)) with brackets | Use 2.718. Bracket the formula card |
| 4 | D8 [04:55] vs [08:30–10:10] | Spenders introduced as ₹1000/1200/2000/8000/9000/9500, but recomputed as 1000/1500/2000 and 8000/8500/9000 → means 1500 and 8500 | With the data as introduced, the means are **1400** and **≈8833** | Use one dataset throughout. Recompute every mean |
| 5 | D8 [~16:55] | DBSCAN full form first given as "density-based grouping and noise detection" | **Density-Based Spatial Clustering of Applications with Noise** (he reads this correctly later) | Give only the correct full form |
| 6 | D8 [18:35], [22:15] | Epsilon is "a particular number; points close to that number" form a cluster | Epsilon is a **radius drawn around each point**. MinPoints is how many points (including itself) must fall inside it for a dense "core" point. Isolated points are noise | Define it as a radius around every point (the radar image fits) |
| 7 | D8 [~12:00–16:55] | Hierarchical merge narration muddled ("C-D-E-F merged with C"). Linkage never stated | Merges must be consistent. The 3,800 figure assumes nearest-pair (single) linkage; average linkage would give 4,000 | Say "nearest pair (single linkage)" once and keep the merge order clean |
| 8 | D8 [00:20] | The recap lists random forests as covered | Random forest was only previewed in D6 | Don't overclaim in recaps |
| 9 | D7 [10:00] | "more than 36 marks is a pass" | The SSC pass mark in AP/Telangana is generally **35**. Check before use | Say "35" or just "the pass mark" |
| 10 | D7 [22:10] | Kernel "uses a formula to divide them" | Acceptable at his depth. More precisely: a kernel lets SVM draw curved boundaries by comparing points as if they were in a higher dimension | A one-line upgrade is optional; no maths needed |

**Policy: keep his depth, but be technically correct.**
1. **Keep the depth, the framing and the analogies, and fix the content.** Viewers copy the on-screen definitions into their notes as truth, so a correct definition matters more than a polished one.
2. **Correct earlier mistakes going forward, without making a fuss.** Fold the fix into the recap in his voice: *"ఇక్కడ ఒక చిన్న point clear చేద్దాం…"* ("let's clear up one small point here"). Don't announce "I was wrong", and don't leave the error standing. Flag issue #2 explicitly in the Day 22 and Day 25 recaps, because deep learning builds on the sigmoid.
3. **AI-generated material is a draft, not a source.** He openly uses GPT and NotebookLM. Every definition and number drawn from them gets a human check before recording.
4. **Simplify, but never falsify.** A simplification may leave things out, for example "the machine calculates the weights itself". It must not state something wrong, such as "the output is always 0 or 1".
5. **Recompute everything.** Every arithmetic step in the script is re-checked, and each toy dataset is fixed once and reused verbatim.
