# DNA Part 02: Voice, Language Mix, Analogies (Tech Boy Deepak, AI Learning Series)

**Sources:** Telugu auto-captions (the main evidence) and the English auto-translation (used to check meaning) for:
- **D6**: Day 6, *Classification vs Regression* (~16 min, ~2,750 Telugu-track words)
- **D7**: Day 7, *Decision Tree / Logistic Regression / SVM* (~25 min, ~4,060 words)
- **D8**: Day 8, *K-Means / Hierarchical / DBSCAN* (~23 min, ~3,560 words)

Timestamps such as `D7 [05:10]` point to the caption block the quote sits in. The captions come from ASR, so spellings like మిషన్/మెషీన్/మషన్ are recogniser variants of one word he says the same way each time ("machine"). This file does not cover video structure or pacing; another part does.

---

## 0. TL;DR: the voice in 10 lines

1. **The grammar is Telugu and the content words are English.** Every technical noun, and many ordinary words like *simple, clear, important, different, example, process, step, notes, doubt, confuse*, stay in English. Telugu supplies the verbs, case endings and discourse particles.
2. **His Telugu is Telangana / Hyderabad colloquial.** He uses `-తది` endings (చేస్తది, ఉంటది, అవుతది) about **146 times against 26** for standard `-తుంది`. He also says చూసినం/చేసినాం, చదివిండు/చెప్పిండు, వచ్చినాయి, ఎట్లా, తోని, ఆగం, ఎమ్మటే, మూలకు, పక్కా.
3. **Three particles carry the delivery:** **సో** (≈217), **అంటే** (≈208) and **అన్నమాట** (≈170). Together they come to roughly 9 per minute.
4. **వచ్చేసి works as a copula or list marker** (≈80): "ఫస్ట్ వన్ వచ్చేసి…", "z వాల్యూ వచ్చేసి 2.4".
5. **Every concept follows the same loop:** "X అంటే ఏంటి?" → "రాసుకోండి", then the English definition is read aloud, then "అంటే…" in Telugu, then "ఇంకా సింపుల్ గా చెప్పాలి అంటే…", then an example, then "దీన్నే X అంటాం అన్నమాట", then "సింపుల్".
6. **His examples come from student life and Indian money:** exams, pass/fail, marks, the 36-mark pass line, hours of study and sleep, attendance, spam email, buying a house in lakhs and square yards, rupee spending, the prices of earphones/mouse/keyboard, fruits, pets, twins.
7. **He reuses one anchor example across videos.** The student pass/fail model shows up in D6, D7 and D8 and grows a little each time.
8. **His tone is a big brother's.** He reassures constantly ("అస్సలు భయపడకండి", "కన్ఫ్యూజ్ అవ్వద్దు", "టెన్షన్ పడకండి"), admits it took him 2–3 days himself, and corrects slips on camera without fuss.
9. **Viewers call him "అన్న".** He never calls them that. He addresses them as గాయ్స్ (opener only), మీరు, మీ అందరికీ, ప్రతి ఒక్కళ్ళు, బిగినర్స్, మన వాళ్ళు.
10. **He limits depth openly.** He says "we won't go into maths yet", explains why ("ఆగం అవుతారు"), and points to later videos. When he does do maths, it is a single worked number example.

---

## 1. Language mix (code-switching)

### 1.1 What stays English and what stays Telugu

| Layer | Stays **English** | Stays **Telugu** |
|---|---|---|
| Technical nouns | model, data, dataset, algorithm, prediction, output, input, category, label, feature, accuracy, formula, residual, error, cluster, centroid, hyperplane, kernel, threshold, probability, weights, bias, node, branch, outlier | n/a. He almost never translates a technical term into Telugu |
| General nouns and adjectives | example, difference, process, concept, topic, step, point, notes, screen, video, doubt, clarity, basic(s), simple, clear, important, different, interesting, engaging, proper, direct, automatic | ఇల్లు (house), బొమ్మ (picture: "డెసిషన్ ట్రీ బొమ్మ"), పేరు, దూరం, దగ్గర, మూల, ఇంట్లో, మార్గం-type everyday words |
| Numbers and ordinals | ఫస్ట్/సెకండ్/థర్డ్, టూ/త్రీ/సిక్స్, "సిక్స్ అవర్స్", "90%", "65 లాక్స్" | ఒకటి/రెండు/మూడు also appear, mostly in "ఈ రెండు", "ఈ మూడిటిని" |
| Connectors and fillers | **సో**, అండ్, బట్, ఆర్, ఫర్ ఎగ్జాంపుల్, ఓకే, యా, ఎస్, ఐ మీన్, ఆబ్వియస్లీ, సారీ, బికాజ్ (rare) | **అంటే**, **అన్నమాట**, **కదా**, అసలు, ఇందాక, మళ్ళీ, కాకుంటే, లేకుంటే, ఎందుకంటే, కాబట్టి, కూడా, అంతే |
| Verbs | **English stem + Telugu light verb**: ప్రిడిక్ట్ చేస్తది, ఎక్స్ప్లెయిన్ చేస్తా, ట్రైన్ చేసినాం, సపరేట్ చేస్తది, డిసైడ్ చేస్తాం, అస్యూమ్ చేసుకున్నాం, క్యాలిక్యులేట్ చేయాలి, మెజర్ చేసి, పుల్ చేసింది. Intransitive verbs take అవ్వు: ఫామ్ అయినాయి, ట్రైన్ అయిపోయింది, కన్ఫ్యూజ్ అవ్వద్దు, స్ప్లిట్ అయింది, రీచ్ అవుతది, బిలాంగ్ అయి ఉంటాయి | Native Telugu verbs for basic actions: నేర్చుకుంటది, ఆలోచిస్తది, చెప్తాం, అడుగుతూ, గీస్తది (draws), చదివిండు, పడుకున్నాడు, కొందాం, ఆడుకుంటుంది, కలిసినాయి, విడదీయి |
| Case and postpositions | n/a | These attach directly to English nouns: మోడల్ **కి**, డేటా**ని**, క్లస్టర్ **లోకి**, కేటగిరీ **కిందకి వస్తది** (≈20, "falls under"), అవుట్పుట్ **లాగా** (≈59, "as/like"), సెంట్రాయిడ్ **కి దగ్గరలో** (≈59) |

Counts across the three Telugu tracks: the `చేయ్` light verb (చేస్త-/చేసి/చేయ-) appears ≈400 times and the `అవ్వు` light verb ≈116 times. This "English verb + చేయ్/అవ్వు" pattern is the backbone of his sentences.

**Rough ratio.** I hand-tagged a sample of sentences (for example D6 [02:36] "సో ఎప్పుడైతే లేబుల్డ్ డేటాని మనం మోడల్ కి ఇస్తామో… ఈ ప్రాసెస్ నే సూపర్వైజడ్ లెర్నింగ్ అంటాం"). About **30–45% of tokens are English-origin**, and in definition-heavy stretches that rises to 60%+, because he reads the English definitions out whole.

### 1.2 Sentence patterns (the templates he repeats)

| Pattern | Gloss | Example |
|---|---|---|
| **X అంటే ఏంటి(ది)?** → **అంటే …** | "What is X? Meaning…" (≈28 "అంటే ఏంటి") | "అసలు కేటగిరీ అంటే ఏంటిది అంటే అంటే దేనికి చెందుతుంది అని అర్థం" D6 [05:09] |
| **X ఏం చేస్తది అంటే …** | "What X does is…" (≈22 with ఏం జరుగుతది/ఏమైతది) | "ఆ మోడల్ ఏం చేస్తది అంటే వెదర్ ఆ ఈమెయిల్ స్పామా కాదా అని ప్రిడిక్ట్ చేస్తది అన్నమాట" D6 [02:36] |
| **…చేసేదే X** (nominaliser -ఏదే/-డమే) | "The thing that does … is X" (≈12) | "ఒక క్యాటగిరీని ప్రిడిక్ట్ చేసేదే క్లాసిఫికేషన్" D6 [03:52] |
| **దీన్నే / ఈ … నే X అంటాం (అన్నమాట)** | "This itself is what we call X" (అంటాం/పిలుస్తాం ≈34) | "ఈ ప్రిడిక్షన్ ఎర్రర్ నే మనం రెసిడ్యువల్ అని కూడా పిలుస్తామ అన్నమాట" D6 [11:07] |
| **N వచ్చేసి X** | "N is X", used for enumerating and stating values (≈80) | "ఫస్ట్ వచ్చేసి డెసిషన్ ట్రీ ఆల్గరిథం… సెకండ్ వన్ వచ్చేసి లాజిస్టిక్ రిగ్రెషన్" D7 [00:00] |
| **ఇంకా సింపుల్ గా చెప్పాలి అంటే** | "To put it even more simply" | D6 [03:52], [06:25]; D7 [09:26] |
| **పేర్లోనే ఉంది కదా** | "It's right there in the name" | binary → two (D6 [03:52]), tree → branches (D7 [02:34]), K → number (D8 [03:54]) |
| **ఫర్ ఎగ్జాంపుల్ … అనుకుందాం / అనుకోండి** | "For example, suppose…" (అనుకుందాం 12, అనుకోండి 15) | "ఫర్ ఎగ్జాంపుల్ మీరు ఒక ఇల్లు కొందాం అనుకున్నారు" D6 [07:15] |
| **Question to the audience, then he answers** | rhetorical | "ప్రైస్ ని ప్రిడిక్ట్ చేయొచ్చా చేయరాదా? మీరేమనుకుంటున్నారు? ఎస్…" D6 [07:15] |
| **…కదా** tag | "…right?" (≈46) | "మన ట్రీస్ కి ఏముంటాయి బ్రాంచెస్ ఉంటాయి కదా" D7 [02:34] |

### 1.3 Dialect markers: Telangana colloquial against standard (counted)

| Feature | Telangana / colloquial form (count) | Standard form (count) | Example |
|---|---|---|---|
| 3sg non-masc present/future | **-తది / -టది**: చేస్తది, ఉంటది, అవుతది, వస్తది, ఆలోచిస్తది (**146**) | -తుంది / -టుంది (26) | "మెషీన్ ఎలా ఆలోచిస్తది ఎలా నేర్చుకుంటది" D6 [00:00] |
| 1pl past | **-ఇనాం / -ఇనం / -ఇం**: చేసినాం (6), చూసినాం (5), చూసినం (3), చేసినం, గీసినాం, వచ్చేసినామ, యూస్ చేసిం (**29**) | చేశాం / చూశాం (rare) | "అప్పుడే మనం డేఎయిట్ కి వచ్చేసినామ అన్నమాట" D8 [00:00] |
| 3sg masc past | **-ఇండు**: చదివిండు (5), చెప్పిండు, ఇచ్చిండు, చేసిండు, పెట్టిండు, and the question form అయిండా (**17**) | -ఆడు (5) | "లెస్ దెన్ టూ అవర్స్ చదివిండు కాబట్టి ఫెయిల్" D7 [06:27] |
| 3pl non-human past | **-ఇనాయి**: వచ్చినాయి, అయినాయి, కలిసినాయి, పెరిగినాయి (16, mostly D8) | వచ్చాయి/అయ్యాయి (0) | "సెంట్రాయిడ్ వాల్యూస్ పెరిగినాయి అన్నమాట" D8 [09:08] |
| 1sg past (dropped -ఆను) | చెప్పిన, పెట్టిన, గీసిన, చూపించిన, ఇచ్చిన (~29) | చెప్పాను | "నేను ఇందాకనే చెప్పిన" D7 [07:26] |
| "how" | **ఎట్లా** (18) | ఎలా (28). Both appear and he switches freely | "స్పామ్ ఈమెయిల్స్ ఎట్లా ఉంటాయి" D6 [03:52] |
| "with" | **తోని** (5) | తో | "డెసిషన్ త్రెషోల్డ్ తోని కంపేర్ చేసుకొని" D7 [11:59] |
| "what" | **ఏంది / ఏందో** (4), **ఏంటిది** (23) | ఏమిటి (0) | "డెఫినిషన్ ఏందో చూద్దాం రాసుకోండి" D6 [01:19] |
| "not doing" | **-ట్లేదు / -ట్లే**, **-తలేదు** | -డం లేదు | "ఈ పెన్ తో హ్యాండ్ రైటింగ్ ప్రాపర్ గా వస్తలేదు" D7 [00:00] |
| "or / otherwise" | **లేకుంటే / కాకుంటే** (-కుంటే ≈72) | లేకపోతే / కానీ | "కాకుంటే కొంచెం డిఫరెన్స్ లో ప్రెడిక్ట్ చేస్తది" D6 [07:15] |
| Slang | **ఆగం అవుతారు** (get flustered), **ఎమ్మటే** (straight away), **మూలకు** (in a corner), **పక్కా**, **మంచిగా** | n/a | "కొంచెం ఆగం అవుతారు అన్నమాట" D6 [11:07] |

**Rule for imitators:** use `-తది` as the default verb ending, with the occasional `-తుంది` (about 1 in 6). Use `-ఇనాం/-ఇనం` for "we did" and `-ఇండు` for "he did". **Do not overdo the slang words**: ఆగం, ఎమ్మటే and మూలకు each appear only once in about 64 minutes of video.

### 1.4 How the transcripts render English (important for script writers)

- ASR writes **every English word in Telugu script, phonetically**: క్లాసిఫికేషన్, రిగ్రెషన్, సూపర్వైజడ్ లెర్నింగ్, ప్రాబబిలిటీ, సిగ్మాయిడ్ ఫంక్షన్, హైపర్ ప్లేన్, సెంట్రాయిడ్.
- Variant spellings are ASR noise, not pronunciation changes. machine → మిషన్ / మెషిన్ / మెషీన్ / మషన్ / మిషిన్; example → ఎగ్జాంపుల్ / ఎగజాంపుల్; definition → డెఫినిషన్ / డెఫినేషన్; calculate → క్లిక్యులేట్ / క్ాలిక్యులేట్; hierarchical → హైరారికల్ / హైరాకల్; epsilon → ఎప్సిన్; dendrogram → డెంోగ్రామ్; lakhs → లాక్స్; σ(z) → సిగమాజ; calculator → క్ల్సీ.
- A few tokens leak into Latin script: `ml`, `YouTube`, `z`, `w1`, `x2`, `C1`, `k`, `d`.
- Particles fuse onto the word before them: చేయట్లేదుఅన్నమాట, ఉందన్నమాట, అంటామ అన్నమాట (అంటాం + అన్నమాట), ఉంటదిన్నమాట, అవుట్పుట్ే.
- `[సంగీతం]` marks a music or SFX sting, not speech.
- **Recommendation for new scripts:** write Telugu grammar in Telugu script and English terms in **Latin script** (e.g. "ఈ model ఏం చేస్తది అంటే…"). That reads naturally as a teleprompter and matches what he puts on screen, where the definitions are English text. If a script must be all-Telugu-script (for TTS, say), transliterate the English the way the ASR does (మోడల్, డేటా, అల్గారిథం).

### 1.5 Thirty real example sentences (Telugu, gloss, timestamp)

| # | Day [time] | Telugu (as captioned) | English gloss |
|---|---|---|---|
| 1 | D6 [00:00] | హే గాయస్ వెల్కమ్ టు ఏఐ లెర్నింగ్ సిరీస్ విత్ టెక్ బాయ్ దీపక్ | Hey guys, welcome to the AI Learning Series with Tech Boy Deepak |
| 2 | D6 [00:00] | అసలు మెషీన్ ఎలా ఆలోచిస్తది ఎలా నేర్చుకుంటది ట్రైనింగ్ అంటే ఏంటిది టెస్టింగ్ అంటే ఏంటిది… ఇవన్నీ టాపిక్స్ కవర్ చేసినాం | How a machine actually thinks, how it learns, what training is, what testing is… we covered all these topics |
| 3 | D6 [00:00] | ఒక స్టూడెంట్ ఎగ్జామ్ లో పాస్ అయిండా ఫెయిల్ అయిండా అనే ఒక మోడల్ ని బిల్డ్ చేసినమ అన్నమాట | We built a model that tells whether a student passed or failed the exam, you see |
| 4 | D6 [01:19] | ప్రతి ఒక్కళ్ళ నోట్స్ ని రాసుకోండి బేసిక్ బేసిక్ ఎగ్జాంపుల్స్ తో ప్రతి ఒక్కరికి అర్థమయ్యేలాగా క్లియర్ గా ఎక్స్ప్లెయిన్ చేస్తా | Everyone write notes. I'll explain clearly with very basic examples so everyone understands |
| 5 | D6 [01:19] | ఎప్పుడైతే మెషన్ లెర్నింగ్ మోడల్ ఒక క్యేటగిరీని ప్రెడిక్ట్ చేస్తదో… అప్పుడు దాన్ని క్లాసిఫికేషన్ అంటామ అన్నమాట | Whenever an ML model predicts a category… that is what we call classification |
| 6 | D6 [02:36] | సింపుల్ గా చెప్పాలంటే మన మోడల్ కి ఆన్సర్ కూడా లీక్ చేస్తామ అన్నమాట | Put simply, we basically leak the answer to our model |
| 7 | D6 [03:52] | బైనరీ క్లాసిఫికేషన్ పేర్లోనే ఉంది కదా బైనరీ అంటే టూ | Binary classification: it's in the name, binary means two |
| 8 | D6 [05:09] | మీరు కన్ఫ్యూజ్ అవ్వద్దు మల్టీ క్లాస్ కి మల్టీ లేబుల్ కి | Don't get confused between multi-class and multi-label |
| 9 | D6 [05:09] | ఒక డాగ్ ఇండోర్ అంటే ఇంట్లో ఆడుకుంటుంది ఒక డాగ్ అవుట్డోర్ లో ఆడుకుంటుంది అన్నమాట | One dog plays indoors, meaning inside the house, another plays outdoors |
| 10 | D6 [05:09] | సో బిగినర్స్ అందరూ టెక్నికల్ టర్మ్స్ ని గుర్తుపెట్టుకోవాల్సిన అవసరం లేదు సింపుల్ గా గుర్తుపెట్టుకోండి | Beginners, you don't need to memorise the technical terms; just remember it simply |
| 11 | D6 [06:25] | మీలాంటి బిగినర్స్ చాలా మంది ఏమంటున్నారంటే మీరు చాలా బాగా ఎక్స్ప్లెయిన్ చేస్తారు అన్న అంటున్నారు | Lots of beginners like you are saying "you explain really well, anna" |
| 12 | D6 [07:15] | ఫర్ ఎగ్జాంపుల్ మీరు ఒక ఇల్లు కొందాం అనుకున్నారు. కానీ దాని ప్రైస్ మీకు తెలియదు | For example, you want to buy a house, but you don't know its price |
| 13 | D6 [07:15] | ప్రైస్ ని ప్రిడిక్ట్ చేయొచ్చా చేయరాదా? మీరేమనుకుంటున్నారు? ఎస్ | Can we predict the price or not? What do you think? Yes |
| 14 | D6 [08:32] | ఒక్క మాటలో చెప్పాలి అంటే న్యూమరికల్ వాల్యూ ని అవుట్పుట్ లాగా తీసుకొస్తే అదే రిగ్రెషన్ | In one word: if it brings out a numerical value as output, that's regression |
| 15 | D6 [08:32] | ఆ జీరో వన్ అది క్లాసిఫికేషన్ లో వచ్చేది అది రిగ్రెషన్ కిందకి రాదు ఇక్కడ కన్ఫ్యూజ్ అవ్వద్దు | That 0/1 belongs to classification, it doesn't fall under regression. Don't get confused here |
| 16 | D6 [09:49] | 100 100 క్యాన్సల్ అయిపోతాయి 90 అనేది వెలుగుతది | The 100s cancel out and 90 is what's left (lit. "90 shines through") |
| 17 | D6 [09:49] | ఎట్ ద సేమ్ టైం మీరు అనుకున్నంత ఈజీ కూడా కాదు | At the same time, it's not as easy as you think either |
| 18 | D6 [11:07] | ఇప్పుడే మాథ్స్ చెప్పడం స్టార్ట్ చేస్తే కొంచెం కన్ఫ్యూజ్ అయితారు కొంచెం ఆగం అవుతారు అన్నమాట | If I start on the maths now you'll get a bit confused, a bit flustered |
| 19 | D6 [15:48] | ఇంకా లేట్ ఏమ అయిపోలేదు జస్ట్ సిక్స్ వీడియోస్ అయిపోయినాయి | It's not late yet, only six videos are done |
| 20 | D7 [00:00] | ఈ పెన్ తో హ్యాండ్ రైటింగ్ ప్రాపర్ గా వస్తలేదు దాన్ని ఇగ్నోర్ చేయండి | The handwriting isn't coming out right with this pen, ignore that |
| 21 | D7 [00:00] | చాలా మంది ఏంటన్నా ఈ టెర్మినాలజీ కొంచెం హార్డ్ అనిపిస్తుంది మేమేమో బిగినర్స్ మాకు అర్థం కాదు అనుకుంటారు కదా అస్సలు భయపడకండి | Many think "what is this anna, the terminology feels hard, we're beginners, we won't get it". Don't be scared at all |
| 22 | D7 [00:00] | మీరు విన్నాక మీరే అంటారు చాలా ఈజీ గా ఉందన్న మేము దీన్ని హార్డ్ అనుకున్నాం కదా అంటారు | After listening you yourselves will say "it's so easy anna, and we thought it was hard" |
| 23 | D7 [01:17] | ఒకవేళ చూడకుంటే లాస్ట్ వీడియో చూడండి మర్చిపోతూ ఉండరు అందుకే మళ్ళీ రివైజ్ చేయాలి | If you haven't, watch the last video. You'll forget, so we must revise |
| 24 | D7 [02:34] | జనరల్ గా ఇప్పుడు మన ట్రీస్ కి ఏముంటాయి బ్రాంచెస్ ఉంటాయి కదా | Generally, what do our trees have? Branches, right? |
| 25 | D7 [02:34] | నువ్వు ఎగ్జామ్ కి ప్రిపేర్ అయినావా లేదా ఒకవేళ ప్రిపేర్ అయితే ఎన్ని హవర్స్ ప్రిపేర్ అయినావ్ | Did you prepare for the exam or not? If you did, how many hours? (he speaks directly to the "student") |
| 26 | D7 [06:27] | లెస్ దన్ టూ అవర్స్… ఫెయిల్ పక్కా ఫెయిల్ ఇంకా ఎందుకంటే చదవలేదు | Less than two hours: fail, definitely fail, because he didn't study |
| 27 | D7 [10:42] | మన ఎగ్జామ్స్ లో 36 మార్క్స్ కంటే ఎక్కువ[ైతే] పాస్ అంటాం కదా అలానే ఇది కూడా | Like in our exams, above 36 marks we call it a pass; this is the same |
| 28 | D7 [14:36] | మాథ్స్ గురించి ఏం టెన్షన్ పడకండి ఈజీగానే ఉంటది… స్లో స్లోగా నేర్చుకుందాం | Don't stress about the maths, it'll be easy… let's learn slowly |
| 29 | D7 [17:11] | మీ దగ్గర క్ల్సీ [కాలిక్యులేటర్] ఉంటే క్ల్సీలో దీన్ని ఫార్ములా మీరు చెక్ చేయొచ్చు | If you have a calculator you can check this formula on it |
| 30 | D7 [23:08] | సి నేను దాన్ని ఏం చెప్పలేదు సపరేట్ చేసుకోమని అది ఒక లైన్ గీసుకుంది | See, I never told it to separate them, it drew a line by itself |
| 31 | D7 [24:04] | నేను క్లాస్ విన్నప్పుడు నాకు ఒక రెండు మూడు రోజులు పట్టింది ఇదంతా నేర్చుకోవడానికి | When I attended the class it took me two or three days to learn all this |
| 32 | D8 [00:00] | అప్పుడే మనం డేఎయిట్ కి వచ్చేసినామ అన్నమాట | We've already reached Day 8, you see |
| 33 | D8 [01:17] | ప్రెసెంటేషన్ లాగా అస్సలు చెప్ప[ను] ఎంగేజింగ్ గా మీకు అర్థమయ్యేలాగా నేను చెప్తూ ఉంటాను | I won't deliver it like a presentation at all; I'll keep it engaging so you get it |
| 34 | D8 [06:32] | ఆ సెంట్రాయిడ్ అనేది దాన్ని పుల్ చేసుకుంటది అన్నమాట | That centroid pulls it towards itself, you see |
| 35 | D8 [09:08] | సో నెక్స్ట్ స్టెప్ చేసి లాభం లేదు ఎందుకంటే ఆల్రెడీ క్లస్టర్స్ లాగా మారిపోయినారు | No point doing the next step, because they've already turned into clusters |
| 36 | D8 [10:26] | మీరు ఎవరికైనా ఎక్స్ప్లెయిన్ చేయాలి అనుకున్నా ఆర్ ఎగ్జామ్ లో రాయాలి అనుకున్నా… కే అంటే నెంబర్ ఆఫ్ క్లస్టర్స్ | If you want to explain it to someone or write it in an exam… K means the number of clusters |
| 37 | D8 [17:49] | వీటికి దానికి సంబంధం లేకుండా ఎక్కడనో మూలకు ఉంటదో దాన్ని అవుట్లయర్ అని పిలుస్తాం అన్నమాట | Whatever sits off in some corner with no connection to these, we call it an outlier |
| 38 | D8 [22:50] | డిబి స్కాన్ లో ఏం చేస్తాం ఒక రేడార్ లాగా ఉంటది అన్నమాట | What do we do in DBSCAN? It's like a radar |

---

## 2. Signature phrases and fillers (frequency-ranked)

Counts are regex hits over the **Telugu tracks only** (about 10,370 words, about 64 minutes). They are approximate: ASR fuses and splits words, so treat ±10%.

| Rank | Phrase | Function | D6 | D7 | D8 | **Total** | ≈ per min |
|---|---|---|---|---|---|---|---|
| 1 | **సో** (So) | sentence starter, transition | 41 | 94 | 82 | **217** | 3.4 |
| 2 | **అంటే** | "meaning / that is / X means"; his explanation hinge | 66 | 78 | 64 | **208** | 3.3 |
| 3 | **అన్నమాట** (incl. fused -న్నమాట) | sentence-final "you see / that's it"; closes almost every explanatory sentence | 43 | 57 | 70 | **170** | 2.7 |
| 4 | **మనం** | inclusive "we" | 44 | 58 | 38 | **140** | 2.2 |
| 5 | ఇప్పుడు / ఇక్కడ | "now" / "here", pointing at the screen | 13/7 | 42/48 | 30/30 | 85 / 85 | 1.3 each |
| 6 | **వచ్చేసి** | copula / list marker ("X వచ్చేసి Y") | 17 | 37 | 26 | **80** | 1.25 |
| 7 | కూడా | "also" | 28 | 22 | 10 | 60 | |
| 8 | ఏంటి / ఏంటిది | "what (is it)" | 20 | 24 | 16 | 60 | |
| 9 | **కదా** | tag "…right?" | 13 | 26 | 7 | **46** | |
| 10 | ఫస్ట్ | "first" (step markers) | 4 | 22 | 19 | 45 | |
| 11 | అండ్ | "and" (often to open a sentence) | 18 | 9 | 18 | 45 | |
| 12 | ఎగ్జాంపుల్ (any) / ఫర్ ఎగ్జాంపుల్ | example cue | 16/5 | 16/5 | 11/5 | 43 / 15 | |
| 13 | అంటాం / పిలుస్తాం | "we call it…" | 12 | 20 | 2 | 34 | |
| 14 | డిఫరెంట్ | "different" (over-used adjective) | 14 | 13 | 6 | 33 | |
| 15 | చూసుకుంటే | "if we look (at it)" | 1 | 8 | 22 | 31 | |
| 16 | **సింపుల్** | "simple", repeated as a comfort word | 14 | 9 | 6 | **29** | |
| 17 | అంటే ఏంటి(ది) | "what does X mean" | 14 | 12 | 2 | 28 | |
| 18 | యా (yeah) | live, unscripted filler, mostly while reading slides | 1 | 6 | 19 | 26 | |
| 19 | ఆర్ (or) | "or" | 11 | 8 | 6 | 25 | |
| 20 | కాబట్టి | "therefore" | 2 | 9 | 13 | 24 | |
| 21 | అసలు | "actually / in the first place", used to open a question ("అసలు X అంటే ఏంటి") | 12 | 6 | 5 | 23 | |
| 22 | డెఫినిషన్ / డెఫినేషన్ | definition cue | 3 | 13 | 7 | 23 | |
| 23 | చూపిస్తా / చూపిస్తున్న | "I'll show / I'm showing" | 4 | 11 | 7 | 22 | |
| 24 | ఏం చేస్తది అంటే / ఏం జరుగుతది / ఏమైతది | "what it does is…" | 4 | 11 | 7 | 22 | |
| 25 | అనుకుంటున్నా | "I think / I hope (you got it)" | 6 | 11 | 4 | 21 | |
| 26 | ఎక్స్ప్లెయిన్ (చేస్తా) | "I'll explain" | 6 | 11 | 3 | 20 | |
| 27 | ఎందుకంటే | "because" | 4 | 6 | 9 | 19 | |
| 28 | బట్ | "but" | 2 | 9 | 7 | 18 | |
| 29 | మీ అందరికీ / మీరందరూ | "all of you" | 7 | 5 | 5 | 17 | |
| 30 | లాస్ట్ వీడియో(స్) | callback to earlier days | 8 | 6 | 3 | 17 | |
| 31 | సారీ / సారి | self-correction and "sorry for interrupting" | 3 | 7 | 6 | 16 | |
| 32 | రాసుకోండి / రాసుకోవాలి | "write it down" | 4 | 6 | 5 | 15 | |
| 33 | గుర్తుపెట్టుకోండి / -వాలి | "remember this" | 7 | 5 | 3 | 15 | |
| 34 | ఎప్పుడైతే … -ఓ | "whenever…" (correlative) | 8 | 4 | 3 | 15 | |
| 35 | అనుకోండి / అనుకుందాం | "suppose / let's assume" | 4 | 19 | 4 | 27 | |
| 36 | అర్థమైంది / అర్థమవుతది | "(you) understood / it'll be clear" | 5 | 4 | 5 | 14 | |
| 37 | స్క్రీన్ మీద | "on the screen" | 3 | 5 | 5 | 13 | |
| 38 | క్లియర్ గా | "clearly" | 2 | 6 | 5 | 13 | |
| 39 | అర్థమయ్యేలాగా / అర్థమయ్యే విధంగా | "so that you understand" | 2 | 6 | 4 | 12 | |
| 40 | బేసిక్ (బేసిక్ బేసిక్) | "basic" | 11 | 1 | 0 | 12 | |
| 41 | నోట్స్ | "notes" | 1 | 7 | 4 | 12 | |
| 42 | చూడండి | "look" | 1 | 7 | 3 | 11 | |
| 43 | ఇంపార్టెంట్ (చాలా చాలా ఇంపార్టెంట్) | emphasis | 3 | 4 | 3 | 10 | |
| 44 | ఇందాక | "a little earlier" (in-video callback) | 4 | 3 | 3 | 10 | |
| 45 | ఒక్కసారి / ఒకసారి | "just once / for a moment" | 2 | 3 | 4 | 9 | |
| 46 | ఇదే X | "this is X" (closing a concept) | 0 | 4 | 4 | 8 | |
| 47 | అన్న / అన్నా | "brother". **Only ever in viewers' reported speech to him** | 2 | 2 | 0 | 4 genuine | |
| 48 | ఇంకా సింపుల్ గా / సింపుల్ గా చెప్పాలి | "more simply" | 4 | 1 | 2 | 7 | |
| 49 | అంతే (సింపుల్) | "that's all" | 2 | 2 | 3 | 7 | |
| 50 | ఓకే | "okay" | 0 | 4 | 3 | 7 | |
| 51 | కన్ఫ్యూజ్ (అవ్వద్దు) | "don't get confused" | 5 | 1 | 0 | 6 | |
| 52 | పేర్లోనే ఉంది | "it's in the name" | 1 | 2 | 1 | 4 | |
| 53 | ఏం లేదు | "there's nothing to it" | 0 | 3 | 0 | 3 | |
| 54 | గాయ్స్ | "guys" (opener only) | 1 | 1 | 1 | 3 | |
| 55 | థాంక్యూ సో మచ్ (ఫర్ వాచింగ్) … సైనింగ్ ఆఫ్ టెక్ బాయ్ దీపక్ | sign-off | 1 | 1 | 1 | 3 | |
| 56 | లెట్స్ డైవ్ ఇంటు ద వీడియో | opener | 1 | 1 | 0 | 2 | |

**Notes on the counts**
- **"ఒక్కసారి"** occurs (9 times) but is not a dominant tic. He uses it as "ఒక్కసారి రీక్యాప్ చేసుకుంటే", "ఒకసారి ఇమాజిన్ చేసుకోండి", "ఒక్కసారి చూద్దాం".
- **"బేసికల్లీ" does not appear in the Telugu tracks.** "Basically" in the English translation comes from the translator. His real equivalents are **సింపుల్ గా చెప్పాలి అంటే**, **అంటే**, and **బేసిక్ గా** (once: "మనం ఈ వీడియోలో బేసిక్ గా ఏమేమ కవర్ చేసిమ అంటే" D6 [14:31]).
- **"మస్తు", "బ్రో", "రా", "మామ"** do not appear. He is warm but not street-slangy, and he never uses రా/రే with the audience.
- **Address terms:** గాయ్స్ (opener), **మీరు / మీ అందరికీ / ప్రతి ఒక్కళ్ళు** (constant), **బిగినర్స్** ("మీలాంటి బిగినర్స్"), **మన వాళ్ళు** ("మన వాళ్ళు చాలా మంది… యక్టివ్ గా ఉంటున్నారు" D8 [00:00]), **ఫ్రెండ్స్** (only "మీ ఫ్రెండ్స్ ని కూడా… పార్ట్ చేసుకోండి").
- **Personifying the source.** When he reads AI-generated slides, he refers to the source as "he" or "it": "క్లియర్ గా మెన్షన్ చేసిండు", "స్ట్రెస్ చేసిండు అన్నమాట", "నాట్ నెసెసర్లీ అని పెట్టిండు" (D8 [03:54], [01:17], [22:50]) and "క్లియర్ గా చెప్పింది" (D8 [02:36]). He also says he used GPT and NotebookLM ("ఐమ యూజంగ్ జిపిట ఫర్ రిఫరెన్స్" D7 [13:19]; "నోట్బుక్ ఎల్ఎం యూస్ చేసి ఒక చిన్న ప్రెసెంటేషన్" D8 [01:17]).

---

## 3. Analogies and examples: full catalogue

### 3.1 Catalogue

| # | Day [time] | Example / analogy | Concept it explains | Set-up (how he introduces it) | Extension / payoff | Reused? |
|---|---|---|---|---|---|---|
| 1 | D6 [00:00] | **Student pass/fail model** (built in Day 5) | Classification | "మనం లాస్ట్ వీడియోలో ఏం బిల్డ్ చేసినాం… పాస్ అయిండా ఫెయిల్ అయిండా" (recap) | Contrasted at once with #2 | **Yes**: D6 throughout, D7 recap, decision tree and logistic regression, D8 recap. **Anchor example** |
| 2 | D6 [00:00], [09:49] | **Predicting how many marks a student will get** | Regression | "ఇంకొక మిషన్ లెర్నింగ్ మోడల్… ఎన్ని మార్క్స్ వస్తాయి" | "Same student dataset → classification gives pass/fail, regression gives next-exam marks" | Within D6 |
| 3 | D6 [02:36]–[03:52] | **Spam email detection** with "hundreds of emails" | Supervised learning, labels, classification | "ఒక మనం స్పామ్ డిటెక్షన్ ఈమెయిల్ అనే ఒక మోడల్ ని తీసుకున్నాం అనుకుందాం" | **Label = "leaking the answer to the model"** ("ఆన్సర్ కూడా లీక్ చేస్తాం"), the exam-paper-leak idea | **Yes**: binary (D6), logistic 0/1 (D7 [09:26]), recap (D7 [01:17]) |
| 4 | D6 [03:52] | **Cats, dogs, birds, horses** | Multi-class classification | "ఫర్ ఎగ్జాంపుల్ ఇప్పుడు మీరు తీసుకుంటే…" | n/a | Cats and dogs return in D6 quiz and D8 [02:36] (KNN: "ఇలా క్యాట్ ఉంటది ఇలా డాగ్ ఉంటది అని ముందే నేర్పించినాం") |
| 5 | D6 [05:09] | **Dog playing indoors (ఇంట్లో) vs outdoors** | Multi-label classification | "మీకు ఒక చిన్న ఎగ్జాంపుల్ చెప్తా" | Two labels at once: dog + outdoor | No |
| 6 | D6 [07:15]–[08:32] | **Buying a house**: location, square yards, prime location, bedrooms, surrounding houses → **₹65 lakhs** | Regression | "ఫర్ ఎగ్జాంపుల్ మీరు ఒక ఇల్లు కొందాం అనుకున్నారు. కానీ దాని ప్రైస్ మీకు తెలియదు" (second person: *you* are the buyer) | "అంత పర్ఫెక్ట్ గా ప్రిడిక్ట్ చేయలేదు… కొంచెం డిఫరెన్స్" sets up residual (#9) | **Yes**: residual (D6 [11:07]), quiz "80 lakhs" (D6 [14:31]) |
| 7 | D6 [08:32] | **0/1 output is not a number** | Why classification output can look numeric | "జీరో అనేది న్యూమరికల్ వాల్యూ… మరి వీటిని రిగ్రెషన్ లాగా కన్సిడర్ చేయొచ్చా? చేయం" | Becomes the hook for "why is logistic *regression* classification?" | **Yes**: D6 [13:42], D7 [08:19], [09:26] |
| 8 | D6 [09:49] | **100 students trained, 100 new students tested, 90 correct = 90%** | Accuracy | Framed as an exam: "ఇచ్చిన 100 క్వశ్చన్స్ లో 90 క్వశ్చన్స్ కరెక్ట్ గా ఆన్సర్ చేసింది" | Arithmetic done aloud: "100 100 క్యాన్సల్ అయిపోతాయి 90… వెలుగుతది". Then the honest caveat "అనుకున్నంత ఈజీ కూడా కాదు" (precision/recall later) | No |
| 9 | D6 [11:07] | **House actual ₹55 lakhs vs predicted ₹50 lakhs → ₹5 lakhs error** | Residual / prediction error, MAE / MSE | "మనం ఇందాక తీసుకున్న ఎగ్జాంపుల్ ఏంటిది హౌస్ వాల్యూ" | Scaled to "100 houses" for MAE/MSE, then he stops: "ఇంత డెప్త్ గా మాథ్స్ లోకి… వెళ్ళట్లేదు" | Reuses #6 |
| 10 | D6 [12:25] | **Flow of asking questions until you reach the answer**; **random forest = many trees' answers → one main answer** | Decision tree, random forest (preview) | "ఇక్కడ స్క్రీన్ మీద డెసిషన్ ట్రీ బొమ్మ చూపిస్తున్న" | Promises a detailed example later, delivered in D7 (#13) | **Yes**: D7 |
| 11 | D6 [14:31] | Quiz: **house costs 80 lakhs; image is cat/dog/bird; shop's product sales next month / next 6 months** | Classification vs regression check | "ఒక చిన్న క్విజ్… ఒక్క 30 సెకండ్స్ లో టెస్ట్ చేసుకుందాం" | Viewers answer in comments | Shop sales: new everyday-retail example |
| 12 | D7 [02:34] | **Trees have branches** | Decision-tree name | "పేర్లోనే ఉంది కదా… మన ట్రీస్ కి ఏముంటాయి బ్రాంచెస్ ఉంటాయి కదా" | Root node, branches, decision node, leaf node (the leaf idea continues the tree image) | n/a |
| 13 | D7 [02:34]–[07:26] | **"Did you prepare for the exam? How many hours?" → hours of study (<2, 2–6, >6) → hours of sleep (ఎంతసేపు పడుకున్నాడో) → previous grade** | Decision tree splitting | He interrogates the student in second person: "నువ్వు ఎగ్జామ్ కి ప్రిపేర్ అయినావా లేదా" | Common-sense reasons for each leaf: "పక్కా ఫెయిల్… ఎందుకంటే చదవలేదు"; "previous grade fail అనుకోండి ఈసారి కూడా ఫెయిల్ే అయితాడు" | Extends #1 |
| 14 | D7 [10:42] | **"Above 36 marks we call it a pass in our exams"** | Decision threshold in logistic regression | "ఫర్ ఎగ్జాంపుల్ మన ఎగ్జామ్స్ లో 36 మార్క్స్ కంటే ఎక్కువ[ైతే] పాస్ అంటాం కదా అలానే ఇది కూడా" | 75% sigmoid output > 50% threshold → 1 → pass | **Best single analogy for the target audience**: an Indian board-exam pass mark |
| 15 | D7 [09:26]–[10:42] | **Machine trained on student data, then a new student arrives** | Train → predict flow | "ఆ మిషిన్ మనం ఆల్రెడీ లాస్ట్ వీడియోలో ట్రైన్ చేసినం" | "75% అనే ఒక ప్రాబబిలిటీ ఇచ్చింది అనుకుందాం" | Extends #1 |
| 16 | D7 [13:19]–[18:30] | **5 students A–E with study hours and attendance**; student D: 4 hrs, 80% attendance; w1 = 0.8, w2 = 0.04, b = −4 → z = 2.4 → σ = 0.917 → **91.7% → pass** | Sigmoid, weights, bias, features | "మాథ్స్ గురించి ఏం టెన్షన్ పడకండి… స్లో స్లోగా నేర్చుకుందాం" | "క్ల్సీ ఉంటే… చెక్ చేయొచ్చు"; "10 ఫీచర్స్ ఉంటే w10 x10 దాకా వెళ్తది"; "ఈ అవుట్పుట్ మనం మిషిన్ కి ఇవ్వం… మిషినే కదా ప్రెడిక్ట్ చేయాల్సింది" | Extends #1 with **attendance** as a new feature |
| 17 | D7 [18:30]–[19:32] | **Apples and oranges, then apples and mangoes on a graph** | SVM boundary / hyperplane | "ఇమాజిన్ మన దగ్గర ఆపిల్స్ ఉన్నాయి ఆరెంజెస్ ఉన్నాయి" | He draws circles for apples and marks mangoes, then a line between them. Diagram: stars = apples, triangles = mangoes | Fruit swaps mid-video (orange → mango); slip corrected live ("సారీ యా… రెడ్ ఈస్ ఆపిల్ గ్రీన్ ఈస్ మ్యాంగో") |
| 18 | D7 [21:49]–[24:04] | **Interactive web demo: placing green (mango) and red (apple) points** | Support vectors, margin, kernels (linear, quadratic circle, RBF, sigmoid) | "ఒక ఆనిమేషన్ చూపిస్తా చాలా ఇంట్రెస్టింగ్ గా ఉంటది" | "నేను దాన్ని ఏం చెప్పలేదు సపరేట్ చేసుకోమని అది ఒక లైన్ గీసుకుంది"; mixed data shows the need for a kernel; "డేటా అంతా మెస్సీ మెస్సీ గా ఉందనుకోండి" | n/a |
| 19 | D8 [01:17] | **10 people, two of them twins; separate the twins by eyes and face** | Clustering by similarity | "దీన్నే ఎగ్జాక్ట్… ఎగ్జాంపుల్ అనుకోకండి" (disclaimer) | "ఆ సిమిలారిటీని బట్టి ఓకే వీళ్ళిద్దరు ఒకటి అని క్లస్టర్ లోకి వేస్తాం" | No |
| 20 | D8 [02:36] | **Cats and dogs taught beforehand** | Supervised (KNN) vs unsupervised | "మీకు లాస్ట్ వీడియోస్ లో నేను చెప్పిన…" | Contrast: clustering = "లేబుల్స్ లేకుండా గ్రూపింగ్" | Reuses #4 |
| 21 | D8 [04:53]–[10:26] | **Six people A–F with monthly spending power ₹1000, 1200, 2000, 8000, 9000, 9500** (customers: low vs high spenders) | K-means | "ఏబిసిడిఈఎఫ్ అనే ఒక సిక్స్ మెంబర్స్ ఉన్నారు… డిఫరెంట్ స్పెండింగ్ పవర్ ఉంటది" | People "standing on a line at their point" from ₹0 to ₹10,000; centroids at 1000 and 8000; means recomputed to 1500 and 8500; "మనం ఎప్పుడూ చెప్పలే వీళ్ళు లో స్పెండ్… హై స్పెండ్" | Within D8, revisited in the comparison table |
| 22 | D8 [06:32] | **Centroid = magnet** that pulls nearby points | Centroid | "C2 అనే ఒక… మాగ్నెట్ పెట్టుకున్నాం… ఎందుకు పెట్టిండో మీకు చెప్తా" | "ఈ మాగ్నెట్ ఏం చేసింది అంటే ఏ బి సి పర్సన్స్ ని పుల్ చేసింది" | **Yes**: recalled in the D8 [21:31] summary ("కేమీన్స్ గురించి చెప్పేటప్పుడు మాగ్నెట్… చూపించిన") |
| 23 | D8 [12:45]–[13:57] | **Points A–F joined by nearest distance** (AB, then ABC, ABCD; EF) | Hierarchical clustering (agglomerative) | "ఏ నుంచి బి కి ఏ నుంచి సి కి…" | Becomes a "tree-like structure" | Ties back to the tree image (#12) |
| 24 | D8 [13:57]–[15:14] | **Products: earphones ₹1000, mouse ₹1200, keyboard ₹5000, monitor ₹5200** | Hierarchical clustering by price distance; dendrogram height 3,800 | "నేను తీసుకొచ్చిన నోట్స్ లో ఎలా ఉందో చూద్దాం" | AB (200) and CD (200) pair first, then merge at 3,800 | Shopping / computer-accessory prices |
| 25 | D8 [17:49] | **Point I "sitting off in some corner"** | Outlier / noise | "ఐ అనేది ఎక్కడనో దూరంగా ఉంది" | "ఎక్కడనో మూలకు ఉంటదో దాన్ని అవుట్లయర్…"; recap: "కార్నర్ లో ఉంటది దట్ ఈస్ అవుట్లయర్" | Within D8 |
| 26 | D8 [22:50] | **Radar / scanner circle** | DBSCAN epsilon radius | "ఒక రేడార్ లాగా ఉంటది అన్నమాట" | "ఈ సెంటర్ నుంచి… డయామీటర్ ఈ రేంజ్ లో ఉన్నంతవరకు ఎప్సిన్" | No |
| 27 | D7 [24:04]; D6 [15:48] | **"Sit for one day and cover all six videos"; "it took me 2–3 days"** | Study-habit / motivation framing | n/a | Normalises struggle | Series-level |

### 3.2 His "example universe"

| Domain | Share of examples | Concrete items he uses | Flavour |
|---|---|---|---|
| **Student / exam life** (dominant) | ~45% | pass/fail, marks, next exam, hours of study, hours of sleep, previous grade, attendance, 36-mark pass line, 100 questions / 90 correct, "write it in the exam", notes, revision | Indian school and engineering-student reality; he speaks *to* the student ("నువ్వు ప్రిపేర్ అయినావా") |
| **Money in Indian units** | ~20% | house price ₹65 / 55 / 50 / 80 **lakhs**, **square yards**, **prime location**, bedrooms; monthly spending ₹1000–9500; product prices ₹1000–5200 | Always ₹ and lakhs, never dollars. Real estate and shopping, the things families talk about |
| **Everyday digital life** | ~10% | spam vs not-spam email; image of cat/dog/bird; shop's monthly sales | Familiar from phones |
| **Animals and fruit** | ~15% | cats, dogs, birds, horses; dog indoors/outdoors; apples, oranges, mangoes (mango is the Indian touch) | Visual, easy to draw on the whiteboard |
| **Physical-world metaphors** | ~10% | tree and branches, magnet, radar, twins' faces, "corner" | One concrete object per abstract mechanism |

**Patterns in how he uses examples**
1. **Anchor and extend.** The pass/fail student model starts in D5/D6 and gains features video by video (hours of study, then sleep, then previous grade, then attendance). New scripts should **keep the same student** and add one feature at a time.
2. **The same data answers two questions.** One student dataset gives pass/fail (classification) and marks (regression); one house gives a price (regression) and a residual.
3. **Second-person immersion.** "*You* want to buy a house", "*you* studied 4 hours". The learner is inside the example.
4. **Named toy rows (A, B, C, D, E, F)** with small round numbers, worked through step by step on screen (D7 students A–E, D8 persons A–F, products A–D, points A–I).
5. **Common-sense justification for each model decision**: "fail, because he didn't study", "pass, because he slept more than 6 hours".
6. **He disclaims imperfect analogies**: "దీన్నే ఎగ్జాక్ట్… ఎగ్జాంపుల్ అనుకోకండి" (D8 [01:17]).
7. **He switches fruit or labels mid-example and corrects himself out loud**. Imitators can keep a light version of this as authenticity, but should not script confusion.
8. **No examples from** sports/cricket, movies, food delivery, cars, medicine, social media, or Western contexts. **Cricket and movies would be new territory.** They fit the persona but are not attested, so use them sparingly and keep student, exam and money as the defaults.

---

## 4. How he defines terms (definition, then simplification)

**The fixed sequence**, seen in every major concept:

1. **Cue:** "X డెఫినిషన్ ఏందో చూద్దాం **రాసుకోండి**" / "ఫస్ట్ X డెఫినిషన్ రాసుకోండి" / "స్క్రీన్ మీద చూపిస్తున్న… నోట్స్ లో రాసుకోండి".
2. **Read the formal English definition verbatim** from the slide (often GPT- or NotebookLM-generated).
3. **"అంటే…"** paraphrase in Telugu-English, frequently **phrase by phrase**.
4. **"ఇంకా సింపుల్ గా చెప్పాలి అంటే…"**, a one-line "X చేసేదే Y" formula.
5. **"పేర్లోనే ఉంది కదా"** etymology where it helps.
6. **Example**, then **"దీన్నే Y అంటాం అన్నమాట"**, then **"సింపుల్."**
7. **Recall instruction:** "ఇవి గుర్తుపెట్టుకోండి" / "ఎగ్జామ్ లో రాయాలి అనుకున్నా…".

### Quoted instances

**Classification, D6 [01:19]–[03:52]**
> Formal: "వెన్ ఏ మెషన్ లెర్నింగ్ మోడల్ ప్రిడిక్ట్స్ ఏ కేటగిరి లైక్ పాస్ ఆర్ ఫెయిల్ స్పామ్ ఆర్ నాట్ స్పామ్ ఇట్ ఇస్ కాల్డ్ క్లాసిఫికేషన్"
> Paraphrase: "అంటే ఎప్పుడైతే మెషన్ లెర్నింగ్ మోడల్ ఒక క్యేటగిరీని ప్రెడిక్ట్ చేస్తదో… అప్పుడు దాన్ని క్లాసిఫికేషన్ అంటామ అన్నమాట"
> Simplest: "ఇంకా సింపుల్ గా చెప్పాలి అంటే ఒక క్యాటగిరీని ప్రిడిక్ట్ చేసేదే క్లాసిఫికేషన్. అంటే దీనికి చెందుతదా దీనికి చెందుతదా అనే ఒక కేటగిరీ లోకి దాన్ని ఫిల్టర్ చేసేదే క్లాసిఫికేషన్."

**Regression, D6 [06:25]–[08:32]**. Here the simple version comes *before* the formal one:
> "క్లాసిఫికేషన్ లో అవుట్పుట్ ఏముంటది క్యాటగిరీ ఉంటది. రిగ్రెషన్ లో అవుట్పుట్ ఏముంటది అంటే ఒక నెంబర్ ఉంటదిన్నమాట"
> Then: "రిగ్రెషన్ డెఫినిషన్ వచ్చేసి వెన్ ఏ మెషన్ లెర్నింగ్ మోడల్ ప్రిడిక్ట్స్ ఏ న్యూమరికల్ వాల్యూ లైక్ ఏ హౌస్ ప్రైస్ ఆర్ ఏ స్టూడెంట్స్ మార్క్స్…"
> Then: "సింపుల్ గా చెప్పిన కదా న్యూమరికల్ వాల్యూ ని అవుట్పుట్ లాగా తీసుకొచ్చేదే ఈ రిగ్రెషన్", and after the example: "ఒక్క మాటలో చెప్పాలి అంటే…"

**Decision tree, D7 [02:34]**. Phrase-by-phrase gloss:
> "ఏ డిసిషన్ ట్రీ ఈస్ ఏ సూపర్వైజడ్ మషన్ లెర్నింగ్ ఆల్గరిథం దట్ మేక్స్ ప్రడిక్షన్స్ బై ఫాలోయింగ్ ఏ సీక్వెన్స్ ఆఫ్ క్వశన్స్… పేర్లోనే ఉంది కదా… ట్రీస్ కి ఏముంటాయి బ్రాంచెస్ ఉంటాయి కదా… **దట్ మేక్స్ ప్రెడిక్షన్స్**: ఇప్పుడు మనం మిషన్ లెర్నింగ్ మోడల్ అసలు ఏం చేస్తున్నాం ఒక డేటా సెట్ ఇచ్చి దానికి అవుట్పుట్ తీసుకొస్తున్నాం. ప్రెడిక్షన్ ఏంటిది ఆ అవుట్పుట్ే. సో **బై ఫాలోయింగ్ ఏ సీక్వెన్స్ ఆఫ్ క్వశన్స్** అంటే ఈ మిషన్ లెర్నింగ్ మోడల్ కొన్ని క్వశన్స్ అడుగుతూ…"
> Closing simplification, D7 [08:19]: "ఏం లేదు చాలా సింపుల్ గా ఉంటది ట్రీస్ ఉంటాయి డిఫరెంట్ క్వశన్స్ ని యూస్ చేసుకొని అవుట్పుట్ తీసుకొచ్చేదే డెసిషన్ ట్రీ సింపుల్"

**Root / decision / leaf node, D7 [03:52]–[05:10]**. Point at the diagram, give the English definition, then re-ask in Telugu:
> "లీఫ్ నోడ్ అంటే ద ఫైనల్ ప్రిడిక్షన్ సచ్ యస్ పాస్ ఆర్ ఫెయిల్ **లీఫ్ నోడ్ అంటే ఏంటిది** లాస్ట్ లో ఫైనల్ ప్రెడిక్షన్ ఉంటది కదా దీన్ని లీఫ్ నోడ్ అంటాం."

**Clustering, D8 [01:17]**. Keyword stressing:
> "…గ్రూప్స్ అన్లబుల్డ్ డేటా పాయింట్స్ బేస్డ్ ఆన్ దర్ సిమిలారిటీస్ సో ఈ డెఫినిషన్ లోనే మనకి క్లియర్ గా అర్థమవుతుంది… సెకండ్ థింగ్ వచ్చేసి **బేస్డ్ ఆన్ సిమిలారిటీస్** అని స్ట్రెస్ చేసిండు అన్నమాట. ఇక్కడ చూడండి…" Then the twins example follows.

**K-means, D8 [03:54]**. Etymology:
> "మనం పేర్లోనే చూస్తున్నాం కే మీన్స్ క్లస్టరింగ్ కే అంటే ఏంటిది అంటే ఒక ప్రీడిఫైన్డ్ నెంబర్… k = 2 అని పెడితే ఆ డేటా మొత్తం టూ క్లస్టర్స్ లాగా డివైడ్ అవుతది."

**Label, D6 [02:36]**. Plain-language redefinition with no formal text:
> "లేబుల్ అంటే ఏంటిది ఇది స్పామ్ ఇది నాట్ స్పామ్ అని క్లియర్ గా సింపుల్ గా చెప్పాలంటే మన మోడల్ కి ఆన్సర్ కూడా లీక్ చేస్తామ అన్నమాట"

**Dendrogram, D8 [15:14]**:
> "డెంోగ్రామ్ ఈస్ ఏ ట్రీ లైక్ డయాగ్రామ్ దట్ ఇల్ూస్ట్రేట్స్ ద హైరారికల్ రిలేషన్షిప్… **సింపుల్** ఆ పాయింట్స్ యొక్క డిస్టెన్స్ ని చూసి ఆ రిలేషన్షిప్ ని కనిపెట్టేదే ఈ డెంోగ్రామ్"

**He also defuses false friends**, i.e. names that mislead:
- "ఈ క్లాసిఫికేషన్ రిగ్రెషన్ అనేవి ఆల్గరిథమ్స్ కాదు అవి టైప్స్ ఆఫ్ సూపర్వైజడ్ లెర్నింగ్" (D6 [12:25])
- "లాజిస్టిక్ రిగ్రెషన్ అనే పేరులో రిగ్రెషన్ ఉంది కదా ఇది క్లాసిఫికేషన్ లోకి ఎందుకు వస్తుంది… మీ అందరికీ ఒక క్వశ్చన్ రావాలి" (D7 [08:19]). He plants the doubt himself, then resolves it.

---

## 5. Tone and persona

| Trait | Evidence |
|---|---|
| **Reassurance before difficulty** | "అస్సలు భయపడకండి చాలా సింపుల్ టాపిక్స్ ఇవన్నీ" (D7 [00:00]); "మాథ్స్ గురించి ఏం టెన్షన్ పడకండి ఈజీగానే ఉంటది… స్లో స్లోగా నేర్చుకుందాం" (D7 [14:36]); "బిగినర్స్ అందరూ టెక్నికల్ టర్మ్స్ ని గుర్తుపెట్టుకోవాల్సిన అవసరం లేదు" (D6 [05:09]) |
| **Voicing the viewer's fear, then flipping it** | "చాలా మంది ఏంటన్నా ఈ టెర్మినాలజీ కొంచెం హార్డ్ అనిపిస్తుంది మేమేమో బిగినర్స్ మాకు అర్థం కాదు అనుకుంటారు కదా… మీరు విన్నాక మీరే అంటారు చాలా ఈజీ గా ఉందన్న మేము దీన్ని హార్డ్ అనుకున్నాం కదా" (D7 [00:00]). This is his signature way of handling "you might think this is hard" |
| **"Don't get confused" guard-rails** | "కన్ఫ్యూజ్ అవ్వద్దు" at the multi-class/multi-label split (D6 [05:09]), the 0/1 trap (D6 [08:32]), the term residual (D6 [11:07]), and algorithm vs type (D6 [12:25]) |
| **Honest balance, not hype** | "ఎట్ ద సేమ్ టైం మీరు అనుకున్నంత ఈజీ కూడా కాదు ఎమ్మటే మనం చిన్న ఫార్ములా వేసేసినం… అనుకుంటే కాదు" (D6 [09:49]); "30 మినిట్స్ లో మీకు అంత డెఫినెట్ గా మొత్తం అర్థం కాదు" (D7 [24:04]) |
| **Humility / peer learner** | "నేను క్లాస్ విన్నప్పుడు నాకు ఒక రెండు మూడు రోజులు పట్టింది" (D7 [24:04]); "నాతో పాటు మీరు కూడా ఈ ఏఐ లెర్నింగ్ సిరీస్ లో పార్ట్ అవ్వాలి" (D6 [15:48]); he admits using GPT and NotebookLM |
| **Self-deprecating, unpolished moments** | Pen joke: "ఈ పెన్ తో హ్యాండ్ రైటింగ్ ప్రాపర్ గా వస్తలేదు దాన్ని ఇగ్నోర్ చేయండి బట్ మీకు అర్థమవుతుంది అనుకుంటున్నా" (D7 [00:00]). Live slips: "గ్రీన్ కలర్ ని మ్యాంగోస్ అనుకుందాం సారీ యా" (D7 [21:49]), "a+ సారీ d+e+f/3" (D8 [10:26]), "ఆ దీన్ని ఏమంటారు డయామీటర్" (D8 [22:50]) |
| **Personal enthusiasm** | "ఇది చాలా మంచి కాన్సెప్ట్ నాకైతే ఇంట్రెస్టింగ్ అనిపించే కాన్సెప్ట్" (D7 [18:30]); "చాలా మంచి ఎగ్జాంపుల్ అయితే నేను తీసుకొచ్చిన" (D7 [03:52]); "చాలా ఇంట్రెస్టింగ్ గా ఉంటది" (D7 [21:49]); "చూడండి ఆటోమేటిక్ గా అది హైపర్ ప్లేన్ గీసుకుంటుంది" (D7 [23:08]) |
| **Teacher-in-class energy** | "రాసుకోండి" ×15, "నోట్స్" ×12, "గుర్తుపెట్టుకోండి" ×15, a quiz each video, "pause చేసి రాసుకోండి" (D7 [07:26]), "ఎగ్జామ్ లో రాయాలి అనుకున్నా" (D8 [10:26]) |
| **Community / "మన" language** | "మన ఛానల్", "మన వ్యూవర్స్", "మన వాళ్ళు చాలా మంది… యక్టివ్ గా ఉంటున్నారు", "మా టీం", "నోట్స్ మా టీం వాళ్ళు మీకు నైట్ లోపు షేర్ చేస్తారు" (D8 [22:50]) |
| **Gentle FOMO / motivation** | "ఇంకా లేట్ ఏమ అయిపోలేదు… ఒక 30 వీడియోస్ అయిపోయినాక మీరు చూడడం స్టార్ట్ చేస్తే మీరే మిస్ అయిపోతారు… ఒక్క రోజు కూర్చుంటే కవర్ చేయొచ్చు" (D6 [15:48]) |
| **Humour** | Mild and situational rather than jokes: the pen, "answer leak", "90 అనేది వెలుగుతది", "పక్కా ఫెయిల్… ఎందుకంటే చదవలేదు". No sarcasm, no put-downs |
| **Relationship** | Big brother / senior. The audience calls him **అన్న** (D6 [06:25], D7 [00:00], [09:26]). He responds to their requests ("స్లో చేయకన్నా ఫాస్ట్ గా చెప్పు… కచ్చితంగా తీసుకొస్తాం") |

---

## 6. Depth markers (explicit depth limits)

| Day [time] | Quote | What it does |
|---|---|---|
| D6 [05:09] | "వచ్చే ఫర్దర్ వీడియోస్ లో కూడా ఇంకా కొంచెం డీటెయిల్ గా… ఇంకా డెప్త్ గా ఎక్స్ప్లెయిన్ చేయగలిగితే ఎక్స్ప్లెయిన్ చేస్తా" | Defers detail |
| D6 [05:09] | "ఈ బేసిక్ టర్మ్స్ ఆ బేసిక్ ఎగ్జాంపుల్స్ ని గుర్తుపెట్టుకోండి" | Scope = terms + examples only |
| D6 [11:07] | "ప్రెసిషన్ రీకాల్ ఇంకా మెట్రిక్స్… అవి మనం వచ్చే వీడియోస్ లో కూడా డిస్కస్ చేద్దాం" | Names the advanced terms, then parks them |
| D6 [11:07] | "**సో ఇంత డెప్త్ గా మాథ్స్ లోకి అయితే అప్పుడే వెళ్ళట్లేదు.** నెక్స్ట్ వీడియోస్ లో… చెప్తా ఎందుకంటే ఇప్పుడే మాథ్స్ చెప్పడం స్టార్ట్ చేస్తే కొంచెం కన్ఫ్యూజ్ అయితారు కొంచెం ఆగం అవుతారు అన్నమాట. అందుకే అది గుర్తుపెట్టుకొని నేనేం చెప్పట్లేదు" | **The canonical depth limit, with the reason given** |
| D6 [12:25] | "ఇవైతే బేసిక్స్ ఇవి మీరందరూ రాసుకోవాలి" | Marks the must-know layer |
| D6 [12:25] | "నేను ఆల్గరిథమ్స్ గురించి డెప్త్ గా చెప్ప[ను] బట్ బేసిక్స్ చెప్తా" | Algorithms only previewed |
| D6 [12:25] | "దీని గురించి నేను డీటెయిల్ గా ఒక ఎగ్జాంపుల్ తీసుకొని తర్వాత ఎక్స్ప్లెయిన్ చేస్తా" | Promise, kept in D7 |
| D6 [13:19] | "సో ఇవి మీకు ఎందుకు చెప్తున్నా అంటే **జస్ట్ బేసిక్ ఐడియా ఉండడానికి**" | States the purpose of a preview |
| D7 [07:26] | "ఈ రెండు కాన్సెప్ట్స్ డెఫినేషన్స్ గురించి మీరు తెలుసుకోవాలి అనుకుంటే ఇక్కడ స్క్రీన్ మీద వన్ మినిట్ పాస్ చేసి… రాసుకోండి" | Gini / Entropy offloaded to the screen and made optional |
| D7 [14:36] | "మాథ్స్ గురించి ఏం టెన్షన్ పడకండి ఈజీగానే ఉంటది సో కన్ఫ్యూజ్ అయితే మళ్ళీ మనకి అర్థం కాదు సో స్లో స్లోగా నేర్చుకుందాం" | **When he does go into maths**, it comes wrapped in reassurance, one worked example, calculator-level |
| D7 [13:19]–[15:53] | "దీస్ ఆర్ ద ఇల్యూస్ట్రేటివ్ వాల్యూస్… మెషిన్ మాత్రం క్యాలిక్యులేట్ చేసుకుంటది" | Assumes the weights, skips how they are learned |
| D7 [24:04] | "నేనేం సజెస్ట్ చేస్తా అంటే మీకు డిస్క్రిప్షన్ లో దీన్ని నోట్స్ పెడుతున్నా విత్ డెఫినేషన్స్ విత్ గ్రాఫ్స్ ఫార్ములాస్" | Depth moved to the notes |
| D8 [01:17] | "దీన్నే ఎగ్జాక్ట్… ఎగ్జాంపుల్ అనుకోకండి" | Analogy-precision disclaimer |
| D8 [02:36] | "డెన్సిటీ బేస్డ్ సిమిలారిటీ సంథింగ్ ఉంటది" | Comfortable hand-wave on a full form; fixes it precisely later |

**Takeaway.** He goes as deep as one hand-calculable example (sigmoid with three assumed numbers, K-means means of three values, price differences). He **does not** derive anything, show calculus, explain how weights are learned, or use matrix notation. Formulas are shown, read once, worked with toy numbers, and summarised ("ఒకవేళ 10 ఫీచర్స్ ఉంటే w10 x10 దాకా వెళ్తది").

---

## 7. Do / Don't rules for imitating him

### DO
1. **Write Telugu grammar with English content words.** Keep every ML term in English (model, data, feature, weights, loss, neuron, layer, activation, epoch…). Never coin a Telugu translation for a technical term.
2. **Use Telangana verb endings by default**: చేస్తది, ఉంటది, అవుతది, వస్తది, నేర్చుకుంటది; చేసినాం / చూసినం; చదివిండు / చెప్పిండు; వచ్చినాయి. Mix in an occasional standard -తుంది (about 1 in 6).
3. **Build verbs as English stem + చేయ్ / అవ్వు**: predict చేస్తది, train చేసినాం, separate చేస్తది, confuse అవ్వద్దు, form అయినాయి.
4. **End explanatory sentences with అన్నమాట** (about 2–3 per minute), hinge with **అంటే**, start with **సో**, and tag with **కదా**.
5. **Use వచ్చేసి to enumerate and state values**: "ఫస్ట్ వన్ వచ్చేసి…, సెకండ్ వన్ వచ్చేసి…", "output వచ్చేసి 0.91".
6. **Follow the definition loop**: "X అంటే ఏంటి? → రాసుకోండి → English definition read verbatim → అంటే… → ఇంకా సింపుల్ గా చెప్పాలి అంటే … చేసేదే X → example → దీన్నే X అంటాం అన్నమాట → సింపుల్."
7. **Explain from the name** wherever possible ("పేర్లోనే ఉంది కదా": neural network means a network of neurons, deep means many layers).
8. **Anchor on the student pass/fail model.** Reuse hours of study, sleep, attendance, previous grade and marks. Add one new feature or idea per video, and call back with "మనం లాస్ట్ వీడియోలో…" and "ఇందాక…".
9. **Use Indian money and units**: ₹, lakhs, square yards, monthly spending, prices of phones/earphones/laptops, the 35/36 pass mark.
10. **Give toy data named A, B, C, D, E** with small round numbers, and work one row out loud ("స్టూడెంట్ D ది చూద్దాం…").
11. **Give each abstract mechanism one physical metaphor** (magnet, radar, tree, leak), and disclaim it if it's loose ("దీన్నే ఎగ్జాక్ట్ ఎగ్జాంపుల్ అనుకోకండి").
12. **Voice the viewer's fear in their own words, including "అన్నా"**, then flip it: "చాలా మంది ఏంటన్నా ఇది హార్డ్ అనుకుంటారు కదా… అస్సలు భయపడకండి".
13. **Say outright where you're stopping**: "ఇంత డెప్త్ గా మాథ్స్ లోకి అయితే అప్పుడే వెళ్ళట్లేదు… ఆగం అవుతారు", and promise a later video.
14. **Put "కన్ఫ్యూజ్ అవ్వద్దు" at every look-alike pair** (for example, a parameter is not a hyperparameter, an epoch is not an iteration).
15. **Ask rhetorical questions and answer them**: "చేయొచ్చా చేయరాదా? మీరేమనుకుంటున్నారు? ఎస్…".
16. **Keep it collaborative**: మనం, మన, "నాతో పాటు మీరు కూడా", "స్లో స్లోగా నేర్చుకుందాం".
17. **Include one small humility or honesty beat** per video ("నాకు కూడా రెండు మూడు రోజులు పట్టింది", "అనుకున్నంత ఈజీ కూడా కాదు").
18. **Use "simple" a lot**: "సింపుల్", "అంతే సింపుల్", "ఏం లేదు చాలా సింపుల్", about 0.5 per minute.

### DON'T
1. **Don't write pure or bookish Telugu**: no ఏమిటి, చేస్తుంది-only, యంత్ర అభ్యాసం, దత్తాంశం. It would sound like Doordarshan, not Deepak.
2. **Don't use Andhra/coastal or formal endings throughout** (చేశాము, వచ్చాయి, చెప్పాడు). They exist in his speech but are a minority.
3. **Don't overload the slang.** ఆగం, ఎమ్మటే, మూలకు and పక్కా are spices (once per video at most). **Never** use రా/రే/మామ/బ్రో with viewers, and don't make him call viewers "అన్నా".
4. **Don't put "basically" in his mouth**; it comes from the translator. Use సింపుల్ గా చెప్పాలి అంటే / అంటే.
5. **Don't use Western examples** ($, miles, SAT scores, baseball, Netflix as a default). Keep to ₹, lakhs, exams, Indian shops and homes.
6. **Don't introduce a new example universe every video.** Reuse the student, the spam email, the house and the spending customers before inventing new ones.
7. **Don't derive maths.** At most: show a formula, read it once, plug in 2–3 assumed numbers, use a calculator, compare with a threshold, summarise.
8. **Don't sound like a slide deck.** He explicitly says "ప్రెసెంటేషన్ లాగా అస్సలు చెప్పను". Break up definitions with అంటే, కదా and questions.
9. **Don't make him infallible or slick.** No polished corporate tone; small live corrections (సారీ యా) are in character, though they shouldn't be scripted heavily.
10. **Don't insult or talk down to beginners.** Even the honest caveat is framed kindly ("30 మినిట్స్ లో మొత్తం అర్థం కాదు, నాకు కూడా 2–3 రోజులు పట్టింది").
11. **Don't translate technical terms into Telugu on screen.** On-screen definitions stay in English; the Telugu explanation is spoken.
12. **Don't drop the "write it down" cues.** Without రాసుకోండి / గుర్తుపెట్టుకోండి / notes, the classroom feel is gone.
13. **Don't use long subordinate English clauses in the spoken parts.** English appears as single words or read-out definitions, not as full spoken English sentences (except stock lines: "let's dive into the video", "that's it for the day", "thank you so much for watching").

---

## 8. Voice calibration paragraph (original, new concept: "What is data?")

*(Telugu grammar in Telugu script; English terms in Latin script as he would put them on screen; ~125 words)*

> సో ఇప్పుడు మనం అసలు **data** అంటే ఏంటో చూద్దాం, అందరూ **notes** లో రాసుకోండి. **Definition** వచ్చేసి: *"Data is a collection of facts, numbers or observations that a machine learning model learns from."* అంటే సింపుల్ గా చెప్పాలి అంటే, మనం **machine** కి ఏదైతే **information** ఇస్తామో దాన్నే **data** అంటాం అన్నమాట. ఫర్ ఎగ్జాంపుల్ ఒక **class** లో 60 మంది **students** ఉన్నారు అనుకుందాం. ప్రతి ఒక్క **student** ఎన్ని **hours** చదివిండు, **attendance** ఎంత ఉంది, **last exam** లో ఎన్ని **marks** వచ్చినాయి, ఇవన్నీ ఒక **table** లాగా రాసుకుంటే అదే మన **dataset** అన్నమాట. ఒక్కో **column** ని **feature** అంటాం, ఒక్కో **row** ఒక **student**. ఇక్కడ కన్ఫ్యూజ్ అవ్వద్దు, **data** అంటే **numbers** మాత్రమే కాదు, **photos**, **emails**, **voice** కూడా **data** నే. మనం మంచి **data** ఇస్తే **model** మంచిగా నేర్చుకుంటది, తప్పు **data** ఇస్తే తప్పుగానే నేర్చుకుంటది కదా. అంతే సింపుల్, ఏం లేదు దీంట్లో!

**The same paragraph as the ASR would caption it** (English rendered in Telugu script), for reference:
> సో ఇప్పుడు మనం అసలు డేటా అంటే ఏంటో చూద్దాం అందరూ నోట్స్ లో రాసుకోండి డెఫినిషన్ వచ్చేసి డేటా ఈస్ ఏ కలెక్షన్ ఆఫ్ ఫాక్ట్స్ నంబర్స్ ఆర్ అబ్జర్వేషన్స్ దట్ ఏ మెషీన్ లెర్నింగ్ మోడల్ లెర్న్స్ ఫ్రమ్ అంటే సింపుల్ గా చెప్పాలి అంటే మనం మెషిన్ కి ఏదైతే ఇన్ఫర్మేషన్ ఇస్తామో దాన్నే డేటా అంటామ అన్నమాట…

**Features of the voice in the paragraph:** opens with సో; uses "అసలు X అంటే ఏంటో చూద్దాం"; cues రాసుకోండి; marks the definition with వచ్చేసి; gives the English definition verbatim; continues with "అంటే సింపుల్ గా చెప్పాలి అంటే"; uses "ఏదైతే… దాన్నే… అంటాం అన్నమాట"; anchors on the student / attendance / marks example; uses ఫర్ ఎగ్జాంపుల్ … అనుకుందాం; has Telangana forms చదివిండు, వచ్చినాయి, నేర్చుకుంటది; includes the "కన్ఫ్యూజ్ అవ్వద్దు" guard-rail; ends on a common-sense moral with కదా and closes with "అంతే సింపుల్, ఏం లేదు దీంట్లో".

---

## Appendix: method

- The Telugu sections (after `## తెలుగు`) were extracted, timestamps stripped, and phrases counted with Python regex (Telugu-letter boundaries for short tokens like సో, యా, అండ్, బట్, ఆర్). The count scripts are in the session scratchpad: `/tmp/claude-0/-home-user-AI-Learning-series/991ce546-83cf-5aab-8ee0-6ee23f4b3e74/scratchpad/count.py`, `count2.py` and `count3.py`.
- Counts include ASR artefacts (fused tokens, duplicated words) and are good to about ±10%. The *ranking* is robust.
- "అన్న/అన్నా" hits were checked by hand in context. Of all the hits, 4 are genuine vocatives (all viewer-to-Deepak). The rest are parts of ఉందన్నమాట or "రెడ్ అన్న[ీ]" ("all the reds").
