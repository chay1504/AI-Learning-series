# Video D: "How AI Sees Images" (RECORDING SCRIPT, Telugu)

**Series:** AI Learning Series, **Day 12** on the channel (Deep Learning Part 4). This covers plan Day 31 (what is computer vision?), Day 32 (what is a CNN? filters, feature maps, pooling) and Day 35 (build an image classifier: MNIST in Colab). Plan Days 33–34 (NLP; RNN vs LSTM vs Transformer) are the next part.
**Previous episodes:** Day 9 "Inside a Neural Network" · Day 10 "How a Neural Network Learns" · Day 11 "Train Your First Neural Network" (Keras, 9-knob network).
**Runtime:** @@RUNTIME@@
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
⏱ **@@A0@@**

🎙
> Exams అయిపోయినాక answer sheets correct చేస్తారు కదా. Teacher ప్రతి question పక్కన red pen తో marks రాస్తది — 7, 5, 9. ఆ handwritten 7 ని మీరు ఒక్క second లో చదివేస్తారు. కానీ ఒక computer కి? దానికి అది ఒక photo మాత్రమే — కొన్ని numbers. మరి ఆ numbers ని చూసి "ఇది 7" అని computer ఎట్లా చెప్తది? ఈరోజు మనం computer కి చదవడం నేర్పిస్తాం. Video end కి వచ్చేసరికి మీరే Colab లో ఒక model ని train చేసి, అది handwritten digits ని దాదాపు 99% correct గా చదవడం చూస్తారు. ఎవరైతే AI ని basics నుంచి, scratch నుంచి నేర్చుకోవాలి అనుకుంటున్నారో, మన channel ని subscribe చేసి పెట్టుకోండి. Let's dive into the video.

🖊
- Close-up B-roll: a red-pen "7" being written in the marks box of an answer sheet.
- Text pop: **"You see: 7 · Computer sees: numbers 🔢"**. Channel logo sting.

---

## [A] Welcome + headline promise
⏱ **@@A@@**

🎙
> Hey guys, welcome back to AI Learning Series Day 12! అప్పుడే మనం Day 12 కి వచ్చేసినం అన్నమాట. ఈరోజు video చాలా special — ఇప్పటిదాకా మనం numbers తోనే పని చేసినం. ఈరోజు ఫస్ట్ టైం images లోకి వెళ్తున్నాం. How AI sees images — అసలు AI ఒక image ని ఎట్లా చూస్తది, ఎట్లా అర్థం చేసుకుంటది. ఈరోజు ఇదే.

🖊
- Title card: **AI Learning Series · Day 12 · How AI Sees Images** *(renumber if needed)*
- Badge: **"Deep Learning · Part 4"**

---

## [B] Recap of Days 9–11 + catch-up
⏱ **@@B@@**

🎙
> సో ఫస్ట్ ఒక్కసారి recap చేసుకుందాం. Deep learning లో ఇది మన నాలుగో video. Day 9 లో neural network లోపల ఏముందో చూసినం — neuron: inputs × weights + bias, తర్వాత activation, తర్వాత output. Layers — input, hidden, output. And మన చిన్న network: study hours, sleep hours లోపలికి, రెండు hidden neurons, ఒక output. మొత్తం 9 knobs — అవే weights and biases.
>
> Day 10 లో ఆ network ఎట్లా నేర్చుకుంటదో చూసినం — ReLU, sigmoid, loss, gradient descent, backpropagation. ఆ loop గుర్తుంది కదా: forward pass → loss → backprop → update → repeat.
>
> Day 11 లో ఫస్ట్ టైం మనమే Keras లో build చేసినం. అదే 9-knob network — model.summary లో 9 parameters కనిపించినాయి కదా. Compile చేసినం, fit చేసినం — 320 training students, batch size 32, అంటే ఒక epoch కి 10 batches, 100 epochs — మొత్తం 1,000 updates. Model చూడని test students మీద evaluate చేస్తే 90% వచ్చింది. And మన Sita — Day 9 లో మనం guess చేసిన knobs తో 38% అన్నది కదా — trained network 95% pass అని correct గా చెప్పింది.
>
> లాస్ట్ వీడియో end లో ఒక question తో వదిలేసినం కదా — ఇప్పటిదాకా numbers తో పని చేసినం, మరి AI ఒక photo ని ఎట్లా చూస్తది? And Day 9 లో నేను ఒక బొమ్మ గీసిన — answer sheet photo network లోకి వెళ్తది, network దానంతట అదే features నేర్చుకుంటది: ఫస్ట్ lines, edges, తర్వాత letters, words. అప్పుడు దాన్ని ఒక black box లాగా వదిలేసినం. ఈరోజు ఆ box ని open చేస్తున్నాం.
>
> ఒకవేళ మీరు Day 9, 10, 11 చూడకుంటే ఒక్కసారి చూసి రండి. ఈరోజు ఆ మూడు videos లో ప్రతి concept మళ్ళీ వస్తది.

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
> సో ఈరోజు మనం ఏమేం discuss చేయబోతున్నాం అంటే — pen తో రాస్తున్నా చూడండి. ఫస్ట్ వచ్చేసి computer vision — computer కి ఒక image అసలు ఎట్లా కనిపిస్తది. సెకండ్ వచ్చేసి CNN — Convolutional Neural Network: filters, feature maps, pooling. ఈరోజు main topic ఇదే. థర్డ్ వచ్చేసి మనమే ఒక image classifier build చేద్దాం — Google Colab లో, handwritten digits చదివే model. Theory నేర్చుకున్న వెంటనే అది పని చేయడం మీ కళ్ళతో చూస్తారు.

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
> చాలా మంది ఏమనుకుంటారు అంటే — "ఏంటన్నా, convolution, pooling, feature maps… ఈ పేర్లే భయంగా ఉన్నాయి" అనుకుంటారు కదా. అస్సలు భయపడకండి. ఈరోజు కొత్త maths ఏం లేదు. ఒక చిన్న grid గీసి, 9 numbers ని multiply చేసి add చేస్తాం — అంతే. Class 10 student phone calculator లో check చేయొచ్చు. And ఒక secret చెప్తా — CNN లో కొత్తగా నేర్చుకునేది చాలా తక్కువ. Weights, bias, ReLU, loss, backprop — అన్నీ మీకు ఆల్రెడీ తెలుసు. విన్నాక మీరే అంటారు "ఇంతేనా అన్నా, ఇది hard అనుకున్నాం" అని.
>
> Google Lens అయినా, X-ray చూసి doctors కి help చేసే AI అయినా — images తో పని చేసే చాలా AI tools ఈ ideas మీదే build అయినాయి. సో చాలా important. అందరూ notes రాసుకోండి.

🖊
- Sticky note: **"New today: only how the neurons are connected. Everything else you already know ✔"**

---

## [F] CONCEPT 1: Computer vision

### F1. Announce + definition + name unpack
⏱ **@@F1@@**

🎙
> సో ఫస్ట్ topic — computer vision. Definition screen మీద చూపిస్తున్నా, రాసుకోండి.
>
> *"Computer vision is the field of AI that enables computers to get useful information from images and videos: what is in them, where it is, or what it says."*
>
> అంటే ఏంటిది? పేర్లోనే ఉంది కదా — computer కి vision, అంటే చూపు. మనకి కళ్ళు ఉన్నాయి — చూస్తాం, అర్థం చేసుకుంటాం. Computer కి camera ఉంటది. కానీ camera photo తీయడం వేరు, ఆ photo లో ఏముందో అర్థం చేసుకోవడం వేరు. ఆ అర్థం చేసుకునే part నే computer vision అంటాం అన్నమాట.
>
> Definition లో మూడు phrases చూడండి. "What is in them" — photo లో ఏముంది, cat ఆ dog ఆ. "Where it is" — అది photo లో ఎక్కడ ఉంది. "What it says" — దాంట్లో ఏం రాసి ఉంది. ఈ మూడు గుర్తుపెట్టుకోండి, కాసేపట్లో మళ్ళీ వస్తాయి.

🖊
1. Definition card (English). ✍️ "Write it down".
2. Split the name: **COMPUTER + VISION (చూపు)**. Doodle: camera 📷 → "takes the photo" vs 🧠 → "understands the photo" = computer vision.
3. Underline the three phrases: **what · where · what it says**.

### F2. An image is a grid of numbers (drawing first)
⏱ **@@F2@@**

🎙
> ఇప్పుడు ఈ topic లో అన్నిటికంటే important point. ఒక question — computer కి ఒక photo ఎట్లా కనిపిస్తది? మనకి కనిపించినట్టే కనిపిస్తదా? No. Computer కి photo అంటే కేవలం numbers — ఒక numbers table అన్నమాట.
>
> Board మీద చూడండి. ఒక చిన్న 6 by 6 grid గీస్తున్నా — 36 చిన్న squares. మన school లో maths graph book ఉంటది కదా, అలాంటిది. ఇప్పుడు దాంట్లో ఒక "1" రాస్తా — కొన్ని squares ని నింపుతున్నా: పైన ఒక చిన్న flag, మధ్యలో నిలువు గీత, కింద base. ఈ ఒక్కో చిన్న square ని pixel అంటాం — picture element.
>
> ఇప్పుడు computer దీన్ని ఎట్లా store చేస్తది? ప్రతి pixel కి ఒక number. Black అంటే 0, full white అంటే 255. మధ్యలో ఉండేవి grey shades. ఈరోజు మనం వాడే digits dataset లో black background మీద white ink ఉంటది. సో ink ఉన్న చోట 255, ఖాళీ చోట 0. ఇదిగో — left side మనకి కనిపించేది, right side computer కి కనిపించేది. Same image, రెండు రూపాలు. Definition రాసుకోండి:
>
> *"A digital image is a grid of tiny squares called pixels. In a grayscale image, each pixel is one number from 0 (black) to 255 (white)."*
>
> Graph book లో squares నింపితే బొమ్మ వస్తది కదా — image కూడా అంతే. చిన్న చిన్న squares, ప్రతి square ఒక number. Real photos లో ఆ squares లక్షల్లో, కోట్లలో ఉంటాయి, అంతే తేడా.

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
> మరి colour photo అయితే? ప్రతి pixel కి మూడు numbers — Red, Green, Blue. దీన్నే RGB అంటాం. మీ phone screen ని magnifying glass తో చూస్తే, ప్రతి pixel లో మూడు చిన్న lights ఉంటాయి — ఒక red, ఒక green, ఒక blue. ఏ light ఎంత bright గా వెలుగుతది అనే దాన్ని బట్టి colour వస్తది. Red 255, green 0, blue 0 — pure red. మూడూ 255 — white. మూడూ 0 — black. రాసుకోండి: grayscale అంటే pixel కి ఒక number, colour అంటే pixel కి మూడు numbers. ఈ మూడింటిని channels అంటారు.
>
> ఇప్పుడు size చూడండి. మన చిన్న grid — 6 × 6 = 36 numbers. ఈరోజు build లో వాడే dataset లో ఒక్కో image 28 × 28 — అంటే 784 numbers. Day 9 లో phone photo లెక్క చేసినం గుర్తుందా? 12 megapixel అంటే దాదాపు 1.2 కోట్ల pixels, into 3 colours — దాదాపు 3.6 కోట్ల numbers! ఒక్క photo కి.

🖊
1. One pixel blown up into three boxes: **R | G | B = 255 | 0 | 0 → red**. Below: **255 | 255 | 255 → white · 0 | 0 | 0 → black**.
2. Write: **Grayscale = 1 number per pixel · Colour = 3 numbers per pixel (3 channels)**. ✍️
3. Size ladder: **6 × 6 = 36 → 28 × 28 = 784 → 12 MP photo × 3 ≈ 3.6 crore numbers**.

### F4. Three vision tasks + where we see them + "not always deep learning"
⏱ **@@F4@@**

🎙
> సో computer vision లో ముఖ్యంగా మూడు రకాల పనులు ఉంటాయి. Definition లో మూడు phrases చెప్పిన కదా — అవే.
>
> ఫస్ట్ వన్ వచ్చేసి image classification — మొత్తం image కి ఒక్క label. "ఈ digit 7", "ఈ leaf కి disease ఉంది". Day 6 లో చూసినం కదా — category ని predict చేసేదే classification. Images కి కూడా అదే. And digits అంటే 0 నుంచి 9 — 10 categories. అంటే Day 6 లో చూసిన multi-class classification అన్నమాట.
>
> సెకండ్ వన్ వచ్చేసి object detection — image లో ప్రతి object ని కనిపెట్టి, దాని చుట్టూ ఒక box గీస్తది. Traffic camera photo లో car ఎక్కడ ఉంది, number plate ఎక్కడ ఉంది అని box వేసి చూపిస్తది.
>
> థర్డ్ వన్ వచ్చేసి segmentation — ప్రతి ఒక్క pixel కి label. ఈ pixels road, ఈ pixels మనిషి, ఈ pixels sky. ఈరోజు మనం చేసేది ఫస్ట్ ది — classification.
>
> మనం రోజూ చూసేవి చూద్దాం. Google Lens — ఒక flower మీద camera పెడితే దాని పేరు చెప్తది. Hyderabad లో traffic cameras number plates చదువుతాయి — కానీ challan పంపే ముందు police verify చేస్తారు. Farmers కోసం apps ఉన్నాయి — leaf photo తీస్తే ఏ pest, ఏ disease అని చెప్తాయి. Hospitals లో X-ray చూసి TB chance ఉందని flag చేసే AI — Day 9 లో చెప్పుకున్నం కదా.
>
> కానీ ఇక్కడ కన్ఫ్యూజ్ అవ్వద్దు — computer vision అంటే ఎప్పుడూ deep learning కాదు. మీరు UPI pay చేసేటప్పుడు QR code scan చేస్తారు కదా — అది కూడా camera, image ఏ. కానీ QR code చదవడానికి fixed rules ఉంటాయి, ఒక fixed method ఉంటది. దానికి model ని train చేయాల్సిన అవసరం లేదు. మరి deep learning ఎక్కడ కావాలి? Rules రాయలేనంత variety ఉన్నప్పుడు. Handwriting — ప్రతి ఒక్కరిది different గా ఉంటది కదా. Faces, leaves, X-rays — అక్కడ deep learning.

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
> ఇప్పుడు మీకు ఒక doubt రావాలి — "అన్నా, image అంటే numbers ఏ కదా. Day 11 లో numbers ఇచ్చి Dense network ని train చేసినం కదా. అదే network కి ఈ 784 numbers ఇస్తే సరిపోతది కదా?" Good question. ఇస్తే పని చేస్తది, కానీ మూడు problems ఉన్నాయి. మూడు fingers చూపిస్తా, రాసుకోండి.
>
> ఫస్ట్ finger — weights చాలా ఎక్కువ. Dense అంటే fully connected — ప్రతి input ప్రతి neuron కి connect అయి ఉంటది, Day 9 లో చూసినం. 784 pixels, 128 neurons అనుకుందాం. 784 × 128 weights, ప్లస్ 128 biases — 1,00,480 parameters! Day 11 network కి 9 parameters, ఇక్కడ ఒక్క layer కే లక్ష. And 12 megapixel colour photo అయితే, ఒక్క layer కే దాదాపు 460 కోట్ల weights. Impossible కదా.
>
> సెకండ్ finger — "పక్కపక్కన ఉండడం" అనే విషయం పోతది. Dense లోకి ఇవ్వాలి అంటే ముందు ఈ grid ని ఒక్క పొడవాటి line లాగా పరచాలి — దీన్నే flatten అంటాం. Row 1, తర్వాత row 2, తర్వాత row 3. ఇప్పుడు చూడండి — grid లో ఈ pixel, సరిగ్గా దాని కింద ఉండే pixel — ఒకే గీత మీద పక్కపక్కనే ఉన్నాయి. కానీ line లో? 28 places దూరం అయిపోయినాయి. Dense network కి "ఈ రెండు neighbours" అని ముందే తెలియదు. కానీ images లో meaning అంతా neighbours లోనే ఉంటది — ఒక గీత అంటే పక్కపక్కన ఉండే pixels కలిసి ఒకే వైపు వెళ్ళడమే కదా.
>
> థర్డ్ finger — digit కొంచెం జరిగితే. అదే 7 ని 3 pixels right కి జరిపి రాస్తే, మనకి అది same 7. కానీ Dense network కి దాదాపు ఒక కొత్త pattern — numbers అన్నీ వేరే positions లోకి వెళ్ళిపోయినాయి కదా. మా team test చేసింది: normal test digits మీద 97% correct చెప్పిన Dense network, ప్రతి digit ని 3 pixels జరిపితే 49% కి పడిపోయింది. సగం కంటే ఎక్కువ తప్పు!
>
> సో ఈ మూడు problems కి answer ఏంటి? అదే మన next topic.

🖊
Draw three fingers ✋ and write one problem per finger (✍️):
1. **Too many weights:** 784 × 128 + 128 = **1,00,480** in layer 1 (vs Day 11's 9!). 12 MP colour photo → **≈ 460 crore**.
2. **Loses "nearby-ness":** 28 × 28 square → arrow "Flatten" → one long line of dots. Circle two pixels one above the other in the grid; in the line, draw them **28 dots apart**.
3. **Shifted digit = new pattern:** a "7", and the same "7" moved 3 squares right. Caption: **"Dense: 97% → 49% when shifted 3 pixels"**.

### F6. Doubt + one-line recap
⏱ **@@F6@@**

🎙
> ఇంకో చిన్న doubt — "అన్నా, face unlock కూడా image classification ఏ కదా?" Strictly చెప్పాలి అంటే కాదు. అది verification — "ఈ face, ముందు register చేసిన face ఒకటేనా కాదా" అని check చేస్తది. Neural networks వాడుతారు, కానీ పని వేరు. 0 నుంచి 9 లో ఏదో ఒక category లోకి వేయడం కాదు.
>
> సింపుల్ — computer కి image అంటే numbers grid. ఆ numbers లో patterns కనిపెట్టి, image లో ఏముందో, ఎక్కడ ఉందో, ఏం రాసి ఉందో అర్థం చేసుకునేదే computer vision.

🖊
- Small chip: **Face unlock = verification ("same person?"), not classification**.
- Recap card: **Computer vision = finding patterns in a grid of numbers → what / where / what it says.**

---

## [H] CONCEPT 2: CNN (Convolutional Neural Network)

### H1. Announce + definition + name unpack
⏱ **@@H1@@**

🎙
> సో computer vision అయిపోయింది. ఇప్పుడు ఈరోజు main concept — CNN. Full form — Convolutional Neural Network. Definition రాసుకోండి.
>
> *"A Convolutional Neural Network (CNN) is a neural network designed for grid-like data such as images. Instead of connecting every pixel to every neuron, it slides small learnable filters across the image to detect local patterns, and stacks layers to combine them into bigger shapes and objects."*
>
> అంటే ఏంటిది? పేరులో రెండు parts. "Neural network" — ఇది మనకి తెలుసు. అవే neurons, అవే weights, అవే layers. "Convolutional" — ఇదే కొత్త word. Convolution అంటే సింపుల్ గా — ఒక చిన్న window ని image మీద జరుపుకుంటూ, slide చేసుకుంటూ, ప్రతి చోట ఒక చిన్న calculation చేయడం. అంతే.
>
> Definition లో మూడు keywords. "Small learnable filters" — చిన్న filters, అవి నేర్చుకుంటాయి. "Local patterns" — ఒక చిన్న area లో ఉండే patterns — ఒక గీత, ఒక మూల. "Stacks layers" — ఒక దాని మీద ఒక layer పెట్టి, చిన్న patterns ని కలిపి పెద్ద shapes తయారు చేయడం.

🖊
1. Definition card (English). ✍️
2. Split the name: **CONVOLUTIONAL = slide a small window + calculate at every spot** | **NEURAL NETWORK = same neurons, weights, layers ✔**.
3. Underline: **small learnable filters · local patterns · stacks layers**.

### H2. Filter = the teacher's 3 × 3 window (and it is our old neuron)
⏱ **@@H2@@**

🎙
> ఇప్పుడు filter అంటే ఏంటి? Definition రాసుకోండి:
>
> *"A filter (also called a kernel) is a small grid of weights, usually 3 × 3. It looks at one small patch of the image at a time, multiplies each pixel by its weight, adds them up (plus a bias) and gives one number. Then it slides to the next position."*
>
> ఒక example చెప్తా. ఒక teacher దగ్గర ఒక చిన్న cardboard ఉంది అనుకోండి — మధ్యలో 3 by 3 size లో ఒక చిన్న కిటికీ కట్ చేసి ఉంది. ఆ teacher answer sheet మీద ఆ window ని పెట్టి ఒకే ఒక్క విషయం వెతుకుతది — "ఇక్కడ tick mark ఉందా?" అని. Top-left నుంచి start చేసి, కొంచెం కొంచెం జరుపుకుంటూ మొత్తం page చూస్తది. ప్రతి position కి ఒక score వేరే paper మీద రాసుకుంటది — ఇక్కడ tick బాగా ఉంది, 3. ఇక్కడ లేదు, 0. ఆ score sheet నే feature map అంటాం. ఇంకో teacher వేరే window తో "cross mark ఉందా" అని వెతుకుతది — అది ఇంకో filter.
>
> And ఒక secret — ఈ filter ఏం చేస్తది? 9 pixels × 9 weights, అన్నీ add చేసి, bias add చేస్తది. ఇది ఎక్కడో చూసినం కదా? Day 9 neuron! Inputs × weights + bias. Filter అంటే మన పాత neuron ఏ — ఒక చిన్న window గుండా చూస్తది అంతే.
>
> కానీ దీన్నే exact example అనుకోకండి. Teacher కి tick mark ఎట్లా ఉంటదో ముందే తెలుసు. CNN filter కి ముందు ఏం తెలియదు — random numbers తో start అవుతది, data నుంచి నేర్చుకుంటది. ఇది కాసేపట్లో మళ్ళీ చెప్తా, చాలా important.

🖊
1. Definition card (English). ✍️
2. Doodle: an answer sheet, a cardboard with a **3 × 3 window cut out**, arrows showing it sliding left → right, row by row. A separate "score sheet" grid beside it labelled **"feature map"**.
3. Second teacher with a different window: **"another filter → another pattern"**.
4. Write: **Filter = our Day 9 neuron looking through a small window (9 inputs × 9 weights + 1 bias)**.
5. Chip: **"Teacher knows the pattern; a CNN filter LEARNS it."**

### [G] Mid-roll CTA
⏱ **@@G@@**

🎙
> వీడియో మధ్యలో interrupt చేస్తున్నందుకు sorry. ఒక్క second ఈ video ని pause చేసి like చేయండి. And three dots క్లిక్ చేసి hype చేయండి — hype చేస్తే ఈ video మీలాంటి ఇంకా చాలా మంది beginners కి reach అవుతది. ఈ series చూసేవాళ్ళలో చాలా మంది ఇంకా subscribe చేయలేదు. ఈరోజు video కోసం మా team ఈ Colab notebook ని ముందే run చేసి test చేసింది, మీకు ఏ error రాకుండా. మీ ఒక్క like, ఒక్క subscribe మా team కి అదే energy ఇస్తది. సో ప్లీజ్ support చేయండి. సో మళ్ళీ మన filter దగ్గరికి వద్దాం.

🖊
- Like / three-dots → **Hype** / Subscribe animation. Keep the filter definition card visible underneath so the cut back is seamless.

> **Note:** his usual stat is "90% of viewers are not subscribed". Only say a number if YouTube Studio supports it on the day of recording; otherwise keep the generic line above.

### H3. The worked convolution: one window, then the whole feature map (the one worked example)
⏱ **@@H3@@**

🎙
> Maths గురించి ఏం టెన్షన్ పడకండి — multiply and add మాత్రమే. స్లో స్లోగా చూద్దాం.
>
> మన "1" grid తీసుకుందాం. ఈసారి simple గా ఉండడానికి 255 ని 1 అని రాస్తున్నా — ink ఉంటే 1, లేకుంటే 0. అంటే 255 తో divide చేసినం అన్నమాట. Build లో కూడా ఇదే చేస్తాం.
>
> ఇప్పుడు ఒక filter — నేనే ఒకటి choose చేస్తున్నా: ప్రతి row లో 1, 0, −1. మూడు rows. దీని meaning ఏంటి అంటే — "left side bright, right side dark" ఉంటే పెద్ద number ఇస్తది. అంటే ఒక నిలువు గీత యొక్క right edge ని పట్టుకుంటది. దీన్ని vertical edge filter అంటారు.
>
> Step 1 — ఈ red 3 by 3 square ని grid top-left corner లో పెడుతున్నా. లోపల 9 pixels: ఫస్ట్ row 0 0 1, సెకండ్ row 0 1 1, థర్డ్ row 0 0 1. ఇప్పుడు ప్రతి pixel ని filter లో అదే position లో ఉండే number తో multiply చేయాలి. Left column లో filter 1 — pixels 0, 0, 0 — అన్నీ 0. Middle column లో filter 0 — ఏది multiply చేసినా 0. Right column లో filter −1 — pixels 1, 1, 1 — వచ్చేసి −1, −1, −1. అన్నీ add చేస్తే — −3. ఈ −3 ని feature map లో ఫస్ట్ box లో రాస్తున్నా.
>
> Step 2 — window ని ఒక్క pixel right కి జరుపుతున్నా. ఇప్పుడు patch: 0 1 0, 1 1 0, 0 1 0. Left column 0, 1, 0 — into 1 — మొత్తం 1. Middle — 0. Right column అంతా 0. Total — 1.
>
> Step 3 — ఇంకొక్క pixel right. Patch: 1 0 0, 1 0 0, 1 0 0. Left column 1, 1, 1 — into 1 — 3. మిగతావి 0. Total — 3! ఇది పెద్ద number. ఎందుకు? ఇక్కడ సరిగ్గా మన "1" యొక్క నిలువు గీత left side లో ఉంది, right side ఖాళీ. Filter వెతికే pattern exact గా ఇదే — perfect match.
>
> ఇట్లా మొత్తం grid మీద జరుపుకుంటూ వెళ్తే — 6 by 6 image మీద 3 by 3 window — ఒక row లో 4 positions, అట్లా 4 rows — 4 by 4 feature map వస్తది. Full map screen మీద చూపిస్తున్నా. చూడండి — మూడో column అంతా 3, 3, 3, 3. ఆ map ఏం చెప్తది అంటే "ఇక్కడ పై నుంచి కింది దాకా ఒక నిలువు edge ఉంది" అని. And ఫస్ట్ column అంతా −3 — అది opposite edge, గీత యొక్క left side, dark నుంచి bright. దాన్ని పట్టుకోవాలి అంటే వేరే, flip చేసిన filter కావాలి. Feature map definition రాసుకోండి:
>
> *"A feature map is the grid of numbers a filter produces as it slides over the image. Big values show where the filter's pattern was found."*
>
> సింపుల్ గా — feature map అంటే ఒక heat map. Filter యొక్క pattern image లో ఎక్కడెక్కడ ఉందో చూపించే map అన్నమాట. నేను ఫస్ట్ టైం CNN చదివినప్పుడు feature map అంటే ఏంటో అస్సలు అర్థం కాలేదు. ఇట్లనే paper మీద ఒక చిన్న grid గీసి, చేతితో calculate చేసినప్పుడు అప్పుడు click అయింది. మీ దగ్గర calculator ఉంటే మిగతా boxes మీరే check చేయండి.

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
> నెక్స్ట్ step — ఈ map మీద ReLU. Day 10 లో చూసినం కదా: negative అయితే 0, positive అయితే అదే number. సో −3 లు అన్నీ 0 అయిపోతాయి. Negative అంటే "ఇక్కడ ఈ pattern లేదు" — దాన్ని 0 చేసేసినం. Sita ది h2 neuron OFF అయింది కదా — same ReLU.
>
> ఇప్పుడు pooling. Definition రాసుకోండి:
>
> *"Max pooling shrinks a feature map by keeping only the largest value in each small block, usually 2 × 2. It keeps the strongest signal and makes the network a little less sensitive to small shifts."*
>
> ఈ 4 by 4 map ని నాలుగు 2 by 2 blocks గా విడదీస్తున్నా — thick lines గీసి. ప్రతి block లో biggest number ఒక్కటే ఉంచుకుంటాం. Top-left block: 0, 1, 0, 1 — biggest 1. Top-right: 3, 0, 3, 0 — 3. Bottom-left: అన్నీ 0 — 0. Bottom-right: 3, 0, 3, 1 — 3. సో 16 numbers నుంచి 4 numbers: 1, 3, 0, 3.
>
> ఒక example — మీ report card లో ఒక subject కి నాలుగు unit tests ఉన్నాయి. Principal "నాకు నాలుగు marks అక్కర్లేదు, best mark ఒక్కటి చెప్పు" అన్నారు అనుకోండి. Max pooling కూడా అంతే — ప్రతి block నుంచి best ఒక్కటే. చూడండి — map నాలుగో వంతు అయిపోయింది, కానీ message పోలేదు: "right side లో strong నిలువు గీత ఉంది" — అది ఇంకా ఆ 3, 3 లో కనిపిస్తది.
>
> ఇక్కడ కన్ఫ్యూజ్ అవ్వద్దు — max pooling అంటే maximum, average కాదు. Average తీసుకునే pooling కూడా ఉంది, కానీ మనం ఈరోజు వాడేది max.
>
> Pooling ఎందుకు? రెండు reasons. ఒకటి — size తగ్గుతది, calculations తగ్గుతాయి. రెండు — గీత ఒక్క pixel అటు ఇటు జరిగినా, ఆ 2 by 2 block లో max చాలాసార్లు మారదు కదా. సో కొంచెం జరిగినా పెద్దగా పట్టించుకోదు.

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
> ఇప్పుడు ఇంకో interesting విషయం. ఇదే filter ని పక్కకి తిప్పితే — ఫస్ట్ row 1 1 1, మధ్యలో 0 0 0, కింద −1 −1 −1 — ఇది horizontal edge filter, అడ్డ గీతల్ని పట్టుకుంటది. Result screen మీద చూపిస్తున్నా. మన "1" మీద ఇది వేస్తే — pool చేసినాక దాదాపు అంతా 0: 1, 0, 0, 0. ఎందుకంటే "1" లో అడ్డ గీతలు దాదాపు లేవు. అదే ఒక "7" మీద వేస్తే — map ఫస్ట్ row వచ్చేసి 3, 2, 2, 1. అది 7 పైన ఉండే అడ్డ గీత! సో "1" vertical detector ని వెలిగిస్తది, "7" పైన horizontal detector ని వెలిగిస్తది. ఇలాంటి detectors ని కలిపితే digits ని వేరు చేయొచ్చు కదా.
>
> ఇప్పుడు చాలా చాలా important point, రాసుకోండి: real CNN లో filters ని ఎవరూ design చేయరు. ఈరోజు board మీద నేను 1, 0, −1 choose చేసిన — Day 7 లో w = 0.8 అని assume చేసినట్టు, మీకు చూపించడానికి మాత్రమే. Real CNN లో ప్రతి filter random numbers తో start అవుతది. Training లో backprop వాటిని కూడా మిగతా weights లాగే మారుస్తది. ఏ patterns వెతకాలో network ఏ నేర్చుకుంటది. Day 9 లో "network features ని దానంతట అదే నేర్చుకుంటది" అన్నాం కదా — దాని అర్థం ఇదే.
>
> And ఇంకో magic. ఒక filter లో ఎన్ని numbers? 9 weights + 1 bias = 10. ఆ same 10 numbers ని image లో ప్రతి position లో వాడుతది. ఎందుకంటే నిలువు గీత top-left లో ఉన్నా, bottom-right లో ఉన్నా — నిలువు గీత నిలువు గీత ఏ కదా. ఒక rubber stamp ని page మొత్తం వాడినట్టు — అదే stamp. దీన్నే parameter sharing అంటారు. మన build లో ఫస్ట్ layer కి 32 filters — 32 × 10 = 320 parameters. అదే Dense లో 784 pixels నుంచి 32 neurons కే 25,120. తేడా చూసినారా? ఫస్ట్ finger problem solve.
>
> సెకండ్ finger — neighbours? Filter ఎప్పుడూ పక్కపక్కన ఉండే 3 by 3 pixels నే కలిపి చూస్తది. Grid ని line చేయదు. Solve. థర్డ్ finger — జరిగిన digit? Same filter ప్రతి చోటా వెతుకుతది కాబట్టి, గీత ఎక్కడ ఉన్నా దొరుకుతది. Pooling ఇంకొంచెం help చేస్తది.

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
> సో ఇప్పుడు మొత్తం CNN ఒక్క picture లో. ఈ video లో ఇది most important drawing — రాసుకోండి.
>
> Image → Conv + ReLU → Pool → Conv + ReLU → Pool → Flatten → Dense → Softmax → answer.
>
> ఒక factory line లాగా చదవండి. ఫస్ట్ Conv layer — చాలా filters, చిన్న చిన్న edges, గీతలు పట్టుకుంటాయి. Pool — size తగ్గిస్తది. సెకండ్ Conv layer — ఫస్ట్ layer feature maps మీద పని చేస్తది, అంటే edges ని కలిపి పెద్ద shapes — మూలలు, loops, 7 పైన ఉండే అడ్డ గీత లాంటివి. మళ్ళీ Pool. తర్వాత Flatten — ఇప్పుడు line లాగా పరిచినా problem లేదు, ఎందుకంటే ముఖ్యమైన features ఆల్రెడీ బయటకి వచ్చినాయి. తర్వాత Dense — మన Day 9 normal network — "పైన loop ఉంది, right side నిలువు గీత ఉంది — ఇది 9" అని final decision తీసుకుంటది.
>
> Edges → shapes → which digit. Day 9 లో దూరం నుంచి ఒక relative నడుచుకుంటూ వస్తుంటే అనే example చెప్పిన కదా — simple నుంచి complex. Same idea. కానీ ఒక్క తేడా — మనం దూరం నుంచి ఫస్ట్ outline చూస్తాం, CNN ఫస్ట్ చిన్న edges చూస్తది. "Simple features కలిసి complex features" అనే idea కి మాత్రమే ఈ example. And real filters మన labels అంత neat గా ఉండవు — చాలాసార్లు "ఇది loop detector" అని పేరు పెట్టలేం.

🖊
- Big pipeline across the bottom of the board (keep it there for the build):
  **Image → [Conv + ReLU] → [Pool] → [Conv + ReLU] → [Pool] → Flatten → Dense → Softmax → "7"**
- Under the stages write: **"edges" → "shapes / parts" → "which digit?"** ✍️
- Chip: **"Analogy: simple → complex only. CNN sees small edges first. Real filters rarely have neat names."**

### H7. Softmax: percentages that add to 100
⏱ **@@H7@@**

🎙
> Last box — softmax. Day 10 లో పేరు మాత్రమే చెప్పిన, ఇప్పుడు చూద్దాం. Definition రాసుకోండి:
>
> *"Softmax turns the output layer's raw scores into probabilities that are all positive and add up to 100%. The biggest score gets the biggest share."*
>
> Last layer లో 10 neurons ఉంటాయి — 0 నుంచి 9, ఒక్కో digit కి ఒక్కటి. ప్రతి neuron ఒక score ఇస్తది — ఏ number అయినా కావచ్చు. Simple గా మూడు digits తీసుకుందాం: "1" కి score 3, "7" కి 1.5, "4" కి 0.5. Softmax రెండు steps చేస్తది. ఒకటి — ప్రతి score ని e power తో positive చేస్తది — Day 7 sigmoid లో వచ్చిన అదే e, 2.718. రెండు — అన్నిటినీ total తో divide చేస్తది, అప్పుడు అన్నీ కలిపి 100 అవుతాయి. Result: "1" వచ్చేసి 76.6%, "7" వచ్చేసి 17.1%, "4" వచ్చేసి 6.3%. Add చేయండి — 100%. Formula corner లో ఉంది — machine ఏ చేస్తది. Interest ఉంటే calculator లో e^x button తో check చేయండి.
>
> And ఒక beautiful connection. రెండే classes ఉంటే? Pass, fail. Student D కి scores 2.4 and 0 ఇస్తే softmax ఏమిస్తది? 91.7% and 8.3%. Day 7 sigmoid లో exact గా 91.7% వచ్చింది కదా! సో sigmoid అంటే రెండు classes softmax అన్నమాట.
>
> ఇక్కడ కన్ఫ్యూజ్ అవ్వద్దు — softmax ఒక answer ని pick చేయదు, percentages ఇస్తది. Biggest ఏదో దాన్ని answer గా తీసుకోవడం ఒక separate last step — sigmoid తర్వాత 50% threshold లాగా. And 99% అంటే "model 99% sure" అని అర్థం, "ఎప్పుడూ correct" అని కాదు. ఇది build లో మనకి real గా కనిపిస్తది.

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
> ఇప్పుడు మీకు doubt — "అన్నా, CNN ఎట్లా train అవుతది? అది వేరే కొత్త method ఆ?" కాదు! Day 10 loop గుర్తుంది కదా — forward pass, loss, backprop, gradient descent update, repeat. Exact గా అదే. Loss కూడా అదే log loss — −ln(correct digit కి ఇచ్చిన percentage). True digit "1" అయితే — model 76.6% ఇచ్చింది కదా — loss 0.27. తప్పు కాదు, కానీ ఇంకా improve అవ్వొచ్చు. Backprop ఆ error ని వెనక్కి పంపి, Dense weights కే కాదు — filters లో ఉండే 9 numbers కి కూడా blame ఇస్తది. Gradient descent వాటిని కొంచెం మారుస్తది. సో CNN లో కొత్త learning ఏం లేదు. Weights, bias, ReLU, softmax, loss, backprop, epochs — అన్నీ మనకి తెలిసినవే. కొత్తది ఒక్కటే — neurons ఎట్లా connect అయి ఉంటాయి.
>
> ఇంకో doubt — "CNN కి digit ఎక్కడ ఉన్నా పర్వాలేదా?" పూర్తిగా కాదు. Dense కంటే చాలా better, కానీ immune కాదు. Build తర్వాత real numbers చూపిస్తా.
>
> సింపుల్ — చిన్న filters ని image మీద slide చేసి patterns కనిపెట్టి, pooling తో shrink చేసి, layer by layer కలిపి, last లో softmax తో percentages ఇచ్చేదే CNN. అంతే సింపుల్.

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
> సో theory అయిపోయింది. ఇప్పుడు నాకు చాలా ఇష్టమైన part — build. మనమే ఒక image classifier తయారు చేద్దాం. Notebook link description లో ఉంది — open చేసి నాతో పాటు run చేయండి. Line by line code లోకి వెళ్ళను. ప్రతి block ఏం చేస్తదో concept లో చెప్తా — board మీద గీసినవి code లో ఎక్కడ ఉన్నాయో చూపిస్తా.
>
> Dataset పేరు MNIST. Handwritten digits, 0 నుంచి 9 — 70,000 చిన్న photos. 60,000 training కి, 10,000 testing కి. Computer vision లో ఇది "hello world" లాంటిది — చాలా మంది ఫస్ట్ project ఇదే చేస్తారు. Answer sheet మీద handwritten marks చదవడం, postal cover మీద PIN code చదవడం — వాటికి ఇది ఒక simple version అన్నమాట.
>
> Colab లో Runtime → Change runtime type. Normal CPU సరిపోతది, training కి కొన్ని నిమిషాలు పట్టొచ్చు. T4 GPU select చేస్తే ఇంకా fast.

💻
- Screen-share Colab with `part-4-build-an-image-classifier.ipynb` open at the title cell. Cursor on the "plan, block by block" list.
- Show **Runtime → Change runtime type** menu for 2 seconds.

🖊
- Lower-third: **"Notebook link in description ↓"**. Name card: **MNIST: 60,000 training + 10,000 test images · 28 × 28 · digits 0–9**.
- Put the 7-box flow on the side of the board (tick each as it runs): **Load & look → ÷255 → Build CNN → Compile + Train → Test → Predict → Mistakes**.

### I2. Block 1: Setup + Block 2: Load the dataset
⏱ **@@I2@@**

🎙
> Block 1: Setup — tools load చేస్తున్నాం: numbers కోసం NumPy, బొమ్మల కోసం Matplotlib, deep learning కోసం Keras — Day 11 లో వాడిన అదే Keras. Seed fix చేస్తున్నాం — random starting weights ప్రతిసారి same గా రావడానికి. Run.
>
> Block 2: Load the dataset — MNIST Keras లోనే built-in గా ఉంది. Run చేస్తే — training images: 60,000, 28, 28. అంటే 60,000 images, ప్రతిది 28 by 28. Test images 10,000. And labels — ప్రతి image కి correct answer, మన answer key. ముందు వీడియోస్ లో చూసిన supervised learning ఏ — features అంటే pixels, label అంటే digit.

💻
- Run **Block 1: Setup** (prints the TensorFlow / Keras versions). *(run pause ~3 s)*
- Run **Block 2: Load the dataset**. Highlight `Training images: (60000, 28, 28)`, `Test images: (10000, 28, 28)` and `First 10 labels: [5 0 4 1 9 2 1 3 1 4]`. *(run pause ~3 s; first run downloads the data, so run it once before recording)*

🖊
- Tick box 1 "Load & look". Write **features = pixels · label = digit (answer key)**.

### I3. Block 3: An image is just a grid of numbers
⏱ **@@I3@@**

🎙
> Block 3 — "An image is just a grid of numbers". ఫస్ట్ training image ని numbers లాగా print చేస్తున్నాం. Screen చూడండి… ఒక్క second pause చేసి చూడండి — background అంతా 0 లు, మధ్యలో 253, 255 లాంటి పెద్ద numbers. ఆ పెద్ద numbers ని కళ్ళతో follow చేస్తే… ఒక 5 కనిపిస్తది కదా! Label కూడా 5. Board మీద మనం 6 by 6 గీసినం — ఇది అదే, 28 by 28. కింద బొమ్మల్లాగా 18 images, వాటి labels తో.

💻
- Run the first cell of **Block 3**. Zoom into the printed 28 × 28 grid; trace the 5 with the cursor. Show `Label: 5`. *(run pause ~2 s)*
- Run the second cell: the 3 × 6 grid of digit pictures with labels.

🖊
- Point from the screen to the board's 6 × 6 "1": **"same idea, 28 × 28 = 784 numbers"**.

### I4. Block 4: Prepare the data
⏱ **@@I4@@**

🎙
> Block 4: Prepare the data — రెండు చిన్న పనులు. ఒకటి — ప్రతి pixel ని 255 తో divide చేస్తున్నాం, అప్పుడు అన్నీ 0 నుంచి 1 మధ్యలో వస్తాయి. Board మీద 255 ని 1 అని రాసినం కదా — అదే. చిన్న, ఒకే size numbers ఉంటే learning smooth గా ఉంటది. రెండు — ఒక channel add చేస్తున్నాం. Grayscale కాబట్టి 1 channel. Colour అయితే 3 — R, G, B. Output చూడండి: 60,000, 28, 28, 1 — min 0, max 1.

💻
- Run **Block 4: Prepare the data**. Highlight `New shape: (60000, 28, 28, 1) | min: 0.0 | max: 1.0`. *(run pause ~2 s)*

🖊
- Tick box 2 "÷255". Point to the board's "÷ 255 → 0/1" grid.

### I5. Block 5: Build a small CNN
⏱ **@@I5@@**

🎙
> Block 5: Build a small CNN — ఈ block = మనం board మీద గీసిన CNN stack! పై నుంచి కిందకి చదవండి. Conv2D, 32, 3 by 3 — 32 filters, ఒక్కొక్కటి 3 by 3. Board మీద గీసిన filter layer ఇదే, కానీ ఇక్కడ 32 filters, అన్నీ random తో start. Activation relu — feature map మీద ReLU. MaxPooling2D 2 by 2 — మన pooling. మళ్ళీ Conv2D 64, మళ్ళీ MaxPooling. Flatten. Dense 64 — మన Day 9 normal layer. Last లో Dense 10, softmax — 10 digits, 10 percentages.
>
> Comments లో sizes కూడా రాసినం — 28 నుంచి 26, pool తర్వాత 13, మళ్ళీ 11, pool 5. Board మీద 6 by 6 కి 3 by 3 వేస్తే 4 by 4 వచ్చింది కదా — 2 తగ్గింది. ఇక్కడ కూడా 28 నుంచి 26. Same.
>
> Run చేసి model.summary చూడండి. Day 11 లో 9 parameters చూసినం గుర్తుందా? ఇక్కడ 1,21,930. Interesting విషయం — దాంట్లో దాదాపు 84% ఆ ఒక్క Dense 64 layer లోనే ఉన్నాయి — 1,02,464. రెండు Conv layers కలిపి 18,816 మాత్రమే. Filters share అవుతాయి కదా — అందుకే.

💻
- Show **Block 5: Build a small CNN** code cell. Move the cursor down the layers one by one while he names them; on screen, draw an arrow from each code line to the matching box of the board pipeline.
- Run it. Zoom into `model.summary()`: Output Shape column (26, 26, 32 → 13, 13, 32 → 11, 11, 64 → 5, 5, 64 → 1600 → 64 → 10) and **Total params: 121,930**. *(run pause ~2 s)*

🖊
- Tick box 3 "Build CNN". Under the board pipeline write the real sizes: **28×28 → 26×26×32 → 13×13×32 → 11×11×64 → 5×5×64 → 1,600 → 64 → 10**.
- Card: **121,930 params · Dense(64) = 102,464 (84%) · both Conv layers = 18,816**.

### I6. Block 6: Compile + Block 7: Train
⏱ **@@I6@@**

🎙
> Block 6: Compile — Day 11 లో చేసినట్టే. Optimizer adam — Video B లో పేరు చెప్పిన smarter gradient descent. Loss — sparse categorical crossentropy. పేరు పెద్దగా ఉంది, భయపడకండి — అదే Day 10 log loss, 10 classes కి: −ln(correct digit కి ఇచ్చిన percentage). "Sparse" అంటే labels 7 లాంటి plain numbers అని అంతే. Metrics accuracy — train చేసేది loss మీద, report చేసేది accuracy.
>
> Block 7: Train — model.fit. Day 10 loop ఇక్కడే run అవుతది. Epochs 5 — మొత్తం training images ని 5 సార్లు చూస్తది. Batch size 128 — 128 images చూసి ఒక update. Validation split 0.1 — అంటే 6,000 images ని పక్కన పెట్టి, ప్రతి epoch తర్వాత ఒక mock test. సో 54,000 images మీద train — 54,000 ÷ 128 — ఒక epoch కి 422 batches. Screen మీద 422/422 కనిపిస్తది. Run చేస్తున్నా…
>
> చూడండి — epoch 1 తర్వాత accuracy దాదాపు 92.8%. Epoch 2 — 97.9. Epoch 5 కి వచ్చేసరికి 99.1%. Loss 0.25 నుంచి 0.03 కి తగ్గింది. Validation accuracy — model నేర్చుకోని ఆ 6,000 images మీద — దాదాపు 99%. Graph లో epoch by epoch పైకి వెళ్తది చూడండి. Day 11 లో 100 epochs పట్టినాయి, ఇక్కడ 5 చాలు — ఎందుకంటే ఇక్కడ 54,000 examples ఉన్నాయి, ఒక్కో epoch లో 422 updates.

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
> Block 8: Test on 10,000 new images — ఇప్పుడు real exam. ఈ 10,000 images ని model ఒక్కసారి కూడా చూడలేదు. Coaching centre లో 60,000 practice questions చేసినాక, final exam లో 10,000 కొత్త questions లాగా. Run… Test accuracy — 98.85%! అంటే 10,000 లో దాదాపు 9,885 correct. 115 మాత్రమే తప్పు. 5 epochs, ఒక చిన్న notebook — handwritten digits ని 98.85%!
>
> రాసుకోండి: honest score ఎప్పుడూ test data మీదే — training data మీద కాదు. మీ screen మీద number కొంచెం different రావొచ్చు — 98.6, 99.0 — అది normal, computer ని బట్టి కొంచెం మారుతది. దాదాపు 99% వస్తే మీ model correct గా పని చేస్తున్నట్టే.

💻
- Show **Block 8: Test on 10,000 new images**, run. Zoom: 🔁 `Test accuracy: 98.85%   (test loss: 0.0352)` and `That is about 9885 correct out of 10,000.` *(run pause ~2 s)*

🖊
- Tick box 5 "Test". Big stamp: **98.85% · 9,885 / 10,000 ✔** 🔁 ✍️ **"Honest score = TEST data, not training data"**.

### I8. Block 9: Predict one image
⏱ **@@I8@@**

🎙
> Block 9: Predict one image — ఇప్పుడు ఒక్క image ఇద్దాం. Test image number 0 — ఇది ఒక handwritten 7. Starting లో teacher రాసిన 7 గుర్తుందా? Run… 10 percentages వచ్చినాయి. 7 వచ్చేసి — 99.999%! మిగతా అన్నీ దాదాపు 0. Bar chart లో ఒక్కటే పొడవాటి bar — 7 దగ్గర. ఇవి softmax percentages — అన్నీ add చేస్తే 100. Model says 7, true answer 7. మీరు idx మార్చి వేరే images try చేయండి — 1, 2, 3 — 9999 వరకు ఏదైనా.

💻
- Show **Block 9: Predict one image**, run with `idx = 0`. Zoom into the list: 🔁 `7:  99.999%`, all others `0.000%`, and `Model says: 7 | True answer: 7`. Show the image + bar chart. *(run pause ~2 s)*

🖊
- Tick box 6 "Predict". Sketch the bar chart: one tall bar at **7 (99.999%)**, flat everywhere else. Note: **"softmax: all 10 add to 100%"**.

### I9. Block 10: The images it got wrong
⏱ **@@I9@@**

🎙
> Block 10: The images it got wrong — నాకు అన్నిటికంటే ఇష్టమైన block. Model తప్పు చెప్పిన 115 లో ఫస్ట్ 10 చూద్దాం. Run… చూడండి. Image 18 — true answer 3, model 5 అన్నది, 44% sure. నిజం చెప్పండి — ఆ 3 చూస్తే మీకు కూడా 5 లాగే అనిపిస్తది కదా? Image 717 — ఒక 0, కానీ ఒక వైపు వంగిపోయిన loop — model 5 అన్నది, 56%. ఇలాంటి handwriting ని teacher కూడా కళ్ళు చిన్నవి చేసి చూస్తది.
>
> కింద ఉండే list లో top 2 guesses ఉన్నాయి — ఈ 10 లో 9 సార్లు correct answer model కి second choice! Image 18 లో 3 కి 39% ఇచ్చింది. అంటే model కి doubt ఉంది, correct కి దగ్గరగానే ఉంది.
>
> కానీ ఇది చూడండి — image 449. True 3, model 5 అన్నది — 99% sure! Softmax దగ్గర చెప్పిన కదా — 99% sure అంటే correct అని కాదు. Confidence వేరు, correctness వేరు. గుర్తుపెట్టుకోండి.

💻
- Show **Block 10: The images it got wrong**, run the first cell: 🔁 `Wrong: 115 out of 10000 test images` and the 2 × 5 picture grid. Circle **image 18** ("True 3 | Said 5 (44% sure)") and **image 717** ("True 0 | Said 5"). *(run pause ~3 s)*
- Run the second cell (top-2 list). Highlight 🔁 `Image   18: true 3 | model: 5 44%, 3 39%` and `Image  449: true 3 | model: 5 99%, 3 1%`.

🖊
- Tick box 7 "Mistakes". Pin up three mini-cards: **#18: True 3 · Said 5 · 44% (2nd guess 3: 39%)** · **#717: True 0 · Said 5 · 56%** · **#449: True 3 · Said 5 · 99% 😮**.
- Write ✍️: **"99% sure ≠ correct. Confidence ≠ correctness."** and **"9 of 10: right answer = 2nd guess"** 🔁.

### I10. Block 11 (optional): Try it yourself + Block 12: Homework, Fashion-MNIST
⏱ **@@I10@@**

🎙
> Block 11 optional — Try it yourself. (a) లో board మీద గీసిన అదే 1, 0, −1 filter ని ఒక real 7 మీద వేసినం. Vertical map లో 7 యొక్క వాలు గీత వెలుగుతది, horizontal map లో 7 పైన ఉండే అడ్డ గీత వెలుగుతది — board మీద చూసిందే. (b) లో real trained CNN ఫస్ట్ layer లో ఉండే 32 filters లో 8 feature maps. ఇవి model దానంతట అదే నేర్చుకున్న filters — ఎవరూ design చేయలేదు. కొన్ని edges పట్టుకుంటున్నాయి, కొన్ని వేరే patterns. Day 9 లో "ఫస్ట్ lines, edges" అన్నాం కదా — ఇదిగో మీ కళ్ళ ముందు.
>
> Block 12: Homework, Fashion-MNIST — Block 2 లో ఒక్క line మార్చండి: mnist బదులు fashion_mnist. Runtime → Run all. Same code, same CNN — ఇప్పుడు digits కాదు, 10 రకాల బట్టలు, shoes — T-shirt, trouser, sneaker, bag. Accuracy digits కంటే ఎక్కువ వస్తదా, తక్కువ వస్తదా? ఏ items ని ఎక్కువ confuse అవుతది? Comments లో మీ accuracy చెప్పండి.

💻
- Run **Block 11 (optional): Try it yourself** (a): show "Original / Vertical filter + ReLU / Horizontal filter + ReLU" for test image #0. Cursor on the top bar in the horizontal map and the slanted stroke in the vertical map. *(run pause ~2 s)*
- Run (b): the 8 learned feature maps ("filter 0 … filter 7"). Point at 2–3 that look like edge maps (say only what is visible on your screen). *(run pause ~2 s)*
- Scroll to **Block 12: Homework, Fashion-MNIST**. Show the one-line change `dataset = keras.datasets.fashion_mnist` in Block 2 (do **not** run it on camera).

🖊
- Homework card: **Block 2 → `keras.datasets.fashion_mnist` → Runtime → Run all → comment your test accuracy + the items it confuses**.

### I11. Why CNNs for images: the comparison card + one doubt
⏱ **@@I11@@**

🎙
> Last ఒక్క card. మా team same 5 epochs తో ఒక normal Dense network కూడా train చేసింది — Flatten, Dense 128, Dense 10. Test లో 97.0%. మన CNN — 98.85%. చిన్న తేడా అనిపిస్తదా? Dense కి దాదాపు 299 mistakes, CNN కి 115 — దాదాపు 2.6 times తక్కువ mistakes. And ప్రతి digit ని 3 pixels జరిపితే — Dense 49%, CNN 88%. CNN కూడా పడిపోయింది, immune కాదు — ముందే చెప్పిన కదా — కానీ చాలా better. దీనికి fix ఏంటి అంటే — training లో జరిపిన, తిప్పిన copies కూడా ఇవ్వడం. దీన్ని data augmentation అంటారు — పేరు మాత్రమే. Images కి CNN ఎందుకు వాడుతారు అంటే — అందుకే. రాసుకోండి.
>
> ఒక doubt — "అన్నా, నా handwriting photo తీసి ఇస్తే చదువుతదా?" Direct గా ఇస్తే కష్టం. MNIST లో digits center లో ఉంటాయి, 28 by 28, black background మీద white ink. మీ photo ని కూడా అలాగే crop చేసి, resize చేసి, colours ని తిప్పి ఇవ్వాలి. లేకుంటే accuracy చాలా పడిపోవచ్చు. 99% అంటే "MNIST లాంటి digits మీద 99%" అని అర్థం.

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
> ఇప్పుడు ఈరోజు quiz — comments లో చెప్పండి. ఒకటి: ఒక colour photo 100 by 100 pixels. Computer కి ఎన్ని numbers కనిపిస్తాయి? రెండు: vertical filter — ప్రతి row 1, 0, −1 — ఈ patch మీద వేస్తే: ప్రతి row 1, 0, 0. ఏ number వస్తది? మూడు: ఈ 2 by 2 block ని max pool చేయండి — 2, 7, 0, 5. నాలుగు: trick question — వీటిలో ఏది deep learning image classification కాదు? (a) Google Lens flower పేరు చెప్పడం, (b) UPI QR code scan చేయడం, (c) leaf photo చూసి disease చెప్పే app. ఎవరు నాలుగూ correct చెప్తారో చూద్దాం. And Fashion-MNIST accuracy కూడా మర్చిపోకండి.

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
> And that's it for the day! ఈ video లో మనం — computer vision: image అంటే numbers grid, grayscale కి ఒక number, colour కి మూడు. CNN: filters, feature maps, ReLU, max pooling, softmax — and filters ని machine ఏ నేర్చుకుంటది. And మనమే MNIST మీద ఒక image classifier build చేసినం — దాదాపు 99% test accuracy. ఇవన్నీ AI లో, machine learning లో, deep learning లో — computer vision అనే branch లో వస్తాయి అన్నమాట.

🖊
- Taxonomy line: **AI → ML → Deep Learning → Computer Vision → CNN → MNIST classifier (≈ 99%)**.
- Keep the CNN stack drawing on screen.

---

## [L] Outro
⏱ **@@L@@**

🎙
> ఒక్కసారి చూస్తే convolution పూర్తిగా clear కాకపోయినా టెన్షన్ పడకండి. ఒక paper తీసుకొని 6 by 6 grid గీసి, ఒక్క window మీరే calculate చేయండి — click అయితది.
>
> Notes అన్నీ — definitions, board drawings, numbers — description లో పెడుతున్నా. And Colab notebook link కూడా description లో ఉంది. Run చేయండి, homework చేయండి.
>
> ఈరోజు AI images ని చూడడం నేర్చుకుంది. Next video లో — AI text ని ఎట్లా చదువుతది? ChatGPT మన sentence ని ఎట్లా అర్థం చేసుకుంటది? NLP, RNN, LSTM and Transformers — ChatGPT లో T అంటే Transformer ఏ. How AI reads text. ఎవరికైతే ఆ video కావాలో ఈ video ని like చేయండి.
>
> And ఇంకా late ఏం అయిపోలేదు — జస్ట్ 12 videos ఏ అయినాయి. ఒక్క రోజు కూర్చుంటే అన్నీ cover చేయొచ్చు. మీ friends ని కూడా ఈ AI Learning Series లో add చేయండి. మీ support ఎంత ఎక్కువ ఉంటే అంత మంచి videos మీకు తీసుకొస్తాం.
>
> Thank you so much for watching, signing off, Tech Boy Deepak.

🖊
- The CNN stack stays on screen.
- Lower-third: **"Notes + Colab notebook in description ↓"**.
- End card: **Next: How AI Reads Text (NLP · RNN · LSTM · Transformer)** + the previous-video tile (Day 11).
