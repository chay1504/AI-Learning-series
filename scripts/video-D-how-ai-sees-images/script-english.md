# Video D: "How AI Sees Images" (English rendering for review)

**Series:** AI Learning Series, **Day 12** on the channel (Deep Learning Part 4). This covers plan Day 31 (what is computer vision?), Day 32 (what is a CNN? filters, feature maps, pooling) and Day 35 (build an image classifier: MNIST in Colab). Plan Days 33–34 go to Part 5.
**Recording script:** `script-telugu.md`. This file is a faithful English rendering of it, with the same segments, timestamps and cues. It is for checking content and accuracy. Do not record from it.
**Runtime:** ~25:43 (≈ 25.7 min): 4,394 English-equivalent spoken words at 175 wpm (25:07) plus ~36 s of Colab run pauses. Allow ~27 min with drawing pauses.
**Legend:** ⏱ timestamp (start–end) · 🎙 what he says · 🖊 what to draw, write or show (in order) · 💻 Colab screen-share cues (block names match the notebook) · 🔁 live result: say the number on your own screen if it differs

> **Production note on numbering:** Parts 1–3 are assumed to go out as Days 9, 10 and 11, so this video opens as **Day 12**. If the channel numbering changes, update the day number in segment A, the "only 12 videos" line in segment L, the title card, the title and the description (the notebook's title cell also says "Day 12").

---

## [A0] Cold-open hook + pitch
⏱ **00:00 – 00:33**

🎙
> After exams, the teacher writes the marks next to each question in red pen, right? 7, 5, 9. You read that handwritten 7 in one second. But to a computer it's just a photo: some numbers, you see. So how does it say "this is a 7"? So today we teach a computer to read. By the end of the video you'll train a model in Colab yourself and watch it read handwritten digits almost 99% correctly. If you want to learn AI from the basics, from scratch, subscribe to our channel. Let's dive into the video.

🖊
- Close-up B-roll: a red-pen "7" being written in the marks box of an answer sheet.
- Text pop: **"You see: 7 · Computer sees: numbers 🔢"**. Channel logo sting.

---

## [A] Welcome + headline promise
⏱ **00:33 – 00:47**

🎙
> Hey guys, welcome back to AI Learning Series Day 12! We've already reached Day 12, you see. Until now we've only worked with numbers, right? Today, for the first time, we go into images. How AI sees images: that's today.

🖊
- Title card: **AI Learning Series · Day 12 · How AI Sees Images** *(renumber if needed)*
- Badge: **"Deep Learning · Part 4"**

---

## [B] Recap of Days 9–11 + catch-up
⏱ **00:47 – 02:20**

🎙
> So first, let's recap once. On Day 9 we saw the neuron: inputs × weights + bias, then activation, then output. Layers, and our small network: study hours and sleep hours in, two hidden neurons, one output: 9 knobs. So on Day 10 we saw how it learns: ReLU, sigmoid, loss, gradient descent, backprop, and that loop: forward → loss → backprop → update → repeat.
>
> On Day 11 we saw epochs, batches, the learning rate and overfitting: validation is the mock test, test is the final exam. And we built that same 9-knob network in Keras. model.summary showed 9 parameters, right? 320 students, batch size 32, 100 epochs: that's 1,000 updates, you see. On test students the model had never seen, we got 90%. And Sita: with the knobs we guessed she got 38%, remember? The trained network said 95% pass.
>
> Quick answers to the last quiz. One: 60 ÷ 20 = 3 batches, 10 epochs: 30 updates. Two: that's overfitting, mugging up: stop near epoch 6. Three: with Dense 3, 6 + 3 + 3 + 1 = 13 params.
>
> At the end of the last video we left you with a question, right? Until now, numbers; so how does AI see a photo? And on Day 9 I drew a picture: an answer-sheet photo goes into the network, and the network learns the features by itself: first lines and edges, then letters, then words. Back then we didn't see how it does that. So today we open that box. If you haven't watched Days 9 to 11, watch them once and come back: every concept comes back today.

🖊
1. One neuron doodle: **inputs × weights + bias → activation → output**.
2. The 9-knob network: **S, L → h1, h2 → output**, with "9 knobs".
3. The Day 10 loop in a corner: **Forward → Loss → Backprop → Update → repeat ↺**.
4. Day 11 sticky note: **epoch · batch · learning rate · overfitting (validation = mock test, test = final exam) · Keras · 320 students · batch 32 → 10 batches/epoch · 100 epochs = 1,000 updates · test 90% · Sita 38% → 95% ✔**.
   Quick card: Day 11 quiz answers **30 updates · overfitting → stop near epoch 6 · 13 params**.
5. Flash Day 9's board: **answer-sheet photo → [network] → Pass**, with "edges → letters → words". Draw a big box around the network labelled **"black box → TODAY we open it 🔓"**.

---

## [C] Agenda
⏱ **02:20 – 02:39**

🎙
> So what are we going to see today? I'm writing it with the pen. First is computer vision: how an image looks to a computer. Second is CNN, the Convolutional Neural Network: filters, feature maps, pooling. This is the main topic. Third, we build an image classifier ourselves in Google Colab: a model that reads handwritten digits.

🖊
- Handwrite a numbered list:
  1. What is Computer Vision?
  2. What is a CNN? (filters · feature maps · pooling)
  3. Build an image classifier (MNIST in Colab)
- Corner note: **"Drawings first ✏️ → numbers → code last 💻"**

---

## [E] Reassurance + stakes + notes
⏱ **02:39 – 03:12**

🎙
> Many people think, "What is this, anna, convolution, pooling... even the names are scary," right? Don't be afraid at all. There's no new maths today: we multiply 9 numbers and add them, that simple. A Class 10 student can check it on a calculator. And a secret: there's almost nothing new in a CNN. Weights, bias, ReLU, loss, backprop: you already know all of them. Whether it's Google Lens or X-ray screening tools, a lot of the AI that works with images is built on these ideas. So it's very important. Everyone, take notes.

🖊
- Sticky note: **"New today: only how the neurons are connected. Everything else you already know ✔"**

---

## [F] CONCEPT 1: Computer vision

### F1. Announce + definition + name unpack
⏱ **03:12 – 03:51**

🎙
> So the first topic: computer vision. The definition is on screen. Write it down.
>
> *"Computer vision is the field of AI that enables computers to get useful information from images and videos: what is in them, where it is, or what it says."*
>
> What does that mean? It's right there in the name: vision for a computer, meaning sight. So a camera can take a photo, but understanding what's in that photo is a different thing. That understanding part is what we call computer vision, you see. Remember three phrases: what's in it, a cat or a dog; where it is; and what's written in it. These will come back in a little while.

🖊
1. Definition card (English). ✍️ "Write it down".
2. Split the name: **COMPUTER + VISION (sight)**. Doodle: camera 📷 → "takes the photo" vs 🧠 → "understands the photo" = computer vision.
3. Underline the three phrases: **what · where · what it says**.

### F2. An image is a grid of numbers (drawing first)
⏱ **03:51 – 04:58**

🎙
> Now the most important point here. How does a photo look to a computer? The way it looks to us? No. Just numbers: a table of numbers, you see. Look at the board: a small 6 by 6 grid, 36 squares, like our school graph book. Now I'll fill some squares and write a "1": a flag on top, a vertical line in the middle, a base at the bottom. Each of these little squares is what we call a pixel, you see: picture element. And every pixel is one number: black 0, full white 255, grey in between. In today's dataset the ink is white on a black background, so ink is 255 and empty is 0. The left side is what we see, the right side is what the computer sees. Write down the definition:
>
> *"A digital image is a grid of tiny squares called pixels. In a grayscale image, each pixel is one number from 0 (black) to 255 (white)."*
>
> When you fill squares in a graph book you get a picture, right? An image is just as simple. Real photos have lakhs or crores of those squares; that's the only difference.

🖊
1. Draw a **6 × 6 grid**. Shade the "1": row 1 col 3; row 2 cols 2–3 (flag); rows 3–5 col 3; row 6 cols 2–4 (base).
2. Beside it, the same grid as numbers (255 = ink, 0 = blank):
   ```
     0    0  255    0    0    0
     0  255  255    0    0    0
     0    0  255    0    0    0
     0    0  255    0    0    0
     0    0  255    0    0    0
     0  255  255  255    0    0
   ```
   Caption: **"What we see vs what the computer sees"**.
3. Label one square **"pixel = picture element"** and write **0 = black · 255 = white**.
4. Definition card (English). ✍️

### F3. Colour = 3 numbers + the size ladder
⏱ **04:58 – 05:29**

🎙
> So, a colour photo? Three numbers per pixel: Red, Green, Blue, RGB. Every pixel on your phone screen is three tiny lights. Red 255, green 0, blue 0: pure red. All three 255: white. All three 0: black. Write it down: grayscale means one number per pixel, colour means three. These are what we call channels, you see. Now the size: our grid is 36 numbers. In today's dataset, 28 × 28 = 784. And the Day 9 phone photo: 12 megapixels × 3, about 3.6 crore numbers for one photo!

🖊
1. One pixel blown up into three boxes: **R | G | B = 255 | 0 | 0 → red**. Below: **255 | 255 | 255 → white · 0 | 0 | 0 → black**.
2. Write: **Grayscale = 1 number per pixel · Colour = 3 numbers per pixel (3 channels)**. ✍️
3. Size ladder: **6 × 6 = 36 → 28 × 28 = 784 → 12 MP photo × 3 ≈ 3.6 crore numbers**.

### F4. Three vision tasks + where we see them + "not always deep learning"
⏱ **05:29 – 06:33**

🎙
> Computer vision has three main jobs: the same three phrases. The first is image classification: one label for the whole image, "this digit is 7". The thing that predicts a category is classification: we saw it on Day 6, right? 0 to 9 means 10 categories: multi-class. The second is object detection: a box around each object, like a traffic camera putting a box around a number plate. The third is segmentation: a label for every pixel: road, person, sky. So what we do today is classification, you see.
>
> Let me tell you the ones we see every day: Google Lens tells you a flower's name. Hyderabad traffic cameras read number plates, and the police verify before a challan is sent. There are apps that look at a leaf photo and tell farmers the pest or disease. But don't get confused: computer vision isn't always deep learning. A UPI QR-code scan is a camera and an image too, but it's read with fixed rules; there's no model to train. That means deep learning is needed when there's too much variety to write rules: handwriting, faces, leaves, X-rays.

🖊
1. Three small boxes side by side (✍️ write the three names):
   - **Classification:** whole photo → "7" / "Cat"
   - **Detection:** photo with rectangles → "Car", "Plate"
   - **Segmentation:** photo with coloured regions → "Road / Person / Sky"
   Tick **Classification** = "today".
2. Icon strip as he speaks: 🔍 Google Lens (flower → name) · 🚦 Traffic camera (plate → police verify → challan) · 🌿 Leaf photo → pest/disease · 🩻 X-ray → "possible TB, doctor to check".
3. QR code icon with a red stamp: **"Camera ✔, deep learning ✘ (fixed rules)"**. Next to it: **"DL = when rules are impossible to write: handwriting, faces, leaves"**.

### F5. Why a plain Dense network struggles: three fingers
⏱ **06:33 – 07:47**

🎙
> Now a doubt: "Anna, an image is just numbers, right? Isn't it enough to give these 784 numbers to the Day 11 Dense network?" It works, but there are three problems. Three fingers: write them down.
>
> First finger: far too many weights. Dense means fully connected. 784 pixels to 128 neurons: 784 × 128, plus 128 biases: 1,00,480 parameters! Day 11 had just 9. For a 12-megapixel colour photo, one layer alone would need about 460 crore. Impossible, right?
>
> Second finger: the neighbours are lost. To give it to Dense, the grid has to be laid out as one long line, row after row. That's called flatten. This pixel and the pixel below it are on the same stroke. But in the line they're 28 places apart! So Dense doesn't know they're neighbours. But in images all the meaning is in the neighbours.
>
> Third finger: when the digit moves a little. Shift a 7 three pixels to the right: for us it's the same 7, for Dense it's almost a new pattern. You can check this yourself in Block 13 at the end of the notebook: a Dense network that scores 97% on normal digits falls to 49% when every digit is shifted 3 pixels! So what's the answer to these three problems? Our next topic.

🖊
Draw three fingers ✋ and write one problem per finger (✍️):
1. **Too many weights:** 784 × 128 + 128 = **1,00,480** in layer 1 (vs Day 11's 9!). 12 MP colour photo → **≈ 460 crore**.
2. **Loses "nearby-ness":** 28 × 28 square → arrow "Flatten" → one long line of dots. Circle two pixels one above the other in the grid; in the line, draw them **28 dots apart**.
3. **Shifted digit = new pattern:** a "7", and the same "7" moved 3 squares right. Caption: **"Dense: 97% → 49% when shifted 3 pixels"**.

### F6. Doubt + one-line recap
⏱ **07:47 – 08:06**

🎙
> One more doubt: is face unlock image classification? Strictly, no. It's verification: "is this the same face as the registered one?" It uses neural networks, but the job is different. Simple: finding patterns in a grid of numbers to understand what's in the image, where it is and what's written in it: that is computer vision.

🖊
- Small chip: **Face unlock = verification ("same person?"), not classification**.
- Recap card: **Computer vision = finding patterns in a grid of numbers → what / where / what it says.**

---

## [H] CONCEPT 2: CNN (Convolutional Neural Network)

### H1. Announce + definition + name unpack
⏱ **08:06 – 08:49**

🎙
> So computer vision is done. Now the main concept: CNN, the Convolutional Neural Network. Write down the definition.
>
> *"A Convolutional Neural Network (CNN) is a neural network designed for grid-like data such as images. Instead of connecting every pixel to every neuron, it slides small learnable filters across the image to detect local patterns, and stacks layers to combine them into bigger shapes and objects."*
>
> The name has two parts. "Neural network": we know it: the same neurons, weights, layers. "Convolutional": this is the new word. That means sliding a small window across the image and doing a small calculation at every spot: that simple. The keywords: small learnable filters; local patterns, like a stroke or a corner; and layers stacked to make bigger shapes.

🖊
1. Definition card (English). ✍️
2. Split the name: **CONVOLUTIONAL = slide a small window + calculate at every spot** | **NEURAL NETWORK = same neurons, weights, layers ✔**.
3. Underline: **small learnable filters · local patterns · stacks layers**.

### H2. Filter = the teacher's 3 × 3 window (and it is our old neuron)
⏱ **08:49 – 09:59**

🎙
> So what's a filter? Write it down:
>
> *"A filter (also called a kernel) is a small grid of weights, usually 3 × 3. It looks at one small patch of the image at a time, multiplies each pixel by its weight, adds them up (plus a bias) and gives one number. Then it slides to the next position."*
>
> An example: a teacher has a piece of cardboard with a small 3 by 3 window cut out in the middle. She slides it over an answer sheet looking for only one thing: a tick mark. For each position she writes a score on a separate paper: a clear tick, 3; nothing, 0. That score sheet is what we call a feature map, you see. Another teacher with another window looks for cross marks: that's another filter. And a secret: 9 pixels × 9 weights, add, plus a bias. We've seen that somewhere, right? The Day 9 neuron! So a filter is just our old neuron looking through a small window. But don't take this as the exact example: the teacher already knows what a tick looks like. A CNN filter starts with random numbers and learns from data. Very important; I'll say it again.

🖊
1. Definition card (English). ✍️
2. Doodle: an answer sheet, a cardboard with a **3 × 3 window cut out**, arrows showing it sliding left → right, row by row. A separate "score sheet" grid beside it labelled **"feature map"**.
3. Second teacher with a different window: **"another filter → another pattern"**.
4. Write: **Filter = our Day 9 neuron looking through a small window (9 inputs × 9 weights + 1 bias)**.
5. Chip: **"Teacher knows the pattern; a CNN filter LEARNS it."**

### [G] Mid-roll CTA
⏱ **09:59 – 10:23**

🎙
> Sorry for interrupting in the middle of the video. Pause for one second and like it. Click the three dots and hit hype: it'll reach many more beginners like you. Many of the people watching this series still haven't subscribed. Our team tested today's Colab notebook in advance so you don't get errors; your like and subscribe gives us that same energy. Please support us. So, let's go back to the filter.

🖊
- Like / three-dots → **Hype** / Subscribe animation. Keep the filter definition card visible underneath so the cut back is seamless.

> **Note:** his usual stat is "90% of viewers are not subscribed". Only say a number if YouTube Studio supports it on the day of recording; otherwise keep the generic line above.

### H3. The worked convolution: one window, then the whole feature map (the one worked example)
⏱ **10:23 – 12:35**

🎙
> Don't stress about the maths: it's only multiply and add. Let's go slowly. Let's take our "1" grid. To keep it simple, I'm writing 255 as 1: ink is 1, empty is 0. That means we divided by 255; we'll do the same in the build. Now a filter, which I'm choosing myself: three rows, 1, 0, −1 in every row. When it's "bright on the left, dark on the right", it gives a big number: so it catches the right edge of a vertical stroke. This is what we call a vertical edge filter, you see.
>
> Step 1: this red 3 by 3 square on the top-left corner. Inside: 0 0 1, 0 1 1, 0 0 1. Multiply each pixel by the filter number in the same position. Left column: filter 1, pixels all 0: 0. Middle: filter 0: 0. Right column: filter −1, pixels 1, 1, 1: that gives −1, −1, −1. Add them: −3. I'm writing −3 in the first box of the feature map.
>
> Step 2: one pixel to the right. Patch: 0 1 0, 1 1 0, 0 1 0. Left column 0, 1, 0 times 1: 1. The rest are 0. Total 1.
>
> Step 3: one more. Patch: 1 0 0, 1 0 0, 1 0 0. Left column 1, 1, 1: 3! A big number. Why? The stroke is on the left, the right is empty: exactly the pattern the filter is looking for. A perfect match, you see.
>
> So, keep sliding like this: 4 positions per row, 4 rows: a 4 by 4 feature map. The full map is on screen. The third column is all 3s: "there's a vertical edge here from top to bottom". The first column is all −3: the opposite edge, which a flipped filter would catch. Write it down:
>
> *"A feature map is the grid of numbers a filter produces as it slides over the image. Big values show where the filter's pattern was found."*
>
> Simply put, it's a heat map showing everywhere the filter's pattern appears, you see. To be honest, when I first studied CNNs I didn't understand feature maps at all. It clicked when I drew a small grid like this on paper and calculated it by hand. Check the remaining boxes yourself with a calculator.

🖊
1. Redraw the "1" grid with **0 / 1** values (note "÷ 255"):
   ```
   0 0 1 0 0 0
   0 1 1 0 0 0
   0 0 1 0 0 0
   0 0 1 0 0 0
   0 0 1 0 0 0
   0 1 1 1 0 0
   ```
2. The filter, labelled **"Filter = vertical edge detector (WE chose it for class)"**:
   ```
   1  0  -1
   1  0  -1
   1  0  -1
   ```
3. **Red 3 × 3 square** over the top-left corner. Write the 9 multiplications beside it: `0 0 −1 / 0 0 −1 / 0 0 −1` → **sum = −3**. Write −3 in the top-left cell of an empty 4 × 4 grid labelled **"Feature map"**.
4. Slide the red square right: write **1**, then **3** (circle the 3: "perfect match ✔").
5. Reveal the full map on a slide:
   ```
   -3  1  3  0
   -3  1  3  0
   -3  0  3  0
   -3  0  3  1
   ```
   Highlight the column of 3s: **"vertical edge here, top to bottom"**. Note on the −3 column: **"opposite edge (needs a flipped filter)"**.
6. Definition card (English). ✍️

> **Note (keep only if true):** the two lines "when I first studied CNNs I didn't understand feature maps… it clicked when I drew a grid on paper" are a personal claim. Keep them only if this really happened to him; otherwise cut them (about −8 s). See production-notes §8.3.

### H4. ReLU + max pooling
⏱ **12:35 – 13:38**

🎙
> Next: ReLU on this map, which we saw on Day 10: negative becomes 0. So all the −3s become 0: "the pattern isn't here". The same ReLU that switched off Sita's h2. Now pooling. Write it down:
>
> *"Max pooling shrinks a feature map by keeping only the largest value in each small block, usually 2 × 2. It keeps the strongest signal and makes the network a little less sensitive to small shifts."*
>
> We split the 4 by 4 map into four 2 by 2 blocks and keep only the biggest in each. Top-left 0, 1, 0, 1: 1. Top-right: 3. Bottom-left, all 0: 0. Bottom-right: 3. So from 16 numbers to 4: 1, 3, 0, 3. Like a principal saying, "I don't need all four unit-test marks, just tell me the best one." The map became a quarter of the size, but the message isn't lost: a strong vertical stroke on the right side. Don't get confused: max pooling means maximum, not average. Why pool at all? Fewer numbers, fewer calculations. And even if the stroke moves one pixel, the block's max often doesn't change.

🖊
1. Redraw the map with the −3s crossed out → 0, labelled **"ReLU"**:
   ```
   0  1  3  0
   0  1  3  0
   0  0  3  0
   0  0  3  1
   ```
2. Definition card (English). ✍️
3. Thick lines split it into four 2 × 2 blocks. Circle the max in each → a 2 × 2 grid **[1 3 / 0 3]**. Caption: **"Max pooling: keep the strongest · 16 → 4 numbers"**.
4. Report-card doodle: four unit-test marks → "best mark only".
5. Chip: **MAX, not average**.

### H5. Different filters see different things + filters are LEARNED + parameter sharing
⏱ **13:38 – 15:08**

🎙
> Now if we turn this same filter sideways, 1 1 1, 0 0 0, −1 −1 −1, it's a horizontal edge filter. On our "1", after pooling it's almost all 0: 1, 0, 0, 0; a "1" is mainly a vertical stroke, right? On a "7": the map's first row is 3, 2, 2, 1: the bar on top! So a 1 lights up the vertical detector, and a 7 the horizontal one. Combine detectors and you can tell digits apart, right?
>
> Now a very, very important point. Write it down: in a real CNN, nobody designs the filters. I chose 1, 0, −1 only for class, like assuming w = 0.8 on Day 7. Real filters start random, and backprop and gradient descent together change them like the other weights. The network itself learns which patterns to look for. On Day 9 we said "it learns the features by itself", right? This is what that means.
>
> And one filter = 9 weights + 1 bias = 10 numbers, and the same ones at every position in the image, because a vertical stroke is a vertical stroke wherever it is. Like one rubber stamp across the whole page. This is what we call parameter sharing, you see. Our first layer has 32 filters: 320 parameters. In a Dense layer, just 784 pixels to 32 neurons is 25,120. First finger solved. A filter always looks at neighbours together: second finger solved. The same filter searches everywhere, so a shifted stroke is found too, with a little help from pooling: third finger mostly solved.

🖊
1. Slide: the horizontal filter `1 1 1 / 0 0 0 / −1 −1 −1`, and two results side by side:
   - On the **"1"** → pooled **[1 0 / 0 0]** ("almost nothing")
   - On a **"7"** (show the tiny 6 × 6 "7") → map first row **3 2 2 1** ("the top bar!") → pooled **[3 2 / 0 1]**
   Caption: **"1 lights up the vertical detector · 7 lights up the horizontal detector"**.
2. Big boxed note ✍️: **Filters are LEARNED, not hand-designed. Start random → backprop + gradient descent update them.** Small: *"Board filter = for class only (like w = 0.8 on Day 7)"*.
3. Rubber-stamp doodle: one stamp pressed all over a page → **"same 10 numbers everywhere = parameter sharing"**.
4. Card: **1 filter = 9 + 1 = 10 · 32 filters = 320 · Dense 784 → 32 = 25,120**.
5. Go back to the three fingers and tick each: **✔ fewer weights · ✔ neighbours kept · ✔ (mostly) finds it anywhere**.

### H6. The full CNN stack
⏱ **15:08 – 15:58**

🎙
> Now the whole CNN in one picture: today's most important drawing. Write it down. Image → Conv + ReLU → Pool → Conv + ReLU → Pool → Flatten → Dense → Softmax → answer. Read it like a factory line. The first Conv catches small edges. Pool: shrink. The second Conv combines edges into shapes: corners, loops, the bar on top of a 7. Pool again. So Flatten isn't a problem now, because the important features have already come out. Then Dense, our Day 9 network, decides: "loop on top, vertical stroke on the right: this is a 9". Edges → shapes → which digit. Simple to complex, like the Day 9 example of a relative coming from far away, but only for that idea: a CNN sees small edges first. And most of the time real filters don't have neat names like "loop detector".

🖊
- Big pipeline across the bottom of the board (keep it there for the build):
  **Image → [Conv + ReLU] → [Pool] → [Conv + ReLU] → [Pool] → Flatten → Dense → Softmax → "7"**
- Under the stages write: **"edges" → "shapes / parts" → "which digit?"** ✍️
- Chip: **"Analogy: simple → complex only. CNN sees small edges first. Real filters rarely have neat names."**

### H7. Softmax: percentages that add to 100
⏱ **15:58 – 16:57**

🎙
> The last box: softmax. On Day 10 I only told you the name. Write it down:
>
> *"Softmax turns the output layer's raw scores into probabilities that are all positive and add up to 100%. The biggest score gets the biggest share."*
>
> The last layer has 10 neurons, a score for each digit. Let's take three: "1" gets 3, "7" gets 1.5, "4" gets 0.5. Softmax makes each score positive with e to the power (the same e, 2.718), then divides by the total. Result: "1" is 76.6%, "7" 17.1%, "4" 6.3%. Total 100%. The formula is in the corner; the machine does it. And what if there are only two classes, pass and fail? Give Student D scores 2.4 and 0 and you get 91.7% and 8.3%: exactly the Day 7 sigmoid! The sigmoid is two-class softmax, you see. Don't get confused: softmax gives percentages; picking the biggest is a separate last step, like the 50% threshold. And 99% means 99% sure, not always correct. You'll see this in the build.

🖊
1. Definition card (English). ✍️
2. Table:

   | Digit | Score | → Softmax |
   |---|---|---|
   | "1" | 3.0 | **76.6%** |
   | "7" | 1.5 | **17.1%** |
   | "4" | 0.5 | **6.3%** |
   | Total | | **100%** |

3. Small corner card (do not dwell): *e^score ÷ total · e ≈ 2.718 · e³ = 20.09, e^1.5 = 4.48, e^0.5 = 1.65, total 26.22*.
4. Under it: **"2 classes → same as sigmoid: Student D 2.4 vs 0 → 91.7% / 8.3%"**.
5. Chip: **"Softmax gives %s · picking the biggest = a separate step · 99% sure ≠ always right"**.

### H8. Same learning loop + doubts + one-line recap
⏱ **16:57 – 17:37**

🎙
> A doubt: "Anna, is CNN training some new method?" No! The same Day 10 loop: forward, loss, backprop, update, repeat. The same log loss: if the true digit is "1" and the model gives 76.6%, the loss is 0.27. Backprop sends that blame to the numbers in the filters too, and gradient descent changes them a little. Write this down: how it learns isn't new. How the neurons are connected: that's the only new thing. "Anna, does a CNN catch the digit wherever it is?" Not completely: I'll show you the real numbers after the build. Simple: sliding filters to find patterns, shrinking with pooling, stacking layers, and giving percentages with softmax: that is a CNN. That simple.

🖊
1. Point to the Day 10 loop in the corner: **Forward → Loss → Backprop → Update ↺** and add an arrow from "Backprop" into the filter drawing: **"blame reaches the filters too"**.
2. Write: **True "1", model 76.6% → loss = −ln(0.766) = 0.27**.
3. Big line ✍️: **"Nothing new in HOW a CNN learns. Only HOW the neurons are connected is new."**
4. Recap card: **CNN = slide filters → feature maps → ReLU → pool → stack → Dense → softmax %.**

---

## [I] CONCEPT 3: Build an image classifier (MNIST in Colab)

### I1. Open the notebook + the dataset
⏱ **17:37 – 18:12**

🎙
> So the theory is done. Now my favourite part: the build. The notebook link is in the description; run it along with me. No line-by-line code: I'll say what each block does and show where it is on the board. So the dataset is MNIST: 70,000 handwritten digits, 60,000 for training, 10,000 for testing. It's the "hello world" of computer vision: a simple version of reading answer-sheet marks or the PIN code on a postal cover, you see. Runtime → Change runtime type: a normal CPU is enough, a few minutes of training; with a T4 GPU it's even faster.

💻
- Screen-share Colab with `part-4-build-an-image-classifier.ipynb` open at the title cell. Cursor on the "plan, block by block" list.
- Show **Runtime → Change runtime type** menu for 2 seconds.

🖊
- Lower-third: **"Notebook link in description ↓"**. Name card: **MNIST: 60,000 training + 10,000 test images · 28 × 28 · digits 0–9**.
- Put the 7-box flow on the side of the board (tick each as it runs): **Load & look → ÷255 → Build CNN → Compile + Train → Test → Predict → Mistakes**.

### I2. Block 1: Setup + Block 2: Load the dataset
⏱ **18:12 – 18:42**

🎙
> Block 1: Setup: NumPy for numbers, Matplotlib for pictures, and Keras, the one we used on Day 11. We fix the seed so the starting weights are the same every time. Run. Block 2: Load the dataset: MNIST is right inside Keras. 60,000 training images, 28 by 28; 10,000 test images; and a label for every image: our answer key. That means features are pixels, the label is the digit.

💻
- Run **Block 1: Setup** (prints the TensorFlow / Keras versions). *(run pause ~3 s)*
- Run **Block 2: Load the dataset**. Highlight `Training images: (60000, 28, 28)`, `Test images: (10000, 28, 28)` and `First 10 labels: [5 0 4 1 9 2 1 3 1 4]`. *(run pause ~3 s; first run downloads the data, so run it once before recording)*

🖊
- Tick box 1 "Load & look". Write **features = pixels · label = digit (answer key)**.

### I3. Block 3: An image is just a grid of numbers
⏱ **18:42 – 19:05**

🎙
> Block 3: "An image is just a grid of numbers". The first training image as numbers. Pause and look: 0s all around, big numbers like 253, 255 in the middle. Follow them with your eyes... you can see a 5, right! The label is 5 too. On the board, 6 by 6; here, 28 by 28. Below, 18 images as pictures.

💻
- Run the first cell of **Block 3**. Zoom into the printed 28 × 28 grid; trace the 5 with the cursor. Show `Label: 5`. *(run pause ~2 s)*
- Run the second cell: the 3 × 6 grid of digit pictures with labels.

🖊
- Point from the screen to the board's 6 × 6 "1": **"same idea, 28 × 28 = 784 numbers"**.

### I4. Block 4: Prepare the data
⏱ **19:05 – 19:24**

🎙
> Block 4: Prepare the data: divide by 255, so everything is between 0 and 1, just like we did on the board, right? small numbers keep learning smooth. And add one channel: 1 for grayscale, it would be 3 for colour. New shape: 60,000, 28, 28, 1: min 0, max 1.

💻
- Run **Block 4: Prepare the data**. Highlight `New shape: (60000, 28, 28, 1) | min: 0.0 | max: 1.0`. *(run pause ~2 s)*

🖊
- Tick box 2 "÷255". Point to the board's "÷ 255 → 0/1" grid.

### I5. Block 5: Build a small CNN
⏱ **19:24 – 20:05**

🎙
> Block 5: Build a small CNN. This block = the CNN stack we drew on the board! Top to bottom: Conv2D 32, 3 by 3: our filter layer, but 32 filters, all starting random, with relu. MaxPooling2D 2 by 2: our pooling. Conv2D 64 again, pooling. Flatten. Dense 64: the Day 9 layer. Dense 10, softmax: 10 percentages. The sizes: 28 to 26, the way 6 became 4 on the board, then 13, 11, 5. Run it and look at model.summary: Day 11 had 9 parameters; here 1,21,930. And about 84%, that is 1,02,464, sit in that one Dense 64 layer! The two Conv layers together have only 18,816, because the filters are shared, right?

💻
- Show **Block 5: Build a small CNN** code cell. Move the cursor down the layers one by one while he names them; on screen, draw an arrow from each code line to the matching box of the board pipeline.
- Run it. Zoom into `model.summary()`: Output Shape column (26, 26, 32 → 13, 13, 32 → 11, 11, 64 → 5, 5, 64 → 1600 → 64 → 10) and **Total params: 121,930**. *(run pause ~2 s)*

🖊
- Tick box 3 "Build CNN". Under the board pipeline write the real sizes: **28×28 → 26×26×32 → 13×13×32 → 11×11×64 → 5×5×64 → 1,600 → 64 → 10**.
- Card: **121,930 params · Dense(64) = 102,464 (84%) · both Conv layers = 18,816**.
- Small footnote on the card (don't read it out): *2nd Conv: each filter looks at all 32 maps → 3 × 3 × 32 + 1 = 289 numbers · × 64 filters = 18,496 · + 320 = 18,816*.

### I6. Block 6: Compile + Block 7: Train
⏱ **20:05 – 21:10**

🎙
> Block 6: Compile, like Day 11. Optimizer adam: the smarter gradient descent whose name I told you on Day 10. Loss: sparse categorical crossentropy. A big name; don't be scared: the Day 10 log loss for 10 classes: −ln(the percentage given to the correct digit). "Sparse" means the labels are plain numbers like 7, that's all. Metric: accuracy. Block 7: Train: model.fit, our Day 10 loop. 5 epochs, batch size 128, validation split 0.1: it keeps 6,000 images aside for a mock test. So 54,000 ÷ 128 = 421.9, round up: 422 batches per epoch, that's the 422/422: write this calculation down. I'm running it... Epoch 1: accuracy about 92.8%. Epoch 5: 99.1%. Loss from 0.25 to 0.03. Validation, on images it doesn't learn from: about 99%, close to training. None of the overfitting gap we saw on Day 11. On Day 11 we needed 100 epochs; here 5 are enough, because each epoch already has 422 updates, you see.

💻
- Show **Block 6: Compile**, run it (instant).
- Show **Block 7: Train**. Point at `epochs=5`, `batch_size=128`, `validation_split=0.1`. Run. **Edit: speed up / time-lapse the training wait to ~10 s on screen.** *(run pause ~10 s after time-lapse)* Point at `422/422` and the epoch lines. 🔁 Reference values: epoch 1 `accuracy: 0.9280 – loss: 0.2492 – val_accuracy: 0.9808`; epoch 5 `accuracy: 0.9912 – loss: 0.0289 – val_accuracy: 0.9895`.
- Run the plot cell ("Learning progress").

🖊
- Tick box 4 "Compile + Train". Note beside the Day 10 loop: **"fit = this loop · 5 epochs × 422 batches"**.
- Card: **54,000 ÷ 128 = 421.9 → 422 batches per epoch**.

### I7. Block 8: Test on 10,000 new images
⏱ **21:10 – 21:35**

🎙
> Block 8: Test on 10,000 new images: the real exam. Images the model has never seen even once, like new questions after coaching-centre practice. Test accuracy: 98.85%! That means about 9,885 correct, only 115 wrong. Write it down: the honest score is on test data, not training data. Your number may be a little different, 98.6, 99.0: that's normal. If you get about 99%, it's working.

💻
- Show **Block 8: Test on 10,000 new images**, run. Zoom: 🔁 `Test accuracy: 98.85%   (test loss: 0.0352)` and `That is about 9885 correct out of 10,000.` *(run pause ~2 s)*

🖊
- Tick box 5 "Test". Big stamp: **98.85% · 9,885 / 10,000 ✔** 🔁 ✍️ **"Honest score = TEST data, not training data"**.

### I8. Block 9: Predict one image
⏱ **21:35 – 21:54**

🎙
> Block 9: Predict one image: test image 0, a handwritten 7, like the 7 the teacher wrote at the start. Run... 7: 99.999%! The rest are almost 0: just one tall bar. Softmax percentages, total 100. Model says 7, true answer 7. Change idx and try any image up to 9999.

💻
- Show **Block 9: Predict one image**, run with `idx = 0`. Zoom into the list: 🔁 `7:  99.999%`, all others `0.000%`, and `Model says: 7 | True answer: 7`. Show the image + bar chart. *(run pause ~2 s)*

🖊
- Tick box 6 "Predict". Sketch the bar chart: one tall bar at **7 (99.999%)**, flat everywhere else. Note: **"softmax: all 10 add to 100%"**.

### I9. Block 10: The images it got wrong
⏱ **21:54 – 22:39**

🎙
> Block 10: The images it got wrong: my favourite block. The first 10 of the 115 mistakes. Image 18: true 3, the model said 5, 44% sure. Be honest: doesn't that 3 look like a 5 to you too? Image 717: a 0 leaning to one side; the model said 5. Even a teacher would squint at these. In the top-2 list: in 9 of these 10, the correct answer was the model's second choice; in image 18 it gave 39% to 3: so the model had a doubt, you see. But image 449: true 3, the model said 5, 99% sure! I told you at softmax, right? 99% sure doesn't mean correct. Confidence is one thing, correctness another. Remember this.

💻
- Show **Block 10: The images it got wrong**, run the first cell: 🔁 `Wrong: 115 out of 10000 test images` and the 2 × 5 picture grid. Circle **image 18** ("True 3 | Said 5 (44% sure)") and **image 717** ("True 0 | Said 5"). *(run pause ~3 s)*
- Run the second cell (top-2 list). Highlight 🔁 `Image   18: true 3 | model: 5 44%, 3 39%` and `Image  449: true 3 | model: 5 99%, 3 1%`.

🖊
- Tick box 7 "Mistakes". Pin up three mini-cards: **#18: True 3 · Said 5 · 44% (2nd guess 3: 39%)** · **#717: True 0 · Said 5 · 56%** · **#449: True 3 · Said 5 · 99% 😮**.
- Write ✍️: **"99% sure ≠ correct. Confidence ≠ correctness."** and **"9 of 10: right answer = 2nd guess"** 🔁.

### I10. Block 11 (optional): Try it yourself + Block 12: Homework, Fashion-MNIST
⏱ **22:39 – 23:21**

🎙
> Block 11, optional: Try it yourself. In (a) we put the board's 1, 0, −1 filter on a real 7: in the vertical map the slanted stroke lights up, in the horizontal map the bar on top. In (b), 8 feature maps from filters the trained model learned by itself: nobody designed them. Some are catching edges: Day 9's "first lines and edges", in front of your eyes. Block 12: Homework, Fashion-MNIST: one line in Block 2, fashion_mnist instead of mnist, then Run all. So, the same CNN, now 10 kinds of clothes and shoes. Higher than digits or lower? What does it confuse? Tell me your accuracy in the comments.

💻
- Run **Block 11 (optional): Try it yourself** (a): show "Original / Vertical filter + ReLU / Horizontal filter + ReLU" for test image #0. Cursor on the top bar in the horizontal map and the slanted stroke in the vertical map. *(run pause ~2 s)*
- Run (b): the 8 learned feature maps ("filter 0 … filter 7"). Point at 2–3 that look like edge maps (say only what is visible on your screen). *(run pause ~2 s)*
- Scroll to **Block 12: Homework, Fashion-MNIST**. Show the one-line change `dataset = keras.datasets.fashion_mnist` in Block 2 (do **not** run it on camera).

🖊
- Homework card: **Block 2 → `keras.datasets.fashion_mnist` → Runtime → Run all → comment your test accuracy + the items it confuses**.

### I11. Block 13 (optional): Dense vs CNN, and shifted digits + one doubt
⏱ **23:21 – 24:04**

🎙
> Last card: Block 13, optional. With the same 5 epochs we also trained a normal Dense network: 97.0% on test, about 299 mistakes; the CNN has 115: about 2.6 times fewer. With every digit shifted 3 pixels: Dense 49%, CNN 88%. The CNN dropped too, it's not immune, but it's much better. The usual fix is data augmentation, meaning you also give shifted copies in training: name only. Why CNNs for images? That's why. Write it down. And if you give it a photo of your handwriting, will it read it? Directly, it'll struggle: MNIST digits are centred, 28 by 28, white on black. You'd first crop, resize and flip the colours. 99% means 99% on MNIST-style digits.

💻
- Scroll to **Block 13 (optional): Dense vs CNN, and shifted digits** and run it (pre-run once before recording; time-lapse the Dense training wait). *(run pause ~3 s after time-lapse)* Zoom into the table: 🔁 `Dense | 97.01% | 49.46%` and `CNN | 98.85% | 87.75%`, then the "Test image 0 / Shifted 3 px right" pictures.

🖊
- Final card ✍️:

  | | Dense (Flatten → 128 → 10) | CNN (ours) |
  |---|---|---|
  | Test accuracy | 97.0% (≈ 299 wrong) | **98.85% (115 wrong)** |
  | Digits shifted 3 px | 49% | **88%** |

  Caption: **"This is why we use CNNs for images." · Fix for shifts: data augmentation (name only)**.
- Chip: **"Your own photo → crop · centre · 28 × 28 · white-on-black first"**.

---

## [J] Comment quiz
⏱ **24:04 – 24:40**

🎙
> Now today's quiz: tell me in the comments. One: a colour photo is 100 by 100 pixels: how many numbers for the computer? Two: the vertical filter, 1, 0, −1 in every row, on this patch: 1, 0, 0 in every row. What number comes out? Three: max-pool this 2 by 2 block: 2, 7, 0, 5. Four, a trick question: which is not deep-learning image classification? (a) Google Lens naming a flower, (b) a UPI QR-code scan, (c) an app that looks at a leaf photo and tells the disease. Let's see who gets all four right. Don't forget your Fashion-MNIST accuracy too.

🖊
- Quiz card:
  1. Colour photo, 100 × 100 pixels → how many numbers?
  2. Filter `1 0 −1` (3 rows) on patch rows `1 0 0` (3 rows) → ?
  3. Max-pool this 2 × 2 block: **2, 7, 0, 5** → ?
  4. NOT deep-learning image classification? (a) Google Lens naming a flower (b) scanning a UPI QR code (c) a leaf-disease app
  *(Answers go in production notes. Don't show them on screen.)*

---

## [K] Video recap
⏱ **24:40 – 25:02**

🎙
> And that's it for the day! In this video: computer vision, an image is a grid of numbers; CNN: filters, feature maps, ReLU, max pooling, softmax, and the machine learns the filters itself; and we built a classifier ourselves on MNIST, about 99% test accuracy. All of these come in AI, in ML, in deep learning, in the computer vision branch, you see.

🖊
- Taxonomy line: **AI → ML → Deep Learning → Computer Vision → CNN → MNIST classifier (≈ 99%)**.
- Keep the CNN stack drawing on screen.

---

## [L] Outro
⏱ **25:02 – 25:43**

🎙
> Even if convolution isn't fully clear in one go, don't stress: draw a 6 by 6 grid on paper and calculate one window yourself; it'll click. So the notes (definitions, drawings, numbers) and the Colab notebook link are both in the description.
>
> Today AI learned to see. In the next video: how does AI read text? How does ChatGPT understand our sentence? NLP, RNN, LSTM and Transformers: the T in ChatGPT is Transformer. If you want that video, like this one.
>
> It's not late yet: just 12 videos, and you can cover them if you sit for one day. Add your friends to the AI Learning Series too.
>
> Thank you so much for watching, signing off, Tech Boy Deepak.

🖊
- The CNN stack stays on screen.
- Lower-third: **"Notes + Colab notebook in description ↓"**.
- End card: **Next: How AI Reads Text (NLP · RNN · LSTM · Transformer)** + the previous-video tile (Day 11).
