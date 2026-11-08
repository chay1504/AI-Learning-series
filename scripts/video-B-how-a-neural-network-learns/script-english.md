# Video B: "How a Neural Network Learns" (English rendering for review)

**Series:** AI Learning Series, **Day 10** on the channel. This covers plan Days 25–28: activation function, loss function, gradient descent and backpropagation.
**Recording script:** `script-telugu.md`. This file is a faithful English rendering of it, with the same segments, timestamps and board cues. It is for checking content and accuracy. Do not record from it.
**Runtime:** ~24:06 (≈ 24.1 min) estimated, from 4,217 spoken words at 175 wpm (his measured average).
**Legend:** ⏱ timestamp (start–end) · 🎙 what he says · 🖊 what to draw, write or show (in order)

> **Production note on numbering:** Video A ("Inside a Neural Network", plan Days 21–24) is assumed to go out as **Day 9**, so this video opens as **Day 10**. If the channel numbering changes, update the day number in three places: segment A, segment L (the "only 10 videos" line) and the title.

---

## [A0] Cold-open pitch
⏱ **00:00 – 00:07**

🎙
> If you want to learn AI from the basics, from scratch, subscribe to our channel. Let's dive into the video.

🖊
- Face to camera. No board yet. Channel logo sting.

---

## [A] Welcome + headline promise
⏱ **00:07 – 00:21**

🎙
> Hey guys, welcome back to AI Learning Series Day 10! We've already reached Day 10, you see. Today's topic is very interesting: how does a neural network actually learn? How a neural network learns. That's exactly what we'll see today.

🖊
- Title card: **AI Learning Series · Day 10 · How a Neural Network Learns**

---

## [B] Recap of Video A + catch-up
⏱ **00:21 – 02:02**

🎙
> First, let's recap once. In the last video we entered deep learning. On Day 2 we drew circles, right? AI, inside it ML, inside that DL. Last video we went into that innermost circle.
>
> Then we saw what an artificial neuron is. Inputs come in, it multiplies each input by a weight, adds them all, adds a bias, passes that through an activation, and gives one output. Inputs × weights + bias → activation → output. That simple. And the Student D calculation from Day 7 (4 hours of study, 80% attendance, z = 2.4, 91.7% pass) was already one neuron. We saw that last time.
>
> Then layers: input layer, hidden layer, output layer. We drew a small network too: study hours and sleep hours go in, two hidden neurons, one output. That network has 9 numbers in total. Those are the weights and biases. These are the knobs of the network, you see.
>
> And at the end of the last video I asked you a question, right? Where do these weights actually come from? On Day 7 we *assumed* 0.8, 0.04 and −4. But in real life nobody types them in. The machine finds them by itself. How does it find them? Today's video is the answer to that.
>
> Remember one more person: Sita. She studied 6 hours but slept only 3 hours. What did our network say? 38% pass, so "fail". And the twist, remember? Sita actually passed. That means the network was wrong. How does the network learn from this mistake? By the end of this video, you yourselves will calculate it.
>
> If you haven't watched Day 1 to Day 9, especially the last video, please watch them once and come back. This video is its continuation. You'll understand it much more clearly.

🖊
1. Quick redraw (or flash Video A's final board): three nested circles **AI ⊃ ML ⊃ DL**, with DL highlighted.
2. One neuron: two arrows in (x1, x2) → circle (Σ | σ) → arrow out. Write **inputs × weights + bias → activation → output**.
3. The Video A network: **S, L → h1, h2 → output**, with "9 knobs = weights + biases" written beside it.
4. Write the question big: **"Weights ela vasthayi?" / "Where do the weights come from?"** and circle it.
5. Sita card: **Sita: studied 6 h, slept 3 h → network says 38% pass ✗ (actually PASSED)**. Leave this card in a corner of the board for the rest of the video.

---

## [C] Agenda
⏱ **02:02 – 02:18**

🎙
> So what are we going to discuss today? First is the activation function. Second is the loss function. Third is gradient descent. Fourth is backpropagation. Only when these four come together does a network learn. They're like a chain: if one is missing, the others don't work.

🖊
- Write with pen, numbered:
  1. Activation function
  2. Loss function
  3. Gradient descent
  4. Backpropagation
- Draw a bracket joining all four: "= how a network learns".

---

## [E] Reassurance + stakes + notes
⏱ **02:18 – 02:49**

🎙
> What do many people think? "What is this, anna, gradient descent, backpropagation... even the names are scary. There'll be maths, we won't understand." Right? Don't be afraid at all. Today I won't use even one calculus formula. I'll explain with drawings, with our same students example and with small numbers. After listening you'll say, "Is that all, anna? We thought it was very hard."
>
> Every deep learning model, whether it's ChatGPT or face unlock, is built and trained with these four concepts. So they're very, very important. Everyone, take notes.

🖊
- Small sticky note on screen: **"No calculus today. Drawings + small numbers only."**

---

## [F] CONCEPT 1: Activation function

### F1. Announce + definition + name unpack
⏱ **02:49 – 03:39**

🎙
> So the first topic is the activation function. I'm showing the definition on screen. Write it down.
>
> *"An activation function is a function applied to a neuron's weighted sum (z). It decides the neuron's output and adds non-linearity, so the network can learn curved, complex patterns."*
>
> What does that mean? Last video, a neuron had two steps, right? Step one: the weighted sum, z = w1x1 + w2x2 + b. Step two: we send that z into a function. The function in that second step is what we call the activation function. It's in the name itself: "activation" means it decides how much the neuron gets activated, how much output it gives.
>
> The second keyword is **non-linearity**. This is the most important word here. What does linear mean? Linear means a straight line. Non-linear means something that isn't a straight line: a curve, a bend.

🖊
1. Definition card (English) on screen.
2. Redraw the neuron circle split in two: left half **Σ "z = w1x1 + w2x2 + b"**, right half **"f(z) ← activation function"**. Box the right half in red.
3. Underline **"non-linearity"** in the definition. Next to it, draw a straight line labelled "linear" and a wavy curve labelled "non-linear".

### F2. Why we need a bend: the sleep "sweet spot"
⏱ **03:39 – 04:24**

🎙
> For example, take sleep. If a student sleeps 3 hours, they're sleepy in the exam and perform badly. 5 hours, a little better. 7 hours, perfect, fresh. And what if they sleep 11 hours? Sleeping more doesn't keep making it better, right? They won't wake up in time for the exam and there's no time left to study. So if we draw a graph, what does it look like? It goes up, peaks at 7, then comes down again. Like a hill, a mountain shape.
>
> Now a question: can we draw this mountain with one straight line? What do you think? No. A straight line always goes up, or always goes down. It never turns in the middle. Lots of things in the real world are like this. They're not straight lines.

🖊
1. Axes: x = **sleep hours (3 to 11)**, y = **exam performance**.
2. Plot rough dots at 3 (low), 5 (mid), 7 (peak), 9 (mid), 11 (low). Join them into a mountain peaking at 7.
3. Overlay a straight ruler line in a different colour. Write **"✗ a straight line can't do this"**.

### F3. Without activation, layers collapse (the one worked example for this concept)
⏱ **04:24 – 05:22**

🎙
> Now a very interesting point. What happens without an activation function? The neuron only multiplies and adds, and that's always a straight line. So you might doubt: "Anna, one neuron is a straight line, but if we put 100 layers, won't a curve come?" No, it won't. I'll show you.
>
> Layer 1 multiplies the input by 2 and adds 1. Layer 2 multiplies that by 3 and subtracts 2. Suppose x = 4. Layer 1: 2 × 4 + 1 = 9. Layer 2: 3 × 9 − 2 = 25. Now take one single layer, 6x + 1. 6 × 4 + 1 = 25. The same answer! Whatever x you put, it comes out the same. That means the two layers together turned into one straight line. Even with 100 layers it's the same: without activation, everything collapses into one layer. No point in going deep.
>
> So without activation functions, the "deep" in deep learning has no meaning. Remember this: the activation function gives the network its bend.

🖊
1. Two boxes with arrows: **x → [×2 +1] → h → [×3 −2] → out**.
2. Under it, write: **x = 4 → 9 → 25**.
3. Then one box: **x → [×6 +1] → out**, and **6 × 4 + 1 = 25 ✔**.
4. Big stamp: **"2 layers without activation = 1 straight line!"**
5. (Optional, small, for curious viewers: "3(2x + 1) − 2 = 6x + 1".)

### F4. ReLU
⏱ **05:22 – 06:51**

🎙
> So now let's look at two famous activation functions. The first is **ReLU**. Full form: Rectified Linear Unit. Write it down: ReLU(z) = max(0, z). What does that mean? If z is positive, it gives out the same number. If it's negative, it gives 0. That's all. That is ReLU. For example, ReLU(1.5) = 1.5, and ReLU(−1) = 0.
>
> An analogy: on our houses there's a water tank on the terrace, right? It has an overflow pipe. As long as the water level is below the pipe, not a single drop comes out. Zero. As soon as it crosses the pipe level, however much extra water there is comes out. ReLU is just like that.
>
> Remember Sita from the last video? Sita's h2 neuron, the "did she rest enough" neuron, got a sum of −1. What did ReLU do? It made it 0. That neuron switched off. That was ReLU.
>
> Why is ReLU famous? It's very simple and very fast. In hidden layers it's what people use by default, you see.
>
> Now a doubt should come to you: "Anna, ReLU is also made of straight lines, right? One flat line, one slanted line. So how is it non-linear?" Good question. Where those two lines meet, at 0, there's a bend, right? That bend is the magic. One ReLU gives one bend. Many ReLU neurons together give many bends, and then you can draw almost any shape. Even our sleep mountain: combine two ReLU neurons and you get exactly that mountain shape, peaking at 7 hours. Look at the screen.

🖊
1. Definition card: **ReLU (Rectified Linear Unit): ReLU(z) = max(0, z). Positive → same number; negative → 0.**
2. Small axes: flat line along 0 for negative z, then a 45° ramp from 0. Label **max(0, z)**.
3. Mark two points: **1.5 → 1.5** and **−1 → 0 (Sita's h2: OFF)**.
4. Quick doodle: a water tank with an overflow pipe, with "below pipe → 0" and "above → flows".
5. Circle the corner at 0 and write **"bend = non-linear"**.
6. Show the sleep mountain again with the caption **"2 ReLU neurons → this shape"**. Small text for pause-and-note viewers: *score(L) = ReLU(L − 3) − 2 × ReLU(L − 7), for L = 3 to 11 → 0, 2, 4 (peak at 7), 3, 2, 0.*

### F5. Sigmoid (formula shown once) + Video A callback
⏱ **06:51 – 07:45**

🎙
> The second is **sigmoid**. This one isn't new for us: we saw it on Day 7 in logistic regression. The formula, once, on screen: σ(z) = 1 / (1 + e^(−z)), where e is about 2.718. Don't stress about the formula. I'm showing it just once.
>
> Simply put, sigmoid takes any number and squeezes it between 0 and 1. A big positive number comes out close to 1, a big negative number close to 0, and z = 0 gives exactly 0.5. Student D: z = 2.4 gives 0.917. It's like a fan regulator: smooth from slow to full speed. It never goes above full and never below zero. Or think of it as a confidence meter from 0% to 100%.
>
> And remember from last video: sigmoid gives a **probability**, like 0.917, and the 50% **threshold**, like our 35-marks pass mark, makes the pass/fail decision. That probability is exactly what the loss function will check next.

🖊
1. Formula card (the only time it is shown): **σ(z) = 1 / (1 + e^(−z)), e ≈ 2.718**.
2. Axes: an S-curve between dashed lines at 0 and 1. Mark **(0, 0.5)** and **(2.4, 0.917) "Student D"**.
3. Two boxes side by side: **[sigmoid → 0.917 = probability]** → **[threshold 50% → PASS (1)]**. Write "≠" between "probability" and "label".
4. Small note: **35 marks = pass mark ↔ 50% threshold**.

### F6. Where each is used + name-drops + mini-recap
⏱ **07:45 – 08:32**

🎙
> So where does ReLU go and where does sigmoid go? Mostly ReLU in hidden layers. If you need a yes/no, pass/fail at the output, sigmoid. Our network is exactly like that: ReLU in the hidden layer, sigmoid at the output. Don't think "sigmoid was used on Day 7, so it must be the best". If you put sigmoid in many hidden layers, learning becomes slow. That's one reason ReLU became the default.
>
> There are more activation functions too, like tanh, softmax and GELU. Transformer models like GPT use GELU-type ones inside. Just know the names. We're not going deep into them now.
>
> Simple: the small bend that comes after the weighted sum is the activation function. ReLU turns negatives into 0. Sigmoid squeezes everything between 0 and 1. Without it, all the layers become one straight line. That simple.

🖊
1. Redraw the Video A network. Write **ReLU** under the hidden neurons and **sigmoid** under the output neuron.
2. A side list titled "names only": **tanh · softmax · GELU**.
3. One-line recap card: **Activation = the bend after the weighted sum. ReLU: negatives → 0. Sigmoid: squeeze to 0–1.**

---

## [H] CONCEPT 2: Loss function

### H1. Announce + definition + exam-paper analogy
⏱ **08:32 – 09:19**

🎙
> So the activation function is done. Now the network gives a prediction. But is that prediction right or wrong? And how wrong? To measure that, the next concept is the **loss function**. Write down the definition.
>
> *"A loss function measures how far the model's prediction is from the true answer (the label). It gives a single number: 0 means a perfect prediction, and a bigger number means a worse one."*
>
> What does that mean? Think of exam paper correction. The teacher has an answer key. She compares your answer with the answer key and tells you how many marks you lost. Here, what's the answer key? The label. In supervised learning we saw that we basically leak the answer to the model, right? How far the prediction is from that true answer, that is the loss.

🖊
1. Definition card (English).
2. Doodle: an answer sheet beside an **answer key**, with red marks. Arrow: **"compare → marks lost = loss"**.
3. Write **label = answer key** under it.

### [G] Mid-roll CTA (cuts in mid-concept, D7 style)
⏱ **09:19 – 09:51**

🎙
> Sorry for interrupting the video in the middle. Pause this video for one second and hit like. And click the three dots and hit hype. When you hype it, our video reaches many more people, and many more beginners like you learn. Most of the people watching this series still haven't subscribed. Every like and every subscription you give pushes our whole team to make more videos like this. Many of you are saying "Anna, don't slow the series down, bring the next videos fast." We will, for sure. But we need all your support.

🖊
- Like / three-dots → **Hype** / Subscribe animation. Keep the loss definition card visible underneath so the cut back is seamless.

> **Note:** his usual stat is "90% of viewers are not subscribed". Only say a number if YouTube Studio supports it on the day of recording; otherwise keep the generic line above.

### H2. Single number, lower is better + the two types
⏱ **09:51 – 10:41**

🎙
> So, back to loss. One more example: Google Maps shows "destination 3 km away", right? That 3 km is the loss. If it's 0 km, you've arrived. What's our goal? To reduce the loss. Training, put simply, means reducing the loss again and again.
>
> There are different loss functions for different problems. Remember Day 6? Regression gives a number and classification gives a category. For **regression**, like predicting marks or a house price, we use **squared error**. On Day 6 we saw the house: actual price 55 lakhs, predicted 50 lakhs, an error of 5 lakhs. We called that the residual. We square that error and take the average over all examples. That's MSE, mean squared error. On Day 6 I only told you the name. Now you know what it's for.
>
> For **classification**, like our pass/fail, we use **log loss**, also called binary cross-entropy.

🖊
1. Google Maps pin doodle: **"3 km away" = loss** → **"0 km = perfect"**. Arrow down: **Goal: loss ↓**.
2. Two-column card:
   - **Regression (numbers) → squared error / MSE** (house: 55L actual vs 50L predicted → error 5L)
   - **Classification (categories) → log loss (binary cross-entropy)**

### H3. Log loss with the student numbers (the one worked example for this concept)
⏱ **10:41 – 11:47**

🎙
> In pass/fail, the model gives a probability, right? We check how much probability the model gave to the correct answer. The formula's on screen: loss = −ln(probability given to the correct answer). ln means natural log. You don't need to remember the formula. I did it on a calculator. Just look at the numbers. If you check it on a calculator, use the "ln" button, not the "log" button.
>
> Student D passed, and the model said 91.7%. Loss: 0.087, very small. Another student passed, and the model said 50-50. Loss: 0.69. Sita passed, and the model said 37.8%. Loss: about 0.97. And one more student passed, but the model very confidently said "only 5%, definitely fail". Loss: 3.0. Very high.
>
> Look: going from 50% to 5% didn't double the punishment. It became more than 4 times. What log loss does is this: if you're confidently wrong, it gives a very big punishment.
>
> In our friend group there's always one guy who says "100% I'll pass, guaranteed", and then fails. How embarrassing is that for him? Another one said "don't know, 50-50" and failed. Not so embarrassing. Log loss works the same way.

🖊
1. Formula card (small): **Log loss = −ln(probability given to the correct answer)**. Footnotes: *ln = natural log (the "ln" key on a calculator, not "log"). If the truth is Fail, use 1 − P(pass).*
2. Table (truth = Pass for every row):

   | Student | Model's P(pass) | Loss |
   |---|---|---|
   | D | 0.917 | 0.087 |
   | "50-50" student | 0.50 | 0.69 |
   | Sita | 0.378 | ≈ 0.97 |
   | "Confidently wrong" | 0.05 | 3.0 |

3. Sketch the curve: x = probability given to the correct answer (0 → 1), y = loss. It shoots up near 0 and touches about 0 at 1. Put the four dots on it.
4. Arrow from 0.69 to 3.0: **"more than 4×!"**

### H4. Doubt: loss vs accuracy + mini-recap
⏱ **11:47 – 12:40**

🎙
> Now many of you will ask: "Anna, loss and accuracy are the same thing, right?" Don't get confused. They're not. On Day 6 we saw accuracy: 90 correct out of 100 is 90%. Accuracy only counts right or wrong. If the model says 51% or 99% and both students pass, it's the same for accuracy. But for loss it's different: 99% gives a very small loss and 51% a bigger one. Loss tells you *how* right or *how* wrong, smoothly. That smoothness is exactly what our next concept, gradient descent, needs. So remember: we **train** on loss and **report** accuracy.
>
> One more thing. Loss isn't for one student. We take the average over all the students in training, because the model should be good for everyone, not just for Sita.
>
> Simple: the loss function says, in one number, how wrong the prediction is. 0 means perfect. Squared error for regression, log loss for classification.

🖊
1. Two boxes:
   - **Accuracy:** counts right/wrong (51% pass and 99% pass → both "correct")
   - **Loss:** how right or wrong (99% → tiny loss; 51% → bigger loss)
2. Write: **Train on LOSS · Report ACCURACY**.
3. Write: **Total loss = average over all students**.
4. Recap card: **Loss = one number for "how wrong". 0 = perfect. Regression → squared error. Classification → log loss.**

---

## [I] CONCEPT 3: Gradient descent

### I1. Announce + definition + name unpack
⏱ **12:40 – 13:17**

🎙
> Now we know the loss. Sita's loss is 0.97. What should we do now? Reduce the loss. How? We have 9 knobs, right, the weights and biases. Which knob do we turn, which way, and by how much? The answer is **gradient descent**. Personally, I find this a really interesting concept.
>
> Write down the definition. *"Gradient descent is an optimization method that repeatedly adjusts the model's weights and biases in small steps, in the direction that reduces the loss."*
>
> It's in the name itself. Gradient means slope: which way the ground slopes and how steep it is. Descent means going down. Gradient descent means feeling the slope and walking down.

🖊
1. Definition card (English).
2. Split the name on the board: **GRADIENT = slope (direction + steepness)** | **DESCENT = going down**.

### I2. Walking down a hill in the fog: the valley picture (drawing first)
⏱ **13:17 – 13:52**

🎙
> Imagine this once. You're on Ananthagiri Hills at night. Full fog, no torch. You have to come down to the village. You can't see the path. What will you do? You'll feel which way the ground slopes under your feet. You'll take one small step towards the downward side. Feel again, step again. Like that you'll come all the way down. This is gradient descent.
>
> Here, what's the hill? The loss. More height means more loss. The bottom of the valley is minimum loss, the best weight. The slope under your feet is the gradient. Each step is a weight update.

🖊
1. Draw a big **U-shaped valley**. x-axis **"weight w"**, y-axis **"loss"**. Mark the bottom with ⭐ **"best w (minimum loss)"**.
2. Put a stick figure (or a ball) high on the left slope. Draw a short tangent line under its feet labelled **"slope = gradient"**.
3. Draw small hops down the slope: step → step → step → ⭐.
4. Fog doodle over the top: "can't see the bottom, only feel the slope".

### I3. The direction rule + update rule in words
⏱ **13:52 – 14:25**

🎙
> Now a very important rule. Write it down: **always move opposite to the slope.** If the slope is positive, increasing the weight increases the loss, so decrease the weight. If the slope is negative, increasing the weight decreases the loss, so increase the weight.
>
> The rule in words: new weight = old weight − (step size × slope).
>
> "Anna, minus and minus, what's this confusion?" Why the minus in the formula? Because we always go opposite to the slope. If the slope is −1, minus times minus is plus, so the weight goes up. That's all.

🖊
1. On the valley: at a point on the **left** slope, write **"slope −" → arrow pointing RIGHT → "increase w"**. At a point on the **right** slope, write **"slope +" → arrow pointing LEFT → "decrease w"**.
2. Rule box (keep it visible): **new weight = old weight − (step size × slope)**.
3. Mini note: **slope −1 → − × − = + → weight goes UP**.

### I4. Step size = learning rate (named, details deferred) + Amma's salt
⏱ **14:25 – 15:23**

🎙
> Now the step size. How big a step should we take? That step size is what we call the **learning rate**. Amma puts salt in the curry, right? She tastes it, says "a bit bland", adds a pinch, and tastes again. What if she throws in a whole fistful at once? The curry is spoiled. Overshoot. And if she adds one grain at a time? By the time the curry is ready it's night. So the step size has to be right. The details of the learning rate, what happens if it's too big or too small, I'll explain in the next episode along with epochs and batches. For now just remember: learning rate = step size.
>
> But don't take this as the exact example. Amma changes one ingredient at a time, by feel. Gradient descent changes **all** the weights at once, each with its own slope, calculated exactly. And once salt goes in you can't take it out, but a weight can move both ways, up or down.

🖊
1. Doodle: a pot of curry with a pinch of salt (✔ "small step") and a fistful of salt (✘ "overshoot").
2. On the valley: one tiny hop vs one giant jump over the bottom to the far side.
3. Write: **learning rate = step size → details next episode (with epochs and batches)**.
4. Disclaimer chip: **GD = all knobs at once, each by its own slope.**

### I5. One real update: student Priya (the one worked example for this concept)
⏱ **15:23 – 16:54**

🎙
> Don't worry about the maths. Let's go slowly. Take the Day 7 neuron: w1 = 0.8, w2 = 0.04, b = −4. A new student, Priya, studied 2 hours and has 60% attendance. She actually passed.
>
> Step 1, forward: z = 0.8 × 2 + 0.04 × 60 − 4 = 1.6 + 2.4 − 4 = 0. Sigmoid of 0 is 0.5. The network said "50-50, I don't know."
>
> Step 2, loss: −ln(0.5) = 0.69.
>
> Step 3, slope. Here's a shortcut: when sigmoid and log loss come together, the slope comes out very simple: (prediction − truth) × input. I'm not going into the proof; the machine calculates it. The slope for w1 = (0.5 − 1) × 2 = −1. Negative! So w1 should be increased.
>
> Step 4, update. Step size 0.1. New w1 = 0.8 − 0.1 × (−1) = 0.8 + 0.1 = 0.9.
>
> Step 5, check: z = 0.9 × 2 + 2.4 − 4 = 0.2. Sigmoid gives 0.55. Loss is 0.60. The loss came down from 0.69 to 0.60! We turned one knob and the loss dropped. This is gradient descent. If you have a calculator, check it yourselves.
>
> I showed only w1 to keep it simple. Actually the machine updates w2 and b too, all at once, the same way. And this was one step. In real training it takes steps like this thousands of times, even lakhs of times. The weights we assumed on Day 7: in reality the machine finds them exactly like this, step by step. That's the answer to the last video's question!

🖊
1. Neuron card: **w1 = 0.8 (study), w2 = 0.04 (attendance), b = −4**. Student card: **Priya: 2 h, 60%, actually PASSED (truth = 1)**.
2. Write the steps one by one as he speaks:
   - **① Forward:** 0.8×2 + 0.04×60 − 4 = 1.6 + 2.4 − 4 = **0** → σ(0) = **0.5**
   - **② Loss:** −ln(0.5) = **0.69**
   - **③ Slope (shortcut):** (prediction − truth) × input = (0.5 − 1) × 2 = **−1** → "negative → increase w1"
   - **④ Update:** 0.8 − 0.1 × (−1) = **0.9**
   - **⑤ Check:** 0.9×2 + 2.4 − 4 = **0.2** → σ = **0.55** → loss **0.60** ✔
3. On the valley drawing, move the ball one hop down and write **0.69 → 0.60**.
4. Note in a box: *"Shortcut works for sigmoid + log loss. Machine does w2 and b at the same time."* Small grey footnote (do not read out): *"w2 with raw 60% gives slope −30, too big a jump. Real projects scale attendance to 0.6 first. Next episode."*

### I6. Doubts + mini-recap
⏱ **16:54 – 17:35**

🎙
> "Anna, do we get the perfect answer in one step?" No. Small, small steps, many times. "Are gradient descent and backpropagation the same?" I'll clear that up in the next concept.
>
> One more doubt: "Will it always reach the very bottom, the best answer?" Not guaranteed. A real loss valley isn't one neat U like my drawing. It has many small dips, and sometimes it stops in a dip that isn't the deepest. But in big networks, in practice, it reaches a good enough point. Real libraries also use smarter versions, like Adam. Same idea: slope, step, repeat.
>
> Simple: look at the slope, take a small step opposite to it, and keep reducing the loss. That is gradient descent.

🖊
- Quick sketch beside the U: a wavy valley with two dips, a ball resting in the shallower one. Caption: **"real valley: many dips → not always the deepest, usually good enough"**. Chip: **"Adam = a smarter GD (name only)"**.
- Recap card: **Gradient descent = feel the slope → step opposite to it → loss ↓ → repeat.**

---

## [J] CONCEPT 4: Backpropagation

### J1. The problem + definition + name unpack
⏱ **17:35 – 18:30**

🎙
> Now there's a problem. In Priya's example there was only one neuron, so we directly knew the input for w1. But in our 9-knob network? Take a first-layer weight, the S → h1 wire. Its effect goes through h1 and then through the output. The output came out wrong, but how much of that mistake belongs to the S → h1 weight? We can't see it directly. And big networks have crores of weights. How do we find the slope for every single weight? The answer is **backpropagation**.
>
> Write down the definition. *"Backpropagation is the method a neural network uses to calculate how much each weight and bias contributed to the error, by passing the error backward from the output layer to the earlier layers. Gradient descent then uses these amounts (the gradients) to update the weights."*
>
> It's in the name: "back" means backwards, "propagation" means passing it along, spreading it. Sending the error backwards. People call it "backprop" for short.

🖊
1. Redraw the Video A network: **S, L → h1, h2 → output**. Put a big **"?"** on the S → h1 wire: "how much of the mistake is this wire's?"
2. Definition card (English).
3. Split the name: **BACK = backwards** | **PROPAGATION = passing along**.

### J2. Analogy: cricket coach's post-match analysis
⏱ **18:30 – 19:10**

🎙
> Think of a cricket match. India lost by 30 runs. After the match the coach does an analysis. The result is the loss. The coach traces it backwards: the bowler in the last overs gave away a lot of runs, so more blame. One batsman didn't even get to bat, so zero batting blame for him. Whoever contributed how much gets that much blame. After that, everyone changes their practice a little. Backprop is the same thing: **blame assignment**.
>
> But don't take this as the exact example. In backprop nobody is dropped from the team. It never removes a neuron. It nudges every weight a little. And the coach goes by opinion, while backprop calculates with exact numbers.

🖊
1. Scoreboard doodle: **"Lost by 30 runs" = loss**.
2. Red arrows going backwards from the scoreboard to player stick figures: **"bowler: big blame"**, **"didn't bat: 0 blame"**.
3. Write **Backprop = blame assignment**, and a chip: *"Nobody dropped. Everyone nudged a little."*

### J3. Sita's backward pass (the one worked example for this concept)
⏱ **19:10 – 20:28**

🎙
> Don't worry. Slowly. Sita studied 6 hours and slept 3 hours. Forward pass: h1 = 1.5, so it's on. h2's sum was −1, and ReLU made it 0, so it's off. Output: 37.8%. The truth: she passed. Loss about 0.97.
>
> Step 1, the error at the output: prediction − truth = 0.378 − 1 = −0.622. The minus means "the output should have been higher".
>
> Step 2, the output-layer wires. Blame for each wire = error × the value that came along that wire. h1 → output: −0.622 × 1.5 = −0.93. h1 sent a value, so it gets blame. h2 → output: −0.622 × 0 = 0. h2 was silent and sent nothing, so its blame is zero, like the batsman who didn't get to bat.
>
> Step 3, back into the hidden neurons. The blame reaching h1 = error × the h1 → output weight, which is 1: −0.622 × 1 = −0.622. h1 was on, so ReLU lets it through. For h2 it's also −0.622 × 1, but h2 was off, so ReLU blocks it. Blame: 0.
>
> Step 4, the first-layer wires. S → h1: −0.622 × 6 = −3.73. That's the biggest blame, because study hours was 6, a big input. L → h1: −0.622 × 3 = −1.87. All the wires on h2's side: 0. See? Whoever contributed more gets more blame. That's backprop.

🖊
1. Network in **black** with Sita's forward numbers: inputs **6, 3** → **h1 = 1.5 (ON)**, **h2: −1 → 0 (OFF)** → output **37.8%**.
2. At the output in **red**: **"Truth = PASS (1). Error = 0.378 − 1 = −0.622"** → "should be higher".
3. **Red arrows right-to-left** along each wire, written as he speaks:
   - h1 → output: **−0.622 × 1.5 = −0.93**
   - h2 → output: **−0.622 × 0 = 0** ("h2 was off")
   - into h1: **−0.622 × 1 (its output weight) = −0.622 ✔ passes (ON)**; into h2: **−0.622 × 1 → red ✗ "blocked by ReLU" → 0**
   - S → h1: **−0.622 × 6 = −3.73** (circle it: "biggest blame")
   - L → h1: **−0.622 × 3 = −1.87**
   - all of h2's input wires: **0**
4. Write the rule at the top: **blame on a wire = error arriving × value it carried**.

### J4. Gradient descent applies the update → Sita flips to pass
⏱ **20:28 – 21:15**

🎙
> Now, what are these blame numbers? They're exactly the gradients, the slopes. Step 5: now gradient descent comes in: new = old − step size × blame. Step size 0.02. S → h1 goes from 1 to 1.075. h1 → output goes from 1 to 1.019. The full table is on screen. Pause and write it down.
>
> Step 6, forward pass again for Sita: 37.8% becomes 53%! It flipped from fail to pass. Loss: 0.97 down to 0.63.
>
> And here's an interesting thing. Ravi's prediction also changed: 81.8% to 89.3%. Kiran stays at about 38%. When the network learns from one student, it changes for everyone. That's why in real training we don't use just one student. We average the blame over many students and then update, so no single student drags the network too far.

🖊
1. In **green**, next to the old weights, using **new = old − 0.02 × blame**:

   | Parameter | Old | Blame | New |
   |---|---|---|---|
   | S → h1 | 1 | −3.73 | **1.075** |
   | L → h1 | 0.5 | −1.87 | **0.537** |
   | h1 bias | −6 | −0.622 | **−5.988** |
   | h1 → output | 1 | −0.93 | **1.019** |
   | output bias | −2 | −0.622 | **−1.988** |
   | all of h2's weights and bias, h2 → output | same | 0 | **unchanged** |

   Caption: "PAUSE & NOTE". Footnote under the table: *"bias blame = error arriving × 1 (a bias always carries 1)"*.
2. Forward again, in green at the output: **Sita 37.8% → 53% ✔ PASS · loss 0.97 → 0.63**.
3. Side box: **Ravi 81.8% → 89.3% · Kiran ≈ 38% (almost no change)** → "one lesson changes the network for everyone → average over many students".

### J5. Doubts + chain rule (name only) + mini-recap
⏱ **21:15 – 22:01**

🎙
> "Anna, in backprop does the data go backwards?" No. The inputs never change: Sita studied 6 hours, and that doesn't change. Only the error, the blame signal, goes backwards.
>
> "Are backprop and gradient descent the same?" Don't get confused. Backprop is the calculator: it works out how much blame each weight gets. Gradient descent is the update: it looks at that blame and changes the weights. Backprop computes, gradient descent updates.
>
> And don't think only the last layer learns. Blame reaches every layer. That's the power of backprop. The maths behind it is technically called the **chain rule**. That's just the name. We won't go into its formula in this series.
>
> Simple: look at the error at the output, go backwards layer by layer, and calculate each weight's share of the blame. That is backpropagation.

🖊
1. Two boxes with an arrow between them: **BACKPROP = calculator ("who gets how much blame")** → **GRADIENT DESCENT = update ("change the weights")**.
2. Chip: **Only the error flows backward. Inputs never change.**
3. Small grey text: *"maths name: chain rule (no formula in this series)"*.
4. Recap card: **Backprop = error at the output → backwards layer by layer → each weight's share of the blame.**

---

## [K1] The full "how a network learns" loop
⏱ **22:01 – 22:37**

🎙
> Now let's put all four together in one picture. This is the most important picture in this video. Write it down.
>
> One: **forward pass**. Inputs go through the layers, with activation functions, and give a prediction. Two: **loss**. Compare the prediction with the true answer: how wrong is it? Three: **backpropagation**. Send the error backwards and give each weight its blame. Four: **gradient descent update**. A small step opposite to the slope. Five: **repeat**. Forward again, thousands of times.
>
> When we build a neural network in an upcoming video, we'll write one line, model.fit(). Inside that one line, exactly this loop is running.

🖊
- In a corner (keep it there to the end), draw a circular loop with arrows:
  **① Forward pass → ② Loss → ③ Backprop → ④ Gradient-descent update → (repeat) ↺**
- Under ①: "activation functions live here". Under ④: "step size = learning rate".
- Sticky note: **model.fit() = this loop**.

---

## [K2] Video recap + comment quiz
⏱ **22:37 – 23:13**

🎙
> And that's it for the day! In this video we covered the activation function (ReLU and sigmoid), the loss function, gradient descent and backpropagation. All of this sits inside AI, in machine learning, in deep learning, in the training of neural networks.
>
> Now today's quiz. Tell me in the comments. One: what is ReLU(−5)? And ReLU(3)? Two: the weight is 2, the slope is +4 and the step size is 0.1. What's the new weight? Did it go up or down? Three: in Sita's case, why didn't the h2 → output weight change at all? Answer in one line. Let's see who's been listening properly.

🖊
1. Taxonomy line: **AI → ML → Deep Learning → training a neural network → {activation, loss, GD, backprop}**.
2. Quiz card:
   1. ReLU(−5) = ? ReLU(3) = ?
   2. weight 2, slope +4, step size 0.1 → new weight? Up or down?
   3. Sita: why did the h2 → output weight not change?
   *(Answers go in production notes. Don't show them on screen.)*

---

## [L] Outro
⏱ **23:13 – 24:06**

🎙
> If not everything is 100% clear in one viewing, don't worry. Backprop doesn't click for most people the first time. It didn't for me either. Watch it once more with the notes and it'll click.
>
> I'm putting all the notes, the definitions, drawings and numbers, in the description. Download them and revise.
>
> Today we said "repeat thousands of times", right? So what do we call each round? How many students' data do we give at once? And what happens if the step size is too big? In the next video: **epochs, batches and learning rate**. Whoever wants that video, like this one.
>
> And it's not late yet. Only 10 videos are done. If you sit for one day, you can cover them all. Add your friends to this AI Learning Series too. The more support we get, the better the videos we'll bring you.
>
> Thank you so much for watching. Signing off, Tech Boy Deepak.

🖊
- The loop drawing stays on screen.
- Lower-third: **"Notes in description ↓"**.
- End card: **Next: Epochs · Batches · Learning rate** + the previous-video tile (Video A / Day 9).
