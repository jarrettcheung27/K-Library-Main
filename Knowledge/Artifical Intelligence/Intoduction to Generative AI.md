## **LLM(Large Language Model)**
### **Foundational Model**
GPT
Codex
Calude
BERT
...
### **Specified Model**
Once a foundational model is trained, it can be adapted to a wide range of down- stream tasks by fine-tuning its parameters.

### **Transformer architecture**
Transformers are the bedrock of foundational models and are responsible for their remarkable language understanding capabilities.In the context of generative AI, a transformer model would take an input (such as a prompt) and generate an output (such as the next word or the completion of the sentence) by weighing the importance of each part of the input in generating the out- put. 
### **Architecture of a LLM Implementation**

![Pasted image 20250405163352.png](Pasted%20image%2020250405163352.png)
 It is first converted into a sequence of tokens using tokenization. Each token is then converted into a numerical vector via a process called embedding, which acts as the encoder input.
 The encoder processes the input sequence and generates a sequence of hidden states. These hidden states are then fed into the decoder with a start token. The decoder generates the output sequence one token at a time by predicting the next token based on the previous tokens and hidden states. Once all the layers have processed the information, the model predicts the next token in the learned sequence. This outcome is converted back to the text, and we see the response. This process runs in an iterative loop and occurs for each new token generated, thus creating a coherent text output. The final text that the model generates is an emergent property of this layered, iterative process. The final output sequence is also called a completion.
### Model configuration
1) Max Response
	The parameter known as max response essentially defines the upper limit for the text length that the model generates. 
2) Temperature
	 Temperature is one of the most import- ant settings for controlling the degree of the model’s randomness. Typically, this is a value from 0 to 1, with 0 representing a more accurate and predictable output. In con- trast, setting a 1 makes the output more diverse and random.
3) Top Probability
	This parameter allows one to fine-tune the balance between creativity and reliability in the text that the model generates. 
4) Frequency penalty 
	This reduces the chance of repeating a token proportionally based on how often it has appeared in the text. This decreases the likelihood of repeating the same text in response.
5) Presence penalty
	This reduces the chance of repeating any token that has appeared in the text so far. This increases the likelihood of introducing new topics in a response.
## Prompt Engineering
*Foundational models such as the GPT series are trained on large amounts of data, distilling much knowledge. To make such large models useful for tasks that we are trying to solve, we need to steer them in a certain direction, and prompt engineering allows us to do that.*

[Generative AI Prompt Design](Generative%20AI%20Prompt%20Design.md)

### How to make a good prompt?
1. Clear Instructions
	- Heading and subheadings—Use headings and bullet points to organize your prompt into sections and subsections. For example, you can follow the mark- down file syntax and use #, ##, or ### to create headings and - or * to create bul- let points.
	-  One of the best practices is to have important information up front in the prompt and then repeat it at the end. 
2. Adopt a persona
3. Specify the format
4. Avoid leading the answer
5. Limit the scope
6. Tone
Telling the model what you want to do before you provide any other details produces higher-quality results. 

### Avoid hallucinating
 If a model cannot complete a task, give it an alternative exit path. For example, including something similar to “respond with ‘not found’ if the answer is not present” will minimize the probability of the model hallucinating.

## Retrieval-augmented generation(RAG)
***RAG** is a method that combines additional data with a language model’s input to improve its output without altering the initial prompt*.
![Pasted image 20250406143531.png](Pasted%20image%2020250406143531.png)


### Vector search engine
- **FAISS**: **FAISS** 全称是 **Facebook AI Similarity Search**，是由 Facebook（现在的 Meta）开发的一个**高效相似度搜索库**，专门用于在大规模向量集合中快速查找与查询向量最相似的向量。

## Maximal Marginal Relevance(MMR)
To select some less relevant item when retrieving data using RGA.
