---
readingTime:
  minutes: 2.948
  words: 737
fkglResult: 10.92
---

# 01.6 Costruire un Chatbot di Base

L'IA conversazionale è ovunque: dagli assistenti virtuali ai bot di supporto clienti. Una caratteristica chiave che rende i chatbot naturali è la loro capacità di ricordare le interazioni precedenti e mantenere il contesto. In questa lezione, imparerai come costruire un chatbot di base usando LangChain che tiene traccia della cronologia della conversazione utilizzando la memoria.

## Perché Usare la Memoria nei Chatbot?

Senza memoria, un chatbot tratta ogni messaggio come un input nuovo e isolato. Questo porta a conversazioni disgiunte. La memoria permette al bot di richiamare i messaggi passati, consentendogli di rispondere in modo più coerente e personalizzare le interazioni.

## Componenti Chiave di LangChain per Chatbot

- **ConversationChain**: Una catena progettata specificamente per applicazioni conversazionali. Collega un modello linguistico con la memoria per gestire il dialogo.
- **ConversationBufferMemory**: Memorizza l'intera cronologia della conversazione in un buffer, permettendo al bot di fare riferimento a tutti gli scambi precedenti.
- **OpenAI LLM Wrapper**: Il modello linguistico che genera risposte basate su prompt e memoria.

## Costruire il Chatbot: Passo dopo Passo

```python
# Importa le classi necessarie di LangChain
from langchain.chains import ConversationChain
from langchain.memory import ConversationBufferMemory
from langchain.llms import OpenAI

# Inizializza il modello linguistico con temperatura bassa per risposte coerenti
llm = OpenAI(temperature=0)

# Imposta la memoria della conversazione per memorizzare la cronologia della chat
memory = ConversationBufferMemory()

# Crea una catena di conversazione con memoria
conversation = ConversationChain(llm=llm, memory=memory)

# Esempio di ciclo di interazione che simula input utente
user_inputs = [
    "Ciao, sto cercando un buon libro di fantascienza.",
    "Mi è piaciuto molto Dune. Hai qualche raccomandazione?",
    "Grazie! Puoi ricordarmi cosa hai suggerito prima?"
]

for user_input in user_inputs:
    response = conversation.run(user_input)
    print(f"Utente: {user_input}")
    print(f"Bot: {response}\n")
```

### Come Funziona

- La **ConversationBufferMemory** tiene traccia di tutti i messaggi precedenti.
- Ogni volta che viene chiamato `conversation.run()`, il bot usa l'intera cronologia della conversazione per generare una risposta contestuale.
- Questo permette al bot di ricordare argomenti precedenti e farvi riferimento, rendendo la chat naturale.

### Idee per Sperimentare

- Prova a cambiare `ConversationBufferMemory` con altri tipi di memoria come `ConversationSummaryMemory` per chat più lunghe.
- Aggiungi preferenze utente alla memoria per personalizzare le raccomandazioni.
- Regola il parametro `temperature` per rendere le risposte più creative o deterministiche.

## Visualizzare il Flusso del Chatbot

![GENERATING: Un diagramma dettagliato che illustra il flusso di un chatbot LangChain usando ConversationChain e ConversationBufferMemory. Il diagramma mostra passaggi numerati: 1) L'utente invia un input, 2) Input e cronologia della conversazione sono combinati da ConversationBufferMemory, 3) Il prompt combinato è inviato al modello linguistico OpenAI, 4) Il modello genera una risposta considerando l'intero contesto, 5) La risposta viene restituita e mostrata all'utente. Le frecce indicano il flusso dei dati e i componenti sono codificati a colori per differenziare memoria, modello e interazione utente. Le annotazioni evidenziano come la memoria consenta la conservazione del contesto e migliori la coerenza del chatbot.](/.learn/assets/i27ffndbp2l)

## Riepilogo

- I chatbot hanno bisogno di memoria per mantenere il contesto e avere conversazioni significative.
- La **ConversationChain** di LangChain combinata con **ConversationBufferMemory** permette una facile creazione di chatbot.
- Il modello linguistico genera risposte basate sull'intera cronologia della conversazione.
- Sperimentare con diversi tipi di memoria e parametri può migliorare il comportamento del chatbot.

---

### Metti alla Prova la Tua Comprensione

Seleziona la risposta corretta per ogni domanda.

1. Qual è il ruolo di **ConversationBufferMemory** in un chatbot LangChain?

   - [ ] Genera risposte basate sull'input dell'utente.
   - [x] Memorizza l'intera cronologia della conversazione per fornire contesto.
   - [ ] Collega il chatbot a API esterne.
   - [ ] Controlla la creatività del modello linguistico.

2. Cosa succede se non usi la memoria in un chatbot?

   - [ ] Il chatbot ricorderà tutte le conversazioni precedenti.
   - [x] Il chatbot tratta ogni messaggio indipendentemente senza contesto.
   - [ ] Il chatbot personalizzerà automaticamente le risposte.
   - [ ] Il chatbot si bloccherà dopo il primo messaggio.

3. Come influisce il parametro **temperature** sulle risposte del chatbot?

   - [ ] Controlla la velocità di generazione della risposta.
   - [ ] Determina la lunghezza della risposta.
   - [x] Regola la creatività o casualità dell'output.
   - [ ] Imposta il numero massimo di turni di conversazione.

4. Quale componente di LangChain combina il modello linguistico e la memoria per la conversazione?

   - [ ] PromptTemplate
   - [ ] OpenAI
   - [x] ConversationChain
   - [ ] LLMChain

5. Per personalizzare le raccomandazioni del chatbot basate sulle preferenze dell'utente, dovresti:

   - [ ] Usare solo ConversationBufferMemory.
   - [ ] Aumentare la temperatura a 1.0.
   - [x] Memorizzare le preferenze utente nella memoria e usarle nei prompt.
   - [ ] Rimuovere la memoria per semplificare il chatbot.

[Chiedi a Rigo come funziona ConversationBufferMemory nei chatbot LangChain](https://4geeks.com/ask?query=how-does-conversationbuffermemory-work-in-langchain-chatbots)
