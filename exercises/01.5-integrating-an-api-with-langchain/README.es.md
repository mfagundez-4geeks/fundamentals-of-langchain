# 01.5 Integrando una API con LangChain

Imagina que quieres que tu aplicación obtenga información fresca y dinámica o genere contenido creativo utilizando potentes modelos de lenguaje. Aquí es donde la integración de una API externa como la de OpenAI con LangChain se vuelve esencial.

## ¿Por qué integrar una API?

LangChain simplifica el trabajo con grandes modelos de lenguaje (LLMs) al abstraer las llamadas a la API y permitirte enfocarte en construir la lógica de tu aplicación. Al conectarte a una API, puedes:

- Acceder a modelos de IA potentes y actualizados.
- Personalizar las respuestas con parámetros como la creatividad.
- Encadenar múltiples operaciones para flujos de trabajo complejos.

## Paso 1: Configurar el cliente de OpenAI

Primero, necesitas instalar el cliente de OpenAI para Python si aún no lo has hecho:

```python
!pip install openai
```

Luego, configura tu clave API de OpenAI de forma segura. Por ejemplo, usando variables de entorno:

```python
import os
os.environ["OPENAI_API_KEY"] = "tu-clave-api-openai"
```

> **Nota:** Nunca codifiques tu clave API directamente en el código de producción.

## Paso 2: Inicializar el wrapper LLM de OpenAI en LangChain

LangChain proporciona un wrapper conveniente alrededor de la API de OpenAI. Puedes inicializarlo así:

```python
from langchain.llms import OpenAI

llm = OpenAI(temperature=0.7)  # La temperatura controla la creatividad: 0 = determinista, más alto = más creativo
```

## Paso 3: Crear una cadena LangChain con una plantilla de prompt

Una **cadena** combina una plantilla de prompt y un LLM para procesar entradas y generar salidas.

```python
from langchain.chains import LLMChain
from langchain.prompts import PromptTemplate

# Define una plantilla de prompt con un marcador de posición variable
prompt = PromptTemplate(
    input_variables=["topic"],
    template="Proporciona un resumen conciso sobre {topic}."
)

# Combina el prompt y el LLM en una cadena
chain = LLMChain(llm=llm, prompt=prompt)
```

## Paso 4: Ejecutar la cadena para obtener datos

Ahora, puedes ejecutar la cadena con un tema específico:

```python
result = chain.run("El algoritmo de recomendación de Spotify")
print(result)
```

Esto enviará el prompt a la API de OpenAI e imprimirá el resumen generado.

## Cómo funciona

- El **PromptTemplate** define la estructura del prompt con marcadores de posición.
- El **LLMChain** conecta el prompt y el modelo de lenguaje.
- Llamar a `run()` completa el prompt con tu entrada y lo envía a la API.
- La API devuelve el texto generado, que LangChain te retorna.

## Experimenta y explora

- Prueba cambiando el `topic` a cualquier cosa que te interese.
- Ajusta el parámetro `temperature` para ver cómo afecta la creatividad de las respuestas.
- Modifica la plantilla de prompt para pedir listas, explicaciones o comparaciones.

## Visualizando el flujo

![GENERANDO: Diagrama que muestra el flujo desde la cadena LangChain a la API de OpenAI y de regreso, con pasos etiquetados: 1) La entrada del usuario entra en la cadena, 2) PromptTemplate formatea el prompt, 3) La API de OpenAI procesa el prompt, 4) La respuesta regresa a la cadena, 5) La salida se muestra al usuario. El diagrama usa flechas para indicar el flujo de datos y codificación de colores para diferenciar componentes](/.learn/assets/cvv73sgjr3h)

## Resumen

- Integrar una API te permite aprovechar potentes LLMs en tus aplicaciones.
- LangChain abstrae las llamadas a la API, enfocándose en el diseño de prompts y el encadenamiento.
- Usa variables de entorno para gestionar las claves API de forma segura.
- El parámetro `temperature` controla la creatividad de las respuestas.
- Las cadenas combinan prompts y LLMs para procesar entradas y generar salidas.

---

### Tu turno: Desafío de código

```code_challenge_proposal
En este ejercicio, crearás una aplicación LangChain que se conecte a la API de OpenAI para generar contenido creativo.

Trabajarás con un solo archivo Python llamado app.py.

Instrucciones:
1. Configura la clave API de OpenAI de forma segura usando variables de entorno.
2. Inicializa el wrapper LLM de OpenAI con una temperatura de 0.8.
3. Crea un PromptTemplate que pida una lista de tres datos interesantes sobre un tema dado.
4. Combina el prompt y el LLM en un LLMChain.
5. Escribe una función que tome un tema como entrada, ejecute la cadena e imprima los resultados.
6. Prueba tu función con al menos dos temas diferentes.

Este ejercicio te ayudará a practicar la integración de APIs, el diseño de prompts y el encadenamiento en LangChain.
```