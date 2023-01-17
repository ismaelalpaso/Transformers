# Transformers

Transformer architectures are a type of neural network used in natural language processing (NLP) and other language-related tasks. They are characterized by their ability to handle input sequences of variable length and their use of attention, which allows the network to focus on relevant parts of the input similar to when humans grasp the meaning of sentences. 

The original Transformer model was presented in 2017 significantly improving the capabilities of recurrent networks, used until then for NLP. Transformer models has been improved and adapted for a variety of tasks and applications since then. 

The model consists of repeating an encoding and decoding structure n times:

- Encoder: The encoder is made up of a stack of $n$ identical layers. Each layer has two sublayers. The first is a multi-head self-service mechanism, and the second is a fully connected network.
  We use a residual connection around each of the two sublayers, followed by a normalization layer. In other words, the output of each sublayer is $LayerNorm(x + Sublayer(x))$, where $Sublayer(x)$ is the function implemented by the sublayer itself. To facilitate the creation of these residual connections, all sublayers of the model, as well as the embedding layer, produce outputs of dimension $d_{model}$ .
  
- Decoder: The decoder is also made up of a stack of $n$ identical layers. In addition to the two sublayers in each encoder layer, the decoder inserts a third sublayer, which performs **multi-head attention** on the output of the encoder stack. Similar to the encoder, we employ residual connections around each of the sublayers, followed by layer normalization. 
  The autoattention sublayer in the decoder stack is modified to prevent positions from paying attention to subsequent positions. This masking, combined with the fact that output embeddings are offset by one position, ensures that predictions for position $i$ can depend only on known outputs at positions less than $i$ so that the model cannot use future data.
  
![image](https://user-images.githubusercontent.com/114246096/212961994-f311712b-3448-4967-9197-1167e1b15e02.png)


An attention function can be described as mapping a query $Q$ and a set of key-value $K, V$ pairs to an output, where the query, keys, values, and output are all vectors. The output is computed as a weighted sum of the values, where the weight assigned to each value is computed by a compatibility function of the query with the corresponding key.

![image](https://user-images.githubusercontent.com/114246096/212970402-ee348458-cb5f-4183-bc21-de9c2185bf85.png)






You can find the complete paper and references on https://arxiv.org/pdf/1706.03762.pdf
