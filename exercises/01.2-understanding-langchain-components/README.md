---
readingTime:
  minutes: 2.396
  words: 599
fkglResult: 9.85
---

# 01.2 Understanding LangChain Components

LangChain is built around several key components that work together to create powerful applications powered by large language models (LLMs). In this lesson, we'll explore the three main components: **Chains**, **Agents**, and **Memory**. Understanding how these pieces fit together will help you design and build your own LangChain applications.

---

## 1. Chains: The Building Blocks

A **Chain** is a sequence of operations that process input and generate output. Think of it as a pipeline where each step transforms data or calls a language model with a prompt.

- **SimpleChain**: The most basic chain that takes input, runs it through an LLM, and returns the output.
- Chains can be combined to create more complex workflows.

**Example:** A chain that summarizes a tweet thread by sending a prompt to the LLM.

```python
from langchain.llms import OpenAI

llm = OpenAI(temperature=0)

def summarize_chain(input_text):
    prompt = f"Summarize this tweet thread: {input_text}"
    return llm(prompt)
```

---

## 2. Memory: Keeping Context

**Memory** allows your application to remember previous interactions, enabling context-aware conversations.

- **ConversationBufferMemory** stores the chat history.
- Memory can be passed to chains or agents to maintain state across multiple inputs.

This is essential for chatbots or any app where context matters.

---

## 3. Agents: Intelligent Decision Makers

An **Agent** uses an LLM as its "brain" to decide which actions to take, often by using **Tools**.

- Tools are functions or APIs the agent can call to fetch information or perform tasks.
- Agents combine tools and memory to interact dynamically with users and external data.

**Example:** An agent that fetches the latest tweets about a topic and remembers the conversation.

```python
def fetch_latest_tweets(query):
    # Imagine this calls Twitter API and returns tweets
    return f"Fetched tweets about {query}"

from langchain.agents import AgentExecutor, Tool
from langchain.memory import ConversationBufferMemory

memory = ConversationBufferMemory(memory_key="chat_history", return_messages=True)

tools = [Tool(name="FetchTweets", func=fetch_latest_tweets, description="Fetch latest tweets based on a query")]

agent = AgentExecutor.from_agent_and_tools(
    agent=llm,  # Using LLM as the agent's brain
    tools=tools,
    memory=memory,
    verbose=True
)

user_input = "LangChain updates"
response = agent.run(user_input)

summary = summarize_chain(response)
print("Summary of fetched tweets:", summary)
```

---

## How These Components Work Together

The user input flows into the **Agent**, which uses its **Tools** and **Memory** to fetch data and maintain context. The output from the agent can then be passed through a **Chain** for further processing, such as summarization.

This modular design allows you to build complex applications by combining simple, reusable parts.


![GENERATING: Diagram showing the flow from user input to agent with tools and memory, then to a chain for summarization, with arrows indicating data flow and labeled components](/.learn/assets/qrztaerujwn)

---

## Summary

- **Chains** process inputs and outputs in a sequence.
- **Memory** stores conversation history to maintain context.
- **Agents** use LLMs and tools to decide actions dynamically.
- Together, they enable powerful, context-aware language applications.

---

## Your Turn: Code Challenge Proposal

```code_challenge_proposal
In this exercise, you will create a LangChain application that integrates the three components: chains, agents, and memory.

You will:
- Implement a simple chain that processes text input.
- Define a tool function that simulates fetching data (e.g., news headlines).
- Set up conversation memory to keep track of user inputs.
- Create an agent that uses the tool and memory to respond to user queries.
- Chain the agent's output to the simple chain for additional processing (e.g., summarization).

The main file will be app.py, containing the skeleton code with placeholders for each component.

This hands-on exercise will solidify your understanding of how LangChain components interact.
```

---

Keep experimenting with these components to build your own intelligent applications!