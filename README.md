# Perplexity Explorer

An interactive, in-browser educational tool to explore and understand language model perplexity from first principles to real neural predictions.

🌐 **Live Demo:** [https://soumilsri21.github.io/perplexity-explorer/](https://soumilsri21.github.io/perplexity-explorer/)

## Features

- **Section 1 – Sentence Perplexity with Real Model**:
  - Runs `Xenova/distilgpt2` (q8 quantization) entirely inside the client's browser using [Transformers.js](https://huggingface.co/docs/transformers.js).
  - Starts inference from token `[50256]` (`<|endoftext|>`) to evaluate probability for every token including the first word.
  - Numerically stable softmax to avoid floating-point overflow.

- **Section 2 – Token Probability Breakdown**:
  - Full table with token IDs, decoded representation (spaces as `␣`), probabilities $P$, and surprise values $1/P$.
  - Detailed step-by-step calculation:
    - Step 1: Total surprise product ($\prod 1/P$)
    - Step 2: Sequence length ($N$)
    - Step 3: Perplexity = $(\prod 1/P)^{1/N} = \exp\left(\frac{1}{N}\sum -\ln P\right)$

- **Section 3 – Next Token Prediction**:
  - Real-time top 8 next token candidates from the last logit slice with visual probability bars and top pick highlights.

- **Section 4 – Interactive Simulation (Hand-crafted)**:
  - Add, edit, or remove custom tokens and probabilities.
  - Built-in presets to observe how unexpected or low-probability words affect total perplexity.

## Tech Stack

- Standalone HTML5, CSS3, and JavaScript (ES Modules).
- Zero build tools, zero dependencies, no API keys or backend required.
