## Summary & Status

This is a commented version of this Notebook from Unsloth:

[Mistral 7b Text Completion - Raw Text training full example.ipynb](https://colab.research.google.com/drive/1ef-tab5bhkvWmBOObepl1WgJvfvSzn5Q?usp=sharing)

It which demonstrates how to train an LLM on raw text in order learn a particular writing style. Specifically–we train on “tiny stories”(only a couple paragraphs long) which use a 4-year old’s vocabulary.


**Status**

_2025-01-18_

- The Notebook is complete and runs. 
- I’m still going through publishing and clean up

**Getting Started**

You can simply read through the Notebook like a blog post, but if you’d like to run it, you’ll need:

* A HuggingFace account so that you can create a “token”
* To accept the Mistral license on the hf model hub.

The Notebook will run in Colab on a free T4 GPU.

## Key Qualities

**Task & Approach**

* Next-token Prediction on the TinyStories dataset. 
* After training, prompt the model with “A long time ago, in a galaxy far, far away,” to have it continue writing a tiny children’s story.

**Effectiveness of Tuning**

* Training on 2,500 samples was enough to get the model to adopt the writing style.

**Libraries Used**

The Notebook uses Unsloth classes that are based on the HuggingFace TRL library:

* e.g., instead of `SFTTrainer` we are using `UnslothTrainer`

## GPU Requirements

_Does it run on the Free T4?_

* Yes, this Notebook will run on a free T4 in Colab.
* The current outputs in the Notebook are from running on an A100.

