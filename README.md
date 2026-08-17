<a id="inicio"></a>

<div align="center">

# Experimento A/B en Landing Page

### Analítica de conversión · Pruebas estadísticas · Decisión de negocio

Comparación de dos versiones de una página de inicio para identificar cuál genera **mayor conversión y valor económico por usuario**.

<p>
  <img alt="Python" src="https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white">
  <img alt="Jupyter" src="https://img.shields.io/badge/Jupyter-F37626?style=flat-square&logo=jupyter&logoColor=white">
  <img alt="VS Code" src="https://img.shields.io/badge/VS%20Code-007ACC?style=flat-square&logo=visualstudiocode&logoColor=white">
  <img alt="pandas" src="https://img.shields.io/badge/pandas-150458?style=flat-square&logo=pandas&logoColor=white">
  <img alt="NumPy" src="https://img.shields.io/badge/NumPy-013243?style=flat-square&logo=numpy&logoColor=white">
  <img alt="SciPy" src="https://img.shields.io/badge/SciPy-8CAAE6?style=flat-square&logo=scipy&logoColor=white">
  <img alt="Seaborn" src="https://img.shields.io/badge/Seaborn-Data%20Viz-4C72B0?style=flat-square">
  <img alt="statsmodels" src="https://img.shields.io/badge/statsmodels-Statistics-4051B5?style=flat-square">
</p>

<img src="assets/portada_experimento_ab.webp" alt="Portada del experimento A/B" width="100%">

<br>

[![Ver análisis completo](https://img.shields.io/badge/🔎_Ver_análisis_completo-Notebook-1f6feb?style=for-the-badge)](./Proyecto_Landing_Experiment_Portfolio.ipynb)
[![Ver resultados](https://img.shields.io/badge/📊_Ver_resultados-Resumen-238636?style=for-the-badge)](#resultados-clave)

</div>

---

## Navegación

[Sobre el proyecto](#sobre-el-proyecto) · [Resultados clave](#resultados-clave) · [Visualizaciones](#visualizaciones) · [Análisis estadístico](#analisis-estadistico) · [Recomendación](#recomendacion) · [Tecnologías](#tecnologias) · [Repositorio](#estructura-del-repositorio)

---

<a id="sobre-el-proyecto"></a>
## Sobre el proyecto

El objetivo fue evaluar un **experimento A/B** aplicado a una landing page y convertir sus resultados en una recomendación accionable para negocio. Se analizaron **40,000 usuarios** asignados de forma prácticamente equilibrada entre las versiones A y B durante el periodo del **1 al 28 de enero de 2026**.

El análisis responde cuatro preguntas principales:

- ¿Qué versión genera una **mayor tasa de conversión**?
- ¿Qué versión consigue un **mayor gasto promedio** entre los usuarios convertidos?
- ¿La **fuente de tráfico** está asociada con la conversión?
- ¿El **tipo de usuario** —nuevo o recurrente— cambia la probabilidad de convertir?

> **En una frase:** Landing B obtuvo mejores resultados tanto en conversión como en valor económico, y las pruebas estadísticas respaldan que las diferencias observadas difícilmente se deben únicamente al azar.

[↑ Volver al inicio](#inicio)

---

<a id="resultados-clave"></a>
## Resultados clave

| Indicador | Landing A | Landing B | Impacto observado |
|---|---:|---:|---:|
| Usuarios | 19,982 | 20,018 | Grupos balanceados |
| Conversiones | 2,512 | **3,194** | **+682** |
| Tasa de conversión | 12.57% | **15.96%** | **+3.38 pp** |
| Gasto promedio por usuario convertido | $61.09 | **$68.75** | **+$7.66 · +12.54%** |
| Ingreso total observado | $153,449.47 | **$219,572.68** | **+$66,123.21 · +43.09%** |

### Insight principal

**Landing B convierte mejor y genera mayor valor por cada usuario convertido.** Su tasa de conversión fue aproximadamente **27% mayor en términos relativos** frente a Landing A, mientras que el gasto promedio de los usuarios convertidos aumentó **12.54%**.

[↑ Volver al inicio](#inicio)

---

<a id="visualizaciones"></a>
## Visualizaciones

<table>
<tr>
<td width="50%" valign="top">
  <img src="assets/conversiones_landing.png" alt="Conversiones por Landing Page" width="100%"><br>
  <b>Conversiones por Landing Page</b><br>
  Landing B obtuvo 3,194 conversiones frente a 2,512 de Landing A.
</td>
<td width="50%" valign="top">
  <img src="assets/gasto_outliers.png" alt="Distribución del gasto y outliers" width="100%"><br>
  <b>Gasto y validación de outliers</b><br>
  La diferencia de gasto se mantuvo significativa incluso después de excluir valores extremos.
</td>
</tr>
<tr>
<td width="50%" valign="top">
  <img src="assets/trafico_conversion.png" alt="Conversión por fuente de tráfico" width="100%"><br>
  <b>Fuente de tráfico</b><br>
  La asociación es estadísticamente significativa, aunque la diferencia proporcional entre canales es pequeña.
</td>
<td width="50%" valign="top">
  <img src="assets/tipo_usuario_conversion.png" alt="Conversión por tipo de usuario" width="100%"><br>
  <b>Tipo de usuario</b><br>
  Nuevos y recurrentes presentan tasas de conversión prácticamente equivalentes.
</td>
</tr>
</table>

[↑ Volver al inicio](#inicio)

---

<a id="analisis-estadistico"></a>
## Análisis estadístico

| Pregunta | Prueba | Resultado |
|---|---|---|
| ¿El gasto promedio difiere entre A y B? | **t de Welch** | Diferencia significativa · `p ≈ 3.63 × 10⁻²¹` |
| ¿Los outliers explican la diferencia de gasto? | IQR + t de Welch | La diferencia permanece · `p ≈ 2.33 × 10⁻²⁰` |
| ¿La conversión difiere entre A y B? | **Z de proporciones** | Diferencia significativa · `p ≈ 3.76 × 10⁻²²` |
| ¿La fuente de tráfico se relaciona con conversión? | **Chi-cuadrado** | Existe asociación · `p = 0.034` |
| ¿El tipo de usuario se relaciona con conversión? | **Chi-cuadrado** | No hay evidencia suficiente · `p = 0.474` |

<details>
<summary><b>Ver validación de calidad de datos y metodología</b></summary>
<br>

Antes de realizar las pruebas se validó que:

- no existieran valores ausentes;
- los **40,000 `user_id` fueran únicos**;
- `converted` contuviera únicamente valores binarios 0/1;
- no existieran gastos negativos;
- los usuarios no convertidos tuvieran gasto igual a cero;
- las variables categóricas contuvieran únicamente categorías esperadas;
- los grupos A y B estuvieran balanceados.

**Técnicas aplicadas:** análisis exploratorio, validación de calidad, prueba de Levene, t de Welch, Z de proporciones, Chi-cuadrado de independencia, método IQR y visualización de datos.

</details>

[↑ Volver al inicio](#inicio)

---

<a id="recomendacion"></a>
## Recomendación de negocio

### Implementar Landing B como versión principal

La recomendación se sustenta en tres resultados convergentes:

1. **Mayor tasa de conversión:** 15.96% vs. 12.57%.
2. **Mayor gasto promedio por usuario convertido:** $68.75 vs. $61.09.
3. **Mayor ingreso total observado:** $219,572.68 vs. $153,449.47.

Las diferencias de conversión y gasto cuentan con respaldo estadístico y el resultado sobre gasto se mantiene incluso después de controlar los outliers.

Después de la implementación conviene continuar monitoreando **tasa de conversión, ingreso por usuario, fuente de tráfico, dispositivo y tipo de usuario**, para comprobar que el efecto se mantiene en operación real.

> **Decisión basada en datos:** el experimento aporta evidencia suficiente para elegir **Landing B** como la alternativa con mayor potencial de impacto comercial.

[↑ Volver al inicio](#inicio)

---

<a id="tecnologias"></a>
## Tecnologías y herramientas

**Lenguaje y entorno**  
`Python` · `Jupyter Notebook` · `Visual Studio Code`

**Manipulación y análisis**  
`pandas` · `NumPy`

**Estadística**  
`SciPy` · `statsmodels`

**Visualización**  
`Matplotlib` · `Seaborn`

[↑ Volver al inicio](#inicio)

---

<a id="estructura-del-repositorio"></a>
## Estructura del repositorio

```text
Proyecto_Experimento_A-B_en_Landing_Page/
│
├── README.md
├── Proyecto_Landing_Experiment_Portfolio.ipynb
├── datasets/
│   └── landing_experiment.csv
└── assets/
    ├── portada_experimento_ab.webp
    ├── conversiones_landing.png
    ├── gasto_outliers.png
    ├── trafico_conversion.png
    └── tipo_usuario_conversion.png
```

### ¿Quieres revisar el código?

El notebook contiene el proceso completo: exploración, limpieza y validación de datos, construcción de hipótesis, pruebas estadísticas, visualizaciones e interpretación de negocio.

➡️ **[`Abrir Proyecto_Landing_Experiment_Portfolio.ipynb`](./Proyecto_Landing_Experiment_Portfolio.ipynb)**

[↑ Volver al inicio](#inicio)

---

<div align="center">

### De datos a una decisión de negocio

**Experimento A/B · Estadística aplicada · Data Storytelling**

</div>
