# Predicción de Fuga de Clientes en Restaurantes

Este proyecto permite entrenar un modelo de detección visual para identificar comportamientos asociados a la fuga de clientes en un restaurante, utilizando visión artificial con YOLOv8.

## ✅ Requisitos previos

- Tener Python 3.9.6 instalado.
- Contar con una API Key válida de [Roboflow](https://roboflow.com/).
- Haber subido y etiquetado manualmente los frames del video en Roboflow (incluyendo partición y augmentations desde su plataforma).

## 🧪 Instalación

1. Crea un entorno virtual:
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

2. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

3. Crea un archivo `.env` con tu API Key de Roboflow:
   ```
   ROBOFLOW_API_KEY=tu_api_key_aqui
   ```

## 🔁 Flujo de trabajo

1. Ejecuta `generar-fotogramas.ipynb`  
   Este script toma los videos fuente de la carpeta `Videos/` y extrae los fotogramas a `FramesCompletos/`.

2. Sube manualmente los frames extraídos a Roboflow y realiza el etiquetado visual y aumentación de datos desde su plataforma.

3. Ejecuta `entrenar-yolov8.ipynb`  
   Este notebook descarga el dataset ya dividido (train/valid/test) desde Roboflow y entrena un modelo YOLOv8 con los datos etiquetados.

## 📁 Estructura del proyecto recomendada

```
PREDICCION-FUGA-RESTAURANTE/
├── FramesCompletos/              ← frames extraídos de videos
│   └── 2025_06_07_12_04/
├── Videos/                       ← videos fuente
│   └── 2025_06_07_12_04.mp4
├── dataset-yolov8/               ← dataset descargado desde Roboflow
│   ├── train/
│   │   ├── images/
│   │   └── labels/
│   ├── valid/
│   │   ├── images/
│   │   └── labels/
│   ├── test/
│   │   ├── images/
│   │   └── labels/
│   └── data.yaml
├── generar-fotogramas.ipynb      ← extracción de frames
├── entrenar-yolov8.ipynb         ← entrenamiento YOLOv8
├── .env                          ← contiene la API key de Roboflow
├── requirements.txt              ← dependencias del proyecto
└── venv/                         ← entorno virtual
```

## 📌 Notas

- La creación de `train/`, `valid/` y `test/` es automática al descargar el dataset desde Roboflow en formato YOLOv8.
- Asegúrate de tener los permisos adecuados para acceder al proyecto en Roboflow.

## 🔐 Ejemplo de archivo `.env`

Crea un archivo `.env` en la raíz del proyecto con el siguiente contenido:

```
ROBOFLOW_API_KEY=tu_api_key_de_roboflow
```

Reemplaza `tu_api_key_de_roboflow` por tu clave real obtenida desde tu cuenta en [Roboflow](https://roboflow.com/).

---