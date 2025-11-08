# Proyecto Final: Análisis del Valor de Mercado de Jugadores FIFA 23

## 📋 Descripción

Este proyecto realiza un análisis estadístico completo del valor de mercado de jugadores de FIFA 23 utilizando técnicas de **Métodos Lineales**. El objetivo es determinar qué factores futbolísticos y de mercado explican el valor de un jugador, construyendo una "historia" desde modelos simples hasta modelos lineales generalizados.

## 🎯 Objetivos del Análisis

- **Regresión Lineal Simple (RLS):** Modelo base con una sola variable predictora
- **Regresión Lineal Múltiple (RLM):** Modelo con múltiples predictores
- **Bondad de Ajuste:** Análisis de R², diagnósticos de residuos, VIF
- **Variables Categóricas:** Incorporación de pie dominante y posición
- **Modelos Lineales Generalizados (GLM):** GLM Gamma para modelar precios

## 📁 Estructura del Proyecto

```
fifa-proyecto-final/
├── .devcontainer/
│   └── devcontainer.json       # Configuración del entorno de desarrollo
├── data/
│   └── Fifa 23 Players Data.csv # Dataset original
├── output/                      # (Se generará al ejecutar el análisis)
│   └── analisis.html            # Reporte HTML generado
├── analisis.Rmd                 # Archivo principal de análisis en R Markdown
└── README.md                    # Este archivo
```

## 🚀 Instrucciones de Uso

### Opción 1: Usar Dev Container (Recomendado)

Esta es la forma más fácil y reproducible de ejecutar el proyecto. Requiere:
- **VS Code** instalado
- **Docker** instalado y en ejecución
- **Extensión "Dev Containers"** de VS Code

#### Pasos:

1. **Abrir el proyecto en VS Code:**
   ```bash
   cd /home/schafler/ITAM/fifa-proyecto-final
   code .
   ```

2. **Reabrir en contenedor:**
   - VS Code detectará el archivo `.devcontainer/devcontainer.json`
   - Aparecerá una notificación: **"Reopen in Container"**
   - Haz clic en **"Reopen in Container"**
   - Espera a que Docker construya el contenedor (primera vez tarda ~5-10 min)

3. **Ejecutar el análisis:**
   - Una vez dentro del contenedor, abre el archivo `analisis.Rmd`
   - En VS Code, presiona `Ctrl+Shift+K` (o el botón "Knit" si aparece)
   - O desde la terminal integrada:
     ```bash
     Rscript -e "rmarkdown::render('analisis.Rmd')"
     ```

4. **Ver el resultado:**
   - Se generará un archivo `analisis.html` en el directorio del proyecto
   - Ábrelo en tu navegador para ver el reporte completo

### Opción 2: Instalación Manual (Sin Docker)

Si prefieres no usar Docker, instala manualmente:

1. **Instalar R** (versión 4.0 o superior):
   - [Descargar R](https://cran.r-project.org/)

2. **Instalar RStudio** (opcional pero recomendado):
   - [Descargar RStudio](https://www.rstudio.com/products/rstudio/download/)

3. **Instalar librerías de R:**
   ```r
   install.packages(c("tidyverse", "car", "rmarkdown", "knitr", "corrplot"))
   ```

4. **Ejecutar el análisis:**
   - En RStudio: Abrir `analisis.Rmd` y hacer clic en "Knit"
   - Desde la consola de R:
     ```r
     rmarkdown::render("analisis.Rmd")
     ```

## 📊 Dataset

El dataset `Fifa 23 Players Data.csv` contiene información de miles de jugadores de FIFA 23:

- **Variables cuantitativas:** Overall, Potential, Age, Pace, Shooting, Passing, etc.
- **Variables categóricas:** Preferred Foot, Best Position, Nationality, Club
- **Variable respuesta:** Value (in Euro) - Valor de mercado

**Fuente:** [SoFIFA](https://sofifa.com/) / Kaggle

## 🔬 Metodología

El análisis sigue esta secuencia:

1. **EDA (Análisis Exploratorio):**
   - Limpieza de datos (conversión de "€1.5M" a valores numéricos)
   - Transformación logarítmica de `value_eur`
   - Visualizaciones de distribuciones y correlaciones

2. **Regresión Lineal Simple:**
   - Modelo: `log(value) ~ overall`
   - Interpretación de coeficientes y R²

3. **Regresión Lineal Múltiple:**
   - Modelo: `log(value) ~ overall + potential + age + international_reputation`
   - Análisis de significancia y mejora del ajuste

4. **Diagnósticos:**
   - Gráficos de residuos (linealidad, homocedasticidad, normalidad)
   - Cálculo de VIF (multicolinealidad)

5. **Variables Categóricas:**
   - Incorporación de `preferred_foot` y `position`
   - Interpretación de variables dummy

6. **GLM Gamma:**
   - Modelo: `glm(value_eur ~ ..., family = Gamma(link="log"))`
   - Comparación con OLS transformado

## 📈 Resultados Esperados

El análisis revelará:

- **Overall** es el predictor más fuerte del valor (~85-90% de correlación)
- **Edad** tiene un efecto negativo en el valor (jugadores mayores valen menos)
- **Potencial** y **reputación internacional** añaden valor significativo
- **Posición** y **pie dominante** tienen efectos moderados
- Los modelos explican ~75-85% de la variabilidad en el valor de mercado

## 🛠️ Tecnologías Utilizadas

- **Lenguaje:** R 4.x
- **Librerías:**
  - `tidyverse` (dplyr, ggplot2, readr)
  - `car` (VIF para multicolinealidad)
  - `rmarkdown` (generación de reportes)
  - `knitr` (integración de código y texto)
  - `corrplot` (matrices de correlación)
- **Entorno:** Docker + Dev Containers (rocker/tidyverse)

## 📝 Notas

- El código está completamente en **español** (comentarios e interpretaciones)
- Cada chunk de código incluye una **explicación detallada** de los resultados
- El reporte HTML generado es **autocontenido** (incluye gráficos y tablas)
- El proyecto es **100% reproducible** usando el Dev Container

## 👨‍💻 Autor

**[Tu Nombre]**
Proyecto Final - Métodos Lineales
ITAM - 2025

## 📧 Contacto

Para preguntas o comentarios sobre el análisis:
- Email: [tu_email@example.com]
- GitHub: [tu_usuario]

## 📄 Licencia

Este proyecto es para fines educativos (Proyecto Final de Métodos Lineales).

---

**¡Disfruta explorando los datos de FIFA 23!** ⚽📊
