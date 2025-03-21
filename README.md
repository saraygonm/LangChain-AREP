# Construcción de una Aplicación Simple de LLM con LangChain

## Descripción

Este repositorio contiene  las instrucciones necesarias para obtener y ejecutar una aplicación simple de Modelo de Lenguaje (LLM) desarrollada 
LangChain. La aplicación realiza la traducción de texto desde el inglés hacia otro idioma, usando un 
de chat y plantillas de instrucciones.

---

## Arquitectura y Componentes del Proyecto

La aplicación se estructura por medio de los siguientes componentes:

- **Modelo de Lenguaje:** Es el elemento central encargado de realizar las traducciones, en este caso, se utiliza el modelo GPT de OpenAI.
- **Plantillas de Instrucciones:** Facilitan la organización de la entrada para el modelo de lenguaje, fusionando instrucciones predefinidas con los datos proporcionados por el usuario.
- **Interfaz de Transmisión:** Permite la transmisión en tiempo real de los tokens generados por el modelo.
- **Configuración del Entorno:** Contiene las indicaciones necesarias para la instalación y configuración de la clave API.


---

## 📍 Comenzando

Estas instrucciones te permitirán:

- Utilizar modelos de lenguaje dentro de LangChain.
- Crear y aplicar plantillas de instrucciones para organizar las entradas.
- Interactuar con modelos de chat y manejar respuestas en tiempo real.

### 🔧 Prerrequisitos
- Python 3.7 o superior.
- Una clave API válida de OpenAI.

### ⚙️ Instrucciones paso a paso 

- Iniciamos sesión en https://colab.google/

<p align="center">
<img src="./img/colab.png" alt="" width="700px">
</p>

- Seleccionamos Nuevo Cuaderno

<p align="center">
<img src="./img/cuaderno.png" alt="" width="700px">
</p>


- y procedemos a ejecutar todos los fragmentos de codigo a continuación los ejecutamos en el cuadreno de jupyter


1) **Instalar LangChain:¨** Se hace la instalación usando pip.

   Para instalar LangChain, ejecuta el siguiente comando:
   ```bash
   pip install langchain


2) **Instalar Dependencias Adicionales:** Dado que se usa un modelo de chat de OpenAI, instalamos las dependencias necesarias:
   ```bash
   pip install -qU "langchain[openai]"
   ```

3) **Configurarmos la Clave API de OpenAI:** Clave API de OpenAI como una variable de entorno. 

   En la Terminal:
   ```bash
   export OPENAI_API_KEY="tu-clave-api-aquí"
   ```

   En un cuaderno Jupyter:
   ```python
   import getpass
   import os

   if not os.environ.get("OPENAI_API_KEY"):
       os.environ["OPENAI_API_KEY"] = getpass.getpass("Introduce tu clave API para OpenAI: ")
   ```

4) **Inicializar el Modelo de Chat:**  
   Luego, inicializa el modelo de chat utilizando LangChain:
   ```python
   from langchain.chat_models import init_chat_model

   model = init_chat_model("gpt-4o-mini", model_provider="openai")
   ```

5) **Interactuar con el Modelo:**  
   Interactúa con el modelo pasando una lista de mensajes. Aquí tienes un ejemplo de traducir "hi!" del inglés al italiano:
   ```python
   from langchain_core.messages import HumanMessage, SystemMessage

   messages = [
       SystemMessage("Translate the following from English into Italian"),
       HumanMessage("hi!"),
   ]

   response = model.invoke(messages)
   print(response.content)  # Salida: Ciao!
   ```

6) **Transmitir Respuestas:**  
   LangChain permite recibir tokens generados en tiempo real:
   ```python
   for token in model.stream(messages):
       print(token.content, end="|")
   ```

----

## 👨🏼‍💻 Autora

**Saray Alieth Mendivelso Gonzalez** 

---
