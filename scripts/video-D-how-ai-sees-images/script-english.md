# Video D: "How AI Sees Images" (English rendering for review)

**Series:** AI Learning Series, **Day 12** on the channel (Deep Learning Part 4). This covers plan Day 31 (what is computer vision?), Day 32 (what is a CNN? filters, feature maps, pooling) and Day 35 (build an image classifier: MNIST in Colab). Plan Days 33–34 go to Part 5.
**Recording script:** `script-telugu.md`. This file is a faithful English rendering of it, with the same segments, timestamps and cues. It is for checking content and accuracy. Do not record from it.
**Runtime:** @@RUNTIME@@
**Legend:** ⏱ timestamp (start–end) · 🎙 what he says · 🖊 what to draw, write or show (in order) · 💻 Colab screen-share cues (block names match the notebook) · 🔁 live result: say the number on your own screen if it differs

> **Production note on numbering:** Parts 1–3 are assumed to go out as Days 9, 10 and 11, so this video opens as **Day 12**. If the channel numbering changes, update the day number in segment A, the "only 12 videos" line in segment L, the title card, the title and the description (the notebook's title cell also says "Day 12").

---

## [A0] Cold-open hook + pitch
⏱ **@@A0@@**

🎙
> After exams, answer sheets get corrected, right? Next to each question the teacher writes the marks in red pen: 7, 5, 9. You read that handwritten 7 in one second. But a computer? To it, it's just a photo: some numbers. So how does a computer look at those numbers and say "this is a 7"? Today we teach a computer to read. By the end of the video you'll train a model in Colab yourself and watch it read handwritten digits almost 99% correctly. If you want to learn AI from the basics, from scratch, subscribe to our channel. Let's dive into the video.

🖊
- Close-up B-roll: a red-pen "7" being written in the marks box of an answer sheet.
- Text pop: **"You see: 7 · Computer sees: numbers 🔢"**. Channel logo sting.

---

## [A] Welcome + headline promise
⏱ **@@A@@**

🎙
> Hey guys, welcome back to AI Learning Series Day 12! We've already reached Day 12, you see. Today's video is very special: until now we've only worked with numbers. Today, for the first time, we go into images. How AI sees images: how AI actually looks at an image and understands it. That's today.

🖊
- Title card: **AI Learning Series · Day 12 · How AI Sees Images** *(renumber if needed)*
- Badge: **"Deep Learning · Part 4"**

---

## [B] Recap of Days 9–11 + catch-up
⏱ **@@B@@**

🎙
> So first, let's recap once. This is our fourth video in deep learning. On Day 9 we saw what's inside a neural network: the neuron, inputs × weights + bias, then activation, then output. Layers: input, hidden, output. And our small network: study hours and sleep hours go in, two hidden neurons, one output. 9 knobs in total: those are the weights and biases.
>
> On Day 10 we saw how that network learns: ReLU, sigmoid, loss, gradient descent, backpropagation. Remember the loop? Forward pass → loss → backprop → update → repeat.
>
> On Day 11, for the first time, we built it ourselves in Keras. The same 9-knob network: model.summary showed 9 parameters, right? We compiled it and fit it: 320 training students, batch size 32, so 10 batches per epoch, 100 epochs, 1,000 updates in total. When we evaluated on test students the model had never seen, we got 90%. And our Sita: with the knobs we guessed on Day 9 the network said 38%, remember? The trained network correctly said 95% pass.
>
> At the end of the last video we left you with a question, right? Until now we worked with numbers, so how does AI see a photo? And on Day 9 I drew a picture: an answer-sheet photo goes into the network, and the network learns the features by itself: first lines and edges, then letters, then words. Back then we left it as a black box. Today we open that box.
>
> If you haven't watched Days 9, 10 and 11, please watch them once and come back. Every concept from those three videos comes back today.

🖊
1. One neuron doodle: **inputs × weights + bias → activation → output**.
2. The 9-knob network: **S, L → h1, h2 → output**, with "9 knobs".
3. The Day 10 loop in a corner: **Forward → Loss → Backprop → Update → repeat ↺**.
4. Day 11 sticky note: **Keras · 320 students · batch 32 → 10 batches/epoch · 100 epochs = 1,000 updates · test 90% · Sita 38% → 95% ✔**.
5. Flash Day 9's board: **answer-sheet photo → [network] → Pass**, with "edges → letters → words". Draw a big box around the network labelled **"black box → TODAY we open it 🔓"**.

---

## [C] Agenda
⏱ **@@C@@**

🎙
> So what are we going to discuss today? I'm writing it with the pen, look. First is computer vision: how an image actually looks to a computer. Second is CNN, the Convolutional Neural Network: filters, feature maps, pooling. That's today's main topic. Third, we build an image classifier ourselves, in Google Colab: a model that reads handwritten digits. Right after learning the theory, you'll see it working with your own eyes.

🖊
- Handwrite a numbered list:
  1. What is Computer Vision?
  2. What is a CNN? (filters · feature maps · pooling)
  3. Build an image classifier (MNIST in Colab)
- Corner note: **"Drawings first ✏️ → numbers → code last 💻"**

---

## [E] Reassurance + stakes + notes
⏱ **@@E@@**

🎙
> What do many people think? "What is this, anna, convolution, pooling, feature maps... even the names are scary." Right? Don't be afraid at all. There's no new maths today. We draw a small grid, multiply 9 numbers and add them. That's all. A Class 10 student can check it on a phone calculator. And I'll tell you a secret: there's very little new to learn in a CNN. Weights, bias, ReLU, loss, backprop: you already know all of them. After listening you'll say, "Is that all, anna? We thought this was hard."
>
> Whether it's Google Lens or AI that looks at X-rays to help doctors, a lot of the AI tools that work with images are built on these ideas. So it's very important. Everyone, take notes.

🖊
- Sticky note: **"New today: only how the neurons are connected. Everything else you already know ✔"**

---

## [F] CONCEPT 1: Computer vision

### F1. Announce + definition + name unpack
⏱ **@@F1@@**

🎙
> So the first topic: computer vision. I'm showing the definition on screen. Write it down.
>
> *"Computer vision is the field of AI that enables computers to get useful information from images and videos: what is in them, where it is, or what it says."*
>
> What does that mean? It's right there in the name: vision for a computer, meaning sight. We have eyes: we see, we understand. A computer has a camera. But taking a photo with a camera is one thing, and understanding what's in that photo is another. That understanding part is what we call computer vision, you see.
>
> Look at three phrases in the definition. "What is in them": what's in the photo, a cat or a dog. "Where it is": where it is in the photo. "What it says": what's written in it. Remember these three; they'll come back in a little while.

🖊
1. Definition card (English). ✍️ "Write it down".
2. Split the name: **COMPUTER + VISION (sight)**. Doodle: camera 📷 → "takes the photo" vs 🧠 → "understands the photo" = computer vision.
3. Underline the three phrases: **what · where · what it says**.

### F2. An image is a grid of numbers (drawing first)
⏱ **@@F2@@**

🎙
> Now the most important point in this topic. A question: how does a photo look to a computer? Does it look the way it looks to us? No. To a computer, a photo is just numbers: a table of numbers, you see.
>
> Look at the board. I'm drawing a small 6 by 6 grid: 36 little squares. Like the maths graph book we had in school, right? Now I'll write a "1" in it by filling some squares: a little flag on top, a vertical line in the middle, a base at the bottom. Each of these little squares is called a pixel: picture element.
>
> Now how does the computer store this? One number per pixel. Black is 0, full white is 255. The ones in between are grey shades. In the digits dataset we use today, the ink is white on a black background. So where there's ink it's 255, and where it's empty it's 0. Here: the left side is what we see, the right side is what the computer sees. Same image, two forms. Write down the definition:
>
> *"A digital image is a grid of tiny squares called pixels. In a grayscale image, each pixel is one number from 0 (black) to 255 (white)."*
>
> When you fill squares in a graph book, a picture appears, right? An image is just the same: tiny squares, each square one number. Real photos have lakhs or crores of those squares; that's the only difference.

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
⏱ **@@F3@@**

🎙
> What about a colour photo? Three numbers per pixel: Red, Green, Blue. That's what we call RGB. If you look at your phone screen with a magnifying glass, every pixel has three tiny lights: one red, one green, one blue. The colour depends on how brightly each light glows. Red 255, green 0, blue 0: pure red. All three 255: white. All three 0: black. Write it down: grayscale means one number per pixel, colour means three numbers per pixel. These three are called channels.
>
> Now look at the size. Our small grid: 6 × 6 = 36 numbers. In the dataset for today's build, each image is 28 × 28: that's 784 numbers. Remember the phone-photo calculation from Day 9? 12 megapixels means about 1.2 crore pixels, into 3 colours: about 3.6 crore numbers! For one photo.

🖊
1. One pixel blown up into three boxes: **R | G | B = 255 | 0 | 0 → red**. Below: **255 | 255 | 255 → white · 0 | 0 | 0 → black**.
2. Write: **Grayscale = 1 number per pixel · Colour = 3 numbers per pixel (3 channels)**. ✍️
3. Size ladder: **6 × 6 = 36 → 28 × 28 = 784 → 12 MP photo × 3 ≈ 3.6 crore numbers**.

### F4. Three vision tasks + where we see them + "not always deep learning"
⏱ **@@F4@@**

🎙
> So in computer vision there are mainly three kinds of jobs. I told you the three phrases in the definition, right? These are they.
>
> The first is image classification: one label for the whole image. "This digit is 7", "this leaf has a disease". We saw it on Day 6, right? The thing that predicts a category is classification. For images it's the same. And digits means 0 to 9: 10 categories. So it's the multi-class classification we saw on Day 6, you see.
>
> The second is object detection: it finds each object in the image and draws a box around it. In a traffic-camera photo it puts a box to show where the car is and where the number plate is.
>
> The third is segmentation: a label for every single pixel. These pixels are road, these pixels are a person, these pixels are sky. What we do today is the first one: classification.
>
> Let's look at the ones we see every day. Google Lens: point the camera at a flower and it tells you its name. In Hyderabad, traffic cameras read number plates, but the police verify before a challan is sent. There are apps for farmers: take a photo of a leaf and they tell you which pest, which disease. In hospitals, AI that looks at an X-ray and flags a chance of TB: we talked about it on Day 9, right?
>
> But don't get confused here: computer vision doesn't always mean deep learning. When you pay with UPI you scan a QR code, right? That's a camera and an image too. But reading a QR code has fixed rules, a fixed method. There's no need to train a model for it. So where do we need deep learning? When there's so much variety that you can't write rules. Handwriting: everyone's is different, right? Faces, leaves, X-rays: that's where deep learning comes in.

🖊
1. Three small boxes side by side (✍️ write the three names):
   - **Classification:** whole photo → "7" / "Cat"
   - **Detection:** photo with rectangles → "Car", "Plate"
   - **Segmentation:** photo with coloured regions → "Road / Person / Sky"
   Tick **Classification** = "today".
2. Icon strip as he speaks: 🔍 Google Lens (flower → name) · 🚦 Traffic camera (plate → police verify → challan) · 🌿 Leaf photo → pest/disease · 🩻 X-ray → "possible TB, doctor to check".
3. QR code icon with a red stamp: **"Camera ✔, deep learning ✘ (fixed rules)"**. Next to it: **"DL = when rules are impossible to write: handwriting, faces, leaves"**.

### F5. Why a plain Dense network struggles: three fingers
⏱ **@@F5@@**

🎙
> Now you should get a doubt: "Anna, an image is just numbers, right? On Day 11 we gave numbers to a Dense network and trained it. Won't it be enough to give these 784 numbers to the same network?" Good question. If you give them, it works, but there are three problems. I'll show you three fingers. Write them down.
>
> First finger: far too many weights. Dense means fully connected: every input is connected to every neuron, we saw that on Day 9. Say 784 pixels and 128 neurons. 784 × 128 weights, plus 128 biases: 1,00,480 parameters! The Day 11 network had 9 parameters; here, one layer alone has a lakh. And for a 12-megapixel colour photo, one layer alone would need about 460 crore weights. Impossible, right?
>
> Second finger: the idea of "being next to each other" is lost. To give it to a Dense layer, we first have to lay this grid out as one long line. That's called flatten. Row 1, then row 2, then row 3. Now look: in the grid, this pixel and the pixel right below it are next to each other on the same stroke. But in the line? They've ended up 28 places apart. A Dense network doesn't know in advance that "these two are neighbours". But in images, all the meaning is in the neighbours: a stroke is just neighbouring pixels going the same way together, right?
>
> Third finger: when the digit moves a little. If you write the same 7 shifted 3 pixels to the right, for us it's the same 7. But for a Dense network it's almost a new pattern: the numbers have all moved to different positions, right? Our team tested it: a Dense network that got 97% right on normal test digits fell to 49% when every digit was shifted 3 pixels. More than half wrong!
>
> So what's the answer to these three problems? That's our next topic.

🖊
Draw three fingers ✋ and write one problem per finger (✍️):
1. **Too many weights:** 784 × 128 + 128 = **1,00,480** in layer 1 (vs Day 11's 9!). 12 MP colour photo → **≈ 460 crore**.
2. **Loses "nearby-ness":** 28 × 28 square → arrow "Flatten" → one long line of dots. Circle two pixels one above the other in the grid; in the line, draw them **28 dots apart**.
3. **Shifted digit = new pattern:** a "7", and the same "7" moved 3 squares right. Caption: **"Dense: 97% → 49% when shifted 3 pixels"**.

### F6. Doubt + one-line recap
⏱ **@@F6@@**

🎙
> One more small doubt: "Anna, face unlock is also image classification, right?" Strictly speaking, no. It's verification: it checks "is this face the same as the face that was registered earlier, or not?" It uses neural networks, but the job is different. It isn't putting the image into one of the categories 0 to 9.
>
> Simple: to a computer an image is a grid of numbers. Finding patterns in those numbers and understanding what's in the image, where it is and what's written in it: that is computer vision.

🖊
- Small chip: **Face unlock = verification ("same person?"), not classification**.
- Recap card: **Computer vision = finding patterns in a grid of numbers → what / where / what it says.**

---

## [H] CONCEPT 2: CNN (Convolutional Neural Network)

### H1. Announce + definition + name unpack
⏱ **@@H1@@**

🎙
> So computer vision is done. Now today's main concept: CNN. Full form: Convolutional Neural Network. Write down the definition.
>
> *"A Convolutional Neural Network (CNN) is a neural network designed for grid-like data such as images. Instead of connecting every pixel to every neuron, it slides small learnable filters across the image to detect local patterns, and stacks layers to combine them into bigger shapes and objects."*
>
> What does that mean? The name has two parts. "Neural network": we know this. The same neurons, the same weights, the same layers. "Convolutional": this is the new word. Convolution, simply put, means sliding a small window across the image and doing a small calculation at every spot. That's all.
>
> Three keywords in the definition. "Small learnable filters": small filters, and they learn. "Local patterns": patterns in a small area: a stroke, a corner. "Stacks layers": putting one layer on top of another and combining small patterns into bigger shapes.

🖊
1. Definition card (English). ✍️
2. Split the name: **CONVOLUTIONAL = slide a small window + calculate at every spot** | **NEURAL NETWORK = same neurons, weights, layers ✔**.
3. Underline: **small learnable filters · local patterns · stacks layers**.

### H2. Filter = the teacher's 3 × 3 window (and it is our old neuron)
⏱ **@@H2@@**

🎙
> Now what is a filter? Write down the definition:
>
> *"A filter (also called a kernel) is a small grid of weights, usually 3 × 3. It looks at one small patch of the image at a time, multiplies each pixel by its weight, adds them up (plus a bias) and gives one number. Then it slides to the next position."*
>
> Let me give an example. Suppose a teacher has a small piece of cardboard with a tiny 3 by 3 window cut out in the middle. She puts that window on an answer sheet and looks for only one thing: "Is there a tick mark here?" She starts at the top-left and slides it a little at a time until she has looked at the whole page. For each position she writes a score on a separate paper: a clear tick here, 3; nothing here, 0. That score sheet is what we call a feature map. Another teacher with a different window looks for "is there a cross mark?": that's another filter.
>
> And a secret: what does this filter do? 9 pixels × 9 weights, add them all, add a bias. We've seen this somewhere, right? The Day 9 neuron! Inputs × weights + bias. A filter is just our old neuron, looking through a small window, that's all.
>
> But don't take this as the exact example. The teacher already knows what a tick mark looks like. A CNN filter knows nothing at first: it starts with random numbers and learns from data. I'll say this again in a little while; it's very important.

🖊
1. Definition card (English). ✍️
2. Doodle: an answer sheet, a cardboard with a **3 × 3 window cut out**, arrows showing it sliding left → right, row by row. A separate "score sheet" grid beside it labelled **"feature map"**.
3. Second teacher with a different window: **"another filter → another pattern"**.
4. Write: **Filter = our Day 9 neuron looking through a small window (9 inputs × 9 weights + 1 bias)**.
5. Chip: **"Teacher knows the pattern; a CNN filter LEARNS it."**

### [G] Mid-roll CTA
⏱ **@@G@@**

🎙
> Sorry for interrupting in the middle of the video. Pause this video for one second and like it. And click the three dots and hit hype: if you hype it, this video reaches many more beginners like you. Many of the people watching this series still haven't subscribed. For today's video our team ran and tested this Colab notebook in advance, so you don't get any errors. Your one like, your one subscribe gives our team that same energy. So please support us. So, let's go back to our filter.

🖊
- Like / three-dots → **Hype** / Subscribe animation. Keep the filter definition card visible underneath so the cut back is seamless.

> **Note:** his usual stat is "90% of viewers are not subscribed". Only say a number if YouTube Studio supports it on the day of recording; otherwise keep the generic line above.

### H3. The worked convolution: one window, then the whole feature map (the one worked example)
⏱ **@@H3@@**

🎙
> Don't stress about the maths: it's only multiply and add. Let's go slowly.
>
> Let's take our "1" grid. To keep it simple this time, I'm writing 255 as 1: 1 if there's ink, 0 if not. That means we divided by 255, you see. We'll do the same thing in the build.
>
> Now a filter. I'm choosing one myself: 1, 0, −1 in every row. Three rows. What does it mean? If it's "bright on the left, dark on the right", it gives a big number. So it catches the right edge of a vertical stroke. This is called a vertical edge filter.
>
> Step 1: I'm putting this red 3 by 3 square on the top-left corner of the grid. The 9 pixels inside: first row 0 0 1, second row 0 1 1, third row 0 0 1. Now multiply each pixel by the number in the same position in the filter. The left column has filter 1, pixels 0, 0, 0: all 0. The middle column has filter 0: anything times 0 is 0. The right column has filter −1, pixels 1, 1, 1: that gives −1, −1, −1. Add them all: −3. I'm writing this −3 in the first box of the feature map.
>
> Step 2: I'm moving the window one pixel to the right. Now the patch is 0 1 0, 1 1 0, 0 1 0. Left column 0, 1, 0, times 1: total 1. Middle: 0. The right column is all 0. Total: 1.
>
> Step 3: one more pixel to the right. Patch: 1 0 0, 1 0 0, 1 0 0. Left column 1, 1, 1, times 1: 3. The rest are 0. Total: 3! That's a big number. Why? Right here, our "1"'s vertical stroke is on the left side and the right side is empty. That's exactly the pattern the filter is looking for: a perfect match.
>
> If we keep sliding like this over the whole grid (a 3 by 3 window on a 6 by 6 image), there are 4 positions in a row, and 4 rows like that, so we get a 4 by 4 feature map. I'm showing the full map on screen. Look: the third column is all 3, 3, 3, 3. What the map says is "there's a vertical edge here from top to bottom". And the first column is all −3: that's the opposite edge, the left side of the stroke, dark to bright. To catch that one you need a different, flipped filter. Write down the feature-map definition:
>
> *"A feature map is the grid of numbers a filter produces as it slides over the image. Big values show where the filter's pattern was found."*
>
> Simply put, a feature map is a heat map: a map showing everywhere in the image that the filter's pattern appears, you see. When I first studied CNNs, I didn't understand what a feature map was at all. It clicked only when I drew a small grid like this on paper and calculated it by hand. If you have a calculator, check the remaining boxes yourself.

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

### H4. ReLU + max pooling
⏱ **@@H4@@**

🎙
> Next step: ReLU on this map. We saw it on Day 10, right? Negative becomes 0; positive stays the same number. So all the −3s become 0. Negative means "this pattern isn't here", so we've made it 0. Sita's h2 neuron switched OFF, remember? The same ReLU.
>
> Now pooling. Write down the definition:
>
> *"Max pooling shrinks a feature map by keeping only the largest value in each small block, usually 2 × 2. It keeps the strongest signal and makes the network a little less sensitive to small shifts."*
>
> I'm splitting this 4 by 4 map into four 2 by 2 blocks by drawing thick lines. In each block we keep only the biggest number. Top-left block: 0, 1, 0, 1, biggest 1. Top-right: 3, 0, 3, 0, so 3. Bottom-left: all 0, so 0. Bottom-right: 3, 0, 3, 1, so 3. So from 16 numbers to 4 numbers: 1, 3, 0, 3.
>
> An example: your report card has four unit tests in one subject. Suppose the principal says, "I don't need four marks; just tell me the best one." Max pooling is just like that: only the best one from each block. Look: the map has shrunk to a quarter, but the message isn't lost: "there's a strong vertical stroke on the right side". You can still see it in those 3, 3.
>
> Don't get confused here: max pooling means maximum, not average. There is a pooling that takes the average too, but what we use today is max.
>
> Why pooling? Two reasons. One: the size goes down, so the calculations go down. Two: even if the stroke moves one pixel here or there, the max in that 2 by 2 block often doesn't change, right? So small shifts don't bother it much.

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
⏱ **@@H5@@**

🎙
> Now another interesting thing. If we turn the same filter sideways (first row 1 1 1, middle 0 0 0, bottom −1 −1 −1), it's a horizontal edge filter: it catches horizontal strokes. I'm showing the result on screen. Put it on our "1" and after pooling it's almost all 0: 1, 0, 0, 0. Because a "1" has almost no horizontal strokes. Put the same filter on a "7", and the first row of the map comes out as 3, 2, 2, 1. That's the horizontal bar on top of the 7! So a "1" lights up the vertical detector, and a "7" lights up the horizontal detector at the top. Combine detectors like these and you can tell digits apart, right?
>
> Now a very, very important point. Write it down: in a real CNN, nobody designs the filters. Today on the board I chose 1, 0, −1, just like we assumed w = 0.8 on Day 7, only to show you. In a real CNN every filter starts with random numbers. During training, backprop changes them just like the other weights. The network itself learns which patterns to look for. On Day 9 we said "the network learns the features by itself", right? This is what that means.
>
> And another magic. How many numbers are in one filter? 9 weights + 1 bias = 10. Those same 10 numbers are used at every position in the image. Because whether a vertical stroke is at the top-left or the bottom-right, a vertical stroke is a vertical stroke, right? Like using one rubber stamp across the whole page: the same stamp. This is called parameter sharing. In our build, the first layer has 32 filters: 32 × 10 = 320 parameters. In a Dense layer, just 784 pixels to 32 neurons is 25,120. See the difference? First-finger problem solved.
>
> Second finger, neighbours? A filter always looks at 3 by 3 neighbouring pixels together. It doesn't turn the grid into a line. Solved. Third finger, a shifted digit? The same filter searches everywhere, so it finds the stroke wherever it is. Pooling helps a little more.

🖊
1. Slide: the horizontal filter `1 1 1 / 0 0 0 / −1 −1 −1`, and two results side by side:
   - On the **"1"** → pooled **[1 0 / 0 0]** ("almost nothing")
   - On a **"7"** (show the tiny 6 × 6 "7") → map first row **3 2 2 1** ("the top bar!") → pooled **[3 2 / 0 1]**
   Caption: **"1 lights up the vertical detector · 7 lights up the horizontal detector"**.
2. Big boxed note ✍️: **Filters are LEARNED, not hand-designed. Start random → backprop updates them.** Small: *"Board filter = for class only (like w = 0.8 on Day 7)"*.
3. Rubber-stamp doodle: one stamp pressed all over a page → **"same 10 numbers everywhere = parameter sharing"**.
4. Card: **1 filter = 9 + 1 = 10 · 32 filters = 320 · Dense 784 → 32 = 25,120**.
5. Go back to the three fingers and tick each: **✔ fewer weights · ✔ neighbours kept · ✔ (mostly) finds it anywhere**.

### H6. The full CNN stack
⏱ **@@H6@@**

🎙
> So now the whole CNN in one picture. This is the most important drawing in this video. Write it down.
>
> Image → Conv + ReLU → Pool → Conv + ReLU → Pool → Flatten → Dense → Softmax → answer.
>
> Read it like a factory line. The first Conv layer: lots of filters, catching small edges and strokes. Pool: shrinks the size. The second Conv layer works on the first layer's feature maps, so it combines edges into bigger shapes: corners, loops, things like the bar on top of a 7. Pool again. Then Flatten: laying it out as a line is no problem now, because the important features have already come out. Then Dense, our normal Day 9 network, takes the final decision: "there's a loop on top and a vertical stroke on the right, so this is a 9".
>
> Edges → shapes → which digit. On Day 9 I gave the example of a relative walking towards you from far away, right? Simple to complex. Same idea. But one difference: from far away we see the outline first; a CNN sees the small edges first. Use this example only for the idea that "simple features combine into complex features". And real filters aren't as neat as our labels: most of the time you can't name one "the loop detector".

🖊
- Big pipeline across the bottom of the board (keep it there for the build):
  **Image → [Conv + ReLU] → [Pool] → [Conv + ReLU] → [Pool] → Flatten → Dense → Softmax → "7"**
- Under the stages write: **"edges" → "shapes / parts" → "which digit?"** ✍️
- Chip: **"Analogy: simple → complex only. CNN sees small edges first. Real filters rarely have neat names."**

### H7. Softmax: percentages that add to 100
⏱ **@@H7@@**

🎙
> The last box: softmax. On Day 10 I only told you the name; now let's see it. Write down the definition:
>
> *"Softmax turns the output layer's raw scores into probabilities that are all positive and add up to 100%. The biggest score gets the biggest share."*
>
> The last layer has 10 neurons: 0 to 9, one for each digit. Each neuron gives a score, which can be any number. To keep it simple, let's take three digits: "1" has score 3, "7" has 1.5, "4" has 0.5. Softmax does two steps. One: it makes every score positive with e to the power, the same e from the Day 7 sigmoid, 2.718. Two: it divides each by the total, so they all add up to 100. Result: "1" is 76.6%, "7" is 17.1%, "4" is 6.3%. Add them: 100%. The formula is in the corner; the machine does it. If you're interested, check it on a calculator with the e^x button.
>
> And a beautiful connection. What if there are only two classes? Pass and fail. If we give Student D scores 2.4 and 0, what does softmax give? 91.7% and 8.3%. With the Day 7 sigmoid we got exactly 91.7%, right? So the sigmoid is just softmax with two classes, you see.
>
> Don't get confused here: softmax doesn't pick an answer; it gives percentages. Taking the biggest one as the answer is a separate, last step, like the 50% threshold after the sigmoid. And 99% means "the model is 99% sure", not "always correct". We'll actually see this in the build.

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
⏱ **@@H8@@**

🎙
> Now your doubt: "Anna, how does a CNN train? Is it some new method?" No! Remember the Day 10 loop? Forward pass, loss, backprop, gradient-descent update, repeat. Exactly the same. The loss is the same log loss too: −ln(the percentage given to the correct digit). If the true digit is "1" (the model gave 76.6%, right?), the loss is 0.27. Not wrong, but it can still improve. Backprop sends that error backwards and gives blame not only to the Dense weights but also to the 9 numbers inside the filters. Gradient descent changes them a little. So there's no new learning in a CNN. Weights, bias, ReLU, softmax, loss, backprop, epochs: we know all of them. Only one thing is new: how the neurons are connected.
>
> Another doubt: "Does a CNN not care where the digit is?" Not completely. Much better than Dense, but not immune. I'll show you the real numbers after the build.
>
> Simple: sliding small filters over the image to find patterns, shrinking with pooling, combining layer by layer, and finally giving percentages with softmax: that is a CNN. That simple.

🖊
1. Point to the Day 10 loop in the corner: **Forward → Loss → Backprop → Update ↺** and add an arrow from "Backprop" into the filter drawing: **"blame reaches the filters too"**.
2. Write: **True "1", model 76.6% → loss = −ln(0.766) = 0.27**.
3. Big line ✍️: **"Nothing new in HOW a CNN learns. Only HOW the neurons are connected is new."**
4. Recap card: **CNN = slide filters → feature maps → ReLU → pool → stack → Dense → softmax %.**

---

## [I] CONCEPT 3: Build an image classifier (MNIST in Colab)

### I1. Open the notebook + the dataset
⏱ **@@I1@@**

🎙
> So the theory is done. Now my favourite part: the build. Let's make an image classifier ourselves. The notebook link is in the description: open it and run it along with me. I won't go into the code line by line. I'll tell you in concept terms what each block does, and show you where the things we drew on the board are in the code.
>
> The dataset is called MNIST. Handwritten digits, 0 to 9: 70,000 small photos. 60,000 for training, 10,000 for testing. In computer vision it's like "hello world": lots of people do this as their first project. Reading handwritten marks on an answer sheet, reading the PIN code on a postal cover: this is a simple version of those, you see.
>
> In Colab, Runtime → Change runtime type. A normal CPU is enough; training may take a few minutes. If you select a T4 GPU, it's even faster.

💻
- Screen-share Colab with `part-4-build-an-image-classifier.ipynb` open at the title cell. Cursor on the "plan, block by block" list.
- Show **Runtime → Change runtime type** menu for 2 seconds.

🖊
- Lower-third: **"Notebook link in description ↓"**. Name card: **MNIST: 60,000 training + 10,000 test images · 28 × 28 · digits 0–9**.
- Put the 7-box flow on the side of the board (tick each as it runs): **Load & look → ÷255 → Build CNN → Compile + Train → Test → Predict → Mistakes**.

### I2. Block 1: Setup + Block 2: Load the dataset
⏱ **@@I2@@**

🎙
> Block 1: Setup. We load the tools: NumPy for numbers, Matplotlib for pictures, Keras for deep learning, the same Keras we used on Day 11. We fix the seed so the random starting weights come out the same every time. Run.
>
> Block 2: Load the dataset. MNIST is built into Keras. Run it: training images 60,000, 28, 28. That means 60,000 images, each 28 by 28. Test images 10,000. And the labels: the correct answer for every image, our answer key. It's the supervised learning we saw in earlier videos: features are the pixels, the label is the digit.

💻
- Run **Block 1: Setup** (prints the TensorFlow / Keras versions). *(run pause ~3 s)*
- Run **Block 2: Load the dataset**. Highlight `Training images: (60000, 28, 28)`, `Test images: (10000, 28, 28)` and `First 10 labels: [5 0 4 1 9 2 1 3 1 4]`. *(run pause ~3 s; first run downloads the data, so run it once before recording)*

🖊
- Tick box 1 "Load & look". Write **features = pixels · label = digit (answer key)**.

### I3. Block 3: An image is just a grid of numbers
⏱ **@@I3@@**

🎙
> Block 3: "An image is just a grid of numbers". We're printing the first training image as numbers. Look at the screen... pause for one second and look: the background is all 0s, and in the middle there are big numbers like 253, 255. If you follow those big numbers with your eyes... you can see a 5, right! The label is also 5. On the board we drew 6 by 6; this is the same thing, 28 by 28. Below, 18 images as pictures, with their labels.

💻
- Run the first cell of **Block 3**. Zoom into the printed 28 × 28 grid; trace the 5 with the cursor. Show `Label: 5`. *(run pause ~2 s)*
- Run the second cell: the 3 × 6 grid of digit pictures with labels.

🖊
- Point from the screen to the board's 6 × 6 "1": **"same idea, 28 × 28 = 784 numbers"**.

### I4. Block 4: Prepare the data
⏱ **@@I4@@**

🎙
> Block 4: Prepare the data. Two small jobs. One: we divide every pixel by 255, so they all come between 0 and 1. On the board we wrote 255 as 1, right? Same thing. With small, similar-sized numbers, learning is smooth. Two: we add a channel. It's grayscale, so 1 channel. For colour it would be 3: R, G, B. Look at the output: 60,000, 28, 28, 1, min 0, max 1.

💻
- Run **Block 4: Prepare the data**. Highlight `New shape: (60000, 28, 28, 1) | min: 0.0 | max: 1.0`. *(run pause ~2 s)*

🖊
- Tick box 2 "÷255". Point to the board's "÷ 255 → 0/1" grid.

### I5. Block 5: Build a small CNN
⏱ **@@I5@@**

🎙
> Block 5: Build a small CNN. This block = the CNN stack we drew on the board! Read it from top to bottom. Conv2D, 32, 3 by 3: 32 filters, each one 3 by 3. This is the filter layer we drew on the board, but here there are 32 filters, all starting random. Activation relu: ReLU on the feature map. MaxPooling2D 2 by 2: our pooling. Conv2D 64 again, MaxPooling again. Flatten. Dense 64: our normal Day 9 layer. And last, Dense 10, softmax: 10 digits, 10 percentages.
>
> We've also written the sizes in the comments: 28 to 26, 13 after pooling, then 11, pool to 5. On the board, a 3 by 3 on a 6 by 6 gave a 4 by 4, right? It went down by 2. Here too, 28 to 26. Same.
>
> Run it and look at model.summary. Remember the 9 parameters on Day 11? Here: 1,21,930. An interesting thing: about 84% of them are in that one Dense 64 layer alone, 1,02,464. The two Conv layers together have only 18,816. Because the filters are shared, right? That's why.

💻
- Show **Block 5: Build a small CNN** code cell. Move the cursor down the layers one by one while he names them; on screen, draw an arrow from each code line to the matching box of the board pipeline.
- Run it. Zoom into `model.summary()`: Output Shape column (26, 26, 32 → 13, 13, 32 → 11, 11, 64 → 5, 5, 64 → 1600 → 64 → 10) and **Total params: 121,930**. *(run pause ~2 s)*

🖊
- Tick box 3 "Build CNN". Under the board pipeline write the real sizes: **28×28 → 26×26×32 → 13×13×32 → 11×11×64 → 5×5×64 → 1,600 → 64 → 10**.
- Card: **121,930 params · Dense(64) = 102,464 (84%) · both Conv layers = 18,816**.

### I6. Block 6: Compile + Block 7: Train
⏱ **@@I6@@**

🎙
> Block 6: Compile, just like on Day 11. Optimizer adam: the smarter gradient descent whose name I told you in Video B. Loss: sparse categorical crossentropy. The name is long; don't be scared. It's the same Day 10 log loss, for 10 classes: −ln(the percentage given to the correct digit). "Sparse" only means the labels are plain numbers like 7, that's all. Metrics accuracy: we train on loss and report accuracy.
>
> Block 7: Train, model.fit. The Day 10 loop runs right here. Epochs 5: it goes through all the training images 5 times. Batch size 128: look at 128 images, then one update. Validation split 0.1: that means we keep 6,000 images aside and, after every epoch, do a mock test. So it trains on 54,000 images: 54,000 ÷ 128 is 422 batches per epoch. You'll see 422/422 on screen. I'm running it...
>
> Look: after epoch 1, accuracy is about 92.8%. Epoch 2: 97.9. By epoch 5: 99.1%. Loss came down from 0.25 to 0.03. Validation accuracy, on those 6,000 images the model doesn't learn from: about 99%. Look at the graph going up epoch by epoch. On Day 11 it took 100 epochs; here 5 are enough, because here there are 54,000 examples, 422 updates in every epoch.

💻
- Show **Block 6: Compile**, run it (instant).
- Show **Block 7: Train**. Point at `epochs=5`, `batch_size=128`, `validation_split=0.1`. Run. **Edit: speed up / time-lapse the training wait to ~10 s on screen.** *(run pause ~10 s after time-lapse)* Point at `422/422` and the epoch lines. 🔁 Reference values: epoch 1 `accuracy: 0.9280 – loss: 0.2492 – val_accuracy: 0.9808`; epoch 5 `accuracy: 0.9912 – loss: 0.0289 – val_accuracy: 0.9895`.
- Run the plot cell ("Learning progress").

🖊
- Tick box 4 "Compile + Train". Note beside the Day 10 loop: **"fit = this loop · 5 epochs × 422 batches"**.
- Card: **54,000 ÷ 128 = 421.9 → 422 batches per epoch**.

### I7. Block 8: Test on 10,000 new images
⏱ **@@I7@@**

🎙
> Block 8: Test on 10,000 new images. Now the real exam. The model has never seen these 10,000 images even once. Like doing 60,000 practice questions at a coaching centre and then getting 10,000 new questions in the final exam. Run... Test accuracy: 98.85%! That means about 9,885 correct out of 10,000. Only 115 wrong. 5 epochs, one small notebook: handwritten digits at 98.85%!
>
> Write it down: the honest score is always on test data, not on training data. The number on your screen may come out a little different, 98.6, 99.0; that's normal, it changes a little depending on the computer. If you get about 99%, your model is working correctly.

💻
- Show **Block 8: Test on 10,000 new images**, run. Zoom: 🔁 `Test accuracy: 98.85%   (test loss: 0.0352)` and `That is about 9885 correct out of 10,000.` *(run pause ~2 s)*

🖊
- Tick box 5 "Test". Big stamp: **98.85% · 9,885 / 10,000 ✔** 🔁 ✍️ **"Honest score = TEST data, not training data"**.

### I8. Block 9: Predict one image
⏱ **@@I8@@**

🎙
> Block 9: Predict one image. Now let's give it just one image. Test image number 0: this is a handwritten 7. Remember the 7 the teacher wrote at the start? Run... 10 percentages came out. 7: 99.999%! All the others are almost 0. In the bar chart there's only one tall bar, at 7. These are softmax percentages: add them all and you get 100. Model says 7, true answer 7. Change idx and try other images: 1, 2, 3, anything up to 9999.

💻
- Show **Block 9: Predict one image**, run with `idx = 0`. Zoom into the list: 🔁 `7:  99.999%`, all others `0.000%`, and `Model says: 7 | True answer: 7`. Show the image + bar chart. *(run pause ~2 s)*

🖊
- Tick box 6 "Predict". Sketch the bar chart: one tall bar at **7 (99.999%)**, flat everywhere else. Note: **"softmax: all 10 add to 100%"**.

### I9. Block 10: The images it got wrong
⏱ **@@I9@@**

🎙
> Block 10: The images it got wrong. My favourite block of all. Of the 115 the model got wrong, let's look at the first 10. Run... Look. Image 18: true answer 3, the model said 5, 44% sure. Be honest: when you look at that 3, it looks like a 5 to you too, right? Image 717: a 0, but a loop that leans to one side; the model said 5, 56%. Even a teacher would squint at handwriting like this.
>
> The list below has the top 2 guesses: in 9 of these 10, the correct answer was the model's second choice! In image 18 it gave 39% to 3. So the model had a doubt; it was close to the correct answer.
>
> But look at this one: image 449. True 3, the model said 5, 99% sure! I told you at softmax, right? 99% sure doesn't mean correct. Confidence is one thing, correctness is another. Remember this.

💻
- Show **Block 10: The images it got wrong**, run the first cell: 🔁 `Wrong: 115 out of 10000 test images` and the 2 × 5 picture grid. Circle **image 18** ("True 3 | Said 5 (44% sure)") and **image 717** ("True 0 | Said 5"). *(run pause ~3 s)*
- Run the second cell (top-2 list). Highlight 🔁 `Image   18: true 3 | model: 5 44%, 3 39%` and `Image  449: true 3 | model: 5 99%, 3 1%`.

🖊
- Tick box 7 "Mistakes". Pin up three mini-cards: **#18: True 3 · Said 5 · 44% (2nd guess 3: 39%)** · **#717: True 0 · Said 5 · 56%** · **#449: True 3 · Said 5 · 99% 😮**.
- Write ✍️: **"99% sure ≠ correct. Confidence ≠ correctness."** and **"9 of 10: right answer = 2nd guess"** 🔁.

### I10. Block 11 (optional): Try it yourself + Block 12: Homework, Fashion-MNIST
⏱ **@@I10@@**

🎙
> Block 11, optional: Try it yourself. In (a) we put the same 1, 0, −1 filter we drew on the board onto a real 7. In the vertical map the 7's slanted stroke lights up; in the horizontal map the bar on top of the 7 lights up: exactly what we saw on the board. In (b), 8 of the 32 feature maps from the first layer of the real trained CNN. These are filters the model learned by itself; nobody designed them. Some catch edges, some catch other patterns. On Day 9 we said "first lines and edges", right? Here it is, in front of your eyes.
>
> Block 12: Homework, Fashion-MNIST. In Block 2, change one line: fashion_mnist instead of mnist. Runtime → Run all. Same code, same CNN, but now not digits: 10 kinds of clothes and shoes: T-shirt, trouser, sneaker, bag. Will the accuracy be higher or lower than for digits? Which items does it confuse most? Tell me your accuracy in the comments.

💻
- Run **Block 11 (optional): Try it yourself** (a): show "Original / Vertical filter + ReLU / Horizontal filter + ReLU" for test image #0. Cursor on the top bar in the horizontal map and the slanted stroke in the vertical map. *(run pause ~2 s)*
- Run (b): the 8 learned feature maps ("filter 0 … filter 7"). Point at 2–3 that look like edge maps (say only what is visible on your screen). *(run pause ~2 s)*
- Scroll to **Block 12: Homework, Fashion-MNIST**. Show the one-line change `dataset = keras.datasets.fashion_mnist` in Block 2 (do **not** run it on camera).

🖊
- Homework card: **Block 2 → `keras.datasets.fashion_mnist` → Runtime → Run all → comment your test accuracy + the items it confuses**.

### I11. Why CNNs for images: the comparison card + one doubt
⏱ **@@I11@@**

🎙
> One last card. With the same 5 epochs, our team also trained a normal Dense network: Flatten, Dense 128, Dense 10. On the test: 97.0%. Our CNN: 98.85%. Does it feel like a small difference? Dense makes about 299 mistakes, the CNN 115: about 2.6 times fewer mistakes. And when every digit is shifted 3 pixels: Dense 49%, CNN 88%. The CNN dropped too; it's not immune, I told you earlier, right? But it's much better. The fix is to also give shifted and rotated copies during training. That's called data augmentation: name only. That's why we use CNNs for images. Write it down.
>
> One doubt: "Anna, if I take a photo of my own handwriting and give it, will it read it?" Given directly, it'll struggle. In MNIST the digits are centred, 28 by 28, white ink on a black background. You'd have to crop your photo the same way, resize it and flip the colours. Otherwise the accuracy can drop a lot. 99% means "99% on MNIST-style digits".

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
⏱ **@@J@@**

🎙
> Now today's quiz: tell me in the comments. One: a colour photo is 100 by 100 pixels. How many numbers does the computer see? Two: the vertical filter, 1, 0, −1 in every row, on this patch: 1, 0, 0 in every row. What number comes out? Three: max-pool this 2 by 2 block: 2, 7, 0, 5. Four, a trick question: which of these is not deep-learning image classification? (a) Google Lens telling a flower's name, (b) scanning a UPI QR code, (c) an app that looks at a leaf photo and tells the disease. Let's see who gets all four right. And don't forget your Fashion-MNIST accuracy too.

🖊
- Quiz card:
  1. Colour photo, 100 × 100 pixels → how many numbers?
  2. Filter `1 0 −1` (3 rows) on patch rows `1 0 0` (3 rows) → ?
  3. Max-pool this 2 × 2 block: **2, 7, 0, 5** → ?
  4. NOT deep-learning image classification? (a) Google Lens naming a flower (b) scanning a UPI QR code (c) a leaf-disease app
  *(Answers go in production notes. Don't show them on screen.)*

---

## [K] Video recap
⏱ **@@K@@**

🎙
> And that's it for the day! In this video we covered computer vision: an image is a grid of numbers, one number for grayscale, three for colour. CNN: filters, feature maps, ReLU, max pooling, softmax, and the machine learns the filters itself. And we built an image classifier ourselves on MNIST: about 99% test accuracy. All of these come in AI, in machine learning, in deep learning, in the branch called computer vision, you see.

🖊
- Taxonomy line: **AI → ML → Deep Learning → Computer Vision → CNN → MNIST classifier (≈ 99%)**.
- Keep the CNN stack drawing on screen.

---

## [L] Outro
⏱ **@@L@@**

🎙
> Even if convolution isn't completely clear after one watch, don't stress. Take a paper, draw a 6 by 6 grid and calculate one window yourself: it'll click.
>
> All the notes (definitions, board drawings, numbers) are going in the description. And the Colab notebook link is in the description too. Run it, do the homework.
>
> Today AI learned to see images. In the next video: how does AI read text? How does ChatGPT understand our sentence? NLP, RNN, LSTM and Transformers: the T in ChatGPT is Transformer. How AI reads text. Whoever wants that video, like this video.
>
> And it's not late yet: just 12 videos are done. Sit for one day and you can cover them all. Add your friends to this AI Learning Series too. The more support you give, the better the videos we'll bring you.
>
> Thank you so much for watching, signing off, Tech Boy Deepak.

🖊
- The CNN stack stays on screen.
- Lower-third: **"Notes + Colab notebook in description ↓"**.
- End card: **Next: How AI Reads Text (NLP · RNN · LSTM · Transformer)** + the previous-video tile (Day 11).
