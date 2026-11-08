# Deep Learning Foundations — Content Research Brief (Days 21–28)

_For Tech Boy Deepak's Telugu "AI Learning Series". Prepared 8 Nov 2026._

- **Video A — "Inside a Neural Network"**: Day 21 (What is DL), Day 22 (artificial neuron), Day 23 (layers), Day 24 (weights & biases)
- **Video B — "How a Neural Network Learns"**: Day 25 (activation functions), Day 26 (loss), Day 27 (gradient descent), Day 28 (backpropagation)

**Audience level:** a college student with no maths background. Teach with drawings first, numbers second, formulas last or not at all. Nothing below is simplified to the point of being wrong. Where a simplification is used, it is flagged.

**Research note:** In this session the web *search* tool worked, but direct page fetches to developers.google.com, cs231n.github.io and 3blue1brown.com were blocked by the session's network settings. So the facts from those references were checked against search-result extracts and the standard textbook content, not by reading the pages in full. Items marked **[verify]** should be re-checked against the linked page before filming. All arithmetic was checked with a Python script (results reproduced below).

---

## 0. The running example (reuse from Day 7, so viewers feel continuity)

In Day 7, Deepak already did this on screen (logistic regression, "Student D"):

| | value |
|---|---|
| x1 = study hours | 4 |
| x2 = attendance % | 80 |
| w1 (assumed) | 0.8 |
| w2 (assumed) | 0.04 |
| b (bias, assumed) | −4 |
| z = 0.8×4 + 0.04×80 − 4 | 3.2 + 3.2 − 4 = **2.4** |
| σ(2.4) = 1 / (1 + e^−2.4) = 1 / (1 + 0.0907) | **0.917 → 91.7% pass** |
| threshold 50% → | **Pass** |

**The big reveal for Video A:** *"Remember Student D from Day 7? That calculation was already one artificial neuron. Logistic regression is a neural network with exactly one neuron."* Everything in Days 21–28 builds on this.

**Small Day 7 fixes to make while recapping.** They matter because DL builds on the sigmoid.
1. The sigmoid output is a **probability between 0 and 1** (e.g. 0.917). The **threshold** then turns it into a class, 0 or 1. The output isn't "always 0 or 1". The *final decision* is 0/1, but the sigmoid output is not.
2. e ≈ **2.718** (one slip in Day 7 said 2.717).
3. Write the formula with brackets, σ(z) = 1 / (1 + e^(−z)). Without them it reads as "1/1 + …".

**Optional neatness trick (used in Day 27):** write attendance as a fraction (80% → 0.8) and use weight 4 instead of 0.04. The contribution is the same: 4 × 0.8 = 3.2 = 0.04 × 80. This also teaches a Day 24 point: **the size of a weight depends on the scale of its input.**

---

## Day 21 — What is Deep Learning?

### 1. Core idea
Deep learning is the part of machine learning that uses **artificial neural networks with many layers** ("deep" = many layers stacked). Instead of humans hand-picking features like "hours studied", a deep network can take **raw data** (pixels, audio samples, text) and learn the useful features itself, layer by layer, from very large amounts of examples.

### 2. Key points to convey (and depth boundary)
1. **DL ⊂ ML ⊂ AI.** He covered this in Day 2. DL is still machine learning: it learns from data with training and testing, like everything in Days 3–8.
2. **The difference is feature learning.** In ML (Days 5–8) *we* gave the model columns like hours studied and attendance. In DL, the network can learn its own features from raw input, such as a photo of a face, a voice note or a sentence.
3. **"Deep" means many layers.** There is no official cutoff. IBM's own pages count it differently ("more than three layers including input and output", "at least 4 layers"). Say "many hidden layers" and don't quote a number as a rule.
4. **Why now:** (a) huge data (smartphones, internet), (b) GPUs that do millions of multiplications in parallel, (c) better training tricks. Milestones: AlexNet won ImageNet 2012. The Transformer came in 2017 (Day 34). ChatGPT launched in Nov 2022. The 2024 Nobel Prize in Physics went to John Hopfield and Geoffrey Hinton for foundational work on artificial neural networks.
5. **DL is not always the best tool.** For a small table like the student pass/fail CSV, a decision tree or logistic regression is often as good or better, and cheaper. DL shines with images, audio, text and massive data.

**Do NOT go into:** CNN/RNN/Transformer internals (Days 32–34), GPUs/hardware detail, the "how many layers exactly" debate, or brain neuroscience.

### 3. Toy numeric example
- **ML style (what we did):** a student is described by 3 numbers: [study hours 4, sleep 7, attendance 80].
- **DL style:** the input is a *photo of the student's answer sheet*. A 12-megapixel phone photo is about 12,000,000 pixels × 3 colours (R, G, B) ≈ **36 million numbers**. Nobody can hand-write rules for 36 million numbers, so the network learns which patterns matter.
- **Classic benchmark (Nielsen, Ch. 1):** handwritten-digit images are 28 × 28 = **784 pixels**, so the network has 784 input numbers. His book's network that learns to read digits is ~74 lines of Python.
- **Size intuition:** our Day 23 toy network will have **9** learnable numbers (parameters). GPT-3 (2020) had **175 billion**. Sarvam's open model released at the India AI Impact Summit (Feb 2026) has about **105 billion** **[verify]**. Same idea, just enormously bigger.

### 4. Indian analogies
| Analogy | How it maps | Accuracy / risk |
|---|---|---|
| **A child learning to recognise Amma's handwriting / a relative from far away** — nobody gives the child rules; after seeing many examples they just *know*. From far you first notice the outline, then the walk, then the face. | Learns features from raw examples; layers go from simple to complex. | **Most accurate** for "learns its own features" and for layers building up. Risk: implies DL works like a human brain. Say it is only *loosely inspired* by the brain. |
| **Factory assembly line (cotton → thread → cloth → shirt)** or **rice → batter → dosa** | Each layer turns the previous output into something more refined. | Good for Day 23 layers. Risk: in a real network every stage is *learned*, not designed by a person. |
| **Instagram Reels / YouTube feed "knows what you like"** | A real product built on deep networks. | Fine as a motivating example, not as an explanation. |

### 5. Whiteboard diagram
1. Draw three nested circles: **AI** (outer) ⊃ **ML** ⊃ **DL** (inner). Callback to Day 2.
2. Left side, under the heading "ML (Days 5–8)": draw a small table (Study hrs | Sleep | Attendance → Pass/Fail) → box "Model" → "Pass".
3. Right side, under "DL": draw a photo (a smiley face or a scribbled digit "7") → a stack of 4–5 vertical columns of small circles (the layers) → "It's a 7".
4. Under the DL stack, label the columns left to right: "edges → shapes → parts → whole object".
5. Write the 3 "why now" ingredients as icons: database (Data), chip (GPU), lightbulb (Better algorithms).

### 6. Misconceptions to pre-empt
- "DL is a different thing from ML." No, it is a subset of ML.
- "Neural networks work like the human brain." They are loosely inspired only. Real neurons are far more complex (CS231n calls the artificial neuron a "very coarse model").
- "DL is always better." Not on small tabular data.
- "Deep = intelligent / understands." Deep only means many layers.
- "DL needs no human work." Humans still collect and label data, choose the architecture and test the model.

### 7. Quiz / comment question
"Which of these do you use daily that runs on deep learning? (a) Face unlock (b) Google Lens (c) Reels feed (d) UPI fraud alerts (e) all of them. Comment your answer!" (Answer: (e). All of them use neural networks at some stage.)

---

## Day 22 — What is an artificial neuron?

### 1. Core idea
An artificial neuron is a tiny calculator. It takes some input numbers, multiplies each by a **weight** (how much that input matters), adds them up, adds a **bias**, and passes the total through an **activation function** to produce one output number. That's all a neuron does. A neural network is many of these connected together.

### 2. Key points (and depth boundary)
1. **Four parts:** inputs (x), weights (w), bias (b), output (after activation).
2. **Two steps:** ① weighted sum, z = w1·x1 + w2·x2 + … + b. ② activation, output = f(z). For now use **sigmoid** because they already know it. Day 25 explains why activation exists.
3. **It's the same as Day 7's logistic regression.** One neuron + sigmoid = logistic regression.
4. **Weights are learned, not typed in by hand.** In Day 7 we *assumed* 0.8, 0.04 and −4. In real training the machine finds them (Day 27).
5. **Biological inspiration only:** dendrites ≈ inputs, synapse strength ≈ weights, the cell "fires" ≈ output. Mention it in one line, then move on.

**Do NOT go into:** vector/dot-product notation, perceptron learning rule, biology beyond one line, other activation functions (Day 25).

### 3. Toy numeric example (Day 7 numbers, now redrawn as a neuron)
Neuron: w1 = 0.8 (study hours), w2 = 0.04 (attendance %), b = −4, activation = sigmoid.

| Student | Study hrs | Attendance % | 0.8×hrs | 0.04×att | + b | z | σ(z) | Decision (50%) |
|---|---|---|---|---|---|---|---|---|
| D (from Day 7) | 4 | 80 | 3.2 | 3.2 | −4 | **2.4** | **0.917** | Pass |
| A (new) | 1 | 50 | 0.8 | 2.0 | −4 | **−1.2** | **0.231** | Fail |

Check: e^−2.4 = 0.0907 → 1/1.0907 = 0.917 ✔. e^1.2 = 3.320 → 1/4.320 = 0.231 ✔.

**Bonus third input** (shows weights can be negative): x3 = hours on Instagram the night before, w3 = −0.5. Student D scrolled 3 hours: z = 2.4 + (−0.5 × 3) = 2.4 − 1.5 = **0.9** → σ(0.9) = **0.711**. Still a pass, but less confident.

### 4. Indian analogies
| Analogy | Mapping | Accuracy / risk |
|---|---|---|
| **Cricket selector deciding whether to pick a player**: looks at recent runs, fitness score, fielding (inputs). Each matters a different amount (weights). The selector has a built-in strictness (bias). The output is "chance of selection". | Inputs × weights + bias → a yes/no confidence. | **Most accurate** single-neuron analogy. Risk: a selector chooses weights by opinion; a neuron *learns* them from data. Say this explicitly. |
| **CGPA / weightage calculation**: internals 20% + externals 80%, credits per subject. | The weighted sum is literally the same arithmetic. | Very accurate for step ①. Risk: CGPA weights are fixed by the university and always positive; NN weights are learned and can be negative. CGPA also has no activation step. |
| **Chai-stall owner deciding to open on a rainy morning**: weather, festival day, exam season (inputs), each with importance; owner's general enthusiasm (bias). | Decision from weighted factors. | OK and relatable; slightly vaguer than the selector analogy. |

### 5. Whiteboard diagram (the "hand-drawn neuron")
1. Draw one **big circle** in the middle. Split it with a vertical line: left half "Σ" (sum), right half "σ" (sigmoid, a small S-curve).
2. On the left, draw **2 arrows** coming in. Write "Study hrs = 4" at the tail of one and "Attendance = 80" at the tail of the other.
3. On each arrow, write its weight: "× 0.8" and "× 0.04".
4. Draw a small arrow from the top labelled "bias b = −4".
5. Inside the Σ half, write "3.2 + 3.2 − 4 = 2.4".
6. Inside the σ half, write "σ(2.4) = 0.917".
7. Draw one **arrow out** to the right: "91.7% → PASS ✔".
8. (Optional) Sketch a cartoon biological neuron above it with arrows: dendrites → inputs, cell body → Σ, axon → output.

### 6. Misconceptions to pre-empt
- "A neuron is a piece of hardware / a tiny brain cell in the computer." It is just a calculation in software.
- "A neuron stores knowledge." The knowledge is in the **weights and bias**, not in the neuron.
- "One neuron is AI." One neuron can only draw a straight-line boundary, just like logistic regression. Power comes from many neurons in layers.
- "Bias means unfair bias." Here bias is just a number added to the sum. It is unrelated to "biased data / unfair AI". Flag this clearly; Telugu speakers will hear "bias" with its everyday meaning.

### 7. Quiz / comment question
"Student X studied 3 hours and has 50% attendance. Using w1 = 0.8, w2 = 0.04, b = −4, what is z? Pass or fail?" (Answer: 2.4 + 2.0 − 4 = 0.4 → σ(0.4) ≈ 0.60 → Pass, but only 60% sure.)

---

## Day 23 — How does a neural network work? (input, hidden, output layers)

### 1. Core idea
A neural network arranges neurons in **layers**. The **input layer** just holds the data. One or more **hidden layers** combine the inputs into intermediate "features". The **output layer** gives the final prediction. Data flows left to right (the **forward pass**). Every neuron does the same small job as Day 22, but stacking them lets the network learn patterns a single neuron cannot.

### 2. Key points (and depth boundary)
1. **Input layer = data, not real neurons.** It does no calculation. (By convention the input layer isn't counted when people say "a 2-layer network".)
2. **Hidden layers learn intermediate features.** Their values aren't shown to us, which is why they're called "hidden". In images, early layers detect edges and later layers detect shapes or objects.
3. **Output layer** gives the answer. For pass/fail that is 1 neuron with sigmoid. For "which of 10 digits" it is 10 output neurons (don't go into softmax).
4. **Fully connected:** each neuron in one layer connects to every neuron in the next, and each connection has its own weight.
5. **Forward pass = prediction.** Learning comes in Video B.

**Do NOT go into:** matrix multiplication, counting layers conventions in depth, CNN/RNN, how many neurons to choose. A one-liner is fine: "people choose this by experiment".

### 3. Toy numeric example (2 inputs → 2 hidden → 1 output)
Inputs: **S = study hours, L = sleep hours** (his Day 7 decision-tree features).

Hidden neurons use **ReLU**: output = the number itself if positive, otherwise 0. One line now; Day 25 explains it. The output uses sigmoid.

- **h1** ("did they study enough?") = ReLU(1·S + 0.5·L − 6)
- **h2** ("did they rest enough?") = ReLU(0.5·S + 1·L − 7)
- **Output** = σ(1·h1 + 1·h2 − 2)

Parameter count: 4 hidden weights + 2 hidden biases + 2 output weights + 1 output bias = **9**.

| Student | S | L | h1 sum | h1 | h2 sum | h2 | z = h1 + h2 − 2 | σ(z) | Prediction |
|---|---|---|---|---|---|---|---|---|---|
| Ravi | 4 | 7 | 4 + 3.5 − 6 = 1.5 | 1.5 | 2 + 7 − 7 = 2 | 2 | 1.5 | **0.818** | Pass (82%) |
| Sita | 6 | 3 | 6 + 1.5 − 6 = 1.5 | 1.5 | 3 + 3 − 7 = −1 | **0** | −0.5 | **0.378** | Fail (38%) |
| Kiran | 1 | 8 | 1 + 4 − 6 = −1 | **0** | 0.5 + 8 − 7 = 1.5 | 1.5 | −0.5 | **0.378** | Fail (38%) |

Story: Sita studied a lot but barely slept, so the "rested" neuron stays off. Kiran slept well but hardly studied, so the "studied" neuron stays off. Ravi did both, so both neurons are on and he passes. This mirrors his Day 7 decision tree, where sleep mattered after study. **Caveat to say aloud:** the names "studied enough" and "rested enough" are *our* labels for the story. Real hidden neurons learn whatever is useful and usually have no neat human meaning.

### 4. Indian analogies
| Analogy | Mapping | Accuracy / risk |
|---|---|---|
| **Exam evaluation chain**: answer sheet (input) → subject teachers each check different aspects (hidden layer) → principal combines their reports into a final result (output). | Layered processing; each hidden "teacher" focuses on something different. | **Most accurate** for structure. Risk: real hidden neurons aren't assigned roles; they discover them during training. |
| **Cricket team selection committee**: stats (input) → batting coach, bowling coach, fitness trainer each give a score (hidden) → chief selector decides (output). | Same layered idea; very Indian. | Good. Same risk as above, plus real networks often have many hidden layers, not one. |
| **Dosa making**: rice + urad dal (input) → batter (hidden, an intermediate product you can't eat directly) → dosa (output). | Intermediate representations. | Nice for "hidden = intermediate"; weak on weights/connections. Use as a one-liner only. |

### 5. Whiteboard diagram
1. Draw **3 columns**. Left: 2 circles labelled S and L ("Input layer"). Middle: 2 circles h1, h2 ("Hidden layer"). Right: 1 circle ("Output layer").
2. Draw **all 4 lines** from inputs to hidden (show "fully connected"), and 2 lines from hidden to output.
3. Write a weight on each line (1, 0.5, 0.5, 1; then 1, 1). Write the biases (−6, −7, −2) on small arrows into each neuron.
4. Put **Sita's numbers** in: 6 and 3 at the inputs → 1.5 in h1 and "−1 → 0" in h2 (strike through −1) → "38% → Fail" at the output.
5. Draw a big arrow under the whole thing: "Forward pass →".
6. Bonus: erase and redraw with 3 hidden columns to show "deep = more hidden layers".

### 6. Misconceptions to pre-empt
- "Each hidden neuron has a clear human meaning." Not usually.
- "More layers is always better." It costs more data and compute and can overfit (ties to Day 3: training vs testing).
- "The network looks things up in a database." No. It *computes* the answer from weights every time.
- "The input layer does computing." It only holds the data.
- "Data flows backwards during prediction." Prediction is forward only. The backward flow is for learning (Day 28).

### 7. Quiz / comment question
"In our network, a student studied 6 hours and slept 8 hours. Is h2 on or off?" (Answer: h2 = 3 + 8 − 7 = 4 → ON. h1 = 6 + 4 − 6 = 4. z = 4 + 4 − 2 = 6 → σ(6) ≈ 0.998 → Pass.)

---

## Day 24 — What are weights and biases?

### 1. Core idea
**Weights** say how strongly each input pushes the prediction, and in which direction: a positive weight pushes up, a negative weight pushes down, a weight near zero means "ignore this". The **bias** is a starting offset that shifts how easily the neuron fires, whatever the inputs are. Together they are the network's **parameters**: the numbers that training adjusts. A trained model *is* basically its weights and biases.

### 2. Key points (and depth boundary)
1. **Weight = importance + direction.** Big positive → strong push up. Negative → push down. ~0 → ignored.
2. **Bias = threshold / starting point.** With b = −4, the neuron says "pass" (z > 0) only when the weighted evidence is more than 4. This is like the "36 marks to pass" cutoff he used in Day 7.
3. **Weight size depends on input scale.** 0.04 looks tiny, but attendance runs 0–100, so it contributes as much (3.2) as study hours with weight 0.8. Don't judge importance by the raw weight alone.
4. **These numbers ARE what the model "learned".** When you download a model (e.g. an open LLM), you mostly download a giant file of weights.
5. **Initially random, then trained.** Training starts from small random weights and adjusts them (Video B).

**Do NOT go into:** weight initialisation schemes, regularisation, normalisation, why biases are sometimes omitted.

### 3. Toy numeric example (turn the knobs on Student D: 4 hrs, 80%)
| Change | z | σ(z) | Decision |
|---|---|---|---|
| Original (w1 = 0.8, w2 = 0.04, b = −4) | 3.2 + 3.2 − 4 = **2.4** | 0.917 | Pass |
| Ignore attendance (w2 = 0) | 3.2 + 0 − 4 = **−0.8** | 0.310 | **Fail** |
| Stricter examiner (b = −6) | 6.4 − 6 = **0.4** | 0.599 | Pass (barely) |
| Lenient examiner (b = −2) | 6.4 − 2 = **4.4** | 0.988 | Pass (very sure) |
| Add Instagram hours = 3 with w3 = −0.5 | 2.4 − 1.5 = **0.9** | 0.711 | Pass (less sure) |

Lesson: **the same student gets a different prediction just by changing the weights or bias.** So "learning" = finding the right weights and bias.

### 4. Indian analogies
| Analogy | Mapping | Accuracy / risk |
|---|---|---|
| **Volume/bass/treble knobs on a music system (or EQ in a phone)**: each knob controls how loud one part is; there's also a master offset. | Weights = knobs; training = turning knobs till it sounds right. | **Most accurate** for "parameters you tune". Risk: knobs only go 0 → max, while weights can be negative. |
| **Mother deciding if a son can go to a movie**: marks (+ strong weight), homework done (+), late nights this week (− weight). Her base mood that day = bias. | Positive/negative weights + a baseline. | Very relatable and handles negative weights. Risk: like the selector, she chooses by judgement, not by data. |
| **Grace marks / moderation = bias** | Shifts everyone's result by a fixed amount, whatever their answers. | Accurate for bias. Note that a negative bias = stricter. |

### 5. Whiteboard diagram
1. Redraw the Day 22 neuron.
2. On the weight arrows, draw **arrow thickness**: thick line = large weight, thin = small, dashed red = negative (Instagram).
3. Next to it, draw a **number line**: mark 0 in the middle, "Fail ← | → Pass". Place a dot at 2.4 (D).
4. Change b from −4 to −6 → slide the dot left to 0.4. Show "bias shifts everyone". Then set w2 = 0 → dot jumps to −0.8 (Fail).
5. Optional (for curious viewers): sketch the sigmoid S-curve and show that changing the bias slides the whole S left or right, while a bigger weight makes the S steeper.

### 6. Misconceptions to pre-empt
- "Bigger weight = more important feature, always." Only if the inputs are on the same scale.
- "Weights are set by programmers." They are learned. In Day 7 we only *assumed* them for a demo.
- "Bias = prejudice." Not here (see Day 22).
- "Weights are always between 0 and 1 / always positive." They can be any real number, including negative.
- "Each weight means one fact the model knows." In big networks, knowledge is spread across many weights.

### 7. Quiz / comment question
"If we change the bias from −4 to −8, will Student D (4 hrs, 80%) still pass?" (Answer: z = 6.4 − 8 = −1.6 → σ ≈ 0.17 → Fail.)

---

## Day 25 — What is an activation function? (Video B opener)

### 1. Core idea
An activation function is the small "decision step" applied after a neuron's weighted sum. It bends the straight-line calculation into something non-straight. Without it, stacking 100 layers would collapse into one straight-line model: no more powerful than a single neuron. **ReLU** (keep positives, turn negatives to 0) is the default in hidden layers. **Sigmoid** squashes any number into 0–1, so it suits a yes/no probability output.

### 2. Key points (and depth boundary)
1. **Why nonlinearity:** linear on top of linear is still linear (Google MLCC). The real world isn't straight-line: more sleep helps up to a point, then too much doesn't.
2. **ReLU = max(0, z).** It is simple, fast, and the most common default for hidden layers (Google MLCC recommends starting with ReLU).
3. **Sigmoid = squash to (0, 1).** σ(0) = 0.5. Big positive → near 1. Big negative → near 0. Used at the output for pass/fail (same as Day 7).
4. **Each ReLU adds one "bend".** Many ReLU neurons together can approximate curvy patterns.
5. **Name-drop only:** other activations exist (tanh; GELU and its variants inside Transformers/LLMs; softmax for multi-class outputs). Mention, don't explain.

**Do NOT go into:** derivatives of activations, vanishing gradients in detail (one line max: "sigmoid in many hidden layers makes learning slow, which is one reason ReLU won"), leaky ReLU, softmax maths, universal approximation theorem proofs.

### 3. Toy numeric examples
**(a) Without activation, layers collapse:**
Layer 1: h = 2x + 1. Layer 2: out = 3h − 2. Substitute: out = 3(2x + 1) − 2 = **6x + 1**. That's just one straight line, so two layers did nothing extra.

**(b) ReLU and sigmoid tables:**
| z | ReLU(z) | σ(z) |
|---|---|---|
| −2.4 | 0 | 0.083 |
| −1 | 0 | 0.269 |
| 0 | 0 | 0.500 |
| 1.5 | 1.5 | 0.818 |
| 2.4 | 2.4 | 0.917 |

**(c) Callback to Day 23:** Sita's h2 sum was −1 → ReLU → 0. That neuron "stayed off".

**(d) The sleep "sweet spot" that a straight line cannot draw:**
score(L) = ReLU(L − 3) − 2 × ReLU(L − 7) for sleep hours L between 3 and 11.

| Sleep L | ReLU(L−3) | 2×ReLU(L−7) | score |
|---|---|---|---|
| 3 | 0 | 0 | 0 |
| 5 | 2 | 0 | 2 |
| 7 | 4 | 0 | **4 (peak)** |
| 8 | 5 | 2 | 3 |
| 9 | 6 | 4 | 2 |
| 11 | 8 | 8 | 0 |

Two ReLU neurons made a mountain shape peaking at 7 hours. A single straight line can only ever go up or only ever go down. (The formula keeps falling below 0 after 11 hours; keep the drawing to the 3–11 range.)

### 4. Indian analogies
| Analogy | Mapping | Accuracy / risk |
|---|---|---|
| **ReLU = water-tank overflow pipe**: nothing comes out until the water rises above the pipe; after that, outflow grows with the extra water. | Zero below threshold, linear above (the threshold is set by the bias). | **Most accurate** for ReLU. |
| **Sigmoid = fan regulator / dimmer**: smoothly goes from "off" to "full", never beyond. Or a confidence meter from 0% to 100%. | Smooth squash into a fixed range. | Good. Risk: a regulator has steps; sigmoid is smooth. |
| **Salt in curry (non-linearity)**: a little salt improves taste, more improves it more, too much ruins it. Taste isn't a straight line in salt. | Why we need non-straight functions. | Good for *why nonlinear*. Keep it separate from the gradient-descent salt analogy, or tell the audience you'll reuse it. |
| **Traffic signal (on/off)** | A hard step function, like the old perceptron. | **Can mislead.** A hard on/off step has no slope, so the network can't learn which way to adjust (Day 27). Use it only to contrast: "old step-function neurons were like a traffic light; modern ones are smooth or ramp-like so they can learn." |

### 5. Whiteboard diagram
1. Draw two small axes side by side.
2. **Left: ReLU.** A flat line on the zero axis for negative values, then a 45° ramp up from 0. Label "max(0, z)". Mark Sita's −1 → 0.
3. **Right: sigmoid.** An S-curve between horizontal dashed lines at 0 and 1. Mark the middle point (0, 0.5) and the point (2.4, 0.917) (Student D).
4. Below: draw two boxes "×2 +1" → "×3 −2" with an arrow = "6x + 1" and a big "same as one line!" stamp.
5. Then draw the **sleep mountain**: x-axis sleep hours 3–11, rising to a peak at 7, falling to 0 at 11. Label "only possible with activation".

### 6. Misconceptions to pre-empt
- "Activation = the neuron switching on like a light bulb." Only partly. ReLU passes a *value*, not just on/off. Sigmoid is smooth.
- "Sigmoid is the best because logistic regression uses it." For hidden layers ReLU is usually preferred. Sigmoid is typically used at a yes/no output.
- "More complicated activation = smarter network." The key point is just *non-linearity*.
- "ReLU is linear because it's made of straight pieces." It's piecewise-linear, and the bend at 0 is what makes it non-linear.

### 7. Quiz / comment question
"What is ReLU(−5)? What is ReLU(3)? And why can't we just remove activation functions?" (Answers: 0; 3; without them, stacked layers collapse into one straight line.)

---

## Day 26 — What is a loss function?

### 1. Core idea
A loss function is a single number that measures **how wrong** the network's prediction is compared with the true answer. 0 means perfect; bigger means worse. Training means "make this number as small as possible" across all training examples. For predicting numbers (regression) we commonly use squared error. For predicting probabilities like pass/fail (classification) we use **log loss (binary cross-entropy)**, which punishes confident wrong answers very heavily.

### 2. Key points (and depth boundary)
1. **Loss = score of wrongness.** We compare the prediction with the label (the "answer key" from Day 5, supervised learning).
2. **Regression → squared error.** Error = actual − predicted. Squaring makes negatives positive and punishes big misses more. The average over many examples is MSE.
3. **Classification → log loss.** Loss = −ln(probability the model gave to the correct answer). 90% sure and right → tiny loss. 5% sure (confidently wrong) → huge loss.
4. **Loss ≠ accuracy.** Accuracy (Day 3) just counts right/wrong. Loss also measures *how* right or wrong, and it changes smoothly. That smoothness is what gradient descent needs. We train on loss and report accuracy.
5. **We average loss over all training examples.** We want the model to be good for everyone, not just one student.

**Do NOT go into:** the derivation of cross-entropy, information theory, softmax/categorical cross-entropy, MAE vs Huber, regularisation terms.

### 3. Toy numeric examples
**(a) Regression (marks prediction, from Day 6):**
| Student | Actual marks | Predicted | Error | Squared |
|---|---|---|---|---|
| 1 | 80 | 70 | 10 | 100 |
| 2 | 60 | 65 | −5 | 25 |
| 3 | 90 | 88 | 2 | 4 |
| **MSE** | | | | (100 + 25 + 4)/3 = **43** |

**(b) Classification (pass/fail, log loss), with natural log:**
| Case | P(pass) predicted | Truth | P(correct answer) | Loss = −ln(…) |
|---|---|---|---|---|
| Student D | 0.917 | Pass | 0.917 | **0.087** (tiny) |
| Unsure | 0.50 | Pass | 0.50 | **0.693** |
| Sita (Day 23 net) | 0.378 | actually **Passed** | 0.378 | **0.974** |
| Confidently wrong | 0.05 | Pass | 0.05 | **3.00** (huge) |

Shortcut: when the truth is "Fail", use (1 − P(pass)) as the probability of the correct answer.

Simple talking point: "Going from 50% to 5% for the right answer doesn't double the punishment; it multiplies it by more than 4 (0.69 → 3.0)."

### 4. Indian analogies
| Analogy | Mapping | Accuracy / risk |
|---|---|---|
| **Google Maps "you are 3 km away from destination"** | Loss = distance from the right answer; training = reduce that distance. | **Most accurate** for "single number, lower is better". |
| **Betting with friends on an India–Pakistan match**: say "100% India will win" and lose → huge embarrassment; say "60%" and lose → small embarrassment. | Log loss: confident wrong answers cost much more. | Accurate for log loss. Risk: avoid gambling framing. Maybe use "promise to friends" instead. |
| **Negative marking in EAMCET/JEE** | Wrong answers cost you. | **Partly misleading:** negative marking is a fixed penalty per wrong answer. Log loss scales with *how confident* you were. Use it only to say "wrong answers have a cost". |

### 5. Whiteboard diagram
1. Draw a dartboard. The bullseye is "true answer". Darts at different distances. Label the distance "loss".
2. Draw a small number line from 0 to 1 (predicted P(pass)) with truth = Pass at 1. Mark 0.917 (short red gap), 0.5 (medium), 0.05 (long gap).
3. Sketch the log-loss curve: x-axis "probability given to the correct answer" 0 → 1, y-axis "loss". The curve shoots up near 0 and touches ~0 at 1. Mark the 4 points from the table.
4. Write "Training goal = push the loss down ↓".

### 6. Misconceptions to pre-empt
- "Loss = accuracy." No. Accuracy is a count; loss is a smooth penalty.
- "Loss 0 on training data = perfect model." It might be memorising (overfitting). Check test data (Day 3).
- "Loss can be any number, so we just look at the error sign." For log loss and MSE, loss is never negative.
- "One loss function fits every problem." The choice depends on the task (regression vs classification).

### 7. Quiz / comment question
"Model A says 90% pass, Model B says 60% pass, and the student actually failed. Which model gets the bigger loss and why?" (Answer: Model A. It was more confident and wrong: −ln(0.10) = 2.30 vs −ln(0.40) = 0.92.)

---

## Day 27 — What is gradient descent?

### 1. Core idea
Gradient descent is the method that **adjusts the weights and biases, step by step, to reduce the loss**. For each weight, it asks: "if I nudge this weight up a tiny bit, does the loss go up or down, and how steeply?" That slope is the **gradient**. Then it moves every weight a small step in the direction that lowers the loss. The **learning rate** controls how big each step is. Repeat thousands of times and the loss slides downhill.

### 2. Key points (and depth boundary)
1. **Loss as a valley.** Picture loss vs one weight as a U-shaped valley. The goal is the bottom.
2. **Gradient = slope = direction + steepness.** Go *opposite* to the slope (downhill).
3. **Update rule in words:** new weight = old weight − (learning rate × slope).
4. **Learning rate matters.** Too small → very slow. Too big → overshoots, bounces or blows up. (Day 29 will expand on this, so just plant the seed.)
5. **All weights update together**, each by its own slope. Real training uses small batches of examples at a time ("stochastic" or mini-batch GD) and smarter variants (e.g. Adam). Name-drop only; batches/epochs belong to Day 29.

**Do NOT go into:** partial derivatives, calculus notation, convexity, local-minima theory, momentum/Adam internals, the derivation of the (p − y)·x gradient. You may *state* it as "the slope comes out simple", without proof.

### 3. Toy numeric examples
**(a) One-weight valley (pure intuition):** loss(w) = (w − 3)². The best w is 3. Slope at w is 2(w − 3).

| Learning rate | Steps of w starting at 0 | Behaviour |
|---|---|---|
| 0.25 | 0 → 1.5 → 2.25 → 2.625 → 2.81 → 2.91 | Smoothly approaches 3 ✔ |
| 1.0 | 0 → 6 → 0 → 6 → 0 … | Bounces forever ✘ |
| 1.1 | 0 → 6.6 → −1.32 → 8.18 → −3.22 → 10.47 | Explodes ✘ |

(First step for lr = 0.25: slope at 0 = 2(0 − 3) = −6 → w = 0 − 0.25 × (−6) = 1.5.)

**(b) One real update in the student universe (sigmoid neuron + log loss):**
Using attendance as a fraction: w1 = 0.8 (study hrs), w2 = 4 (attendance fraction), b = −4. This is the same model as Day 7, rescaled.
New student **Priya**: studied 2 hrs, attendance 60% (0.6), **actually passed** (y = 1).

- Forward: z = 0.8×2 + 4×0.6 − 4 = 1.6 + 2.4 − 4 = **0** → σ(0) = **0.50** → "50-50, confused".
- Loss = −ln(0.5) = **0.693**.
- For a sigmoid neuron with log loss, the slope for each weight comes out neatly as **(prediction − truth) × that input**:
  - slope for w1 = (0.5 − 1) × 2 = **−1.0**
  - slope for w2 = (0.5 − 1) × 0.6 = **−0.3**
  - slope for b = (0.5 − 1) = **−0.5**
- Learning rate = 0.1:
  - w1: 0.8 − 0.1×(−1.0) = **0.9**
  - w2: 4 − 0.1×(−0.3) = **4.03**
  - b: −4 − 0.1×(−0.5) = **−3.95**
- Check: z = 0.9×2 + 4.03×0.6 − 3.95 = 1.8 + 2.418 − 3.95 = **0.268** → σ = **0.567**. Loss = −ln(0.567) = **0.568**. Loss went down ✔ (0.693 → 0.568).
- **Simplest on-screen version (update w1 only):** w1 = 0.9 → z = 1.8 + 2.4 − 4 = 0.2 → σ = 0.550 → loss 0.598. "One knob turned, loss dropped."

Why the earlier "0.04 × 80" scale is awkward here: the slope for w2 would be −0.5 × 60 = −30, and a 0.1 step would throw w2 from 0.04 to 3.04, which is nonsense. This is why real projects **scale inputs** (60% → 0.6). It's a nice "pro tip" moment and a teaser for Day 29–30.

### 4. Indian analogies
| Analogy | Mapping | Accuracy / risk |
|---|---|---|
| **Walking down Tirumala ghat steps / a hill in thick fog at night**: you can't see the bottom, but you feel which way the ground slopes under your feet and take a step downhill, again and again. | Loss surface = hill; gradient = slope under your feet; step size = learning rate. | **Most accurate** (the standard textbook analogy). Risk: you might stop in a small dip (local minimum). Say "in big networks this works surprisingly well in practice". |
| **Amma adjusting salt/spice in curry or sambar by tasting**: taste (loss) → "too bland, add a little" → taste again. Too big a fistful → overshoot. | Feedback loop, direction, step size, overshooting. | Very relatable. **Can mislead:** (1) she adjusts one ingredient at a time; GD adjusts *all* weights at once, each by its own slope; (2) she judges by feel, while GD computes the exact slope; (3) salt can't be removed, but weights can move either way. |
| **Tuning a veena/guitar string or an old radio dial**: turn, listen, turn less as you get close. | Small corrections in the right direction. | Good, but single-knob only. |

### 5. Whiteboard diagram
1. Draw a big **U-shaped valley**. X-axis "weight w", y-axis "loss". Mark the bottom with a ⭐ "best w".
2. Put a ball (or a stick figure) on the left slope at w = 0. Draw a short tangent line showing the slope.
3. Draw arrows: small hops going down → down → down to the ⭐ (lr = 0.25).
4. In another colour, draw a ball jumping across the valley 0 ↔ 6 (lr = 1.0, "too big"), and one jumping out of the valley (lr = 1.1).
5. Side box: "new w = old w − (learning rate × slope)".
6. Then, under it, write Priya's update: 0.8 → 0.9, loss 0.693 → 0.598.

### 6. Misconceptions to pre-empt
- "Gradient descent finds the perfect answer in one step." It takes many small steps.
- "A bigger learning rate is always faster." It can overshoot or diverge.
- "Gradient descent and backpropagation are the same." GD *uses* slopes to update weights. Backprop is how we *compute* those slopes in a multi-layer network (Day 28).
- "It updates one weight at a time." All weights move together, each by its own slope.
- "The loss always goes down every step." With mini-batches it wiggles, and the trend is down.

### 7. Quiz / comment question
"Your weight is 2, the slope is +4, and the learning rate is 0.1. What's the new weight? Did it go up or down?" (Answer: 2 − 0.1×4 = 1.6 → down, because the slope was positive.)

---

## Day 28 — What is backpropagation?

### 1. Core idea
Backpropagation is how a multi-layer network figures out **how much each weight (even deep inside hidden layers) contributed to the final error**. It starts at the output's mistake and passes "blame" backwards, layer by layer. Each connection gets blame in proportion to how strongly it carried the signal. A neuron that was switched off (ReLU = 0) gets none. These blame amounts are exactly the gradients that gradient descent needs. The full cycle is **forward pass → loss → backward pass (backprop) → gradient-descent update**, repeated many times.

### 2. Key points (and depth boundary)
1. **Problem it solves:** for a hidden weight, we can't directly see how it affected the loss, because its effect passes through other neurons. Backprop computes this efficiently for all weights in one backward sweep.
2. **Blame flows backwards along the same wires** the data flowed forward on.
3. **Blame is proportional to contribution:** a weight's blame = (error signal arriving at its neuron) × (the input it carried). A big input → big blame. A zero input → zero blame.
4. **It's the chain rule** ("multiply the effects along the path"). Say the name once; no formulas.
5. **Backprop computes; gradient descent updates.** One update also changes predictions for other students, which is why we average over many examples.

**Do NOT go into:** chain-rule derivations, computational graphs in detail, vanishing/exploding gradients beyond one sentence, automatic differentiation frameworks (save for Day 30), biology ("the brain doesn't obviously do backprop" is fine as one line).

### 3. Toy numeric example (Day 23 network, student Sita)
Recall: Sita, S = 6, L = 3. The network said **37.8% pass**, but **she actually passed** (y = 1). Loss = −ln(0.378) = **0.974**.

**Step 1: error at the output.** For sigmoid + log loss, the output's error signal = prediction − truth = 0.378 − 1 = **−0.62**. The minus sign means "the output should have been *higher*".

**Step 2: blame for the output layer's weights** (error × what came in on that wire):
- wire h1 → output: −0.62 × h1 (1.5) = **−0.93** → increase this weight
- wire h2 → output: −0.62 × h2 (**0**) = **0** → no change ("h2 was silent, so it can't be blamed")
- output bias: **−0.62** → increase

**Step 3: pass blame back to hidden neurons** (error × the weight connecting them, then through ReLU):
- To h1: −0.62 × 1 (its output weight) = −0.62. h1 was ON (sum 1.5 > 0), so ReLU lets it through → **−0.62**
- To h2: −0.62 × 1 = −0.62, but h2 was OFF (sum −1 < 0), so ReLU blocks it → **0**

**Step 4: blame for the first layer's weights:**
- S → h1: −0.62 × S (6) = **−3.73**
- L → h1: −0.62 × L (3) = **−1.87**
- h1 bias: **−0.62**
- All of h2's weights and bias: **0**

**Step 5: gradient-descent update** (learning rate 0.02; new = old − 0.02 × blame):
| Parameter | Old | Blame | New |
|---|---|---|---|
| S → h1 | 1 | −3.73 | **1.075** |
| L → h1 | 0.5 | −1.87 | **0.537** |
| h1 bias | −6 | −0.62 | **−5.988** |
| h1 → output | 1 | −0.93 | **1.019** |
| output bias | −2 | −0.62 | **−1.988** |
| h2's weights/bias, h2 → output | unchanged | 0 | unchanged |

**Step 6: forward pass again for Sita:** h1 = 1.075×6 + 0.537×3 − 5.988 ≈ **2.07**; h2 = 0. z ≈ 1.019×2.07 − 1.988 ≈ **0.12** → **53% pass**. Loss drops from 0.974 → **0.633** ✔. Prediction flips to Pass.

**Side effect worth showing:** Ravi's prediction moves from 81.8% → **89.3%**. Kiran stays at **38%**. One student's lesson changed the network for everyone. That's why training averages the blame over many students, so one student doesn't drag the weights too far.

(The numbers above were computed at full precision and rounded for display. If you show the products with −0.62 exactly, the rounded results match to 2 decimals.)

### 4. Indian analogies
| Analogy | Mapping | Accuracy / risk |
|---|---|---|
| **Restaurant complaint traced back through the kitchen**: a customer says the biryani is too salty (loss). The head chef asks who added what: the masala assistant added a lot (big blame), the rice cook added none (no blame), and the masala assistant checks his supplier's mix. Everyone adjusts *a little* next time. | Error at the output, blame passed backwards along the chain, proportional to contribution. Those who contributed nothing get zero blame. | **Most accurate**, because the chain structure mirrors the chain rule. Risk: in real backprop *every* contributing weight is adjusted slightly and simultaneously. Nobody gets "fired". |
| **Cricket post-match analysis**: lost by 30 runs. The coach traces back which batters, bowlers and fielding decisions contributed, and by how much, then adjusts practice. | Credit/blame assignment. | Good and very relatable. **Can mislead** if it implies dropping players. Backprop never removes neurons; it nudges every weight. Also, the coach uses opinion, while backprop uses exact arithmetic. |
| **Exam result → tracing mistakes back**: failed maths → which chapters → which concepts → which practice habit. | Going backwards through the layers of cause. | Intuitive for "backwards", but weaker on "proportional amounts" and "all at once". |

### 5. Whiteboard diagram
1. Redraw the Day 23 network (S, L → h1, h2 → output) in **black** with Sita's forward numbers (6, 3 → 1.5, 0 → 38%).
2. At the output, write in **red**: "Truth = Pass (1). Error = −0.62".
3. Draw **red arrows going right-to-left** along each wire. On h1 → output write "−0.93". On h2 → output write "0 (h2 was off)".
4. Draw a red arrow into h1 ("−0.62") and a red ✗ on h2 ("blocked by ReLU").
5. Continue red arrows to the input wires: "−3.73" on S → h1, "−1.87" on L → h1.
6. In **green**, write the new weights next to the old ones (1 → 1.075, etc.).
7. Draw a circular loop in a corner: **Forward → Loss → Backward → Update → (repeat)**. This is the one picture to remember for the whole of Video B.

### 6. Misconceptions to pre-empt
- "Backprop is a separate learning algorithm from gradient descent." It's the slope-calculator that GD relies on.
- "Data flows backwards." Only the *error/blame signal* flows backwards. Inputs are never changed.
- "Backprop fixes the network in one go." It's one small nudge per step, over thousands of steps.
- "Only the last layer learns." Every layer gets blame, which is the whole point of backprop.
- "The brain learns exactly like this." That's an open research question. Don't claim it.
- "A neuron with zero output gets the biggest correction." It gets **none** for that example (that's also why "dead" ReLU neurons can be a problem, a one-line teaser at most).

### 7. Quiz / comment question
"In Sita's case, why did the h2 → output weight not change at all? Comment your answer in one line!" (Answer: h2's output was 0, because ReLU switched it off, so it contributed nothing and gets no blame.)

---

## Real-world deep learning examples for Indian viewers (2026)

| Example | What DL does | 2026 fact / hook (with source) |
|---|---|---|
| **ChatGPT, Gemini, Claude (LLMs)** | Huge Transformer neural networks predict the next word (Day 34). | Feb 2026: Sam Altman said India had ~**100 million weekly ChatGPT users**, the 2nd-largest market and the largest number of student users ([TechCrunch](https://www.techcrunch.com/2026/02/15/india-has-100m-weekly-active-chatgpt-users-sam-altman-says/), [TechRepublic](https://www.techrepublic.com/article/news-india-100-million-weekly-chatgpt-users/)). Later 2026 reports quote OpenAI India saying India overtook the US. That is a company claim, so **[verify]** before saying "No. 1". |
| **UPI fraud detection** | Models score each transaction/account for fraud risk in real time. | NPCI provides an AI/ML-based fraud monitoring solution to banks. RBI Innovation Hub's **MuleHunter.AI** (spots mule accounts) was onboarded by **29 banks** per a Rajya Sabha answer, July 2026 ([eWeek](https://www.eweek.com/news/npci-ai-payments-fraud-rules-apac-india/), [The Next Web](https://thenextweb.com/news/india-upi-npci-ai-billion-daily-transactions)). UPI handles 750M+ transactions/day. Note: these are "AI/ML" systems; don't claim every one is specifically a deep network. |
| **Face unlock, Aadhaar face authentication, DigiYatra** | Neural networks turn a face image into a numeric "faceprint" and compare it. | Aadhaar face authentication crossed **200 crore** transactions by Aug 2025 ([Business Standard](https://www.business-standard.com/india-news/uidai-aadhaar-face-authentication-crosses-2-billion-transactions-125081101734_1.html)). DigiYatra became **mandatory for international transit passengers at Delhi, Mumbai, Bengaluru and Hyderabad** from 1 June 2026 ([Outlook Traveller](https://www.outlooktraveller.com/News/digiyatra-now-mandatory-for-international-transit-at-four-major-indian-airports)). Good hook for a Hyderabad audience. Mention privacy concerns briefly for balance. |
| **Medical imaging: TB from chest X-rays** | A deep network reads X-rays and flags likely TB. | Qure.ai's qXR in Delhi slum screening (Jul 2025–Mar 2026): **1,68,568** people X-rayed, **18,377** flagged, **877** TB cases confirmed by molecular tests ([ThePrint](https://theprint.in/india/ai-assisted-x-rays-flag-18377-people-for-tb-testing-in-delhi-slums-877-confirmed-study/3064481/)). WHO has recommended computer-aided detection for TB screening since 2021. |
| **Indian-language AI (Telugu!)** | Neural translation and speech models. | Bhashini (Govt of India) hosts translation/speech models, including open Sarvam models ([tele.net.in](https://tele.net.in/digital-india-bhashini-division-enables-availability-of-advanced-ai-models-on-the-bhashini-platform/)). Sarvam-Translate covers all 22 scheduled languages, including Telugu ([Sarvam blog](https://www.sarvam.ai/blogs/sarvam-translate)). |
| **YouTube / Instagram Reels recommendations** | Deep networks rank which video you'll watch next. | Google's paper "Deep Neural Networks for YouTube Recommendations" (2016) describes the two-stage deep model ([Google Research](https://research.google/pubs/pub45530/)). Great hook: "this very video reached you because of a neural network." |
| **Google Lens / photo search, Google Translate camera** | Image recognition (Day 31–32 CNN preview). | Point the camera at a Telugu signboard and translate it. Demo-able live. |
| **Self-driving & driver assistance** | Cameras + neural nets detect lanes, cars, pedestrians. | Robotaxis run in some US/China cities. In India, ADAS features (lane-keep, auto-braking) are in many new cars. Don't claim full self-driving in India. |

---

## Continuity bridge — how each DL idea connects to what he already taught

| DL concept (Day) | Already-taught ML concept | Bridge line for the script |
|---|---|---|
| Deep learning (21) | AI vs ML vs DL (Day 2); supervised learning (Day 5) | "DL is the innermost circle we drew on Day 2. It still learns from labelled examples, like Day 5." |
| Artificial neuron (22) | **Logistic regression + sigmoid** (Day 7, Student D: z = 2.4 → 91.7%) | "That Day 7 calculation *was* one neuron. Logistic regression = a 1-neuron network." |
| Layers (23) | Decision tree's multi-step questions (Day 7: study → sleep → previous grade) | "A tree asks questions one after another; a network combines features layer after layer, but with smooth weights instead of yes/no splits." |
| Weights & biases (24) | Day 7's w1 = 0.8, w2 = 0.04, b = −4 ("assumed, normally learned"); the 36-marks / 50% threshold | "Day 7 we *assumed* them. Now we see they're the knobs the machine learns." |
| Activation (25) | Sigmoid (Day 7); SVM kernels for non-straight boundaries (Day 7) | "SVM needed a kernel trick for curvy boundaries; neural networks get curves from activation functions." |
| Loss (26) | Training vs testing, accuracy (Day 3); regression = numbers, classification = categories (Day 6) | "Accuracy tells you *if* it's right; loss tells you *how wrong*. Regression → squared error, classification → log loss." |
| Gradient descent (27) | "The machine learns the weights from data" (Days 3–4, 7) | "Finally we see *how* the machine found those weights: by stepping downhill on the loss." |
| Backprop (28) | Training phase (Day 3); first ML project (Day 4) | "This is what happens inside `model.fit()` for neural networks. Forward, loss, backward, update, again and again." |
| (Optional contrast) | K-means/DBSCAN (Day 8) | "Clustering is unsupervised; everything in these two videos is supervised, because we need the true answer to compute the loss." |

---

## Sources

Core concept references (standard textbooks/courses; see the research note at the top about blocked page fetches):
- Google Machine Learning Crash Course: Neural networks: activation functions. https://developers.google.com/machine-learning/crash-course/neural-networks/activation-functions (linear-on-linear is still linear; ReLU is the recommended default.)
- Google MLCC: Neural networks overview / backpropagation / gradient descent modules. https://developers.google.com/machine-learning/crash-course **[verify exact subpage paths]**
- Stanford CS231n: Neural Networks Part 1 (neuron model, "coarse model" caveat, single sigmoid neuron = logistic regression). https://cs231n.github.io/neural-networks-1/
- Stanford CS231n: Backpropagation, intuitions. https://cs231n.github.io/optimization-2/
- Stanford CS109 lecture "Deep learning" (one neuron = logistic regression; threshold at 0.5). https://web.stanford.edu/class/archive/cs/cs109/cs109.1226/lectures/28_deep_learning.pdf
- 3Blue1Brown: Neural networks series. https://www.3blue1brown.com/topics/neural-networks ; Backpropagation (intuitive). https://www.3blue1brown.com/lessons/backpropagation ; Backpropagation calculus. https://www.3blue1brown.com/lessons/backpropagation-calculus
- Michael Nielsen, *Neural Networks and Deep Learning*, Ch. 1 (perceptrons, sigmoid neurons, 28×28 MNIST, 74-line program). http://neuralnetworksanddeeplearning.com/chap1.html ; Ch. 2 (backprop). http://neuralnetworksanddeeplearning.com/chap2.html
- IBM: What is deep learning? https://www.ibm.com/topics/deep-learning ; What is a neural network? https://www.ibm.com/topics/neural-networks
- deeplearning.ai: Neural Networks and Deep Learning course (Andrew Ng; logistic regression as a neural network). https://www.deeplearning.ai/courses/deep-learning-specialization/
- Nobel Prize in Physics 2024 (Hopfield, Hinton). https://www.nobelprize.org/prizes/physics/2024/summary/

India / 2026 examples:
- TechCrunch, India 100M weekly ChatGPT users (Feb 2026). https://www.techcrunch.com/2026/02/15/india-has-100m-weekly-active-chatgpt-users-sam-altman-says/
- TechRepublic, India second-largest ChatGPT market. https://www.techrepublic.com/article/news-india-100-million-weekly-chatgpt-users/
- eWeek, NPCI turns to AI as fraud rules tighten. https://www.eweek.com/news/npci-ai-payments-fraud-rules-apac-india/
- The Next Web, UPI/NPCI AI and billion daily transactions (Jun 2026). https://thenextweb.com/news/india-upi-npci-ai-billion-daily-transactions
- Free Press Journal, NPCI pilots AI model to track stolen money. https://www.freepressjournal.in/tech/npci-pilots-ai-model-to-track-stolen-money-in-real-time-stop-digital-frauds
- Business Standard, Aadhaar face authentication crosses 2 billion. https://www.business-standard.com/india-news/uidai-aadhaar-face-authentication-crosses-2-billion-transactions-125081101734_1.html
- Outlook Traveller, DigiYatra mandatory for international transit at four airports. https://www.outlooktraveller.com/News/digiyatra-now-mandatory-for-international-transit-at-four-major-indian-airports
- ThePrint, AI-assisted X-rays flag 18,377 for TB testing in Delhi; 877 confirmed. https://theprint.in/india/ai-assisted-x-rays-flag-18377-people-for-tb-testing-in-delhi-slums-877-confirmed-study/3064481/
- Qure.ai "AI in Action" report (India AI Impact Summit, Feb 2026). https://www.qure.ai/news-press-coverages/qureai-unveils-aiin-action-report-at-india-ai-impact-summit-mapping-ais-ole-across-indias-public-healthcare-system
- Bhashini hosts Sarvam models. https://tele.net.in/digital-india-bhashini-division-enables-availability-of-advanced-ai-models-on-the-bhashini-platform/
- Sarvam-Translate (22 Indian languages). https://www.sarvam.ai/blogs/sarvam-translate
- Covington, Adams, Sargin, "Deep Neural Networks for YouTube Recommendations" (RecSys 2016). https://research.google/pubs/pub45530/

---

## Appendix — arithmetic check log (Python, natural log, sigmoid σ(z) = 1/(1+e^−z))

```
σ(2.4)=0.9168  σ(-1.2)=0.2315  σ(-0.8)=0.3100  σ(0.4)=0.5987  σ(4.4)=0.9879
σ(0.9)=0.7109  σ(0)=0.5  σ(1.5)=0.8176  σ(-0.5)=0.3775  σ(-2.4)=0.0832  σ(0.2)=0.5498
Day23: Ravi(4,7)->h=(1.5,2) z=1.5 p=0.8176 | Sita(6,3)->h=(1.5,0) z=-0.5 p=0.3775 | Kiran(1,8)->h=(0,1.5) z=-0.5 p=0.3775
Sleep mountain: L=3:0 5:2 7:4 8:3 9:2 10:1 11:0
Log loss: -ln(.917)=0.087  -ln(.5)=0.693  -ln(.378)=0.974  -ln(.05)=2.996
Priya GD: p=0.5, grads (w1,w2,b)=(-1.0,-0.3,-0.5); lr .1 -> (0.9,4.03,-3.95), z=0.268, p=0.5666, loss 0.568; w1-only: p=0.5498, loss 0.598
Parabola (w-3)^2 from 0: lr .25 -> 1.5,2.25,2.625,2.8125,2.906 ; lr 1 -> 6,0,6,0 ; lr 1.1 -> 6.6,-1.32,8.184,-3.22,10.47
Backprop Sita: d_out=-0.6225; grads v1=-0.934 v2=0 c=-0.6225 w(S->h1)=-3.735 w(L->h1)=-1.867 b1=-0.6225 (h2 all 0)
  lr .02 -> w(S->h1)=1.0747 w(L->h1)=0.5373 b1=-5.9876 v1=1.0187 c=-1.9876 ; Sita h1=2.0727 z=0.124 p=0.5309 loss 0.633
  Ravi 0.8176->0.8932 ; Kiran 0.3775->0.3805
```
