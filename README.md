# Customer Segmentation (RFM) con SQL + Python (SQLite)

Proyecto de analítica de clientes usando el dataset **Online Retail** para construir segmentación **RFM** (Recency, Frequency, Monetary) sobre transacciones limpias en **SQLite**, consultadas con **SQL** y analizadas/visualizadas con **Python**.

---

## Objetivo
Identificar segmentos accionables de clientes para priorizar **retención**, **reactivación (winback)** y **crecimiento**, mediante métricas RFM calculadas desde transacciones.

---

## Stack
- Python (pandas, numpy, matplotlib)
- SQLite (base local)
- SQL (CTEs, agregaciones, filtros)
- VS Code + Jupyter

---

## Dataset
- Fuente: Online Retail (transacciones 2010–2011).
- Nota: El archivo de base de datos (`.db`) y datos crudos **no se versionan** en GitHub por tamaño/licencia.  
  El repositorio incluye el flujo reproducible para generarlos localmente.

---

## Metodología (RFM)
1. **Filtrado de transacciones**:
   - `CustomerID` no nulo
   - `Quantity > 0` y `UnitPrice > 0`
   - excluir notas de crédito (`InvoiceNo` que inicia con `C`)
2. **Definición de fecha de referencia**: `max(invoice_day) + 1 día`
3. Cálculo por cliente:
   - **Recency** = días desde última compra
   - **Frequency** = número de órdenes (distinct `InvoiceNo`)
   - **Monetary** = suma de ingresos (Quantity * UnitPrice)
4. **Scoring**:
   - R invertido (menos días = mejor score)
   - F y M por cuantiles (1–5)
5. **Segmentación** (reglas sobre scores R/F/M):
   - Champions
   - Loyal Customers
   - Potential Loyalists
   - At Risk (High Value)
   - At Risk (High Frequency)
   - New Customers
   - Hibernating
   - Others

---

## Resultados
- Se generan:
  - `data/processed/rfm_customers.csv` (RFM por cliente + segmento)
  - `data/processed/rfm_segment_summary.csv` (resumen por segmento)
  - `images/rfm_segments.png` (distribución de clientes por segmento)

Ejemplo de lectura de resultados:
- **Champions**: alta frecuencia y gasto, compras recientes → beneficios VIP, early access.
- **At Risk (High Value)**: alto valor histórico pero recencia baja → campañas winback con incentivo.
- **Hibernating**: baja actividad → campañas de bajo costo o depuración de base.

---

## Estructura del proyecto
customer-segmentation-rfm-sql/
├─ notebooks/
│ └─ 01_rfm_segmentation.ipynb
├─ data/
│ └─ processed/
├─ images/
├─ sql/
├─ database/ (IGNORADO)
└─ README.md


---

## Cómo correr el proyecto (local)
1. Crear/colocar base SQLite (si vienes del proyecto 1 puedes reutilizarla):
   - `database/online_retail.db`
   - Debe contener la tabla `transactions_clean`

2. Abrir y ejecutar:
   - `notebooks/01_rfm_segmentation.ipynb`

---

## Próximas mejoras
- Segmentación RFM 100% en SQL (vista/tabla final en SQLite)
- Cohorts (retención mensual)
- Reglas de segmentación parametrizables
- Dashboard (Power BI / Looker Studio)
