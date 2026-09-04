Descripcion General : Evaluación de Calidad y Preparación de Datos


# 1. Diagnóstico de Calidad de Datos
Se realizó una auditoría profunda del dataset original (5,100 registros), identificando:
*Valores Faltantes:** Afectan a variables críticas como `Attendance` y `AssignmentsCompleted` (~4%).
*Duplicados:** Se detectaron 100 registros idénticos que representaban ruido estadístico.
*Inconsistencias de Dominio:** Valores imposibles como horas negativas, notas superiores al máximo y asistencias fuera del rango 0-100%.
*Errores de Formato:** Variantes de escritura en variables categóricas (`Program` y `Scholarship`).

# 2. Análisis Exploratorio de Datos (EDA)
Se investigaron las relaciones entre el comportamiento estudiantil y las notas finales:
*Correlaciones:** Se identificó que la *Asistencia** (r=0.64) y las *Tareas Completadas** (r=0.68) son los factores más determinantes del éxito académico.
*Análisis de Grupos:** Se confirmó que los estudiantes becados tienen, en promedio, un mejor rendimiento (4.37 vs 4.07).
*Estado Crítico:** Se observó que casi el 80% de la muestra inicial presentaba una nota inferior a 5.0.

# 3. Estrategia de Limpieza e Imputación
Se definió un criterio estadístico riguroso para tratar los datos:
 *Imputación por Mediana:* Aplicada a variables con asimetría o valores atípicos relevantes ("Efecto Bill Gates").
*Imputación por Media:* Reservada para variables con distribución normal (`PreviousGPA`).
*Estandarización:** Uso de técnicas de procesamiento de texto para unificar categorías.

# 4. Implementación de Pipeline de Scikit-Learn
Para asegurar la *reproducibilidad**, se construyó un sistema automatizado que incluye:
*Transformadores Personalizados:** `DomainRangeCleaner` y `CategoryStandardizer` para encapsular las reglas de negocio.
*Escalamiento Robusto:** Uso de `RobustScaler` para manejar outliers válidos sin sesgar el modelo.
*Codificación:** Transformación de variables categóricas mediante `OneHotEncoder`.

# 5. Resultado Final
El proceso concluye con un dataset de *5,000 registros limpios y 15 variables**, totalmente libre de nulos e inconsistencias, exportado como `rendimiento_academico_limpio.csv` y listo para fases de modelamiento predictivo.
