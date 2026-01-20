We developed this project, a GPT-style Transformer model, using PyTorch for the WIDS 5.0 Final Project. The focus is on providing a deeper and more practical understanding of how GPT and ChatGPT Architecture work by creating all of their key components from scratch without utilising any existing libraries of Transformer architecture.

The GPT-style Transformer model was designed to work at the character level and was trained using a large number of plain text sample datasets. The model predicts the next character in a given input sequence using a self-attention mechanism with a mask applied to the self-attention mechanism, allowing generation of text one character at a time.

There are several key features of this project:

- The Transformer is decoder-only architecture
- Created as an autoregressive language model at the character level
- A manual implementation of the self-attention mechanism using the Query, Key, Value approach
- A causal mask has been implemented to prevent the decoder from looking at any future tokens while generating text
- The multi-head attention mechanism
- The feed-forward part of the network (the neural networks) has been created using a non-linear activation function
- Each component in the model has been designed with a Residual connection and Layer Normalization added, providing a smoother learning curve for the neural network
- Positional embeddings provide an additional method for encoding the relative order of sequences
- All of these features worked together to provide a single file (gpt.py) for both end-to-end training of the model and for generating new text.

The model architecture consists of a series of Transformer encoder blocks that are configured in a sequential manner, which is typical for the GPT architecture. Each input character is transformed into a dense embedding vector by the token embedding table, and the order of the characters in the sequence is retained by adding a positional embedding.

Once these two embeddings have been created for each character, they are combined and input to multiple Transformer encoder blocks. Each Transformer block consists of masked multi-head self-attention followed by a feed-forward neural network. The residual connection and layer normalization are added around each sub-layer of the transformer encoder block to enable stable and effective training.

The final hidden representations from the transformer encoder blocks are normalized and fed into a linear layer that outputs a vocabulary logits. The result is a probability distribution over the next character.

The training data is a plain text file that contains samples from the collected works of William Shakespeare (public domain). The file is approximately 1.1MB in size. The training and validation data was created from the same text file and divided by a ratio of 90:10, to allow the model to evaluate how well it generalizes from training data to unseen data during training.

The PyTorch deep learning framework was used to train the models using the AdamW optimizer and a loss function of Cross Entropy Loss.

There are approximately 4000 training iterations for each model, a batch size of 32, a context length (block size) of 64, a learning rate of 3e-4, and a dropout rate of 0.2.

Every few iterations, the losses incurred while training and validating are printed to the console so that users can monitor progress and detect the possibility of overfitting.

Result & observation:

- Training Loss at End: 1.89 Approximated
- Validation Loss at End: 1.97 Approximation

The loss in validation meets the stated goals from the project guide, indicating that the model has been trained on realising meaningful linguistic constructions. Appropriate English words, sentences and dialogue have appeared according to expectations of such a character based Transformer, which was trained entirely from random weights on the initial network’s architecture.

Generation of Text Using Model:

Model generates text behaved like a traditional autoregressive model, immediately sampling based on predicted probabilities of the next character. Output is the combination of some level of random temperature values which balance between coherence of output, and randomly generated output will still be usable as coherent text or something resembling the actual text was based on sampled characters and words of English. While generated sentences may not represent grammatical correctness in all cases, they consistently display a version of a proper sentence with exact Capitalization and Word-like elements.

Contents inside Repo:

- gpt.py – Complete Version of GPT Decoder Only Character Level Transformer
- data.txt – Text file containing all training data
- README.md – Documentation regarding the Project
- Screenshot 1 & 2 - Training Logs Final Train Validation Loss Outputs and Completed Generated Text Outputs

What have I learned?

- Through my work on this project I believe I have:
- A Very Good Understanding of Transformer Architecture and Internally Structured Self-Attention Models
- How to A Model Like Autoregressive Behaviour
- Limits of a Learning Rate
- How to Build Deep Learning Models from the Ground-Up
- My work on this project allows for learning experiences to the user when building API driven Applications.

