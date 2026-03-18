---
readingTime:
  minutes: 2.396
  words: 599
fkglResult: 9.85
---

# 01.2 Comprendere i Componenti di LangChain

LangChain è costruito attorno a diversi componenti chiave che lavorano insieme per creare applicazioni potenti alimentate da grandi modelli linguistici (LLM). In questa lezione, esploreremo i tre componenti principali: **Catene**, **Agenti** e **Memoria**. Comprendere come questi elementi si integrano ti aiuterà a progettare e costruire le tue applicazioni LangChain.

---

## 1. Catene: I Mattoni Fondamentali

Una **Catena** è una sequenza di operazioni che elaborano un input e generano un output. Pensala come una pipeline in cui ogni passaggio trasforma i dati o chiama un modello linguistico con un prompt.

- **SimpleChain**: La catena più semplice che prende un input, lo passa attraverso un LLM e restituisce l'output.
- Le catene possono essere combinate per creare flussi di lavoro più complessi.

**Esempio:** Una catena che riassume un thread di tweet inviando un prompt all'LLM.

```python
from langchain.llms import OpenAI

llm = OpenAI(temperature=0)

def summarize_chain(input_text):
    prompt = f"Riassumi questo thread di tweet: {input_text}"
    return llm(prompt)
```

---

## 2. Memoria: Mantenere il Contesto

La **Memoria** permette alla tua applicazione di ricordare le interazioni precedenti, abilitando conversazioni consapevoli del contesto.

- **ConversationBufferMemory** memorizza la cronologia della chat.
- La memoria può essere passata a catene o agenti per mantenere lo stato attraverso più input.

Questo è essenziale per chatbot o qualsiasi app in cui il contesto è importante.

---

## 3. Agenti: Decisori Intelligenti

Un **Agente** usa un LLM come suo "cervello" per decidere quali azioni intraprendere, spesso utilizzando **Strumenti**.

- Gli strumenti sono funzioni o API che l'agente può chiamare per recuperare informazioni o eseguire compiti.
- Gli agenti combinano strumenti e memoria per interagire dinamicamente con gli utenti e dati esterni.

**Esempio:** Un agente che recupera gli ultimi tweet su un argomento e ricorda la conversazione.

```python
def fetch_latest_tweets(query):
    # Immagina che questa funzione chiami l'API di Twitter e restituisca tweet
    return f"Tweet recuperati su {query}"

from langchain.agents import AgentExecutor, Tool
from langchain.memory import ConversationBufferMemory

memory = ConversationBufferMemory(memory_key="chat_history", return_messages=True)

tools = [Tool(name="FetchTweets", func=fetch_latest_tweets, description="Recupera gli ultimi tweet basati su una query")]

agent = AgentExecutor.from_agent_and_tools(
    agent=llm,  # Usa l'LLM come cervello dell'agente
    tools=tools,
    memory=memory,
    verbose=True
)

user_input = "Aggiornamenti LangChain"
response = agent.run(user_input)

summary = summarize_chain(response)
print("Riassunto dei tweet recuperati:", summary)
```

---

## Come Questi Componenti Lavorano Insieme

L'input dell'utente fluisce nell'**Agente**, che usa i suoi **Strumenti** e la **Memoria** per recuperare dati e mantenere il contesto. L'output dell'agente può quindi essere passato attraverso una **Catena** per ulteriori elaborazioni, come il riassunto.

Questo design modulare ti permette di costruire applicazioni complesse combinando parti semplici e riutilizzabili.

![GENERATING: Diagramma che mostra il flusso dall'input utente all'agente con strumenti e memoria, poi a una catena per il riassunto, con frecce che indicano il flusso dei dati e componenti etichettati](/.learn/assets/qrztaerujwn)

---

## Riassunto

- Le **Catene** elaborano input e output in sequenza.
- La **Memoria** conserva la cronologia della conversazione per mantenere il contesto.
- Gli **Agenti** usano LLM e strumenti per decidere azioni in modo dinamico.
- Insieme, permettono applicazioni linguistiche potenti e consapevoli del contesto.

---

## Tocca a Te: Proposta di Sfida di Codice

```code_challenge_proposal
In questo esercizio, creerai un'applicazione LangChain che integra i tre componenti: catene, agenti e memoria.

Farai:
- Implementare una catena semplice che elabora l'input testuale.
- Definire una funzione strumento che simula il recupero di dati (es. titoli di notizie).
- Configurare la memoria della conversazione per tenere traccia degli input utente.
- Creare un agente che usa lo strumento e la memoria per rispondere alle query degli utenti.
- Collegare l'output dell'agente alla catena semplice per un'ulteriore elaborazione (es. riassunto).

Il file principale sarà app.py, contenente il codice scheletro con segnaposto per ogni componente.

Questo esercizio pratico consoliderà la tua comprensione di come interagiscono i componenti di LangChain.
```

---

Continua a sperimentare con questi componenti per costruire le tue applicazioni intelligenti!