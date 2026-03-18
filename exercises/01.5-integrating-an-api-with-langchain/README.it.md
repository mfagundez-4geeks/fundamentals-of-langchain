# 01.5 Integrare un'API con LangChain

Immagina di voler far sì che la tua applicazione recuperi informazioni fresche e dinamiche o generi contenuti creativi utilizzando potenti modelli linguistici. È qui che diventa essenziale integrare un'API esterna come quella di OpenAI con LangChain.

## Perché integrare un'API?

LangChain semplifica il lavoro con grandi modelli linguistici (LLM) astrando le chiamate API e permettendoti di concentrarti sulla logica della tua applicazione. Collegandoti a un'API, puoi:

- Accedere a modelli AI potenti e aggiornati.
- Personalizzare le risposte con parametri come la creatività.
- Collegare più operazioni per flussi di lavoro complessi.

## Passo 1: Configurare il client OpenAI

Per prima cosa, devi installare il client Python di OpenAI se non l'hai già fatto:

```python
!pip install openai
```

Poi, imposta in modo sicuro la tua chiave API di OpenAI. Ad esempio, usando variabili d'ambiente:

```python
import os
os.environ["OPENAI_API_KEY"] = "tua-chiave-api-openai"
```

> **Nota:** Non inserire mai la tua chiave API direttamente nel codice di produzione.

## Passo 2: Inizializzare il wrapper LLM di OpenAI in LangChain

LangChain fornisce un comodo wrapper attorno all'API di OpenAI. Puoi inizializzarlo così:

```python
from langchain.llms import OpenAI

llm = OpenAI(temperature=0.7)  # La temperatura controlla la creatività: 0 = deterministico, valori più alti = più creativo
```

## Passo 3: Creare una catena LangChain con un modello di prompt

Una **catena** combina un modello di prompt e un LLM per elaborare input e generare output.

```python
from langchain.chains import LLMChain
from langchain.prompts import PromptTemplate

# Definisci un modello di prompt con un segnaposto variabile
prompt = PromptTemplate(
    input_variables=["topic"],
    template="Fornisci un riassunto conciso su {topic}."
)

# Combina il prompt e l'LLM in una catena
chain = LLMChain(llm=llm, prompt=prompt)
```

## Passo 4: Esegui la catena per recuperare dati

Ora puoi eseguire la catena con un argomento specifico:

```python
result = chain.run("L'algoritmo di raccomandazione di Spotify")
print(result)
```

Questo invierà il prompt all'API di OpenAI e stamperà il riassunto generato.

## Come funziona

- Il **PromptTemplate** definisce la struttura del prompt con segnaposti.
- L'**LLMChain** collega il prompt e il modello linguistico.
- Chiamando `run()` si riempie il prompt con il tuo input e lo si invia all'API.
- L'API restituisce il testo generato, che LangChain ti passa indietro.

## Sperimenta ed esplora

- Prova a cambiare il `topic` con qualsiasi cosa ti interessi.
- Modifica il parametro `temperature` per vedere come la creatività influisce sulle risposte.
- Adatta il modello di prompt per chiedere liste, spiegazioni o confronti.

## Visualizzazione del flusso

![GENERATING: Diagramma che mostra il flusso dalla catena LangChain all'API OpenAI e ritorno, con passaggi etichettati: 1) Input utente entra nella catena, 2) PromptTemplate formatta il prompt, 3) API OpenAI elabora il prompt, 4) La risposta torna alla catena, 5) L'output viene mostrato all'utente. Il diagramma usa frecce per indicare il flusso dei dati e codifica a colori per differenziare i componenti](/.learn/assets/cvv73sgjr3h)

## Riepilogo

- Integrare un'API ti permette di sfruttare potenti LLM nelle tue applicazioni.
- LangChain astrae le chiamate API, concentrandosi sul design del prompt e sul chaining.
- Usa variabili d'ambiente per gestire in modo sicuro le chiavi API.
- Il parametro `temperature` controlla la creatività delle risposte.
- Le catene combinano prompt e LLM per elaborare input e generare output.

---

### Tocca a te: Sfida di codice

```code_challenge_proposal
In questo esercizio, creerai un'applicazione LangChain che si collega all'API OpenAI per generare contenuti creativi.

Lavorerai con un singolo file Python chiamato app.py.

Istruzioni:
1. Configura in modo sicuro la chiave API OpenAI usando variabili d'ambiente.
2. Inizializza il wrapper LLM di OpenAI con una temperatura di 0.8.
3. Crea un PromptTemplate che richieda una lista di tre fatti interessanti su un dato argomento.
4. Combina il prompt e l'LLM in una LLMChain.
5. Scrivi una funzione che prenda un argomento come input, esegua la catena e stampi i risultati.
6. Testa la tua funzione con almeno due argomenti diversi.

Questo esercizio ti aiuterà a praticare l'integrazione API, il design del prompt e il chaining in LangChain.
```