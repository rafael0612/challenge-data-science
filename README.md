# Alura Store LATAM — Análisis de 4 Tiendas (Google Colab)

> Proyecto de análisis de datos para identificar **qué tienda vender** en la cadena *Alura Store*, usando **Python + Pandas + Matplotlib** en **Google Colab**. Incluye un **extra geográfico opcional** (lat/lon) para analizar la distribución espacial de ventas.

---

## 🎯 Objetivo
Ayudar al Sr. Juan a decidir **qué tienda vender** para financiar un nuevo emprendimiento. El análisis compara 4 tiendas en base a:
- **Ingresos** totales.
- **Ventas por categoría** y **productos top/bottom**.
- **Valoración promedio** de clientes.
- **Costo de envío** promedio.
- (Extra) **Distribución geográfica** de ventas y desempeño por regiones.

Se genera una **recomendación cuantitativa** basada en un *score de peor desempeño* (**Bad_Score**) que pondera: menores ingresos, peor review y mayor costo de envío.

---

## 📦 Datos y supuestos
Los CSV de las 4 tiendas ya están preparados y se cargan en el notebook base (`AluraStoreLatam.ipynb`) desde Google Drive. Cada tienda se expone como un **DataFrame** de Pandas, típicamente con nombres en español:

- `tienda`, `tienda2`, `tienda3`, `tienda4`  *(o bien listas `tiendas` y `nombres`)*
- Columnas recomendadas (los scripts son tolerantes a alias comunes):
  - **Precio** (`Precio`, `price`, `valor`, `unit_price`)
  - **Categoría del Producto** (`Categoría del Producto`, `category`, `categoria`, `product_category`)
  - **Producto** (`Producto`, `product`, `nombre_producto`)
  - **Calificación** (`Calificación`, `review`, `rating`, `review_score`, `evaluación`)
  - **Costo de envío** (`Costo de envío`, `shipping`, `freight_value`, `costo_envio`, `shipping_cost`)
  - **Fecha** (`Fecha`, `order_purchase_timestamp`, `date`, `fecha_compra`)
  - **lat** / **lon** para el extra geográfico (`lat`, `latitude`, `latitud` / `lon`, `lng`, `longitude`, `longitud`)

> El parser de fechas usa `dayfirst=True` para interpretar `dd/mm/yyyy`.

---

## 🧰 Requisitos
- **Google Colab** (recomendado) o Python 3.10+ local.
- Librerías (Colab ya las incluye): `pandas`, `numpy`, `matplotlib`.
- **Opcional** para mapas interactivos: `folium`.

---

## 🗂️ Estructura sugerida del repositorio
.
├─ AluraStoreLatam.ipynb # Notebook principal (Colab)
├─ README.md # Este archivo
└─ data/ # (opcional) CSV si decides versionarlos


---

## ▶️ Ejecución en Google Colab (paso a paso)

1) **Abrir el notebook en Colab**  
   - Sube `AluraStoreLatam.ipynb` a GitHub.
   - Abre el archivo desde GitHub en Colab o usa el badge (ver más abajo).

2) **Montar Google Drive y cargar datos**  
   - Ejecuta la **celda base** del notebook (ya incluida) que monta Drive y carga las 4 tiendas como DataFrames (`tienda`, `tienda2`, `tienda3`, `tienda4`) o las listas `tiendas`/`nombres`.

3) **Pegar el bloque de análisis integral**  
   - En una nueva celda, pega el bloque titulado **“Análisis integral Alura Store (versión Rafael)”** que:
     - Normaliza columnas (soporta alias).
     - Calcula **ingresos**, **ventas por categoría**, **valoración promedio**, **envío promedio**, **productos top/bottom**.
     - Genera gráficos de barras y **línea mensual unificada** (Mes/Año jerárquico).
     - Construye una **tabla de métricas** y emite una **recomendación cuantitativa** (*Bad_Score*).

4) **(Opcional) Pegar el EXTRA geográfico**  
   - En otra celda, pega el bloque **EXTRA (OPCIONAL): Análisis geográfico** para visualizar dispersión y heatmaps (hexbin) por tienda, y tablas de desempeño por región (`lat_bin`, `lon_bin`).

5) **Informe final**  
   - Agrega una celda **Markdown** con el informe final (plantilla más abajo) y explica la recomendación.

6) **(Opcional) Exportar resultados**  
   - Exporta métricas y tablas a CSV para publicar o versionar.

---

## 🧪 Qué gráficos y tablas se generan
- **Ingresos por tienda** (barras, con etiquetas y peor tienda resaltada).
- **Valoración promedio** (barras, escala 0–5, etiquetas).
- **Costo de envío promedio** (barras, etiquetas).
- **Top 10 categorías** de la tienda con menos ingresos.
- **Ingresos mensuales unificados** por tienda (línea; eje X con Mes y, debajo, Año).
- **Top/Bottom 5 productos** por tienda (tablas).
- **Tabla de métricas consolidada** + **Recomendación cuantitativa** (Bad_Score).
- **(Extra)** Dispersión de puntos georreferenciados y **heatmaps** (hexbin) por tienda y combinados.
- **(Extra)** Tablas de **Top regiones** por ingresos y **participación** regional por tienda.

