---
readingTime:
  minutes: 1.144
  words: 286
fkglResult: 12.59
---

# 01.1 Setting Up Your LangChain Environment

Before you start building powerful applications with LangChain, it's essential to set up a clean and organized development environment. This helps keep your project dependencies isolated and manageable, just like professional developers do.

## Step 1: Create a Python Virtual Environment

A **virtual environment** allows you to create an isolated space for your LangChain project, preventing conflicts with other Python packages on your system.

Open your terminal and run the following commands:

```bash
python3 -m venv langchain-env
source langchain-env/bin/activate  # On Windows use: langchain-env\Scripts\activate
```

- The first command creates a new virtual environment named `langchain-env`.
- The second command activates this environment so that any Python packages you install will be contained within it.

## Step 2: Install LangChain

With your virtual environment activated, install LangChain using pip:

```bash
pip install langchain
```

This command downloads and installs the latest LangChain package and its dependencies.

## Step 3: Verify Your Installation

To make sure everything is set up correctly, create a simple Python script named `test_langchain.py` with the following content:

```python
from langchain import LLMChain

print("LangChain imported successfully!")
```

Run the script in your terminal:

```bash
python test_langchain.py
```

If you see the message **LangChain imported successfully!** without any errors, your environment is ready!

## Optional: Install IPython for Interactive Development

For a better coding experience, you can install **IPython**, an enhanced interactive Python shell:

```bash
pip install ipython
ipython
```

Inside IPython, you can quickly test LangChain imports and experiment with code snippets interactively.

---

Setting up your environment properly is the first step toward building amazing applications with LangChain. In the next lessons, you'll start creating chains and integrating APIs using this setup.

Happy coding! 🚀