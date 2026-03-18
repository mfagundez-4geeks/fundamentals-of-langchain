# 01.4 Trabajando con Prompts en LangChain

¿Alguna vez has querido que tu modelo de lenguaje responda de manera diferente según la situación o la entrada del usuario? ¡Ahí es donde los **templates de prompt** son muy útiles! Te permiten crear prompts flexibles que se adaptan dinámicamente a diferentes entradas, haciendo que tus aplicaciones sean más inteligentes y personalizadas.

## ¿Qué es un PromptTemplate?

En LangChain, un **PromptTemplate** es una forma de definir un prompt con espacios reservados (variables) que puedes completar más adelante con datos reales. Esta separación entre la estructura del prompt y los datos de entrada te ayuda a reutilizar prompts fácilmente y mantener tu código limpio.

## Creando un Prompt Dinámico

Veamos un ejemplo donde construimos un prompt para un asistente de redes sociales. Este asistente genera respuestas amigables basadas en las acciones del usuario en diferentes plataformas.

```python
from langchain.prompts import PromptTemplate

# Define un template de prompt con variables para contenido dinámico
prompt = PromptTemplate(
    input_variables=["platform", "user_action"],
    template="""
Eres un asistente de redes sociales. Cuando un usuario realiza la acción '{user_action}' en {platform}, genera una respuesta útil y amigable.

Ejemplo:
Acción del usuario: 'le gusta una publicación'
Respuesta: '¡Gracias por darle me gusta a la publicación! Mira más contenido que podría gustarte.'

Ahora, responde a esta acción:
Acción del usuario: '{user_action}'
Respuesta:
"""
)

# Uso de ejemplo con entradas dinámicas
inputs = {
    "platform": "Instagram",
    "user_action": "comenta en una foto"
}

# Genera el prompt final
final_prompt = prompt.format(**inputs)

print(final_prompt)
```

### Cómo Funciona Esto

- **input_variables**: Son los espacios reservados en tu prompt que serán reemplazados con valores reales.
- **template**: El texto del prompt con espacios reservados entre llaves `{}`.
- **format()**: Este método llena los espacios reservados con los valores que proporcionas.

## ¿Por qué Usar PromptTemplate?

- **Reutilización**: Escribe tu prompt una vez y reutilízalo con diferentes entradas.
- **Mantenibilidad**: Mantén la lógica del prompt separada de tus datos.
- **Flexibilidad**: Personaliza fácilmente los prompts para diferentes escenarios.

## ¡Pruébalo Tú Mismo!

- Cambia los valores de `platform` y `user_action` para ver cómo se adapta el prompt.
- Crea un template de prompt para un bot de Twitter que responda a menciones, incluyendo variables como nombre de usuario y contenido de la mención.
- Experimenta añadiendo instrucciones condicionales dentro de tu prompt para guiar el comportamiento del modelo.

## Resumen

- **PromptTemplate** te ayuda a crear prompts dinámicos con espacios reservados.
- Usa **input_variables** para definir qué partes del prompt cambiarán.
- El método **format()** llena estas variables con datos reales.
- Esta técnica es esencial para construir aplicaciones LangChain flexibles y mantenibles.

### ¡Pon a Prueba Tu Comprensión!

Explica con tus propias palabras qué es un PromptTemplate y por qué es útil en aplicaciones LangChain.

```question eval="El usuario debe explicar que un PromptTemplate es un prompt con espacios reservados para variables que pueden llenarse dinámicamente, permitiendo la reutilización y personalización de prompts en aplicaciones LangChain."
CORRECT: Un PromptTemplate es un prompt con variables que pueden ser reemplazadas con diferentes entradas para crear prompts dinámicos.
CORRECT: Permite reutilizar la misma estructura de prompt con diferentes datos, haciendo tu código más flexible.
INCORRECT: Es un prompt fijo que no puede cambiarse.
INCORRECT: Es una función que ejecuta el modelo de lenguaje.
CORRECT: PromptTemplate separa el texto del prompt de los datos de entrada, ayudando a personalizar respuestas fácilmente.
INCORRECT: Se usa para almacenar el historial de conversaciones.
```