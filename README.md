# Academic Text Humanizer with Length Control

## Overview

This project implements a fine-tuned Llama 3.1 8B model specialized in humanizing academic text while preserving LaTeX mathematical expressions and maintaining precise length control. The model converts stiff, AI-generated, or overly formal academic writing into natural, fluent English suitable for research papers, theses, and scholarly documents.

## Key Features

- **LaTeX Preservation**: Automatically masks and restores mathematical formulas, citations, and LaTeX commands during processing
- **Length Control**: Precise output length management with ratios from 0.8x to 1.2x relative to input text
- **Academic Focus**: Optimized for research writing, maintaining scholarly tone and terminology
- **Efficient Inference**: Uses 4-bit quantization for fast, memory-efficient text processing
- **Web Interface**: Includes a Gradio-based UI for easy interaction

## How It Was Built

### 1. Base Model

| Property | Details |
|----------|---------|
| **Model** | Llama 3.1 8B (unsloth/llama-3.1-8b-bnb-4bit) |
| **Framework** | Unsloth for efficient fine-tuning |
| **Quantization** | 4-bit quantization to reduce memory usage |

### 2. Dataset Preparation

- **Source**: Hugging Face `humarin/chatgpt-paraphrases` dataset (50,000 samples)
- **Processing**:
  - Calculated length ratios between original and paraphrased text
  - Added special tokens `<len_0.8>` through `<len_1.2>` for length control
  - Formatted as instruction-response pairs for supervised fine-tuning

### 3. Fine-Tuning Process

| Parameter | Value |
|-----------|-------|
| **Method** | LoRA (Low-Rank Adaptation) with rank 16 |
| **Training Steps** | 500 steps with batch size 16 |
| **Hardware** | Optimized for T4 GPU (Colab), ~1–2 hours training time |
| **Final Loss** | ~0.4 |
| **Packing** | Enabled sequence packing for 2x training speed |

### 4. Special Features Implementation

- **LaTeX Masking**: Advanced regex patterns to identify and protect mathematical content
- **Length Constraint Decoding**: Dynamic max token limits based on target ratios
- **Temperature Sampling**: 0.7 with top-p 0.9 for natural text generation

### 5. Export and Deployment

- **GGUF Export**: Converted to 4-bit GGUF format for local inference
- **Ollama Integration**: Created Modelfile for easy Ollama deployment
- **Gradio Interface**: Web-based UI with slider controls for length adjustment

## Model Download

Download the trained model (GGUF format) from this Google Drive link:

**[INSERT DRIVE LINK HERE]**

The model file is: `humanizer_gguf/unsloth.Q4_K_M.gguf`

## Usage

### Option 1: Run the Jupyter Notebook

1. Open `Academic_Humanizer.ipynb` in Google Colab or Jupyter
2. Install dependencies:
   ```bash
   pip install -q unsloth[colab-new] xformers trl peft accelerate bitsandbytes datasets gradio
   ```
3. Run the inference cells to test the model
4. Launch the Gradio interface for interactive use

### Option 2: Local Ollama Deployment

1. Install Ollama from https://ollama.ai/
2. Download the GGUF model from the Drive link above
3. Create a `Modelfile` with the following content:
   ```
   FROM ./humanizer_gguf/unsloth.Q4_K_M.gguf
   PARAMETER temperature 0.7
   PARAMETER top_p 0.9
   PARAMETER stop "<|eot_id|>"
   PARAMETER stop "<|start_header_id|>"
   PARAMETER stop "<|end_header_id|>"

   TEMPLATE """
   <|begin_of_text|><|start_header_id|>system<|end_header_id|>
   Humanize the following text while strictly preserving LaTeX and formatting. Match the requested length ratio (0.8x to 1.2x).<|eot_id|>
   <|start_header_id|>user<|end_header_id|>
   {{{ .Prompt }}}<|eot_id|>
   <|start_header_id|>assistant<|end_header_id|>
   """

   SYSTEM """You are a professional academic humanizer. You convert AI-generated or stiff text into natural, fluent English. You must never change LaTeX math ($...$), citations, or references."""
   ```
4. Run:
   ```bash
   ollama create academic-humanizer -f Modelfile
   ```
5. Use:
   ```bash
   ollama run academic-humanizer
   ```

### Option 3: Python API

```python
from unsloth import FastLanguageModel
import torch

# Load model
model, tokenizer = FastLanguageModel.from_pretrained(
    model_name="path/to/saved/model",  # Use local path or Hugging Face repo
    max_seq_length=2048,
    dtype=None,
    load_in_4bit=True,
)

# Humanize text
def humanize_text(text, ratio=1.0):
    # Implementation from notebook
    pass
```

## Example

**Input (Stiff Academic Text):**
```
The implementation of the proposed algorithm facilitates a significant reduction in
computational overhead, especially when processing high-dimensional datasets within
a distributed framework as shown in \cite{paper2024}.
```

**Output (Humanized, 1.0x ratio):**
```
Our algorithm significantly cuts down on computing costs, particularly when handling
complex, high-dimensional data in distributed systems, as demonstrated in \cite{paper2024}.
```

## Performance Metrics

| Metric | Value |
|--------|-------|
| **Training Time** | ~90 minutes on T4 GPU |
| **Model Size** | ~4.5 GB (4-bit quantized) |
| **Inference Speed** | ~20–30 tokens/second on consumer GPU |
| **Length Accuracy** | ±5% of target ratio |
| **LaTeX Preservation** | 100% (tested on academic papers) |

## Future Scope

### Multi-Tone Support

- **Professional**: Current implementation (formal academic)
- **Informal**: Casual, conversational academic writing
- **Technical**: Highly specialized jargon for specific fields
- **Educational**: Simplified explanations for students
- **Review-Style**: Critical analysis tone for literature reviews

### Advanced Features

- **Domain Adaptation**: Fine-tune for specific academic fields (CS, Biology, Physics, etc.)
- **Citation Style Control**: Automatic APA/MLA/Chicago formatting
- **Multi-Language Support**: Extend to other academic languages
- **Quality Metrics**: Integrated BLEU/ROUGE scoring for output assessment
- **Batch Processing**: Handle multiple documents simultaneously
- **API Service**: Deploy as REST API for integration with writing tools

### Technical Improvements

- **Larger Base Models**: Scale to 70B+ parameters for better quality
- **Reinforcement Learning**: Use RLHF for tone and quality preferences
- **Hybrid Approaches**: Combine with smaller specialized models
- **Real-time Collaboration**: Integration with Overleaf/Google Docs

## Dependencies

- Python 3.8+
- PyTorch 2.0+
- Transformers 4.30+
- Unsloth
- PEFT
- BitsAndBytes
- Datasets
- Gradio
- Accelerate

## License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

## Contact

For questions or collaborations, feel free to reach out!

📧 **vpscholachetan24@gmail.com**
