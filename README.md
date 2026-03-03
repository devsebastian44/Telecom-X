# 📡 Telecom X — Análisis de Evasión de Clientes (Churn)

<p align="center">
  <img src="./Img/Badge.png" alt="Insignia Oracle Next Education" width="450"/>
</p>

Proyecto de análisis de datos desarrollado para **Telecom X** con el objetivo de identificar los factores que llevan a los clientes a cancelar sus servicios, como insumo para el desarrollo de modelos predictivos y estrategias de retención.

---

## 📁 Estructura del repositorio

```
📦 TelecomX-Churn
 ┣ 📄 TelecomX_Data.json          # Dataset original (7.267 registros, estructura anidada)
 ┣ 📓 TelecomX_LATAM.ipynb        # Notebook principal con el análisis completo
 ┣ 📄 TelecomX_diccionario.md     # Diccionario de variables del dataset
 ┣ 📄 TelecomX_clean.csv          # Dataset limpio exportado (generado al ejecutar el notebook)
 ┗ 📄 README.md                   # Este archivo
```

---

## 🎯 Objetivo

Comprender qué factores están asociados a la cancelación de servicios en Telecom X, mediante un proceso completo de **ETL + EDA**, para que el equipo de Data Science pueda avanzar en modelos predictivos.

---

## 🔄 Pipeline del proyecto

### 📌 1. Extracción
- Carga del archivo `TelecomX_Data.json` (estructura JSON anidada con 4 sub-objetos por cliente: `customer`, `phone`, `internet`, `account`)
- Aplanado de la estructura con `pd.json_normalize`

### 🔧 2. Transformación
- Renombrado y aplanado de columnas anidadas
- Corrección de tipos: `TotalCharges` a `float`, `SeniorCitizen` de `0/1` a `No/Yes`
- Limpieza de valores vacíos en la variable objetivo `Churn`
- Imputación de nulos en `TotalCharges` con la mediana
- Estandarización: `No internet service` / `No phone service` → `No`
- **Feature engineering:**
  - `TotalServices` — número total de servicios contratados por cliente
  - `TenureGroup` — segmento de antigüedad (0-12, 13-24, 25-48, 49-72 meses)
  - `Churn_num` — variable objetivo numérica para correlaciones

### 📊 3. Análisis EDA

| # | Visualización |
|---|--------------|
| 1 | Distribución global de Churn (barras + pie) |
| 2 | Variables demográficas vs Churn |
| 3 | Tipo de contrato y método de pago vs Churn |
| 4 | Servicios de internet y add-ons vs Churn |
| 5 | Histogramas de tenure, cargos mensuales y totales |
| 6 | Churn por segmento de antigüedad |
| 7 | Tasa de churn según número de servicios contratados |
| 8 | Boxplots de cargos por tipo de contrato |
| 9 | Mapa de calor de correlaciones |

### 📄 4. Informe Final
Conclusiones, tabla de recomendaciones estratégicas y próximos pasos — incluidos en la última sección del notebook.

---

## 🔑 Principales hallazgos

- **Tasa de churn global: ~26–27%** sobre 7.267 clientes
- El **tipo de contrato** es el predictor más fuerte: mes a mes tiene ~42–45% de churn vs ~3% en contratos bianuales
- Los clientes nuevos (**0–12 meses**) son el segmento de mayor riesgo
- El **cheque electrónico** como método de pago se asocia con la mayor tasa de churn (~45%)
- La ausencia de `OnlineSecurity` y `TechSupport` aumenta significativamente el riesgo de churn
- Clientes con **fibra óptica** tienen mayor churn que los de DSL, posiblemente por insatisfacción con el precio-valor

---

## 🛠️ Tecnologías utilizadas

| Librería | Uso |
|----------|-----|
| `pandas` | Manipulación y transformación de datos |
| `numpy` | Operaciones numéricas |
| `matplotlib` | Visualizaciones base |
| `seaborn` | Visualizaciones estadísticas |
| `json` | Carga y parseo del dataset |

---

## ▶️ Cómo ejecutar

1. Clonar el repositorio o subir los archivos a Google Colab
2. Asegurarse de que `TelecomX_Data.json` esté en el mismo directorio que el notebook
3. Ejecutar las celdas en orden (Menú → **Runtime > Run all**)
4. El dataset limpio se exportará automáticamente como `TelecomX_clean.csv`

> **Nota:** Para usar en Colab desde URL, descomentar la Opción B en la celda de extracción y actualizar el enlace raw del repositorio.

---

## 👤 Autor

Proyecto desarrollado como parte del programa de formación en Data Science — **Alura LATAM**.
