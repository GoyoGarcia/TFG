# Detección de Activos Infravalorados

**Modelado de precios inmobiliarios con Machine Learning y NLP.**

Trabajo de Fin de Grado en Ingeniería Informática, CUNEF Universidad (2025-2026).


---
# Contexto
El mercado inmobiliario español arrastra una ineficiencia clásica: el precio de lista de un piso lo fija un humano sobre criterios subjetivos, esto permite que convivan activos infravalorados y sobrevalorados. Los modelos de valoración automática tradicionales (AVMs) cubren parte del problema con variables numéricas (superficie, número de habitaciones, planta, etc.), pero ignoran toda la información que vive en la descripción libre del anuncio: reformas, calidades, vistas, estado real del inmueble, etc. Bajo esta premisa, la motivación de este trabajo es desarrollar un sistema que cierre dicha brecha funcional. Se propone transformar estas descripciones no estructuradas en dimensiones cuantitativas mediante Large Language Models (LLMs), permitiendo además al sistema discernir entre el contenido promocional y los atributos reales del activo. El objetivo final es identificar "oportunidades de inversión invisibles".

---
## Estructura del repositorio

```
.
├── TFG_Gregorio_Github.ipynb        # Notebook con todo el pipeline
├── pisos_madrid_dataset.csv         # Dataset bruto del scraping (10.270 × 11)
├── pisos_madrid_dataset_limpio.csv  # Dataset tras limpieza + scoring (10.238 × 61)
└── README.md                        
```

Los dos CSV intermedios permiten reproducir partes del pipeline sin tener que volver a ejecutar las fases más lentas:
- **`pisos_madrid_dataset.csv`** contiene los 10.270 anuncios recolectados del portal pisos.com tal cual salen del scraper, con la columna `caracteristicas` aún serializada como diccionario. Sirve como punto de entrada si se quiere repetir la fase de preparación sin volver a hacer ~10.000 peticiones HTTP.
- **`pisos_madrid_dataset_limpio.csv`** es el resultado tras la limpieza, la expansión del diccionario de características y el scoring ordinal: 10.238 filas y 61 variables numéricas. Es el punto de partida natural si se quiere experimentar directamente con la fase de NLP o con el modelo, sin pasar por las dos etapas anteriores.

El notebook está organizado en seis secciones que reproducen el flujo del trabajo:
1. Web scraping
2. Preparación del dataset
3. Feature engineering con embeddings
4. Métricas descriptivas y visualizaciones
5. Modelo predictivo BART
6. Detección de anomalías y análisis de residuos

---
## Stack técnico
 
- **Lenguaje:** Python 3.10
- **Scraping:** `requests`, `BeautifulSoup`
- **Procesado de datos:** `pandas`, `numpy`, expresiones regulares
- **NLP:** `sentence-transformers` (`intfloat/multilingual-e5-large`)
- **Modelado:** `pymc`, `pymc-bart`, `arviz`, `scikit-learn`
- **Visualización:** `matplotlib`, `seaborn`, `plotly`
- **Entorno:** Google Colab (GPU T4)

---
## Autor
 
**Gregorio García Velasco** — Grado en Ingeniería Informática, CUNEF Universidad.
