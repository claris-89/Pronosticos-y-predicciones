# Pronosticos-y-predicciones

# Estrategia de Retención de Clientes para Model Fitness

## Descripción del Proyecto

El objetivo de este proyecto es desarrollar una estrategia analítica basada en datos para mejorar la interacción y retención de clientes de Model Fitness. Al abordar el problema común de la pérdida de clientes, nos enfocaremos en:

- Predecir la probabilidad de pérdida (churn) para cada cliente en el próximo mes.
- Elaborar perfiles típicos de usuarios/as y clasificar a los clientes según sus características principales.
- Identificar los factores más influyentes en la pérdida de clientes.
- Proponer estrategias específicas para reducir la rotación y mejorar la lealtad de los usuarios.

## Descripción de los Datos

### Campos Incluidos:
1. **Datos del usuario del mes anterior**:
   - `gender`: Género del cliente.
   - `Near_Location`: Indica si el cliente vive/trabaja cerca del gimnasio.
   - `Partner`: Cliente empleado en una empresa asociada con descuentos especiales.
   - `Promo_friends`: Inscripción mediante una oferta de código promocional.
   - `Phone`: Indica si se proporcionó un número de teléfono.
   - `Age`: Edad del cliente.
   - `Lifetime`: Meses desde que el cliente se unió por primera vez.

2. **Datos de visitas, compras y estado de membresía**:
   - `Contract_period`: Duración del contrato (1 mes, 3 meses, 6 meses o 1 año).
   - `Month_to_end_contract`: Meses restantes para la expiración del contrato.
   - `Group_visits`: Participación en sesiones grupales.
   - `Avg_class_frequency_total`: Frecuencia promedio de visitas semanales a lo largo de la membresía.
   - `Avg_class_frequency_current_month`: Frecuencia promedio de visitas semanales en el último mes.
   - `Avg_additional_charges_total`: Gastos en servicios adicionales (cafetería, masajes, productos deportivos, etc.).

3. **Cancelación**:
   - `Churn`: Indica si el cliente canceló o no durante el mes analizado.

### Ubicación del Dataset:
Archivo: `/datasets/gym_churn_us.csv`

---

## Pasos del Análisis

### 1. Exploración y Preparación de Datos
- **Limpieza**: Identificar valores ausentes, calcular estadísticas clave (`describe()`), y revisar distribuciones de características.
- **Grupos por Cancelación**: Comparar características de clientes que se quedaron vs. los que se fueron (`groupby()`).
- **Visualización**: Graficar histogramas y correlaciones para detectar patrones iniciales.

### 2. Construcción de Modelos Predictivos
- **División de Datos**: Crear conjuntos de entrenamiento y validación con `train_test_split()`.
- **Entrenamiento**:
  - Modelo de Regresión Logística.
  - Modelo de Bosques Aleatorios.
- **Evaluación**: Comparar métricas de exactitud, precisión y recall para ambos modelos.

### 3. Análisis de Clústeres
- **Estandarización**: Escalar características para homogeneizar los datos.
- **Dendrograma**: Utilizar `linkage()` para estimar el número ideal de clústeres.
- **Clustering**: Entrenar un modelo K-means con `n=5`.
- **Análisis por Clúster**:
  - Calcular valores promedio por clúster.
  - Graficar distribuciones.
  - Evaluar tasas de cancelación y distinguir perfiles leales de propensos a irse.

### 4. Conclusiones y Recomendaciones
- Proponer estrategias para identificar grupos objetivo y reducir la rotación.
- Sugerir medidas prácticas basadas en los patrones observados en los datos.

---

## Herramientas Utilizadas
- **Python**:
  - Análisis de datos: Pandas, NumPy.
  - Visualización: Matplotlib, Seaborn.
  - Modelado: Scikit-learn, Scipy.
- **Entorno**: Jupyter Notebook u otro IDE preferido.

## Objetivos de Resultado
- **Estrategias Basadas en Datos**: Identificación precisa de clientes en riesgo.
- **Optimización de Recursos**: Acciones dirigidas a segmentos con mayor impacto.
- **Visión Mejorada de Usuarios**: Perfiles claros de usuarios/as típicos para iniciativas futuras.

## Conclusiones
Se observaron valores medios de varias características para dos grupos: personas que se quedaron y personas que se fueron. Esto  proporcionó una visión inicial sobre las diferencias en comportamiento y características entre los dos grupos, destacando factores como edad, duración del contrato, y cargos adicionales.

Modelos de Clasificación
Regresión Logística: La precisión del modelo fue del 92%, con una ligera ventaja en precisión y recall comparado con el modelo de bosque aleatorio. Este modelo destacó en la identificación correcta de los clientes que se quedaron y los que se fueron.

Bosque Aleatorio: También mostró una precisión del 92%, con un desempeño muy similar al de la regresión logística. Sin embargo, tuvo un poco menos de precisión y recall en comparación con la regresión logística.

Clustering con K-means
Se realizó un clustering con K-means utilizando 5 clústeres. Las características medias y las distribuciones de las características para cada clúster revelaron patrones interesantes:

Los clústeres 0 y 2 tendieron a tener contratos y duraciones de vida más cortos.

Los clústeres 3 y 4 mostraron preferencias por contratos más largos y tenían duraciones de vida más largas, indicando una mayor lealtad.

Análisis de Tasa de Cancelación
Los resultados reflejan que los clústeres 1, 2 y 4 tienen una alta lealtad y bajas tasas de cancelación. Sin embargo, el Cluster 3 muestra una tasa de cancelación extremadamente alta, indicando una necesidad urgente de abordar las preocupaciones de estos clientes. El Cluster 0 tiene una tasa de cancelación moderada, lo que sugiere una mezcla de lealtad y propensión a cancelar.

Utilizar estos insights para diseñar estrategias de retención específicas puede mejorar significativamente la satisfacción del cliente y reducir las tasas de cancelación. La comprensión de las características y comportamientos específicos de cada clúster es clave para tomar decisiones informadas y optimizar los esfuerzos de marketing y servicio al cliente.

Este análisis ha permitido identificar claramente los grupos de clientes que son leales y aquellos que están en riesgo de cancelar. Utilizando estos insights, se pueden diseñar estrategias de retención más efectivas y personalizadas, mejorando la satisfacción del cliente y reduciendo la tasa de cancelación. La comprensión de las características y comportamientos específicos de cada clúster es clave para tomar decisiones informadas y optimizar los esfuerzos de marketing y servicio al cliente.
