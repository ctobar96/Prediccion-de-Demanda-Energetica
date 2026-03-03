# ⚡ Energy Demand Prediction Pipeline: Data Engineering & MLOps

![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)
![Docker](https://img.shields.io/badge/Docker-Enabled-blue.svg)
![MLflow](https://img.shields.io/badge/MLflow-Tracking-blue.svg)
![XGBoost](https://img.shields.io/badge/XGBoost-Model-green.svg)

## 📌 Descripción del Proyecto
Este proyecto implementa un flujo completo de Ingeniería de Datos y Machine Learning (MLOps) para predecir la demanda energética basada en variables meteorológicas y patrones de consumo. El sistema ingiere datos en tiempo real, los procesa siguiendo una **Arquitectura Medallón** (Bronce, Plata, Oro), y entrena un modelo predictivo registrando todas las métricas y artefactos automáticamente.

[Image of MLOps architecture pipeline with MLflow and PostgreSQL]

## 🏗️ Arquitectura y Tecnologías
* **Entorno:** Docker & Docker Compose
* **Exploración:** JupyterLab
* **Procesamiento de Datos:** Pandas / PyArrow (Formato Parquet)
* **Modelado:** Scikit-Learn, XGBoost
* **Tracking de ML:** MLflow + PostgreSQL (Backend Store)

## 📂 Estructura del Repositorio
```
├── data/
│   ├── bronze/         # Datos crudos (JSON/Parquet desde la API)
│   ├── silver/         # Datos limpios y normalizados
│   └── gold/           # Features listas para el modelo (Feature Store)
├── docker-compose.yml  # Infraestructura del proyecto
├── notebooks/          # Exploración y pruebas en Jupyter
├── src/
│   ├── ingestion/      # Scripts de extracción (Ej. Open-Meteo API)
│   ├── processing/     # Limpieza y transformación de datos
│   └── training/       # Entrenamiento y registro en MLflow
└── README.md
```

## 🚀 Guía de Instalación y Despliegue

1.  **Clonar y Configurar Entorno**
    ```bash
    # Clonar el repositorio
    git clone https://github.com/ctobar96/Prediccion-de-Demanda-Energetica.git
    cd Prediccion-de-Demanda-Energetica

    # Crear el entorno virtual
    python -m venv env

    # Activar el entorno virtual
    # Si estás en Windows:
    env\Scripts\activate

    # Si estás en macOS/Linux:
    # source env/bin/activate

    # Instalar las dependencias
    pip install -r requirements.txt
    ```

2.  **Levantar la infraestructura con Docker:**
    ```bash
    docker-compose up -d
    ```

3.  **Acceder a los servicios:**
    * **JupyterLab:** [http://localhost:8888](http://localhost:8888) (Entorno de desarrollo)
    * **MLflow UI:** [http://localhost:5000](http://localhost:5000) (Dashboard de modelos)

## 🗺️ Hoja de Ruta de Desarrollo (Checklist)

- [x] **Fase 1: Infraestructura:** Configuración de contenedores (Postgres, MLflow, Jupyter).
- [ ] **Fase 2: Ingesta (Capa Bronce):** Programar la extracción de datos de la API meteorológica y guardarlos en formato Parquet.
- [ ] **Fase 3: Procesamiento (Capa Plata/Oro):** Limpiar valores nulos, crear variables temporales (hora del día, día de la semana, promedios móviles) y guardar el dataset final.
- [ ] **Fase 4: Entrenamiento (XGBoost):** Entrenar el modelo predictivo, conectando el script con MLflow para registrar métricas ($R^2$, RMSE) y guardar el modelo en el *Model Registry*.
- [ ] **Fase 5: Orquestación (Opcional):** Automatizar la ejecución de los scripts usando Apache Airflow o un cron job simple.

## 🔒 Roadmap Futuro
* Implementación de privacidad diferencial en la capa de transformación para anonimizar los datos de consumo subyacentes, asegurando un presupuesto de privacidad $\epsilon \leq 2.0$ antes de que los datos lleguen a la fase de entrenamiento.
* Integración de un pipeline CI/CD con GitHub Actions para testeo automático del código fuente.

---
*Desarrollado para demostrar competencias avanzadas en Data Engineering y ciclo de vida de Machine Learning.*