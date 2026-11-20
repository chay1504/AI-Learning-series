# Deep Learning Foundations: Content Research Brief, Part 3 (Days 29–30)

_For Tech Boy Deepak's Telugu "AI Learning Series". Prepared 20 Nov 2026._

- **Part 3: "Train Your First Neural Network"**, channel episode **Day 11**. It covers plan **Day 29** (epochs, batches, learning rate) and **Day 30** (build a neural network in Keras on Google Colab).
- **Companion notebook:** [`../notebooks/part-3-train-your-first-neural-network.ipynb`](../notebooks/part-3-train-your-first-neural-network.ipynb). It is tested end to end, and every "real result" below comes from it.
- **Format:** this follows [`dl-content-research.md`](dl-content-research.md) (Days 21–28): core idea → key points + depth boundary → toy numbers → analogies → whiteboard → misconceptions → quiz.

**Audience level:** college students with no maths background. Drawings first, numbers second. Code is a Colab artefact, explained in about 7 conceptual blocks and never as a syntax lesson (style DNA §3.6, §4.1).

**Research note.** In this session the web *search* tool worked, but direct page fetches to developers.google.com and keras.io were blocked by the network settings (DNS refused). So:
1. Every Keras behaviour quoted here was checked against the **installed Keras 3.15.1 source and docstrings** (`keras/src/trainers/trainer.py`, `keras/src/optimizers/sgd.py`, `adam.py`) and by actually running it.
2. Google MLCC, Google ML Glossary and deeplearning.ai facts were checked against search-result extracts of those pages.

Items marked **[verify]** should be re-checked on the linked page before filming. Every number below was produced or re-checked with Python. The log is in the Appendix.

---

## 0. Continuity: what Video B promised, and the fixed numbers for Part 3

### 0.1 Promises to pay off (from Video B's script and production notes)
| Video B line (segment) | Pay-off in Part 3 |
|---|---|
| "Repeat thousands of times" (I5, K1) | Each full pass over the data is an **epoch**. In the notebook, 100 epochs × 10 batches = **1,000 updates** |
| "Average the blame over many students and then update" (H4, J4) | That group of students is a **batch**. `batch_size=32` |
| "Step size = learning rate… details next episode with epochs and batches" (I4) | The learning-rate section, with Priya's numbers and a real Keras experiment |
| Outro: "what do we call each round? How many students' data do we give at once? What happens if the step size is too big?" | These are exactly the three Day 29 questions. Answer them in that order |
| "When we build a neural network… we'll write one line, model.fit(). Inside that one line, exactly this loop is running." (K1) | Day 30 block "Fit". Open the build half by redrawing the K1 loop next to `model.fit(...)` |
| Grey footnote (I5): "Real projects scale attendance to 0.6 first. Next episode." | Notebook Block 3: `X / 10` (6 hours → 0.6). One line: "remember 60% → 0.6?" |
| Video A: Sita 38% → "fail", but she actually passed | Notebook Block 9: the **trained** network says Sita **95% → PASS** |
| Video A: "9 knobs" | `model.summary()` → **Trainable params: 9** |

### 0.2 Fixed numbers (use these everywhere; do not invent new ones)
| Item | Value |
|---|---|
| Video A network | S, L → h1, h2 (ReLU) → output (sigmoid). Assumed weights: S→h1 1, L→h1 0.5, S→h2 0.5, L→h2 1, biases −6, −7. Output weights 1, 1, bias −2. **9 parameters** |
| Video A predictions (assumed knobs) | Ravi (4 h, 7 h) 81.8% · **Sita (6 h, 3 h) 37.8%, actually passed** · Kiran (1 h, 8 h) 37.8% |
| Video B Priya (one neuron) | w1 = 0.8 (study), w2 = 0.04 (attendance %), b = −4. Priya: 2 h study, 60% attendance, **passed**. z = 0 → 0.5 → loss 0.693. Slope for w1 = −1. **Step size 0.1** → w1 = 0.9 → z = 0.2 → 0.550 → loss 0.598 |
| Video B valley (production notes) | loss(w) = (w − 3)², start w = 0 |
| **New in Part 3** | **Arjun**: 1 h study, 50% attendance, **failed** (Day 29 learning-rate demo). Class of **60 students** (one section) for the batch arithmetic |
| Notebook dataset | 500 pretend students, 400 train (of which 80 are held out as validation) / 100 test, seed 42 |

---

## Day 29: What are epochs, batches and learning rates?

### 1. Core idea
Training a network means running the Video B loop (forward → loss → backprop → update) many times. A **batch** is the small group of training examples the network looks at before making **one** weight update. Their blame is averaged. An **epoch** is one complete pass through the **whole** training set, so one epoch contains (number of students ÷ batch size) updates. The **learning rate** is the size of each update step. Together with the number of epochs and the batch size, it is a setting **we** choose (a *hyperparameter*). The weights and biases are what the machine learns (the *parameters*).

### 2. Key points to convey
1. **Epoch = one full round through all the training data.** Keras docstring: *"An epoch is an iteration over the entire `x` and `y` data provided."* `epochs=100` means every training student is seen 100 times.
2. **Batch size = how many examples per weight update.** Keras docstring: *"batch_size: Number of samples per gradient update. If unspecified, `batch_size` will default to 32."* Google's glossary: "if the batch size is 100, then the model processes 100 examples per iteration."
3. **Iteration (step) = one update on one batch.** Steps per epoch = training examples ÷ batch size, rounded **up**. The last batch can be smaller: 60 students with batch size 32 → batches of 32 + 28. **Total updates = epochs × steps per epoch.** In Keras's output, `Epoch 7/100` counts epochs and `10/10` counts batches inside that epoch.
4. **Three flavours, one idea** (deeplearning.ai, Andrew Ng):
   - batch size = whole training set → "batch gradient descent" (1 update per epoch)
   - batch size = 1 → "stochastic gradient descent"
   - in between (16, 32, 64…) → **mini-batch gradient descent**, which is what everyone uses.

   Keras's optimizer is called `SGD`, but with `batch_size=32` it runs mini-batch gradient descent. *Guard:* "batch" in Keras's `batch_size` means the mini-batch, not the whole dataset.
5. **Why not use all students at once?** (a) With crores of examples they don't fit in memory, so batches let a GPU chew through them in pieces. (b) You get many updates per epoch instead of one, so learning starts sooner. In our notebook, full batch reached 81% test accuracy in 100 epochs while batch size 32 reached 90% (Appendix). (c) The small wobble from batches is fine; the trend is downhill. Video B already said "with mini-batches the loss wiggles."
6. **Shuffling:** Keras shuffles the training data **before every epoch** by default (`shuffle=True`). So each epoch's batches contain different mixes of students, like a teacher shuffling the answer-sheet pile each round.
7. **Learning rate = step size** (Video B). Too small: correct direction but painfully slow. Too big: overshoots the valley bottom, zigzags, or breaks the network. Google MLCC: the ideal learning rate is **problem-dependent**, so we find it by experiment. Keras defaults are 0.01 for `SGD` and 0.001 for `Adam` (verified in the source). Our notebook uses SGD with 0.1, chosen by experiment.
8. **Parameter vs hyperparameter** (a *కన్ఫ్యూజ్ అవ్వద్దు* moment from style DNA §4.2): the 9 weights/biases are **parameters**, learned by the machine. Epochs, batch size, learning rate, number of layers and number of neurons are **hyperparameters**, chosen by us before training.
9. **Too many epochs → memorising (overfitting).** Training loss keeps falling while validation loss turns back up. **Too few epochs → underfitting**: the model hasn't learned enough yet. See §5.

### 3. Depth boundary (what NOT to go into)
- **No optimiser maths:** no momentum, no Adam internals (beyond "Adam = a smarter gradient descent that adjusts its own step sizes", one line at most), no RMSprop.
- **No learning-rate schedules or decay maths.** One name-drop line is allowed: "some people make the step smaller as training goes on."
- **No GPU internals or memory arithmetic.** One line is fine: "batches also let a GPU process many students in parallel." No CUDA, VRAM or tensor cores.
- **No theory of why small batches generalise,** no "sharp vs flat minima", no convergence proofs, no "batch size should be a power of 2" rules. Say "common choices are 32, 64, 128" and nothing more.
- **No batch normalisation** (a different concept that shares the word "batch". If it comes up, say "a different topic").
- **No early-stopping or regularisation details.** Name-drop "early stopping" once in the overfitting segment, nothing more.

### 4. Fully worked toy numbers

#### (a) Batches and epochs: a class of 60 students (calculator-checkable)
| Batch size | Batches (steps) per epoch | Last batch | Updates in 5 epochs | Updates in 20 epochs | Name |
|---|---|---|---|---|---|
| 1 | 60 | 1 | 300 | 1,200 | stochastic GD |
| **10** | **6** | 10 | **30** | **120** | mini-batch (**use this one on the board**) |
| 20 | 3 | 20 | 15 | 60 | mini-batch |
| 32 (Keras default) | 2 | **28** (uneven) | 10 | 40 | mini-batch |
| 60 (whole class) | 1 | 60 | 5 | 20 | batch GD |

The rule on the board: **updates per epoch = students ÷ batch size (round up) · total updates = epochs × updates per epoch.**

Cross-check with Google MLCC's own example: 1,000 examples with batch size 100 → 10 iterations per epoch, and 20 epochs → 200 updates.

#### (b) The notebook's real numbers (Day 30 bridge)
- 400 training students; `validation_split=0.2` holds back the last 80 → **320** actually train.
- 320 ÷ 32 = **10 batches per epoch**. Keras prints `10/10` on every epoch line.
- `epochs=100` → 100 × 10 = **1,000 weight updates**. These are the "thousands of steps" from Video B.
- Homework variant: `batch_size=320` → `1/1` per epoch → only 100 updates.

#### (c) Learning rate with Priya (exact continuation of Video B)
Same neuron: w1 = 0.8, w2 = 0.04, b = −4. Priya: 2 h study, 60%, passed. Before the update: z = 0, P(pass) = 0.50, loss 0.693. Slope for w1 = (0.5 − 1) × 2 = **−1**.
Update only w1 (as in Video B): new w1 = 0.8 − (learning rate × −1) = 0.8 + learning rate.

New student for the "too big" case: **Arjun**, 1 h study, 50% attendance, **failed**. With the original knobs: z = 0.8 + 2.0 − 4 = −1.2 → 23.1% pass → correctly "fail", loss 0.263.

| Learning rate | New w1 | Priya: z → P(pass) → loss | Arjun: z → P(pass) → loss | Both students' loss together | Verdict |
|---|---|---|---|---|---|
| (before) | 0.8 | 0 → 50.0% → 0.693 | −1.2 → 23.1% → 0.263 | **0.956** | |
| **0.01** | 0.81 | 0.02 → 50.5% → **0.683** | −1.19 → 23.3% → 0.266 | 0.949 | too small: barely moved |
| **0.1** (Video B) | 0.9 | 0.2 → 55.0% → **0.598** | −1.1 → 25.0% → 0.287 | **0.885** | good: steady |
| **3** | 3.8 | 6.0 → 99.75% → 0.002 | **1.8 → 85.8% → 1.953** | **1.955** | too big: overshoot |

Story line: "With 0.01 the loss went from 0.693 to only 0.683, a crawl. With 0.1 (last video's step) it went to 0.598. With 3, Priya is fixed (99.75%), but now even **Arjun, who studied 1 hour and failed, is predicted 86% pass**. Total wrongness *doubled* (0.956 → 1.955). Too big a step fixes one student and breaks another." This is the fistful-of-salt overshoot from Video B, in numbers.

Optional pro-tip (pays off Video B's footnote): with the raw 60% scale, w2's slope is (0.5 − 1) × 60 = **−30**. Step 0.1 throws w2 from 0.04 to **3.04**, and then Arjun's z = 0.8 + 3.04 × 50 − 4 = **148.8**, which is nonsense. That's why we scale inputs (60% → 0.6, hours ÷ 10).

#### (d) The valley picture: loss(w) = (w − 3)², start at w = 0 (best w = 3)
Update: new w = w − learning rate × 2(w − 3). The first step's slope at w = 0 is −6.

| Learning rate | w after steps 1 → 6 | Loss after 6 steps | Behaviour |
|---|---|---|---|
| 0.01 | 0.06, 0.12, 0.18, 0.23, 0.29, 0.34 | 7.06 | **too small**: barely moving (started at 9) |
| 0.25 | 1.5, 2.25, 2.625, 2.81, 2.91, 2.95 | 0.002 | **good**: smooth arrival |
| 1.0 | 6, 0, 6, 0, 6, 0 | 9.0 | **too big**: bounces wall to wall forever |
| 1.1 | 6.6, −1.32, 8.18, −3.22, 10.47, −5.96 | 80.2 | **way too big**: jumps out, explodes |

Note: lr 0.5 lands on w = 3 in one step for this particular valley. Don't show it; it suggests a "magic" value exists in general.

#### (e) Real Keras runs (from the notebook; same 9-knob network, same data, same seed 42, SGD, 100 epochs, batch 32)
| Learning rate | Training loss, epoch 1 → 100 | Test accuracy | What happened |
|---|---|---|---|
| **0.001** | 0.577 → 0.504 | 68% | Too small. Barely learned, and it predicts **PASS for all 100 test students** (68 of them really passed, so it scores 68% while knowing nothing) |
| **0.1** | 0.532 → **0.193** | **90%** | About right |
| **20.0** | **3.921** → 1.465, zigzagging: 3.92, 1.43, 1.70, 0.85, 2.11, 0.85, 1.80 … | 68% | Too big. Loss never settles, and the network ends up saying 96% PASS for everyone |

Extra runs for Deepak's own understanding (not in the notebook): lr 1.0 and 2.0 still reached 90%. lr 3.0, 5.0 and 10.0 "broke" the network: the loss froze at a constant (0.645 / 0.669 / 0.926) with the same prediction for every student. **Teaching point: the "right" learning rate is a range, found by trying.** On this tiny problem the range is roughly 0.1–2. On another problem it will be different (Google MLCC: problem-dependent).

#### (f) Epochs: real numbers (main notebook model, SGD 0.1, batch 32)
| After epoch | Training loss | Training accuracy | Validation loss |
|---|---|---|---|
| 1 | 0.532 | 70% | 0.439 |
| 10 | 0.401 | 82% | 0.319 |
| 50 | 0.229 | 91% | 0.178 |
| 100 | 0.193 | 93% | 0.159 |

Re-trained from scratch with fewer epochs (test accuracy): **5 epochs → 68%** (still the lazy "everyone passes" answer, so *underfitting*) · **20 epochs → 88%** · **100 epochs → 90%**.

### 5. Overfitting tie-in: too many epochs = బట్టీ (memorising)
- **Callback:** earlier episodes taught training vs testing. Video A said bigger networks "can mug up the training data and then fail on the testing data." Video B said "loss 0 on training doesn't mean a perfect model." Day 29 shows it happening.
- **Mechanism, in plain words:** each epoch the network sees the same students again. Early epochs learn the general pattern ("more study → more likely to pass"). If you keep going with a model that has lots of knobs and too little data, it starts fitting each student's *luck* too: "this exact student with 4.4 h passed, that one with 4.5 h failed." That is memorising the answer key, బట్టీ. New students don't share that luck, so it gets *worse* on them.
- **How we catch it: the validation set = a mock test.** Keep some training students aside (`validation_split=0.2`). The model never learns from them, and we check its loss on them after every epoch. Google MLCC: overfitting shows up as training and validation loss curves that **diverge**, with training loss still going down while validation loss starts going **up**.
- **Validation vs test (keep it simple):** validation = the mock test we check *during* preparation, to decide how many epochs and which learning rate. Test = the final exam, used **once** at the end. If you keep tuning on the test set, it stops being an honest exam.
- **Real numbers (notebook Experiment 2):** a big network (two hidden layers of 64 → **4,417 knobs**), only **30 students** to learn from, Adam lr 0.01, **500 epochs**, checked on 80 other students:

  | Epoch | 10 | **35 (best)** | 100 | 200 | 300 | 500 |
  |---|---|---|---|---|---|---|
  | Training loss (30 students) | 0.390 | – | 0.193 | 0.144 | 0.031 | **0.0006** |
  | Validation loss (80 new students) | 0.320 | **0.185** | 0.198 | 0.233 | 0.405 | **0.903** |

  At epoch 500, training accuracy is **100%** with loss ≈ 0 (fully memorised), while validation loss is **~5× worse** than at epoch 35 (0.903 vs 0.185). The training-loss value at epoch 35 isn't recorded in the log, hence "–".
- **What people do (name-drop only):** watch the validation curve and stop near the best epoch. Keras has a ready-made helper for this, called *early stopping*. More data and smaller models also help.
- **Contrast with our 9-knob model:** its validation loss kept going down for all 100 epochs (0.439 → 0.159). With only 9 knobs and 320 students, there isn't room to memorise. Overfitting is about **too many knobs + too little data + too many epochs together**, not epochs alone.

### 6. Indian everyday analogies (most accurate flagged ★)

**Epochs**
| Analogy | Mapping | Accuracy / how it misleads |
|---|---|---|
| ★ **Revising the full syllabus again and again before exams** (1st revision, 2nd revision, 3rd…) | One revision of the *whole* syllabus = one epoch; more revisions = more epochs | **Most accurate.** Risk: suggests more revisions are always better. Fix it with the next analogy |
| **Practising the same previous-year question papers over and over** | Same examples each epoch; after too many rounds you remember *those answers*, not the concept, so a new paper floors you | Excellent for **overfitting** (బట్టీ). Risk: real training also shuffles the order each round, and an epoch covers *all* papers, not one |
| **Cricket nets: facing the same bowler's six balls daily** | Repetition improves you, but only against that bowler | Good for "learn patterns vs memorise one source". Weaker on the "full pass over all data" definition |

**Batches**
| Analogy | Mapping | Accuracy / how it misleads |
|---|---|---|
| ★ **A teacher correcting answer sheets in bundles**: she corrects a bundle of 10 sheets, notes the *common* mistakes, adjusts her next lesson a little, then takes the next bundle | Bundle = batch. "Adjust after each bundle, based on the bundle's average mistakes" = one update per batch. Whole pile once = one epoch | **Most accurate**: it captures "update after each batch, using the average". Risk: a teacher adjusts *teaching*, while the network adjusts *weights*. Also, in training the same sheets come back every epoch (shuffled) |
| **Pressure cooker for 60 guests**: you can't cook all the rice at once, so you cook 3 batches of 20 | Memory limit → batches | Accurate for *why* batches exist (memory). **Misleads** on the key point: cooking batches are independent, but in training **each batch changes the weights before the next batch** |
| **Hostel mess serving in rounds (pankti)** | The group is served in rounds; everyone is served by the end (one epoch) | OK for "groups until everyone is covered". Says nothing about updating. Use as a one-liner only |

**Learning rate**
| Analogy | Mapping | Accuracy / how it misleads |
|---|---|---|
| ★ **Walking down Ananthagiri Hills in fog (from Video B)**: tiny steps take all night, giant leaps make you overshoot the valley and land on the opposite slope | Step size = learning rate; overshoot/bounce = too big | **Most accurate**, and continues Video B. Risk (already stated in Video B): real loss valleys have many dips |
| **Amma adding salt (from Video B)**: one grain at a time = too slow; a fistful = spoiled | Small vs big correction | Relatable continuity. **Misleads:** she changes one ingredient, you can't remove salt, and she judges by feel. Gradient descent changes all knobs, can move both ways, and computes the slope |
| **Learning to ride a cycle**: jerk the handle hard at every wobble and you zigzag across the road; correct too gently and you drift into the gutter | Overcorrection → zigzag. That is exactly the lr = 20 curve | Very good visual for the **zigzag** in the real plot. Risk: steering is continuous feel-based feedback, not computed slopes |

### 7. Whiteboard drawings (step by step)
**Board 1: epoch and batch, with 60 students**
1. Draw a grid of 60 small stick-figure dots labelled "Training data = 60 students".
2. Draw boxes around groups of 10 → 6 boxes, labelled "Batch 1 … Batch 6 (batch size = 10)".
3. Under each box, draw a small spanner icon: "update the 9 knobs" (6 spanners).
4. Draw a big loop arrow around all 6 boxes: "**1 epoch** = all 60 students once = **6 updates**".
5. Draw it as a ladder: "Epoch 1, Epoch 2, … Epoch 5" → "5 × 6 = **30 updates**".
6. Side table: batch size 1 / 10 / 60 → updates per epoch 60 / 6 / 1.
7. Redraw the Video B K1 loop (forward → loss → backprop → update) and write next to it: "this loop runs once per **batch**".

**Board 2: learning rate, the valley**
1. Reuse Video B's U-shaped valley ("loss vs weight", ⭐ at the bottom, w = 3).
2. Green: tiny dots creeping from w = 0 (lr 0.01: "0.06, 0.12, … still far").
3. Blue: neat hops into the ⭐ (lr 0.25: 1.5 → 2.25 → 2.6 → ⭐).
4. Red: a ball pinging wall to wall 0 ↔ 6 (lr 1.0: "bounces forever").
5. Red dashed: a ball jumping out of the valley (lr 1.1: "explodes").
6. Side box: the Priya/Arjun table. Circle "Arjun 23% → 86% ✗".

**Board 3: overfitting**
1. Axes "epochs →" and "loss ↓".
2. Blue curve "training loss": goes down and keeps going down to almost 0.
3. Orange curve "validation loss (mock test)": goes down, reaches a lowest point, then curves **up**.
4. A vertical dashed line at the lowest point: "best epoch, stop here".
5. Left region label: "learning ✅". Right region label: "బట్టీ / memorising ❌".
6. Then show the real Colab plot (Experiment 2) side by side: "best epoch = 35".

### 8. Common misconceptions to pre-empt
- **"More epochs is always better."** Only up to a point. After that, validation loss rises (overfitting). Too few epochs is also bad (underfitting: 5 epochs gave 68% in our run).
- **"Batch = epoch."** No. A batch is a *slice* of the data, giving one update. An epoch is *all* the data once, giving many updates.
- **"Iteration = epoch."** In Keras's output, `10/10` counts batches (iterations) and `Epoch 7/100` counts epochs.
- **"Learning rate = how fast the computer runs."** No. It's the **size of each weight change**. A bigger learning rate doesn't make the computer faster, and it can make learning *fail* (lr 20 → loss zigzag, 68%).
- **"A bigger learning rate always learns faster."** Only until it overshoots (Arjun 23% → 86%; valley lr 1.1 explodes).
- **"Bigger batch = more learning."** A bigger batch means *fewer* updates per epoch. Full batch gave 100 updates and 81% test accuracy, while batch size 32 gave 1,000 updates and 90% (same 100 epochs).
- **"Epochs, batch size and learning rate are learned by the network."** No. They are **hyperparameters** we choose. Only weights and biases (parameters) are learned.
- **"Validation data = test data."** Validation is the mock test used while choosing settings; test is the final exam, used once.
- **"68% accuracy means it learned something."** Check what it predicts. Our broken models said PASS for every student and still scored 68%, because 68 of the 100 test students passed.

### 9. Comment-quiz question
"A class has **60 students**. We train with **batch size 20** for **10 epochs**. How many times do the weights get updated? And if the validation loss starts going **up** after epoch 6 while the training loss keeps going down, what is happening?"
Answer: 60 ÷ 20 = 3 updates per epoch × 10 = **30 updates**. It is **overfitting** (memorising, బట్టీ), so stop around epoch 6.

Alternative, calculator-checkable: "Priya's w1 = 0.8, slope = −1. Learning rate 0.5: what's the new w1?" (0.8 − 0.5 × −1 = **1.3**.)

---

## Day 30: Build a neural network (Keras in Google Colab)

### 1. Core idea
A deep-learning library like **Keras** lets us build the exact network we drew in about five lines. We stack `Dense` layers (the circles and lines), choose ReLU/sigmoid, and call `compile` to choose the loss, the gradient-descent version and the learning rate. Then one call to `fit` runs the whole Video B loop (forward → loss → backprop → update) for every batch and every epoch, computing all the slopes automatically. We then `evaluate` on unseen test students and `predict` for Sita. Every line maps to something already taught. Nothing new is happening, it is just automated.

### 2. Key points to convey
1. **Keras = the ready-made toolkit; TensorFlow = the engine underneath.** On Colab, `import keras` gives Keras 3 running on TensorFlow. (Keras 3 can also run on JAX or PyTorch. Name-drop at most.)
2. **The 9-knob aha:** `model.summary()` prints **hidden_layer: 6, output_layer: 3, Trainable params: 9**. This is the same count as Video A (4 weights + 2 biases + 2 weights + 1 bias). It also prints "(36.00 B)": 9 numbers × 4 bytes = 36 bytes. Optional size contrast: GPT-3's 175 billion parameters at the same 4 bytes each is about 700 GB (175e9 × 4 = 7 × 10¹¹ bytes).
3. **`fit` = the loop.** Backprop and the slopes are computed automatically (what Video B did by hand for Sita). Our job is to choose `epochs`, `batch_size` and the learning rate.
4. **The trained network fixes Video A's mistake.** Learned knobs give **Sita 95% → PASS**. She actually passed, and our guessed knobs had said 38%.
5. **We check on unseen data.** Test accuracy is **90%** on 100 students the model never saw. That's also the ceiling for this data: the hidden rule *without* the luck term scores exactly 90% on the same test students.
6. **Bigger isn't automatically better.** A 193-knob network also got 90% (loss 0.203 vs 0.199). For simple tabular data, small is enough. This echoes Video A's "DL isn't always the best tool for small tables."
7. **Results vary slightly from run to run.** Seeds are fixed, but hardware and library versions differ.

### 3. Depth boundary (what NOT to go into)
- **No line-by-line syntax:** no Python lessons (dicts, f-strings, `np.column_stack`, slicing), and no explaining `keras.Input(shape=(2,))` beyond "2 inputs".
- **No tensors, shapes or `(None, 2)` explanations.** If asked: "None = any number of students". One line.
- **No Sequential vs Functional API, no `tf.data`, no callbacks code, no model saving/loading, no GPU setup** (the notebook runs on CPU in ~80 s; say "no GPU needed").
- **No Adam internals** ("smarter gradient descent" only), and no initialisers or regularisers.
- **No metrics beyond accuracy** (precision/recall are still an open promise from Day 6; don't open them here).
- **Don't read the 2×2 weight matrix.** Show the labelled 9-knob printout (Block 9b) and say "these are the 9 knobs the machine found."

### 4. Block-by-block conceptual walkthrough of the notebook
Use these exact block titles on screen; they match the notebook's markdown headings. The script needs about **7 spoken blocks**. Blocks 1–3 can be grouped as "data", and the two experiments come after.

| # | Notebook block | Say this (concept, not syntax) | Callback | Real output to show |
|---|---|---|---|---|
| 1 | **Get our tools ready** | "numpy = calculator, matplotlib = graphs, keras = the neural-network toolkit." | — | `Keras version: 3.15.1` (Colab may show a different 3.x) |
| 2 | **Make our class data (features + label)** | "500 pretend students. Study and sleep are the **features**; Pass/Fail is the **label**, the answer key. We create it with a hidden rule plus luck, but the network only sees examples, never the rule." | Day 3 features/label; Day 5 supervised | First rows: 7.7 h/8.2 h Pass · 4.4/9.2 Pass · 8.6/9.4 Pass · 7.0/6.5 Pass · 0.9/6.6 Fail. **347 of 500 passed (69%)** |
| 3 | **Training data vs testing data** | "400 to learn from, 100 locked away for the final exam. And hours ÷ 10, like 60% → 0.6." | Training vs testing (earlier videos); Video B footnote | `Training students: 400`, `Testing students: 100` |
| 4 | **Build the network we drew** | "This block **is** the drawing: 2 inputs → `Dense(2, relu)` = the 2 hidden circles → `Dense(1, sigmoid)` = the output circle. Dense = fully connected, every line drawn." | Video A board; Video B ReLU/sigmoid | Summary: **6 + 3 = Trainable params: 9 (36.00 B)** ← the aha |
| 5 | **Compile (choose the loss, the gradient-descent version and the learning rate)** | "We tell it *how* to learn: loss = log loss (Video B), optimizer = SGD = gradient descent, learning rate = 0.1 = the same step as Priya. Accuracy is just for us to read." | Video B loss + GD; "train on loss, report accuracy" | (no output) |
| 6 | **Fit (the training loop: epochs and batches)** | "`model.fit` = the Video B loop. 320 students ÷ 32 = 10 batches per epoch (see `10/10`), × 100 epochs = 1,000 updates. Backprop is done for us." | Video B K1 loop; Day 29 numbers | Epoch 1: loss 0.532, acc 70% → Epoch 100: loss 0.193, acc 93%, val_loss 0.159 |
| 7 | **Look at the loss curves** | "Both curves go down together, so it's genuinely learning, not memorising." | Day 29 overfitting board | Plot: training 0.53 → 0.19, validation 0.44 → 0.16, both smooth and falling |
| 8 | **Final exam (evaluate on the test data)** | "100 students it has never seen. This is the honest score." | Training vs testing | **Test loss 0.199 · Test accuracy 90%** |
| 9 | **Predict for Sita, Ravi and Kiran** | "Remember our guessed knobs said Sita 38%? The learned knobs say…" | Video A Sita twist | **Sita 95% PASS** · Ravi 87% PASS · Kiran 13% FAIL. "Try yourself" default (5 h, 7 h) → 96% |
| 9b | (same block) **The 9 knobs the machine found by itself** | "The same 9 slots as our drawing, now filled by gradient descent instead of by me." | Video A 9 knobs; Video B "where do weights come from?" | study→h1 3.58, sleep→h1 1.07, h1 bias −1.06 · study→h2 0.45, sleep→h2 1.08, h2 bias −0.05 · h1→out 3.93, h2→out −0.14, out bias −2.40 |
| E1 | **Experiment 1: Learning rate too small, about right, too big** | "Same everything, only the step size changes." | Day 29 valley | 0.001 → 0.504 loss, 68% · **0.1 → 0.193, 90%** · 20.0 → loss starts at 3.921, zigzags, 68% |
| E2 | **Experiment 2: Too many epochs, and memorising instead of learning (overfitting)** | "Big network, only 30 students, 500 epochs. Watch the orange curve turn up." | Day 29 overfitting; Video A "mug up" line | 4,417 knobs · best validation loss 0.185 at epoch 35 · at 500: training loss 0.0006 (100% train acc), validation loss 0.903 |
| Opt | **Optional: a slightly bigger network** | "193 knobs vs 9: does it win?" | Video A "more layers isn't always better" | Bigger: 193 knobs, 90%, loss 0.203 · ours: 9 knobs, 90%, loss 0.199 |

**Two "aha" beats worth slowing down for:**
1. **Block 4:** circle "Trainable params: 9" on screen next to the Video A drawing with its 9 knobs labelled.
2. **Block 9:** put Video A's Sita card (38% ✗) next to the new output (95% ✓). Line: "We didn't change Sita. We changed the knobs, and the machine found them from 320 students' data." Optional calculator moment: plugging Sita into the 9 learned knobs gives h1 = 1.404, h2 = 0.543, z = 3.051 → σ = 0.955, exactly what `predict` printed. "predict = the same forward pass we did by hand in Video A."

**Interpretation note (optional, careful):** the learned h1 neuron weights study about 3.4× more than sleep per hour (0.358 vs 0.107 per raw hour). The hidden rule used 7 vs 3 (2.3×). Say only "the network learned that study counts more than sleep for this data." Don't claim it recovered the exact rule. h2's output weight is tiny (−0.14), so most of the work is done by h1, a reminder that hidden neurons don't come with neat human meanings (Video A caveat).

### 5. Indian analogies for Day 30
| Analogy | Mapping | Accuracy / how it misleads |
|---|---|---|
| ★ **Ready-made masala packet vs grinding masala at home**: Video B was grinding by hand (computing Sita's blame ourselves). Keras is the packet: same spices, same taste, much faster | Keras automates the exact steps we did by hand | **Most accurate** for "nothing new, just automated." Risk: implies you no longer need to understand the spices. Counter: "you still choose how much (epochs, batch size, learning rate)" |
| **Building a house with ready bricks**: Dense layers are bricks; you decide how many floors (layers) and rooms (neurons) | Stacking layers | Good for `Sequential([...])`. Risk: bricks are fixed, but layer weights change during training |
| **Mock tests vs board exam**: validation = weekly mock tests at coaching; test = the board exam | validation_split vs test set | Accurate and very Indian. Risk: in Keras the "mock test" doesn't change the knobs; it only reports |

### 6. Whiteboard / screen layout for the build
1. Split screen: **left** = Video A's network drawing (S, L → h1, h2 → output, 9 knobs labelled); **right** = Colab.
2. As each block runs, draw a coloured arrow from the code block to the matching part of the drawing: data → the input arrows; `Dense(2, relu)` → the hidden circles; `Dense(1, sigmoid)` → the output circle; `compile` → a sticky note "loss + GD + step 0.1"; `fit` → the K1 loop (circled "repeat ↺ 1,000 times").
3. After `summary`: write "**9 = 9** ✔" big between the drawing and the output.
4. After predict: replace Sita's old card "38% ✗" with "95% ✓ (learned)".
5. For the experiments, show the two plots full screen with hand annotations ("zigzag = too big a step", "best epoch = 35", "బట్టీ zone").

### 7. Common misconceptions (Day 30)
- **"model.fit is some new magic, different from what we learned."** It *is* the forward → loss → backprop → update loop, run per batch and per epoch.
- **"You need a GPU / a powerful laptop."** This notebook runs on a plain CPU: 78–81 s measured on a 4-core machine, so budget 1–3 minutes on Colab's free CPU runtime **[verify on Colab]**.
- **"100% training accuracy = a great model."** Experiment 2 got 100% on training and got worse on new students.
- **"Bigger network = better."** 193 knobs = 90%, the same as 9 knobs.
- **"The model learned the rule we wrote."** It never saw the rule, only examples, and its knobs are not the rule's numbers.
- **"Keras and TensorFlow are competitors."** Keras is the easy front end; TensorFlow (or JAX/PyTorch) runs the maths underneath.
- **"Same code → exactly the same numbers everywhere."** Small differences across machines are normal.
- **"I can feed raw hours at predict time."** You must apply the same ÷ 10 as in training. The notebook does this inside the predict cell.

### 8. Comment-quiz question (Day 30)
"In our notebook, `model.summary()` showed **Trainable params: 9**. If we change the hidden layer to **`Dense(3, relu)`** (3 hidden neurons instead of 2), how many trainable parameters will it show? Run it in Colab and comment!"
Answer: hidden 2 × 3 weights + 3 biases = 9, output 3 weights + 1 bias = 4 → **13**.

Homework (already in the notebook's last cell; answers from our runs):
1. `epochs=5` → test accuracy **68%**: it predicts PASS for everyone, so it hasn't learned yet (underfitting).
2. `batch_size=320` → the output shows **`1/1`** each epoch (1 update per epoch). Test accuracy drops to **81%** after 100 epochs, because there are only 100 updates.
3. `learning_rate=1.0` → still fine on this data: **90%**.

### 9. Real results (seed 42; Python 3.13, TensorFlow 2.21.0, Keras 3.15.1, CPU)
All cells run end to end with no errors, in about 80 s. Two separate full runs gave identical numbers (timings excluded).

```
Keras version: 3.15.1
First 5 students:  7.7 8.2 Pass | 4.4 9.2 Pass | 8.6 9.4 Pass | 7.0 6.5 Pass | 0.9 6.6 Fail
Total students: 500, passed: 347 (69%)        Training students: 400   Testing students: 100
model.summary(): hidden_layer (Dense) (None, 2) 6 | output_layer (Dense) (None, 1) 3
                 Total params: 9 (36.00 B)  Trainable params: 9 (36.00 B)  Non-trainable params: 0
fit (verbose=2), every line starts "10/10":
  Epoch 1   accuracy 0.7031  loss 0.5319  val_accuracy 0.7750  val_loss 0.4389
  Epoch 10  accuracy 0.8219  loss 0.4006  val_accuracy 0.9000  val_loss 0.3188
  Epoch 50  accuracy 0.9125  loss 0.2287  val_accuracy 0.9500  val_loss 0.1784
  Epoch 100 accuracy 0.9250  loss 0.1926  val_accuracy 0.9375  val_loss 0.1589
Test loss 0.199 · Test accuracy 90%
Sita  (6 h, 3 h) -> 95% PASS   Ravi (4 h, 7 h) -> 87% PASS   Kiran (1 h, 8 h) -> 13% FAIL   You (5 h, 7 h) -> 96%
Learned knobs: study->h1 3.58  sleep->h1 1.07  h1 bias -1.06 | study->h2 0.45  sleep->h2 1.08  h2 bias -0.05
               h1->output 3.93  h2->output -0.14  output bias -2.40
Experiment 1: lr 0.001: loss 0.577 -> 0.504, test 68% | lr 0.1: 0.532 -> 0.193, 90% | lr 20.0: 3.921 -> 1.465, 68%
Experiment 2: big model 4417 knobs; best val loss 0.185 at epoch 35; after 500 epochs train loss 0.0006 (100%), val loss 0.903
Optional:     bigger network 193 knobs, test 90%, loss 0.203  vs  9 knobs, test 90%, loss 0.199
```

### 10. "Your numbers will differ slightly": the evidence and what to say
- **Seed sweep (main model, seeds 0–9):** 9 of 10 seeds gave test accuracy **90–91%** (loss 0.196–0.226), Sita 93–95%, Ravi 77–84%, Kiran 7–12%. Seed 42 (the notebook's) gave Ravi 87% and Kiran 13%, which is slightly outside the 0–9 range but in the same story.
- **1 in 10 seeds (seed 8) got stuck:** every student got 68%, and test accuracy was 68%. The tiny network's two ReLU neurons started "switched off" for everyone, so no blame flowed back (Video B: an off neuron gets zero blame). The same thing happened once with Adam (lr 0.05, seed 0). The notebook's closing note tells viewers to change the seed (e.g. 42 → 7, which works) and re-run. This is a *real* teaching moment: it links straight to Sita's h2 getting zero blame.
- **Suggested line:** "Your numbers may come out a little different: 89% or 91% instead of 90%, Sita 93% instead of 95%. That's normal. Training starts from random knobs and shuffles students every epoch. On Colab's GPU the decimals can also change. The story stays the same."
- **Why validation loss can be lower than training loss** (it is, in Block 7), in case a viewer asks: the 80 mock-test students happen to be a little easier, and Keras reports training loss as an average *during* the epoch while the knobs are still improving, whereas validation is measured at the end of the epoch. **[verify]** the second reason against the Keras FAQ: https://keras.io/getting_started/faq/

### 11. Technical gotchas found while testing (for the production team)
1. **`learning_rate` must be a float in Keras 3.15.** `SGD(learning_rate=10)` raises `ValueError: Argument learning_rate should be float…`. Write `10.0`. The notebook says so.
2. **`validation_split` takes the *last* 20% of the data, before shuffling** (Keras docstring). Fine here, because our data is randomly generated. With a sorted CSV (all passes first) the mock test would be all one class.
3. **Scaling must match at prediction time** (÷ 10). Forgetting it would feed "60 hours" to the network.
4. **Colab versions:** written for TensorFlow 2.x + Keras 3 via `import keras`, using only stable APIs (`keras.Sequential`, `keras.Input`, `keras.layers.Dense`, `keras.optimizers.SGD/Adam`, `keras.utils.set_random_seed`, `get_layer().get_weights()`, `count_params()`). TF ≥ 2.16 ships Keras 3 as the default. **[verify]** the exact versions on the day of recording by running Block 1 in Colab. The summary table layout may look slightly different on other versions; the "9" will not change.
5. Timing: ~78–81 s total on a 4-core CPU. The slowest cells are Experiment 1 (3 × 100 epochs) and Experiment 2 (500 epochs).

---

## Suggested flow for the Part 3 episode (for the scriptwriter; adjust freely)
1. Recap: redraw the Video B loop and circle "repeat ↺". Answer the three outro questions in order.
2. **Concept 1, Epoch** (class of 60, revision analogy) → **Concept 2, Batch** (answer-sheet bundles, 6 updates/epoch) → **Concept 3, Learning rate** (valley + Priya/Arjun table).
3. Parameter vs hyperparameter guard. Then **overfitting** (బట్టీ board).
4. Mid-roll around 35–45%, likely during the learning-rate or overfitting segment.
5. **Build:** Blocks 1–3 (data) → 4 (the 9 aha) → 5 → 6 → 7 → 8 → 9 (Sita 95%) → Experiments 1 and 2 as proof of the Day 29 theory.
6. Quiz + homework (the three notebook homework questions) + the "numbers may differ" note + tease for Part 4 (how AI sees images).

---

## Sources
Keras (checked against the installed Keras 3.15.1 source and docstrings; the keras.io pages were not fetchable in this session):
- Keras Model training APIs (`compile`, `fit`, `evaluate`, `predict`; `batch_size` default 32; epoch definition; `validation_split` "selected from the last samples… before shuffling"; `shuffle` before each epoch). https://keras.io/api/models/model_training_apis/
- Keras SGD optimizer (default learning_rate 0.01). https://keras.io/api/optimizers/sgd/ · Adam (default 0.001). https://keras.io/api/optimizers/adam/
- Keras Dense layer. https://keras.io/api/layers/core_layers/dense/
- Keras FAQ (training vs validation loss reporting). https://keras.io/getting_started/faq/ **[verify]**
- Keras 3 README ("drop-in replacement for tf.keras" with the TensorFlow backend; multi-backend). https://github.com/keras-team/keras
- TensorFlow 2.16 release blog: Keras 3 becomes the default. https://blog.tensorflow.org/2024/03/whats-new-in-tensorflow-216.html

Google Machine Learning Crash Course / Glossary (via search extracts; page fetch blocked):
- Linear regression: Hyperparameters (learning rate, batch size, epochs; 1,000 examples / batch 100 → 10 iterations per epoch; 20 epochs → 200 updates; ideal learning rate is problem-dependent). https://developers.google.com/machine-learning/crash-course/linear-regression/hyperparameters **[verify exact wording]**
- Overfitting: Interpreting loss curves (training and validation loss diverge; validation loss rises). https://developers.google.com/machine-learning/crash-course/overfitting/interpreting-loss-curves
- Generalization / Peril of overfitting. https://developers.google.com/machine-learning/crash-course/generalization/peril-of-overfitting
- ML Glossary: Fundamentals (batch, batch size, epoch, iteration, full batch, mini-batch). https://developers.google.com/machine-learning/glossary/fundamentals

deeplearning.ai (Andrew Ng, *Improving Deep Neural Networks*; via search extracts):
- Mini-batch gradient descent (one epoch = one pass through the training set; batch size M = batch GD; size 1 = stochastic GD). https://learn.deeplearning.ai/courses/deep-neural-network/lesson/gvh26/mini-batch-gradient-descent
- Understanding mini-batch gradient descent. https://learn.deeplearning.ai/courses/deep-neural-network/lesson/vxgiv/understanding-mini-batch-gradient-descent

Continuity sources (this repo): `research/dl-content-research.md`, `scripts/video-A-inside-a-neural-network/script-english.md`, `scripts/video-B-how-a-neural-network-learns/script-english.md`, `scripts/video-B-how-a-neural-network-learns/production-notes.md` §6, `research/style-dna-report.md` §3.6 and §4.

---

## Appendix: arithmetic and run logs (Python 3.13; natural log; σ(z) = 1/(1+e^−z))

```
Batches (N = 60): bs 1 -> 60/epoch | bs 10 -> 6 (5 ep = 30, 20 ep = 120) | bs 20 -> 3 | bs 32 -> 2 (last batch 28) | bs 60 -> 1
Notebook: 320 train / 32 = 10 steps/epoch x 100 epochs = 1000 updates.  MLCC check: 1000/100 = 10 x 20 = 200
Priya (w1 .8, w2 .04, b -4; 2 h, 60%, y=1): z=0, p=.5, loss .6931, slopes w1 -1.0, w2 -30.0, b -0.5
Arjun (1 h, 50%, y=0): z=-1.2, p(pass)=.2315, loss .2633
  lr .001: w1 .801  Priya p .5005 loss .692 | Arjun p .2317 loss .264 | pair .956
  lr .01 : w1 .81   Priya p .5050 loss .683 | Arjun p .2333 loss .266 | pair .949
  lr .1  : w1 .9    Priya p .5498 loss .598 | Arjun p .2497 loss .287 | pair .885
  lr 1   : w1 1.8   Priya p .8808 loss .127 | Arjun p .4502 loss .598 | pair .725
  lr 3   : w1 3.8   Priya p .9975 loss .002 | Arjun z 1.8 p .8581 loss 1.953 | pair 1.955   (before: .956)
  lr 5   : w1 5.8   Priya p 1.000 loss .000 | Arjun z 3.8 p .9781 loss 3.822
  raw-scale w2 with lr .1: 0.04 -> 3.04 ; Arjun z = 148.8
Valley (w-3)^2 from 0: lr .01 -> .06,.1188,.1764,.2329,.2882,.3425 (loss 7.06) | lr .1 -> .6,1.08,1.464,1.771,2.017,2.214
  lr .25 -> 1.5,2.25,2.625,2.8125,2.906,2.953 (loss .0022) | lr .5 -> 3 (one step) | lr 1 -> 6,0,6,0,6,0 | lr 1.1 -> 6.6,-1.32,8.184,-3.221,10.465,-5.958 (loss 80.2)
Dataset (seed 42): 347/500 pass (69.4%); train 279/400 (69.75%); test 68/100; hidden rule w/o luck on test = 90%
Keras SGD lr sweep (seed 42, 100 ep, bs 32; test acc): 0.0001 .81 | 0.001 .68 | 0.01 .80 | 0.1 .90 | 0.5 .90 | 1.0 .90 | 2.0 .90 | 3.0 .68 (stuck .645) | 5.0 .68 (stuck .669) | 10.0 .68 (stuck .926) | 20.0 .68 (zigzag) | 50.0 .32
  lr 20 per-epoch loss: 3.921 1.428 1.696 0.849 2.110 0.845 1.803 1.650 0.878 1.486 0.870 1.515 ...
  models at 68% (lr .001, lr 20, 5 epochs) all predict PASS for 100/100 test students
Epoch/batch variants (seed 42, SGD .1; test acc): 5 ep .68 | 20 ep .88 | 100 ep .90 | 100 ep bs 320 .81 | 100 ep bs 1 .91 | lr 1.0 .90
Seed sweep 0-9 (main model): acc .90/.90/.90/.90/.91/.90/.90/.90/.68(stuck)/.90 ; Sita .93-.95, Ravi .77-.84, Kiran .07-.12 (excluding seed 8)
Learned knobs (full precision): s->h1 3.5787, s->h2 0.4534, l->h1 1.0670, l->h2 1.0755, b1 -1.0631, b2 -0.0519, h1->out 3.9318, h2->out -0.1368, c -2.3955
  hand forward pass: Sita h1 1.404 h2 0.543 z 3.051 p .9548 | Ravi z 1.869 p .8663 | Kiran z -1.929 p .1269  (matches model.predict)
Overfit demo (64-64, 4417 params, 30 students, Adam .01, 500 ep): val loss @10 .320 @35 .185(best) @100 .198 @200 .233 @300 .405 @500 .903 ;
  train loss @10 .390 @100 .193 @200 .144 @300 .031 @500 .0006 ; train acc 100% ; val acc at best .913, at 500 .900
  (32-32 variant, 1185 params, 1000 ep: best val .191 at ep 63 -> .987 at end)
Bigger optional model (16-8): 193 params; test acc .90, loss .203
Sizes: 9 params x 4 B = 36 B ; GPT-3 175e9 x 4 B = 700 GB
```
