# Production Notes: Video D, "How AI Sees Images" (AI Learning Series Day 12)

**Files in this folder**
- `script-telugu.md`: the recording script. Telugu voice, English terms in Latin script, with board cues (🖊) and Colab cues (💻).
- `script-english.md`: the same script rendered in English, for reviewing content and accuracy.
- `production-notes.md`: this file.
- Notebook demonstrated in the build: [`../../notebooks/part-4-build-an-image-classifier.ipynb`](../../notebooks/part-4-build-an-image-classifier.ipynb). Content brief: [`../../research/dl-content-research-part-4.md`](../../research/dl-content-research-part-4.md).

**Covers plan Days 31, 32 and 35:** what is computer vision (image = grid of numbers, RGB, classification/detection/segmentation, real examples) · what is a CNN (filters, feature maps, ReLU, max pooling, the CNN stack, softmax, parameter sharing, filters are learned) · build an image classifier (MNIST in Colab: dataset, training, testing, prediction, mistakes, homework). Plan Days 33–34 (NLP; RNN vs LSTM vs Transformer) are Part 5.

**Runtime estimate:** 4,394 English-equivalent spoken words ÷ 175 wpm = 25:07, plus ~36 s of on-screen Colab run pauses (training time-lapsed to ~10 s) ≈ **25:43**. Allow **~27 min** once drawing pauses are included. The Telugu script is about 3,840 spoken words (≈ 150 per minute, his measured density).
**Segment budget:** intro 3:12 · Concept 1 (computer vision) 4:54 · Concept 2 (CNN) 9:31 incl. mid-roll · Concept 3 (build) **6:27** · quiz/recap/outro 1:39.
**Mid-roll CTA:** 09:59, about **39%** of runtime, inside his 35–46% band. It cuts in between the filter definition and the worked convolution.
**Notes prompts ("రాసుకోండి"):** 16 spoken, at every definition card, the "notes రాసుకోండి" in E, the three-fingers list, the colour rule, "filters are learned", the CNN stack, "nothing new in how a CNN learns" (H8), the 422-batch calculation, "honest score = test data" and the Dense-vs-CNN card. Longest gap ≈ 3.5 min (H8 → I6).
**Numbering:** assumes Parts 1–3 go out as **Days 9, 10, 11**. If not, change the day number in segment A, the title card, the "జస్ట్ 12 videos" line (segment L), the titles below and the description. The notebook's first cell also says "Day 12".

---

## 1. Title options (his format: emoji, topic, ✅, series tag)

1. **😱 How AI Sees Images? ✅ | Computer Vision, CNN & Build an Image Classifier | AI Learning Series Day-12**
2. **CNN in 25 Minutes ...... ✅ | AI Learning Series Day 12 | Ft. Tech Boy Deepak**
3. **😱 AI కి చదవడం నేర్పించాం – 99% ✅ | CNN Explained in Telugu | Ai learning | Ft. Tech Boy Deepak | Detailed Explanation**

(Patterns from his real titles: "Day 6: 😱 Classification vs Regression ✅ | Ai learning | Ft. Tech Boy Deepak | Detailed Explanation" and "Day 8: ML Algorithms in 24 Minutes ...... ✅". If the final cut runs longer, update the minute count in option 2.)

## 2. Thumbnail ideas

| # | Big text | Small text / visual |
|---|---|---|
| 1 | **AI కళ్ళు ఎట్లా చూస్తాయి? 👀** | Left: a handwritten red "7". Right: the same 7 as a grid of 0/255 numbers. "Day 12" badge |
| 2 | **99.999% → "7" ✅** | Colab bar chart with one tall bar at 7; Deepak pointing at it |
| 3 | **Photo = Numbers 🤯** | 6 × 6 pixel grid of a "1" with a red 3 × 3 filter window on it |
| 4 | **99% sure… but WRONG 😮** | MNIST test image #449 (a 3) labelled "AI said: 5". Curiosity angle for the mistakes block |

## 3. YouTube description (paste-ready)

```
AI Learning Series – Day 12 | How AI Sees Images 👀
Computer vision, CNNs (filters, feature maps, pooling, softmax) and we BUILD an image classifier in Google Colab that reads handwritten digits with ~99% accuracy. Drawings first, no scary maths!

Last video we trained our first neural network on numbers. Today: how does AI see a photo?

💻 Colab notebook (run it yourself!): <NOTEBOOK LINK>

⏱ Chapters
00:00 Intro
00:47 Recap: Days 9–11 + last quiz answers
02:20 Today's agenda
03:12 What is computer vision?
03:51 An image is a grid of numbers
04:58 Colour = 3 numbers (RGB)
05:29 Classification, detection, segmentation
06:33 Why a normal Dense network struggles
08:06 What is a CNN?
08:49 What is a filter?
10:23 Worked example: filter → feature map
12:35 ReLU + max pooling
13:38 Filters are learned + parameter sharing
15:08 The full CNN, step by step
15:58 Softmax: percentages that add to 100
16:57 How a CNN learns (same loop as Day 10)
17:37 Build: MNIST in Colab
19:24 Building the CNN in Keras
20:05 Training: epochs and batches
21:10 Test accuracy on 10,000 new images
21:35 Predicting a handwritten 7
21:54 The mistakes it made
22:39 Try it yourself + homework
23:21 Dense vs CNN: why CNNs for images
24:04 Quiz + what's next

📝 NOTES (write these down!)
1. Computer vision: the field of AI that gets useful information from images and videos: what is in them, where it is, or what it says.
   • A digital image = a grid of pixels. Grayscale: 1 number per pixel (0 = black, 255 = white). Colour: 3 numbers per pixel (Red, Green, Blue = 3 channels).
   • 6×6 = 36 numbers · 28×28 = 784 · a 12 MP colour photo ≈ 3.6 crore numbers.
   • Tasks: classification (one label per image) · detection (a box around each object) · segmentation (a label for every pixel).
   • Not all computer vision is deep learning: QR/UPI codes are read with fixed rules.
2. Why a plain Dense network struggles with images: (a) too many weights (784 → 128 = 1,00,480 parameters in one layer), (b) flattening loses which pixels are neighbours, (c) a shifted digit looks like a new pattern (Dense: 97% → 49% with a 3-pixel shift; try it in Block 13 of the notebook).
3. CNN (Convolutional Neural Network): slides small learnable filters across the image to find local patterns, then stacks layers to build bigger shapes.
   • Filter (kernel): a small grid of weights (e.g. 3×3). Multiply 9 pixels by 9 weights, add (+ bias) → one number. Then slide. (= our Day 9 neuron looking through a small window)
   • Feature map: the grid of outputs; big values = where the pattern was found. 6×6 image + 3×3 filter → 4×4 map.
   • ReLU on the map: negatives → 0.
   • Max pooling (2×2): keep the biggest number in each 2×2 block → 4× fewer numbers, strongest signal kept. MAX, not average.
   • Filters are LEARNED (start random, updated by backprop + gradient descent), not hand-designed.
   • Parameter sharing: 1 filter = 9 + 1 = 10 numbers reused everywhere. 32 filters = 320 parameters (Dense 784 → 32 = 25,120).
   • The stack: Image → Conv+ReLU → Pool → Conv+ReLU → Pool → Flatten → Dense → Softmax ("edges → shapes → which digit").
   • Softmax: turns scores into percentages that are positive and add to 100% (3, 1.5, 0.5 → 76.6%, 17.1%, 6.3%). With 2 classes it equals the sigmoid (Student D: 91.7%).
   • Training is the SAME loop as Day 10: forward → loss (log loss) → backprop → gradient-descent update → repeat.
4. Our MNIST build (60,000 training + 10,000 test images, 28×28):
   • CNN with 121,930 parameters · 5 epochs · batch size 128 → 422 batches per epoch
   • Test accuracy ≈ 98.85% (115 wrong out of 10,000). Your number may vary slightly (~98.5–99%).
   • Test image #0 → "7: 99.999%"
   • 99% sure ≠ always correct (image #449: a 3 called "5" with 99% confidence)
   • Dense-only network: 97.0% → CNN: 98.85% · shifted 3 px: Dense 49%, CNN 88% (notebook Block 13, optional)

📌 Quiz (answer in comments!)
1) A colour photo is 100 × 100 pixels. How many numbers does the computer see?
2) Filter rows (1 0 −1) ×3 on a patch with rows (1 0 0) ×3 → what number?
3) Max-pool the 2×2 block 2, 7, 0, 5 → ?
4) Which is NOT deep-learning image classification? (a) Google Lens naming a flower (b) scanning a UPI QR code (c) a leaf-disease app

🏠 Homework: in Block 2 change ONE line to keras.datasets.fashion_mnist → Runtime → Run all. Comment your test accuracy and which items it confuses!

▶ Previous: Day 11 – Train Your First Neural Network (Keras)
▶ Next: Day 13 – How AI Reads Text (NLP · RNN · LSTM · Transformer)

#AILearningSeries #DeepLearning #ComputerVision #CNN #TechBoyDeepak #AIinTelugu #MNIST #GoogleColab
```

> The chapter times are word-count estimates. **Re-time them from the final edit before publishing**: YouTube needs the first chapter at 00:00 and each chapter to be at least 10 s long. Replace `<NOTEBOOK LINK>` with the Colab/GitHub link. If the 🔁 live numbers differ on recording day, update notes section 4 to match the video.

## 4. Board drawings to prepare (in order of use)

Prepare clean versions of items 3, 7, 8, 10 and 12 in advance (grids are slow to draw neatly). Draw the others live with the pen, which is his style.

| # | Segment | Drawing | Notes |
|---|---|---|---|
| 1 | B | **Recap board**: neuron doodle; 9-knob network; Day 10 loop in a corner; Day 11 sticky note (epoch · batch · learning rate · overfitting · validation = mock test · 320 students · batch 32 · 10 batches · 100 epochs = 1,000 updates · 90% · Sita 38% → 95%) + quick card with the Day 11 quiz answers (30 · overfitting → stop near epoch 6 · 13) | Reuse Day 10's loop drawing if possible. Keep the loop corner until H8 |
| 2 | B | **Day 9 answer-sheet board** (photo → network → Pass, "edges → letters → words") with a box "black box → TODAY we open it 🔓" | Flash Video A's board for continuity |
| 3 | F2 | **6 × 6 grid of a "1"** (shaded) + the same grid as 0/255 numbers | Keep on the board until H5 |
| 4 | F3 | **RGB pixel** (255 \| 0 \| 0 = red, etc.) + **size ladder** 36 → 784 → 3.6 crore | |
| 5 | F4 | **Three task boxes**: classification / detection (rectangles) / segmentation (coloured regions); QR icon "Camera ✔, DL ✘" | |
| 6 | F5 | **Three fingers**: 1,00,480 weights · flatten line with two neighbours 28 dots apart · a "7" and the shifted "7" (97% → 49%) | Ticked again in H5 |
| 7 | H2 | **Teacher's cardboard window** sliding over an answer sheet + "score sheet = feature map" | |
| 8 | H3 | **The worked convolution**: 0/1 "1" grid, filter `1 0 −1` ×3, red 3 × 3 square, the 9 products → −3, empty 4 × 4 map; then 1, 3; then the full map slide | **The one worked example.** Draw the grid and filter before any number |
| 9 | H4 | **ReLU map** (−3s crossed out) → thick lines into 2 × 2 blocks → circled maxes → **[1 3 / 0 3]**; report-card doodle | "MAX, not average" chip |
| 10 | H5 | **Horizontal filter slide**: "1" → [1 0 / 0 0]; tiny 6 × 6 "7" → first row 3 2 2 1 → [3 2 / 0 1]; rubber-stamp doodle; "Filters are LEARNED" box | The "7" grid: rows 11111 0 / 00001 0 / 00010 0 / 00010 0 / 00100 0 / 00100 0 |
| 11 | H6 | **The CNN stack** across the bottom of the board: Image → Conv+ReLU → Pool → Conv+ReLU → Pool → Flatten → Dense → Softmax → "7", with "edges → shapes → which digit?" | **The core picture of the video.** Keep it there for the whole build and the outro |
| 12 | H7 | **Softmax table** 3.0/1.5/0.5 → 76.6/17.1/6.3 = 100%, corner eˣ card, "2 classes = sigmoid: Student D 91.7%" | |
| 13 | I1–I9 | **7-box flow** (Load & look → ÷255 → Build CNN → Compile + Train → Test → Predict → Mistakes), ticked as each block runs; real sizes under the CNN stack (28×28 → 26×26×32 → 13×13×32 → 11×11×64 → 5×5×64 → 1,600 → 64 → 10) | |
| 14 | I7–I9 | **Result stamps**: 98.85% · 9,885/10,000; bar chart with one tall bar at 7; mini-cards for images #18, #717, #449 | 🔁 update to your live run |
| 15 | I11 | **Dense vs CNN card** (97.0% vs 98.85%; shifted 49% vs 88%) | On-screen "PAUSE & NOTE". Same numbers as notebook Block 13's table |

## 5. Colab prep checklist (do this the day before, and again 30 min before recording)

1. **Open the notebook** `notebooks/part-4-build-an-image-classifier.ipynb` in Colab (upload it, or open from GitHub). Save a copy to the channel's Drive and put the **share link** in the description (`<NOTEBOOK LINK>`). Set sharing to "Anyone with the link can view".
2. **Runtime type** (Runtime → Change runtime type). Either works:
   - **CPU** (default, what most viewers will use): expect roughly **1–3 minutes** for the 5 epochs on Colab's free CPU **[verify on the day]**. Our 4-core test machine took 34–45 s.
   - **T4 GPU**: faster (expect well under a minute) **[verify]**, but GPU results can differ slightly from CPU results and between runs.
   - Pick one and keep it for both the rehearsal run and the recording.
3. **Run all once before recording** (Runtime → Run all). This downloads and caches MNIST (~11 MB), warms up TensorFlow, and tells you **your** live numbers. Write them in the table in §6.
4. Then **Runtime → Restart session** (keeps the cached dataset on disk) and **Edit → Clear all outputs**, so the outputs appear fresh on camera. With `set_random_seed(42)` on the same runtime type, the re-run should give the same or near-identical numbers; if they change, use the recording-run numbers.
5. Check the first cell's printout: our test used **TensorFlow 2.21.0 / Keras 3.15.1**; Colab's image may show an older 2.x version (e.g. 2.19) **[verify]**. The notebook only uses long-stable Keras 3 APIs, so no change is needed.
6. **Readability**: browser zoom 125–150%; collapse the Colab left sidebar; Tools → Settings → Editor → larger font. Pre-scroll so each block title is visible when he names it.
7. **Training wait**: the editor time-lapses the Block 7 wait to ~10 s. Keep the full epoch log visible at the end so he can point at the numbers.
8. **Do not run the Fashion-MNIST homework on camera** (it re-trains everything). Optionally run it off-camera on a copy so he knows roughly what viewers will get (ours: 89.46%).
9. Expected run times on our test machine (Colab will differ): Block 2 load ~2 s (first time includes the download) · Block 5 summary instant · Block 7 train 34–45 s (CPU) · Block 8 evaluate ~1–2 s · Block 10 predict all 10,000 ~2 s · Block 11 ~2 s · Block 13 (optional) ~13 s (trains the Dense network, then tests both models; time-lapse it like Block 7).

## 6. Live results (🔁) and what to say if your numbers differ

The script uses the numbers from our tested run. Floating-point results differ slightly across hardware, TF versions and CPU vs GPU, so Deepak's Colab screen may not match exactly. **Rule: always say the number on his screen.** Fill this in after the rehearsal run:

| Where | Our tested value | Your rehearsal value |
|---|---|---|
| I6 epoch 1 → 5 train accuracy | 92.80% → 99.12% ("92.8 → 99.1") | |
| I6 loss epoch 1 → 5 | 0.2492 → 0.0289 ("0.25 → 0.03") | |
| I6 validation accuracy, epoch 5 | 98.95% ("about 99%") | |
| I7 test accuracy | **98.85%** (loss 0.0352) | |
| I7 correct / wrong | 9,885 / **115** | |
| I8 test image #0 | **7: 99.999%** | |
| I9 first 10 mistakes | 18, 62, 321, 445, 449, 625, 646, 684, 717, 726 | |
| I9 "right answer = 2nd guess" | **9 of 10** | |
| I9 highest-confidence mistake | #449: true 3 → said 5, 99% | |
| I11 Block 13 table | Dense **97.01%** / shifted **49.46%** · CNN **98.85%** / shifted **87.75%** (Dense 101,770 params) | |
| Training time (not spoken as a number) | 34–45 s (4-core CPU) | |

Fixed numbers that do **not** depend on his live run (say them as is): parameters 121,930 (architecture, always identical); 422 batches; 60,000 / 10,000. The Dense baseline (97.01%, 101,770 params) and the shift test (CNN 87.75%, Dense 49.46%) come from **notebook Block 13 (optional)**, which reproduces them exactly with seed 42 on our machine (three end-to-end runs, identical). They are 🔁 on his screen like the other live results: if Block 13 shows slightly different numbers, say his (and update the I11 card and description note 4).

**If the mistake images differ** (likely on a different machine), keep the I9 structure and fill in from his screen:
> Image ___ — true ___, model ___ అన్నది, ___% sure. నిజం చెప్పండి, మీకు కూడా అలాగే అనిపిస్తది కదా? … ఈ 10 లో ___ సార్లు correct answer model కి second choice. … కానీ ఇది చూడండి — image ___, ___% sure, అయినా తప్పు! Confidence వేరు, correctness వేరు.

Pick (1) one mistake a human would also misread, (2) the most-confident wrong one, (3) the 2nd-guess count. If no mistake in the first 10 is above ~90% confident, change the "99% sure" beat to "___% sure అయినా తప్పు", and keep the rule "confidence ≠ correctness".

## 7. Comment quiz (answers, not shown on screen)

1. **Colour photo, 100 × 100 pixels → how many numbers?** → 100 × 100 × 3 = **30,000**.
2. **Filter `1 0 −1` (3 rows) on patch rows `1 0 0` (3 rows)?** → 1 + 1 + 1 = **3** (a strong vertical edge: the same as Step 3 on the board).
3. **Max-pool 2, 7, 0, 5?** → **7**.
4. **Which is NOT deep-learning image classification?** → **(b) scanning a UPI QR code.** QR decoding is a fixed algorithm (finder squares + error correction), not a trained classifier.

Pin a comment with the answers about 24–48 hours after upload, and reply to a few correct answers by name.

**Homework follow-up for the pinned comment:** "Our Fashion-MNIST run: **89.46%** test accuracy (1,054 wrong). Lower than digits! It mostly confuses shirt ↔ T-shirt / coat / pullover and sneaker ↔ sandal / ankle boot. What did you get?"

Bonus question for the pinned comment: "A 6 × 6 image with a 3 × 3 filter gives a 4 × 4 feature map. What size do you get from a 28 × 28 image?" → **26 × 26** (shown in Block 5).

## 8. Accuracy notes

### 8.1 Arithmetic: every number in the script, checked with Python

Check scripts: `vd_check.py` (convolution, pooling, softmax, parameter counts) and `b11.py` (Block 11 filter check on the real MNIST test image #0) in the session scratchpad `/tmp/claude-0/-home-user-AI-Learning-series/991ce546-83cf-5aab-8ee0-6ee23f4b3e74/scratchpad/`. These are session scratch files; copy them into the repo if you want to keep them.

| Where | Number(s) | Check |
|---|---|---|
| F2, H3 | 6 × 6 "1" grid (0/255, then 0/1) | ✔ identical to the research brief |
| F3 | 6×6 = 36; 28×28 = 784; 12 MP × 3 = 3.6 crore (36,000,000) | ✔ matches Video A's "12 million × 3 = 36 million" |
| F5, H5 | Dense 784 × 128 + 128 = **1,00,480**; 12 MP RGB × 128 = 4,608,000,000 ≈ **460 crore**; Dense 784 × 32 + 32 = **25,120** | ✔ |
| F5, I11 | Dense 97.01% ("97%"); shifted 3 px: Dense 49.46% ("49%"), CNN 87.75% ("88%") | ✔ reproduced by notebook **Block 13** (seed 42; Dense = Flatten → 128 → 10, 101,770 params, same 5 epochs / batch 128 / 10% validation; shift = move right 3 px, fill with 0) |
| H3 | Window 1: products (0 0 −1)×3 → **−3**; window 2 → **1**; window 3 → **3**; full map [[−3 1 3 0],[−3 1 3 0],[−3 0 3 0],[−3 0 3 1]] | ✔ |
| H4 | ReLU map [[0 1 3 0],[0 1 3 0],[0 0 3 0],[0 0 3 1]] → 2×2 max pool **[[1 3],[0 3]]**; 16 → 4 numbers | ✔ |
| H5 | Horizontal filter on "1" → pooled [[1 0],[0 0]]; on "7" first map row **3 2 2 1**, pooled [[3 2],[0 1]] | ✔. The board "1" has a short flag and base, so its horizontal map is not all zero (one row of 1s before pooling; the base gives only negatives because it sits on the image's bottom edge). The script therefore says "a 1 is mainly a vertical stroke", not "a 1 has no horizontal strokes" |
| H5, I5 | 1 filter = 9 + 1 = 10; 32 filters = 320; Conv(64) = 64 × (3×3×32 + 1) = 18,496; both Conv = 18,816 | ✔ |
| H7 | softmax(3, 1.5, 0.5): e^x = 20.086, 4.482, 1.649, total 26.216 → **76.6% / 17.1% / 6.3%** (sum 100%) | ✔ |
| H7 | softmax(2.4, 0) = **91.7% / 8.3%** = σ(2.4) = 0.9168 (Student D) | ✔ |
| H8 | −ln(0.766) = 0.266 → "0.27" | ✔ |
| I2, I6 | 60,000 + 10,000 = 70,000; validation 10% = 6,000; 54,000 ÷ 128 = 421.9 → **422** batches | ✔ |
| I5 | Sizes 28 → 26 → 13 → 11 → 5; 5 × 5 × 64 = 1,600; Dense(64) = 1,600 × 64 + 64 = 102,464; Dense(10) = 650; total **121,930**; 102,464 / 121,930 = **84.0%** | ✔ |
| I6 | Epoch 1 acc 0.9280, loss 0.2492; epoch 2 acc 0.9788 ("97.9"); epoch 5 acc 0.9912, loss 0.0289, val 0.9895 | ✔ from the tested run |
| I7 | 98.85% × 10,000 = 9,885 → 115 wrong | ✔ |
| I8 | P(7) = 99.9994% → notebook prints `99.999%` | ✔ |
| I9 | #18: 3 → 5 (44%), 2nd 3 (39%); #717: 0 → 5 (56%); #449: 3 → 5 (99%), 2nd 3 (1%); 9 of the first 10 have the true digit as the 2nd guess (#726 is the exception: 4 then 5) | ✔ |
| I10 | Real MNIST test #0: horizontal filter's strongest rows = 8–9 (the 7's top bar); vertical filter's strongest column = 19 (the slanted stroke) | ✔ checked with `b11.py` |
| I11 | 10,000 × (1 − 0.9701) = 299 wrong; 299 / 115 = **2.6** | ✔ |
| Quiz | 30,000; 3; 7; (b); bonus 26 × 26 | ✔ |
| B | Day 11 quiz answers: 60 ÷ 20 = 3 × 10 = **30** updates; overfitting → stop near epoch 6; Dense(3): 2×3 + 3 + 3 + 1 = **13** | ✔ against Part 3 production-notes §8 |
| B | Day 11 facts: 320 students, batch 32 → 10 batches, 100 epochs → 1,000 updates, 90% test, Sita 38% → 95% | ✔ against `research/dl-content-research-part-3.md` |

### 8.2 Technical guard-rails in the script (keep these on edit)
- **Filters are learned, not hand-designed** (H2 disclaimer, H5 boxed note, I5, I10b). The board filter is explicitly "WE chose it for class, like w = 0.8 on Day 7".
- **Pooling keeps the maximum**, shrinks 16 → 4, and gives only *some* tolerance to small shifts ("often doesn't change") (H4). "MAX, not average" is said aloud.
- **Softmax gives percentages that are positive and add to 100%**; picking the biggest is a separate step; with 2 classes it equals the sigmoid (H7). "99% sure ≠ correct" is stated in H7 and shown live in I9.
- **A CNN learns with the same loop** (forward → log loss → backprop → gradient descent), and backprop reaches the filter weights too (H8). Only the wiring is new.
- **Accuracy is reported on test data, not training data** (I7, with a notes prompt). Validation is described as a mock test during training.
- **CNNs are not fully shift-invariant** (H8 doubt, I11: CNN 98.85% → 88% when shifted). Data augmentation is name-dropped only.
- **Computer vision ≠ always deep learning** (QR codes, F4). **Face unlock = verification, not classification** (F6).
- **"99%" only means MNIST-style digits** (I11 doubt: centring, 28 × 28, white-on-black preprocessing needed for your own photos).
- The CS-pedantic point that deep-learning "convolution" is technically cross-correlation (no kernel flip) is deliberately **not** said on camera; it doesn't matter because the filters are learned.
- The analogies are flagged as loose on camera: the teacher's window ("teacher knows the pattern; a filter learns it"), and the relative-walking-towards-you hierarchy ("simple → complex only; a CNN sees small edges first; real filters rarely have neat names").

### 8.3 Claims to be careful with / [verify]
- **No [verify]-tagged item from the research brief is stated as fact.** Deliberately left out: MNIST writer counts, Aadhaar face-auth figures, India Post's use of DL for PIN codes (the script only says MNIST is "a simple version of" reading PIN codes), OMR, the "10–20% of US cheques" LeNet claim, and the NPSS crop/pest counts. Colab timings and TF version are handled as 🔁 / "a few minutes".
- **Real-world examples used:** Google Lens naming a flower (widely known; Video A already used Lens); Hyderabad traffic cameras reading plates with police verification before a challan (RTI/NewsMeter and IIIT-H VIOLA sources in the brief); leaf-photo pest/disease apps (they exist, e.g. the government's NPSS uses image recognition; no counts quoted); X-ray TB flagging (Video A). QR = fixed algorithm (✔ in brief).
- **"A lot of the AI that works with images is built on these ideas" (E):** kept soft ("చాలా"). Many modern vision systems also use Vision Transformers; don't strengthen it to "all".
- **"Every pixel on your phone screen is three tiny lights" (F3):** true at this depth (red/green/blue sub-pixels). Some OLED layouts share sub-pixels; not worth mentioning.
- **Dense baseline + shift test (F5, I11):** now said as "you can check this yourself in Block 13" (F5) and "Block 13, optional" (I11), because the notebook reproduces them. **"Our team tested the notebook in advance" (G)** is true (the notebook was run end-to-end three times in review); keep "మా team" there.
- **Personal humility beat (H3):** "When I first studied CNNs I didn't understand feature maps; it clicked when I drew a grid on paper." This is a personal claim in his voice, worded differently from Video A ("took me two or three days") and Video B ("didn't click the first time"). **Keep it only if it's true for him**; otherwise cut that sentence (−8 s).
- **"The T in ChatGPT is Transformer" (L):** ✔ (Generative Pre-trained Transformer).
- **"Day 11 needed 100 epochs; here 5 are enough because each epoch already has 422 updates" (I6):** true for these runs (5 × 422 = 2,110 updates vs 1,000). Also helped by having far more data; the simplification is fine.
- **Mid-roll "90% not subscribed":** not used; generic line instead, as in Video B.

## 9. Continuity hooks

### 9.1 Back to Parts 1–3 (and Days 6–7), all checked against the earlier scripts / briefs
| Callback in this script | Source |
|---|---|
| Neuron = inputs × weights + bias → activation → output; layers; fully connected; 9 knobs | Video A (Day 9) |
| Day 9 board "answer-sheet photo → network learns features: lines, edges → letters → words"; "12 MP × 3 ≈ 36 million numbers" | Video A segment F (03:56–05:01) |
| Relative walking towards you from far away = simple → complex (with the order caveat) | Video A segment F (05:01–05:43) |
| Google Lens, chest X-ray TB flagging examples | Video A segment F (06:24–07:04) |
| ReLU (negatives → 0), Sita's h2 OFF; sigmoid; softmax name-dropped; log loss −ln(p); forward → loss → backprop → update loop; Adam = smarter GD | Video B (Day 10) F4, F6, H3, I6, K1 |
| Keras 9-knob network, model.summary = 9 params, 320 students, batch 32 → 10 batches/epoch, 100 epochs = 1,000 updates, test 90%, Sita 38% → 95% | Part 3 (Day 11) final script, segments K2, K4, K5, K6 ✔ |
| Epoch, batch, learning rate, overfitting; validation = mock test vs test = final exam; the overfitting "gap" between the two curves; round-up rule for batches; Adam = "smarter GD" named on Day 10 | Part 3 segments F–J, H4, K8 ✔. Softmax and multi-class loss were **not** taught in Part 3: this video introduces both itself (H7, I6) |
| Day 11 quiz answers (30 · overfitting → stop near epoch 6 · 13) | Part 3 production-notes §8 ✔. Re-check if Part 3's quiz is edited |
| "At the end of the last video we left a question: so far numbers, how does AI see a photo?" | Part 3's teaser. ✔ Matches the Part 3 draft script (`scripts/video-C-…/script-english.md`, segment L: "Until now we worked with numbers, but how does AI see a photo?"), which also shows 90% test accuracy and Sita 38% → 95% on camera. Re-check if Part 3 is edited |
| Student D z = 2.4 → 91.7%; w = 0.8 "assumed"; e = 2.718 | Day 7 (via Videos A/B) |
| Classification = predicting a category; multi-class | Day 6 (transcript available) |
| Supervised learning / features + label: said as "ముందు వీడియోస్ లో" | Avoids unverifiable Day 1–5 callbacks (Video A review fix) |

If the Part 3 script ends up not showing any of the Day 11 numbers on camera (90%, 95%, 1,000 updates), trim segment B to the generic version: "Keras లో అదే 9-knob network build చేసినం — summary, compile, fit with epochs and batch size, test data మీద evaluate, Sita కి predict."

### 9.2 Forward to Part 5 ("How AI Reads Text", plan Days 33–34)
- Teaser in L names **NLP, RNN, LSTM, Transformers** and "the T in ChatGPT is Transformer". The end card says "Next: How AI Reads Text".
- Seeds Part 5 can pick up:
  - "Day 12 లో image = numbers grid. Text ని కూడా numbers గా మార్చాలి" → tokens / embeddings.
  - Grid vs sequence: a CNN slides a window over a **grid**; text is a **sequence** where order matters → RNN/LSTM read it word by word → Transformers look at all words at once (attention).
  - "Same learning loop again": RNNs and Transformers also train with loss + backprop + gradient descent.
  - Optional one-liner for Part 5: Vision Transformers now apply the Transformer idea to images too (closes the loop with this episode).
- Open Part 5 by redrawing this episode's CNN stack next to a sentence written as a row of word boxes.

## 10. Segment timing (from English word counts at 175 wpm + run pauses)

| Seg | Time | Words | Seg | Time | Words |
|---|---|---|---|---|---|
| A0 | 00:00–00:33 | 97 | H6 | 15:08–15:58 | 146 |
| A | 00:33–00:47 | 40 | H7 | 15:58–16:57 | 171 |
| B | 00:47–02:20 | 271 | H8 | 16:57–17:37 | 118 |
| C | 02:20–02:39 | 57 | I1 | 17:37–18:12 | 100 |
| E | 02:39–03:12 | 94 | I2 | 18:12–18:42 | 70 (+6 s) |
| F1 | 03:12–03:51 | 114 | I3 | 18:42–19:05 | 61 (+2 s) |
| F2 | 03:51–04:58 | 195 | I4 | 19:05–19:24 | 51 (+2 s) |
| F3 | 04:58–05:29 | 91 | I5 | 19:24–20:05 | 115 (+2 s) |
| F4 | 05:29–06:33 | 187 | I6 | 20:05–21:10 | 160 (+10 s) |
| F5 | 06:33–07:47 | 216 | I7 | 21:10–21:35 | 66 (+2 s) |
| F6 | 07:47–08:06 | 56 | I8 | 21:35–21:54 | 51 (+2 s) |
| H1 | 08:06–08:49 | 125 | I9 | 21:54–22:39 | 121 (+3 s) |
| H2 | 08:49–09:59 | 203 | I10 | 22:39–23:21 | 111 (+4 s) |
| G | 09:59–10:23 | 72 | I11 | 23:21–24:04 | 118 (+3 s) |
| H3 | 10:23–12:35 | 383 | J / K / L | 24:04–25:43 | 104 / 63 / 119 |
| H4 | 12:35–13:38 | 186 |  |  |  |
| H5 | 13:38–15:08 | 262 |  |  |  |

Timing script: `review_d/retime.py` in the session scratchpad (same folder as §8.1; replaces `vd_time.py`). If you edit spoken lines, recompute and update both scripts and the chapter list.

---

## Self-review log (writer's pass before handing over)

| # | Issue found | Fix |
|---|---|---|
| 1 | First draft ran ~35 min (6,054 words), far over the 24–27 min target; the build alone was ~9 min. | Every spoken block tightened in both languages (cues unchanged). Now 4,295 words ≈ 25:06; build 6:18; mid-roll 38%. |
| 2 | Tightening cut the particle density (సో 11, అన్నమాట 6 in the whole script). | Restored natural సో / అంటే / అన్నమాట / కదా / సింపుల్ beats (now 27 / 33 / 18 / 19 / 7, about Video B's level) and mirrored them in English ("so", "you see", "right?"). |
| 3 | Notes prompts had a ~5 min gap in the build. | Added "ఈ లెక్క రాసుకోండి" at the 422-batch calculation (I6). |
| 4 | Two references to "Video B" in a viewer-facing line. | Changed to "Day 10" (viewers know the episodes by day). |
| 5 | Recap originally described Day 11 only generically. | Updated with the coordinator-confirmed Part 3 facts (320 / 32 / 10 / 100 / 1,000 / 90% / Sita 95%) and a fallback generic line in §9.1. |
| 6 | Block 11(a) claim ("the top bar lights up the horizontal map") was unverified. | Checked on the real MNIST test image #0 with numpy (§8.1). |
| 7 | Live Colab numbers can differ from the tested run, and the mistake indices especially. | Marked as 🔁 in both scripts; §6 gives a fill-in table and a Telugu fallback line for I9. |

---

## Review log

Independent review against the style-DNA checklist, `research/dl-content-research-part-4.md`, the Day 6–8 Telugu transcripts, Videos A–B (reviewed) and the **finished** Part 3 script and notes (`scripts/video-C-…/`). Every number in the script was recomputed in Python (convolution windows and full maps, ReLU, pooling, both horizontal-filter results, softmax, σ(2.4), −ln 0.766, all parameter counts, 422 batches, 2.6×, quiz answers, Part 3 quiz answers). The notebook (with the new Block 13) was run end-to-end **three times** with the venv (TF 2.21.0 / Keras 3.15.1, 4-core CPU, non-interactive matplotlib): every 🔁 value in §6 reproduced exactly each time (98.85% / 0.0352, 115 wrong, 7: 99.999%, the ten mistake indices and top-2 lines, epoch 1 0.9280 / 0.2492 / val 0.9808, epoch 5 0.9912 / 0.0289 / val 0.9895). The notebook is saved with outputs cleared.

| # | Issue | Severity | Fix |
|---|---|---|---|
| 1 | The Dense baseline (97.01%) and the shift test (Dense 49.46%, CNN 87.75%) were presented as "our team tested it" (F5, I11) but could not be reproduced from the notebook. | Medium (verifiability) | Added notebook **Block 13 (optional): Dense vs CNN, and shifted digits** (one markdown + one code cell after Block 12, seed 42; same 5 epochs / batch 128 / 10% validation; shift = 3 px right, zero-filled) and listed it in the title cell's plan. Output: Dense 101,770 params, **97.01% → 49.46%**; CNN **98.85% → 87.75%**: identical to the brief. F5 now says "you can check this yourself in Block 13"; I11 is titled after the block, says "Block 13, optional" and has a 💻 run cue; §6, §8.1, §8.3 and the description updated. G's "our team tested the notebook" stays (true). |
| 2 | Recap skipped the last-quiz-answers beat that Part 3 established (Part 3's B answers Day 10's quiz), and did not mention the Part 3 concepts this video leans on (validation = mock test in I6, overfitting). | Medium (series continuity) | B now opens Day 11 with "epoch, batch, learning rate, overfitting; validation = mock test, test = final exam" and gives quick answers to Part 3's quiz (30 updates · overfitting → stop near epoch 6 · 13 params, checked against Part 3 notes §8). Board quick card added. Recap's Day 11 numbers re-checked against Part 3's final script (K2, K4, K5, K6): all match. |
| 3 | H5 said a "1" "has no horizontal strokes", but the board "1" has a flag and a base (its horizontal map has a row of 1s before pooling). | Low-Medium (accuracy) | Now "a 1 is mainly a vertical stroke" (both languages); §8.1 note explains the map. |
| 4 | H5 said "backprop changes" the filters; Video B's guard-rail is "backprop calculates, gradient descent updates". | Low-Medium (consistency with Day 10) | "backprop and gradient descent together change them"; boxed board note and description note 3 updated. |
| 5 | H8 said backprop reaches "the 9 numbers in the filters"; the 2nd Conv layer's filters have 3 × 3 × 32 weights, and viewers who multiply 64 × 10 would not get I5's 18,816. | Low (precision) | Spoken line now "the numbers in the filters"; non-spoken I5 card footnote: 3 × 3 × 32 + 1 = 289 × 64 = 18,496 (+ 320 = 18,816). |
| 6 | Recap said Day 9 "left it as a black box": Video A never said that. | Low (don't overclaim recaps) | "Back then we didn't see how it does that." The board "open the box" visual is kept. |
| 7 | Notes-prompt gap of ~4.5 min between H7 and I6 (checklist: every 3–4 min); §0 claimed "longest gap ≈ 3 min". | Low | H8's key line now "ఇది రాసుకోండి: …"; header line corrected (16 spoken prompts, longest gap ≈ 3.5 min). |
| 8 | Part 3 teaches "round up" for batches and the overfitting gap between curves; I6 used neither callback. | Low (continuity, cheap win) | I6: "54,000 ÷ 128 = 421.9, round up: 422" and "validation about 99%, close to training: none of the overfitting gap we saw on Day 11" (val loss still falling at epoch 5, 0.0368 → 0.0365). |
| 9 | H8 doubt "Doesn't a CNN care where the digit is? Not completely: real numbers after the build." read as a telegraphic, translated line. | Low (voice) | Rewritten as his usual quoted doubt: "అన్నా, digit ఎక్కడ ఉన్నా CNN పట్టుకుంటదా?" పూర్తిగా కాదు — real numbers build అయినాక చూపిస్తా. |
| 10 | A few stiff Telugu phrasings: "కేవలం numbers", the abrupt "రోజూ చూసేవి —", "ఆ idea కి మాత్రమే". | Low (voice) | "జస్ట్ numbers ఏ", "మనం రోజూ చూసేవి చెప్తా —", "ఆ idea వరకే". |
| 11 | H3's personal humility line ("when I first studied CNNs I didn't understand feature maps…") is a personal claim. | Low (authenticity) | Flagged inline in both scripts as **"keep only if true"** (cut = −8 s); §8.3 already says the same. Not invented further. |
| 12 | Timestamps, chapters, runtime and segment budget went stale after the edits. | Low (production) | All 34 timestamps recomputed in both scripts (English words at 175 wpm + run pauses, I11 +3 s for Block 13); chapters, §0 header lines and §10 table updated. Runtime now **~25:43** (4,394 words + 36 s pauses; Telugu ≈ 3,840 words); mid-roll 09:59 ≈ **39%**; build 6:27. Two lines in B and I11 were trimmed to absorb the additions. |

**Checked, no change needed:** the 6 × 6 "1" and "7" grids; window products −3 / 1 / 3 and the full map; ReLU map and pooled [1 3 / 0 3]; 7's horizontal map first row 3 2 2 1 → [3 2 / 0 1]; 36 / 784 / 3.6 crore; 1,00,480, ≈ 460 crore, 25,120, 320, 121,930, 84.0%; softmax 76.6 / 17.1 / 6.3 and the 2-class = sigmoid bridge (91.7%); −ln 0.766 = 0.27; quiz answers (30,000 · 3 · 7 · b); Block 3's "253, 255" in training image 0; Block 11(a) maps (slanted stroke in the vertical map, top bar in the horizontal map) and (b) learned maps, by viewing the saved figures. Filters learned (not hand-designed), max not average, test vs training accuracy, validation as mock test, "not shift-immune", face unlock = verification, QR/UPI = fixed rules, no FASTag claim, no [verify] item stated as fact. Depth matches Parts 1–2 (one worked example, no new maths beyond multiply-add and the softmax card). Plan subtopics present: Day 31 (how AI processes images, classification examples), Day 32 (filters, feature maps, pooling, image recognition), Day 35 (dataset, training, testing, prediction). Code is narrated per block; block names match the notebook titles exactly (Blocks 1–13). Voice beats present: pitch + "Let's dive into the video", "Hey guys, welcome back to AI Learning Series Day 12", recap + running characters + catch-up nudge, numbered agenda with వచ్చేసి, reassurance before Concept 1 and before the maths, "Sorry for interrupting" mid-roll, doubt beats, disclaimed analogies, taxonomy recap, comment quiz, homework, notes + notebook in the description, Part 5 teaser and the exact sign-off. Part 3 alignment: softmax and multi-class loss are introduced here (H7, I6), not assumed; Adam is called the "smarter GD" named on Day 10 (also used in Part 3's K8); Part 3's teaser (how AI sees a photo) is picked up in B. English and Telugu match in content, numbers, segment IDs and timestamps.
