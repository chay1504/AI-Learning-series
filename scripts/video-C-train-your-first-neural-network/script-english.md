# Video C: "Train Your First Neural Network" (English rendering for review)

**Series:** AI Learning Series, **Day 11** on the channel (Part 3 of the Deep Learning block). This covers plan Days 29–30: epochs, batches and learning rate (plus overfitting), then building and training a neural network in Keras on Google Colab.
**Recording script:** `script-telugu.md`. This file is a faithful English rendering of it, with the same segments, timestamps and board/Colab cues. It is for checking content and accuracy. Do not record from it.
**Runtime:** ~26:48 (≈ 26.8 min) estimated: 4,538 English-equivalent spoken words at 175 wpm (3,700 Telugu-script words), plus ~52 s for Colab cells running in the build. Allow ~28 min with drawing pauses.
**Legend:** ⏱ timestamp (start–end) · 🎙 what he says · 🖊 what to draw, write or show (in order) · 💻 what to show in Colab (block names match the notebook headings exactly)

> **Production note on numbering:** Video A = **Day 9** and Video B = **Day 10** are assumed, so this video opens as **Day 11**. If the numbering changes, update segment A, the "Day 9 / Day 10" callbacks (listed in production-notes §10), the "only 11 videos" line in L2 and the title.

---

## [A0] Cold-open pitch
⏱ **00:00 – 00:20**

🎙
> Until now we drew the neural network on the board and calculated it by hand with a calculator. Today we're going to train that same network for real on a computer, right in front of your eyes. If you want to learn AI from the basics, from scratch, subscribe to our channel. Let's dive into the video.

🖊
- Face to camera. Quick 2-second flash of the Colab training output scrolling ("Epoch 1/100 … 10/10 …"), then the channel logo sting.

---

## [A] Welcome + headline promise
⏱ **00:20 – 00:37**

🎙
> Hey guys, welcome back to AI Learning Series Day 11! We've already reached Day 11, you see. Today's video is very special to me personally, because today we go from theory to practical. Train your first neural network. First the theory, then we'll train our own network in Google Colab.

🖊
- Title card: **AI Learning Series · Day 11 · Train Your First Neural Network**
- Small badge: "Theory ➜ Practical 🛠️"

---

## [B] Recap of Days 9–10 + last quiz answers + catch-up
⏱ **00:37 – 01:58**

🎙
> So first, let's recap once. On Day 9 we drew a small network, right? Study hours and sleep hours go in, two hidden neurons, one output, 9 knobs in total. I guessed those knobs myself. Sita studied 6 hours but slept only 3. With those knobs the network said 38%, it said fail. But Sita actually passed.
>
> On Day 10 we saw how a network learns: forward pass, loss, backpropagation, gradient-descent update. You remember this loop, right? And at the end of the last video I said, "this loop repeats thousands of times." I'm circling this repeat arrow. Today's whole video is about this one arrow, you see.
>
> Quick answers to the last quiz. ReLU(−5) = 0, ReLU(3) = 3. 2 − 0.1 × 4 = 1.6; the slope was positive, so the weight went down. And Sita's h2 was off, its output was 0, so its blame was zero, and that's why that weight didn't change.
>
> At the end of the last video I asked three questions, right? What do we call each round? How many students' data do we give at once? What happens if the step size is too big? Today is the answers to those three. And I made one promise: "inside one line, model.fit(), this same loop runs." Today we'll run that line ourselves. If you haven't watched Day 9 and Day 10, please watch those two first and come back.

🖊
1. Redraw (or flash) the Day 9 network: **S, L → h1, h2 → output**, with "9 knobs = weights + biases".
2. Sita card in a corner: **Sita: 6 h study, 3 h sleep → Day 9 guessed knobs: 38% ✗ (actually PASSED)**. It stays until K6.
3. Redraw the Day 10 loop: **① Forward → ② Loss → ③ Backprop → ④ Update → ↺**. Circle the **↺ repeat** arrow in red: "today = this arrow".
4. Quick card: Day 10 quiz answers **0 · 3 · 1.6 (down) · h2 = 0 → blame 0**.
5. The three questions from the Day 10 outro, numbered: **① each round = ? ② how many students at once = ? ③ step too big = ?**

---

## [C] Agenda
⏱ **01:58 – 02:16**

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
⏱ **02:16 – 02:59**

🎙
> Many people think, "Anna, Colab, code, Keras… we don't know programming, we can't do this," right? Don't be scared at all. Today I won't teach even one line as syntax. For every code block, I'll just tell you which drawing we've already made on the board it matches. The notebook link will be in the description; you just have to press "Run all".
>
> Let me tell you something honestly. The first time I trained a model, when lines like "Epoch 1/100, 10/10, loss…" were scrolling on the screen, I didn't understand a single bit of it. By the end of this video, you'll be able to read every number on that screen yourself. These settings are part of training every deep learning model, so everyone, take notes.

🖊
- Sticky note: **"No syntax lessons. Every code block = a drawing we already know."**
- Small screenshot of a Keras training log with a big "?" over it ("by the end of today you'll read every number").

---

## [F] CONCEPT 1: Epoch

### F1. Announce + definition + keyword
⏱ **02:59 – 03:33**

🎙
> So the first topic: the epoch. In the last video we said "repeat", right? There's a unit for measuring that repeat. That's the epoch. I'm showing the definition on screen, write it down.
>
> *"An epoch is one complete pass through the entire training data. Training for 100 epochs means the network sees every training example 100 times."*
>
> What does that mean? If the network looks at every single student in the training data once, that's one epoch. The most important word here is "entire": all of the data. If it sees only part of it, that's not an epoch.

🖊
1. Definition card (English).
2. Underline **"entire training data"** and write beside it: **"ALL students, once = 1 epoch"**.

### F2. Revision analogy + board (60 students)
⏱ **03:33 – 04:11**

🎙
> To put it even more simply: before exams we do revision, right? First revision: the whole syllabus once. Second revision: the whole thing again. One revision = one epoch, you see. Reading one chapter isn't a revision, right? Only the whole syllabus counts as one round.
>
> Let's see it on the board. Suppose a class has 60 students; that's our training data. I'm drawing 60 dots. When the network has looked at all 60 of them once, completely, that's Epoch 1. Again from the start: Epoch 2, 3, 4, 5. As the epochs go up, the loss comes down little by little, like the ball going down the Day 10 valley.

🖊
1. A grid of **60 small dots** labelled **"Training data = 60 students"**.
2. A big loop arrow around the whole grid: **"Epoch 1 = all 60, once"**.
3. A ladder to the right: **Epoch 1 → Epoch 2 → Epoch 3 → Epoch 4 → Epoch 5**, with a small falling line next to it: "loss ↓".
4. Small doodle: a notebook with "1st revision ✔ 2nd ✔ 3rd ✔" = "1 revision = 1 epoch".

### F3. Doubt + one-liner
⏱ **04:11 – 04:39**

🎙
> You might have a doubt: "Anna, what's the use of showing the same students again and again? Isn't once enough?" It isn't. Gradient descent takes small, small steps, right? In one round it doesn't reach the valley bottom. That's why it needs many rounds. So is more always better? There's a twist in that; I'll tell you in the fourth topic.
>
> Simple: the network looking at all of the training data once, completely, is one epoch. That's what we call an epoch.

🖊
- Recap card: **Epoch = one full pass over ALL the training data.**
- Small sticky note: "More epochs = always better? → topic 4 🤔"

---

## [H] CONCEPT 2: Batch

### H1. Announce + definition + answer-sheet bundles
⏱ **04:39 – 05:51**

🎙
> So the epoch is done. Second question: how many students' data do we give at once? In the last video I said, right, that in real training it's not one person's blame: they average the blame of many students and then update. That group is called a batch. Write down the definition.
>
> *"A batch is a small group of training examples that the network processes together before making one update to its weights and biases. The batch size is the number of examples in each batch."*
>
> What does that mean? The network takes a small group, say 10 people. For those 10 it does the forward pass, the loss and backprop, averages their blame, and updates the 9 knobs once. One batch, one update. Remember this.
>
> A teacher corrects answer sheets, right? If there are 60 papers, she takes 10 papers as one bundle. She corrects that bundle, notes the common mistakes, and in the next class she changes her teaching a little. Then the next bundle. One bundle = one batch. The small change after each bundle = one update. When all 60 papers are done = one epoch. But don't take this as the exact example: the teacher changes her teaching; the network changes its weights.

🖊
1. Definition card (English). Underline **"before making one update"**.
2. Doodle: a stack of answer sheets tied into bundles of 10, a red pen, and a sticky note "common mistakes → adjust a little".
3. Write the mapping: **bundle = batch · small change after each bundle = 1 update · whole pile once = 1 epoch**.
4. Disclaimer chip: *"Teacher changes teaching; network changes weights. Same papers come back every epoch."*

### H2. Board: 60 students in batches of 10 (the rule)
⏱ **05:51 – 06:32**

🎙
> Now on the board. I'm boxing those 60 dots in tens: Batch 1 to Batch 6. Under each box, a spanner, meaning "update". So one epoch has 6 updates. Now write down this rule, it's very important:
>
> Updates per epoch = students ÷ batch size. Total updates = epochs × updates per epoch.
>
> 60 ÷ 10 = 6. If we do 5 epochs? 5 × 6 = 30 updates. See, it's just simple division. Technically, each update is also called an iteration, or a step. The one step we took for Priya on Day 10 was one iteration, you see. And the Day 10 loop goes round once for every batch. So in 5 epochs, that loop went round 30 times.

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
⏱ **06:32 – 07:14**

🎙
> We can set the batch size to anything. Batch size 1: an update after every student; that's called stochastic gradient descent. Batch size 60: the whole class as one batch, one update per epoch; that's called batch gradient descent. In between, things like 10, 32, 64: mini-batch gradient descent. That's what everyone actually uses.
>
> So why don't we give all the data at once? One: real projects have lakhs, crores of examples, and they don't all fit in memory at once. In batches, the GPU processes each batch fast, in parallel. Two: instead of one update per epoch we get many, so learning starts sooner. And before every epoch it shuffles the students, like a teacher mixing the papers and tying new bundles.

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
⏱ **07:14 – 07:50**

🎙
> Lots of people get confused here: epoch, batch, iteration. Don't get confused. A batch is one piece of the data. An iteration is one update made with that one piece. An epoch is all of the data once, and it has many iterations.
>
> Another doubt: "Anna, what if it's 60 students and batch size 32?" It's nothing, very simple. The first batch has 32, and the last batch has the remaining 28. So 2 batches; you round up, you see.
>
> Simple: the small group of students the network looks at before updating the knobs once is a batch. That's what we call a batch.

🖊
1. Three boxes: **BATCH = a slice of the data** → **ITERATION = 1 update on 1 batch** → **EPOCH = all the data once (many iterations)**. Write "కన్ఫ్యూజ్ అవ్వద్దు ⚠️" above.
2. Write: **60 ÷ 32 → batches of 32 + 28 → 2 batches (round UP)**.
3. Recap card: **Batch = the small group seen before ONE update. Batch size = how many in it.**

---

## [I] CONCEPT 3: Learning rate

### I1. Announce + definition + "not computer speed"
⏱ **07:50 – 08:37**

🎙
> Now the third question: what happens if the step size is too big? On Day 10 we saw the gradient-descent rule, right: new weight = old weight − step size × slope. The official name for that step size is the learning rate. Write down the definition.
>
> *"The learning rate is a number that controls how big a step gradient descent takes each time it updates the weights. If it is too small, learning is very slow. If it is too large, the steps overshoot the lowest point, and the loss can bounce around or even blow up."*
>
> Don't look at the name and think "learning rate means how fast the computer runs." It has nothing to do with computer speed. How far to turn a knob in each update: that size is the learning rate.

🖊
1. Definition card (English).
2. Rule box from Day 10, with "step size" crossed out and replaced: **new weight = old weight − (LEARNING RATE × slope)**.
3. Red chip: **❌ learning rate ≠ computer speed · ✅ = size of each knob change**.

### I2. The valley: too small / good / too big (drawing first)
⏱ **08:37 – 09:53**

🎙
> I'm drawing the Day 10 valley again. Loss vs weight, a star at the bottom: the best weight. I'm putting the ball high on the left side. Now let's see what happens with three learning rates.
>
> One: the learning rate is very small. Green colour. Tiny, tiny steps. The direction is correct, but even after 6 steps it's still far from the bottom. Too small means slow.
>
> Two: the right learning rate. Blue. Good hops, and it came smoothly to the star. Good.
>
> Three: the learning rate is very big. Red. In one jump it crossed the bottom and landed on the opposite wall. Jump again, back to this side. It keeps bouncing back and forth and never reaches the bottom. And if it's even bigger? Every jump goes higher, it flies right out of the valley, and the loss keeps going up. That's what we call overshoot; in the worst case, they say it diverges.
>
> Remember when you learned to ride a cycle? If you jerk the handle hard as soon as it wobbles, you zigzag back and forth across the road. If you correct too gently, you drift off into the drain. The learning rate is the same. But don't take this as the exact example: on a cycle we correct by feel, while gradient descent corrects by calculating the slope.

🖊
1. Redraw the Day 10 **U-shaped valley**: x = weight, y = loss, ⭐ at the bottom ("best weight"), ball high on the left wall.
2. **Green, tiny dots** creeping a little way down from the ball: **"too small → slow (6 steps, still far)"**.
3. **Blue, neat hops** into the ⭐: **"just right"**.
4. **Red, a ball pinging wall to wall** across the bottom: **"too big → bounces (overshoot)"**.
5. **Red dashed**, a ball jumping higher each time and out of the valley: **"way too big → blows up (diverges)"**.
6. Tiny doodle: a cycle with a zigzag track ("over-steering") and a drifting track ("under-steering").
7. Optional small grey numbers for pause-and-note viewers (valley loss = (w − 3)², start w = 0, best w = 3): *lr 0.01 → 0.06, 0.12, 0.18 … · lr 0.25 → 1.5, 2.25, 2.63 … ⭐ · lr 1.0 → 6, 0, 6, 0 … · lr 1.1 → 6.6, −1.3, 8.2 … 💥*

### [G] Mid-roll CTA (cuts in mid-concept)
⏱ **09:53 – 10:26**

🎙
> Sorry for interrupting the video in the middle. Pause this video for a second and like it. And click the three dots and hype it. If you hype it, our video reaches many more beginners like you. Lots of you asked, "Anna, is it always theory, when is the practical?", right? Here it is: today is the practical. Many of the people watching this series still haven't subscribed. Every subscription you make pushes our whole team to make more videos like this. Thank you. So let's come back to the learning rate, this time with numbers.

🖊
- Like / three-dots → **Hype** / Subscribe animation. Keep the valley drawing faded underneath so the cut back to the numbers is seamless.

> **Note:** his usual stat is "90% of viewers are not subscribed". Only say a number if YouTube Studio supports it on the day of recording; otherwise keep the generic line above.

### I3. Priya + Student F with three learning rates (the one worked example of the theory half)
⏱ **10:26 – 11:47**

🎙
> This is the only calculation in today's theory. Don't stress, it's what we did on Day 10. You remember Priya: she studied 2 hours, 60% attendance, and passed. w1 = 0.8, w2 = 0.04, b = −4. z comes to 0, meaning 50-50, loss 0.693. The slope for w1 is −1. So new w1 = 0.8 − learning rate × (−1), that is, 0.8 + learning rate. That's all.
>
> Let's call one more student. Remember Student F from Day 9? He studied only 1 hour, 50% attendance, and actually failed. With the original knobs, 23%: it correctly said fail. Loss 0.263. Add the two students' losses: 0.956.
>
> Learning rate 0.01: w1 = 0.81. Priya's loss goes from 0.693 to 0.683. It barely moved. Too small.
>
> Learning rate 0.1, the one we used last video: w1 = 0.9. Priya's loss is 0.598, and Student F is still fail. The two together: 0.885, it went down. Good.
>
> Learning rate 3: w1 = 3.8. Priya: 99.75% pass, loss almost zero. Feels like "wow", right? But look at Student F: z = 3.8 + 2 − 4 = 1.8. It says 86% pass! A boy who studied one hour and failed, it says 86% pass. The two together go from 0.956 to 1.955. It doubled! When the step is too big, it fixes one person and breaks another. That's overshoot, in numbers. If you have a calculator, check it yourselves.

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
⏱ **11:47 – 12:41**

🎙
> So if you ask, "Anna, what's the correct learning rate?", there's no fixed answer. It changes with the problem. In practice people try and see: things like 0.1, 0.01, 0.001.
>
> Now one very important piece of terminology: parameter vs hyperparameter. Write it down.
>
> *"Parameters are the weights and biases that the network learns by itself during training. Hyperparameters are the settings we choose before training, such as the number of epochs, the batch size, the learning rate, and the number of layers and neurons."*
>
> Don't get confused. Our 9 knobs are parameters; the machine learns those itself. Epochs, batch size and learning rate are hyperparameters; we decide those beforehand. Simply put: the machine sets the parameters, we set the hyperparameters.
>
> So the one-liner for the learning rate: the number that says how big a step gradient descent takes in each update is the learning rate. Too small, and it's slow; too big, and it overshoots. That simple.

🖊
1. Chip: **"Right learning rate = depends on the problem → try a few (0.1, 0.01, 0.001)"**.
2. Definition card (English), ✍️.
3. Two-column card:
   - **PARAMETERS (machine learns):** the 9 weights & biases
   - **HYPERPARAMETERS (we choose):** epochs · batch size · learning rate · number of layers / neurons
4. Recap card: **Learning rate = the size of each gradient-descent step. Too small → slow. Too big → overshoot.**

---

## [J] CONCEPT 4: Overfitting (too many epochs)

### J1. The twist + previous-year papers + definition
⏱ **12:41 – 14:05**

🎙
> So now, the twist I held back at the epoch. "Anna, the more epochs we put, the better it learns, right? Not 100, let's put 10,000." Not always.
>
> There's always one guy among us, right? He practises the same 5 previous-year question papers again and again. The first two or three times, the concepts make sense; that's good. But if he does them 50 times? Now it's not the concept; he mugs up the answers. If the question changes a little in the exam: flat. Exactly the same thing happens to a network. That's called overfitting. Write down the definition.
>
> *"Overfitting happens when a model learns the training data too closely, including its noise and random luck, so it does very well on the training data but poorly on new, unseen data."*
>
> What does that mean? There's a real pattern in the data: if you study more, the chance of passing is higher. But there's also some luck. One student studied 4.4 hours and passed, another studied 4.5 hours and failed; that day just didn't go well. An overfitted model mugs up that luck too, as if it were a rule. New students don't have that luck, right? That's why it fails on them. On Day 9 I said, "there's a chance it mugs up the training data and then fails on the testing data", right? This is that.
>
> There's also the opposite. With too few epochs, the network hasn't learned properly yet. That's called underfitting.

🖊
1. Doodle: a student with the same 5 question papers, a counter "×50", thought bubble "Q7 → (b)". Label **"బట్టీ = memorising"**.
2. Definition card (English), ✍️.
3. Two small scribbles: **"pattern: more study → more pass ✔"** vs **"luck: 4.4 h pass, 4.5 h fail ✗ (don't learn this)"**.
4. Mini scale: **UNDERFITTING (too few epochs, hasn't learned) ← ✔ just right → OVERFITTING (too many, memorised)**.

### J2. Validation data = mock test (and ≠ test data)
⏱ **14:05 – 14:57**

🎙
> So how do we find out whether the network is mugging up or really learning? In the earlier videos we saw training vs testing, right? Here there's one more small idea: validation data. Like the weekly mock tests at coaching centres.
>
> Same idea. From the training students, we set a few aside. The network doesn't learn from them; the knobs don't change because of them. After every epoch we just check the loss on them, that's all. That's validation data, our mock test.
>
> Don't get confused here: validation data and test data are not the same. Validation is the mock test: used while preparation is going on, to decide how many epochs and which learning rate. Test is the final exam: only once, at the end. If we look at the test data and keep changing settings again and again, it's like seeing the question paper before writing the exam.

🖊
1. Split the class of students into three boxes: **TRAINING (learn from these)** · **VALIDATION = mock test 📝 (checked every epoch, never learned from)** · **TEST = final exam 🎓 (used ONCE at the end)**.
2. Write "కన్ఫ్యూజ్ అవ్వద్దు ⚠️ validation ≠ test".
3. Chip: *"Tuning on the test set = seeing the question paper before the exam."*

### J3. The two loss curves (the key drawing) + best epoch
⏱ **14:57 – 15:39**

🎙
> Now the most important drawing in this topic; write it down. x-axis: epochs. y-axis: loss. Blue line, training loss: down, down, all the way to almost zero. Orange line, validation loss, meaning the mock test: at first it also comes down, at one point it's at its lowest, and after that it goes back up. See, the two lines have separated. Better on the training students, worse on new students. That gap is the overfitting signal.
>
> At that lowest point, a dashed line: "best epoch, stop here". Left side learning, right side the mugging-up zone. In real projects, people watch the validation curve and stop training near the best point. Keras even has a ready-made helper for this, called early stopping; just remember the name.

🖊
1. Axes: **x = epochs →**, **y = loss ↓**.
2. **Blue curve "training loss"**: falls and keeps falling to almost 0.
3. **Orange curve "validation loss (mock test)"**: falls, reaches a lowest point, then curves **up**.
4. Shade the widening gap between them: **"gap = overfitting signal"**.
5. Vertical dashed line at the orange minimum: **"best epoch → STOP here"**.
6. Region labels: left **"learning ✅"**, right **"బట్టీ zone ❌"**. ✍️ "write it down".
7. Grey name-drop: *"early stopping (Keras helper, name only)"*.

### J4. Doubt: is it epochs alone? + one-liner
⏱ **15:39 – 16:08**

🎙
> Now a doubt: "Anna, so does it always overfit if there are many epochs?" No. When does overfitting mostly happen? When there are a lot of knobs, very little data and a lot of epochs: when all three come together. I'll show both cases for real in Colab: one that doesn't overfit and one that does.
>
> Simple: mugging up the training data instead of learning it, and then failing on new data, is overfitting. When the validation loss starts going up, that's the signal.

🖊
- Formula-style chip: **many knobs + little data + many epochs ➜ overfitting** (with "+ + +" in red).
- Recap card: **Overfitting = memorising the training data (incl. its luck) → worse on new data. Signal: validation loss turns UP.**

---

## [K] BUILD: Train our network in Google Colab (Keras)

### K0. Bridge: the loop = model.fit, open Colab
⏱ **16:08 – 16:41**

🎙
> So the theory is done. Now today's most exciting part: the build! Next to the Day 10 loop I'm writing one line: model.fit. In a little while you'll see for yourselves that these two are the same thing.
>
> Google Colab is a free notebook that runs Python in your browser; you don't need to install anything. This notebook's link is in the description. Open it, then Runtime, Run all. You don't even need a GPU: it finishes in two or three minutes on the free CPU.

🖊
- Left half of the screen: the board with the **Day 9 network** (S, L → h1, h2 → output, 9 knobs labelled) and the **Day 10 loop**. Write **"model.fit() = this loop ↺"** next to the loop.

💻
- Open the notebook in Colab (link from the description). Show the title cell **"Train Your First Neural Network"**.
- Menu: **Runtime → Run all** (pre-run once before recording, see production-notes §6, so outputs are already there; re-run live only if time allows).
- Keep the split screen for the whole build: board left, Colab right.

### K1. Blocks 1–3: tools, class data, training vs testing
⏱ **16:41 – 17:50**

🎙
> Block 1: Get our tools ready. numpy: a big calculator. matplotlib: it draws graphs. Keras: the neural-network toolkit, with TensorFlow working underneath it like the engine. Keras is like a ready-made masala packet. On Day 10 we ground it by hand; here it comes ready. But how much to add, meaning epochs, batch size and learning rate, we have to decide that ourselves.
>
> Block 2: Make our class data. 500 pretend students. Each student has two features, study hours and sleep hours, and one label, pass or fail, meaning the answer key. To create the data we used a hidden rule: calculate marks, add a little luck, and 35 marks means pass. But we don't show this rule to the network; it only gets the 500 examples, just like real data. Out of 500, 347 passed: 69%.
>
> Block 3: Training data vs testing data. It learns from 400, and we lock away 100 for the final exam. And we divide the hours by 10: 6 hours becomes 0.6. On Day 9 I said, right, that 80% can also be written as 0.8. With small numbers, learning goes smoothly.

🖊
- On the board, draw a masala packet next to a grinding stone: **"Day 10 = by hand · Keras = ready packet · you still choose HOW MUCH (epochs, batch size, learning rate)"**.
- Under the input circles S, L of the Day 9 drawing, write **"features"**; under the output, **"label = answer key"**.

💻
- **Block 1: Get our tools ready** → point at the output line `Keras version: 3.x` (read whatever version prints).
- **Block 2: Make our class data (features + label)** → highlight the markdown line "Pass if marks ≥ 35". Point at the first rows (**7.7 / 8.2 → Pass … 0.9 / 6.6 → Fail**) and the line **"Total students: 500, passed: 347 (69%)"**.
- **Block 3: Training data vs testing data** → highlight **`Training students: 400`** and **`Testing students : 100`**. Text pop: "6 hours ÷ 10 → 0.6".

### K2. Block 4: the network we drew → "9 = 9"
⏱ **17:50 – 18:42**

🎙
> Block 4: Build the network we drew. This is my favourite moment today. Look at this block and the Day 9 drawing on the board side by side. Input: 2 inputs, study and sleep. Dense 2, relu: 2 hidden neurons with ReLU, our h1 and h2. Dense means fully connected; on Day 9 we drew four lines, right? That's it. Dense 1, sigmoid: one output neuron; it gives the pass probability. One line = one layer, you see.
>
> Now look at the summary: hidden layer 6, output layer 3. Trainable params: 9! On Day 9 we counted on the board, right: 4 weights, 2 biases, 2 weights, 1 bias, 9 in total. 9 = 9. It's the same network we drew, you see. Only one difference: this time the knobs start random, and the machine learns them itself.

🖊
- Draw coloured arrows from the code lines to the drawing: `Input(2)` → the two input circles · `Dense(2, relu)` → h1, h2 (+ the 4 lines) · `Dense(1, sigmoid)` → the output circle.
- Write big between the drawing and the screen: **"9 = 9 ✔"**.

💻
- **Block 4: Build the network we drew** → zoom on the `model.summary()` table. Circle **hidden_layer … 6**, **output_layer … 3** and **Trainable params: 9**. (It also shows "36.00 B"; don't read it.)

### K3. Block 5: compile = loss + gradient descent + step size
⏱ **18:42 – 19:11**

🎙
> Block 5: Compile. Here we're telling the network "how to learn". Three choices. Loss: binary crossentropy. This is the log loss we saw on Day 10, for pass/fail. Optimizer: SGD. This is our gradient descent. Learning rate: 0.1, the same step size we used for Priya. Metrics: accuracy. This is just for us to read. On Day 10 I said, right: we train on loss and report accuracy. This block gives no output; it's only settings.

🖊
- Sticky note on the board: **compile = loss (log loss) + gradient descent (SGD) + step size 0.1**.

💻
- **Block 5: Compile (choose the loss, the gradient-descent version and the learning rate)** → highlight the three words in turn: `binary_crossentropy`, `SGD(learning_rate=0.1)`, `accuracy`. Text pop: "no output, just settings".

### K4. Block 6: fit = the Day 10 loop, 1,000 times
⏱ **19:11 – 20:24**

🎙
> Now Block 6: Fit. This is the line I promised in the last video. Inside this one line the whole Day 10 loop runs: forward, loss, backprop, update, repeat. The blame calculation we did by hand for Sita happens automatically here.
>
> Three settings, meaning today's theory. Validation split 0.2: the last 80 of the 400 are the mock test. So the ones who actually train are 320. Batch size 32: 320 ÷ 32 = 10 batches per epoch. Epochs: 100. How many updates in total? 100 × 10 = 1,000. Write this calculation in your notes. In the last video we said "thousands of times", right? These are those steps.
>
> Look at the screen. "Epoch 1/100": that's the epoch counter. Next to it, "10/10": the 10 batches in that epoch are done. I told you a little while ago that the first time, I didn't understand this screen. Now you understand it. Epoch 1: loss 0.532, accuracy 70%. Epoch 50: 0.229. Epoch 100: loss 0.193, accuracy 92–93%. The mock-test loss went from 0.439 to 0.159. The network learned!

🖊
- Draw a fat arrow from the Day 10 loop to the `model.fit` line. On the loop write **"× 10 batches × 100 epochs = 1,000 times"**.
- Write the arithmetic: **400 − 80 (mock test) = 320 · 320 ÷ 32 = 10 per epoch · × 100 = 1,000 updates**.

💻
- **Block 6: Fit (the training loop: epochs and batches)** → highlight `epochs=100`, `batch_size=32`, `validation_split=0.2` as he names them.
- In the log, circle **`Epoch 1/100`** ("epoch counter") and **`10/10`** ("batches in this epoch").
- Scroll and freeze on Epoch 1 (**loss 0.5319, accuracy 0.7031, val_loss 0.4389**), Epoch 50 (**loss 0.2287**) and Epoch 100 (**loss 0.1926, accuracy 0.9250, val_loss 0.1589**).

### K5. Blocks 7–8: the loss curves + the final exam (90%)
⏱ **20:24 – 21:07**

🎙
> Block 7: Look at the loss curves. Training loss and validation loss are both coming down together, right? The orange line didn't turn up. That means it's not mugging up; it's really learning.
>
> Block 8: Final exam. The 100 students we locked away, the ones the network has never seen. Test accuracy: 90%!
>
> "Anna, why didn't it get 100%?" Good question. We added luck to the data, right? We checked: if you take the very hidden rule that made the data, without the luck, and apply it to these 100 students, it also gets exactly 90%. That means our little 9-knob network has reached almost the best possible score.

🖊
- Point from the Colab plot to the board's overfitting drawing: **"here: both curves go DOWN together → learning ✅, no బట్టీ zone"**.
- Write: **Final exam (100 unseen students): 90% ✔**. Small chip: *"even the hidden rule itself (no luck) scores 90% on these 100"*.

💻
- **Block 7: Look at the loss curves** → show the plot "Loss goes down as the network learns" full width for 3 seconds; then the printed lines (training loss **0.532 → 0.401 → 0.229 → 0.193**, training accuracy **70% → 82% → 91% → 93%**).
- **Block 8: Final exam (evaluate on the test data)** → zoom on **`Test loss : 0.199`** and **`Test accuracy : 90%`**.

### K6. Block 9: Sita flips from 38% to 95% + the 9 learned knobs
⏱ **21:07 – 22:10**

🎙
> Now today's climax. Block 9: Predict for Sita, Ravi and Kiran. Sita's card is on the board: on Day 9, 38%, fail, but she actually passed. Now let's ask the trained network. When predicting, we also have to divide the hours by 10, the same as in training. It's already in the notebook.
>
> Sita: 95%, PASS! From 38% to 95%. Ravi: 87%, pass. Kiran: 13%, fail.
>
> Look. We didn't change Sita; she still studied 6 hours and slept 3. What changed is the knobs. I didn't guess those knobs; the machine found them itself from 320 students' data. And predict is nothing special: it's the same forward pass we did on the board on Day 9, with new knobs.
>
> The next cell has the 9 knobs the machine found. For example, in h1 the study weight is 3.58 and the sleep weight is 1.07. The network learned that for this data, study matters more. But these are for the ÷10 inputs; don't compare them directly with the Day 9 numbers.

🖊
- Replace the corner Sita card: cross out **"38% ✗ (guessed knobs)"** and write **"95% ✓ PASS (learned knobs)"** in green. Caption: **"Same Sita. New knobs. Found from 320 students' data."**
- Write: **predict = the same forward pass we did by hand on Day 9**.
- Fill the 9 knob slots on the Day 9 drawing in green with the learned values (small): study→h1 **3.58**, sleep→h1 **1.07**, h1 bias **−1.06** · study→h2 **0.45**, sleep→h2 **1.08**, h2 bias **−0.05** · h1→out **3.93**, h2→out **−0.14**, out bias **−2.40**. Tiny note: "for ÷10 inputs".

💻
- **Block 9: Predict for Sita, Ravi and Kiran** → zoom on the three lines: **Sita … 95% pass → PASS · Ravi … 87% pass → PASS · Kiran … 13% pass → FAIL**.
- Scroll past the **Try it yourself** cell (default 5 h, 7 h → **96%**); don't stop. Text pop: "Try your own hours here ✍️".
- Show the **"The 9 knobs the machine found by itself"** output; point only at study→h1 3.58 and sleep→h1 1.07.

### K7. Experiment 1: learning rate too small, about right, too big
⏱ **22:10 – 23:09**

🎙
> Now let's prove the theory. Experiment 1: Learning rate too small, about right, too big. Same network, same data, same starting knobs; only the learning rate changes. A fair race, you see: 0.001, 0.1, 20.0.
>
> 0.001: the loss went from 0.577 to only 0.504; it barely moved. Test accuracy 68%. 0.1, our main model: 0.532 to 0.193, 90%. 20.0: in the very first epoch the loss is 3.92! Then 1.43, 1.70, 0.85, 2.11: up and down, zigzag, like jerking the cycle handle hard. Even at the end it never settled. Test accuracy 68%.
>
> There's a trap here. "Anna, 68% means it learned a bit, right?" No. Those two models say "PASS" for all 100 people. In the test, 68 out of 100 actually passed. So you get 68% without learning anything. On Day 10 we saw loss vs accuracy, right? That's why you shouldn't look at accuracy alone; look at the loss too. Remember this.

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
⏱ **23:09 – 24:06**

🎙
> Experiment 2: Too many epochs, and memorising instead of learning. Now we're deliberately creating the perfect situation for mugging up. A big network, 4,417 knobs. But only 30 students to learn from. 500 epochs. The optimizer is Adam, the "smarter gradient descent" I named on Day 10. A different 80 people for the mock test.
>
> Look at the graph: our board drawing, for real! Training loss goes down, down: 0.0006 at 500 epochs, training accuracy 100%. Feels perfect, right? But look at the validation loss: best at epoch 35, 0.185. After that, up, up: 0.903 at 500, almost 5 times worse. It mugged up the 30 students. The grey dashed line, best epoch 35: it should have stopped there.
>
> And our 9-knob model? In Block 7, its validation loss came down all the way through the 100 epochs. 9 knobs, 320 students: no room for mugging up.

🖊
- Put the board's overfitting drawing (J3) side by side with the real plot. Write on it: **"best epoch = 35"**, **"training loss → 0.0006 (100% on 30 students)"**, **"validation 0.185 → 0.903 (~5× worse)"**, **"బట్టీ zone"**.
- Chip: **4,417 knobs + 30 students + 500 epochs = overfitting ✓ · 9 knobs + 320 students + 100 epochs = no overfitting ✓**.

💻
- **Experiment 2: Too many epochs, and memorising instead of learning (overfitting)** → show **`Knobs in the big model: 4417`**, then the plot "Too many epochs: memorising, not learning" with the grey **best epoch = 35** line. Zoom on the two printed lines: **`Best validation loss 0.185 at epoch 35`** and **`After 500 epochs: training loss 0.0006 (training accuracy 100%), validation loss 0.903`**.
- **Optional: a slightly bigger network** → skip on camera (it's for viewers; result in production-notes §7).

### K9. "Your numbers may differ" + the stuck-at-68% fix + homework
⏱ **24:06 – 25:03**

🎙
> One important note. Your numbers may come out a little different: 89 or 91 instead of 90%, Sita 93 instead of 95. That's normal. Random starting knobs, shuffling and computer differences can change the decimals. The story stays the same.
>
> If your accuracy gets stuck around 68% and every student gets the same %, don't panic; it's not your mistake. In our small network, both ReLU neurons got switched off right at the start, you see. On Day 10 we saw that when Sita's h2 was off, its blame was zero, right? Same thing. If no blame comes, it doesn't learn. In Block 4, change the seed from 42 to 7 and run it again.
>
> The homework is at the end of the notebook. One: with 5 epochs, what test accuracy do you get? Two: with batch size 320, how many batches does each epoch show? Three: with learning rate 1.0, too big or OK? Put your results in the comments.

🖊
- Card: **"Your numbers may differ a little (89–91%, Sita ~93–95%). Normal."**
- Card: **"Stuck at 68%, same % for everyone? → both ReLU neurons started OFF (zero blame, Day 10) → Block 4: seed 42 → 7, run again."**
- Homework card: **① epochs = 5 → test accuracy? ② batch_size = 320 → batches per epoch? ③ learning_rate = 1.0 → too big or OK?** "💬 comment your results".

💻
- Scroll to the last markdown cell **"What we did (block → what we learned earlier)"**: hold on the table for 2 seconds, then the **Homework** list and the "Why are my numbers slightly different" note.
- Highlight `keras.utils.set_random_seed(42)` in Block 4 when he says "seed".

---

## [L1] Video recap + comment quiz
⏱ **25:03 – 25:58**

🎙
> And that's it for the day! What we covered today: the epoch, one round over all the data. The batch, the small group seen for one update. The learning rate, the size of each step. Parameters vs hyperparameters. Overfitting, meaning mugging up, and catching it with a mock test. And in Keras we built our own network, trained it, and took Sita from 38% to 95%. All of these come under AI, ML, deep learning, and training a neural network, you see.
>
> Now the quiz; tell me in the comments. One: 60 students, batch size 20, 10 epochs. How many times do the weights get updated in total? Two: the training loss is going down, but after epoch 6 the validation loss goes up. What's happening, and what should we do? Three: in Block 4, if we change Dense 2 to Dense 3, how many trainable params? First calculate it, then check it in Colab. Let's see who listened well.

🖊
1. Taxonomy line: **AI → ML → Deep Learning → training a neural network → {epoch, batch, learning rate, overfitting} → Keras build (Sita 38% → 95%)**.
2. Quiz card:
   1. 60 students · batch size 20 · 10 epochs → how many weight updates?
   2. Training loss ↓ but validation loss ↑ after epoch 6 → what's happening? What should we do?
   3. `Dense(2)` → `Dense(3)` in Block 4 → Trainable params = ?
   *(Answers go in production notes. Don't show them on screen.)*

---

## [L2] Outro + Part 4 teaser + sign-off
⏱ **25:58 – 26:48**

🎙
> If it doesn't all click after watching once, that's fine. You have the notebook. Once you run it with your own hands, you'll understand more than from watching the video ten times. All the notes, and the Colab notebook link, I'm putting in the description.
>
> Now, the next video. Until now we worked with numbers, but how does AI see a photo? In the next video: what computer vision is, what a CNN is, and again in Colab, we'll build an image classifier that reads handwritten digits, 0 to 9. Whoever wants that video, like this video.
>
> And it's not late yet: only 11 videos are done. If you sit for one day, you can cover them all. Send this video to friends who say "I want to learn AI but I'm scared of coding."
>
> Thank you so much for watching, signing off, Tech Boy Deepak.

🖊
- The Day 10 loop with "model.fit() = this loop ✔" and Sita's green "95% ✓" card stay on screen.
- Lower-third: **"📒 Notes + 💻 Colab notebook in description ↓"**.
- End card: **Next: How AI Sees Images 👁️ · Computer Vision · CNN · build an image classifier** + the previous-video tile (Day 10).
