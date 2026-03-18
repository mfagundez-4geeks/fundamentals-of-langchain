# 01.1 Configurare il tuo ambiente LangChain

Prima di iniziare a costruire applicazioni potenti con LangChain, è essenziale configurare un ambiente di sviluppo pulito e organizzato. Questo aiuta a mantenere le dipendenze del progetto isolate e gestibili, proprio come fanno gli sviluppatori professionisti.

## Passo 1: Crea un ambiente virtuale Python

Un **ambiente virtuale** ti permette di creare uno spazio isolato per il tuo progetto LangChain, prevenendo conflitti con altri pacchetti Python sul tuo sistema.

Apri il terminale ed esegui i seguenti comandi:

```bash
python3 -m venv langchain-env
source langchain-env/bin/activate  # Su Windows usa: langchain-env\Scripts\activate
```

- Il primo comando crea un nuovo ambiente virtuale chiamato `langchain-env`.
- Il secondo comando attiva questo ambiente in modo che tutti i pacchetti Python che installerai saranno contenuti al suo interno.

## Passo 2: Installa LangChain

Con l'ambiente virtuale attivato, installa LangChain usando pip:

```bash
pip install langchain
```

Questo comando scarica e installa l'ultima versione del pacchetto LangChain e le sue dipendenze.

## Passo 3: Verifica l'installazione

Per assicurarti che tutto sia configurato correttamente, crea un semplice script Python chiamato `test_langchain.py` con il seguente contenuto:

```python
from langchain import LLMChain

print("LangChain importato con successo!")
```

Esegui lo script nel terminale:

```bash
python test_langchain.py
```

Se vedi il messaggio **LangChain importato con successo!** senza errori, il tuo ambiente è pronto!

## Opzionale: Installa IPython per uno sviluppo interattivo

Per un'esperienza di coding migliore, puoi installare **IPython**, una shell Python interattiva avanzata:

```bash
pip install ipython
ipython
```

All'interno di IPython, puoi testare rapidamente gli import di LangChain e sperimentare con snippet di codice in modo interattivo.

---

Configurare correttamente il tuo ambiente è il primo passo per costruire applicazioni straordinarie con LangChain. Nelle prossime lezioni, inizierai a creare catene e integrare API utilizzando questa configurazione.

Buona programmazione! 🚀