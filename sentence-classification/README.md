## Summary & Status

This Notebook demonstrates how to fine-tune an LLM for a more “traditional” NLP task of classification. Specifically, we’ll work with a dataset of short sentences where the goal is to label them as grammatically “acceptable” or “unacceptable”.

Even though we’ll be training the model on a dataset, we’ll see how much more effective the fine-tuning process is when you include a prompt with some examples. 

It implements an approach to classifying an LLM where we’ll rely on the LM head and choose a the “label word” with the highest confidence.

**Status**

The Notebook is complete! 

As of 10/20/24, I’m still going through my process for publishing and announcing it.

**Getting Started**

You can simply read through the Notebook like a blog post, but if you’d like to run it, you’ll need:

* A HuggingFace account so that you can create a “token”
* To accept the Llama 3 license on the hf model hub.

(You can find the instructions for this in the Notebook)

The Notebook will run in Colab on a free T4 GPU.

## Key Qualities

**Task & Approach**

* Sentence classification on the CoLA dataset
* Uses examples in the prompt, fine-tunes the model, and uses the LM head for classification (rather than adding a linear classifier).

**Effectiveness of Tuning**

* I can’t say that I did a full “benchmark” on different approaches because I only spent so much time on trying to optimize different methods. 
* But anecdotally, I found:
    * I figured that feeding the task to **GPT-4** via the OpenAI APIs would provide both the simplest and highest accuracy approach, but no–it didn’t “crush” the alternatives. 
    * Using an encoder model for this task–like **RoBERTa-large** was at least as effective as fine-tuning (the much larger) Llama 3.

**Libraries Used**

The Notebook uses HuggingFace transformers to load and implement the model, but doesn’t use the Trainer class. It implements the training loop in PyTorch so you can see all of the details of that.

## GPU Requirements

_Does it run on the Free T4?_

* Yes, this Notebook will run on a free T4 in Colab.
* The current outputs in the Notebook are from running on a T4.
* Check out the table below summarizing the requirements for getting it to fit on a T4, and how that compares to running on an A100 (40GB, $1.17/hr)). 

_Observations_

* Using AdamW8bit saved about 1GB of memory use and improved the test score from 0.642 to 0.647 (vs. AdamW on the A100).

|                                | T4                         | A100                       |
|--------------------------------|----------------------------|----------------------------|
| Memory Use (w/ below settings) | 14.7GB / 14.8 GB           | 15.7GB / 39.6GB            |
| Training Time                  |                    0:35:40 |                    0:10:48 |
| Test Score                     |                      0.647 |                      0.642 |
| Sequence Length                |                         86 |                         86 |
| Effective Batch Size           |                          8 |                          8 |
| GPU Batch Size                 |                          8 |                          8 |
| Gradient Checkpointing         | No                         | No                         |
| Optimizer                      | AdamW8bit                  | AdamW                      |
| LoRA                           | r=8, alpha=16, all modules | r=8, alpha=16, all modules |
| Model                          | Llama 3 8B                 | Llama 3 8B                 |
| Quantization                   | 4-bit                      | 4-bit                      |
