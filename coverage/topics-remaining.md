# What's Left to Explain

## Deep Learning block: the parts
| Part | Channel episode | Plan days | Topics | Status |
|---|---|---|---|---|
| **Part 1: Inside a Neural Network** | Day 9 | 21–24 | What is deep learning · artificial neuron · layers · weights & biases | ✅ Scripted (`scripts/video-A-…`) |
| **Part 2: How a Neural Network Learns** | Day 10 | 25–28 | Activation (ReLU, sigmoid) · loss · gradient descent · backpropagation | ✅ Scripted (`scripts/video-B-…`) |
| **Part 3: Train Your First Neural Network** | Day 11 | 29–30 | Epochs, batches, learning rate · build and train a network in Keras (Colab) | 🛠 In progress (`scripts/video-C-…`, `notebooks/part-3-…`) |
| **Part 4: How AI Sees Images** | Day 12 | 31, 32, 35 | Computer vision · CNN (filters, feature maps, pooling) · build an image classifier (MNIST, Colab) | 🛠 In progress (`scripts/video-D-…`, `notebooks/part-4-…`) |
| Part 5: How AI Reads Text (suggested) | Day 13 | 33–34 | NLP · RNN vs LSTM vs Transformer, which leads into the LLM phase | ⏳ Not scripted yet |

### Why the split looks like this
- **Part 3** delivers what Part 2 teased ("next video: epochs, batches and learning rate") and its line "model.fit() = this loop". Day 30's build fits naturally right after.
- **Part 4** keeps all the vision material together. Plan Day 35 (build an image classifier) moves up next to the CNN theory, so viewers see the theory working straight away.
- **Part 5** groups the two text/sequence days (33–34). Ending the block on Transformers sets up the LLM technical phase.

## Notes
- **Episode numbers:** the channel is at **Day 8**, and nothing in the series has been published since then (checked 2026-11-20). The scripts number the parts Day 9–12. Change that line if you're following the plan's Day 21+ numbering.
- **Phase 2 (plan Days 9–20)** isn't in the screenshot. If it covers LLM concepts, decide whether it comes before or after the deep learning block.
