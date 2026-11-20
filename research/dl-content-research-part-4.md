# Deep Learning Part 4: Content Research Brief (Days 31, 32, 35)

_For Tech Boy Deepak's Telugu "AI Learning Series". Prepared 20 Nov 2026._

- **Channel episode:** **Day 12**, "Computer Vision, CNNs and Building an Image Classifier".
- **Covers plan days:** Day 31 (What is computer vision?), Day 32 (What is a CNN?), Day 35 (Build an image classifier).
- **Deliberately left out:** Days 33–34 (NLP; RNN vs LSTM vs Transformer) go to Part 5.
- **Comes after:** Video A (Day 9, plan Days 21–24), Video B (Day 10, plan Days 25–28) and Part 3 (Day 11, plan Days 29–30: epochs, batches, learning rate, first Keras model with `summary / compile / fit / evaluate / predict`).
- **Companion notebook:** [`../notebooks/part-4-build-an-image-classifier.ipynb`](../notebooks/part-4-build-an-image-classifier.ipynb). It was tested end-to-end; the real results are in §Day 35.

**Audience level:** a college student with no maths background. Drawings first, numbers second, formulas last. Same format as [`dl-content-research.md`](dl-content-research.md): for each day, core idea → key points and depth boundary → toy numbers → analogies → whiteboard → misconceptions → quiz.

**Research note:** web *search* worked in this session. Direct page fetches to cs231n.github.io and keras.io were blocked by the session's network settings, as they were for the earlier brief. So facts from those pages were checked against search-result extracts and standard textbook content. Items marked **[verify]** should be re-checked against the linked page before filming. **Every number in this brief was computed with Python** (log at the end), and every Day 35 result comes from an actual run of the notebook.

---

## 0. Episode-level guidance for the scriptwriter

**The one-sentence story of the episode:**
*"Ee video lo manam computer ki chadavadam nerpistham"* (transliterated; render in Telugu script in the script): we teach a computer to read handwritten digits, the same skill it needs to read the marks written on an answer-sheet cover or the PIN code on a postal cover.

**The running example.** We keep it in the student universe:
- In Video A (Day 9) Deepak already drew "answer-sheet photo → network → Pass" and said the network learns its own features ("first lines and edges, then letters, then words"). **Day 12 opens that black box.**
- New object for this episode: **the handwritten marks box on an answer sheet**. Ravi scored **7** in Q1, and a teacher wrote "7" by hand. Can a machine read that "7"? Sita's sheet has a "1". Kiran writes his 7s with a cross-stroke, the European way, which the machine may find confusing. That gives a natural hook for the "mistakes" block.
- The hand examples in Day 31–32 use a tiny **"1"** and a tiny **"7"** (6 × 6). The notebook uses real 28 × 28 MNIST digits. The first test image in MNIST happens to be a **7**, so the on-screen prediction shows a "7" as well. It's a nice coincidence to use.

**Depth budget (from the style DNA, §3.6 and §4).** His rule is at most one worked formula per video. This episode naturally has three small calculations: a convolution window, max pooling and softmax. Recommended handling:
- **Convolution** = *the* worked example. It uses only "multiply 9 pairs and add", so a Class 10 student can check it on a phone calculator. Do one window fully on the board, then reveal the full 4 × 4 map.
- **Pooling** needs no maths ("pick the biggest of 4"). Do it in 30 seconds.
- **Softmax:** show the result as percentages that add to 100%. Keep the eˣ formula to a small corner card ("the machine does this; check with the eˣ button if you like"). Do not derive it.

**Code policy (style DNA §3.6).** The notebook is shown as a Colab artefact. The build segment explains it in **7 conceptual blocks** (listed in §Day 35.3). It is not a syntax lesson. Show the cell, say what the block *does* in one or two sentences, run it, point at the output.

**Suggested time split (about 22–24 min):** intro/recap 2 min · Day 31 ~5 min · Day 32 ~8–9 min (mid-roll inside it) · Day 35 build ~6–7 min · quiz/recap/outro ~2 min.

**Callback lines to Part 3 (one line each, no re-teaching):** "Remember `compile`, `fit`, epochs and batch size from the last video? Same here." Part 3 is being researched in parallel, so **[verify]** the exact numbers and wording Part 3 uses for epochs and batch size before reusing them.

---

## Day 31: What is computer vision?

### 1. Core idea
Computer vision is the part of AI that lets computers get useful information out of images and videos: what is in a picture, where it is, or what it says. To a computer, an image is not a picture at all. It is a **grid of numbers**, one number per pixel for grayscale (0 = black … 255 = white), or **three numbers per pixel** for colour (Red, Green, Blue). Deep learning, mainly CNNs, learns which patterns in those numbers mean "7", "face" or "diseased leaf".

### 2. Key points (and depth boundary)
1. **Image = grid of pixels = grid of numbers.** Grayscale: 1 number per pixel, 0–255. Colour: 3 numbers per pixel (R, G, B), each 0–255. Examples: pure red = (255, 0, 0), white = (255, 255, 255), black = (0, 0, 0).
2. **MNIST size:** 28 × 28 = **784** numbers per image. A 12-MP phone photo (4000 × 3000) = 12,000,000 pixels × 3 = **36,000,000** numbers. This is the same number used in Video A, so reuse it.
3. **Why a plain Dense network struggles with images.** There are three reasons. Say them as three fingers:
   - **(a) Too many weights.** Every pixel connects to every neuron. For 28 × 28 images, Flatten → Dense(128) already needs 784 × 128 + 128 = **100,480** parameters in the first layer alone. For a 12-MP colour photo, the same layer needs 36,000,000 × 128 ≈ **4.6 billion** weights.
   - **(b) It throws away "nearby-ness".** Flatten turns the grid into one long line of 784 numbers. Pixel 1 and pixel 29 sit right on top of each other in the picture, but they are 28 places apart in the line. A Dense layer has no built-in idea that neighbouring pixels belong together.
   - **(c) A shifted digit looks like a totally different input.** Real numbers from MNIST test image #0 (a "7"): shifting it **3 pixels to the right** changes **150 of the 784** numbers. Of its 105 "ink" pixels, only **44** are still ink at the same position. For a Dense network, it is mostly a new pattern. Measured in our run: a Dense network that scores **97.01%** on normal test digits falls to **49.46%** when every test digit is shifted 3 pixels. Our CNN goes from **98.85%** to **87.75%**. That's more tolerant, not immune; see Day 32 misconceptions.
4. **Three main vision tasks (one line each):**
   - **Image classification:** one label for the whole image ("this is a 7", "this leaf has blight").
   - **Object detection:** finds *each* object and draws a **box** around it with a label (the number plate, cars, people).
   - **Segmentation:** labels **every pixel** ("these pixels are road, these are the tumour"). Today's build is classification only.
5. **Computer vision ≠ always deep learning.** QR/UPI code scanning, OMR bubble sheets and barcodes are read by fixed, hand-written algorithms, not learned classifiers. See the real-world table.

**Do NOT go into:** colour spaces beyond RGB (HSV, YUV), image file formats or compression, resolution/DPI, classical image processing (blur, thresholds) beyond a name, how detection or segmentation models work inside (YOLO and U-Net may be name-dropped at most), or video and optical flow.

### 3. Toy numeric example: a handwritten "1" as numbers (6 × 6)
Grayscale, MNIST-style (white ink on a black background, 0 = black, 255 = white):

```
  0    0  255    0    0    0
  0  255  255    0    0    0
  0    0  255    0    0    0
  0    0  255    0    0    0
  0    0  255    0    0    0
  0  255  255  255    0    0
```

The same image after "÷ 255". This is the version used for the Day 32 hand calculation; 1 = ink, 0 = blank:

```
0 0 1 0 0 0
0 1 1 0 0 0
0 0 1 0 0 0
0 0 1 0 0 0
0 0 1 0 0 0
0 1 1 1 0 0
```

A tiny "7" for the second example:

```
1 1 1 1 1 0
0 0 0 0 1 0
0 0 0 1 0 0
0 0 0 1 0 0
0 0 1 0 0 0
0 0 1 0 0 0
```

**Real MNIST image:** the notebook prints training image #0 (a handwritten **5**) as a full 28 × 28 grid. Ink pixels go up to 253–255 and the background is all 0s. It's a great "pause and look" moment: you can literally see the 5 in the numbers.

**Parameter count (Python-checked):**

| Network first layer | Parameters |
|---|---|
| Dense: 784 pixels → 128 neurons | 784 × 128 + 128 = **100,480** |
| Dense: 784 pixels → 32 neurons | 784 × 32 + 32 = **25,120** |
| Dense: 12-MP colour photo (36 M numbers) → 128 neurons | ≈ **4,608,000,000** weights |
| One 3 × 3 grayscale filter (Day 32 preview) | 9 + 1 = **10** |
| 32 such filters (our first Conv2D layer) | **320** |

### 4. Indian analogies
| Analogy | Mapping | Accuracy / risk |
|---|---|---|
| **Rangoli / muggu on graph dots**, or **cross-stitch / pixel art**: a picture made of small squares, each square one colour | Image = grid of pixels; each square = one number (or 3 for colour) | **Most accurate** for "image = grid". Risk: almost none. Say that real photos have millions of squares. |
| **Teacher entering marks in an Excel sheet**: rows × columns of numbers | The computer only sees a table of numbers, not a picture | Accurate for "the computer sees numbers". Risk: an Excel table's neighbouring cells don't "belong together" the way neighbouring pixels do, so don't stretch it to Day 32. |
| **Colour mixing on a TV/phone screen**: each pixel is a tiny red, green and blue light; turn up R for red, R + G for yellow | Colour = 3 channels | Accurate (that is literally how screens work). Risk: paint mixing (red + yellow = orange) follows different rules; stick to screen lights. |
| **Reading a jumbled answer sheet**: cut a page into 784 strips and shuffle them in a line. Could you still read it? | Why Flatten + Dense loses the "nearby" structure | Good for point 3(b). Risk: a Dense layer keeps the same fixed order every time, so it isn't random. The real issue is that it has no built-in notion of *which* positions are neighbours. |

### 5. Whiteboard diagram
1. Draw a 6 × 6 grid. Shade the "1" (column 3 plus the flag and base). Next to it, write the same grid as 0 / 255 numbers. Caption: **"What we see vs what the computer sees"**.
2. Below, draw one pixel blown up into 3 boxes, R | G | B, holding "255 | 0 | 0 = red". Caption: **"Colour = 3 numbers per pixel"**.
3. Write the size ladder: **6 × 6 = 36 → 28 × 28 = 784 → 12 MP photo ≈ 3.6 crore numbers**.
4. Draw a 28 × 28 square → arrow "Flatten" → one long line of 784 dots → every dot wired to 128 neurons. Write **"1,00,480 weights in layer 1!"** Cross out the neighbours link: circle two pixels that sit on top of each other in the grid and show they end up 28 dots apart in the line.
5. Draw the "7" and the same "7" moved 3 squares right. Caption: **"For a Dense network, this is a new pattern: 97% → 49%"**.
6. Draw three small boxes:
   - **Classification:** whole photo → "Cat".
   - **Detection:** photo with rectangles → "Car, Plate".
   - **Segmentation:** photo with coloured regions → "Road / Person".

### 6. Misconceptions to pre-empt
- **"The computer sees the picture like we do."** It only receives numbers. "Seeing" means finding patterns in those numbers.
- **"Computer vision = deep learning."** Many vision jobs (QR/UPI codes, barcodes, OMR bubbles) use fixed algorithms. Deep learning is used where the patterns are too varied to hand-code, such as handwriting, faces, leaves and X-rays.
- **"Colour images are 3 separate photos."** It is one image with 3 numbers per pixel (3 "channels"). Thinking of it as three stacked layers is fine.
- **"Bigger photo = better AI."** More pixels means more computation. Models usually shrink images first (MNIST is just 28 × 28).
- **"Face unlock / Aadhaar face auth is 'classification'."** Strictly, it is **verification**: *"is this the same person as the enrolled face?"* It is not sorting into fixed classes like 0–9. Neural networks are used, but the task differs from today's build.

### 7. Quiz / comment question
"A colour photo is 100 × 100 pixels. How many numbers does the computer see?" (Answer: 100 × 100 × 3 = **30,000**.)
Alternative: "Which of these is NOT deep-learning image classification? (a) Google Lens naming a flower (b) a phone scanning a UPI QR code (c) an app spotting leaf disease." (Answer: **(b)**. QR decoding is a fixed algorithm.)

---

## Day 32: What is a CNN?

### 1. Core idea
A **Convolutional Neural Network (CNN)** is a neural network built for grid-like data such as images. Instead of wiring every pixel to every neuron, it slides small **filters** (e.g. 3 × 3 = 9 weights) across the image. Each filter is a little pattern detector, and wherever its pattern appears it produces a high number. The result is a **feature map**. **Pooling** then shrinks each map by keeping the strongest values. Stacking these layers lets early layers find edges, later layers find shapes and parts, and a final Dense + **softmax** layer turns everything into class percentages. The filter values are **learned** by the same backprop and gradient descent as in Day 10.

### 2. Key points (and depth boundary)
1. **Filter (kernel)** = a small grid of weights, typically 3 × 3. It looks at one 3 × 3 patch at a time, multiplies the 9 pairs, adds them up (plus a bias) and writes one number. Then it slides one pixel and repeats. This is exactly the Day 22 neuron (inputs × weights + bias), only looking at a small window.
2. **Feature map** = the grid of all those outputs: a "heat map" of *where* the filter's pattern was found. A 6 × 6 image with a 3 × 3 filter gives a **4 × 4** map. MNIST's 28 × 28 gives 26 × 26.
3. **ReLU on the feature map.** Same ReLU as Day 10: negatives → 0. "Pattern not here" becomes 0.
4. **Max pooling (2 × 2)** = in each 2 × 2 block keep only the biggest number. The map shrinks to half the height and half the width, so 16 numbers become 4 (3 of every 4 dropped). The strongest evidence is kept, and the result becomes a little less sensitive to the exact position of a stroke.
5. **Stacking = features of features.** Layer 1: edges and strokes. Deeper layers: combinations, such as corners, loops and the "top bar of a 7". Final Dense layer: "loop on top + vertical line on the right → 9". This edges → parts → objects hierarchy is the standard description in CS231n and in Zeiler & Fergus's visualisations. Real learned features are messier than our neat labels.
6. **Parameter sharing.** The *same* 9 weights + 1 bias are reused at every position, because a vertical edge is a vertical edge whether it's top-left or bottom-right. So one filter = **10 parameters**, however big the image is. Our first Conv2D layer with 32 filters has **320** parameters. A Dense layer from 784 pixels to just 32 neurons would need **25,120**.
7. **Filters are learned, not hand-designed.** In class we *hand-pick* a vertical-edge filter so we can compute it. In a real CNN all filters start as random numbers, and backprop adjusts them like any other weight. The notebook's Block 11(b) shows feature maps from filters the model learned by itself.
8. **Softmax at the end.** The last layer has 10 neurons (digits 0–9). Their raw scores can be any numbers. **Softmax turns the scores into percentages that are all positive and add to 100%.** The biggest score gets the biggest share. It is the multi-class big brother of the sigmoid: with 2 classes, softmax gives exactly the sigmoid answer (see the Student D check below).
9. **Colour images:** a filter on a colour image is 3 × 3 × **3** (one 3 × 3 slice per R, G, B) = 27 weights + 1 bias = **28**. Mention it in one line only.

**Do NOT go into:**
- **Stride and padding** beyond one line: "the filter moves 1 pixel at a time; some models add a border of zeros so the map doesn't shrink".
- The output-size formula (N − F + 2P)/S + 1.
- Backprop through convolution or pooling. Say only "same backprop as Day 10".
- The convolution vs cross-correlation technicality. Footnote only, below.
- 1 × 1 convolutions, depth-wise convolutions, batch norm, dropout.
- The architecture zoo beyond a name-drop: **LeNet** (1998, read cheques), **AlexNet** (2012, the ImageNet moment from Day 9), **ResNet**. Vision Transformers can be a one-line tease for Part 5.

*Accuracy footnote (do not say on camera):* deep-learning "convolution" layers technically compute cross-correlation (the filter is not flipped). This doesn't matter for learning, because the filter values are learned anyway. Keras, PyTorch and CS231n all call it convolution.

### 3. Toy numeric examples (Python-checked)

**(a) The worked convolution: vertical-edge filter over the 6 × 6 "1".**

Filter (a classic vertical-edge detector; **we** chose it for class):
```
 1  0  -1
 1  0  -1
 1  0  -1
```
Meaning: "bright on the left, dark on the right → big positive number".

**Window 1 (top-left 3 × 3 patch), computed on the board:**
```
patch        filter       multiply
0 0 1        1 0 -1       0  0 -1
0 1 1    ×   1 0 -1   =   0  0 -1
0 0 1        1 0 -1       0  0 -1      sum = -3
```
**Slide 1 right:** patch rows (0 1 0), (1 1 0), (0 1 0) → 0 + 1 + 0 = **1**.
**Slide 1 more:** patch rows (1 0 0), (1 0 0), (1 0 0) → 1 + 1 + 1 = **3** ← the stroke's right edge fits the filter perfectly.

**Full feature map (4 × 4):**
```
-3  1  3  0
-3  1  3  0
-3  0  3  0
-3  0  3  1
```
Story: the column of **3s** says "a vertical edge runs all the way down here". The column of **−3s** is the *opposite* edge (dark-to-bright). A different, flipped filter would catch that one.

**After ReLU (negatives → 0):**
```
0  1  3  0
0  1  3  0
0  0  3  0
0  0  3  1
```

**2 × 2 max pooling** (split into four 2 × 2 blocks and keep the biggest in each):
```
block top-left  [0 1 / 0 1] → 1      block top-right  [3 0 / 3 0] → 3
block bot-left  [0 0 / 0 0] → 0      block bot-right  [3 0 / 3 1] → 3

pooled:  1  3
         0  3
```
16 numbers → 4 numbers, and the "strong vertical line on the right side" message survives.

**(b) Optional contrast (one slide, no hand calculation): the same filter turned sideways (horizontal-edge detector).**
```
 1  1  1
 0  0  0
-1 -1 -1
```
- On the **"1"**: map rows = (0 0 0 0), (1 1 0 0), (0 0 0 0), (−1 −2 −1 −1). After ReLU and pooling: **[[1, 0], [0, 0]]**. Almost nothing, because a "1" has hardly any horizontal edges.
- On the **"7"**: first row of the map = **3 2 2 1** (the top bar!). After ReLU and pooling: **[[3, 2], [0, 1]]**.
- The vertical filter on the "7" pools to **[[0, 2], [0, 2]]** (the slanted stroke on the right).

Talking point: *"A '1' lights up the vertical detector; a '7' lights up the horizontal detector at the top. Combine the detectors and you can tell digits apart. A CNN learns dozens of such detectors by itself."*

**(c) Softmax: 3-class example (digits "1", "7", "4").**

| Class | Raw score | eˣ | ÷ total (26.216) | Percentage |
|---|---|---|---|---|
| "1" | 3.0 | 20.086 | 0.7662 | **76.6%** |
| "7" | 1.5 | 4.482 | 0.1710 | **17.1%** |
| "4" | 0.5 | 1.649 | 0.0629 | **6.3%** |
| **Total** | | 26.216 | 1.0000 | **100%** |

Two steps in words: (1) make every score positive with eˣ (the e = 2.718 from Day 9's sigmoid); (2) divide each by the total so they add to 100%.
- Loss link to Video B: if the true digit is "1", loss = −ln(0.766) = **0.27**. If it was really a "7", loss = −ln(0.171) = **1.77**. Same log loss, now for many classes.
- **Sigmoid bridge with Student D:** softmax of the two scores [2.4, 0] = **91.7% / 8.3%**, which is exactly σ(2.4) = 0.917 from Day 7/Day 9. *"Sigmoid is softmax with two classes."*

**(d) Parameter sharing, in numbers:**

| Layer | Parameters |
|---|---|
| One 3 × 3 filter (grayscale) | 9 + 1 = **10** |
| Conv2D(32 filters, 3 × 3) on MNIST | 32 × 10 = **320** |
| Conv2D(64, 3 × 3) on 32 feature maps | 64 × (3 × 3 × 32 + 1) = **18,496** |
| Dense 784 → 32 (for comparison) | **25,120** |
| Dense 784 → 128 | **100,480** |

Fun fact from our real model (§Day 35): **84%** of its 121,930 parameters sit in the single Dense(64) layer after Flatten (102,464). The two conv layers together have only 18,816.

### 4. Indian analogies
| Analogy | Mapping | Accuracy / risk |
|---|---|---|
| **Teacher checking an answer sheet with a small cut-out window (a 3 × 3 "stencil")**: she slides it across the page, looking for one thing only, e.g. "is there a tick mark here?", and writes a score for each position on a separate sheet | Filter = the window with one pattern in mind; sliding = convolution; her score sheet = feature map; several teachers each with a different pattern = several filters | **Most accurate** for filter + feature map. Risk: a teacher *knows* what a tick looks like; a CNN filter starts random and *learns* its pattern. Say this aloud. |
| **Pooling = summarising each section of a report card by its best mark**: four unit-test marks → keep only the highest per quarter | Max pooling keeps the strongest signal per block and shrinks the data | Accurate for *max* pooling. Risk: viewers may think it is the *average*. Say "maximum, not average" (average pooling exists but isn't used here). |
| **Recognising a friend from far away at the bus stand**: first you see an outline (tall, thin), then closer the face shape, then details like specs and a moustache → "That's Ravi!" | Layers: edges → shapes/parts → object | Good intuition for the hierarchy (also used in Day 9 for "layers"). **Can mislead** on *order*: in a CNN all layers run on the same image in one pass, from detail to big picture. Our eye sees the outline *first* from far away; a CNN sees tiny edges first. Use it only for "simple features combine into complex ones". |
| **Police sketch / identity parade**: witnesses describe parts (eyes, nose, scar) and the parts are combined into a face | Feature combination | OK as a one-liner; weaker than the friend analogy. |
| **A stamp or rubber seal pressed all over a page**: the same stamp is used everywhere | Parameter sharing: one filter reused at every position | Accurate for sharing. Risk: a stamp *prints*; a filter *detects*. Use only for "same 9 numbers everywhere". |

### 5. Whiteboard diagram
1. Left: the 6 × 6 "1" grid with 0/1 values. Draw a **red 3 × 3 square** over the top-left corner.
2. Middle: the 3 × 3 filter `1 0 −1` × 3 rows, labelled **"Filter = pattern detector (vertical edge)"**.
3. Show the 9 multiplications for window 1 → **−3**. Write −3 in the top-left cell of an empty 4 × 4 grid on the right (**"Feature map"**).
4. Move the red square right twice: write **1**, then **3**. Then fill in the rest of the map (reveal on a slide).
5. Below the map, redraw it with negatives crossed out → 0: **"ReLU"**.
6. Draw thick lines splitting the ReLU map into four 2 × 2 blocks, circle the max in each → a 2 × 2 grid **[1 3 / 0 3]**: **"Max pooling: keep the strongest"**.
7. Big pipeline across the bottom of the board:
   **Image → [Conv + ReLU] → [Pool] → [Conv + ReLU] → [Pool] → Flatten → Dense → Softmax → "7: 99%"**
   Under the stages, write: **"edges" → "shapes/parts" → "which digit?"**
8. Side card: **softmax table** (3.0 / 1.5 / 0.5 → 76.6% / 17.1% / 6.3%, total 100%). Under it: **"2 classes → same as sigmoid: Student D 91.7%"**.
9. Side card: **"1 filter = 10 numbers, reused everywhere · Dense 784 → 32 = 25,120"**.

### 6. Misconceptions to pre-empt
- **"Programmers design the filters."** Only in classic image processing and in our classroom example. In a CNN all filters are learned from data via backprop.
- **"The CNN sees the 7 like we do."** It finds number patterns that happen to correlate with "7". It can be fooled by things that look nothing like a 7 to us, and it fails on things it never saw (shifted or rotated digits).
- **"CNNs don't care where the object is (fully shift-invariant)."** Only partly. Shared filters find a pattern anywhere, and pooling adds a little tolerance. In our real test the CNN dropped from 98.85% to **87.75%** on digits shifted 3 pixels, and to **66.04%** at 4 pixels. That's far better than Dense (49.46% at 3 pixels), but not immune. The usual fix is *data augmentation* (training on shifted and rotated copies): name only.
- **"Pooling averages."** Max pooling takes the **maximum**.
- **"Each filter has a clear human meaning (an 'eye detector')."** Early filters often look like edges. Deeper ones are mixtures that rarely have neat names. Same caveat as Day 9's "studied-enough neuron".
- **"Softmax picks one answer."** Softmax gives *percentages*. Picking the biggest (argmax) is a separate, final step, like the 50% threshold after sigmoid in Day 7.
- **"CNN is a completely new kind of learning."** It isn't. It uses the same neurons, ReLU, loss, backprop and gradient descent. Only the wiring is different (see the continuity bridge).
- **"Softmax percentages = how often the model is right."** They are the model's confidence, and a model can be 99% sure and still wrong. Our run has a real case: test image #449, a **3** that the model called **5 with 99% confidence**.

### 7. Quiz / comment question
"Apply the vertical filter `1 0 −1` (3 rows) to this 3 × 3 patch: rows (1 0 0), (1 0 0), (1 0 0). What number comes out?" (Answer: 1 + 1 + 1 = **3**, strong vertical edge.)
Alternative: "Max-pool this 2 × 2 block: 2, 7, 0, 5." (Answer: **7**.)

---

## Day 35: Build an image classifier (MNIST in Colab)

### 1. Core idea
We train a small CNN in Google Colab to read handwritten digits. We use **MNIST**: **60,000** training images and **10,000** test images of digits 0–9, each 28 × 28 grayscale. The pipeline is the same as any supervised project from Day 4: load data → prepare → build model → compile → train → test on unseen data → predict. Only the model has changed: Conv2D and MaxPooling2D layers instead of plain Dense.

### 2. Key points (and depth boundary)
1. **Why MNIST:** it is the "hello world" of computer vision. It's small enough to train in under a minute on a CPU, and it maps directly to reading handwritten marks on an answer sheet or a PIN code on a postal cover.
   - **Origin:** built by LeCun, Cortes and Burges from NIST data. The digits come from US Census Bureau employees and US high-school students; the training set alone came from about 250 writers, and the test set from different writers **[verify the writer counts on the MNIST page]**.
   - **History:** a CNN of the same family (LeNet) read millions of bank cheques per month in the US in the late 1990s (LeCun et al. 1998).
2. **Same supervised-learning recipe** as Days 3–4: features = pixels, label = digit, train/test split.
3. **Loss for 10 classes:** `sparse_categorical_crossentropy` = Video B's log loss, −ln(the percentage given to the correct digit), averaged over the images. "Sparse" only means the labels are plain integers (7), not 10-slot lists.
4. **Train on loss, report accuracy** (Video B). The test accuracy on the 10,000 unseen images is the honest score.
5. **Mistakes are normal and educational.** Most of the model's errors are digits that humans also find ambiguous. Showing them builds trust and pays off "no model is 100%".

**Do NOT go into:** dropout, batch normalisation, data augmentation (one line as "the fix for shifted digits"), callbacks or early stopping, saving/loading models, GPU internals, transfer learning (name-drop as a "next step" at most), the confusion-matrix maths (open since Day 6; if anything, show the "top confusions" list), or line-by-line Python syntax.

### 3. The notebook, block by block (for the build segment)
File: [`notebooks/part-4-build-an-image-classifier.ipynb`](../notebooks/part-4-build-an-image-classifier.ipynb). It has 29 cells (15 code), with markdown block titles in simple English and outputs cleared. **Explain it on screen in these 7 conceptual blocks.** Notebook block numbers are in brackets.

| # | On-screen block | What to say (one or two sentences) | What the viewer sees |
|---|---|---|---|
| 1 | **Load & look** [1–3] | "MNIST comes built into Keras: 60,000 practice images, 10,000 exam images. And look, an image is just numbers." | `(60000, 28, 28)`; the full 28 × 28 grid of training image #0 (a **5**) as numbers; an 18-image grid with labels |
| 2 | **Prepare** [4] | "Divide by 255 so every pixel is between 0 and 1, and add one 'channel' because it's grayscale." | `New shape: (60000, 28, 28, 1) | min: 0.0 | max: 1.0` |
| 3 | **Build the CNN** [5] | Read the stack like a factory line: Conv → Pool → Conv → Pool → Flatten → Dense → Dense(10, softmax). "Filters start random; they will be learned." | `model.summary()`: **121,930 parameters** (table below) |
| 4 | **Compile + train** [6–7] | One-line callback to Part 3: "Same compile and fit as last video. Adam optimizer, log loss for 10 classes, 5 epochs, batch size 128." | Epoch lines: accuracy rises 92.8% → 99.1%; training time; accuracy-per-epoch plot |
| 5 | **Test (evaluate)** [8] | "The real exam: 10,000 images the model has never seen." | `Test accuracy: 98.85%` → "about 9,885 correct out of 10,000" |
| 6 | **Predict one image** [9] | "Give it one handwritten 7. It answers with 10 percentages; softmax made them add to 100." | Test image #0 (a **7**) → `7: 99.999%`, all others ≈ 0%; a bar chart |
| 7 | **The mistakes** [10] | "115 wrong out of 10,000. Look at them: would *you* be sure?" | 10 misclassified digits with true/predicted/confidence, plus the top-2 guesses |
| (opt.) | **Try it yourself** [11–12] | (a) The hand-made vertical/horizontal filter from the board, applied to a real MNIST 7. (b) Feature maps from 8 of the 32 *learned* first-layer filters. Homework: swap one line to Fashion-MNIST. | Edge maps; learned feature maps; Fashion-MNIST homework instructions |

**The CNN (as built in the notebook):**
```
Input 28×28×1
Conv2D(32, 3×3, relu)  → 26×26×32     params     320
MaxPooling2D(2×2)      → 13×13×32     params       0
Conv2D(64, 3×3, relu)  → 11×11×64     params  18,496
MaxPooling2D(2×2)      →  5×5×64      params       0
Flatten                → 1,600        params       0
Dense(64, relu)        → 64           params 102,464
Dense(10, softmax)     → 10           params     650
Total                                        121,930
```
`compile(optimizer="adam", loss="sparse_categorical_crossentropy", metrics=["accuracy"])`
`fit(epochs=5, batch_size=128, validation_split=0.1)` → 54,000 images for training, 6,000 for validation → **422 batches per epoch** (54,000 ÷ 128 = 421.9, rounded up).

This is the Keras team's "Simple MNIST convnet" layout (Conv32 → Pool → Conv64 → Pool → Flatten → Dense(10)). It reaches about 99% in 15 epochs and has 34,826 parameters. We made two changes: we added one Dense(64) hidden layer, so the familiar Dense layer from Day 9/10 appears, and we dropped Dropout to keep the depth boundary. We train for 5 epochs.

### 4. REAL results from our test run
**Environment:**
- TensorFlow **2.21.0**, Keras **3.15.1**, CPU only (4 cores), no GPU.
- `keras.utils.set_random_seed(42)`.
- Run twice and got **identical** results both times on this machine.

| Measure | Result |
|---|---|
| Parameters (`model.summary()`) | **121,930** (476 KB) |
| Training time, 5 epochs on CPU | **39 s** (first run), **45 s** (second run); about 7–9 s per epoch after the first |
| Epoch 1 | train acc 92.80%, loss 0.2492 · val acc 98.08%, val loss 0.0637 |
| Epoch 2 | train 97.88% / 0.0676 · val 98.60% / 0.0498 |
| Epoch 3 | train 98.48% / 0.0480 · val 98.83% / 0.0405 |
| Epoch 4 | train 98.84% / 0.0369 · val 98.80% / 0.0368 |
| Epoch 5 | train 99.12% / 0.0289 · val 98.95% / 0.0365 |
| **Test accuracy (10,000 unseen images)** | **98.85%** (test loss 0.0352) → **115 wrong** |
| Predict test image #0 (a 7) | **7: 99.9994%**; next biggest: 9 = 0.0003%, 3 = 0.0002%; loss ≈ 0.000006 |
| Errors by true digit | 0: 6 · 1: 3 · 2: 15 · 3: 16 · 4: 1 · 5: 4 · 6: 18 · 7: 13 · 8: 11 · **9: 28** (most) |
| Most common confusions (true → predicted) | 3 → 5 (10), 9 → 5 (7), 2 → 7 (7), 6 → 4 (5), 6 → 5 (5), 7 → 2 (5) |
| Comparison: Dense-only net (Flatten → Dense(128) → Dense(10)), same 5 epochs | 101,770 params, 7 s, **97.01%** test (≈ 299 wrong, 2.6× more mistakes than the CNN) |
| Shift test, every test digit moved right by 2 / 3 / 4 px | CNN 96.62% / **87.75%** / 66.04% · Dense 77.16% / **49.46%** / 31.58% |
| Homework run: Fashion-MNIST, same code, one line changed | **89.46%** test (1,054 wrong), 43 s. Typical confusions: shirt ↔ T-shirt/coat/pullover, sneaker ↔ sandal/ankle boot |

**The first 10 mistakes** (the notebook shows these; top-2 guesses):

| Test image | True | Model's 1st guess | 2nd guess |
|---|---|---|---|
| 18 | 3 | 5 (44%) | **3 (39%)** |
| 62 | 9 | 5 (62%) | **9 (37%)** |
| 321 | 2 | 7 (71%) | **2 (28%)** |
| 445 | 6 | 0 (69%) | **6 (30%)** |
| 449 | 3 | 5 (**99%**) | **3 (1%)** |
| 625 | 6 | 4 (94%) | **6 (6%)** |
| 646 | 2 | 4 (57%) | **2 (37%)** |
| 684 | 7 | 3 (78%) | **7 (20%)** |
| 717 | 0 | 5 (56%) | **0 (44%)** |
| 726 | 7 | 4 (57%) | 5 (25%) |

Talking point: in **9 of these 10** the right answer was the model's **second** choice (for #449 only at 1%), and several are shaky handwriting that a teacher would also squint at (image 18's "3" looks like a 5; image 717's "0" is a lopsided loop). One mistake (#449) was **99% confident**. That shows confidence is not correctness.

**Notes for the script:**
- **"Your numbers will vary a bit"** (it's also printed in the notebook). Different hardware, Colab's TF version and GPU vs CPU give slightly different floating-point results. Expect roughly **98.5–99.2%** test accuracy **[verify on Colab]**. Say "around 99%", not "exactly 98.85%".
- **Colab timing:** the free Colab CPU runtime has fewer cores (typically 2) than our 4-core test machine, so expect roughly 1–2 minutes for 5 epochs. A T4 GPU runtime is faster **[verify both on Colab before filming]**. Colab's documented default image (2026.01) lists TensorFlow 2.19 **[verify the live version with the notebook's first cell]**. The notebook uses only long-stable Keras 3 APIs (`keras.Sequential`, `keras.Input`, `Conv2D`, `MaxPooling2D`, `set_random_seed`).
- **Why validation accuracy beats training accuracy in epoch 1** (98.08% vs 92.80%): if a sharp viewer asks, Keras's "accuracy" during an epoch is the running average while the weights are still improving, and validation is measured at the end of the epoch. It's not a bug. This is a one-line answer for the comments; don't put it in the script.

### 5. Indian analogies
| Analogy | Mapping | Accuracy / risk |
|---|---|---|
| **Coaching-centre practice tests vs the final exam**: you practise on 60,000 old questions (training) and keep 10,000 fresh ones for the real exam (test). Memorising answers won't help on new questions | Train/test split; test accuracy is the honest score | **Most accurate**. It's the same as Day 3/4's training vs testing, so no risk. |
| **Teacher correcting 10,000 answer sheets and getting 115 wrong because of bad handwriting** | 98.85% accuracy, and mistakes on ambiguous digits are normal | Accurate and relatable. Risk: a teacher can ask the student; the model can't. Fine to leave unsaid. |
| **Postman reading PIN codes on covers / bank clerk reading cheque amounts** | The real-world job MNIST imitates | Good motivation. Risk: real postal/cheque systems do more than single-digit classification (locating the PIN box, splitting the digits) and fall back to humans when unsure. Say "a simple version of". |

### 6. Whiteboard / screen diagram
1. A horizontal flow of 7 boxes matching the build blocks: **Load & look → ÷255 → Build CNN → Compile + Fit → Evaluate → Predict → Mistakes**. Tick each box as the Colab cell runs.
2. Under "Build CNN", redraw the Day 32 pipeline with real sizes: **28×28 → 26×26×32 → 13×13×32 → 11×11×64 → 5×5×64 → 1,600 → 64 → 10**.
3. Under "Evaluate", a big stamp: **98.85% · 9,885 / 10,000 ✔**.
4. Under "Predict", the bar chart with one tall bar at "7".
5. Under "Mistakes", pin up 3 of the 10 mistake images (18, 449, 717) with "True / Said / %".
6. Optional final card: **Dense 97.0% vs CNN 98.9%**, and on shifted digits **49% vs 88%**. "This is why we use CNNs for images."

### 7. Misconceptions to pre-empt
- **"99% accuracy means it reads any handwriting."** It reads *centred, 28 × 28, MNIST-style* digits. A phone photo of your own handwriting first needs cropping, resizing, centring and inverting (MNIST is white-on-black). Without that, the accuracy can drop a lot.
- **"Training accuracy is the score."** The honest score is **test** accuracy on unseen images (Day 3).
- **"More epochs is always better."** Here validation accuracy was already flattening by epoch 4–5 (98.80% → 98.95%). Too many epochs can overfit; Part 3 covers this **[verify Part 3 wording]**.
- **"We wrote rules for each digit."** No line of code describes what a 7 looks like. The model learned it from 54,000 labelled examples.
- **"It needs a GPU."** This model trains in under a minute on an ordinary CPU.

### 8. Quiz / comment question
"Our model got 98.85% on 10,000 test images. How many did it get wrong?" (Answer: **115**.)
Homework comment prompt: "Change one line to Fashion-MNIST and comment your test accuracy! (Ours: 89.46%.) Which two items does it confuse most?"

---

## Real-world computer-vision examples for Indian viewers (2026), with claim checks

| Example | What the vision system does | Fact / hook (source) | Status |
|---|---|---|---|
| **Phone face unlock (Face ID and Android face unlock)** | Neural networks turn the face (on iPhone: a depth map + infrared image) into a numeric representation and compare it with the enrolled face | Apple: facial matching runs in the Secure Enclave "using neural networks trained specifically for that purpose", plus networks for attention and anti-spoofing ([Apple support 102381](https://support.apple.com/102381), [Apple Platform Security guide](https://support.apple.com/guide/security/sec067eb0c9e)) | ✔ for iPhone. Android implementations vary by maker **[verify per phone]**. Task = verification, not classification |
| **Aadhaar face authentication** | Matches a live face photo against the Aadhaar record | 200 crore face-auth transactions by 10 Aug 2025, doubling in about 6 months ([Business Standard](https://www.business-standard.com/india-news/uidai-aadhaar-face-authentication-crosses-2-billion-transactions-125081101734_1.html)). MeitY statement: "based on AI/Machine Learning technology" ([PIB, PRID 2117407](https://www.pib.gov.in/PressReleasePage.aspx?PRID=2117407) **[verify this is the exact release]**) | ✔ volume. The exact model type isn't published, so say "AI/neural networks", not "a CNN" specifically **[verify]** |
| **UPI / QR code scanning** | Finds the 3 corner "finder" squares, straightens the image and decodes the bits with Reed–Solomon error correction | Standard QR decoding is a fixed algorithm, not a learned classifier. DL for QR decoding exists only as research ([arXiv 2506.20305](https://arxiv.org/pdf/2506.20305)) | ✔ **NOT DL classification.** Use it as the "trick" quiz option |
| **Number-plate reading (ANPR) at tolls** | Camera detects the plate (detection) and reads the characters (recognition) | NHAI's first barrier-free Multi-Lane Free Flow toll at Chorayasi, NH-48, Gujarat (announced 2 May 2026) combines **FASTag (RFID) with ANPR cameras**. Vehicles without a FASTag are identified by plate and sent an e-notice ([Autocar India](https://www.autocarindia.com/car-news-amp/india-gets-its-first-barrier-free-tolling-system-in-gujarat-439614), [NBM&CW](https://www.nbmcw.com/news/roads-highways/nhai-launches-barrier-free-multi-lane-free-flow-tolling-on-nh-48-gujarat.html)) | ✔ ANPR is used. **Careful:** FASTag itself is RFID, not vision. Whether a given ANPR vendor uses deep learning is **[verify]**; modern ANPR typically does |
| **Number-plate reading by traffic cameras (Hyderabad)** | ANPR cameras flag violations; humans verify before a challan | RTI: about 2,000 challans a day from ANPR cameras in Hyderabad in 2024 (of about 15,438 daily fines) ([NewsMeter](https://newsmeter.in/hyderabad/rti-hyderabad-averaged-15438-traffic-fines-daily-in-2024-anpr-cameras-behind-2000-a-day-750096)). IIIT Hyderabad's AI "VIOLA" dashcam system: about 96% of AI-flagged violations approved after police verification ([Autocar Pro](https://www.autocarpro.in/news/iiit-hyderabad-develops-ai-based-traffic-violation-detection-system-133700)) | ✔. A good local hook; also shows "human in the loop" |
| **Crop-disease / pest apps** | The farmer photographs a leaf or insect; an image model identifies the pest and gives advice | Govt's **National Pest Surveillance System** (launched Aug 2024) uses Plantix's image recognition, covering about 73–74 crops and 436–445 pests depending on the source ([Drishti IAS](https://www.drishtiias.com/daily-updates/daily-news-analysis/national-pest-surveillance-system-npss/print_manually), [KNN India](https://knnindia.co.in/news/newsdetails/sectors/agri-food/government-launches-ai-powered-national-pest-surveillance-system-to-empower-farmers)). Analytics India Magazine notes its impact on farmer actions is unproven ([AIM](https://analyticsindiamag.com/ai-features/indias-pest-surveillance-ai-has-reached-national-scale-but-its-impact-is-unproven/)) | ✔ exists. Crop/pest counts vary, so say "dozens of crops, hundreds of pests" |
| **Medical X-ray screening (TB)** | A deep network reads chest X-rays and flags likely TB for confirmatory testing | Qure.ai qXR in Delhi slums (Jul 2025–Mar 2026): 1,68,568 X-rayed, 18,377 flagged, 877 confirmed ([ThePrint](https://theprint.in/india/ai-assisted-x-rays-flag-18377-people-for-tb-testing-in-delhi-slums-877-confirmed-study/3064481/)). Same as the earlier brief | ✔. Frame it as "flags for a doctor's test", not "diagnoses" |
| **Google Lens** | Recognises objects and text in camera images; translates signboards (incl. Telugu) | Live demo possible: point it at a Telugu board or a flower | Widely known; Google describes Lens as using AI/computer vision **[verify current Telugu support live]** |
| **Reading PIN codes / postal automation** | OCR reads addresses/PIN codes; unreadable ones go to a human | India Post's Automated Mail Processing Centre (Delhi) used OCR + a video-coding fallback (2012-era release, [reproduced here](https://aipeugujarat.blogspot.com/2012/08/ministry-of-communications-information.html)). Research from ISI Kolkata: deep-CNN PIN-code detection for Indian postal automation ([ISI digital commons](https://digitalcommons.isical.ac.in/conf-articles/71)) | Partly ✔. Current India Post deployment and whether it uses DL for handwritten PINs: **[verify]**. Say "machines like this", not "India Post uses CNNs" |
| **OMR sheets (EAMCET/NEET bubble sheets)** | Checks whether each bubble is dark enough | Classic OMR is threshold-based mark detection, not handwriting recognition | **[verify]**. Useful as a "not DL" contrast next to QR |
| **Bank cheques (history)** | LeNet-style CNN reads handwritten amounts | LeCun et al. 1998: deployed in NCR's cheque-recognition systems, "reading millions of checks per month" in US banks ([paper PDF](https://gwern.net/doc/ai/nn/cnn/1998-lecun.pdf)). The often-quoted "10–20% of all US cheques" is **not** in the paper **[verify; avoid quoting]** | ✔ ("millions per month") |

---

## Continuity bridge: nothing new in *how* it learns, only in *how the layers connect*

| CNN piece | Already taught (where) | Bridge line for the script |
|---|---|---|
| A filter computing one number from a 3 × 3 patch | The neuron: inputs × weights + bias (Day 9, Student D) | "A filter is our old neuron, looking through a small window. 9 inputs, 9 weights, 1 bias." |
| Filter values | Weights and biases, "assumed for the demo, normally learned" (Day 9) | "Today I chose the filter, just like I assumed w = 0.8 in Day 7. In the real CNN the machine learns it." |
| ReLU after convolution | ReLU = max(0, z) (Day 10; Sita's h2 = 0) | "Negative means 'pattern not here' → 0. Same ReLU as Sita's switched-off neuron." |
| Softmax output | Sigmoid for pass/fail (Days 7, 9, 10); softmax was name-dropped in Day 10 | "Sigmoid gave one percentage for pass/fail. Softmax gives 10 percentages that add to 100. With two classes it *is* the sigmoid: Student D, 91.7%." |
| Loss for 10 classes | Log loss = −ln(probability of the correct answer) (Day 10) | "Same log loss, now checking the percentage given to the correct digit." |
| Learning the filters | Gradient descent + backprop; the forward → loss → backward → update loop (Day 10) | "The blame flows back into the filters too. Same backprop, same downhill steps." |
| Epochs, batch size, compile/fit/evaluate | Part 3 (Day 11) | "Same `compile` and `fit` as last time; only the layers inside changed." |
| Dense layers at the end | Fully connected layers (Day 9) | "After the filters do their job, the normal network from Day 9 makes the final decision." |
| Train/test split, accuracy | Days 3–4, Day 6 | "Practice on 60,000, exam on 10,000 new ones." |
| Features learned from raw data | Day 9: "in DL the network learns the features itself" | "Remember 'first lines and edges, then letters'? Today you saw it: the first layer's filters *are* the edge finders." |

**One-liner to say aloud:** *"CNN lo kotha learning em ledu. Weights, bias, ReLU, softmax, loss, backprop, epochs: anni manaki telisinave. Kotha di okkate: neurons ela connect avthayi."* (transliterated) There's nothing new in how a CNN learns; only the way the neurons are connected is new.

---

## Sources

Core concepts (see the research note; cs231n.github.io and keras.io could not be fetched in full from this session):
- Stanford CS231n, Convolutional Neural Networks (filters, local connectivity, parameter sharing, 2 × 2 max pooling with stride 2, edges in early layers). https://cs231n.github.io/convolutional-networks/ **[verify exact wording; checked via search extracts and CS231n-derived lecture notes, e.g. https://userpages.cs.umbc.edu/tinoosh/cmpe650/slides/convolutional-networks/CS231n%20Convolutional%20Neural%20Networks%20for%20Visual%20Recognition.html]**
- Keras example "Simple MNIST convnet" (Conv32 → Pool → Conv64 → Pool → Flatten → Dropout → Dense(10, softmax); "~99% test accuracy"). https://keras.io/examples/vision/mnist_convnet/ (source: https://github.com/keras-team/keras-io/blob/master/examples/vision/mnist_convnet.py; mirror checked: https://cocalc.com/github/keras-team/keras-io/blob/master/examples/vision/mnist_convnet.py)
- Keras datasets API (MNIST, Fashion-MNIST loaders). https://keras.io/api/datasets/ **[verify]**
- Google ML Crash Course, Neural networks: multi-class classification (softmax probabilities add up to 1.0; one class per example). https://developers.google.com/machine-learning/crash-course/neural-networks/multi-class
- Google ML Crash Course, activation functions (from the earlier brief). https://developers.google.com/machine-learning/crash-course/neural-networks/activation-functions
- MNIST dataset card (60,000/10,000, 28 × 28, size-normalised and centred; built from NIST by Burges, Cortes, LeCun). https://huggingface.co/datasets/ylecun/mnist
- LeCun, Bottou, Bengio, Haffner (1998), "Gradient-Based Learning Applied to Document Recognition" (LeNet-5; cheque reading in NCR systems). https://gwern.net/doc/ai/nn/cnn/1998-lecun.pdf
- Xiao, Rasul, Vollgraf (2017), Fashion-MNIST (same format as MNIST, 10 clothing classes). https://arxiv.org/abs/1708.07747 ; https://research.zalando.com/publication/fmnist_2017/
- Zeiler & Fergus (2014), "Visualizing and Understanding Convolutional Networks" (edges → textures → parts hierarchy). https://arxiv.org/abs/1311.2901 **[verify; cited from standard knowledge, not fetched]**
- Classification vs detection vs segmentation (definitions). https://docs.clarifai.com/tutorials/image-classification-detection-segmentation
- Google Colab runtime versions FAQ (2026.01 image lists TF 2.19.0). https://research.google.com/colaboratory/runtime-version-faq.html ; Keras getting started (Keras 3 + TF pairing). https://keras.io/getting_started/

India / 2026 examples: see the URLs inline in the real-world table.

---

## Appendix: arithmetic and run log (Python 3, NumPy; TensorFlow 2.21.0 / Keras 3.15.1, CPU)

```
6x6 "1" (0/1)  *  vertical filter [[1,0,-1]]x3  ->
  [[-3 1 3 0] [-3 1 3 0] [-3 0 3 0] [-3 0 3 1]]
  ReLU -> [[0 1 3 0] [0 1 3 0] [0 0 3 0] [0 0 3 1]]   2x2 maxpool -> [[1 3] [0 3]]
"1" * horizontal filter -> [[0 0 0 0] [1 1 0 0] [0 0 0 0] [-1 -2 -1 -1]]  ReLU+pool -> [[1 0] [0 0]]
"7" * vertical   -> ReLU+pool [[0 2] [0 2]]
"7" * horizontal -> [[3 2 2 1] [0 -1 0 0] [-1 0 0 1] [-1 0 0 1]]  ReLU+pool -> [[3 2] [0 1]]
softmax [3.0,1.5,0.5]: exp 20.086, 4.482, 1.649; sum 26.216 -> 0.7662 0.1710 0.0629
softmax [2.4,0] -> 0.9168 0.0832  == sigmoid(2.4) 0.9168
-ln(0.7662)=0.266   -ln(0.1710)=1.766
params: Dense 784->128 = 100,480 | 784->32 = 25,120 | 12MP RGB x128 = 4,608,000,000
        conv 3x3 gray = 10 | 32 filters = 320 | conv 3x3x32 -> 64 = 18,496 | colour 3x3x3 filter = 28
CNN summary: 320 + 0 + 18,496 + 0 + 0 + 102,464 + 650 = 121,930 (Dense(64) = 84.0%)
fit: 54,000 train / 6,000 val, 422 steps/epoch, 5 epochs, batch 128, seed 42
  ep1 acc .9280 loss .2492 val_acc .9808 val_loss .0637
  ep2 acc .9788 loss .0676 val_acc .9860 val_loss .0498
  ep3 acc .9848 loss .0480 val_acc .9883 val_loss .0405
  ep4 acc .9884 loss .0369 val_acc .9880 val_loss .0368
  ep5 acc .9912 loss .0289 val_acc .9895 val_loss .0365
  training time 39 s (run 1), 45 s (run 2); identical metrics in both runs
test: acc 0.9885, loss 0.0352, wrong 115
idx0 (true 7): P(7)=99.9994%, P(9)=0.0003%, P(3)=0.0002%, P(2)=0.0001%
first wrong idx: 18 62 321 445 449 625 646 684 717 726
top confusions (true,pred): (3,5)x10 (9,5)x7 (2,7)x7 (6,4)x5 (6,5)x5 (7,2)x5
errors per true class: 0:6 1:3 2:15 3:16 4:1 5:4 6:18 7:13 8:11 9:28
shift idx0 by 3 px: 150/784 pixel values change; ink 105 px, only 44 still ink in place; CNN still says 7 (100.0%)
shifted test set accuracy (2/3/4 px): CNN 96.62/87.75/66.04 | Dense(128) 77.16/49.46/31.58
Dense baseline: 101,770 params, 7 s, test 97.01%
Fashion-MNIST (same notebook, one line changed): test 89.46%, wrong 1054, 43 s
```
