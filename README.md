# challenge-Telecom-X-parte-2


# Predicción de Churn de Clientes Telco 📈

Este proyecto se enfoca en la predicción de la rotación (Churn) de clientes en una empresa de telecomunicaciones, utilizando técnicas de Machine Learning. El objetivo principal es identificar a los clientes con alta probabilidad de irse para implementar estrategias de retención proactivas.

---

## 📄 Tabla de Contenidos

1.  [Descripción del Proyecto](#-descripción-del-proyecto)
2.  [Análisis y Modelado](#-análisis-y-modelado)
3.  [Resultados Clave](#-resultados-clave)
4.  [Factores Clave del Churn](#-factores-clave-del-churn)
5.  [Recomendaciones Estratégicas](#-recomendaciones-estratégicas)
6.  [Estructura del Repositorio](#-estructura-del-repositorio)
7.  [Cómo Usar el Proyecto](#-cómo-usar-el-proyecto)
8.  [Tecnologías Utilizadas](#-tecnologías-utilizadas)
9.  [Autor](#-autor)

---

## 🚀 Descripción del Proyecto

En el competitivo sector de las telecomunicaciones, la **rotación de clientes (Churn)** es un desafío constante. La pérdida de clientes impacta directamente en los ingresos y el crecimiento. Este proyecto aborda este problema desarrollando un modelo predictivo que permite anticipar qué clientes están en riesgo de Churn, brindando a la empresa la oportunidad de intervenir a tiempo.

El proceso incluyó:
* **Recolección y Preparación de Datos:** Carga, aplanamiento de estructuras anidadas (diccionarios), limpieza de datos y tratamiento de valores faltantes.
* **Análisis Exploratorio de Datos (EDA):** Entendimiento de las distribuciones de las variables y su relación con el Churn.
* **Ingeniería de Características:** Creación de nuevas variables relevantes y transformación de categóricas a numéricas (One-Hot Encoding).
* **Modelado Predictivo:** Entrenamiento y evaluación de modelos de clasificación (Regresión Logística y Random Forest).
* **Interpretación de Resultados:** Identificación de los factores más influyentes en el Churn para informar decisiones de negocio.

## 📊 Análisis y Modelado

El análisis se realizó en un conjunto de datos de clientes de telecomunicaciones, el cual contenía información demográfica, servicios contratados, información de facturación y el estado de Churn.

### Fases del Análisis:

1.  **Carga y Limpieza:** Se cargaron los datos desde una URL, se aplanaron las columnas con estructuras de diccionario y se trató el problema de los valores nulos en `TotalCharges` (rellenándolos con 0). Un paso crítico fue la **limpieza de valores vacíos en la variable objetivo `Churn`**, asegurando que solo contenga `0` (No Churn) y `1` (Churn).
2.  **Ingeniería y Transformación de Características:** Se creó la columna `Cuentas_Diarias` y se estandarizaron todas las columnas binarias a `0` y `1`. Las variables categóricas (`Servicio_Internet`, `Tipo_Contrato`, `Metodo_Pago`) se convirtieron utilizando **One-Hot Encoding** y las variables numéricas se **escalaron** con `StandardScaler` para preparar los datos para el modelado.
3.  **Modelado Predictivo:** Entrenamiento y evaluación de modelos de clasificación (Regresión Logística y Random Forest). Los datos se dividieron en conjuntos de entrenamiento (80%) y prueba (20%), estratificando por la variable objetivo `Churn` para mantener la proporción de clases.

### Visualizaciones Clave del EDA:

Aquí se muestra la distribución de la variable objetivo Churn y algunas características categóricas importantes.

![Distribución de Clientes por Churn](distribución_de_la_rotación.png)
*Distribución de la variable objetivo 'Churn', mostrando el desbalance de clases.*

---

## ✅ Resultados Clave

La evaluación de los modelos se centró en métricas clave para problemas de clasificación desbalanceados...
---

## 📊 Análisis y Modelado

El análisis se realizó en un conjunto de datos de clientes de telecomunicaciones, el cual contenía información demográfica, servicios contratados, información de facturación y el estado de Churn.

### Fases del Análisis:

1.  **Carga y Limpieza:** Se cargaron los datos desde una URL, se aplanaron las columnas con estructuras de diccionario y se trató el problema de los valores nulos en `TotalCharges` (rellenándolos con 0). Un paso crítico fue la **limpieza de valores vacíos en la variable objetivo `Churn`**, asegurando que solo contenga `0` (No Churn) y `1` (Churn).
2.  **Ingeniería y Transformación de Características:** Se creó la columna `Cuentas_Diarias` y se estandarizaron todas las columnas binarias a `0` y `1`. Las variables categóricas (`Servicio_Internet`, `Tipo_Contrato`, `Metodo_Pago`) se convirtieron utilizando **One-Hot Encoding** y las variables numéricas se **escalaron** con `StandardScaler` para preparar los datos para el modelado.
3.  **Modelado Predictivo:** Se evaluaron dos modelos de clasificación:
    * **Regresión Logística:** Un modelo lineal, interpretable y eficiente.
    * **Random Forest:** Un modelo de ensamble robusto, capaz de capturar relaciones no lineales.
    Los datos se dividieron en conjuntos de entrenamiento (80%) y prueba (20%), estratificando por la variable objetivo `Churn` para mantener la proporción de clases.

---

## ✅ Resultados Clave

La evaluación de los modelos se centró en métricas clave para problemas de clasificación desbalanceados, especialmente el **Recall** (sensibilidad para detectar el Churn) y **ROC-AUC** (capacidad general del modelo para distinguir entre clases).

| Modelo              | Accuracy | Precision (Churn=1) | Recall (Churn=1) | F1-Score (Churn=1) | ROC-AUC |
| :------------------ | :------- | :------------------ | :--------------- | :----------------- | :------ |
| **Regresión Logística** | **0.8026** | **0.6364** | **0.5428** | **0.5859** | **0.8440** |
| Random Forest       | 0.7847   | 0.6007              | 0.4866           | 0.5377             | 0.8195  |

**Conclusión del Modelado:** El modelo de **Regresión Logística** mostró un rendimiento superior, especialmente en su capacidad para identificar clientes que rotan (mayor Recall y ROC-AUC), lo cual es crucial para la proactividad en las estrategias de retención.

---

## 🎯 Factores Clave del Churn

La interpretación del modelo de Regresión Logística y el análisis de importancia de características del Random Forest nos permitieron identificar las variables con mayor influencia en la probabilidad de Churn:

### Importancia de Características (Random Forest):
Las características se ordenan por su contribución al modelo, indicando su poder predictivo.
![Importancia de Características (Random Forest)](visualizations/característica_importancia.png)
*Gráfico de barras mostrando la importancia de las variables en el modelo Random Forest.*

### Coeficientes de la Regresión Logística (Influencia y Dirección):
Los coeficientes revelan la dirección (+/-) y la magnitud de la relación de cada característica con la probabilidad de Churn.
![Coeficientes de Regresión Logística](visualizations/coeficientes_logísticos.png)
*Gráfico de barras mostrando la influencia y dirección de las variables en el modelo de Regresión Logística.*

| Característica                        | Coeficiente (Dirección) | Impacto                                                                                                    |
| :------------------------------------ | :---------------------- | :--------------------------------------------------------------------------------------------------------- |
| **Antiguedad_Meses** | -1.43 (Negativo)        | **Mayor antigüedad = Menor Churn.** Es el factor más influyente para la retención.                         |
| **Tipo_Contrato_Two year** | -1.24 (Negativo)        | Los contratos de **dos años** reducen drásticamente el Churn.                                              |
| Servicio_Telefono                   | -0.69 (Negativo)        | Tener servicio de teléfono está asociado con menor Churn.                                                  |
| Tipo_Contrato_One year              | -0.62 (Negativo)        | Los contratos de **un año** también reducen significativamente el Churn.                                   |
| Servicio_Internet_No                | -0.58 (Negativo)        | Los clientes sin servicio de internet son menos propensos a rotar (posiblemente solo con teléfono fijo).    |
| Soporte_Tecnico                     | -0.40 (Negativo)        | Contratar soporte técnico reduce el Churn.                                                                 |
| Seguridad_Online                    | -0.37 (Negativo)        | Los servicios de seguridad online reducen el Churn.                                                        |
| **Cargos_Totales** | +0.68 (Positivo)        | A **mayor cargo total** (acumulado), mayor probabilidad de Churn. Esto es crucial y puede indicar insatisfacción de valor. |
| **Servicio_Internet_Fiber optic** | +0.57 (Positivo)        | Los clientes con **fibra óptica** tienen mayor probabilidad de Churn. Posibles problemas de servicio o altas expectativas. |
| Facturacion_Electronica             | +0.38 (Positivo)        | Los clientes con facturación electrónica son más propensos a rotar.                                        |

---
---

## 💡 Recomendaciones Estratégicas

Con base en estos hallazgos, se proponen las siguientes acciones para mitigar el Churn:

1.  **Foco en la Retención Temprana:** Implementar programas de bienvenida y seguimiento intensivo durante los primeros **3-6 meses** de servicio, ya que la baja antigüedad es el mayor predictor de Churn.
2.  **Incentivar Contratos de Largo Plazo:** Crear ofertas y beneficios atractivos para que los clientes con contratos mes a mes migren a planes de 1 o 2 años.
3.  **Análisis y Optimización de la Oferta de Fibra Óptica:** Investigar y mejorar la experiencia del cliente con el servicio de fibra óptica, ya que es un factor de alto riesgo de Churn. Evaluar la calidad del servicio, el soporte y la competitividad de los precios.
4.  **Revisar la Estrategia de Precios en Altas Facturaciones:** Analizar si los clientes con altos `Cargos_Totales` perciben un valor adecuado por el precio que pagan. Considerar ofertas de valor añadido o reestructuración de planes.
5.  **Promoción de Servicios de Valor Agregado:** Fomentar la adopción de servicios como `Soporte_Tecnico` y `Seguridad_Online`, ya que actúan como factores protectores contra el Churn.
6.  **Implementar un Sistema de Alertas:** Utilizar el modelo de Regresión Logística para generar alertas automáticas para el equipo de retención cuando un cliente alcance un umbral de riesgo de Churn, permitiendo intervenciones proactivas y personalizadas.

---

## 📂 Estructura del Repositorio
.
├── notebooks/
│   └── 01_exploracion_limpieza_y_modelado.ipynb  # Notebook principal con todo el proceso
├── src/
│   ├── data_processing.py                     # Funciones para limpieza y preprocesamiento
│   └── model_training.py                      # Funciones para entrenamiento y evaluación
├── data/
│   ├── raw/
│   │   └── Telco-Customer-Churn.json          # Datos originales
│   └── processed/
│       └── df_clientes_processed.csv          # Datos limpios y procesados
├── models/
│   └── logistic_regression_model.pkl          # Modelo de Regresión Logística entrenado
├── visualizations/
│   └── churn_distribution.png                 # Gráficos EDA
│   └── feature_importance.png                 # Gráfico de importancia de características
├── README.md                                  # Este archivo
├── requirements.txt                           # Dependencias del proyecto
└── .gitignore                                 # Archivos a ignorar por Git

---
---

## 🛠️ Cómo Usar el Proyecto

Para replicar y ejecutar este proyecto localmente:

1.  **Clonar el repositorio:**
    ```bash
    git clone [https://github.com/tu_usuario/nombre_del_repositorio.git](https://github.com/tu_usuario/nombre_del_repositorio.git)
    cd nombre_del_repositorio
    ```
2.  **Crear un entorno virtual (opcional pero recomendado):**
    ```bash
    python -m venv venv
    # En Windows:
    .\venv\Scripts\activate
    # En macOS/Linux:
    source venv/bin/activate
    ```
3.  **Instalar las dependencias:**
    ```bash
    pip install -r requirements.txt
    ```
    (Asegúrate de crear un `requirements.txt` con `pip freeze > requirements.txt` después de instalar todas las librerías usadas en tu notebook).
4.  **Ejecutar el Notebook:**
    Abre el notebook `notebooks/01_exploracion_limpieza_y_modelado.ipynb` con Jupyter Notebook o JupyterLab y ejecuta todas las celdas en orden.

---

## 💻 Tecnologías Utilizadas

* Python 3.x
* Pandas
* NumPy
* Scikit-learn
* Matplotlib
* Seaborn

---

## 🧑‍💻 Autor

* **Maria Cristina González ** -  LinkedIn [www.linkedin.com/in/maria-cristina-gonzalez-15b0a3346] -  GitHub [https://github.com/CrystyGzz]
