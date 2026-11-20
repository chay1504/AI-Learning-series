# Video D: "How AI Sees Images" (RECORDING SCRIPT, Telugu)

**Series:** AI Learning Series, **Day 12** on the channel (Deep Learning Part 4). This covers plan Day 31 (what is computer vision?), Day 32 (what is a CNN? filters, feature maps, pooling) and Day 35 (build an image classifier: MNIST in Colab). Plan Days 33–34 (NLP; RNN vs LSTM vs Transformer) are the next part.
**Previous episodes:** Day 9 "Inside a Neural Network" · Day 10 "How a Neural Network Learns" · Day 11 "Train Your First Neural Network" (Keras, 9-knob network).
**Runtime:** ~25:06 (≈ 25.1 min): 4,295 English-equivalent spoken words at 175 wpm (24:33) plus ~33 s of Colab run pauses. Allow ~27 min with drawing pauses.
**Companion files:** `script-english.md` (the same script in English, for checking content) · `production-notes.md` (titles, description, drawings list, Colab prep, quiz answers, accuracy notes) · notebook: `notebooks/part-4-build-an-image-classifier.ipynb`

**Legend**
- ⏱ timestamp (start – end), estimated from word count at 175 wpm, plus the Colab run pauses noted in the 💻 cues
- 🎙 spoken lines: Telugu grammar in Telugu script, English technical terms in Latin script. Lines in *"italic quotes"* are the on-screen English definitions; read them out exactly as written, then explain them in Telugu.
- 🖊 board / on-screen cues, in English for the editor. Draw them in the order listed, while you speak.
- 💻 Colab screen-share cues (build segment only). Block names match the notebook's block titles exactly.
- 🔁 = a **live result**. The number shown is from our tested run. If your Colab screen shows a slightly different number, say **your** number (see production-notes §6).

**Delivery notes**
- Drawings first, numbers second, code last. The 6 × 6 grid, the sliding 3 × 3 window, the feature map, the pooling blocks and the CNN stack all go on the board **before** Colab opens.
- In the build, never read code line by line. Point at the block, say what it does in concept words ("ఈ block = మనం board మీద గీసిన filter layer"), run it, react to the output.
- "రాసుకోండి" prompts sit at definitions, rules and key terms, never on the examples.
- The numbers are already checked (production-notes §8). If you change one, recompute everything that depends on it.
- **Running characters:** Student D (Day 7: 91.7%), Sita (Day 9–11). New object for today: **the handwritten "7" marks on an answer sheet**.

> **Production note on numbering:** Parts 1–3 are assumed to go out as Days 9, 10 and 11, so this video opens as **Day 12**. If the channel numbering changes, update the day number in segment A, the "జస్ట్ 12 videos" line in segment L, the title card, the title and the description (the notebook's title cell also says "Day 12").

---

## [A0] Cold-open hook + pitch
⏱ **00:00 – 00:33**

🎙
> Exams అయిపోయినాక teacher ప్రతి question పక్కన red pen తో marks రాస్తది కదా — 7, 5, 9. ఆ handwritten 7 ని మీరు ఒక్క second లో చదివేస్తారు. కానీ computer కి అది ఒక photo మాత్రమే — కొన్ని numbers అన్నమాట. మరి "ఇది 7" అని అది ఎట్లా చెప్తది? సో ఈరోజు మనం computer కి చదవడం నేర్పిస్తాం. Video end కి మీరే Colab లో ఒక model ని train చేసి, అది handwritten digits ని దాదాపు 99% correct గా చదవడం చూస్తారు. ఎవరైతే AI ని basics నుంచి, scratch నుంచి నేర్చుకోవాలి అనుకుంటున్నారో, మన channel ని subscribe చేసి పెట్టుకోండి. Let's dive into the video.

🖊
- Close-up B-roll: a red-pen "7" being written in the marks box of an answer sheet.
- Text pop: **"You see: 7 · Computer sees: numbers 🔢"**. Channel logo sting.

---

## [A] Welcome + headline promise
⏱ **00:33 – 00:47**

🎙
> Hey guys, welcome back to AI Learning Series Day 12! అప్పుడే మనం Day 12 కి వచ్చేసినం అన్నమాట. ఇప్పటిదాకా మనం numbers తోనే పని చేసినం కదా. ఈరోజు ఫస్ట్ టైం images లోకి వెళ్తున్నాం. How AI sees images — ఈరోజు ఇదే.

🖊
- Title card: **AI Learning Series · Day 12 · How AI Sees Images** *(renumber if needed)*
- Badge: **"Deep Learning · Part 4"**

---

## [B] Recap of Days 9–11 + catch-up
⏱ **00:47 – 02:01**

🎙
> సో ఫస్ట్ ఒక్కసారి recap చేసుకుందాం. Day 9 లో neuron చూసినం — inputs × weights + bias, తర్వాత activation, తర్వాత output. Layers, and మన చిన్న network: study hours, sleep hours లోపలికి, రెండు hidden neurons, ఒక output — 9 knobs. సో Day 10 లో అది ఎట్లా నేర్చుకుంటదో చూసినం — ReLU, sigmoid, loss, gradient descent, backprop, and ఆ loop: forward → loss → backprop → update → repeat.
>
> Day 11 లో అదే 9-knob network ని Keras లో build చేసినం. model.summary లో 9 parameters కనిపించినాయి కదా. Compile, fit — 320 students, batch size 32, ఒక epoch కి 10 batches, 100 epochs — అంటే 1,000 updates అన్నమాట. Model చూడని test students మీద 90% వచ్చింది. And Sita — మనం guess చేసిన knobs తో 38% అన్నది కదా, trained network 95% pass అని చెప్పింది.
>
> లాస్ట్ వీడియో end లో ఒక question తో వదిలేసినం కదా — ఇప్పటిదాకా numbers, మరి AI ఒక photo ని ఎట్లా చూస్తది? And Day 9 లో నేను ఒక బొమ్మ గీసిన — answer sheet photo network లోకి వెళ్తది, network దానంతట అదే features నేర్చుకుంటది: ఫస్ట్ lines, edges, తర్వాత letters, words. అప్పుడు దాన్ని ఒక black box లాగా వదిలేసినం. సో ఈరోజు ఆ box ని open చేస్తున్నాం. Day 9 నుంచి 11 వరకు చూడకుంటే ఒక్కసారి చూసి రండి — ప్రతి concept ఈరోజు మళ్ళీ వస్తది.

🖊
1. One neuron doodle: **inputs × weights + bias → activation → output**.
2. The 9-knob network: **S, L → h1, h2 → output**, with "9 knobs".
3. The Day 10 loop in a corner: **Forward → Loss → Backprop → Update → repeat ↺**.
4. Day 11 sticky note: **Keras · 320 students · batch 32 → 10 batches/epoch · 100 epochs = 1,000 updates · test 90% · Sita 38% → 95% ✔**.
5. Flash Day 9's board: **answer-sheet photo → [network] → Pass**, with "edges → letters → words". Draw a big box around the network labelled **"black box → TODAY we open it 🔓"**.

---

## [C] Agenda
⏱ **02:01 – 02:21**

🎙
> సో ఈరోజు ఏమేం చూడబోతున్నాం అంటే — pen తో రాస్తున్నా. ఫస్ట్ వచ్చేసి computer vision — computer కి image ఎట్లా కనిపిస్తది. సెకండ్ వచ్చేసి CNN — Convolutional Neural Network: filters, feature maps, pooling. ఇదే main topic. థర్డ్ వచ్చేసి మనమే Google Colab లో ఒక image classifier build చేద్దాం — handwritten digits చదివే model.

🖊
- Handwrite a numbered list:
  1. What is Computer Vision?
  2. What is a CNN? (filters · feature maps · pooling)
  3. Build an image classifier (MNIST in Colab)
- Corner note: **"Drawings first ✏️ → numbers → code last 💻"**

---

## [E] Reassurance + stakes + notes
⏱ **02:21 – 02:53**

🎙
> చాలా మంది "ఏంటన్నా, convolution, pooling… పేర్లే భయంగా ఉన్నాయి" అనుకుంటారు కదా. అస్సలు భయపడకండి. ఈరోజు కొత్త maths ఏం లేదు — 9 numbers multiply చేసి add చేస్తాం, అంతే సింపుల్. Class 10 student calculator లో check చేయొచ్చు. And ఒక secret — CNN లో కొత్తది దాదాపు ఏం లేదు. Weights, bias, ReLU, loss, backprop — అన్నీ మీకు ఆల్రెడీ తెలుసు. Google Lens అయినా, X-ray screening tools అయినా — images తో పని చేసే చాలా AI ఈ ideas మీదే build అయింది. సో చాలా important. అందరూ notes రాసుకోండి.

🖊
- Sticky note: **"New today: only how the neurons are connected. Everything else you already know ✔"**

---

## [F] CONCEPT 1: Computer vision

### F1. Announce + definition + name unpack
⏱ **02:53 – 03:32**

🎙
> సో ఫస్ట్ topic — computer vision. Definition screen మీద ఉంది, రాసుకోండి.
>
> *"Computer vision is the field of AI that enables computers to get useful information from images and videos: what is in them, where it is, or what it says."*
>
> అంటే ఏంటిది? పేర్లోనే ఉంది కదా — computer కి vision, అంటే చూపు. సో camera photo తీయగలదు, కానీ ఆ photo లో ఏముందో అర్థం చేసుకోవడం వేరే విషయం. ఆ అర్థం చేసుకునే part నే computer vision అంటాం అన్నమాట. మూడు phrases గుర్తుపెట్టుకోండి — దాంట్లో ఏముంది, cat ఆ dog ఆ; అది ఎక్కడ ఉంది; and దాంట్లో ఏం రాసి ఉంది. ఇవి కాసేపట్లో మళ్ళీ వస్తాయి.

🖊
1. Definition card (English). ✍️ "Write it down".
2. Split the name: **COMPUTER + VISION (చూపు)**. Doodle: camera 📷 → "takes the photo" vs 🧠 → "understands the photo" = computer vision.
3. Underline the three phrases: **what · where · what it says**.

### F2. An image is a grid of numbers (drawing first)
⏱ **03:32 – 04:39**

🎙
> ఇప్పుడు ఇక్కడ most important point. Computer కి photo ఎట్లా కనిపిస్తది? మనకి కనిపించినట్టే ఆ? No. కేవలం numbers — ఒక numbers table అన్నమాట. Board చూడండి — ఒక చిన్న 6 by 6 grid, 36 squares, మన school graph book లాగా. ఇప్పుడు కొన్ని squares నింపి ఒక "1" రాస్తా — పైన flag, మధ్యలో నిలువు గీత, కింద base. ఈ ఒక్కో చిన్న square నే pixel అంటాం అన్నమాట — picture element. And ప్రతి pixel ఒక number: black 0, full white 255, మధ్యలో grey. ఈరోజు dataset లో black background మీద white ink — సో ink 255, ఖాళీ 0. Left side మనకి కనిపించేది, right side computer కి కనిపించేది. Definition రాసుకోండి:
>
> *"A digital image is a grid of tiny squares called pixels. In a grayscale image, each pixel is one number from 0 (black) to 255 (white)."*
>
> Graph book లో squares నింపితే బొమ్మ వస్తది కదా — image కూడా అంతే సింపుల్. Real photos లో ఆ squares లక్షల్లో, కోట్లలో ఉంటాయి, అంతే తేడా.

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
⏱ **04:39 – 05:10**

🎙
> సో మరి colour photo? ప్రతి pixel కి మూడు numbers — Red, Green, Blue, RGB. మీ phone screen లో ప్రతి pixel మూడు చిన్న lights. Red 255, green 0, blue 0 — pure red. మూడూ 255 — white. మూడూ 0 — black. రాసుకోండి: grayscale అంటే pixel కి ఒక number, colour అంటే మూడు. వీటినే channels అంటాం అన్నమాట. ఇక size — మన grid 36 numbers. ఈరోజు dataset లో 28 × 28 = 784. And Day 9 phone photo — 12 megapixels × 3 — ఒక్క photo కి దాదాపు 3.6 కోట్ల numbers!

🖊
1. One pixel blown up into three boxes: **R | G | B = 255 | 0 | 0 → red**. Below: **255 | 255 | 255 → white · 0 | 0 | 0 → black**.
2. Write: **Grayscale = 1 number per pixel · Colour = 3 numbers per pixel (3 channels)**. ✍️
3. Size ladder: **6 × 6 = 36 → 28 × 28 = 784 → 12 MP photo × 3 ≈ 3.6 crore numbers**.

### F4. Three vision tasks + where we see them + "not always deep learning"
⏱ **05:10 – 06:13**

🎙
> Computer vision లో మూడు main పనులు — అవే మూడు phrases. ఫస్ట్ వన్ వచ్చేసి image classification — మొత్తం image కి ఒక్క label, "ఈ digit 7". Category predict చేసేదే classification — Day 6 లో చూసినం కదా. 0 నుంచి 9 అంటే 10 categories — multi-class. సెకండ్ వన్ వచ్చేసి object detection — ప్రతి object చుట్టూ ఒక box, traffic camera number plate చుట్టూ box వేసినట్టు. థర్డ్ వన్ వచ్చేసి segmentation — ప్రతి pixel కి label: road, మనిషి, sky. సో ఈరోజు మనం చేసేది classification అన్నమాట.
>
> రోజూ చూసేవి — Google Lens flower పేరు చెప్తది. Hyderabad traffic cameras number plates చదువుతాయి, challan పంపే ముందు police verify చేస్తారు. Leaf photo చూసి farmers కి pest, disease చెప్పే apps ఉన్నాయి. కానీ కన్ఫ్యూజ్ అవ్వద్దు — computer vision అంటే ఎప్పుడూ deep learning కాదు. UPI QR code scan కూడా camera, image ఏ — కానీ అది fixed rules తో చదువుతారు, model train చేయాల్సిన పని లేదు. అంటే rules రాయలేనంత variety ఉన్నప్పుడు deep learning కావాలి — handwriting, faces, leaves, X-rays.

🖊
1. Three small boxes side by side (✍️ write the three names):
   - **Classification:** whole photo → "7" / "Cat"
   - **Detection:** photo with rectangles → "Car", "Plate"
   - **Segmentation:** photo with coloured regions → "Road / Person / Sky"
   Tick **Classification** = "today".
2. Icon strip as he speaks: 🔍 Google Lens (flower → name) · 🚦 Traffic camera (plate → police verify → challan) · 🌿 Leaf photo → pest/disease · 🩻 X-ray → "possible TB, doctor to check".
3. QR code icon with a red stamp: **"Camera ✔, deep learning ✘ (fixed rules)"**. Next to it: **"DL = when rules are impossible to write: handwriting, faces, leaves"**.

### F5. Why a plain Dense network struggles: three fingers
⏱ **06:13 – 07:24**

🎙
> ఇప్పుడు doubt — "అన్నా, image అంటే numbers ఏ కదా. ఈ 784 numbers ని Day 11 Dense network కి ఇస్తే సరిపోదా?" పని చేస్తది, కానీ మూడు problems ఉన్నాయి. మూడు fingers — రాసుకోండి.
>
> ఫస్ట్ finger — weights చాలా ఎక్కువ. Dense అంటే fully connected. 784 pixels నుంచి 128 neurons — 784 × 128, ప్లస్ 128 biases — 1,00,480 parameters! Day 11 లో 9 ఏ. 12 megapixel colour photo అయితే ఒక్క layer కే దాదాపు 460 కోట్లు. Impossible కదా.
>
> సెకండ్ finger — neighbours పోతారు. Dense కి ఇవ్వాలి అంటే grid ని ఒక్క పొడవాటి line లాగా పరచాలి — row తర్వాత row. దీన్నే flatten అంటాం. ఈ pixel, దాని కింద ఉండే pixel — ఒకే గీత మీద ఉన్నాయి. కానీ line లో 28 places దూరం! సో Dense కి అవి neighbours అని తెలియదు. కానీ images లో meaning అంతా neighbours లోనే ఉంటది.
>
> థర్డ్ finger — digit కొంచెం జరిగితే. 7 ని 3 pixels right కి జరిపితే మనకి same 7, Dense కి దాదాపు కొత్త pattern. మా team test చేసింది: normal digits మీద 97% చెప్పిన Dense network, ప్రతి digit ని 3 pixels జరిపితే 49% కి పడిపోయింది! సో ఈ మూడు problems కి answer ఏంటి అంటే — మన next topic.

🖊
Draw three fingers ✋ and write one problem per finger (✍️):
1. **Too many weights:** 784 × 128 + 128 = **1,00,480** in layer 1 (vs Day 11's 9!). 12 MP colour photo → **≈ 460 crore**.
2. **Loses "nearby-ness":** 28 × 28 square → arrow "Flatten" → one long line of dots. Circle two pixels one above the other in the grid; in the line, draw them **28 dots apart**.
3. **Shifted digit = new pattern:** a "7", and the same "7" moved 3 squares right. Caption: **"Dense: 97% → 49% when shifted 3 pixels"**.

### F6. Doubt + one-line recap
⏱ **07:24 – 07:43**

🎙
> ఇంకో doubt — face unlock image classification ఆ? Strictly కాదు — అది verification: "ఈ face register చేసిన face ఒకటేనా?" Neural networks వాడుతారు, కానీ పని వేరు. సింపుల్ — numbers grid లో patterns కనిపెట్టి, image లో ఏముందో, ఎక్కడ ఉందో, ఏం రాసి ఉందో అర్థం చేసుకునేదే computer vision.

🖊
- Small chip: **Face unlock = verification ("same person?"), not classification**.
- Recap card: **Computer vision = finding patterns in a grid of numbers → what / where / what it says.**

---

## [H] CONCEPT 2: CNN (Convolutional Neural Network)

### H1. Announce + definition + name unpack
⏱ **07:43 – 08:26**

🎙
> సో computer vision అయిపోయింది. ఇప్పుడు main concept — CNN, Convolutional Neural Network. Definition రాసుకోండి.
>
> *"A Convolutional Neural Network (CNN) is a neural network designed for grid-like data such as images. Instead of connecting every pixel to every neuron, it slides small learnable filters across the image to detect local patterns, and stacks layers to combine them into bigger shapes and objects."*
>
> పేరులో రెండు parts. "Neural network" — మనకి తెలుసు, అవే neurons, weights, layers. "Convolutional" — ఇదే కొత్త word. అంటే ఒక చిన్న window ని image మీద slide చేస్తూ, ప్రతి చోట ఒక చిన్న calculation చేయడం — అంతే సింపుల్. Keywords: small learnable filters; local patterns — ఒక గీత, ఒక మూల; and layers stack చేసి పెద్ద shapes.

🖊
1. Definition card (English). ✍️
2. Split the name: **CONVOLUTIONAL = slide a small window + calculate at every spot** | **NEURAL NETWORK = same neurons, weights, layers ✔**.
3. Underline: **small learnable filters · local patterns · stacks layers**.

### H2. Filter = the teacher's 3 × 3 window (and it is our old neuron)
⏱ **08:26 – 09:35**

🎙
> మరి filter అంటే? రాసుకోండి:
>
> *"A filter (also called a kernel) is a small grid of weights, usually 3 × 3. It looks at one small patch of the image at a time, multiplies each pixel by its weight, adds them up (plus a bias) and gives one number. Then it slides to the next position."*
>
> ఒక example — ఒక teacher దగ్గర ఒక cardboard ఉంది, మధ్యలో 3 by 3 చిన్న కిటికీ కట్ చేసి ఉంది. దాన్ని answer sheet మీద జరుపుకుంటూ ఒకే ఒక్క విషయం వెతుకుతది — tick mark. ప్రతి position కి వేరే paper మీద score రాస్తది: tick బాగా ఉంది 3, లేదు 0. ఆ score sheet నే feature map అంటాం అన్నమాట. ఇంకో teacher ఇంకో window తో cross marks వెతుకుతది — అది ఇంకో filter. And ఒక secret — 9 pixels × 9 weights, add, ప్లస్ bias. ఎక్కడో చూసినం కదా? Day 9 neuron! సో filter అంటే మన పాత neuron ఏ, చిన్న window గుండా చూస్తది అంతే. కానీ దీన్నే exact example అనుకోకండి — teacher కి tick ఎట్లా ఉంటదో ముందే తెలుసు. CNN filter random numbers తో start అయి, data నుంచి నేర్చుకుంటది. చాలా important — మళ్ళీ చెప్తా.

🖊
1. Definition card (English). ✍️
2. Doodle: an answer sheet, a cardboard with a **3 × 3 window cut out**, arrows showing it sliding left → right, row by row. A separate "score sheet" grid beside it labelled **"feature map"**.
3. Second teacher with a different window: **"another filter → another pattern"**.
4. Write: **Filter = our Day 9 neuron looking through a small window (9 inputs × 9 weights + 1 bias)**.
5. Chip: **"Teacher knows the pattern; a CNN filter LEARNS it."**

### [G] Mid-roll CTA
⏱ **09:35 – 10:00**

🎙
> వీడియో మధ్యలో interrupt చేస్తున్నందుకు sorry. ఒక్క second pause చేసి like చేయండి. Three dots క్లిక్ చేసి hype చేయండి — మీలాంటి ఇంకా చాలా మంది beginners కి reach అవుతది. ఈ series చూసేవాళ్ళలో చాలా మంది ఇంకా subscribe చేయలేదు. ఈరోజు Colab notebook ని మా team ముందే test చేసింది, మీకు errors రాకుండా — మీ like, subscribe మాకు అదే energy ఇస్తది. ప్లీజ్ support చేయండి. సో మళ్ళీ filter దగ్గరికి వద్దాం.

🖊
- Like / three-dots → **Hype** / Subscribe animation. Keep the filter definition card visible underneath so the cut back is seamless.

> **Note:** his usual stat is "90% of viewers are not subscribed". Only say a number if YouTube Studio supports it on the day of recording; otherwise keep the generic line above.

### H3. The worked convolution: one window, then the whole feature map (the one worked example)
⏱ **10:00 – 12:11**

🎙
> Maths గురించి టెన్షన్ పడకండి — multiply and add మాత్రమే. స్లో స్లోగా చూద్దాం. మన "1" grid తీసుకుందాం. Simple గా ఉండడానికి 255 ని 1 అని రాస్తున్నా — ink 1, ఖాళీ 0. అంటే 255 తో divide చేసినం; build లో కూడా ఇదే చేస్తాం. ఇప్పుడు ఒక filter — నేనే choose చేస్తున్నా: మూడు rows, ప్రతి row లో 1, 0, −1. "Left bright, right dark" ఉంటే పెద్ద number ఇస్తది — అంటే నిలువు గీత right edge ని పట్టుకుంటది. దీన్నే vertical edge filter అంటాం అన్నమాట.
>
> Step 1 — ఈ red 3 by 3 square top-left corner లో. లోపల: 0 0 1, 0 1 1, 0 0 1. ప్రతి pixel ని filter లో same position number తో multiply చేయాలి. Left column — filter 1, pixels అన్నీ 0 — 0. Middle — filter 0 — 0. Right column — filter −1, pixels 1, 1, 1 — వచ్చేసి −1, −1, −1. Add చేస్తే — −3. Feature map ఫస్ట్ box లో −3 రాస్తున్నా.
>
> Step 2 — ఒక్క pixel right. Patch: 0 1 0, 1 1 0, 0 1 0. Left column 0, 1, 0 into 1 — 1. మిగతావి 0. Total 1.
>
> Step 3 — ఇంకొక్కటి. Patch: 1 0 0, 1 0 0, 1 0 0. Left column 1, 1, 1 — 3! పెద్ద number. ఎందుకు? గీత left లో ఉంది, right ఖాళీ — filter వెతికే pattern exact గా ఇదే. Perfect match అన్నమాట.
>
> సో ఇట్లా జరుపుకుంటూ వెళ్తే — row కి 4 positions, 4 rows — 4 by 4 feature map. Full map screen మీద. మూడో column అంతా 3 — "ఇక్కడ పై నుంచి కింది దాకా నిలువు edge ఉంది". ఫస్ట్ column అంతా −3 — opposite edge, దాన్ని flip చేసిన filter పట్టుకుంటది. రాసుకోండి:
>
> *"A feature map is the grid of numbers a filter produces as it slides over the image. Big values show where the filter's pattern was found."*
>
> సింపుల్ గా — filter pattern ఎక్కడెక్కడ ఉందో చూపించే heat map అన్నమాట. నిజం చెప్పాలి అంటే, నేను ఫస్ట్ టైం CNN చదివినప్పుడు feature map అస్సలు అర్థం కాలేదు. ఇట్లనే paper మీద చిన్న grid గీసి చేతితో calculate చేసినప్పుడు click అయింది. మిగతా boxes మీరే calculator తో check చేయండి.

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
⏱ **12:11 – 13:15**

🎙
> నెక్స్ట్ — ఈ map మీద ReLU, Day 10 లో చూసినం: negative అయితే 0. సో −3 లు అన్నీ 0 — "ఇక్కడ pattern లేదు". Sita h2 ని off చేసిన అదే ReLU. ఇప్పుడు pooling. రాసుకోండి:
>
> *"Max pooling shrinks a feature map by keeping only the largest value in each small block, usually 2 × 2. It keeps the strongest signal and makes the network a little less sensitive to small shifts."*
>
> 4 by 4 map ని నాలుగు 2 by 2 blocks గా విడదీసి, ప్రతి block లో biggest ఒక్కటే ఉంచుతాం. Top-left 0, 1, 0, 1 — 1. Top-right — 3. Bottom-left అన్నీ 0 — 0. Bottom-right — 3. సో 16 numbers నుంచి 4: 1, 3, 0, 3. Principal "నాలుగు unit test marks అక్కర్లేదు, best mark ఒక్కటి చెప్పు" అన్నట్టు. Map నాలుగో వంతు అయింది, కానీ message పోలేదు — right side లో strong నిలువు గీత. కన్ఫ్యూజ్ అవ్వద్దు — max pooling అంటే maximum, average కాదు. అసలు ఎందుకు pool చేయాలి? Numbers తగ్గుతాయి, calculations తగ్గుతాయి. And గీత ఒక pixel జరిగినా block max చాలాసార్లు మారదు.

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
⏱ **13:15 – 14:43**

🎙
> ఇప్పుడు ఇదే filter ని పక్కకి తిప్పితే — 1 1 1, 0 0 0, −1 −1 −1 — horizontal edge filter. మన "1" మీద pool చేసినాక దాదాపు అంతా 0: 1, 0, 0, 0 — "1" లో అడ్డ గీతలు లేవు. "7" మీద — map ఫస్ట్ row 3, 2, 2, 1 — పైన అడ్డ గీత! సో 1 vertical detector ని వెలిగిస్తది, 7 horizontal detector ని. Detectors కలిపితే digits ని వేరు చేయొచ్చు కదా.
>
> ఇప్పుడు చాలా చాలా important point, రాసుకోండి: real CNN లో filters ని ఎవరూ design చేయరు. 1, 0, −1 నేను class కోసం మాత్రమే choose చేసిన — Day 7 లో w = 0.8 assume చేసినట్టు. Real filters random తో start అవుతాయి, backprop వాటిని మిగతా weights లాగే మారుస్తది. ఏ patterns వెతకాలో network ఏ నేర్చుకుంటది — Day 9 లో "features ని దానంతట అదే నేర్చుకుంటది" అన్నాం కదా, దాని అర్థం ఇదే.
>
> And ఒక filter = 9 weights + 1 bias = 10 numbers, image లో ప్రతి position లో అవే — ఎందుకంటే నిలువు గీత ఎక్కడ ఉన్నా నిలువు గీత ఏ. Page మొత్తం ఒకే rubber stamp లాగా. దీన్నే parameter sharing అంటాం అన్నమాట. మన ఫస్ట్ layer లో 32 filters — 320 parameters. Dense లో 784 pixels నుంచి 32 neurons కే 25,120. ఫస్ట్ finger solve. Filter ఎప్పుడూ neighbours ని కలిపి చూస్తది — సెకండ్ finger solve. Same filter అన్ని చోట్లా వెతుకుతది కాబట్టి జరిగిన గీత కూడా దొరుకుతది, pooling కొంచెం help — థర్డ్ finger దాదాపు solve.

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
⏱ **14:43 – 15:33**

🎙
> ఇప్పుడు మొత్తం CNN ఒక్క picture లో — ఈరోజు most important drawing. రాసుకోండి. Image → Conv + ReLU → Pool → Conv + ReLU → Pool → Flatten → Dense → Softmax → answer. Factory line లాగా చదవండి. ఫస్ట్ Conv — చిన్న edges పట్టుకుంటది. Pool — shrink. సెకండ్ Conv — edges కలిపి shapes: మూలలు, loops, 7 పైన అడ్డ గీత. మళ్ళీ Pool. సో Flatten ఇప్పుడు problem కాదు, ముఖ్యమైన features ఆల్రెడీ బయటకి వచ్చినాయి. తర్వాత Dense — మన Day 9 network — "పైన loop, right లో నిలువు గీత — ఇది 9" అని decide చేస్తది. Edges → shapes → which digit. Day 9 లో దూరం నుంచి వచ్చే relative example లాగా simple నుంచి complex — ఆ idea కి మాత్రమే, CNN ఫస్ట్ చిన్న edges చూస్తది. And real filters కి "loop detector" లాంటి neat పేర్లు చాలాసార్లు ఉండవు.

🖊
- Big pipeline across the bottom of the board (keep it there for the build):
  **Image → [Conv + ReLU] → [Pool] → [Conv + ReLU] → [Pool] → Flatten → Dense → Softmax → "7"**
- Under the stages write: **"edges" → "shapes / parts" → "which digit?"** ✍️
- Chip: **"Analogy: simple → complex only. CNN sees small edges first. Real filters rarely have neat names."**

### H7. Softmax: percentages that add to 100
⏱ **15:33 – 16:32**

🎙
> Last box — softmax. Day 10 లో పేరు మాత్రమే చెప్పిన. రాసుకోండి:
>
> *"Softmax turns the output layer's raw scores into probabilities that are all positive and add up to 100%. The biggest score gets the biggest share."*
>
> Last layer లో 10 neurons, ఒక్కో digit కి ఒక score. మూడు తీసుకుందాం: "1" కి 3, "7" కి 1.5, "4" కి 0.5. Softmax ప్రతి score ని e power తో positive చేస్తది — అదే e, 2.718 — తర్వాత total తో divide చేస్తది. Result: "1" వచ్చేసి 76.6%, "7" 17.1%, "4" 6.3%. Total 100%. Formula corner లో ఉంది, machine ఏ చేస్తది. And రెండే classes — pass, fail — అయితే? Student D scores 2.4, 0 ఇస్తే 91.7%, 8.3% — exact గా Day 7 sigmoid! Sigmoid అంటే two-class softmax అన్నమాట. కన్ఫ్యూజ్ అవ్వద్దు — softmax percentages ఇస్తది; biggest ని pick చేయడం separate last step, 50% threshold లాగా. And 99% అంటే 99% sure, ఎప్పుడూ correct అని కాదు. Build లో ఇది కనిపిస్తది.

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
⏱ **16:32 – 17:10**

🎙
> Doubt — "అన్నా, CNN training ఏదైనా కొత్త method ఆ?" కాదు! అదే Day 10 loop — forward, loss, backprop, update, repeat. అదే log loss — true digit "1", model 76.6% ఇస్తే loss 0.27. Backprop ఆ blame ని filters లో ఉండే 9 numbers కి కూడా పంపుతది, gradient descent వాటిని కొంచెం మారుస్తది. సో ఎట్లా నేర్చుకుంటది — అది కొత్త కాదు. Neurons ఎట్లా connect అయి ఉంటాయి — అదొక్కటే కొత్త. Digit ఎక్కడ ఉన్నా CNN పట్టించుకోదా? పూర్తిగా కాదు — real numbers build తర్వాత. సింపుల్ — filters slide చేసి patterns కనిపెట్టి, pool తో shrink చేసి, layers stack చేసి, softmax తో percentages ఇచ్చేదే CNN. అంతే సింపుల్.

🖊
1. Point to the Day 10 loop in the corner: **Forward → Loss → Backprop → Update ↺** and add an arrow from "Backprop" into the filter drawing: **"blame reaches the filters too"**.
2. Write: **True "1", model 76.6% → loss = −ln(0.766) = 0.27**.
3. Big line ✍️: **"Nothing new in HOW a CNN learns. Only HOW the neurons are connected is new."**
4. Recap card: **CNN = slide filters → feature maps → ReLU → pool → stack → Dense → softmax %.**

---

## [I] CONCEPT 3: Build an image classifier (MNIST in Colab)

### I1. Open the notebook + the dataset
⏱ **17:10 – 17:44**

🎙
> సో theory అయిపోయింది. ఇప్పుడు నాకు ఇష్టమైన part — build. Notebook link description లో ఉంది, నాతో పాటు run చేయండి. Line by line code కాదు — ప్రతి block ఏం చేస్తదో చెప్పి, board మీద ఎక్కడ ఉందో చూపిస్తా. సో dataset పేరు వచ్చేసి MNIST: 70,000 handwritten digits, 60,000 training కి, 10,000 testing కి. Computer vision లో "hello world" — answer sheet marks, postal cover మీద PIN code చదవడానికి ఒక simple version అన్నమాట. Runtime → Change runtime type: normal CPU సరిపోతది, training కి కొన్ని నిమిషాలు; T4 GPU అయితే ఇంకా fast.

💻
- Screen-share Colab with `part-4-build-an-image-classifier.ipynb` open at the title cell. Cursor on the "plan, block by block" list.
- Show **Runtime → Change runtime type** menu for 2 seconds.

🖊
- Lower-third: **"Notebook link in description ↓"**. Name card: **MNIST: 60,000 training + 10,000 test images · 28 × 28 · digits 0–9**.
- Put the 7-box flow on the side of the board (tick each as it runs): **Load & look → ÷255 → Build CNN → Compile + Train → Test → Predict → Mistakes**.

### I2. Block 1: Setup + Block 2: Load the dataset
⏱ **17:44 – 18:14**

🎙
> Block 1: Setup — numbers కి NumPy, బొమ్మలకి Matplotlib, and Keras — Day 11 లో వాడిందే. Seed fix చేస్తున్నాం, starting weights ప్రతిసారి same రావడానికి. Run. Block 2: Load the dataset — MNIST Keras లోనే ఉంది. 60,000 training images, 28 by 28; 10,000 test images; ప్రతి image కి label — మన answer key. అంటే features pixels, label digit.

💻
- Run **Block 1: Setup** (prints the TensorFlow / Keras versions). *(run pause ~3 s)*
- Run **Block 2: Load the dataset**. Highlight `Training images: (60000, 28, 28)`, `Test images: (10000, 28, 28)` and `First 10 labels: [5 0 4 1 9 2 1 3 1 4]`. *(run pause ~3 s; first run downloads the data, so run it once before recording)*

🖊
- Tick box 1 "Load & look". Write **features = pixels · label = digit (answer key)**.

### I3. Block 3: An image is just a grid of numbers
⏱ **18:14 – 18:37**

🎙
> Block 3: "An image is just a grid of numbers". ఫస్ట్ training image numbers లాగా. Pause చేసి చూడండి — చుట్టూ 0 లు, మధ్యలో 253, 255 లాంటి పెద్ద numbers. కళ్ళతో follow చేస్తే… ఒక 5 కనిపిస్తది కదా! Label కూడా 5. Board మీద 6 by 6, ఇక్కడ 28 by 28. కింద 18 images బొమ్మల్లాగా.

💻
- Run the first cell of **Block 3**. Zoom into the printed 28 × 28 grid; trace the 5 with the cursor. Show `Label: 5`. *(run pause ~2 s)*
- Run the second cell: the 3 × 6 grid of digit pictures with labels.

🖊
- Point from the screen to the board's 6 × 6 "1": **"same idea, 28 × 28 = 784 numbers"**.

### I4. Block 4: Prepare the data
⏱ **18:37 – 18:56**

🎙
> Block 4: Prepare the data — 255 తో divide, అన్నీ 0 నుంచి 1 మధ్యలో, board మీద చేసినట్టే కదా; చిన్న numbers తో learning smooth. And ఒక channel add — grayscale కి 1, colour అయితే 3. New shape: 60,000, 28, 28, 1 — min 0, max 1.

💻
- Run **Block 4: Prepare the data**. Highlight `New shape: (60000, 28, 28, 1) | min: 0.0 | max: 1.0`. *(run pause ~2 s)*

🖊
- Tick box 2 "÷255". Point to the board's "÷ 255 → 0/1" grid.

### I5. Block 5: Build a small CNN
⏱ **18:56 – 19:38**

🎙
> Block 5: Build a small CNN — ఈ block = board మీద గీసిన CNN stack! పై నుంచి కిందకి: Conv2D 32, 3 by 3 — మన filter layer, కానీ 32 filters, అన్నీ random తో start, relu తో. MaxPooling2D 2 by 2 — మన pooling. మళ్ళీ Conv2D 64, pooling. Flatten. Dense 64 — Day 9 layer. Dense 10, softmax — 10 percentages. Sizes: 28 నుంచి 26 — board మీద 6 నుంచి 4 అయినట్టు — తర్వాత 13, 11, 5. Run చేసి model.summary — Day 11 లో 9 parameters, ఇక్కడ 1,21,930. And దాదాపు 84%, అంటే 1,02,464, ఆ ఒక్క Dense 64 లోనే! రెండు Conv layers కలిపి 18,816 మాత్రమే — filters share అవుతాయి కదా.

💻
- Show **Block 5: Build a small CNN** code cell. Move the cursor down the layers one by one while he names them; on screen, draw an arrow from each code line to the matching box of the board pipeline.
- Run it. Zoom into `model.summary()`: Output Shape column (26, 26, 32 → 13, 13, 32 → 11, 11, 64 → 5, 5, 64 → 1600 → 64 → 10) and **Total params: 121,930**. *(run pause ~2 s)*

🖊
- Tick box 3 "Build CNN". Under the board pipeline write the real sizes: **28×28 → 26×26×32 → 13×13×32 → 11×11×64 → 5×5×64 → 1,600 → 64 → 10**.
- Card: **121,930 params · Dense(64) = 102,464 (84%) · both Conv layers = 18,816**.

### I6. Block 6: Compile + Block 7: Train
⏱ **19:38 – 20:37**

🎙
> Block 6: Compile — Day 11 లాగే. Optimizer adam — Day 10 లో పేరు చెప్పిన smarter gradient descent. Loss — sparse categorical crossentropy. పెద్ద పేరు, భయపడకండి — Day 10 log loss, 10 classes కి: −ln(correct digit కి ఇచ్చిన percentage). "Sparse" అంటే labels 7 లాంటి plain numbers, అంతే. Metric accuracy. Block 7: Train — model.fit, మన Day 10 loop. 5 epochs, batch size 128, validation split 0.1 — 6,000 images ని mock test కోసం పక్కన పెడ్తది. సో 54,000 ÷ 128 — ఒక epoch కి 422 batches, అదే 422/422 — ఈ లెక్క రాసుకోండి. Run చేస్తున్నా… Epoch 1 — accuracy దాదాపు 92.8%. Epoch 5 — 99.1%. Loss 0.25 నుంచి 0.03. Validation — నేర్చుకోని images మీద — దాదాపు 99%. Day 11 లో 100 epochs కావాల్సి వచ్చింది, ఇక్కడ 5 చాలు — ఎందుకంటే ఒక్కో epoch లోనే 422 updates అన్నమాట.

💻
- Show **Block 6: Compile**, run it (instant).
- Show **Block 7: Train**. Point at `epochs=5`, `batch_size=128`, `validation_split=0.1`. Run. **Edit: speed up / time-lapse the training wait to ~10 s on screen.** *(run pause ~10 s after time-lapse)* Point at `422/422` and the epoch lines. 🔁 Reference values: epoch 1 `accuracy: 0.9280 – loss: 0.2492 – val_accuracy: 0.9808`; epoch 5 `accuracy: 0.9912 – loss: 0.0289 – val_accuracy: 0.9895`.
- Run the plot cell ("Learning progress").

🖊
- Tick box 4 "Compile + Train". Note beside the Day 10 loop: **"fit = this loop · 5 epochs × 422 batches"**.
- Card: **54,000 ÷ 128 = 421.9 → 422 batches per epoch**.

### I7. Block 8: Test on 10,000 new images
⏱ **20:37 – 21:01**

🎙
> Block 8: Test on 10,000 new images — real exam. Model ఒక్కసారి కూడా చూడని images — coaching centre practice తర్వాత కొత్త questions లాగా. Test accuracy — 98.85%! అంటే దాదాపు 9,885 correct, 115 మాత్రమే తప్పు. రాసుకోండి: honest score test data మీదే, training data మీద కాదు. మీ number కొంచెం different రావొచ్చు — 98.6, 99.0 — normal. దాదాపు 99% వస్తే పని చేస్తున్నట్టే.

💻
- Show **Block 8: Test on 10,000 new images**, run. Zoom: 🔁 `Test accuracy: 98.85%   (test loss: 0.0352)` and `That is about 9885 correct out of 10,000.` *(run pause ~2 s)*

🖊
- Tick box 5 "Test". Big stamp: **98.85% · 9,885 / 10,000 ✔** 🔁 ✍️ **"Honest score = TEST data, not training data"**.

### I8. Block 9: Predict one image
⏱ **21:01 – 21:21**

🎙
> Block 9: Predict one image — test image 0, ఒక handwritten 7, starting లో teacher రాసిన 7 లాగా. Run… 7 వచ్చేసి — 99.999%! మిగతావి దాదాపు 0, ఒక్కటే పొడవాటి bar. Softmax percentages, total 100. Model says 7, true answer 7. idx మార్చి 9999 వరకు ఏ image అయినా try చేయండి.

💻
- Show **Block 9: Predict one image**, run with `idx = 0`. Zoom into the list: 🔁 `7:  99.999%`, all others `0.000%`, and `Model says: 7 | True answer: 7`. Show the image + bar chart. *(run pause ~2 s)*

🖊
- Tick box 6 "Predict". Sketch the bar chart: one tall bar at **7 (99.999%)**, flat everywhere else. Note: **"softmax: all 10 add to 100%"**.

### I9. Block 10: The images it got wrong
⏱ **21:21 – 22:05**

🎙
> Block 10: The images it got wrong — నాకు ఇష్టమైన block. 115 mistakes లో ఫస్ట్ 10. Image 18 — true 3, model 5 అన్నది, 44% sure. నిజం చెప్పండి, ఆ 3 మీకు కూడా 5 లాగే అనిపిస్తది కదా? Image 717 — ఒక వైపు వంగిన 0, model 5 అన్నది. ఇలాంటివి teacher కూడా కళ్ళు చిన్నవి చేసి చూస్తది. Top-2 list లో — ఈ 10 లో 9 సార్లు correct answer model కి second choice; image 18 లో 3 కి 39% ఇచ్చింది — అంటే model కి doubt ఉంది అన్నమాట. కానీ image 449 — true 3, model 5 అన్నది, 99% sure! Softmax దగ్గర చెప్పిన కదా — 99% sure అంటే correct కాదు. Confidence వేరు, correctness వేరు. గుర్తుపెట్టుకోండి.

💻
- Show **Block 10: The images it got wrong**, run the first cell: 🔁 `Wrong: 115 out of 10000 test images` and the 2 × 5 picture grid. Circle **image 18** ("True 3 | Said 5 (44% sure)") and **image 717** ("True 0 | Said 5"). *(run pause ~3 s)*
- Run the second cell (top-2 list). Highlight 🔁 `Image   18: true 3 | model: 5 44%, 3 39%` and `Image  449: true 3 | model: 5 99%, 3 1%`.

🖊
- Tick box 7 "Mistakes". Pin up three mini-cards: **#18: True 3 · Said 5 · 44% (2nd guess 3: 39%)** · **#717: True 0 · Said 5 · 56%** · **#449: True 3 · Said 5 · 99% 😮**.
- Write ✍️: **"99% sure ≠ correct. Confidence ≠ correctness."** and **"9 of 10: right answer = 2nd guess"** 🔁.

### I10. Block 11 (optional): Try it yourself + Block 12: Homework, Fashion-MNIST
⏱ **22:05 – 22:47**

🎙
> Block 11, optional: Try it yourself. (a) లో board మీద 1, 0, −1 filter ని real 7 మీద వేసినం — vertical map లో వాలు గీత, horizontal map లో పైన అడ్డ గీత వెలుగుతది. (b) లో trained model దానంతట అదే నేర్చుకున్న filters నుంచి 8 feature maps — ఎవరూ design చేయలేదు. కొన్ని edges పట్టుకుంటున్నాయి — Day 9 లో "ఫస్ట్ lines, edges", మీ కళ్ళ ముందు. Block 12: Homework, Fashion-MNIST — Block 2 లో ఒక్క line: mnist బదులు fashion_mnist, తర్వాత Run all. సో same CNN, ఇప్పుడు 10 రకాల బట్టలు, shoes. Digits కంటే ఎక్కువ వస్తదా, తక్కువా? ఏవి confuse అవుతది? మీ accuracy comments లో చెప్పండి.

💻
- Run **Block 11 (optional): Try it yourself** (a): show "Original / Vertical filter + ReLU / Horizontal filter + ReLU" for test image #0. Cursor on the top bar in the horizontal map and the slanted stroke in the vertical map. *(run pause ~2 s)*
- Run (b): the 8 learned feature maps ("filter 0 … filter 7"). Point at 2–3 that look like edge maps (say only what is visible on your screen). *(run pause ~2 s)*
- Scroll to **Block 12: Homework, Fashion-MNIST**. Show the one-line change `dataset = keras.datasets.fashion_mnist` in Block 2 (do **not** run it on camera).

🖊
- Homework card: **Block 2 → `keras.datasets.fashion_mnist` → Runtime → Run all → comment your test accuracy + the items it confuses**.

### I11. Why CNNs for images: the comparison card + one doubt
⏱ **22:47 – 23:28**

🎙
> Last card. మా team same 5 epochs తో normal Dense network కూడా train చేసింది — test లో 97.0%, దాదాపు 299 mistakes; CNN కి 115 — దాదాపు 2.6 times తక్కువ. ప్రతి digit ని 3 pixels జరిపితే — Dense 49%, CNN 88%. CNN కూడా పడింది, immune కాదు — కానీ చాలా better. Usual fix — data augmentation, అంటే training లో జరిపిన copies కూడా ఇవ్వడం — పేరు మాత్రమే. Images కి CNN ఎందుకు అంటే — అందుకే. రాసుకోండి. And మీ handwriting photo ఇస్తే చదువుతదా? Direct గా కష్టం — MNIST digits center లో, 28 by 28, black మీద white. ముందు crop, resize చేసి colours తిప్పాలి. 99% అంటే MNIST లాంటి digits మీద 99%.

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
⏱ **23:28 – 24:03**

🎙
> ఇప్పుడు ఈరోజు quiz — comments లో చెప్పండి. ఒకటి: colour photo 100 by 100 pixels — computer కి ఎన్ని numbers? రెండు: vertical filter — ప్రతి row 1, 0, −1 — ఈ patch మీద: ప్రతి row 1, 0, 0. ఏ number వస్తది? మూడు: ఈ 2 by 2 block ని max pool చేయండి — 2, 7, 0, 5. నాలుగు: trick question — ఏది deep learning image classification కాదు? (a) Google Lens flower పేరు, (b) UPI QR code scan, (c) leaf photo చూసి disease చెప్పే app. నాలుగూ ఎవరు correct చెప్తారో చూద్దాం. Fashion-MNIST accuracy కూడా మర్చిపోకండి.

🖊
- Quiz card:
  1. Colour photo, 100 × 100 pixels → how many numbers?
  2. Filter `1 0 −1` (3 rows) on patch rows `1 0 0` (3 rows) → ?
  3. Max-pool this 2 × 2 block: **2, 7, 0, 5** → ?
  4. NOT deep-learning image classification? (a) Google Lens naming a flower (b) scanning a UPI QR code (c) a leaf-disease app
  *(Answers go in production notes. Don't show them on screen.)*

---

## [K] Video recap
⏱ **24:03 – 24:25**

🎙
> And that's it for the day! ఈ video లో — computer vision: image అంటే numbers grid; CNN: filters, feature maps, ReLU, max pooling, softmax — filters ని machine ఏ నేర్చుకుంటది; and MNIST మీద మనమే classifier build చేసినం, దాదాపు 99% test accuracy. ఇవన్నీ AI లో, ML లో, deep learning లో — computer vision branch లో వస్తాయి అన్నమాట.

🖊
- Taxonomy line: **AI → ML → Deep Learning → Computer Vision → CNN → MNIST classifier (≈ 99%)**.
- Keep the CNN stack drawing on screen.

---

## [L] Outro
⏱ **24:25 – 25:06**

🎙
> Convolution ఒక్కసారికి పూర్తిగా clear కాకపోయినా టెన్షన్ పడకండి — paper మీద 6 by 6 grid గీసి ఒక్క window మీరే calculate చేయండి, click అయితది. సో notes — definitions, drawings, numbers — and Colab notebook link, రెండూ description లో ఉన్నాయి.
>
> ఈరోజు AI చూడడం నేర్చుకుంది. Next video లో — AI text ని ఎట్లా చదువుతది? ChatGPT మన sentence ని ఎట్లా అర్థం చేసుకుంటది? NLP, RNN, LSTM and Transformers — ChatGPT లో T అంటే Transformer ఏ. ఆ video కావాలంటే ఈ video ని like చేయండి.
>
> ఇంకా late ఏం అయిపోలేదు — జస్ట్ 12 videos ఏ, ఒక్క రోజు కూర్చుంటే cover చేయొచ్చు. మీ friends ని కూడా AI Learning Series లో add చేయండి.
>
> Thank you so much for watching, signing off, Tech Boy Deepak.

🖊
- The CNN stack stays on screen.
- Lower-third: **"Notes + Colab notebook in description ↓"**.
- End card: **Next: How AI Reads Text (NLP · RNN · LSTM · Transformer)** + the previous-video tile (Day 11).
