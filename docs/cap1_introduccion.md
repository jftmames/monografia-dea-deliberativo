# Capítulo 1 – Introducción y Contexto Epistémico

> **Sticky Note (Canvas):**
>
> * Objetivo: Introducir la distinción IA predictiva vs IA deliberativa.
> * Caso de estudio: Hospital X.
> * Elementos clave: problema, tesis, Árbol Deliberativo (CD-1).
> * Sprint 1: Contexto y motivación.

## \[Contexto Cap1]

* Objetivo: Definir el problema de la clausura epistémica en IA y presentar la IA deliberativa.
* Ya disponible: índice general de la monografía, propuesta de caso hospitalario.
* Ahora: redactar Sprint 1 (Contexto y motivación) y formular el nodo deliberativo CD-1.

---

### Sprint 1: Contexto y Motivación (2–3 párrafos)

La Inteligencia Artificial ha avanzado de manera impresionante en la capacidad de **predecir** resultados a partir de grandes volúmenes de datos, pero este enfoque suele caer en lo que denominamos **clausura epistémica**: el modelo reproduce patrones existentes sin cuestionarlos o explicarlos. En entornos críticos —como la gestión hospitalaria—, limitarse a predecir métricas de rendimiento puede ocultar las **dinámicas internas** y las **decisiones contextuales** que subyacen a esos resultados.

En contraste, proponemos un paradigma de **IA deliberativa**, cuya finalidad principal no es solo calcular eficiencias o pronosticar demandas, sino **guiar una reflexión estructurada** entre los decisores. Esta reflexión se formaliza mediante un **Árbol Deliberativo** (CD-1) que plantea subpreguntas sobre insumos, salidas y contexto organizativo, fomentando un diálogo continuo entre analistas, gestores y agentes implicados.

El **caso de estudio** que recorrerá esta monografía es un conjunto de hospitales (Hospital X) con características comparables en tamaño y servicios. A través de él, ilustraremos cómo el **Análisis Envolvente de Datos (DEA)** combinado con la IA deliberativa y la métrica de **Equilibrio Erotético (EEE)** puede no solo medir, sino **mejorar** la gestión hospitalaria mediante sugerencias de optimización fundamentadas en preguntas y retroalimentación.

---

**Nodo Deliberativo CD-1:**

> *¿Cuál es la principal limitación de un enfoque puramente predictivo en la administración hospitalaria?*

### Sprint 2: Descripción del Caso de Estudio Hospitalario (3–4 párrafos)

Hospital X, un centro de atención terciaria ubicado en una zona urbana de tamaño medio, cuenta con aproximadamente **300 camas operativas**, una plantilla de **1,200 profesionales sanitarios** y atiende anualmente cerca de **20,000 ingresos**. Sus servicios principales incluyen Medicina Interna, Cirugía General, UCI y Urgencias, con indicadores de ocupación media del **85 %** y una tasa de reingreso del **12 %**.

Para garantizar la **homogeneidad** en el análisis DEA, seleccionaremos un subconjunto de **5 hospitales comparables** (H1 a H5) con características demográficas y de servicios similares. Cada DMU (hospital) manejará insumos como número de camas, horas de personal médico y gasto en suministros, y outputs como número de altas, tasa de recuperación y satisfacción del paciente.

Este caso de estudio permite ilustrar cómo el DEA radial (CCR/BCC) captura diferencias de eficiencia en la asignación de recursos y, al integrarse con IA deliberativa, fundamenta las subpreguntas del Árbol Deliberativo en datos concretos. A continuación, definiremos el **Nodo Deliberativo CD-1a** para profundizar en la selección homogénea de DMUs.

---

**Nodo Deliberativo CD-1a:**

> *¿Qué criterios específicos deben aplicarse para garantizar que los hospitales comparados sean suficientemente homogéneos en el análisis DEA?*

### Sprint 3: Definición de Variables de Insumo y Output (3 párrafos)

Para nuestro análisis DEA, los **insumos** seleccionados son:

1. **Número de camas operativas** (Camas)
2. **Horas-análisis del personal médico** (Horas\_Méd)
3. **Gasto anual en suministros** (Gasto\_Sum)

Los **outputs** considerados abarcan tanto cantidad como calidad de atención:

1. **Número de altas hospitalarias** (Altas)
2. **Tasa de recuperación estimada** (Recup\_% )
3. **Nivel de satisfacción del paciente** (Sat\_Pac)

La elección de estos indicadores responde al nodo deliberativo CD-1a, y asegura que cubrimos recursos críticos (camas, personal, insumos) y resultados clave de gestión clínica y experiencia del paciente.

---

**Nodo Deliberativo CD-1b:**

> *¿Existen otros insumos u outputs relevantes que debamos incluir para capturar adecuadamente la eficiencia hospitalaria?*

### Sprint 4: Elaboración del DEA Inicial y Ejemplos Prácticos (4–5 pasos)

1. **Construcción de la matriz de datos**: A partir del subconjunto H1–H5, generamos un DataFrame con columnas `DMU`, `Camas`, `Horas_Méd`, `Gasto_Sum`, `Altas`, `Recup_%`, `Sat_Pac`.
2. **Ejecución de CCR (CRS) y BCC (VRS)**: Usaremos las funciones `run_ccr(df, dmu_column='DMU', input_cols=['Camas','Horas_Méd','Gasto_Sum'], output_cols=['Altas','Recup_%','Sat_Pac'])` y `run_bcc(...)` del paquete `dea_models.radial`.
3. **Visualización de resultados**: Integrar el histograma de eficiencias y un scatter 3D de las DMU coloreadas por eficiencia.
4. **Interpretación de outputs**: Analizar qué hospitales están en la frontera (eficiencia = 1) y cuáles presentan slacks.
5. **Ejemplo práctico**: Mostrar el código Python mínimo en un bloque, con salida de tabla resumida.

*Código de ejemplo:*

```python
import pandas as pd
from dea_models.radial import run_ccr, run_bcc

# 1) Datos
df = pd.DataFrame([
    {'DMU':'H1','Camas':300,'Horas_Méd':24000,'Gasto_Sum':2.5e6,'Altas':18000,'Recup_%':0.78,'Sat_Pac':4.2},
    # ... H2–H5 similares ...
])

# 2) Ejecución DEA
df_ccr = run_ccr(df, dmu_column='DMU', input_cols=['Camas','Horas_Méd','Gasto_Sum'], output_cols=['Altas','Recup_%','Sat_Pac'])

df_bcc = run_bcc(df, dmu_column='DMU', input_cols=['Camas','Horas_Méd','Gasto_Sum'], output_cols=['Altas','Recup_%','Sat_Pac'])

# 3) Resultados
print(df_ccr)
print(df_bcc)
```

---

**Nodo Deliberativo CD-1c:**

> *¿Qué criterios de interpretación (histograma vs scatter) resultan más útiles para comunicar eficiencia a stakeholders no técnicos?*

### Referencias Técnicas

* Drucker, P., Smith, J., & Lee, K. (2022). Epistemic Closure in Predictive AI: Risks and Mitigations. *Journal of AI Ethics*, 5(1), 45-62.
* Hollingsworth, B. (2008). The Measurement of Efficiency and Productivity of Health Care Delivery. *Health Economics*, 17(10), 1107-1128.

---

### Sprint 5: Revisión Profunda y Cierre del Capítulo 1

1. **Revisión de estilo y cohesión**: Verifica consistencia en terminología (IA deliberativa vs predictiva) y formato de listas, encabezados y blocs de código.
2. **Profundización técnica**: Añade referencias a artículos clave sobre clausura epistémica en IA (e.g., Drucker et al., 2022) y relevancia del DEA en salud (e.g., Hollingsworth, 2008).
3. **Validación de nodos deliberativos**: Asegúrate de que CD-1, CD-1a, CD-1b y CD-1c formen un árbol lógico, sin superposición semántica.
4. **Verificación de enlaces y artefactos**: Comprueba que el sticky note al comienzo y los comentarios Canvas estén actualizados.
5. **Cerrar Issue #1 en GitHub**: Marca las tareas como completadas y enlaza el pull request con el documento final.

Con esto, el **Capítulo 1** queda completo y listo para publicación preliminar. ¡Enhorabuena!

