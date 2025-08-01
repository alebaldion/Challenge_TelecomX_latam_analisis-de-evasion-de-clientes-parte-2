# Challenge_TelecomX_latam_analisis-de-evasion-de-clientes-parte-2

Este repositorio contiene la segunda fase del proyecto de análisis de datos para Telecom X, enfocada en la construcción y evaluación de modelos de Machine Learning para predecir la cancelación de clientes (churn).

## 🎯 Propósito del Análisis

El objetivo principal de este proyecto es desarrollar un pipeline de modelado predictivo para identificar a los clientes con mayor probabilidad de cancelar sus servicios. Al anticipar el churn, Telecom X puede implementar estrategias de retención proactivas, reducir la pérdida de ingresos y mejorar la satisfacción del cliente.

## 📂 Estructura del Proyecto

El proyecto está organizado de la siguiente manera:

```
.
├── telecomx_datos_tratados.csv   # Dataset limpio utilizado para el modelado
├── Telecom_X_Modelado_Churn.ipynb # Notebook de Jupyter con todo el proceso
└── README.md                     # Este archivo de documentación
```

## 🛠️ Proceso de Preparación de Datos y Modelado

El pipeline desarrollado en el notebook sigue los siguientes pasos:

1.  **Carga y Limpieza:** Se cargan los datos previamente tratados y se eliminan columnas irrelevantes como `customerID`.
2.  **Codificación (Encoding):** Las variables categóricas (ej. 'Contract') se convierten a formato numérico usando One-Hot Encoding (`pd.get_dummies`) para ser compatibles con los modelos.
3.  **Manejo de Desbalance:** Se identifica un fuerte desbalance de clases (más clientes que no cancelan que los que sí). Se aplica la técnica **SMOTE (Synthetic Minority Over-sampling Technique)** sobre el conjunto de entrenamiento para crear un dataset balanceado y evitar que el modelo se sesgue hacia la clase mayoritaria.
4.  **Separación de Datos:** El conjunto de datos se divide en **80% para entrenamiento** y **20% para prueba**, asegurando que la proporción de churn se mantenga en ambos (`stratify`).
5.  **Normalización:** Las características numéricas se estandarizan (`StandardScaler`) para que los modelos sensibles a la escala, como la Regresión Logística, funcionen correctamente.
6.  **Modelado:** Se entrenan y evalúan dos modelos:
      * **Regresión Logística:** Un modelo lineal, interpretable y sensible a la escala de los datos.
      * **Random Forest:** Un modelo basado en árboles, robusto y que no requiere normalización.
7.  **Evaluación:** Los modelos se comparan usando una Matriz de Confusión y métricas como Precisión, Recall y F1-Score, con un enfoque especial en el **Recall** para la clase "Churn".

## 📊 Insights y Gráficos Clave

El análisis reveló que los principales impulsores de la cancelación son:

  * **Tener un contrato mes a mes.**
  * **Tener una baja antigüedad (tenure).**
  * **No contar con servicios de seguridad o soporte técnico.**

*(Nota: Deberías reemplazar la URL de arriba con una URL real de tu gráfico después de subirlo a un servicio como Imgur)*

## 🚀 Cómo Ejecutar el Cuaderno

Para ejecutar el notebook `Telecom_X_Modelado_Churn.ipynb` y replicar el análisis, sigue estos pasos:

1.  **Clona el repositorio:**

    ```bash
    git clone https://github.com/tu-usuario/tu-repositorio.git
    cd tu-repositorio
    ```

2.  **Instala las bibliotecas necesarias:**
    Asegúrate de tener un entorno de Python (3.7+) y luego instala las dependencias.

    ```bash
    pip install pandas numpy scikit-learn seaborn matplotlib imbalanced-learn
    ```

3.  **Ejecuta Notebook:**
    Inicia el servidor en tu terminal.

    ```bash
  Abre el archivo .ipynb en Google Colab o Jupyter Notebook.
    ```

    Luego, abre el archivo `Telecom_X_Modelado_Churn.ipynb` en tu navegador y ejecuta las celdas en orden. Los datos se cargarán directamente desde el archivo `telecomx_datos_tratados.csv` incluido en el repositorio.
