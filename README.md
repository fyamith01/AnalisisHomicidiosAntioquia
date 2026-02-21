# Análisis de Homicidios en Antioquia (2016-2023)

Este proyecto realiza un análisis estadístico y geográfico profundo sobre la criminalidad en Antioquia, procesando múltiples fuentes de datos oficiales para generar visualizaciones e informes comprensibles.

---

## Estructura

A continuación se detalla la organización de todos los archivos y carpetas que componen este repositorio:

```text
AnalisisHomicidiosAntioquia/
├── Base de Datos - por anio/           # Datos crudos anuales (2016-2023)
├── bdentrada/                          # Base de datos de entrada consolidada
│   └── Homicidios_2016-2023.xlsx       # Archivo centralizado de homicidios
├── bdunificada/                        # Base de datos procesada y unificada
│   └── Homicidios_2016-2023_unificado.xlsx # Versión intermedia optimizada
├── analisis/                           # Resultados y reportes narrativos
│   ├── analisis.pdf                    # Informe técnico en formato PDF
│   └── informe.docx                    # Documento descriptivo del proceso
├── demografia-poblacion/               # Datos de referencia poblacional
│   └── poblacion-antioquia.xlsx        # Cifras de habitantes por municipio
├── geoestadistico/                     # Archivos para mapas (DANE)
│   ├── MGN_ADM_MPIO_GRAFICO.shp        # Geometría de municipios
│   └── (archivos complementarios .dbf, .shx, .prj, etc.)
├── analisis_datos_homicidios_2016-2023.ipynb # Código de análisis (Notebook)
└── README.md                           # Guía visual del proyecto (Este archivo)
```

---

## Descripción Detallada de Componentes

### 1. Datos de Entrada (Fuentes)
*   **`Base de Datos - por anio/`**: Contiene los archivos individuales de Excel originales por cada año. Son la fuente primaria de información.
*   **`bdentrada/Homicidios_2016-2023.xlsx`**: Es el archivo que agrupa los datos de todos los años en una sola base consolidada para facilitar su lectura inicial.
*   **`demografia-poblacion/poblacion-antioquia.xlsx`**: Se usa para normalizar los datos y realizar cálculos demográficos (ej. tasas por cada 100,000 habitantes).

### 2. Capa Geoestadística
*   **`geoestadistico/`**: Conjunto de archivos GIS que definen la geografía de Antioquia. Permiten que el notebook genere mapas de calor y representaciones espaciales de los homicidios.

### 3. Ejecución y Procesamiento
*   **[`analisis_datos_homicidios_2016-2023.ipynb`](./analisis_datos_homicidios_2016-2023.ipynb)**: El núcleo técnico donde ocurre la magia. Realiza el ETL, la limpieza de nombres de municipios, el filtrado por departamento y la generación de gráficos.

### 4. Resultados y Documentación
*   **`bdunificada/Homicidios_2016-2023_unificado.xlsx`**: Resultado del procesamiento de limpieza y unificación realizado en el notebook.
*   **`analisis/`**: Carpeta destinada a la documentación narrativa del proyecto. Contiende el `analisis.pdf` y el `informe.docx` que relatan detalladamente los hallazgos y conclusiones del estudio.

---

## Requisitos para Usuarios Técnicos

Si deseas ejecutar el código, asegúrate de tener instaladas estas librerías de Python:

```bash
pip install pandas numpy geopandas scikit-learn matplotlib seaborn scipy tabulate openpyxl
```

---