# Análisis de Homicidios en Antioquia (2016-2023)

Este proyecto realiza un análisis estadístico y geográfico profundo sobre la criminalidad en Antioquia, procesando múltiples fuentes de datos oficiales para generar visualizaciones e informes comprensibles.

---

## Estructura

A continuación se detalla la organización de todos los archivos y carpetas que componen este repositorio:

```text
AnalisisHomicidiosAntioquia/
├── Base de Datos - por anio/           # Datos crudos anuales
│   ├── homicidios_2016.xlsx            # Registros de 2016
│   ├── homicidios_2017.xlsx            # Registros de 2017
│   ├── homicidios_2018.xlsx            # Registros de 2018
│   ├── homicidios_2019.xlsx            # Registros de 2019
│   ├── homicidios_2020.xlsx            # Registros de 2020
│   ├── homicidios_2021.xlsx            # Registros de 2021
│   ├── homicidios_2022.xlsx            # Registros de 2022
│   └── homicidios_2023.xlsx            # Registros de 2023
├── demografia-poblacion/               # Datos de referencia poblacional
│   └── poblacion-antioquia.xlsx        # Cifras de habitantes por municipio
├── geoestadistico/                     # Archivos para mapas (DANE)
│   ├── MGN_ADM_MPIO_GRAFICO.shp        # Geometría de municipios (Principal)
│   ├── MGN_ADM_MPIO_GRAFICO.dbf        # Base de datos de atributos geográficos
│   ├── MGN_ADM_MPIO_GRAFICO.shx        # Índice de la geometría
│   ├── MGN_ADM_MPIO_GRAFICO.prj        # Sistema de referencia de coordenadas
│   └── (otros archivos .cpg, .sbn, .sbx, .xml necesarios para el GIS)
├── analisis_datos_homicidios_2016-2023.ipynb  # Código de análisis (Notebook)
├── Homicidios_2016-2023.xlsx           # Base de datos consolidada (Final)
├── Homicidios_2016-2023_unificado.xlsx # Versión intermedia procesada
├── analisis.pdf                        # Informe técnico en formato PDF
├── informe.docx                        # Documento descriptivo del proceso
└── README.md                           # Guía visual del proyecto (Este archivo)
```

---

## Descripción Detallada de Componentes

### 1. Datos de Entrada (Fuentes)
*   **`Base de Datos - por anio/`**: Contiene archivos individuales de Excel proporcionados por autoridades. Cada archivo tiene columnas como fecha, cantidad de víctimas, municipio, código DANE, género y edad.
*   **`demografia-poblacion/poblacion-antioquia.xlsx`**: Se usa para normalizar los datos de homicidios por cada 100,000 habitantes, permitiendo comparar municipios de distinto tamaño.

### 2. Capa Geoestadística
*   **`geoestadistico/`**: Estos archivos permiten que el código Python "dibuje" el mapa de Antioquia. El archivo `.shp` define los límites de cada municipio, mientras que el `.dbf` contiene los nombres que se asocian con nuestra base de datos criminal.

### 3. Ejecución y Procesamiento
*   **[`analisis_datos_homicidios_2016-2023.ipynb`](./analisis_datos_homicidios_2016-2023.ipynb)**: Es el corazón lógico del proyecto. Realiza:
    *   **Extracción**: Lectura de todos los Excel anuales.
    *   **Limpieza**: Estandariza nombres de municipios (ej: convierte 'MEDELLÍN (CT)' a 'MEDELLÍN') para que coincidan con los mapas.
    *   **Filtrado**: Selecciona exclusivamente los datos de Antioquia.
    *   **Análisis**: Calcula frecuencias por edad, género y arma utilizada.
    *   **Mapeo**: Une los datos estadísticos con los geográficos para generar mapas de calor.

### 4. Resultados y Documentación
*   **`Homicidios_2016-2023.xlsx`**: Es el resultado de unir todos los años en un solo lugar, permitiendo un análisis histórico continuo sin abrir múltiples archivos.
*   **`analisis.pdf` e `informe.docx`**: Estos documentos contienen la redacción narrativa de la investigación. Explican el contexto social, los hallazgos más relevantes y las conclusiones.

---

## Requisitos para Usuarios Técnicos

Si deseas ejecutar el código, asegúrate de tener instaladas estas librerías de Python:

```bash
pip install pandas numpy geopandas matplotlib seaborn scipy tabulate openpyxl
```

---

## Guía de Modificación

*   **¿Quieres analizar 2024?**: Coloca el nuevo archivo en `Base de Datos - por anio/` y ejecute el notebook.
*   **¿Quieres analizar otro departamento?**: Cambie el filtro en la sección de "Limpieza de Datos" del notebook y actualice el shapefile geográfico.
