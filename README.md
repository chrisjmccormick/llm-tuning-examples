# Example Code For Fine-Tuning LLMs

The current emphasis for this project is on examples of fine-tuning with a **single GPU**, ideally in Colab.

Many example code tutorials imply that this is doable, but it's felt unclear to me about what's really being achieved by the example and how, and what the caveats might be. 

I wanted to **gather** these tutorials, port them to **Colab** where needed, comb through them and **add my own comments**, and summarize important details such as:

* Which **techniques** are applied and why (and which aren't?).
* What the **actual task** is we're training on (and some detail on the dataset).
* Important parameters related to **fitting** on a single GPU, such as:
    * Model choice and size (i.e., parameter count).
    * What GPU they ran on.
    * What training parameters they used (particularly batch size and sequence length!).
* The **runtime**--how long you can expect the example to take.
* What **performance measure** they used and how much they gained through tuning.
* Were any special **libraries** used outside of HuggingFace, and what was the impact.
* Finally, in summary, what would I say are the **strengths** and **caveats** of the example.

The landscape of libraries and techniques is bewildering, so this project has / is spawning a number of written tutorials from me, which I'll link to.
