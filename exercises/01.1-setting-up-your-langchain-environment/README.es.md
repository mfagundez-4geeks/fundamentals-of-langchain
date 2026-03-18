# 01.1 Configurando Tu Entorno LangChain

Antes de comenzar a construir aplicaciones potentes con LangChain, es esencial configurar un entorno de desarrollo limpio y organizado. Esto ayuda a mantener las dependencias de tu proyecto aisladas y manejables, tal como lo hacen los desarrolladores profesionales.

## Paso 1: Crear un Entorno Virtual de Python

Un **entorno virtual** te permite crear un espacio aislado para tu proyecto LangChain, evitando conflictos con otros paquetes de Python en tu sistema.

Abre tu terminal y ejecuta los siguientes comandos:

```bash
python3 -m venv langchain-env
source langchain-env/bin/activate  # En Windows usa: langchain-env\Scripts\activate
```

- El primer comando crea un nuevo entorno virtual llamado `langchain-env`.
- El segundo comando activa este entorno para que cualquier paquete de Python que instales se contenga dentro de él.

## Paso 2: Instalar LangChain

Con tu entorno virtual activado, instala LangChain usando pip:

```bash
pip install langchain
```

Este comando descarga e instala el paquete LangChain más reciente y sus dependencias.

## Paso 3: Verificar Tu Instalación

Para asegurarte de que todo está configurado correctamente, crea un script simple de Python llamado `test_langchain.py` con el siguiente contenido:

```python
from langchain import LLMChain

print("¡LangChain importado con éxito!")
```

Ejecuta el script en tu terminal:

```bash
python test_langchain.py
```

Si ves el mensaje **¡LangChain importado con éxito!** sin errores, ¡tu entorno está listo!

## Opcional: Instalar IPython para Desarrollo Interactivo

Para una mejor experiencia de codificación, puedes instalar **IPython**, un shell interactivo mejorado de Python:

```bash
pip install ipython
ipython
```

Dentro de IPython, puedes probar rápidamente las importaciones de LangChain y experimentar con fragmentos de código de forma interactiva.

---

Configurar tu entorno correctamente es el primer paso para construir aplicaciones increíbles con LangChain. En las próximas lecciones, comenzarás a crear cadenas e integrar APIs usando esta configuración.

¡Feliz codificación! 🚀