<p align="center">
  <img src="https://raw.githubusercontent.com/autocheck-udesa/.github/main/assets/autocheck-hero.png" alt="AutoCheck: inspección vehicular asistida por inteligencia artificial" width="100%">
</p>

<h1 align="center">AutoCheck</h1>

<p align="center">
  <strong>Inspección vehicular asistida por IA, con evidencia visual y revisión humana.</strong>
</p>

<p align="center">
  AutoCheck transforma fotografías de un vehículo en un prediagnóstico estructurado:<br>
  detecta daños, identifica las piezas afectadas, propone un rango explicable de reparación<br>
  y conserva la trazabilidad de cada decisión.
</p>

<p align="center">
  <img alt="Estado: MVP en desarrollo" src="https://img.shields.io/badge/estado-MVP%20en%20desarrollo-F59E0B?style=for-the-badge">
  <img alt="Human in the loop" src="https://img.shields.io/badge/IA-human--in--the--loop-06B6D4?style=for-the-badge">
  <img alt="Auditable" src="https://img.shields.io/badge/decisiones-auditables-22C55E?style=for-the-badge">
</p>

---

## De una foto a una evaluación asistida

```mermaid
flowchart LR
    A[📷 Fotografías<br/>del vehículo] --> B[🔎 Control de calidad<br/>y procesamiento]
    B --> C[✨ Detección de daños<br/>y piezas afectadas]
    C --> D[💰 Estimación explicable<br/>de reparación]
    D --> E[👤 Revisión y corrección<br/>por un perito]
    E --> F[🧾 Resultado trazable<br/>y auditable]

    classDef input fill:#0f172a,stroke:#22d3ee,color:#fff;
    classDef ai fill:#082f49,stroke:#22d3ee,color:#fff;
    classDef review fill:#451a03,stroke:#f59e0b,color:#fff;
    classDef result fill:#052e16,stroke:#22c55e,color:#fff;
    class A input;
    class B,C,D ai;
    class E review;
    class F result;
```

## ¿Qué problema resuelve?

Una inspección vehicular no termina al encontrar una abolladura. También hay que determinar **dónde está**, **qué pieza afecta**, **qué evidencia respalda el diagnóstico** y **cómo se llegó a una estimación**.

AutoCheck reúne ese proceso en un único flujo reproducible:

| Capacidad | Resultado |
| --- | --- |
| Análisis visual | Localiza daños y piezas mediante máscaras y niveles de confianza. |
| Evidencia | Superpone los resultados sobre las imágenes originales. |
| Estimación explicable | Desglosa un rango orientativo según pieza, daño, severidad y reglas versionadas. |
| Revisión humana | Permite confirmar, rechazar o corregir las predicciones. |
| Trazabilidad | Vincula imagen, modelo, parámetros, resultado y revisión. |

## Diseñado para asistir, no para decidir solo

> [!IMPORTANT]
> AutoCheck es un sistema de apoyo a la inspección. Las predicciones y estimaciones relevantes requieren revisión humana y no aprueban reclamos ni presupuestos automáticamente.

La explicabilidad y la intervención del perito son parte del producto, no una corrección posterior. Cuando la evidencia es insuficiente, el sistema deriva el caso a revisión en lugar de presentar una certeza que no posee.

## Arquitectura del MVP

```mermaid
flowchart TB
    WEB[Web de inspección] --> API[API y gestión de casos]
    API --> DB[(PostgreSQL)]
    API --> OBJ[(Almacenamiento de imágenes)]
    API --> QUEUE[(Cola de trabajos)]
    QUEUE --> WORKER[Worker]
    WORKER --> INF[Servicio de inferencia]
    INF --> DAMAGE[Modelo de daños]
    INF --> PARTS[Modelo de piezas]
    WORKER --> API
    API --> AUDIT[Historial y auditoría]
```

El entorno está pensado para ejecutarse localmente mediante contenedores, separando la aplicación operativa del entrenamiento de los modelos.

## Estado del proyecto

AutoCheck se encuentra en fase de **MVP académico**. El trabajo actual está concentrado en:

- integración de los modelos de daños y piezas;
- revisión visual y mejora de la calidad de datos;
- estimaciones de costo explicables y versionadas;
- experiencia de revisión para el perito;
- pruebas end-to-end y reproducibilidad del entorno.

El código permanece privado durante esta etapa de desarrollo. Esta portada comunica el alcance, las decisiones de diseño y el progreso del proyecto sin exponer datos ni activos restringidos.

## Principios del proyecto

`Evidencia antes que certeza` · `Revisión humana` · `Trazabilidad completa` · `Datos con procedencia` · `Resultados reproducibles`

---

<p align="center">
  <strong>Proyecto académico de Machine Learning e Ingeniería de Software.</strong><br>
  Construido para explorar una inspección vehicular más clara, consistente y auditable.
</p>
