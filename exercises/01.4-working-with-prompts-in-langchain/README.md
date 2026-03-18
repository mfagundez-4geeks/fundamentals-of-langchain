---
readingTime:
  minutes: 2.14
  words: 535
fkglResult: 10.21
---

# 01.4 Working with Prompts in LangChain

Have you ever wanted your language model to respond differently depending on the situation or user input? That's where **prompt templates** come in handy! They let you create flexible prompts that adapt dynamically to different inputs, making your applications smarter and more personalized.

## What is a PromptTemplate?

In LangChain, a **PromptTemplate** is a way to define a prompt with placeholders (variables) that you can fill in later with actual data. This separation of prompt structure and input data helps you reuse prompts easily and keep your code clean.

## Creating a Dynamic Prompt

Let's look at an example where we build a prompt for a social media assistant. This assistant generates friendly responses based on user actions on different platforms.

```python
from langchain.prompts import PromptTemplate

# Define a prompt template with variables for dynamic content
prompt = PromptTemplate(
    input_variables=["platform", "user_action"],
    template="""
You are a social media assistant. When a user performs the action '{user_action}' on {platform}, generate a helpful and friendly response.

Example:
User action: 'likes a post'
Response: 'Thanks for liking the post! Check out more content you might enjoy.'

Now, respond to this action:
User action: '{user_action}'
Response:
"""
)

# Example usage with dynamic inputs
inputs = {
    "platform": "Instagram",
    "user_action": "comments on a photo"
}

# Generate the final prompt string
final_prompt = prompt.format(**inputs)

print(final_prompt)
```

### How This Works

- **input_variables**: These are the placeholders in your prompt that will be replaced with actual values.
- **template**: The prompt text with placeholders wrapped in curly braces `{}`.
- **format()**: This method fills in the placeholders with the values you provide.

## Why Use PromptTemplate?

- **Reusability**: Write your prompt once and reuse it with different inputs.
- **Maintainability**: Keep your prompt logic separate from your data.
- **Flexibility**: Easily customize prompts for different scenarios.

## Try It Yourself!

- Change the `platform` and `user_action` values to see how the prompt adapts.
- Create a prompt template for a Twitter bot that responds to mentions, including variables like username and mention content.
- Experiment with adding conditional instructions inside your prompt to guide the model's behavior.

## Summary

- **PromptTemplate** helps you create dynamic prompts with placeholders.
- Use **input_variables** to define what parts of the prompt will change.
- The **format()** method fills in these variables with actual data.
- This technique is essential for building flexible and maintainable LangChain applications.


### Test Your Understanding!

Explain in your own words what a PromptTemplate is and why it is useful in LangChain applications.

```question eval="The user needs to explain that a PromptTemplate is a prompt with placeholders for variables that can be filled dynamically, allowing reuse and customization of prompts in LangChain applications."
CORRECT: A PromptTemplate is a prompt with variables that can be replaced with different inputs to create dynamic prompts.
CORRECT: It allows you to reuse the same prompt structure with different data, making your code more flexible.
INCORRECT: It's a fixed prompt that cannot be changed.
INCORRECT: It is a function that runs the language model.
CORRECT: PromptTemplate separates the prompt text from the input data, helping to customize responses easily.
INCORRECT: It is used to store conversation history.
```
