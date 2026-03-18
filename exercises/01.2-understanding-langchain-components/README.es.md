---
readingTime:
  minutes: 2.396
  words: 599
fkglResult: 9.85
---

# 01.2 Entendiendo los Componentes de LangChain

LangChain está construido alrededor de varios componentes clave que trabajan juntos para crear aplicaciones potentes impulsadas por grandes modelos de lenguaje (LLMs). En esta lección, exploraremos los tres componentes principales: **Cadenas**, **Agentes** y **Memoria**. Entender cómo encajan estas piezas te ayudará a diseñar y construir tus propias aplicaciones LangChain.

---

## 1. Cadenas: Los Bloques de Construcción

Una **Cadena** es una secuencia de operaciones que procesan una entrada y generan una salida. Piénsalo como una tubería donde cada paso transforma datos o llama a un modelo de lenguaje con un prompt.

- **SimpleChain**: La cadena más básica que toma una entrada, la procesa a través de un LLM y devuelve la salida.
- Las cadenas pueden combinarse para crear flujos de trabajo más complejos.

**Ejemplo:** Una cadena que resume un hilo de tweets enviando un prompt al LLM.

```python
from langchain.llms import OpenAI

llm = OpenAI(temperature=0)

def summarize_chain(input_text):
    prompt = f"Resume este hilo de tweets: {input_text}"
    return llm(prompt)
```

---

## 2. Memoria: Manteniendo el Contexto

La **Memoria** permite que tu aplicación recuerde interacciones previas, habilitando conversaciones conscientes del contexto.

- **ConversationBufferMemory** almacena el historial del chat.
- La memoria puede pasarse a cadenas o agentes para mantener el estado a través de múltiples entradas.

Esto es esencial para chatbots o cualquier aplicación donde el contexto importe.

---

## 3. Agentes: Tomadores de Decisiones Inteligentes

Un **Agente** usa un LLM como su "cerebro" para decidir qué acciones tomar, a menudo usando **Herramientas**.

- Las herramientas son funciones o APIs que el agente puede llamar para obtener información o realizar tareas.
- Los agentes combinan herramientas y memoria para interactuar dinámicamente con usuarios y datos externos.

**Ejemplo:** Un agente que obtiene los últimos tweets sobre un tema y recuerda la conversación.

```python
def fetch_latest_tweets(query):
    # Imagina que esto llama a la API de Twitter y devuelve tweets
    return f"Tweets obtenidos sobre {query}"

from langchain.agents import AgentExecutor, Tool
from langchain.memory import ConversationBufferMemory

memory = ConversationBufferMemory(memory_key="chat_history", return_messages=True)

tools = [Tool(name="FetchTweets", func=fetch_latest_tweets, description="Obtener los últimos tweets basados en una consulta")]

agent = AgentExecutor.from_agent_and_tools(
    agent=llm,  # Usando LLM como el cerebro del agente
    tools=tools,
    memory=memory,
    verbose=True
)

user_input = "Actualizaciones de LangChain"
response = agent.run(user_input)

summary = summarize_chain(response)
print("Resumen de los tweets obtenidos:", summary)
```

---

## Cómo Funcionan Estos Componentes Juntos

La entrada del usuario fluye hacia el **Agente**, que usa sus **Herramientas** y **Memoria** para obtener datos y mantener el contexto. La salida del agente puede luego pasar a través de una **Cadena** para procesamiento adicional, como la resumición.

Este diseño modular te permite construir aplicaciones complejas combinando partes simples y reutilizables.

![GENERANDO: Diagrama que muestra el flujo desde la entrada del usuario hacia el agente con herramientas y memoria, luego hacia una cadena para resumir, con flechas que indican el flujo de datos y componentes etiquetados](/.learn/assets/qrztaerujwn)

---

## Resumen

- Las **Cadenas** procesan entradas y salidas en secuencia.
- La **Memoria** almacena el historial de la conversación para mantener el contexto.
- Los **Agentes** usan LLMs y herramientas para decidir acciones dinámicamente.
- Juntos, permiten aplicaciones de lenguaje potentes y conscientes del contexto.

---

## Tu Turno: Propuesta de Desafío de Código

```code_challenge_proposal
En este ejercicio, crearás una aplicación LangChain que integre los tres componentes: cadenas, agentes y memoria.

Harás lo siguiente:
- Implementar una cadena simple que procese texto de entrada.
- Definir una función herramienta que simule la obtención de datos (por ejemplo, titulares de noticias).
- Configurar la memoria de conversación para hacer seguimiento de las entradas del usuario.
- Crear un agente que use la herramienta y la memoria para responder a consultas del usuario.
- Encadenar la salida del agente a la cadena simple para procesamiento adicional (por ejemplo, resumir).

El archivo principal será app.py, que contendrá el código base con espacios reservados para cada componente.

Este ejercicio práctico consolidará tu comprensión de cómo interactúan los componentes de LangChain.
```

---

¡Sigue experimentando con estos componentes para construir tus propias aplicaciones inteligentes!