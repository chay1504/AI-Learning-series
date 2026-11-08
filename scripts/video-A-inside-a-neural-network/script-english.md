# Video A: "Inside a Neural Network" (English rendering)

**AI Learning Series, Day 9** (plan Days 21–24: What is DL · Artificial neuron · Layers · Weights & biases)

This is a faithful English rendering of `script-telugu.md`. It uses the **same segment IDs, timestamps and board cues**, so that non-Telugu reviewers can check the content and accuracy. Deepak records from the Telugu file. The on-screen definition cards are identical in both files and stay in English on screen.

- **Timing basis:** about 175 English-equivalent words per minute, his measured rate (DNA Part 01 §6.1). Timestamps are cumulative estimates computed from the spoken word count of each segment.
- **Format:** each segment has ⏱ timestamp · 🎙 spoken lines · 🖊 board / on-screen cues, done step by step. "[DEF CARD]" means a full-screen English definition card that stays up while he reads it.
- **Running example:** everything continues from Day 7's Student D (4 hrs, 80% attendance, w1 = 0.8, w2 = 0.04, b = −4 → z = 2.4 → 91.7%), plus the Ravi / Sita / Kiran network. All numbers match `research/dl-content-research.md` and were re-checked in Python.

---

### ⏱ 00:00–00:24 · [A0] Cold open: the hook

**🎙 Spoken**
> Have you ever wondered how this video reached you? You didn't search for it, right? YouTube decided on its own that you'd probably like it. And what sits inside that system is something called a neural network. Today we're going to open up that neural network and look at what's inside. If you want to learn AI from the basics, from scratch, subscribe to our channel. Let's dive into the video.

**🖊 Board / on-screen**
- Screen-record of the YouTube home feed with this video's thumbnail circled.
- Text pop: "How did this video reach YOU? → a Neural Network 🧠".

---

### ⏱ 00:24–00:45 · [A] Welcome + headline promise

**🎙 Spoken**
> Hey guys, welcome back to AI Learning Series Day 9. We've already reached Day 9! And today is a special day, because until now we were in Machine Learning, and from today we're entering Deep Learning. Today we'll discuss four topics: what deep learning is, what an artificial neuron is, how a neural network works, and what weights and biases are.

**🖊 Board / on-screen**
- Title card: "AI Learning Series · Day 9 · Inside a Neural Network". *(Production: renumber if needed. See production-notes.md.)*
- Small badge: "Phase 3: Deep Learning begins".

---

### ⏱ 00:45–01:47 · [B] Recap: taxonomy walk + catch-up + comment prompt

**🎙 Spoken**
> First, let's do a quick recap. As always, let's walk down the map from the top. Remember the three circles we drew in Day 2? The big outer circle is AI, inside it is ML, and inside ML is DL. Until now we were in the middle circle, ML. In ML we saw supervised learning and unsupervised learning. In supervised: classification and regression. Day 7: decision tree, logistic regression, SVM. Day 8, in unsupervised: K-means, hierarchical clustering, DBSCAN. And who was our hero in all of this? Our student pass/fail model. Study hours, sleep hours, attendance... we built it and kept extending it a little in every video. Today too, that same student comes with us. Especially Student D from Day 7, remember him? He studied 4 hours, 80% attendance, 91.7% pass. Keep him in mind, he's very important today. Whoever hasn't watched Day 1 to Day 8, please watch them, especially Day 7. It'll really help with today's video. And whoever remembers what Student D's z value was, tell me in the comments. Let's see who remembers how much.

**🖊 Board / on-screen**
1. Draw three nested circles: **AI** ⊃ **ML** ⊃ **DL**. Shade ML lightly ("we were here").
2. Next to ML, write a quick list: Supervised → Classification / Regression → DT, LogReg, SVM · Unsupervised → K-means, Hierarchical, DBSCAN.
3. Flash the Day 7 slide (or redraw): "Student D: 4 hrs · 80% · z = 2.4 · 91.7% → PASS". Circle it: "remember him!"
4. Arrow onto the inner **DL** circle: "TODAY ➜".

---

### ⏱ 01:47–02:19 · [C] Agenda (written with pen) + dive in

**🎙 Spoken**
> So what are we going to discuss today? I'm writing it with the pen. First: what is Deep Learning? Second: what is an artificial neuron? Third: how does a neural network work, meaning the input layer, hidden layers and output layer. Fourth: what are weights and biases? Everyone write these four down in your notes. There's a lot of drawing today. First I'll draw the picture on the board, and only after that the numbers. If my handwriting with this pen comes out a bit crooked, ignore that. Let's dive into the video.

**🖊 Board / on-screen**
- Handwrite a numbered list:
  1. What is Deep Learning?
  2. What is an Artificial Neuron?
  3. How does a Neural Network work? (Input · Hidden · Output layers)
  4. What are Weights & Biases?
- Small note in the corner: "Drawings first ✏️ → numbers later".

---

### ⏱ 02:19–02:54 · [E] Reassurance + stakes + take notes

**🎙 Spoken**
> Before we start: many people think, "What is this anna, deep learning, neural networks, it all sounds very hard, we're beginners, we won't understand", right? Don't be afraid at all. Honestly, if you understood Day 7, you already know half of today's video. You just don't know it yet! I'll show you that in a little while. After listening, you yourselves will say, "It's so easy anna, and we thought it was hard." These four topics are very, very important, because whatever comes ahead, whether it's ChatGPT or image recognition, all of it is built on this. So everyone, write notes.

**🖊 Board / on-screen**
- Text pop: "Understood Day 7? → you already know 50% of today 😉".

---

### ⏱ 02:54–03:56 · [F] Concept 1: Deep Learning (definition + name unpack)

**🎙 Spoken**
> So, the first topic is Deep Learning. What actually is deep learning? First let's see the definition. Write it down.
>
> *"Deep learning is a subset of machine learning that uses artificial neural networks with many layers to learn patterns, and even the useful features themselves, directly from large amounts of data such as images, audio and text."*
>
> So what does this mean? First it says "a subset of machine learning". That means deep learning isn't some separate new thing. It sits inside ML: the inner circle we drew in Day 2. It also learns from data. There's training, there's testing, just like we saw from Day 3 to Day 8.
>
> It's right there in the name, isn't it? Deep Learning. What does "deep" mean? Many layers. Like a building with many floors. And what does it use? "Artificial neural networks". That's in the name too: a neural network means a network made of neurons, lots of small neurons connected together. What a neuron is, I'll tell you in the second topic. For now just remember this: deep means many layers.

**🖊 Board / on-screen**
1. **[DEF CARD]** "Deep learning is a subset of machine learning that uses artificial neural networks with many layers to learn patterns, and even the useful features themselves, directly from large amounts of data such as images, audio and text." Notes icon: ✍️ "Write it down".
2. Underline "subset of machine learning" and point back to the inner DL circle.
3. Write: **Deep = many layers**. Sketch a tiny building with floors next to it.
4. Write: **Neural network = network of neurons** (draw 3–4 little circles joined by lines).

---

### ⏱ 03:56–05:01 · [F] Concept 1: the key idea, learning features itself

**🎙 Spoken**
> Now, the most important phrase in this definition is "learn even the useful features themselves". I'll explain with our student example. In ML, what did we do? We gave the model the columns ourselves: study hours 4, sleep 7, attendance 80. Three numbers. Which features are important, we decided that ourselves. That's what we did from Day 5 to Day 8.
>
> Now in deep learning, suppose that instead of those three numbers we give a photo of that student's answer sheet. A normal 12-megapixel phone photo has roughly 12 million pixels, and every pixel has three colours: red, green, blue. So 12 million into 3 is about 36 million numbers! Can anyone sit down and write rules for 36 million numbers? "If pixel number five lakh is dark, then..."? Impossible, right? That's exactly where deep learning comes in. Give it lots of photos along with their correct answers, and the network works out on its own which patterns matter: first lines and edges, then letters, then words. To put it even more simply: in ML, we select the features; in DL, the network learns the features itself from raw data. That's all.

**🖊 Board / on-screen**
1. Split the board into two halves. **Left: "ML (Days 5–8)"**. Draw a small table: Study hrs | Sleep | Attendance → **Model** → "Pass". Write "WE choose features 🧑".
2. **Right: "DL"**. Draw a rectangle for the answer-sheet photo → a stack of 4–5 columns of small circles → "Pass". Write "NETWORK learns features 🤖".
3. Under the photo: "12 MP × 3 colours ≈ **36,000,000 numbers**".
4. Under the stack, label the columns left to right: "edges → letters → words → answer".

---

### ⏱ 05:01–05:43 · [F] Concept 1: everyday analogy (with disclaimer)

**🎙 Spoken**
> Let me give you an example from our own life. When you were small, how did you learn to recognise your Amma's handwriting? Did anyone give you rules, like "if this letter bends like this, Amma wrote it"? No, right? You saw it many, many times, and then you just knew. Or when some relative is walking towards you from far away: first you see the outline, then the way they walk, then the face. Simple things first, then complex things. The layers in deep learning work in roughly the same way: the early layers catch simple patterns, and the later layers combine them into bigger patterns. But don't take this as the exact technical example. It's only to get the feel.

**🖊 Board / on-screen**
- Quick doodle: a stick figure far away → closer → face. Labels: "outline → walk → face" = "simple → complex".
- Small caption: "Analogy only, not the exact mechanism".

---

### ⏱ 05:43–06:24 · [F] Concept 1: why now? (notes prompt)

**🎙 Spoken**
> Now you should have a question: neural networks are a very old idea, from many years ago. So why has deep learning blown up so big only in the last ten or fifteen years? There are three reasons. Write them down. First is data: because of smartphones and the internet, a huge amount of data appeared. Second is GPUs: chips that can do millions of multiplications at the same time. Third is better algorithms: better tricks for training. These three came together at the same time, and that's why it took off. And how important is this? In 2024 the Physics Nobel Prize was given to John Hopfield and Geoffrey Hinton, for foundational work on artificial neural networks.

**🖊 Board / on-screen**
- Draw three icons in a row and write the words under them: 🗄️ **Data** · 🔲 **GPU** · 💡 **Better algorithms**. Then "= Deep Learning boom 🚀". ✍️ "Write it down".
- Text card: "Nobel Prize in Physics 2024: John Hopfield & Geoffrey Hinton, for foundational work on artificial neural networks".

---

### ⏱ 06:24–07:04 · [F] Concept 1: real examples you use daily

**🎙 Spoken**
> And where are we using this? Every day, everywhere. For example, face unlock on your phone: that's a neural network. Google Lens: you point the camera at a Telugu signboard and it translates it, right? Neural networks. ChatGPT, Gemini: you ask in Telugu, they answer in Telugu. Those are very big neural networks. In hospitals there are AI tools that look at chest X-rays and flag whether there's a chance of TB, and then the doctors check. At Hyderabad airport, DigiYatra scans your face and matches it, right? These days, face recognition systems like that mostly run on neural networks. And, like I said at the start, the YouTube feed that brought this video to you, too.

**🖊 Board / on-screen**
- Quick B-roll / icon grid, one per line as he says it: 📱 Face unlock · 🔍 Google Lens (Telugu signboard → English) · 💬 ChatGPT / Gemini in Telugu · 🩻 Chest X-ray → "possible TB, doctor to check" · ✈️ DigiYatra · ▶️ YouTube recommendations.
- *(Production: no stats on screen here. Optional verified stats are in production-notes.md.)*

---

### ⏱ 07:04–07:50 · [F] Concept 1: anticipated doubts + one-line recap

**🎙 Spoken**
> Now many people might have a doubt: "Anna, if DL is this powerful, should we stop using decision trees and logistic regression?" No! Don't get confused here. For a small table like our student pass/fail CSV, a decision tree or logistic regression is often good enough, and cheaper and faster too. Where does deep learning shine? When there's huge data: images, audio, text.
>
> Another doubt: "Does a neural network work just like our brain?" It's only loosely inspired by the brain, that's all. Real brain neurons are far, far more complex. So don't imagine there's a brain sitting inside the computer.
>
> So, simple: machine learning that uses neural networks with many layers, and learns features on its own from huge data, is deep learning. That's what we call deep learning. I hope you understood.

**🖊 Board / on-screen**
- Write two ❌ myth lines and correct them:
  - ❌ "DL always better" → ✅ "Small table? DT / LogReg are often enough"
  - ❌ "Works like a brain" → ✅ "Loosely inspired only"
- One-liner box: **DL = ML + neural networks with many layers + learns its own features from big data**.

---

### ⏱ 07:50–08:40 · [H] Concept 2: Artificial neuron (definition, then the cliff-hanger)

**🎙 Spoken**
> So, deep learning is done. Now let's come to its building block: the artificial neuron. We build a building with bricks, right? In the same way, we build a neural network with neurons. Write down the definition.
>
> *"An artificial neuron is a small mathematical unit that takes one or more inputs, multiplies each input by a weight, adds them up together with a bias, and passes the result through an activation function to produce a single output."*
>
> One line about the name: it's inspired by the neurons in our brain. A brain neuron receives signals, and if they're strong enough, it fires. But our artificial neuron isn't a cell, and it isn't hardware. It's just a small calculation in software. Think of it as a small calculator.
>
> Now, I said at the start that you already know half of today's video, right? And that secret is...

**🖊 Board / on-screen**
1. **[DEF CARD]** "An artificial neuron is a small mathematical unit that takes one or more inputs, multiplies each input by a weight, adds them up together with a bias, and passes the result through an activation function to produce a single output." ✍️
2. Tiny cartoon of a biological neuron with arrows: dendrites → "inputs", cell body → "adds up", axon → "output". Caption: "inspiration only".
3. Write: "Artificial neuron = a tiny calculator in software 🧮 (not a cell, not hardware)".

---

### ⏱ 08:40–09:17 · [G] Mid-roll CTA ("Sorry for interrupting…")

**🎙 Spoken**
> ...but before that, sorry for interrupting the video in the middle. Pause this video for one second and go hit like. And click the three dots and hit hype. If you hype it, our video reaches many more beginners like you. Lots of you have been asking, "Anna, when will you bring deep learning, take the series forward". Here it is, deep learning has started! But we need all of your support. 90% of the people are still not subscribing. If you subscribe, it helps us a lot, and our whole team gets the motivation to make even better videos. Thank you. So now, let's come to that secret.

**🖊 Board / on-screen**
- Animated like 👍 / three-dots → "Hype 🔥" / Subscribe 🔔 overlay. Keep the neuron definition faded in the background, so the return feels seamless.

---

### ⏱ 09:17–10:37 · [H] Concept 2: the big reveal, Student D drawn as a neuron

**🎙 Spoken**
> Do you remember Student D from Day 7? I'll draw him on the board as a neuron now, watch. I'm drawing one big circle. One line down the middle. Inputs come in from the left side: two arrows. The first input is study hours = 4. The second input is attendance = 80. On each arrow I'm writing its weight: × 0.8 on study hours, × 0.04 on attendance. One small arrow from the top: the bias, b = −4.
>
> Now two steps happen inside the neuron. Step 1 is the weighted sum. We multiply each input by its weight, add them all, and add the bias. 0.8 into 4 = 3.2. 0.04 into 80 = 3.2. 3.2 plus 3.2 = 6.4, minus 4 = 2.4. So z comes to 2.4. Looks like something we've seen before, right? Yes! It's the same z = 2.4 we got in Day 7.
>
> Step 2 is activation. We send that z into the sigmoid function, the squashing function we saw in Day 7. Whatever number you give it, it squashes it into somewhere between 0 and 1. σ(2.4) = 0.917. That means 91.7%. More than our 50% threshold, so: pass!
>
> So what happened? The calculation we did for logistic regression in Day 7: that itself was one artificial neuron! Logistic regression is a neural network with exactly one neuron. Simple. Those who watched Day 7: without even knowing it, you calculated a neuron by hand!

**🖊 Board / on-screen** (the hand-drawn neuron, step by step)
1. Draw one **big circle** in the centre. Split it with a vertical line: write **Σ** in the left half and draw a small **S-curve (σ)** in the right half.
2. Draw **2 arrows coming in from the left**. At their tails write "Study hrs = 4" and "Attendance = 80".
3. On the arrows write "× 0.8" and "× 0.04".
4. Draw a **small arrow from the top**: "bias b = −4".
5. Inside Σ write: "0.8×4 + 0.04×80 − 4 = 3.2 + 3.2 − 4 = **2.4**".
6. Inside σ write: "σ(2.4) = **0.917**".
7. Draw **one arrow out** to the right: "91.7% → PASS ✔" (threshold 50%).
8. Big stamp across the top: **"Logistic Regression = 1 Neuron!"** Flash the Day 7 slide beside it for 2 seconds.

---

### ⏱ 10:37–11:11 · [H] Concept 2: a small Day 7 clarification + sigmoid deferral

**🎙 Spoken**
> Let me clear up one small point from Day 7 right here. The sigmoid output isn't 0 or 1. It's a probability between 0 and 1, like 0.917. The final decision, pass or fail, 0 or 1, is what the threshold gives. And the value of e is 2.718. Write the formula with brackets: σ(z) = 1 / (1 + e^(−z)). What happens inside this sigmoid, and why we even need it, is a full topic called activation functions, and we'll open it up in the next video. For today, just remember this much: sigmoid squashes the number into 0 to 1.

**🖊 Board / on-screen**
- Formula card (with brackets): **σ(z) = 1 / (1 + e^(−z))**, e ≈ 2.718.
- Two-step strip: "σ output = probability (0 to 1), e.g. 0.917" → "threshold 50%" → "decision 0 / 1 (Fail / Pass)".
- Sticky note: "Activation functions → NEXT VIDEO 🔜".

---

### ⏱ 11:11–11:50 · [H] Concept 2: second student + terminology drill (notes prompt)

**🎙 Spoken**
> Let's quickly try one more student: let's say Student A. He studied just 1 hour, attendance 50%. 0.8 into 1 = 0.8. 0.04 into 50 = 2. 0.8 plus 2 minus 4 = −1.2. Sigmoid of −1.2 comes to 0.231, that's 23%. Less than 50%. Fail, for sure, because he only studied for one hour. Same neuron, same weights, the student changed, and the answer changed.
>
> So write the parts of a neuron in your notes. This is very important terminology. Input, x: the data that comes in. Weight, w: how much that input matters. Bias, b: a number added at the end. Weighted sum: z. Activation: here, sigmoid. Output: the one number that goes out.

**🖊 Board / on-screen**
1. Beside the neuron, a mini-table:

   | Student | Hrs | Att % | z | σ(z) | Decision |
   |---|---|---|---|---|---|
   | D | 4 | 80 | 2.4 | 0.917 | Pass |
   | A | 1 | 50 | 0.8 + 2.0 − 4 = **−1.2** | 0.231 | Fail |
2. Terminology card ✍️: **Input (x) · Weight (w) · Bias (b) · Weighted sum (z = w1x1 + w2x2 + b) · Activation (σ) · Output**.

---

### ⏱ 11:50–12:21 · [H] Concept 2: cricket-selector analogy

**🎙 Spoken**
> To understand it even more simply: imagine a cricket selector deciding whether to take a player into the team or not. He looks at recent runs, fitness, fielding: those are the inputs. Each one has its own importance: those are the weights. And that selector has his own strictness. Some are strict, some are lenient. That's like the bias. At the end, the chance of selection: that's the output. But there's one difference: the selector decides the weights with his own opinion. The neuron, though, learns its weights from data. Remember that.

**🖊 Board / on-screen**
- Draw a second, smaller neuron labelled for cricket: inputs "Recent runs", "Fitness", "Fielding" → weights → bias "selector's strictness" → output "Selection chance %".
- Footnote: "Selector = opinion · Neuron = learns from data".

---

### ⏱ 12:21–13:12 · [H] Concept 2: anticipated doubts + one-line recap

**🎙 Spoken**
> Now, doubts. First, and very important: bias. Many people hear "bias" and think "biased, unfair", like when we say "that teacher is biased". Don't get confused here! Here, bias just means one number that gets added to the sum. It has nothing to do with being unfair. Second: "Where does the neuron keep its knowledge?" Not in the neuron. It's in the weights and the bias. The neuron is just a calculator, that's all. Third: "Is one neuron enough for AI?" No. One neuron can only draw a straight-line boundary, just like logistic regression. When does the real power come? When we connect lots of neurons together in layers. And that's our next topic.
>
> So, simple: something that takes inputs, multiplies them by weights, adds the bias, passes it through an activation, and gives one output is an artificial neuron. That's what we call an artificial neuron.

**🖊 Board / on-screen**
- Write **"bias ≠ unfair bias ⚠️"** in red. ("Here bias = just a number added to the sum.")
- Write "Knowledge lives in **weights & bias**, not in the neuron".
- Quick sketch: dots of two colours split by **one straight line** → "1 neuron = straight-line boundary only".
- One-liner box: **inputs × weights + bias → activation → 1 output**.

---

### ⏱ 13:12–14:23 · [I] Concept 3: How a neural network works (definition + three layers)

**🎙 Spoken**
> Now let's come to the third topic: how does a neural network work? If one neuron is one brick, now let's build the wall. Write down the definition.
>
> *"A neural network is a set of artificial neurons arranged in layers (an input layer, one or more hidden layers, and an output layer), where the outputs of one layer become the inputs of the next."*
>
> So there are three kinds of layers. I'll draw it, watch. Three columns. First is the input layer. What is the input layer? It just holds the data, that's all. Our data: S = study hours, L = sleep hours. These are the same features we used in the Day 7 decision tree. Two circles. Note this down: the input layer doesn't calculate anything. It's just the gate the data comes in through.
>
> Second is the hidden layer. Why do we call it hidden? Because its values aren't directly visible to us. We only see the input we give and the output that comes out. What happens in the middle is hidden. Here the network builds some intermediate patterns. I'm drawing two neurons: h1 and h2.
>
> Third is the output layer: the final answer. For pass/fail, one neuron with sigmoid, just like our Student D neuron.

**🖊 Board / on-screen**
1. **[DEF CARD]** "A neural network is a set of artificial neurons arranged in layers (an input layer, one or more hidden layers, and an output layer), where the outputs of one layer become the inputs of the next." ✍️
2. Draw **3 columns** and write the headings: **Input layer** · **Hidden layer** · **Output layer**.
3. Input column: 2 circles labelled **S (study hrs)** and **L (sleep hrs)**. Small note: "just holds data, no calculation".
4. Hidden column: 2 circles **h1**, **h2**. Note: "hidden = we don't see these values".
5. Output column: 1 circle with a little σ S-curve: "Pass / Fail".

---

### ⏱ 14:23–14:43 · [I] Concept 3: fully connected

**🎙 Spoken**
> Now I'm drawing the lines. From S to h1, from S to h2, from L to h1, from L to h2: four lines. Every input is connected to every hidden neuron. This is called fully connected. Every line has its own weight. Then two lines from h1 and h2 to the output. Remember: every line = one weight.

**🖊 Board / on-screen**
1. Draw **all 4 lines** input → hidden (S→h1, S→h2, L→h1, L→h2), then **2 lines** hidden → output.
2. Label: "**Fully connected**: every neuron → every neuron in the next layer".
3. Write "1 line = 1 weight".

---

### ⏱ 14:43–16:20 · [I] Concept 3: the worked example, Sita's forward pass (notes prompt)

**🎙 Spoken**
> Now, just like we did in Day 7, I'm assuming the weights. In reality the machine learns them itself, and we'll see that in the next video.
>
> h1 = 1 × S + 0.5 × L − 6.
> h2 = 0.5 × S + 1 × L − 7.
> Output = sigmoid of (1 × h1 + 1 × h2 − 2).
>
> One small rule for the hidden neurons: if the sum comes out negative, that neuron gives output 0. It stays "off". If it's positive, the same number goes out. This rule has a name too, ReLU, and it's also an activation function. We'll see it in detail in the next video. For today: negative means off, positive means on. And there's no matrix stuff or calculus here. Real libraries do all this fast with matrix maths, but if I tell you that right now you'll get a bit flustered. If you know addition and multiplication, that's enough.
>
> Don't stress about the maths, it's just addition. Let's go slow. For example, suppose there's a student called Sita. She studied 6 hours, but slept only 3 hours. Exam tension, she stayed awake the whole night.
>
> h1: 1 into 6 = 6, 0.5 into 3 = 1.5, 6 plus 1.5 minus 6 = 1.5. Positive, so h1 = 1.5. On.
> h2: 0.5 into 6 = 3, 1 into 3 = 3, 3 plus 3 minus 7 = −1. Negative! So h2 = 0. Off.
> Output: 1 into 1.5, plus 1 into 0, minus 2 = −0.5. Sigmoid of −0.5 comes to 0.378. That means 38%. Less than 50%. So what did the network predict? Fail.
>
> This left-to-right flow, from input to hidden and from hidden to output, is called the forward pass. Write it down: the forward pass is the process by which the network gives a prediction.

**🖊 Board / on-screen**
1. Write each weight on its line: S→h1 **1**, L→h1 **0.5**, S→h2 **0.5**, L→h2 **1**, h1→out **1**, h2→out **1**. Small bias arrows: h1 **−6**, h2 **−7**, output **−2**.
2. Side box: "Hidden rule (for today): sum < 0 → output 0 (OFF) · sum > 0 → same number (ON). Name: **ReLU** → next video".
3. Put **Sita's numbers** in: **6** and **3** at the inputs.
4. h1 circle: "6 + 1.5 − 6 = **1.5** ✅ ON".
5. h2 circle: "3 + 3 − 7 = ~~−1~~ → **0** ❌ OFF" (strike through the −1).
6. Output: "1.5 + 0 − 2 = −0.5 → σ = **0.378** → 38% → FAIL".
7. Big arrow under the whole network: **"Forward pass →"**. ✍️ "Forward pass = how the network makes a prediction".

---

### ⏱ 16:20–17:15 · [I] Concept 3: Ravi & Kiran + the Sita twist (Video B hook)

**🎙 Spoken**
> I did the same calculation for two more students too. I'm putting it on the screen; if you have a calculator, check it. Ravi: studied 4 hours, slept 7 hours. Both neurons on: 82%, pass. Kiran: studied just 1 hour, slept 8 hours. h1 off, 38%, fail. Did you get the story? Sita studied well but didn't sleep: the "rest" neuron is off. Kiran slept but didn't study: the "study" neuron is off. Ravi did both: both are on, pass. In the Day 7 decision tree, we checked sleep hours after study hours, right? This is kind of like that. But what's the difference? The tree asks yes/no questions one after another; the network combines all the features with weights, smoothly, layer after layer.
>
> And here's a twist: Sita actually passed the exam! But our network said 38%. It got it wrong. So how will the network correct its own mistake? Hold on to that question. That's the next video.

**🖊 Board / on-screen**
- On-screen table (not drawn live):

  | Student | Study S | Sleep L | h1 | h2 | z = h1 + h2 − 2 | σ(z) | Prediction |
  |---|---|---|---|---|---|---|---|
  | Ravi | 4 | 7 | 1.5 ON | 2 ON | 1.5 | 0.818 | Pass (82%) |
  | Sita | 6 | 3 | 1.5 ON | 0 OFF | −0.5 | 0.378 | Fail (38%) |
  | Kiran | 1 | 8 | 0 OFF | 1.5 ON | −0.5 | 0.378 | Fail (38%) |
- Mini side-by-side: Day 7 tree (yes/no splits) vs network (weighted, smooth, layer by layer).
- Big red stamp on Sita's row: **"ACTUAL RESULT: PASS 😮 → network was wrong → how does it learn? NEXT VIDEO"**.

---

### ⏱ 17:15–18:34 · [I] Concept 3: anticipated doubts + "deep" + parameter count + recap

**🎙 Spoken**
> Now, some doubts. First: "Anna, so h1 is the 'did he study enough' neuron, and h2 is the 'did he sleep enough' neuron?" We gave those names ourselves, for the story. In real networks the hidden neurons learn whatever turns out to be useful, and most of the time they don't have a neat meaning we can understand. Don't get confused there.
>
> Second: so now, what does "deep" mean? If I add more hidden-layer columns here, 3, 10, 100, that's a deep network. That's all deep means.
>
> Third: "More layers is always better?" No. More layers need more data and more computation, and there's also a chance they mug up the training data and then fail on the testing data. We saw training vs testing in Day 3, right?
>
> Fourth: "Does the network look up the answer in some database?" No. Every time, it calculates the answer fresh using the weights.
>
> And how many numbers are in our small network? Let's count. In the hidden layer, 4 weights and 2 biases. At the output, 2 weights and 1 bias. 9 numbers in total. GPT-3, which came out in 2020, has 175 billion. Same idea, just much, much bigger.
>
> So, simple: data comes into the input layer, the hidden layers build patterns, and the output layer gives the answer. That's how a neural network works. I hope it's clearly understood.

**🖊 Board / on-screen**
1. Write over h1 / h2: "'study' / 'rest' = OUR labels for the story. Real hidden neurons ≠ neat meaning".
2. **Erase and redraw** with 3 hidden columns between input and output: "**Deep** = many hidden layers".
3. Myth list: ❌ "More layers always better" (more data, more compute, can overfit, Day 3) · ❌ "Looks up a database" → ✅ "calculates fresh every time".
4. Count on the board: "4 weights + 2 biases + 2 weights + 1 bias = **9 parameters**" vs a big number card: "**GPT-3 (2020): 175,000,000,000**".
5. One-liner box: **Input → Hidden (patterns) → Output (answer)**.

---

### ⏱ 18:34–19:38 · [W] Concept 4: Weights & biases (definition + unpack + 36-marks analogy)

**🎙 Spoken**
> Now the last topic, and in a way the most important one: weights and biases. Because in the whole network (ours has 9 numbers, GPT-3 has 175 billion), what are those numbers? Weights and biases. Write down the definition.
>
> *"Weights are numbers that decide how strongly, and in which direction, each input affects a neuron's output. A bias is a number added to the weighted sum that shifts how easily the neuron activates, whatever the inputs are. Together, weights and biases are the parameters that a neural network learns during training."*
>
> Let's break it down. Weight: "how strongly and in which direction". If there's a big positive weight, it pushes the prediction up strongly. If the weight is negative, it pulls it down. If the weight is near zero, it means "ignore this input".
>
> Bias: it's like a starting point, like a threshold. When b = −4, when does Student D's neuron say pass (z greater than zero)? Only when the weighted evidence comes to more than 4. In our exams you need 36 marks to pass, right? Below the cutoff means fail. This is just like that.

**🖊 Board / on-screen**
1. **[DEF CARD]** "Weights are numbers that decide how strongly, and in which direction, each input affects a neuron's output. A bias is a number added to the weighted sum that shifts how easily the neuron activates, whatever the inputs are. Together, weights and biases are the parameters that a neural network learns during training." ✍️
2. Redraw the Day 22 neuron. Draw the weight arrows with **thickness**: thick = big weight, thin = small; legend "+ pushes up · − pulls down · ≈0 ignored".
3. Write "b = −4 → need weighted evidence > 4 to PASS (like the 36-marks cutoff 📝)".

---

### ⏱ 19:38–20:00 · [W] Concept 4: knobs analogy

**🎙 Spoken**
> A simple analogy: you have a music system at home, right, with bass and treble knobs. Each knob controls one thing. Turn it and the sound changes. What are the knobs of a neural network? Weights and biases. So what is learning? Turning those knobs until the sound, meaning the prediction, comes out right. Just one difference: these knobs can go into negative too.

**🖊 Board / on-screen**
- Draw a music-system panel with knobs labelled **w1**, **w2**, **b** (and a spare **w3**). Caption: "Learning = turning the knobs till the prediction is right 🎛️ (knobs can go negative!)".

---

### ⏱ 20:00–21:01 · [W] Concept 4: turn the knobs on Student D (the worked example)

**🎙 Spoken**
> Let's turn the knobs on Student D and see: 4 hours, 80% attendance. Original: z = 2.4, 91.7%, pass.
>
> Knob 1: if we make the attendance weight 0, the model ignores attendance. z = 3.2 plus 0 minus 4 = −0.8. 31%. Fail! Same student, we changed just one knob, and he failed.
>
> Knob 2: let's make the examiner strict, bias −6. z = 6.4 minus 6 = 0.4. 60%. Pass, but only just. A lenient examiner, bias −2. z = 6.4 minus 2 = 4.4. 98.8%. Pass, and very sure. This is like grace marks: the bias shifts everyone in the same way.
>
> Knob 3: a negative weight. Let's add a new input: how many hours he spent on Instagram the night before the exam. Weight −0.5. Student D scrolled for 3 hours. −0.5 into 3 = −1.5. z = 2.4 minus 1.5 = 0.9. 71%. Still a pass, but the confidence dropped. Instagram pulled him down!
>
> So what's the lesson? Just change the weights or the bias, and the same student's prediction changes. So what is learning? Finding the correct weights and the correct bias. That's it.

**🖊 Board / on-screen**
1. Number line: 0 in the middle, "Fail ←│→ Pass". Put a dot at **2.4** (D).
2. Build this table live, one row at a time:

   | Knob turned | z | σ(z) | Decision |
   |---|---|---|---|
   | Original (w1 0.8, w2 0.04, b −4) | 3.2 + 3.2 − 4 = **2.4** | 0.917 | Pass |
   | w2 = 0 (ignore attendance) | 3.2 + 0 − 4 = **−0.8** | 0.310 | **Fail** |
   | b = −6 (strict) | 6.4 − 6 = **0.4** | 0.599 | Pass (barely) |
   | b = −2 (lenient / grace marks) | 6.4 − 2 = **4.4** | 0.988 | Pass (very sure) |
   | + Instagram 3 hrs × w3 −0.5 | 2.4 − 1.5 = **0.9** | 0.711 | Pass (less sure) |
3. Move the dot on the number line for each row (2.4 → −0.8 → 0.4 → 4.4 → 0.9).
4. Draw the Instagram arrow **dashed red** (negative weight).
5. Underline: "**Same student, different knobs → different prediction. Learning = finding the right knobs.**"

---

### ⏱ 21:01–22:15 · [W] Concept 4: anticipated doubts + "a model IS its weights" + recap

**🎙 Spoken**
> Doubts. First: "Anna, 0.04 is really small, right? So attendance isn't important?" Don't get confused! Attendance goes from 0 to 100, so 0.04 into 80 = 3.2, and study hours is 0.8 into 4 = 3.2. Same contribution. The size of a weight depends on the scale of its input. If we write the same attendance as a fraction, 0.8 instead of 80, the weight becomes 4: 4 into 0.8 = 3.2, the same contribution. Don't decide importance just by looking at the weight.
>
> Second: "Who puts in these weights? Programmers?" No. In Day 7, and today, we assumed them for the demo. In real training the network starts with small random weights, looks at the data, and adjusts them.
>
> Third: there's no rule that weights must be between 0 and 1, or that they're always positive. They can be any number, even negative, like Instagram.
>
> And one fun fact: when someone says "I downloaded an AI model", what did they actually mostly download? One big file full of weights and biases. A trained model, simply put, is its weights and biases.
>
> So, simple: what decides how much each input matters, and in which direction, is the weights; what shifts the starting point is the bias; together they're the parameters the network learns. That's what we call weights and biases.

**🖊 Board / on-screen**
- Write: "0.04 × 80 = 3.2 = 0.8 × 4 → **weight size depends on input scale**". Then: "80% as 0.8 → weight 4 → 4 × 0.8 = 3.2 (same!)".
- Write: "Weights: start **random** → **learned** from data (not typed by programmers)".
- Write: "Weights can be **any number**: +, −, big, small".
- Icon: 📁 "model file = weights & biases".
- One-liner box: **Weights = how much + which direction · Bias = shifts the starting point · Both = learned parameters**.

---

### ⏱ 22:15–22:55 · [J] Comment quiz

**🎙 Spoken**
> Now, today's quiz. Tell me the answers in the comments. Question 1: of these, which one do you use daily that runs on deep learning: face unlock, Google Lens, YouTube recommendations, the Google Translate camera, or all of them? Question 2: Student X studied 3 hours, 50% attendance. Using w1 = 0.8, w2 = 0.04, b = −4, what's z? Pass or fail? Question 3: if we change Student D's bias from −4 to −8, will he still pass? Question 4, for our network: a student studied 6 hours and slept 8 hours. Is h2 on or off? Pause the video, calculate with a calculator, and comment. Let's see how many of you get all four right!

**🖊 Board / on-screen**
- Quiz card with 4 numbered questions (as spoken). "⏸️ Pause → 🧮 calculate → 💬 comment". *(Answers are in production-notes.md, for the pinned comment.)*

---

### ⏱ 22:55–23:35 · [K] Video recap + expectation-setting

**🎙 Spoken**
> And that's it for the day. What did we cover in this video? What deep learning is: ML that uses neural networks with many layers to learn features on its own. What an artificial neuron is: inputs, weights, bias, activation, output, and the fact that Day 7's logistic regression is itself one neuron. How a neural network works: input layer, hidden layers, output layer, forward pass. And weights and biases: the knobs of the network. All of these come under AI, inside ML, under Deep Learning. If not everything is 100% clear in one go, don't stress. When I first learned this, it took me two or three days too. Watch it once more along with the notes.

**🖊 Board / on-screen**
- Back to the 3 circles; inside **DL** list: ① DL ② Neuron ③ Layers / forward pass ④ Weights & biases (tick each ✔).

---

### ⏱ 23:35–24:26 · [L] Outro: Video B teaser → notes → catch-up → share → sign-off

**🎙 Spoken**
> Now, a big question for the next video. Today, every weight was one we assumed. 0.8, 0.04, −4, 1, 0.5: I put them in myself. But in real life, how does the network get its weights? How does it learn? And Sita: the network said fail, and she passed. How will the network correct its own mistake? In the next video: activation functions, loss, gradient descent, backpropagation, meaning how a neural network learns. If you want that video quickly, like this one.
>
> Today's definitions, diagrams, calculations, all of it I'm putting as notes in the description. And whoever hasn't watched Day 1 to Day 8: it's not late at all yet. Only 9 videos are done; sit for just one day and you can cover all of them. Make your friends part of this AI Learning Series too. Thank you so much for watching, signing off, Tech Boy Deepak.

**🖊 Board / on-screen**
- Teaser card: "**Next:** How does a Neural Network LEARN? 🤔 Activation · Loss · Gradient Descent · Backpropagation". Sita's 38% ❌ with a "?" arrow.
- Lower third: "📒 Notes in description" · "▶️ Day 1–8 playlist" · Subscribe 🔔.
- End card.
