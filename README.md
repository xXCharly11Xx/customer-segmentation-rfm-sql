# Customer Segmentation (RFM) — SQL + Python

Proyecto de análisis de clientes usando metodología **RFM (Recency, Frequency, Monetary)** sobre dataset de retail.

Este proyecto simula un caso real de analítica de negocio para segmentación de clientes y priorización de campañas de marketing.

---

## Objetivo

Identificar segmentos de clientes clave:
- Champions
- Loyal customers
- At risk
- Hibernating
- New customers

y proponer acciones de negocio.

---

## Stack

- Python
- Pandas
- SQLite
- SQL
- Matplotlib

---

## Proceso

1. Extracción desde base SQLite
2. Limpieza de transacciones
3. Cálculo RFM
4. Scoring por percentiles
5. Segmentación de clientes
6. Visualización
7. Export a CSV

---

## Estructura

customer-segmentation-rfm-sql/
│
├── notebooks/
│ └── 01_rfm_segmentation.ipynb
│
├── data/
│ └── processed/
│ ├── rfm_customers.csv
│ └── rfm_segment_summary.csv
│
├── images/
│ └── rfm_segments.png
│
└── README.md


---

## Insights

- Champions generan mayor revenue
- Alto volumen de clientes hibernating
- Segmentos At Risk requieren campañas win-back

---

## Próximos pasos

- Dashboard en Power BI
- Clustering K-Means
- Cohort analysis
