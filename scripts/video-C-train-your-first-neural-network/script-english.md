# Video C: "Train Your First Neural Network" (English rendering for review)

**Series:** AI Learning Series, **Day 11** on the channel (Part 3 of the Deep Learning block). This covers plan Days 29–30: epochs, batches and learning rate (plus overfitting), then building and training a neural network in Keras on Google Colab.
**Recording script:** `script-telugu.md`. This file is a faithful English rendering of it, with the same segments, timestamps and board/Colab cues. It is for checking content and accuracy. Do not record from it.
**Runtime:** @@RUNTIME@@
**Legend:** ⏱ timestamp (start–end) · 🎙 what he says · 🖊 what to draw, write or show (in order) · 💻 what to show in Colab (block names match the notebook headings exactly)

> **Production note on numbering:** Video A = **Day 9** and Video B = **Day 10** are assumed, so this video opens as **Day 11**. If the numbering changes, update segment A, the "Day 9 / Day 10" callbacks (listed in production-notes §10), the "only 11 videos" line in L2 and the title.

---

## [A0] Cold-open pitch
⏱ **@@A0@@**

🎙
> Until now we drew the neural network on the board and calculated it by hand with a calculator. Today we're going to train that same network for real on a computer, right in front of your eyes. If you want to learn AI from the basics, from scratch, subscribe to our channel. Let's dive into the video.

🖊
- Face to camera. Quick 2-second flash of the Colab training output scrolling ("Epoch 1/100 … 10/10 …"), then the channel logo sting.

---

## [A] Welcome + headline promise
⏱ **@@A@@**

🎙
> Hey guys, welcome back to AI Learning Series Day 11! We've already reached Day 11, you see. Today's video is very special to me personally, because today we go from theory to practical. Train your first neural network. In the first half we'll see the important terms that come up in training. In the second half we'll build our own neural network in Google Colab and train it.

🖊
- Title card: **AI Learning Series · Day 11 · Train Your First Neural Network**
- Small badge: "Theory ➜ Practical 🛠️"

---

## [B] Recap of Days 9–10 + last quiz answers + catch-up
⏱ **@@B@@**

🎙
> So first, let's recap once. On Day 9 we drew a small network, right? Study hours and sleep hours go in, two hidden neurons, one output. 9 knobs in total, meaning weights and biases. I assumed all 9 of those knobs myself. With those guessed knobs, what did Sita get? She studied 6 hours but slept only 3. The network said 38%, it said fail. But Sita actually passed. You remember.
>
> On Day 10 we saw how a network learns. Remember this loop? One, forward pass: the prediction. Two, loss: how wrong. Three, backpropagation: who gets how much blame. Four, gradient descent: one small step opposite to the slope. In Priya's example, one step brought the loss down from 0.69 to 0.60. And at the end of the last video I said one thing: "this loop repeats thousands of times." I'm circling this repeat arrow. Today's whole video is about this one arrow, you see.
>
> Quick answers to the last video's quiz. One: ReLU(−5) = 0, ReLU(3) = 3. Two: weight 2, slope +4, step size 0.1. 2 − 0.1 × 4 = 1.6. The slope was positive, so the weight went down. Three: in Sita's case, why didn't the h2 → output weight change? h2 was off, its output was 0, it sent nothing, so its blame is zero. Congratulations to everyone who answered correctly in the comments.
>
> And at the end of the last video I asked three questions, right? What do we call each round? How many students' data do we give at once? What happens if the step size is too big? Today is exactly the answers to those three. I also made one more promise: "we'll write one line, model.fit(), and inside that line this same loop runs." Today we'll write that line ourselves and run it.
>
> If you haven't watched Day 9 and Day 10, please watch those two first and come back. Every step today stands on them.

🖊
1. Redraw (or flash) the Day 9 network: **S, L → h1, h2 → output**, with "9 knobs = weights + biases".
2. Sita card in a corner: **Sita: 6 h study, 3 h sleep → Day 9 guessed knobs: 38% ✗ (actually PASSED)**. It stays until K6.
3. Redraw the Day 10 loop: **① Forward → ② Loss → ③ Backprop → ④ Update → ↺**. Circle the **↺ repeat** arrow in red: "today = this arrow".
4. Quick card: Day 10 quiz answers **0 · 3 · 1.6 (down) · h2 = 0 → blame 0**.
5. The three questions from the Day 10 outro, numbered: **① each round = ? ② how many students at once = ? ③ step too big = ?**

---

## [C] Agenda
⏱ **@@C@@**

🎙
> So today's agenda, I'm writing it with the pen. First is the epoch. Second is the batch. Third is the learning rate. Fourth, what happens if there are too many epochs: overfitting. And last, today's main attraction: the build in Google Colab. We'll ask Sita again, this time with knobs the machine learned.

🖊
- Handwrite, numbered:
  1. Epoch
  2. Batch
  3. Learning rate
  4. Overfitting (too many epochs)
  5. 🛠️ Build in Colab → ask Sita again
- Draw arrows from items 1–3 to the three questions from segment B.

---

## [E] Reassurance + honesty beat + notes
⏱ **@@E@@**

🎙
> What many people think is, "Anna, Colab, code, Keras… we don't know programming, we can't do this," right? Don't be scared at all. Today I won't teach even one line as syntax. For every code block, I'll just tell you which drawing we've already made on the board it matches. The notebook link will be in the description. You just have to press "Run all".
>
> Let me tell you something honestly. The first time I trained a model, when lines like "Epoch 1/100, 10/10, loss…" were scrolling on the screen, I didn't understand a single bit of what was happening there. By the end of this video, you'll be able to read every number on that screen yourself. Settings like epochs, batches and learning rate are part of training every deep learning model, small model or big model. So everyone, take notes.

🖊
- Sticky note: **"No syntax lessons. Every code block = a drawing we already know."**
- Small screenshot of a Keras training log with a big "?" over it ("by the end of today you'll read every number").

---

## [F] CONCEPT 1: Epoch

### F1. Announce + definition + keyword
⏱ **@@F1@@**

🎙
> So the first topic: the epoch. In the last video we said "repeat", right? There's a unit for measuring that repeat. That's the epoch. I'm showing the definition on screen, write it down.
>
> *"An epoch is one complete pass through the entire training data. Training for 100 epochs means the network sees every training example 100 times."*
>
> What does that mean? If the network looks at every single student in our training data once, that's one epoch. Without leaving out even one. 100 epochs means it looks at the same students 100 times. The most important word here is "entire": all of the data. If it sees only part of the data, that's not an epoch.

🖊
1. Definition card (English).
2. Underline **"entire training data"** and write beside it: **"ALL students, once = 1 epoch"**.

### F2. Revision analogy + board (60 students)
⏱ **@@F2@@**

🎙
> To put it even more simply: before exams we do revision, right? First revision: the whole syllabus once. Second revision: the whole thing again. Third revision. In every revision something new makes sense, and we catch what we missed the first time. One revision = one epoch, you see. Reading one chapter isn't a revision, right? Only the whole syllabus counts as one round.
>
> Let's see it on the board. Suppose a class has 60 students. That's our training data. I'm drawing 60 dots. When the network has looked at all 60 of them once, that's Epoch 1. Again from the start: Epoch 2. Like this, Epoch 3, 4, 5. As the epochs go up, the loss keeps coming down little by little. Like the ball going down the valley on Day 10.

🖊
1. A grid of **60 small dots** labelled **"Training data = 60 students"**.
2. A big loop arrow around the whole grid: **"Epoch 1 = all 60, once"**.
3. A ladder to the right: **Epoch 1 → Epoch 2 → Epoch 3 → Epoch 4 → Epoch 5**, with a small falling line next to it: "loss ↓".
4. Small doodle: a notebook with "1st revision ✔ 2nd ✔ 3rd ✔" = "1 revision = 1 epoch".

### F3. Doubt + one-liner
⏱ **@@F3@@**

🎙
> Now you might have a doubt: "Anna, what's the use of showing the same students again and again? Isn't once enough?" It isn't. Because gradient descent takes small, small steps, right? In one round it doesn't reach the valley bottom. That's why it needs many rounds. So how many rounds? Is more always better? There's a twist in that; I'll tell you in the fourth topic.
>
> Simple: the network looking at all of the training data once, completely, is one epoch. That's what we call an epoch.

🖊
- Recap card: **Epoch = one full pass over ALL the training data.**
- Small sticky note: "More epochs = always better? → topic 4 🤔"

---

## [H] CONCEPT 2: Batch

### H1. Announce + definition + answer-sheet bundles
⏱ **@@H1@@**

🎙
> So the epoch is done. Now the second question: how many students' data do we give at once? In the last video, when the network learned from Sita alone, Ravi's prediction changed too, right? I said then that in real training it's not one person's blame: they average the blame of many students and then update. That group is called a batch. Write down the definition.
>
> *"A batch is a small group of training examples that the network processes together before making one update to its weights and biases. The batch size is the number of examples in each batch."*
>
> What does that mean? The network doesn't look at all 60 at once, and it doesn't look at them one by one either. It takes a small group, say 10 people. For those 10 it does the forward pass, the loss and backprop. It averages those 10 people's blame. Then it updates the 9 knobs once. One batch, one update. Remember this.
>
> Let me give you an example. A teacher corrects answer sheets, right? There are 60 papers. What she does is take 10 papers as one bundle. She corrects that bundle, notes the common mistakes ("lots of them lost marks on this one question"), and in the next class she changes how she teaches that a little. Then the next bundle. One bundle = one batch. The small change after each bundle = one update. When all 60 papers are done once = one epoch.
>
> But don't take this as the exact example. The teacher changes her teaching; the network changes its weights. And the network gets the same 60 papers again and again in every epoch.

🖊
1. Definition card (English). Underline **"before making one update"**.
2. Doodle: a stack of answer sheets tied into bundles of 10, a red pen, and a sticky note "common mistakes → adjust a little".
3. Write the mapping: **bundle = batch · small change after each bundle = 1 update · whole pile once = 1 epoch**.
4. Disclaimer chip: *"Teacher changes teaching; network changes weights. Same papers come back every epoch."*

### H2. Board: 60 students in batches of 10 (the rule)
⏱ **@@H2@@**

🎙
> Now on the board. I'm boxing those 60 dots in tens. Batch 1, 2, 3, 4, 5, 6. Six batches. Under each box, a spanner, meaning "update". So how many updates in one epoch? 6. Now write down this rule, it's very important:
>
> Updates per epoch = students ÷ batch size. Total updates = epochs × updates per epoch.
>
> 60 ÷ 10 = 6. If we do 5 epochs? 5 × 6 = 30 updates. See, it's just simple division. Technically, each update is also called an iteration, or a step. On Day 10 we took one step for Priya, right? That was one iteration, you see.
>
> And remember the Day 10 loop? Forward, loss, backprop, update. This loop goes round once for every batch. So in 5 epochs, this loop went round 30 times.

🖊
1. On the 60-dot grid, draw **6 boxes of 10**, labelled **Batch 1 … Batch 6 (batch size = 10)**.
2. Under each box, a small spanner icon 🔧 "update the 9 knobs" (6 spanners).
3. Loop arrow around all 6 boxes: **"1 epoch = 60 students = 6 updates"**.
4. Rule box (keep it visible, ✍️ "write it down"):
   **Updates per epoch = students ÷ batch size**
   **Total updates = epochs × updates per epoch**
   → **60 ÷ 10 = 6 · 5 epochs × 6 = 30 updates**
5. Write: **1 update = 1 iteration = 1 step**.
6. Next to the Day 10 loop in the corner, write: **"runs once per BATCH"**.

### H3. Three flavours + why batches + shuffling
⏱ **@@H3@@**

🎙
> Now, we can set the batch size to anything. With batch size 1, there's an update after every student: 60 updates per epoch. That's called stochastic gradient descent. Batch size 60, meaning the whole class as one batch: just one update per epoch. That's called batch gradient descent. In between, things like 10, 32, 64: mini-batch gradient descent. That's what everyone actually uses. You don't need to remember all the names; remembering "mini-batch" is enough.
>
> So why don't we give all the data at once? Two reasons. One: real projects have lakhs, crores of examples. They don't all fit in the computer's memory at once. If we give them in batches, the GPU processes each batch fast, in parallel. Two: instead of one update per epoch we get many updates, so learning starts sooner.
>
> And one small detail. Before every epoch it shuffles the students. Like a teacher mixing all the papers each round and tying new bundles. So in every epoch, each batch gets different students.

🖊
1. Side table:

   | Batch size | Updates per epoch (60 students) | Name |
   |---|---|---|
   | 1 | 60 | stochastic GD |
   | 10 | 6 | **mini-batch GD ✔ (what everyone uses)** |
   | 60 (whole class) | 1 | batch GD |
2. Two reason icons: 🧠💾 "crores of examples don't fit in memory → GPU does a batch in parallel" · ⏩ "more updates per epoch → learns sooner".
3. Small shuffle doodle: two bundles with arrows crossing → **"shuffle before every epoch"**.

### H4. Doubts + one-liner
⏱ **@@H4@@**

🎙
> Lots of people get confused here: epoch, batch, iteration. Don't get confused. A batch is one piece of the data. An iteration is one update made with that one piece. An epoch is all of the data once. One epoch has many iterations.
>
> Another doubt: "Anna, what if it's 60 students and batch size 32?" We can't divide 60 by 32 exactly, right? It's nothing, very simple. The first batch has 32, and the last batch has the remaining 28. So 2 batches. You round up, you see. And in Keras, if we don't specify a batch size, it uses 32 by default.
>
> Simple: the small group of students the network looks at before updating the knobs once is a batch. That's what we call a batch.

🖊
1. Three boxes: **BATCH = a slice of the data** → **ITERATION = 1 update on 1 batch** → **EPOCH = all the data once (many iterations)**. Write "కన్ఫ్యూజ్ అవ్వద్దు ⚠️" above.
2. Write: **60 ÷ 32 → batches of 32 + 28 → 2 batches (round UP)**. Chip: "Keras default batch size = 32".
3. Recap card: **Batch = the small group seen before ONE update. Batch size = how many in it.**

---

## [I] CONCEPT 3: Learning rate

### I1. Announce + definition + "not computer speed"
⏱ **@@I1@@**

🎙
> Now the third question: what happens if the step size is too big? On Day 10 we saw the gradient-descent rule, right: new weight = old weight − step size × slope. The official name for that step size is the learning rate. Write down the definition.
>
> *"The learning rate is a number that controls how big a step gradient descent takes each time it updates the weights. If it is too small, learning is very slow. If it is too large, the steps overshoot the lowest point, and the loss can bounce around or even blow up."*
>
> Let's clear up one thing first. Don't look at the name and think "learning rate means how fast the computer runs." It isn't that. It has nothing to do with computer speed. How far to turn a knob in each update: that size is the learning rate.

🖊
1. Definition card (English).
2. Rule box from Day 10, with "step size" crossed out and replaced: **new weight = old weight − (LEARNING RATE × slope)**.
3. Red chip: **❌ learning rate ≠ computer speed · ✅ = size of each knob change**.

### [G] Mid-roll CTA (cuts in mid-concept)
⏱ **@@G@@**

🎙
> Sorry for interrupting the video in the middle. Pause this video for a second and like it. And click the three dots and hype it. If you hype it, our video reaches many more beginners like you. We ran and tested today's notebook many times and kept it ready for you. Lots of you asked, "Anna, is it always theory, when is the practical?", right? Here it is, today is the practical. Many of the people watching this series still haven't subscribed. Every subscription you make pushes our whole team to make more videos like this. Thank you. So let's come back to the learning rate.

🖊
- Like / three-dots → **Hype** / Subscribe animation. Keep the learning-rate definition card faded underneath so the cut back is seamless.

> **Note:** his usual stat is "90% of viewers are not subscribed". Only say a number if YouTube Studio supports it on the day of recording; otherwise keep the generic line above.

### I2. The valley: too small / good / too big (drawing first)
⏱ **@@I2@@**

🎙
> I'm drawing the Day 10 valley again. Loss vs weight, a star at the bottom: the best weight. I'm putting the ball high on the left side. Now let's see what happens with three different learning rates.
>
> One: the learning rate is very small. Green colour. Tiny, tiny steps. The direction is correct, but even after 6 steps it's still far from the bottom. If you took steps this small on Ananthagiri hills, you could walk all night and the village wouldn't come. Too small means slow.
>
> Two: the right learning rate. Blue. Good hops: one, two, three, and it came smoothly to the star. Good.
>
> Three: the learning rate is very big. Red. In one jump it crossed the bottom and landed on the opposite wall. Jump again, back to this side. It keeps bouncing back and forth and never reaches the bottom. And if it's even bigger? Every jump goes higher, and it flies right out of the valley. The loss keeps going up. That's what we call overshoot. In the worst case they say training diverges, meaning it's completely ruined.
>
> Remember when you learned to ride a cycle? If you jerk the handle hard as soon as it wobbles, you zigzag back and forth across the road. If you correct too gently, you drift off into the drain. The learning rate is the same. On Day 10 I gave the Amma's-salt example, right: a pinch vs a fistful. Same idea. But don't take this as the exact example: on a cycle we correct by feel, while gradient descent corrects by calculating the slope.

🖊
1. Redraw the Day 10 **U-shaped valley**: x = weight, y = loss, ⭐ at the bottom ("best weight"), ball high on the left wall.
2. **Green, tiny dots** creeping a little way down from the ball: **"too small → slow (6 steps, still far)"**.
3. **Blue, neat hops** into the ⭐: **"just right"**.
4. **Red, a ball pinging wall to wall** across the bottom: **"too big → bounces (overshoot)"**.
5. **Red dashed**, a ball jumping higher each time and out of the valley: **"way too big → blows up (diverges)"**.
6. Tiny doodle: a cycle with a zigzag track ("over-steering") and a drifting track ("under-steering").
7. Optional small grey numbers for pause-and-note viewers (valley loss = (w − 3)², start w = 0, best w = 3): *lr 0.01 → 0.06, 0.12, 0.18 … · lr 0.25 → 1.5, 2.25, 2.63 … ⭐ · lr 1.0 → 6, 0, 6, 0 … · lr 1.1 → 6.6, −1.3, 8.2 … 💥*

### I3. Priya + Student F with three learning rates (the one worked example of the theory half)
⏱ **@@I3@@**

🎙
> Now let's see it with numbers. This is the only calculation in today's theory. Don't stress, it's what we did on Day 10; let's go slowly. You remember Priya: she studied 2 hours, 60% attendance, and passed. w1 = 0.8, w2 = 0.04, b = −4. z comes to 0, meaning 50-50, loss 0.693. The slope for w1 is −1. So new w1 = 0.8 − learning rate × (−1), that is, 0.8 + learning rate. That's all.
>
> Now let's call one more student. Remember Student F from Day 9? He studied only 1 hour, 50% attendance. He actually failed. With the original knobs, z = −1.2, 23%: it correctly said fail. Loss 0.263. Add the two students' losses: 0.956.
>
> Learning rate 0.01: w1 = 0.81. Priya's loss goes from 0.693 to 0.683. It barely moved. Too small.
>
> Learning rate 0.1, the one we used last video: w1 = 0.9. Priya's loss 0.598. Student F is still 25%, still fail. The two together: 0.885, it went down. Good.
>
> Learning rate 3: w1 = 0.8 + 3 = 3.8. Priya: 99.75% pass, loss almost zero. Feels like "wow", right? But look at Student F. z = 3.8 + 2 − 4 = 1.8. It says 86% pass! A boy who studied one hour and failed, it says 86% pass. His loss goes from 0.263 to 1.953. The two together go from 0.956 to 1.955. It doubled! When the step is too big, it fixed one person and broke another. That's overshoot, in numbers. If you have a calculator, check it yourselves.

🖊
1. Two student cards: **Priya: 2 h, 60%, PASSED** · **Student F (Day 9): 1 h, 50%, FAILED**. Neuron card: **w1 = 0.8, w2 = 0.04, b = −4 · slope for w1 (Priya) = −1 → new w1 = 0.8 + learning rate**.
2. Build the table row by row as he speaks:

   | Learning rate | New w1 | Priya: P(pass) → loss | Student F: P(pass) → loss | Both together |
   |---|---|---|---|---|
   | (before) | 0.8 | 50% → 0.693 | 23% → 0.263 | **0.956** |
   | 0.01 | 0.81 | 50.5% → 0.683 | 23% → 0.266 | 0.949 · "barely moved" |
   | 0.1 (Day 10) | 0.9 | 55% → 0.598 | 25% → 0.287 | **0.885 ✔** |
   | 3 | 3.8 | 99.75% → 0.002 | **86% → 1.953 ✗** | **1.955 ✗ (doubled)** |
3. Circle **"Student F 23% → 86% ✗"** in red. Write: **"too big a step: fixes one, breaks another"**.
4. Footnote (small): *loss uses ln (natural log). Student F's loss = −ln(1 − P(pass)), because the truth is Fail.*

### I4. How to choose + parameter vs hyperparameter + one-liner
⏱ **@@I4@@**

🎙
> So if you ask, "Anna, what's the correct learning rate?", there's no fixed answer. It changes with the problem. In practice people try and see: things like 0.1, 0.01, 0.001. Today in Colab we'll also try three and see. Some people even shrink the step size little by little as training goes on. That's advanced; name only.
>
> Now one very important piece of terminology: parameter vs hyperparameter. Write it down.
>
> *"Parameters are the weights and biases that the network learns by itself during training. Hyperparameters are the settings we choose before training, such as the number of epochs, the batch size, the learning rate, and the number of layers and neurons."*
>
> Don't get confused. Our 9 knobs are parameters. The machine learns those itself. Epochs, batch size and learning rate are hyperparameters. The network doesn't learn these; we decide them beforehand. Simply put: the machine sets the parameters, we set the hyperparameters.
>
> So the one-liner for the learning rate: the number that says how big a step gradient descent takes in each update is the learning rate. Too small, and it's slow; too big, and it overshoots. That simple.

🖊
1. Chip: **"Right learning rate = depends on the problem → try a few (0.1, 0.01, 0.001)"**. Grey name-drop: *"learning-rate schedule: shrink the step as training goes on (name only)"*.
2. Definition card (English), ✍️.
3. Two-column card:
   - **PARAMETERS (machine learns):** the 9 weights & biases
   - **HYPERPARAMETERS (we choose):** epochs · batch size · learning rate · number of layers / neurons
4. Recap card: **Learning rate = the size of each gradient-descent step. Too small → slow. Too big → overshoot.**

---

## [J] CONCEPT 4: Overfitting (too many epochs)

### J1. The twist + previous-year papers + definition
⏱ **@@J1@@**

🎙
> So now, the twist I held back at the epoch. "Anna, the more epochs we put, the better it learns, right? Not 100, let's put 10,000." Not always.
>
> There's always one guy among us, right? He takes previous-year question papers and practises the same 5 papers again and again. The first two or three times, the concepts make sense; that's good. But if he does the same papers 50 times? Now it's not the concept; he mugs up the answers. All he remembers is "the answer to this question is (b)". If the question changes a little in the exam: flat. Exactly the same thing happens to a network. That's called overfitting. Write down the definition.
>
> *"Overfitting happens when a model learns the training data too closely, including its noise and random luck, so it does very well on the training data but poorly on new, unseen data."*
>
> What does that mean? There's a real pattern in the data: "if you study more, the chance of passing is higher." But there's also some luck. One student studied 4.4 hours and passed, another studied 4.5 hours and failed; that day just didn't go well. An overfitted model mugs up that luck too, as if it were a rule. New students don't have that luck, right? That's why it fails on them. On Day 9 I said, "with more layers there's a chance it mugs up the training data and then fails on the testing data", right? Today we're seeing how that happens.
>
> There's also the opposite. With too few epochs, the network hasn't learned properly yet. That's called underfitting. Like going to the exam without finishing even one revision.

🖊
1. Doodle: a student with the same 5 question papers, a counter "×50", thought bubble "Q7 → (b)". Label **"బట్టీ = memorising"**.
2. Definition card (English), ✍️.
3. Two small scribbles: **"pattern: more study → more pass ✔"** vs **"luck: 4.4 h pass, 4.5 h fail ✗ (don't learn this)"**.
4. Mini scale: **UNDERFITTING (too few epochs, hasn't learned) ← ✔ just right → OVERFITTING (too many, memorised)**.

### J2. Validation data = mock test (and ≠ test data)
⏱ **@@J2@@**

🎙
> So how do we find out whether the network is mugging up or really learning? In the earlier videos we saw training vs testing, right? Here there's one more small idea: validation data. Coaching centres hold weekly mock tests, right? Before the final board exam, to check "are you really learning?"
>
> Same idea. From the training students, we set a few aside. The network doesn't learn from them; the knobs don't change because of them. After every epoch we just check the loss on them, that's all. That's validation data, our mock test.
>
> Don't get confused here: validation data and test data are not the same. Validation is the mock test: we use it while preparation is going on, to decide how many epochs to use and which learning rate. Test is the final exam: only once, at the end. If we look at the test data and keep changing settings again and again, it's like seeing the question paper before writing the exam. That's not an honest score.

🖊
1. Split the class of students into three boxes: **TRAINING (learn from these)** · **VALIDATION = mock test 📝 (checked every epoch, never learned from)** · **TEST = final exam 🎓 (used ONCE at the end)**.
2. Write "కన్ఫ్యూజ్ అవ్వద్దు ⚠️ validation ≠ test".
3. Chip: *"Tuning on the test set = seeing the question paper before the exam."*

### J3. The two loss curves (the key drawing) + best epoch
⏱ **@@J3@@**

🎙
> Now I'll draw a graph. This is the most important drawing in this topic; write it down. x-axis: epochs. y-axis: loss. Blue line, training loss: down, down, all the way to almost zero. Orange line, validation loss, meaning the mock test: at first it also comes down. At one point it's at its lowest. After that? It goes back up. See, the two lines have separated. It keeps getting better on the training students and worse on new students. That gap is the overfitting signal.
>
> At that lowest point, a dashed line: "best epoch, stop here". Left side: learning. Right side: the mugging-up zone. In real projects, people watch the validation curve and stop training near the best point. Keras even has a ready-made helper for this, called early stopping. Just remember the name.

🖊
1. Axes: **x = epochs →**, **y = loss ↓**.
2. **Blue curve "training loss"**: falls and keeps falling to almost 0.
3. **Orange curve "validation loss (mock test)"**: falls, reaches a lowest point, then curves **up**.
4. Shade the widening gap between them: **"gap = overfitting signal"**.
5. Vertical dashed line at the orange minimum: **"best epoch → STOP here"**.
6. Region labels: left **"learning ✅"**, right **"బట్టీ zone ❌"**. ✍️ "write it down".
7. Grey name-drop: *"early stopping (Keras helper, name only)"*.

### J4. Doubt: is it epochs alone? + one-liner
⏱ **@@J4@@**

🎙
> Now a doubt: "Anna, so does it always overfit if there are many epochs?" No. When does overfitting mostly happen? When the model has a lot of knobs, there's very little data, and there are a lot of epochs: when all three come together. If our 9-knob network has hundreds of students, there's no room to mug anything up. I'll show both cases for real in Colab today: one that doesn't overfit and one that does.
>
> Simple: mugging up the training data instead of learning it, and then failing on new data, is overfitting. When the mock-test loss, meaning the validation loss, starts going up, that's the signal.

🖊
- Formula-style chip: **many knobs + little data + many epochs ➜ overfitting** (with "+ + +" in red).
- Recap card: **Overfitting = memorising the training data (incl. its luck) → worse on new data. Signal: validation loss turns UP.**

---

## [K] BUILD: Train our network in Google Colab (Keras)

### K0. Bridge: the loop = model.fit, open Colab
⏱ **@@K0@@**

🎙
> So the theory is done. Now today's most exciting part: the build! I'm putting the Day 10 loop here on the side, and next to it I'm writing one line: model.fit. In a few more minutes you'll see for yourselves that these two are the same thing.
>
> I'm opening Google Colab. Colab is a free notebook that runs Python in your browser; you don't need to install anything. This notebook's link is in the description. Open it, then Runtime, Run all. You don't even need a GPU: the whole notebook finishes in two or three minutes on the free CPU. I'll explain each block by matching it to the drawings on our board. Don't stress about syntax.

🖊
- Left half of the screen: the board with the **Day 9 network** (S, L → h1, h2 → output, 9 knobs labelled) and the **Day 10 loop**. Write **"model.fit() = this loop ↺"** next to the loop.

💻
- Open the notebook in Colab (link from the description). Show the title cell **"Train Your First Neural Network"**.
- Menu: **Runtime → Run all** (pre-run once before recording, see production-notes §6, so outputs are already there; re-run live only if time allows).
- Keep the split screen for the whole build: board left, Colab right.

### K1. Blocks 1–3: tools, class data, training vs testing
⏱ **@@K1@@**

🎙
> Block 1: Get our tools ready. Three tools. numpy: a big calculator that does lots of numbers at once. matplotlib: it draws graphs. Keras: the neural-network toolkit. Keras is like a ready-made masala packet. On Day 10 we ground the masala by hand: we calculated every one of Sita's blames by hand. In Keras the same masala comes ready. Same taste, much faster. But just because you have the packet, if you don't know how much to add, the curry gets spoiled. That "how much" is our epochs, batch size and learning rate; we have to decide those ourselves. Underneath Keras, TensorFlow works like the engine. In the output it'll say Keras version 3 point something.
>
> Block 2: Make our class data. We're creating 500 pretend students. Each student has two features: study hours and sleep hours. And one label: pass or fail. The label is the answer key. To create the data we used a hidden rule: calculate marks from study and sleep, add a little luck, and 35 marks means pass. Our pass mark. But the important thing: we don't show this rule to the network. It only sees the 500 examples, just like real data. Look at the output: one studied 7.7 hours, pass. Another, 0.9 hours, fail. Out of 500, 347 passed: 69%.
>
> Block 3: Training data vs testing data. It learns from 400. We lock away 100 for the final exam. And we divide the hours by 10: 6 hours becomes 0.6. On Day 9 I said, right, that the size of a weight depends on the scale of its input, and that 80% can also be written as 0.8. With small numbers, learning goes smoothly.

🖊
- On the board, draw a masala packet next to a grinding stone: **"Day 10 = by hand · Keras = ready packet · you still choose HOW MUCH (epochs, batch size, learning rate)"**.
- Under the input circles S, L of the Day 9 drawing, write **"features"**; under the output, **"label = answer key"**.

💻
- **Block 1: Get our tools ready** → point at the output line `Keras version: 3.x` (read whatever version prints).
- **Block 2: Make our class data (features + label)** → highlight the markdown line "Pass if marks ≥ 35". Point at the first rows (**7.7 / 8.2 → Pass … 0.9 / 6.6 → Fail**) and the line **"Total students: 500, passed: 347 (69%)"**.
- **Block 3: Training data vs testing data** → highlight **`Training students: 400`** and **`Testing students : 100`**. Text pop: "6 hours ÷ 10 → 0.6".

### K2. Block 4: the network we drew → "9 = 9"
⏱ **@@K2@@**

🎙
> Block 4: Build the network we drew. This is my favourite moment today. Look at this block, and look at the Day 9 drawing on the board. Input: 2 inputs, study and sleep: our two input circles. Dense 2, relu: 2 hidden neurons with ReLU. These are the h1 and h2 we drew on Day 9. Dense means fully connected: every input connected to every neuron. On Day 9 we drew four lines, right? That's it. Dense 1, sigmoid: one output neuron with sigmoid; it gives the pass probability. One line = one layer, you see.
>
> Now look at the summary. The Param column: hidden layer 6, output layer 3. Trainable params: 9! On Day 9 we counted on the board, right: 4 weights, 2 biases, 2 weights, 1 bias, 9 in total. Keras also says 9. 9 = 9. This is the same network we drew, you see. Only one difference: this time I'm not setting the knobs. They start random, and the machine learns them itself.

🖊
- Draw coloured arrows from the code lines to the drawing: `Input(2)` → the two input circles · `Dense(2, relu)` → h1, h2 (+ the 4 lines) · `Dense(1, sigmoid)` → the output circle.
- Write big between the drawing and the screen: **"9 = 9 ✔"**.

💻
- **Block 4: Build the network we drew** → zoom on the `model.summary()` table. Circle **hidden_layer … 6**, **output_layer … 3** and **Trainable params: 9**. (It also shows "36.00 B"; don't read it.)

### K3. Block 5: compile = loss + gradient descent + step size
⏱ **@@K3@@**

🎙
> Block 5: Compile. Here we're telling the network "how to learn". Three choices. Loss: binary crossentropy. This is the log loss we saw on Day 10, for pass/fail. Optimizer: SGD. This is our gradient descent. Learning rate: 0.1, the same step size we used for Priya. Metrics: accuracy. This is just for us to read. On Day 10 I said, right: we train on loss and report accuracy. This block gives no output; it's only settings.

🖊
- Sticky note on the board: **compile = loss (log loss) + gradient descent (SGD) + step size 0.1**.

💻
- **Block 5: Compile (choose the loss, the gradient-descent version and the learning rate)** → highlight the three words in turn: `binary_crossentropy`, `SGD(learning_rate=0.1)`, `accuracy`. Text pop: "no output, just settings".

### K4. Block 6: fit = the Day 10 loop, 1,000 times
⏱ **@@K4@@**

🎙
> Now Block 6: Fit. This is the line I promised in the last video: model.fit. Inside this one line the whole Day 10 loop runs: forward, loss, backprop, update, repeat. Remember how we calculated every weight's blame for Sita by hand? Here it happens automatically.
>
> Three settings, meaning today's theory. Validation split 0.2: the last 20% of the 400, 80 people, are the mock test. So the ones who actually train are 320. Batch size 32: 320 ÷ 32 = 10 batches per epoch. Epochs: 100. So how many updates in total? 100 × 10 = 1,000. In the last video we said "thousands of times", right? These are those steps.
>
> Look, what's coming up on the screen? "Epoch 1/100": that's the epoch counter. Next to it, "10/10": the 10 batches in that epoch are done. I told you a little while ago that the first time, I didn't understand this screen. Now you understand it. Epoch 1: loss 0.532, accuracy 70%. I'm scrolling… Epoch 10: loss 0.401. Epoch 50: 0.229. Epoch 100: loss 0.193, accuracy 92–93%. And val loss, meaning the mock-test loss: it came from 0.439 to 0.159. The loss dropped to about a third. The network learned!

🖊
- Draw a fat arrow from the Day 10 loop to the `model.fit` line. On the loop write **"× 10 batches × 100 epochs = 1,000 times"**.
- Write the arithmetic: **400 − 80 (mock test) = 320 · 320 ÷ 32 = 10 per epoch · × 100 = 1,000 updates**.

💻
- **Block 6: Fit (the training loop: epochs and batches)** → highlight `epochs=100`, `batch_size=32`, `validation_split=0.2` as he names them.
- In the log, circle **`Epoch 1/100`** ("epoch counter") and **`10/10`** ("batches in this epoch").
- Scroll and freeze on Epoch 1 (**loss 0.5319, accuracy 0.7031, val_loss 0.4389**), Epoch 10 (**loss 0.4006**), Epoch 50 (**loss 0.2287**) and Epoch 100 (**loss 0.1926, accuracy 0.9250, val_loss 0.1589**).

### K5. Blocks 7–8: the loss curves + the final exam (90%)
⏱ **@@K5@@**

🎙
> Block 7: Look at the loss curves. Two lines: training loss and validation loss. Both are coming down together, right? The orange line didn't turn up. That means it's not mugging up; it's really learning. Compare it with the overfitting drawing on our board: there's no mugging-up zone here at all.
>
> Block 8: Final exam. Now the 100 students we locked away, the ones the network has never seen. Test loss 0.199. Test accuracy: 90%! It got 90 out of 100 right.
>
> "Anna, why didn't it get 100%?" Good question. Remember, we added luck to the data. We checked: if you take the very hidden rule that made the data, without the luck, and apply it to these 100 students, it also gets exactly 90%. That means our little 9-knob network has reached almost the best possible score.

🖊
- Point from the Colab plot to the board's overfitting drawing: **"here: both curves go DOWN together → learning ✅, no బట్టీ zone"**.
- Write: **Final exam (100 unseen students): 90% ✔**. Small chip: *"even the hidden rule itself (no luck) scores 90% on these 100"*.

💻
- **Block 7: Look at the loss curves** → show the plot "Loss goes down as the network learns" full width for 3 seconds; then the printed lines (training loss **0.532 → 0.401 → 0.229 → 0.193**, training accuracy **70% → 82% → 91% → 93%**).
- **Block 8: Final exam (evaluate on the test data)** → zoom on **`Test loss : 0.199`** and **`Test accuracy : 90%`**.

### K6. Block 9: Sita flips from 38% to 95% + the 9 learned knobs
⏱ **@@K6@@**

🎙
> Now today's climax. Block 9: Predict for Sita, Ravi and Kiran. Sita's card is on the board: on Day 9, 38%, fail. But she actually passed. Now let's ask the trained network. One thing: when predicting, we also have to divide the hours by 10, the same as in training. It's already in the notebook.
>
> Sita: 95%, PASS! From 38% to 95%. Ravi: 87%, pass. Kiran: 13%, fail.
>
> Look. We didn't change Sita. Sita still studied 6 hours and still slept 3 hours. What changed is the knobs. I didn't guess those knobs; the machine found them itself from 320 students' data. And predict is nothing special: it's the same forward pass we did on the board on Day 9, with new knobs.
>
> There's a "Try it yourself" cell in the notebook. Put in your own study hours and sleep hours and see what your chance is.
>
> And in the next cell, the 9 knobs the machine found get printed. On Day 9 there were 9 slots, and I filled them with 1, 0.5, −6 and so on. Now gradient descent filled them. For example, in h1 the study weight is 3.58 and the sleep weight is 1.07. The network learned that for this data, study matters more. But don't compare these numbers directly with the Day 9 numbers; these are for the ÷10 inputs.

🖊
- Replace the corner Sita card: cross out **"38% ✗ (guessed knobs)"** and write **"95% ✓ PASS (learned knobs)"** in green. Caption: **"Same Sita. New knobs. Found from 320 students' data."**
- Write: **predict = the same forward pass we did by hand on Day 9**.
- Fill the 9 knob slots on the Day 9 drawing in green with the learned values (small): study→h1 **3.58**, sleep→h1 **1.07**, h1 bias **−1.06** · study→h2 **0.45**, sleep→h2 **1.08**, h2 bias **−0.05** · h1→out **3.93**, h2→out **−0.14**, out bias **−2.40**. Tiny note: "for ÷10 inputs".

💻
- **Block 9: Predict for Sita, Ravi and Kiran** → zoom on the three lines: **Sita … 95% pass → PASS · Ravi … 87% pass → PASS · Kiran … 13% pass → FAIL**.
- Scroll past the **Try it yourself** cell (default 5 h, 7 h → **96%**); don't stop.
- Show the **"The 9 knobs the machine found by itself"** output; point only at study→h1 3.58 and sleep→h1 1.07.

### K7. Experiment 1: learning rate too small, about right, too big
⏱ **@@K7@@**

🎙
> Now let's prove the theory. Experiment 1: Learning rate too small, about right, too big. Same network, same data, same starting knobs; we change only the learning rate. A fair race, you see: 0.001, 0.1, 20.0.
>
> Look at the results. 0.001: the loss went from 0.577 to only 0.504. Even after 100 epochs it barely moved. Test accuracy 68%. 0.1, our main model: 0.532 to 0.193, 90%. 20.0: in the very first epoch the loss is 3.92! Then 1.43, 1.70, 0.85, 2.11: up and down, zigzag. Look at that line in the graph: like jerking the cycle handle hard. Even at the end it's 1.465; it never settled. Test accuracy 68%.
>
> Now there's a trap. 0.001 and 20.0 both got 68%. "Anna, 68% means it learned a bit, right?" No. If you look at what those two models are doing, they say "PASS" for all 100 people. In the test, 68 out of 100 actually passed. So even saying pass for everyone gets 68%, without learning anything. On Day 10 we saw loss vs accuracy, right? That's why you shouldn't look at accuracy alone; look at the loss too.

🖊
- Back on the board valley, label the three colours with the real values: **green = 0.001 (crawls)**, **blue = 0.1 (smooth ✔)**, **red = 20.0 (zigzag ✗)**.
- Trap box: **"68% = says PASS for everyone (68 of 100 passed) → learned NOTHING. Check the loss, not just accuracy!"**

💻
- **Experiment 1: Learning rate too small, about right, too big** → zoom on the three printed lines:
  `learning rate 0.001: … epoch 1 = 0.577, after epoch 100 = 0.504, test accuracy = 68%`
  `learning rate 0.1: … 0.532 … 0.193 … 90%`
  `learning rate 20.0: … 3.921 … 1.465 … 68%`
- Show the "Step size matters" plot; trace the zigzagging lr = 20.0 line with the cursor.

### K8. Experiment 2: too many epochs → overfitting, for real
⏱ **@@K8@@**

🎙
> Experiment 2: Too many epochs, and memorising instead of learning. Now we're deliberately creating the perfect situation for mugging up. A big network: two hidden layers with 64 neurons each, 4,417 knobs in total. But only 30 students to learn from. And 500 epochs. The optimizer is Adam: the "smarter gradient descent" I named on Day 10; we're using it here. A different 80 people for the mock test.
>
> Look at the graph. The drawing we made on our board, for real! Training loss, on the 30 people: down, down, 0.0006 at 500 epochs. Almost zero. Training accuracy 100%. Feels perfect, right? But look at the validation loss. Best at epoch 35: 0.185. After that, up, up: 0.903 at 500 epochs. Almost 5 times worse than the best. With 4,417 knobs it mugged up the 30 students and got worse on the 80 new ones. The grey dashed line, best epoch 35: it should have stopped there.
>
> And our main 9-knob model? In Block 7, its validation loss came down all the way through the 100 epochs. 9 knobs, 320 students: no room for mugging up. That's why I said overfitting needs those three together.
>
> At the end of the notebook there's also an optional cell: a slightly bigger network with 193 knobs. The result? The same 90%. On Day 9 I said, right, more layers aren't always better. For this small table data, our 9 knobs are enough.

🖊
- Put the board's overfitting drawing (J3) side by side with the real plot. Write on it: **"best epoch = 35"**, **"training loss → 0.0006 (100% on 30 students)"**, **"validation 0.185 → 0.903 (~5× worse)"**, **"బట్టీ zone"**.
- Chip: **4,417 knobs + 30 students + 500 epochs = overfitting ✓ · 9 knobs + 320 students + 100 epochs = no overfitting ✓**.
- Small: **"193 knobs → 90%, same as our 9 knobs"**.

💻
- **Experiment 2: Too many epochs, and memorising instead of learning (overfitting)** → show **`Knobs in the big model: 4417`**, then the plot "Too many epochs: memorising, not learning" with the grey **best epoch = 35** line. Zoom on the two printed lines: **`Best validation loss 0.185 at epoch 35`** and **`After 500 epochs: training loss 0.0006 (training accuracy 100%), validation loss 0.903`**.
- **Optional: a slightly bigger network** → just the two result lines (**193 knobs, 90%** vs **9 knobs, 90%**).

### K9. "Your numbers may differ" + the stuck-at-68% fix + homework
⏱ **@@K9@@**

🎙
> One important note. When you run it, your numbers may come out a little different. 89 or 91 instead of 90%, Sita 93 instead of 95. That's normal. Training starts from random knobs, the students get shuffled every epoch, and depending on the computer the decimals can change too. The story stays the same.
>
> If your accuracy gets stuck around 68% and every student gets the same %, don't panic; it's not your mistake. In our small network, both ReLU neurons got switched off right at the start, you see. On Day 10 we saw that when Sita's h2 was off, its blame was zero, right? Same thing. If no blame comes, it doesn't learn. In Block 4, change the seed number from 42 to 7 and run it again.
>
> Now the homework; it's at the end of the notebook. One: change epochs from 100 to 5. What test accuracy do you get? Two: make the batch size 320. How many batches does each epoch show? Three: set the learning rate to 1.0. Too big, or still OK? Put your results in the comments.

🖊
- Card: **"Your numbers may differ a little (89–91%, Sita ~93–95%). Normal."**
- Card: **"Stuck at 68%, same % for everyone? → both ReLU neurons started OFF (zero blame, Day 10) → Block 4: seed 42 → 7, run again."**
- Homework card: **① epochs = 5 → test accuracy? ② batch_size = 320 → batches per epoch? ③ learning_rate = 1.0 → too big or OK?** "💬 comment your results".

💻
- Scroll to the last markdown cell **"What we did (block → what we learned earlier)"**: hold on the table for 2 seconds, then the **Homework** list and the "Why are my numbers slightly different" note.
- Highlight `keras.utils.set_random_seed(42)` in Block 4 when he says "seed".

---

## [L1] Video recap + comment quiz
⏱ **@@L1@@**

🎙
> And that's it for the day! What we covered today: the epoch, one round over all the data. The batch, the small group seen for one update. The learning rate, the size of each step. Parameters vs hyperparameters. Overfitting, meaning mugging up, and how to catch it with a mock test. And in Keras we built our own network, trained it, gave it a final exam, and took Sita from 38% to 95%. All of these come under AI, machine learning, deep learning, and training a neural network, you see.
>
> Now today's quiz; tell me in the comments. One: a class of 60 students, batch size 20, 10 epochs. How many times do the weights get updated in total? Two: the training loss is going down, but after epoch 6 the validation loss is going up. What's happening, and what should we do? Three: in Block 4, if we change Dense 2 to Dense 3, meaning 3 hidden neurons, how many trainable params will the summary show? First calculate it, then run it in Colab, check, and tell me. Let's see who listened well.

🖊
1. Taxonomy line: **AI → ML → Deep Learning → training a neural network → {epoch, batch, learning rate, overfitting} → Keras build (Sita 38% → 95%)**.
2. Quiz card:
   1. 60 students · batch size 20 · 10 epochs → how many weight updates?
   2. Training loss ↓ but validation loss ↑ after epoch 6 → what's happening? What should we do?
   3. `Dense(2)` → `Dense(3)` in Block 4 → Trainable params = ?
   *(Answers go in production notes. Don't show them on screen.)*

---

## [L2] Outro + Part 4 teaser + sign-off
⏱ **@@L2@@**

🎙
> If it doesn't all click after watching once, that's fine. You have the notebook. Change the numbers, run it, and see what happens. Once you run it with your own hands, you'll understand more than from watching the video ten times.
>
> All the notes, definitions, drawings, numbers, and the Colab notebook link, I'm putting in the description.
>
> Now, the next video. Until now we worked with numbers: study hours, sleep hours. But how does AI see a photo? Face unlock, Google Lens: how do they figure out what's in a photo? In the next video: what computer vision is, what a CNN is, and again in Colab, we'll build an image classifier that reads handwritten digits, 0 to 9. Whoever wants that video, like this video.
>
> And it's not late yet: only 11 videos are done. If you sit for one day, you can cover them all. Add your friends to this AI Learning Series too, and especially send this video to friends who say "I want to learn AI but I'm scared of coding."
>
> Thank you so much for watching, signing off, Tech Boy Deepak.

🖊
- The Day 10 loop with "model.fit() = this loop ✔" and Sita's green "95% ✓" card stay on screen.
- Lower-third: **"📒 Notes + 💻 Colab notebook in description ↓"**.
- End card: **Next: How AI Sees Images 👁️ · Computer Vision · CNN · build an image classifier** + the previous-video tile (Day 10).
