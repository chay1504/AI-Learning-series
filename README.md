# AI Learning Series: Research & Scripts

Research and video scripts for **Tech Boy Deepak's _AI Learning Series_** on YouTube ([@tech.boy.deepak](https://www.youtube.com/@tech.boy.deepak/videos)). The aim is to continue the series into **Deep Learning** in Deepak's own voice, depth and teaching style.

## Start here

| If you want to… | Open |
|---|---|
| **Record the deep learning videos** | `script-telugu.md` in each folder under [`scripts/`](scripts): Part 1 (`video-A-…`), Part 2 (`video-B-…`), Part 3 (`video-C-…`), Part 4 (`video-D-…`) |
| Run the Colab demos (Parts 3 & 4) | [`notebooks/`](notebooks): open in Google Colab → Runtime → Run all |
| Review the scripts in English | `script-english.md` in each video folder |
| Get titles, thumbnails, descriptions, board drawings | `production-notes.md` in each video folder |
| Understand Deepak's style ("DNA") | [`research/style-dna-report.md`](research/style-dna-report.md) |
| See what's covered and what's next | [`coverage/`](coverage) |

## Layout

```
transcripts/   Series transcripts: Telugu original + English auto-translation, timestamped
coverage/      curriculum-days-21-35.md (the Phase 3 plan) · topics-covered.md · topics-remaining.md
research/
  style-dna-report.md                 Master Style DNA report + scriptwriter's checklist
  dna-parts/01-structure-pacing-depth.md     Video architecture, timings, depth (detailed)
  dna-parts/02-voice-language-analogies.md   Telugu/English code-mix, phrases, analogies (detailed)
  dl-content-research.md              Fact-checked deep learning brief, Days 21–28, with worked numbers
  dl-content-research-part-3.md       Brief for Days 29–30 (epochs, batches, learning rate, first Keras build)
  dl-content-research-part-4.md       Brief for Days 31, 32, 35 (computer vision, CNN, image classifier)
notebooks/
  part-3-train-your-first-neural-network.ipynb   Tested Colab notebook: 9-parameter student network
  part-4-build-an-image-classifier.ipynb         Tested Colab notebook: MNIST CNN (~98.9% test accuracy)
scripts/
  video-A-inside-a-neural-network/    Day 9: What is DL · artificial neuron · layers · weights & biases (plan Days 21–24)
  video-B-how-a-neural-network-learns/ Day 10: activation · loss · gradient descent · backpropagation (plan Days 25–28)
  video-C-train-your-first-neural-network/ Day 11: epochs · batches · learning rate · build in Keras (plan Days 29–30)
  video-D-how-ai-sees-images/         Day 12: computer vision · CNN · build an image classifier (plan Days 31, 32, 35)
```

## The four videos

| | Part 1: Inside a Neural Network | Part 2: How a Neural Network Learns | Part 3: Train Your First Neural Network | Part 4: How AI Sees Images |
|---|---|---|---|---|
| Folder | `video-A-…` | `video-B-…` | `video-C-…` | `video-D-…` |
| Channel episode | Day 9 | Day 10 | Day 11 | Day 12 |
| Plan days | 21–24 | 25–28 | 29–30 | 31, 32, 35 |
| Topics | What is DL, artificial neuron, layers, weights & biases | Activation (ReLU, sigmoid), loss, gradient descent, backprop | Epochs, batches, learning rate, overfitting; build in Keras/Colab | Pixels, CNN filters, feature maps, pooling, softmax; MNIST classifier in Colab |
| Running example | Student D, then the Ravi / Sita / Kiran network | The network learns from Sita's wrong 38% | The same 9-knob network trained on a class; Sita goes from 38% to 95% | Handwritten digits, like reading marks on an answer sheet |
| Length | ~24 min | ~24 min | ~26 min | ~26 min |

Next up (not scripted yet): **Part 5: How AI Reads Text** (plan Days 33–34: NLP, RNN vs LSTM vs Transformer). See [`coverage/topics-remaining.md`](coverage/topics-remaining.md).

## Notes & caveats

- **Transcripts:** the transcripts come from YouTube's auto-generated captions, so expect some speech-recognition errors. **Days 3, 6, 7 and 8** are included. Days 1, 2 and 4 could not be downloaded because YouTube blocked automated access from the cloud server ("confirm you're not a bot"). The Day 3 transcript only came through on a later retry, so the style analysis is based on Days 6–8, and Day 3 was used to check the scripts' callbacks.
- **Numbers:** every number in the scripts was checked with Python.
- **Unconfirmed claims:** facts the research couldn't confirm are tagged **[verify]** and kept out of the scripts.
- **Episode numbers:** episodes are numbered Day 9–12 to follow the channel.
- **Personal lines:** a few lines describe Deepak's own experience (for example Part 3's mid-roll and Part 4's H3). Each video's `production-notes.md` marks them "keep only if true".
- **Colab results:** notebook numbers were produced with fixed seeds on TF 2.21 / Keras 3.15. Your Colab run may differ slightly, and the scripts mark those spots. Renumber them if you're following the plan's Day 21+ numbering.
