# tec2025sql

Agente SQL para consultas inteligentes sobre una base de datos de tienda, usando FastAPI, OpenAI y SQLite.

## Descripción general
Este proyecto implementa un asistente web que responde preguntas en lenguaje natural sobre los datos de una tienda, generando y ejecutando consultas SQL sobre una base de datos SQLite. Utiliza FastAPI para el backend, Jinja2 para la interfaz web y la API de OpenAI para la generación de SQL.

## Estructura del proyecto

- `main.py`: Servidor FastAPI, lógica de endpoints, integración con OpenAI y renderizado de la interfaz web.
- `create_db.py`: Script para crear y poblar la base de datos `store.db` con tablas y datos de ejemplo.
- `requirements.txt`: Lista de dependencias Python necesarias.
- `templates/index.html`: Interfaz web para interactuar con el asistente.
- `prompt.txt`: (Opcional) Puede contener instrucciones o prompts para el modelo de lenguaje.
- `store.db`: Base de datos SQLite generada por `create_db.py` (no incluida por defecto).

## Detalle de archivos principales

### `main.py`
- Inicia el servidor FastAPI y configura CORS.
- Define el endpoint raíz `/` que muestra la interfaz web.
- Expone un endpoint para recibir preguntas y devolver respuestas generadas por el modelo de OpenAI.
- Incluye funciones para adaptar SQL generado a la sintaxis de SQLite.

### `create_db.py`
- Crea las tablas `Productos`, `Distribuidores` y `Ventas` en `store.db`.
- Inserta datos de ejemplo para pruebas y demostraciones.

### `templates/index.html`
- Interfaz web moderna para enviar preguntas y mostrar respuestas.
- Permite interacción tipo chat con el agente SQL.

### `requirements.txt`
- Dependencias principales: `fastapi`, `uvicorn`, `openai`, `pydantic`, `jinja2`, `langgraph`, `langchain`.

## Cómo ejecutar el proyecto

1. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```
2. Crea la base de datos de ejemplo:
   ```bash
   python create_db.py
   ```
3. Inicia el servidor:
   ```bash
   uvicorn main:app --reload
   ```
4. Abre tu navegador en [http://localhost:8000](http://localhost:8000)

## Notas
- Necesitas una clave de API de OpenAI en la variable de entorno `OPENAI_API_KEY`.
- El archivo `prompt.txt` puede usarse para personalizar instrucciones al modelo.
- El sistema adapta automáticamente SQL generado para compatibilidad con SQLite.

---

Este proyecto es una base para asistentes conversacionales que interactúan con bases de datos usando lenguaje natural y modelos de IA.
