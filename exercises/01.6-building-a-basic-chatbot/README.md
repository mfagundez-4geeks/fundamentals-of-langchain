---
readingTime:
  minutes: 2.948
  words: 737
fkglResult: 10.92
---

# 01.6 Building a Basic Chatbot

Conversational AI is everywhere—from virtual assistants to customer support bots. A key feature that makes chatbots feel natural is their ability to remember previous interactions and maintain context. In this lesson, you'll learn how to build a basic chatbot using LangChain that keeps track of conversation history using memory.

## Why Use Memory in Chatbots?

Without memory, a chatbot treats every message as a new, isolated input. This leads to disjointed conversations. Memory allows the bot to recall past messages, enabling it to respond more coherently and personalize interactions.

## Key LangChain Components for Chatbots

- **ConversationChain**: A chain designed specifically for conversational applications. It connects a language model with memory to handle dialogue.
- **ConversationBufferMemory**: Stores the entire conversation history in a buffer, allowing the bot to reference all previous exchanges.
- **OpenAI LLM Wrapper**: The language model that generates responses based on prompts and memory.

## Building the Chatbot: Step-by-Step

```python
# Import necessary LangChain classes
from langchain.chains import ConversationChain
from langchain.memory import ConversationBufferMemory
from langchain.llms import OpenAI

# Initialize the language model with low temperature for consistent responses
llm = OpenAI(temperature=0)

# Set up conversation memory to store chat history
memory = ConversationBufferMemory()

# Create a conversation chain with memory
conversation = ConversationChain(llm=llm, memory=memory)

# Example interaction loop simulating user inputs
user_inputs = [
    "Hi, I'm looking for a good sci-fi book.",
    "I really enjoyed Dune. Any recommendations?",
    "Thanks! Can you remind me what you suggested earlier?"
]

for user_input in user_inputs:
    response = conversation.run(user_input)
    print(f"User: {user_input}")
    print(f"Bot: {response}\n")
```

### How This Works

- The **ConversationBufferMemory** keeps track of all previous messages.
- Each time `conversation.run()` is called, the bot uses the entire conversation history to generate a context-aware response.
- This allows the bot to remember earlier topics and refer back to them, making the chat feel natural.

### Experimentation Ideas

- Try changing `ConversationBufferMemory` to other memory types like `ConversationSummaryMemory` for longer chats.
- Add user preferences to memory to personalize recommendations.
- Adjust the `temperature` parameter to make responses more creative or deterministic.

## Visualizing the Chatbot Flow

![GENERATING: A detailed diagram illustrating the flow of a LangChain chatbot using ConversationChain and ConversationBufferMemory. The diagram shows numbered steps: 1) User sends input, 2) Input and conversation history are combined by ConversationBufferMemory, 3) The combined prompt is sent to the OpenAI language model, 4) The model generates a response considering the full context, 5) Response is returned and displayed to the user. Arrows indicate data flow, and components are color-coded to differentiate memory, model, and user interaction. Annotations highlight how memory enables context retention and improves chatbot coherence.](/.learn/assets/i27ffndbp2l)

## Summary

- Chatbots need memory to maintain context and have meaningful conversations.
- LangChain's **ConversationChain** combined with **ConversationBufferMemory** enables easy chatbot creation.
- The language model generates responses based on the entire conversation history.
- Experimenting with different memory types and parameters can enhance chatbot behavior.

---

### Test Your Understanding

Select the correct answer for each question.

1. What is the role of **ConversationBufferMemory** in a LangChain chatbot?

   - [ ] It generates responses based on user input.
   - [x] It stores the entire conversation history to provide context.
   - [ ] It connects the chatbot to external APIs.
   - [ ] It controls the creativity of the language model.

2. What happens if you do not use memory in a chatbot?

   - [ ] The chatbot will remember all previous conversations.
   - [x] The chatbot treats each message independently without context.
   - [ ] The chatbot will automatically personalize responses.
   - [ ] The chatbot will crash after the first message.

3. How does the **temperature** parameter affect the chatbot's responses?

   - [ ] It controls the speed of response generation.
   - [ ] It determines the length of the response.
   - [x] It adjusts the creativity or randomness of the output.
   - [ ] It sets the maximum number of conversation turns.

4. Which LangChain component combines the language model and memory for conversation?

   - [ ] PromptTemplate
   - [ ] OpenAI
   - [x] ConversationChain
   - [ ] LLMChain

5. To personalize chatbot recommendations based on user preferences, you should:

   - [ ] Use ConversationBufferMemory only.
   - [ ] Increase the temperature to 1.0.
   - [x] Store user preferences in memory and use them in prompts.
   - [ ] Remove memory to simplify the chatbot.


[Ask Rigo how does ConversationBufferMemory work in LangChain chatbots](https://4geeks.com/ask?query=how-does-conversationbuffermemory-work-in-langchain-chatbots)

