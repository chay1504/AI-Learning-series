# Production Notes: Video A, "Inside a Neural Network"

Companion files: `script-telugu.md` (recording script) · `script-english.md` (review rendering). Source research: `research/dl-content-research.md`, `research/dna-parts/01-…`, `02-…`.

---

## 1. At a glance

| | |
|---|---|
| Channel episode | **AI Learning Series Day 9** (the last published episode is Day 8) |
| Curriculum plan days covered | Day 21 (What is DL) · Day 22 (Artificial neuron) · Day 23 (How a NN works / layers) · Day 24 (Weights & biases) |
| Spoken length | **4,276 English-equivalent words ÷ 175 wpm ≈ 24.4 min (≈ 24:26)**. Telugu track ≈ 3,750 tokens ≈ 154 tokens/min, inside his measured 149–165 range |
| Mid-roll CTA | 08:40, at **35.5%** of runtime (template: 35–45%). Like D7, it cuts in mid-thought, right before the "logistic regression = 1 neuron" reveal, as a cliff-hanger |
| Minutes per concept | DL ≈ 4.9 · Neuron ≈ 5.4 (incl. mid-roll) · Layers ≈ 5.4 · Weights & biases ≈ 3.7 |
| "Write it down" prompts | 01:47 agenda · 02:19 · 02:54 DL def · 05:43 three reasons · 07:50 neuron def · 11:11 terminology · 13:12 NN def · ~16:10 forward pass · 18:34 W&B def · 22:55 notes. Max gap is ≈ 3 min |
| Worked examples | One per concept, all calculator-checkable: Student D neuron (+ Student A) · Sita's forward pass (+ Ravi/Kiran shown as a table) · "turn the knobs" on Student D |
| Deliberately NOT covered (Video B) | Why activation is needed / ReLU in depth, loss, gradient descent, backprop, learning rate. Sigmoid is only "the squashing function from Day 7". ReLU is only a one-line "negative → 0" rule (needed so that Sita's h2 = 0 matches Video B) |

### Renumbering note
The script says **"Day 9"** to follow the channel's numbering. If you renumber to match the plan ("Day 21"), change exactly these lines in both scripts:
- T02: "welcome back to AI Learning Series Day 9" / "అప్పుడే మనం Day 9 కి వచ్చేసినాం".
- T03 and T30: "Day 1 నుంచి Day 8 వరకు" → the new range.
- T30: "జస్ట్ 9 videos ఏ అయిపోయినాయి" → the new count.
- The title card (T02 board cue), the titles below, and the description.

Internal callbacks such as "Day 2 circles", "Day 3 training vs testing" and "Day 7 Student D" refer to **published** episodes, so leave them as they are.

### Delivery tips for Deepak
- The script is deliberately a little *cleaner* than his natural speech. The filler density is about half his usual rate (సో ≈ 40 and అన్నమాట ≈ 37 in the script, against roughly 80 and 65 in a normal 24-minute video). Let the natural సో / అంటే / అన్నమాట / యా come out while recording; don't read it word-perfect.
- **Read definition cards verbatim, in English.** Viewers copy them into notes.
- "అన్నా" appears only in viewers' reported speech, never as him addressing viewers. Keep it that way.
- Draw live on the board for T03, T06–T08, T12, T14, T17, T19–T21, T23–T26. Show the tables in T16, T22 and T26 as pre-made overlays if the live drawing gets crowded.

---

## 2. Title options (his title style)

1. **😱 Deep Learning Explained in Telugu 🧠 | Neural Network Inside | AI Learning Series Day-09 ✅**
2. **Neural Networks Explained ✅ | Neuron, Layers, Weights & Bias | AI Learning Series Day-09 | Ft. Tech Boy Deepak**
3. **Deep Learning in 24 Minutes ...... 🧠✅ | Logistic Regression = 1 Neuron?! 😱**

## 3. Thumbnail text ideas

- **"1 NEURON = Logistic Regression?! 😱"** with a hand-drawn neuron showing "z = 2.4 → 91.7% ✅".
- **"DEEP LEARNING 🧠 INSIDE"** with Deepak pointing at a 3-column network (input → hidden → output).
- **"Day 7 lo already chesaru! 🤯"** (curiosity hook for returning viewers).
- **"Network: FAIL ❌ · Sita: PASS ✅ ?"** (teases the Video B cliff-hanger).
- Small corner badge on all of them: "AI Learning Series · Day 9".

---

## 4. YouTube description (paste-ready)

> Chapter times are script estimates. Re-time them after the edit; YouTube needs the first chapter at 00:00 and each chapter to be at least 10 seconds long.

```
AI Learning Series Day 9 🧠 Deep Learning lo first step! Neural network lopala em jarugutundo board meeda draw chesi, mana Day 7 Student D example tho simple ga explain chesa.
Day 7 lo meeru chesina logistic regression calculation — adi already oka neuron! 😱

📌 Ee video lo:
1️⃣ What is Deep Learning?
2️⃣ What is an Artificial Neuron? (inputs, weights, bias, output)
3️⃣ How does a Neural Network work? (input, hidden, output layers)
4️⃣ What are Weights & Biases?

⏱ Chapters
00:00 How did this video reach you?
00:45 Recap: AI → ML → DL
01:47 Today's agenda
02:54 What is Deep Learning?
05:43 Why Deep Learning now?
06:24 Deep Learning in your daily life
07:50 What is an Artificial Neuron?
09:17 Logistic Regression = 1 Neuron (Student D)
11:11 Parts of a neuron
13:12 Input, Hidden & Output layers
14:43 Forward pass example (Sita)
17:15 What does "deep" mean? 9 vs 175 billion
18:34 What are Weights & Biases?
20:00 Turning the knobs on Student D
22:15 Quiz – answer in comments!
22:55 Recap
23:35 Next video: how does a network LEARN?

📒 NOTES (definitions, formulas, examples)

▶ Deep Learning
Deep learning is a subset of machine learning that uses artificial neural networks with many layers to learn patterns, and even the useful features themselves, directly from large amounts of data such as images, audio and text.
• AI ⊃ ML ⊃ DL. Deep = many (hidden) layers. No fixed official number.
• ML: we choose the features (study hrs, sleep, attendance). DL: the network learns features from raw data (photos, audio, text).
• Why now: big data + GPUs + better algorithms.
• DL is NOT always better: for small tables, decision trees / logistic regression are often enough.
• Neural networks are only loosely inspired by the brain.

▶ Artificial Neuron
An artificial neuron is a small mathematical unit that takes one or more inputs, multiplies each input by a weight, adds them up together with a bias, and passes the result through an activation function to produce a single output.
• Step 1 (weighted sum): z = w1·x1 + w2·x2 + … + b
• Step 2 (activation): output = σ(z) = 1 / (1 + e^(−z)), e ≈ 2.718
• σ output = probability between 0 and 1; threshold 50% → Pass / Fail
• Student D: x1 = 4 hrs, x2 = 80%, w1 = 0.8, w2 = 0.04, b = −4
  z = 3.2 + 3.2 − 4 = 2.4 → σ(2.4) = 0.917 → 91.7% → PASS
• Student A: 1 hr, 50% → z = 0.8 + 2 − 4 = −1.2 → σ = 0.231 → FAIL
• Logistic regression = a neural network with exactly ONE neuron.
• "Bias" here is just a number, NOT unfair bias!

▶ Neural Network (layers)
A neural network is a set of artificial neurons arranged in layers (an input layer, one or more hidden layers, and an output layer), where the outputs of one layer become the inputs of the next.
• Input layer: just holds the data (no calculation)
• Hidden layer(s): build intermediate patterns (we don't see their values)
• Output layer: final answer (pass/fail → 1 neuron with sigmoid)
• Fully connected: every neuron connects to every neuron in the next layer; each line = one weight
• Forward pass = input → hidden → output = how the network makes a prediction
• Our toy network (weights assumed for demo):
  h1 = ReLU(1·S + 0.5·L − 6)   h2 = ReLU(0.5·S + 1·L − 7)   output = σ(1·h1 + 1·h2 − 2)
  (ReLU for today: negative → 0, positive → same number. Details next video.)
  Ravi (S 4, L 7): h1 1.5, h2 2 → z 1.5 → 81.8% Pass
  Sita (S 6, L 3): h1 1.5, h2 0 → z −0.5 → 37.8% Fail
  Kiran (S 1, L 8): h1 0, h2 1.5 → z −0.5 → 37.8% Fail
• Parameters: 4 + 2 + 2 + 1 = 9. GPT-3 (2020): 175 billion.

▶ Weights & Biases
Weights are numbers that decide how strongly, and in which direction, each input affects a neuron's output. A bias is a number added to the weighted sum that shifts how easily the neuron activates, whatever the inputs are. Together, weights and biases are the parameters that a neural network learns during training.
• + weight pushes up, − weight pulls down, ≈0 ignored
• Bias = starting point / cutoff (like the 36-marks pass mark)
• Turning the knobs on Student D (4 hrs, 80%):
  Original → z 2.4 → 91.7% Pass
  w2 = 0 → z −0.8 → 31.0% Fail
  b = −6 → z 0.4 → 59.9% Pass (barely)
  b = −2 → z 4.4 → 98.8% Pass
  + Instagram 3 hrs × (−0.5) → z 0.9 → 71.1% Pass (less sure)
• Weight size depends on input scale: 0.04 × 80 = 3.2 = 0.8 × 4 (or 4 × 0.8 if attendance is written as 0.8)
• Weights start random and are LEARNED from data — not typed in by programmers
• A trained model file is mostly its weights & biases

❓ Quiz (answer in comments!)
1. Which runs on deep learning: face unlock, Google Lens, YouTube recommendations, Google Translate camera, or all?
2. Student X: 3 hrs, 50% attendance, w1 0.8, w2 0.04, b −4. z = ? Pass or fail?
3. Student D's bias changes from −4 to −8. Still pass?
4. Our network: studied 6 hrs, slept 8 hrs. Is h2 ON or OFF?

👉 Next video: How does a neural network LEARN? Activation functions, loss, gradient descent, backpropagation.
👉 Watch Day 1–8 first if you're new: [playlist link]

#AILearningSeries #DeepLearning #NeuralNetwork #TeluguTech #TechBoyDeepak #MachineLearningTelugu #AIinTelugu
```

---

## 5. Board drawings and on-screen assets to prepare

**Live board drawings (in order)**
1. Three nested circles AI ⊃ ML ⊃ DL with the ML recap list (T03). Reused in T06 and T29.
2. Handwritten 4-item agenda (T04).
3. Two-half board: ML table → model vs answer-sheet photo → stack of layers; "12 MP × 3 ≈ 36,000,000 numbers"; "edges → letters → words" (T07).
4. Stick figure far → near → face doodle (T08).
5. Three icons: Data · GPU · Better algorithms (T09).
6. Two myth/fact lines for DL (T11).
7. Tiny biological-neuron cartoon labelled dendrites/cell body/axon (T12).
8. **The hand-drawn neuron**, the signature drawing of the episode (T14). Big circle split into Σ | σ, two input arrows (4, 80), weights ×0.8 / ×0.04, bias arrow −4, "3.2 + 3.2 − 4 = 2.4", "σ(2.4) = 0.917", output arrow "91.7% → PASS", stamp "Logistic Regression = 1 Neuron!".
9. Cricket-selector neuron (T17).
10. "bias ≠ unfair bias" in red; one straight line splitting two colours of dots (T18).
11. **The 3-column network** (T19–T21): S, L → h1, h2 → output; all 4 + 2 lines; weights 1, 0.5, 0.5, 1, 1, 1; biases −6, −7, −2; Sita's values with −1 struck through → 0; "Forward pass →" arrow.
12. Erase-and-redraw the network with 3 hidden columns: "Deep = many hidden layers" (T23).
13. Redrawn neuron with thick/thin/dashed-red weight arrows (T24).
14. Music-system knob panel w1, w2, b, w3 (T25).
15. Number line Fail ← 0 → Pass with a moving dot: 2.4 → −0.8 → 0.4 → 4.4 → 0.9 (T26).

**Pre-made screen assets**
- Definition cards (4), English, full screen: DL (T06), Neuron (T12), Neural network (T19), Weights & biases (T24).
- Formula card σ(z) = 1 / (1 + e^(−z)), e ≈ 2.718 (T15), and the two-step strip "probability → threshold → 0/1".
- Terminology card: Input (x) · Weight (w) · Bias (b) · Weighted sum (z) · Activation (σ) · Output (T16).
- Tables: Student D / A (T16) · Ravi / Sita / Kiran (T22) · Knob-turning table (T26).
- Nobel 2024 text card (T09). Icon grid for daily-life examples (T10).
- "9 parameters vs GPT-3 175,000,000,000" number card (T23).
- Quiz card (T28). Teaser card for Video B (T30). Day 7 Student D slide clip (T03, T14).
- YouTube home-feed screen recording for the cold open (T01).

---

## 6. Comment quiz: answers (for the pinned comment)

1. **All of them (e).** Face unlock, Google Lens, YouTube recommendations and the Google Translate camera all use neural networks. *(UPI fraud alerts are deliberately not in the list: they are AI/ML-based, but the research could not confirm that they are deep networks specifically.)*
2. z = 0.8×3 + 0.04×50 − 4 = 2.4 + 2.0 − 4 = **0.4** → σ(0.4) ≈ **0.60** → **Pass**, but only about 60% sure.
3. z = 6.4 − 8 = **−1.6** → σ ≈ **0.17** → **Fail**.
4. h2 = 0.5×6 + 1×8 − 7 = **4** → **ON**. (Bonus: h1 = 6 + 4 − 6 = 4, z = 4 + 4 − 2 = 6, σ(6) ≈ 0.998 → Pass.)

All values were checked in Python (σ(0.4) = 0.5987, σ(−1.6) = 0.1680, σ(6) = 0.9975).

---

## 7. Accuracy notes

**Arithmetic.** Every number was re-computed in Python and matches `research/dl-content-research.md`: σ(2.4) = 0.9168, e^(−2.4) = 0.0907, σ(−1.2) = 0.2315, σ(−0.8) = 0.3100, σ(0.4) = 0.5987, σ(4.4) = 0.9879, σ(0.9) = 0.7109, Ravi 0.8176, Sita / Kiran 0.3775, 9 parameters, 12 M × 3 = 36 M. **No research numbers were changed.**

**Research items tagged [verify]: kept out of the script**
- Sarvam's ~105 B-parameter model (India AI Impact Summit, Feb 2026): **not used**. GPT-3 (175 B, 2020) is used instead, because it is well documented (Brown et al., 2020).
- "India is ChatGPT's No. 1 market": **not used**. The script only says ChatGPT/Gemini answer in Telugu.
- Google MLCC sub-page paths: not relevant to the script.

**Optional stats for the T10 B-roll** (sourced in the research file; use only after re-checking the link before upload):
- Aadhaar face authentication crossed 200 crore transactions by Aug 2025 (Business Standard).
- DigiYatra mandatory for international transit at Delhi, Mumbai, Bengaluru and Hyderabad from 1 June 2026 (Outlook Traveller).
- Qure.ai qXR Delhi screening, Jul 2025–Mar 2026: 1,68,568 X-rayed, 18,377 flagged, 877 TB confirmed (ThePrint).
- India ~100 M weekly ChatGPT users (Sam Altman, Feb 2026; TechCrunch). This is a company claim.

**Claims in the script, with their basis**
- 2024 Nobel Prize in Physics: Hopfield & Hinton, "for foundational discoveries and inventions that enable machine learning with artificial neural networks" (nobelprize.org). ✔
- YouTube recommendations use deep neural networks: Covington et al., RecSys 2016. ✔
- DigiYatra: the script says "face recognition systems like that mostly run on neural networks". This was **softened on purpose**, because DigiYatra's own algorithm isn't documented in the research.
- TB X-ray AI "flags, then doctors check": accurate framing. WHO has recommended computer-aided detection for TB screening since 2021.

**Simplifications flagged on camera or kept safe**
- *Amma's handwriting / relative-from-far* layers analogy: disclaimed on camera ("not the exact technical example").
- *"edges → letters → words"* layer labels: illustrative. Real layers learn whatever is useful.
- *h1 = "study" / h2 = "rest" neuron names*: disclaimed on camera ("our labels for the story").
- *ReLU*: introduced only as a one-line rule (negative → 0), and the script says it's an activation function covered next video. This is needed so the Day 23 numbers (Sita's h2 = 0) match Video B.
- *Bias ≈ 36-marks cutoff*: exact in this setup. With b = −4, z > 0 (σ > 50%) happens precisely when 0.8·hrs + 0.04·att > 4.
- *Cricket selector / knobs analogies*: on camera, the selector is said to use opinion while a neuron learns from data, and knobs are said to be able to go negative.
- *"One neuron = straight-line boundary"*: true for a single weighted-sum neuron with a monotonic activation (= logistic regression).
- *"A model file is mostly weights & biases"*: "mostly" keeps it correct. The file also holds an architecture config, a tokenizer, etc.
- *12 MP × 3 = 36 M numbers*: correct as the raw count. In practice, images are usually resized before going into a network. It isn't needed on camera.
- *"Deep" has no fixed number of layers*: the script says only "many hidden layers".

**Day 7 slips corrected on camera (T15):** the sigmoid output is a probability between 0 and 1 (the threshold makes it 0/1); e ≈ 2.718; the formula is written with brackets, 1 / (1 + e^(−z)).

---

## 8. Continuity hooks into Video B ("How a Neural Network Learns", Days 25–28)

**Open questions Video A leaves for Video B to answer (said on camera, T22 and T30)**
- "Network ki weights ela vasthayi? Ela nerchukuntadi?" (Every weight in Video A was assumed.)
- **Sita actually PASSED**, but the network said 37.8% → "how will the network correct its own mistake?" (This sets up Day 26 loss −ln(0.378) = 0.974 and Day 28 backprop on Sita.)
- Next-video list said aloud: activation functions, loss, gradient descent, backpropagation.

**Established in Video A, so Video B can call back without re-teaching**

| Item | Exactly as in Video A |
|---|---|
| Student D neuron | x1 = 4 hrs, x2 = 80%, w1 = 0.8, w2 = 0.04, b = −4 → z = 2.4 → σ = 0.917 (91.7%) |
| Attendance rescale | Said in T27: "80% as 0.8 → weight 4 → 4 × 0.8 = 3.2, same contribution". This sets up Day 27's w2 = 4 version (Priya example) |
| Sigmoid | "Squashing function from Day 7", output is a probability 0–1, σ(z) = 1 / (1 + e^(−z)). **Why** activation is needed was NOT explained → Day 25 |
| ReLU | Only "negative → 0 (OFF), positive → same number (ON); name is ReLU, next video". Sita's h2 sum −1 → 0 shown on the board → Day 25 callback (c) |
| Day 23 network | h1 = ReLU(1·S + 0.5·L − 6), h2 = ReLU(0.5·S + 1·L − 7), out = σ(1·h1 + 1·h2 − 2); 9 parameters |
| Students | Ravi (4, 7) → 81.8% Pass · Sita (6, 3) → h1 1.5, h2 0, z −0.5, 37.8% Fail (actually passed) · Kiran (1, 8) → 37.8% Fail |
| Vocabulary defined | input, weight, bias, weighted sum z, activation, output, input / hidden / output layer, fully connected, **forward pass**, parameters |
| Analogies used (reuse, don't contradict) | Cricket selector (neuron) · **music-system knobs** (weights/bias; "learning = turning knobs till the prediction is right") → natural lead-in to gradient descent "which way to turn each knob" · strict / lenient examiner & grace marks (bias) · Instagram scrolling (negative weight) · 36-marks cutoff (bias) |
| Analogies deliberately NOT used | Curry salt, ghat-road hill, water-tank overflow, restaurant-complaint, cricket post-match. All are left for Video B |
| Facts stated | "Weights start small & random and are adjusted from data", "a trained model is basically its weights & biases", "more layers can overfit (Day 3 training vs testing)" |

**Suggested Video B opening callback:** "Last video lo Sita gurtunda? Network 38% fail annadi, kani tanu pass ayindi. Ivala aa mistake ni network ela correct chesukuntado chuddam."
