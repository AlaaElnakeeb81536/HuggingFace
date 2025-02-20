### LLM

- Large Language Models are AI models trained on vast amounts of text data to understand and generate human-like text.

- They use transformer architectures (like GPT, BERT, etc.) to process and generate text.

- Applications: Text generation, summarization, translation, question answering, chatbots, and more.
  
![image](https://github.com/user-attachments/assets/7533b29f-8c0a-4d8e-8e54-8c5d3a02cd85)

# There are several frameworks and libraries for working with LLMs. 
**The most popular ones are:**

1- Hugging Face Transformers: A library that provides pre-trained models and tools for NLP tasks.

2- OpenAI API: Provides access to powerful LLMs like GPT-3 and GPT-4 via an API.

3- LangChain: A framework for building applications with LLMs, including chatbots and agents.


**Start with a simple example using Hugging Face Transformers :**

- [Text Generation](https://github.com/AlaaElnakeeb81536/Hugging-Face/blob/main/HuggingFace/Text_Generation_.ipynb) : gpt2, facebook/opt-1.3 Check out this on GitHub:  

- [Summarization](https://github.com/AlaaElnakeeb81536/Hugging-Face/blob/main/HuggingFace/Text_Summarization_.ipynb) : facebook/bart-large-cnn

- [Translation](https://github.com/AlaaElnakeeb81536/Hugging-Face/blob/main/HuggingFace/Text_Translation_.ipynb) : Helsinki-NLP/opus-mt-en-fr

# Fine-Tune a Model.
 
If you have a specific use case, you can fine-tune a pre-trained model on your own dataset.

![image](https://github.com/user-attachments/assets/0d4d0ee6-5663-4bb1-b6d4-ec689ec05ad8)

# Steps for Fine-Tuning

## 1. Choose a Pre-Trained Model  
Select a model from a library like Hugging Face (e.g., `bert-base-uncased`, `gpt2`, etc.).  

**Example:**  
```python
from transformers import AutoModelForSequenceClassification, AutoTokenizer

model_name = "bert-base-uncased"
model = AutoModelForSequenceClassification.from_pretrained(model_name)
tokenizer = AutoTokenizer.from_pretrained(model_name)
```
## 2. Prepare Your Dataset
Use tools like Hugging Face's datasets library to load and preprocess data.

### 3. Define the Training Setup
Use a framework like Hugging Face's Trainer or PyTorch's DataLoader to define the training process

**Example:**  
```python
from transformers import TrainingArguments, Trainer

training_args = TrainingArguments(
    output_dir="./results",
    evaluation_strategy="epoch",
    save_strategy="epoch",
    per_device_train_batch_size=8,
    per_device_eval_batch_size=8,
    num_train_epochs=3
)

trainer = Trainer(
    model=model,
    args=training_args,
    train_dataset=dataset["train"],
    eval_dataset=dataset["test"]
)

trainer.train()
```
Applications:
[Sentiment Analysis](https://github.com/AlaaElnakeeb81536/Hugging-Face/blob/main/FineTunning_on_imdb(SentimentAnalysis).ipynb)

-------------------------------
### Langchain

### Why Use LangChain?
- **Simplify Complex Applications**: LangChain provides tools to build complex applications powered by large language models (LLMs).
- **Prompt Management**: LangChain makes it easier to manage prompts using **Prompt Templates**.
- **Memory Support**: LangChain supports memory for interactive applications like chatbots.
- **Integration with External Tools**: LangChain integrates with databases, APIs, and other tools.

### When Not to Use LangChain?
- **For Simple Applications**: If you're building a simple application that doesn't require complex interactions.
- **To Reduce Dependencies**: If you want to minimize the number of libraries in your project.
- **For Basic Tasks**: If you're performing simple tasks like text generation or translation.

### Memories Of langchain:
  
**1- ConversationBufferMemory**
- Stores the full conversation history.
- Useful when keeping track of past interactions is necessary for context.

**2- ConversationBufferWindowMemory**

- Retains only the last K interactions.
- Ideal for chatbots needing short-term memory without excessive storage.

**3- ConversationSummaryMemory**

- Summarizes past interactions instead of storing them entirely.
- Helps maintain context efficiently for long conversations.


**4-ConversationTokenBufferMemory**

This memory type retains conversation history up to a specified number of tokens, ensuring that the memory doesn't exceed the token limit of the model
  
 **For detailed code examples, check the full notebook [LangchainMemories](https://github.com/AlaaElnakeeb81536/HuggingFace/blob/main/LangChain/LangChainMemories.ipynb).**

