# Sistema MultiAgentes para Predicción y Análisis de Abandono de Clientes

## Descripción del proyecto

Este proyecto implementa un sistema basado en arquitectura **MultiAgente** orientado al análisis y predicción del abandono de clientes (*Customer Churn*) utilizando el dataset **Telco Customer Churn**.

El sistema divide las tareas en agentes independientes con responsabilidades específicas:

* Un agente encargado de la normalización y preparación de datos.
* Un agente encargado del entrenamiento y evaluación del modelo de Machine Learning.
* Un agente comunicador basado en **RAG (Retrieval Augmented Generation)** para generar respuestas y explicaciones en lenguaje natural utilizando **Mistral AI**.

La arquitectura permite separar procesos, reutilizar componentes y combinar Machine Learning tradicional con modelos de lenguaje y recuperación semántica.

---

## Arquitectura MultiAgente

```text
Usuario
    ↓

SistemaMultiAgente

    ↓

┌─────────────────────┐
│ AgenteNormalizador  │
│ Limpieza y          │
│ transformación      │
└─────────────────────┘

            ↓

┌─────────────────────┐
│ AgenteEntrenador    │
│ Entrenamiento y     │
│ evaluación ML       │
└─────────────────────┘

            ↓

┌─────────────────────┐
│ AgenteComunicador   │
│ RAG + Mistral AI    │
└─────────────────────┘

            ↓

Respuesta final
```

---

## Agentes y funciones

### Agente 1: Normalizador

Responsabilidades:

* Exploración de datos
* Limpieza de registros
* Tratamiento de valores faltantes
* Codificación de variables categóricas
* Escalado de variables numéricas
* Preparación de datos para Machine Learning

Entrada:

* Dataset original

Salida:

* Dataset procesado y listo para entrenamiento

---

### Agente 2: Entrenador

Responsabilidades:

* División de datos en entrenamiento y prueba
* Entrenamiento del modelo
* Comparación de modelos
* Evaluación de desempeño
* Selección del modelo final

Entrada:

* Dataset normalizado

Salida:

* Modelo entrenado
* Métricas de evaluación

Modelo seleccionado:

* Logistic Regression

Accuracy obtenido:

```text
0.8006
```

---

### Agente 3: Comunicador

Responsabilidades:

* Construcción del corpus documental
* Generación de embeddings
* Recuperación semántica
* Integración con Mistral AI
* Generación de respuestas en lenguaje natural

Entrada:

* Preguntas del usuario

Salida:

* Explicaciones y respuestas contextualizadas

---

## Tecnologías utilizadas

Lenguajes:

* Python

Librerías y herramientas:

* Pandas
* NumPy
* Scikit-Learn
* LangChain
* HuggingFace Embeddings
* ChromaDB (Base vectorial y recuperación semántica)
* Mistral AI
* Google Colab

Modelo de Machine Learning:

* Logistic Regression

Modelo LLM:

* mistral-small-latest

Dataset utilizado:

* Telco Customer Churn

---

## Cómo ejecutar el proyecto

### 1. Clonar el repositorio

```bash
git clone https://github.com/c4rlosantonio527/mistral-rag-colab.git
```

### 2. Instalar dependencias

```bash
pip install pandas
pip install numpy
pip install scikit-learn
pip install mistralai
pip install langchain
pip install langchain-community
pip install langchain-huggingface
pip install chromadb
pip install sentence-transformers
```

### 3. Configurar la API Key de Mistral

Agregar la API Key en el entorno:

```python
api_key="TU_API_KEY"
```

---

### 4. Ejecutar el proyecto

```bash
python MultiAgentes.py
```

---

## Resultados obtenidos

Modelo seleccionado:

```text
Logistic Regression
```

Accuracy:

```text
80.06%
```

El modelo presentó mejor desempeño en clientes que permanecen dentro del servicio y menor desempeño en la detección de clientes que abandonan, debido principalmente al desbalance de clases presente en el dataset.

---

## Ejemplo de reporte generado

Pregunta:

```text
¿Qué características presentan los clientes que abandonan el servicio?
```

Respuesta:

```text
Los clientes que abandonan el servicio suelen presentar contratos mensuales (Month-to-month), menor tiempo de permanencia y ciertos métodos de pago específicos. Además, pueden mostrar patrones relacionados con servicios contratados y soporte técnico limitado.
```

---

## Estructura del repositorio

```text
mistral-rag-colab/ Multi Agentes
│ 
│── WA_Fn-UseC_-Telco-Customer-Churn.csv
│── Agente1_DataCurator_AGNews.ipynb
├── MultiAgentes.py
│
└── README.md
```

---

## Autor

Carlos Galeano

GitHub:

c4rlosantonio527
