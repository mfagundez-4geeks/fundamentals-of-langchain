# 01.6 Construyendo un Chatbot Básico

La IA conversacional está en todas partes, desde asistentes virtuales hasta bots de soporte al cliente. Una característica clave que hace que los chatbots se sientan naturales es su capacidad para recordar interacciones previas y mantener el contexto. En esta lección, aprenderás cómo construir un chatbot básico usando LangChain que mantiene un registro del historial de conversación mediante memoria.

## ¿Por qué usar memoria en los chatbots?

Sin memoria, un chatbot trata cada mensaje como una entrada nueva y aislada. Esto conduce a conversaciones desconectadas. La memoria permite que el bot recuerde mensajes anteriores, lo que le permite responder de manera más coherente y personalizar las interacciones.

## Componentes clave de LangChain para chatbots

- **ConversationChain**: Una cadena diseñada específicamente para aplicaciones conversacionales. Conecta un modelo de lenguaje con memoria para manejar el diálogo.
- **ConversationBufferMemory**: Almacena todo el historial de la conversación en un buffer, permitiendo que el bot haga referencia a todos los intercambios previos.
- **OpenAI LLM Wrapper**: El modelo de lenguaje que genera respuestas basadas en indicaciones y memoria.

## Construyendo el chatbot: paso a paso

```python
# Importar las clases necesarias de LangChain
from langchain.chains import ConversationChain
from langchain.memory import ConversationBufferMemory
from langchain.llms import OpenAI

# Inicializar el modelo de lenguaje con baja temperatura para respuestas consistentes
llm = OpenAI(temperature=0)

# Configurar la memoria de la conversación para almacenar el historial del chat
memory = ConversationBufferMemory()

# Crear una cadena de conversación con memoria
conversation = ConversationChain(llm=llm, memory=memory)

# Ejemplo de bucle de interacción simulando entradas del usuario
user_inputs = [
    "Hola, estoy buscando un buen libro de ciencia ficción.",
    "Realmente disfruté Dune. ¿Alguna recomendación?",
    "¡Gracias! ¿Puedes recordarme qué sugeriste antes?"
]

for user_input in user_inputs:
    response = conversation.run(user_input)
    print(f"Usuario: {user_input}")
    print(f"Bot: {response}\n")
```

### Cómo funciona esto

- **ConversationBufferMemory** mantiene un registro de todos los mensajes anteriores.
- Cada vez que se llama a `conversation.run()`, el bot usa todo el historial de la conversación para generar una respuesta consciente del contexto.
- Esto permite que el bot recuerde temas anteriores y se refiera a ellos, haciendo que el chat se sienta natural.

### Ideas para experimentar

- Prueba cambiar `ConversationBufferMemory` por otros tipos de memoria como `ConversationSummaryMemory` para chats más largos.
- Añade preferencias del usuario a la memoria para personalizar las recomendaciones.
- Ajusta el parámetro `temperature` para hacer las respuestas más creativas o deterministas.

## Visualizando el flujo del chatbot

![GENERANDO: Un diagrama detallado que ilustra el flujo de un chatbot LangChain usando ConversationChain y ConversationBufferMemory. El diagrama muestra pasos numerados: 1) El usuario envía una entrada, 2) La entrada y el historial de conversación se combinan mediante ConversationBufferMemory, 3) El prompt combinado se envía al modelo de lenguaje OpenAI, 4) El modelo genera una respuesta considerando todo el contexto, 5) La respuesta se devuelve y se muestra al usuario. Flechas indican el flujo de datos, y los componentes están codificados por colores para diferenciar memoria, modelo e interacción del usuario. Las anotaciones resaltan cómo la memoria permite la retención del contexto y mejora la coherencia del chatbot.](/.learn/assets/i27ffndbp2l)

## Resumen

- Los chatbots necesitan memoria para mantener el contexto y tener conversaciones significativas.
- **ConversationChain** de LangChain combinado con **ConversationBufferMemory** facilita la creación de chatbots.
- El modelo de lenguaje genera respuestas basadas en todo el historial de la conversación.
- Experimentar con diferentes tipos de memoria y parámetros puede mejorar el comportamiento del chatbot.

---

### Pon a prueba tu comprensión

Selecciona la respuesta correcta para cada pregunta.

1. ¿Cuál es el rol de **ConversationBufferMemory** en un chatbot LangChain?

   - [ ] Genera respuestas basadas en la entrada del usuario.
   - [x] Almacena todo el historial de la conversación para proporcionar contexto.
   - [ ] Conecta el chatbot con APIs externas.
   - [ ] Controla la creatividad del modelo de lenguaje.

2. ¿Qué sucede si no usas memoria en un chatbot?

   - [ ] El chatbot recordará todas las conversaciones previas.
   - [x] El chatbot trata cada mensaje de forma independiente sin contexto.
   - [ ] El chatbot personalizará automáticamente las respuestas.
   - [ ] El chatbot se bloqueará después del primer mensaje.

3. ¿Cómo afecta el parámetro **temperature** las respuestas del chatbot?

   - [ ] Controla la velocidad de generación de respuestas.
   - [ ] Determina la longitud de la respuesta.
   - [x] Ajusta la creatividad o aleatoriedad de la salida.
   - [ ] Establece el número máximo de turnos de conversación.

4. ¿Qué componente de LangChain combina el modelo de lenguaje y la memoria para la conversación?

   - [ ] PromptTemplate
   - [ ] OpenAI
   - [x] ConversationChain
   - [ ] LLMChain

5. Para personalizar las recomendaciones del chatbot basadas en las preferencias del usuario, deberías:

   - [ ] Usar solo ConversationBufferMemory.
   - [ ] Aumentar la temperatura a 1.0.
   - [x] Almacenar las preferencias del usuario en la memoria y usarlas en los prompts.
   - [ ] Eliminar la memoria para simplificar el chatbot.

[Pregunta a Rigo cómo funciona ConversationBufferMemory en chatbots LangChain](https://4geeks.com/ask?query=how-does-conversationbuffermemory-work-in-langchain-chatbots)