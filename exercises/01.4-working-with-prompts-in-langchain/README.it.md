# 01.4 Lavorare con i Prompt in LangChain

Hai mai desiderato che il tuo modello linguistico rispondesse in modo diverso a seconda della situazione o dell'input dell'utente? È qui che entrano in gioco i **modelli di prompt**! Ti permettono di creare prompt flessibili che si adattano dinamicamente a diversi input, rendendo le tue applicazioni più intelligenti e personalizzate.

## Cos'è un PromptTemplate?

In LangChain, un **PromptTemplate** è un modo per definire un prompt con segnaposto (variabili) che puoi riempire successivamente con dati reali. Questa separazione tra struttura del prompt e dati di input ti aiuta a riutilizzare facilmente i prompt e a mantenere il codice pulito.

## Creare un Prompt Dinamico

Vediamo un esempio in cui costruiamo un prompt per un assistente dei social media. Questo assistente genera risposte amichevoli basate sulle azioni degli utenti su diverse piattaforme.

```python
from langchain.prompts import PromptTemplate

# Definisci un modello di prompt con variabili per contenuti dinamici
prompt = PromptTemplate(
    input_variables=["platform", "user_action"],
    template="""
Sei un assistente per i social media. Quando un utente esegue l'azione '{user_action}' su {platform}, genera una risposta utile e amichevole.

Esempio:
Azione utente: 'mette mi piace a un post'
Risposta: 'Grazie per aver messo mi piace al post! Dai un'occhiata a più contenuti che potrebbero piacerti.'

Ora, rispondi a questa azione:
Azione utente: '{user_action}'
Risposta:
"""
)

# Esempio di utilizzo con input dinamici
inputs = {
    "platform": "Instagram",
    "user_action": "commenta una foto"
}

# Genera la stringa finale del prompt
final_prompt = prompt.format(**inputs)

print(final_prompt)
```

### Come Funziona

- **input_variables**: Questi sono i segnaposto nel tuo prompt che verranno sostituiti con valori reali.
- **template**: Il testo del prompt con segnaposto racchiusi tra parentesi graffe `{}`.
- **format()**: Questo metodo riempie i segnaposto con i valori che fornisci.

## Perché Usare PromptTemplate?

- **Riutilizzabilità**: Scrivi il tuo prompt una volta e riutilizzalo con input diversi.
- **Manutenibilità**: Mantieni la logica del prompt separata dai dati.
- **Flessibilità**: Personalizza facilmente i prompt per scenari diversi.

## Provalo Tu Stesso!

- Cambia i valori di `platform` e `user_action` per vedere come il prompt si adatta.
- Crea un modello di prompt per un bot di Twitter che risponde alle menzioni, includendo variabili come nome utente e contenuto della menzione.
- Sperimenta aggiungendo istruzioni condizionali all'interno del tuo prompt per guidare il comportamento del modello.

## Riepilogo

- **PromptTemplate** ti aiuta a creare prompt dinamici con segnaposto.
- Usa **input_variables** per definire quali parti del prompt cambieranno.
- Il metodo **format()** riempie queste variabili con dati reali.
- Questa tecnica è essenziale per costruire applicazioni LangChain flessibili e manutenibili.

### Metti alla Prova la Tua Comprensione!

Spiega con parole tue cos'è un PromptTemplate e perché è utile nelle applicazioni LangChain.

```question eval="L'utente deve spiegare che un PromptTemplate è un prompt con segnaposto per variabili che possono essere riempite dinamicamente, permettendo il riutilizzo e la personalizzazione dei prompt nelle applicazioni LangChain."
CORRECT: Un PromptTemplate è un prompt con variabili che possono essere sostituite con input diversi per creare prompt dinamici.
CORRECT: Permette di riutilizzare la stessa struttura di prompt con dati diversi, rendendo il codice più flessibile.
INCORRECT: È un prompt fisso che non può essere modificato.
INCORRECT: È una funzione che esegue il modello linguistico.
CORRECT: PromptTemplate separa il testo del prompt dai dati di input, aiutando a personalizzare facilmente le risposte.
INCORRECT: Viene usato per memorizzare la cronologia delle conversazioni.
```