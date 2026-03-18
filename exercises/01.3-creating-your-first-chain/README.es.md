# 01.3 Creando Tu Primera Cadena

¿Alguna vez te has preguntado cómo hacer que un modelo de lenguaje genere contenido creativo basado en tu entrada? En LangChain, esto se hace usando **Cadenas** — secuencias que conectan tu entrada, los prompts y el modelo de lenguaje para producir una salida significativa.

## ¿Qué es una Cadena?

Una **Cadena** en LangChain es como una tubería: toma tu entrada, la procesa a través de una plantilla de prompt, la envía a un modelo de lenguaje (LLM) y devuelve la salida. Esto te permite automatizar tareas como generar tweets, subtítulos o resúmenes.

## Construyendo una Cadena Simple

Vamos a crear una cadena que genere un tweet creativo sobre cualquier tema que elijas.

```python
# Importar las clases necesarias de LangChain
from langchain.chains import LLMChain
from langchain.llms import OpenAI

# Paso 1: Inicializar el modelo de lenguaje
llm = OpenAI(temperature=0.7)  # Controla la creatividad de la salida

# Paso 2: Definir una plantilla de prompt simple
prompt_template = "Genera un tweet creativo sobre {topic}."

# Paso 3: Crear la cadena combinando el LLM y el prompt
chain = LLMChain(llm=llm, prompt=prompt_template)

# Paso 4: Ejecutar la cadena con datos de entrada
topic_input = {"topic": "LangChain y IA"}
output = chain.run(topic_input)

# Paso 5: Mostrar el resultado
print(output)
```

### Cómo Funciona

- **Inicializar el LLM**: Creamos una instancia de OpenAI con un parámetro `temperature` que controla cuán creativa o aleatoria es la salida.
- **Plantilla de Prompt**: Es una cadena con un marcador de posición `{topic}` que será reemplazado por tu entrada.
- **LLMChain**: Combina el prompt y el LLM en una cadena.
- **Ejecutar la Cadena**: Pasa un diccionario con tu tema de entrada, y la cadena genera un tweet.

## ¡Pruébalo Tú Mismo!

- Cambia el valor de `topic` a algo que te guste, como "exploración espacial" o "recetas saludables".
- Modifica el prompt para generar subtítulos de Instagram o descripciones de listas de reproducción de Spotify.
- Experimenta con el parámetro `temperature`: valores bajos hacen la salida más enfocada, valores altos la hacen más creativa.

## Visualizando el Flujo de la Cadena

![GENERANDO: Un diagrama claro y educativo que muestra el flujo de datos en una cadena de LangChain: comenzando con la entrada del usuario etiquetada como 'Datos de Entrada', una flecha apuntando a un cuadro etiquetado 'Plantilla de Prompt' con el marcador {topic}, luego una flecha a un cuadro etiquetado 'Modelo de Lenguaje (LLM)', y finalmente una flecha a 'Salida' mostrando el texto generado. El diagrama está anotado con pasos numerados y flechas para guiar al aprendiz a través del proceso](/.learn/assets/p40c2y51c8a)

## Resumen

- Una **Cadena** conecta tu entrada, prompt y modelo de lenguaje para generar salida.
- La **plantilla de prompt** guía al LLM sobre qué generar.
- El parámetro **temperature** controla la creatividad.
- Ejecutar la cadena con entrada produce la salida deseada.

---

### ¡Pon a Prueba Tu Comprensión!

Selecciona la respuesta correcta para cada pregunta.

1. ¿Qué controla el parámetro `temperature` en el LLM de OpenAI?

   - [ ] La velocidad de la respuesta
   - [x] La creatividad o aleatoriedad de la salida
   - [ ] La longitud de la salida
   - [ ] El idioma de la salida

2. En la plantilla de prompt "Genera un tweet creativo sobre {topic}.", ¿qué representa `{topic}`?

   - [ ] La salida generada por el LLM
   - [x] Un marcador de posición que es reemplazado por la entrada del usuario
   - [ ] El nombre de la cadena
   - [ ] La configuración de temperatura

3. ¿Cuál es el propósito principal de un LLMChain en LangChain?

   - [ ] Almacenar el historial de conversación
   - [ ] Conectar múltiples APIs
   - [x] Combinar una plantilla de prompt con un modelo de lenguaje
   - [ ] Depurar código

4. Si quieres una salida más enfocada y menos aleatoria, ¿deberías aumentar o disminuir la temperatura?

   - [ ] Aumentar la temperatura
   - [x] Disminuir la temperatura
   - [ ] La temperatura no afecta la aleatoriedad
   - [ ] Depende del prompt

¡Sigue experimentando con cadenas para desbloquear el poder de los modelos de lenguaje en tus aplicaciones!