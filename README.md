# Ciencia de Datos en Descubrimiento de Fármacos
### Daniel Felipe Victoria Muñoz - Universidad Nacional de Colombia · Extensión UNAL 2026

> Curso de 40 horas para químicos farmacéuticos, químicos, biólogos o cualquier profesional interesado sin experiencia previa en programación.  
> Énfasis diferenciador: **Colección, Curación y Visualización de datos moleculares desde ChEMBL**.

---

## Sobre el curso

Este curso nace de la experiencia del programa **AI4MedChem** de la Universidad de Münster  ([Koch group](https://www.uni-muenster.de/Chemie.pz/forschen/ag/koch/ai4medchem.html)), adaptado al contexto latinoamericano y al perfil de los profesionales. El objetivo no es formar ingenieros de ML, sino profesionales de las ciencias de la vida capaces de **entender, obtener, curar y modelar datos químicos** para el descubrimiento de fármacos y otras aplicaciones de interes.

- **Modalidad:** Extensión UNAL · Virtual sincrónica  
- **Duración:** 40 horas · 7 semanas · 3 sesiones/semana de 2h  
- **Horario:** Lunes, Martes y Jueves · 6:00–8:00 pm (hora Bogotá) / (27 de abril al 18 de junio del 2026) 
- **Requisitos:** Ninguno de programación. Conocimiento básico de química orgánica y bioquímica.  
- **Plataforma:** Google Colab (sin instalación local requerida)

---

## Estructura del repositorio

```
intro_pharma_ai/
│
├── README.md                        ← Este archivo
│
├── notebooks/
│   ├── 01 Introduccion a Jupiter.ipynb              ✅ Existente
│   ├── 02 Contexto Pipeline.ipynb                   🆕 Nuevo 
│   ├── 03 Introduccion a Python.ipynb               ✅ Existente 
│   ├── NB-03_Quimioinformatica_RDKit.ipynb    ✅ Existente
│   ├── NB-DATA-01_Coleccion_ChEMBL.ipynb      🆕 Nuevo ★
│   ├── NB-DATA-02_Curacion_Molecular.ipynb    🆕 Nuevo ★
│   ├── NB-DATA-03_Features_Espacio_Quimico.ipynb 🆕 Nuevo ★
│   ├── NB-04_Regresion_Lineal.ipynb           ✅ Existente
│   ├── NB-05_Data_Science_EDA.ipynb           ✅ Existente
│   ├── NB-ML-01_Clasificacion_QSAR.ipynb      🆕 Nuevo
│   ├── NB-07_Primera_Red_Neuronal.ipynb       ✅ Existente
│   ├── NB-08_PyTorch.ipynb                    ✅ Existente
│   ├── NB-10_Transfer_Learning.ipynb          ✅ Existente
│   ├── NB-11_RNN_Generativa.ipynb             ✅ Existente
│   ├── NB-12_Autoencoders.ipynb               ✅ Existente
│   ├── NB-13_Graph_Neural_Networks.ipynb      ✅ Existente
│   ├── NB-STRUCT-01_Docking_AlphaFold.ipynb   🆕 Nuevo
│   ├── NB-14_Resumen_Cierre.ipynb             ✅ Existente
│   └── NB-PROJECT_Template_Proyecto.ipynb     🆕 Nuevo
│
└── data/
    └── ejemplo_compuestos.csv                 🆕 Dataset de práctica sem 1
```

> ★ Los notebooks `NB-DATA-01`, `NB-DATA-02` y `NB-DATA-03` constituyen el núcleo diferenciador del curso.

---

## Plan de 7 semanas

### Semana 1 — Contexto, herramientas y Python
**6 horas · 3 sesiones**

El objetivo de esta semana no es el código: es la motivación. Los estudiantes deben entender por qué vale la pena aprender ciencia de datos antes de escribir su primera línea de Python.

| Sesión | Tema | Actividad práctica |
|--------|------|--------------------|
| Ses 1 | ¿Por qué IA en descubrimiento de fármacos? Pipeline target → fármaco. Casos: imatinib, nirmatrelvir. Introducción a ChEMBL. | Explorar ChEMBL web: buscar un target (EGFR), leer $IC_{50}$, entender qué es un assay |
| Ses 2 | Jupyter/Colab, Python básico: variables, tipos, listas, condicionales, ciclos | Ejecutar NB-01 guiado. Mini-reto: clasificar compuestos como activo/inactivo según $IC_{50}$ |
| Ses 3 | Funciones, NumPy, pandas, Matplotlib | Cargar CSV de compuestos, calcular estadísticas de $IC_{50}$, graficar distribución |

**Notebooks:** NB-00 (nuevo), NB-01, NB-02

---

### Semana 2 — Quimioinformática y colección de datos
**6 horas · 3 sesiones**

La semana que conecta la química que los estudiantes ya saben con la representación computacional, y abre la puerta a los datos reales.

| Sesión | Tema | Actividad práctica |
|--------|------|--------------------|
| Ses 4 | Representación molecular: SMILES, InChI. RDKit: manipulación y visualización de moléculas. Fingerprints (Morgan, MACCS). Similitud de Tanimoto. | Dibujar moléculas conocidas con RDKit, calcular similitud entre aspirina e ibuprofeno |
| Ses 5 | Estructura de ChEMBL: targets, assays, bioactividad. ¿Qué significa $IC_{50}$, $K_i$, $\%$ inhibición? Unidades y contexto farmacológico. | Navegar ChEMBL API desde Python: primer query a un target de interés |
| Ses 6 | Colección práctica con `chembl_webresource_client`. Filtros por tipo de actividad, organismo, tipo de ensayo. Exportar a DataFrame. | Colectar dataset completo de un target (EGFR o Mpro) para usar en semanas 3 y 4 |

**Notebooks:** NB-03 (existente), NB-DATA-01 🆕

---

### Semana 3 — Curación y creación de datos ★
**6 horas · 3 sesiones**

El módulo más diferenciador del curso. La calidad del modelo depende casi completamente de la calidad del dato. Esta semana es el corazón del programa.

| Sesión | Tema | Actividad práctica |
|--------|------|--------------------|
| Ses 7 | Problemas del dato crudo: duplicados, valores faltantes, SMILES inválidos, mezcla de unidades ($nM$ vs $µM$ vs $mg/mL$). | Diagnóstico del dataset de la semana 2: ¿cuántos problemas tiene? |
| Ses 8 | Curación práctica: conversión de unidades, estandarización de SMILES con RDKit, eliminación de sales, clasificación activo/inactivo por umbral de $IC_{50}$. $|_ $Curar $el data$set del target elegido: de dato crudo a dataset limpio |
| Ses 9 | Descriptores fisicoquímicos (LogP, MW, HBD, HBA, Lipinski). EDA químico. PCA y t-SNE para visualizar el espacio químico. | Crear mapa del espacio químico del dataset curado |

**Notebooks:** NB-DATA-02 🆕, NB-DATA-03 🆕, NB-05 (apoyo EDA)

---

### Semana 4 — Modelos predictivos clásicos (QSAR)
**6 horas · 3 sesiones**

La semana donde se cierra el primer ciclo completo: colectar → curar → modelar → evaluar. Los estudiantes construyen su primer modelo real con datos de ChEMBL.

| Sesión | Tema | Actividad práctica |
|--------|------|--------------------|
| Ses 10 | Regresión lineal: predecir $IC_{50}$ con descriptores moleculares. Concepto de variable respuesta, features, overfitting. | Entrenar modelo de regresión sobre dataset curado. Interpretar R² y RMSE. |
| Ses 11 | Clasificación: Random Forest para predecir activo/inactivo. Métricas: AUC-ROC, F1, MCC. Importancia de features. | Entrenar Random Forest. Visualizar curva ROC. Identificar qué descriptores importan más. |
| Ses 12 | Train/test split, cross-validation. Pipeline completo. Evaluación honesta del modelo. | Pipeline end-to-end: desde CSV de ChEMBL hasta reporte de desempeño del modelo |

**Notebooks:** NB-04 (existente), NB-ML-01 🆕

---

### Semana 5 — Redes neuronales para química
**6 horas · 3 sesiones**

Teoría mínima necesaria, siempre anclada a ejemplos moleculares. El objetivo no es dominar PyTorch sino entender qué hace la red y cuándo tiene sentido usarla.

| Sesión | Tema | Actividad práctica |
|--------|------|--------------------|
| Ses 13 | Fundamentos intuitivos de redes neuronales: perceptrón, capas, activaciones, backpropagation conceptual. ¿Cuándo supera a Random Forest? | Visualizar una red neuronal simple. Comparar predicciones vs Random Forest del NB-ML-01. |
| Ses 14 | Primera red neuronal en PyTorch para predicción de bioactividad. Hiperparámetros básicos: learning rate, epochs, batch size. | Entrenar red neuronal sobre el dataset de la semana 3. Comparar con modelos anteriores. |
| Ses 15 | Moléculas como grafos: átomos = nodos, enlaces = aristas. Graph Neural Networks (GNN): intuición y aplicación. | Ejecutar NB-13: GNN para predicción de propiedades moleculares |

**Notebooks:** NB-07, NB-08, NB-13 (todos existentes)

---

### Semana 6 — Modelos avanzados: generativa, lenguaje y estructura
**6 horas · 3 sesiones**

La semana del horizonte. El objetivo es mostrar el estado del arte del campo, no exigir que los estudiantes dominen estas técnicas.

| Sesión | Tema | Actividad práctica |
|--------|------|--------------------|
| Ses 16 | Química generativa: RNNs para generación de SMILES válidos. Autoencoders variacionales (VAE) para diseño de novo. Introducción conceptual a REINVENT4. | Generar moléculas con un modelo RNN pre-entrenado. Analizar validez química de las salidas. |
| Ses 17 | Modelos de lenguaje molecular: ChemBERTa, MolBERT. Transfer learning en química. ¿Qué aprende un modelo de lenguaje sobre moléculas? | Usar embeddings de ChemBERTa para visualizar el espacio químico de un dataset |
| Ses 18 | Docking molecular básico: AutoDock Vina. AlphaFold3 (introducción). Virtual screening guiado por modelos QSAR. | Demo: preparar ligando + proteína, correr docking, interpretar score de afinidad |

**Notebooks:** NB-11, NB-12, NB-10 (existentes), NB-STRUCT-01 🆕

---

### Semana 7 — Proyecto integrador y cierre
**4 horas · 2 sesiones**

El cierre del ciclo completo. Cada estudiante elige un target de su interés y aplica todo el pipeline aprendido.

| Sesión | Tema | Actividad práctica |
|--------|------|--------------------|
| Ses 19 | Trabajo en proyecto. Acompañamiento del docente. Resolución de dudas técnicas. | Pipeline completo con target elegido desde semana 1: colección → curación → features → modelo |
| Ses 20 | Presentaciones (5 min/estudiante). Reflexión crítica: limitaciones, sesgos, ética del dato. ¿Qué sigue? Recursos y comunidades. | Presentar resultados. Discusión grupal sobre calidad de datos y decisiones de modelado. |

**Notebooks:** NB-PROJECT 🆕, NB-14 (cierre conceptual)


---

## Notebooks nuevos a desarrollar

| Notebook | Semana | Descripción |
|----------|--------|-------------|
| `NB-00_Contexto_Pipeline.ipynb` | 1 | Pipeline drug discovery, casos reales (imatinib, nirmatrelvir), primera consulta a ChEMBL |
| `NB-DATA-01_Coleccion_ChEMBL.ipynb` | 2 | Query por target, filtros por actividad/unidad/organismo, exportar a DataFrame |
| `NB-DATA-02_Curacion_Molecular.ipynb` | 3 | Limpieza, conversión de unidades, estandarización SMILES, clasificación activo/inactivo |
| `NB-DATA-03_Features_Espacio_Quimico.ipynb` | 3 | Descriptores fisicoquímicos, PCA, t-SNE, mapa del espacio químico |
| `NB-ML-01_Clasificacion_QSAR.ipynb` | 4 | Pipeline Random Forest + métricas + interpretación farmacológica |
| `NB-STRUCT-01_Docking_AlphaFold.ipynb` | 6 | AutoDock Vina básico, visualización, introducción AlphaFold3 |
| `NB-PROJECT_Template_Proyecto.ipynb` | 7 | Template guiado con target a elección, rúbrica de evaluación integrada |

---

## Dependencias principales

```python
# Quimioinformática
rdkit
chembl_webresource_client

# Ciencia de datos
pandas
numpy
matplotlib
seaborn
scikit-learn

# Deep learning
torch
torch-geometric        # GNNs

# Estructura
autodock-vina          # Semana 6 (demo)
```

Todos los notebooks están diseñados para ejecutarse en **Google Colab** sin instalación local.  
Las celdas de instalación (`!pip install ...`) están incluidas al inicio de cada notebook.

---

## Filosofía del curso

1. **Los datos primero.** Antes de modelar, hay que entender de dónde vienen los datos, qué significan y cómo limpiarlos. Un modelo entrenado con datos mal curados es peor que ningún modelo.

2. **Dominio primero, código segundo.** Cada concepto computacional se introduce con un ejemplo farmacológico o bioquímico concreto. El código es el medio, no el fin.

3. **Ciclo completo, siempre.** Desde la semana 4, cada sesión práctica produce un output que conecta con la siguiente. Al final del curso, cada estudiante tiene un pipeline real, no ejercicios aislados.

4. **Horizonte, no dominio.** Las técnicas avanzadas (GNNs, VAEs, docking) se presentan para que los estudiantes sepan que existen y cuándo pedirlas, no para que las implementen desde cero.

---

## Créditos y referencias

- Repositorio base: [intro_pharma_ai](https://github.com/FelPVic/intro_pharma_ai)
- Inspiración: Curso AI4MedChem, Grupo Koch, Universidad de Münster
- Base de datos: [ChEMBL](https://www.ebi.ac.uk/chembl/) — European Bioinformatics Institute
- Docente: Daniel Felipe Victoria Muñoz QF, Dr. en Química Medicinal, Universidad de Münster · Profesor asociado Fundación Universitaria Salesiana

---

*Curso ofrecido a través de la Dirección de Extensión de la Universidad Nacional de Colombia.*  
*Para información sobre próximas ediciones: contactar a través del portal Hermes Extensión UNAL.*
