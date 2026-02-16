# RA2 SBD · Dashboard IoT en Streamlit con datos en S3 (AWS Academy) — Entrega Final

Este repositorio contiene la **implementación final** para la *Tarea Evaluable RA2* del curso de especialización (Sistemas de Big Data) en entorno **AWS Academy Lab**. Se ha desarrollado un dashboard funcional que integra almacenamiento cloud, procesamiento de datos y visualización interactiva.

## Objetivo
Implementar un **pipeline completo**:
1. Generar/obtener datos IoT (JSON) y **subirlos a un bucket S3 privado**.
2. Desplegar una app **Streamlit** en una **EC2 Ubuntu 22.04** que **lee el JSON desde S3** usando `boto3`.
3. Construir un dashboard con:
   - Filtros dinámicos (estado del sensor + rango de temperatura).
   - Métricas de control (total de registros, sensores únicos y última lectura).
   - Tabla de datos filtrada en tiempo real.
   - Gráficas Plotly (Evolución de temperatura y media de CO₂).
   - Mapa de calor de sensores (lat/lon) con extracción de datos anidados.
   - Despliegue permanente accesible por `http://IP_PUBLICA:8501`.

---

## Solución de Problemas Técnicos (Evidencias)
Durante el desarrollo se han resuelto los siguientes desafíos:
- **Carga de Datos:** Implementación de `load_json_from_s3` para conectar con el bucket privado.
- **Preprocesamiento:** Extracción manual de `latitud` y `longitud` desde diccionarios anidados en la columna `ubicacion`.
- **Compatibilidad:** Resolución del error `AttributeError: 'DataFrame' object has no attribute 'array'` mediante el filtrado de columnas numéricas puras para el componente de mapa.
- **Codificación:** Corrección de errores de `utf-8 codec` mediante la limpieza de caracteres especiales en el editor `nano`.

---

## Notebooks / Scripts de carga a S3
Coloca aquí el notebook (Colab/Local) o script que:
1. Genera o transforma datos IoT (JSON)
2. Sube el fichero a `s3://<bucket>/data/sensores/<...>.json`

**Importante:** No subas credenciales ni tokens.

---

## Quickstart (EC2 Ubuntu 22.04 en AWS Academy)
En la instancia EC2, una vez configurado el entorno:

```bash
# 1. Activar el entorno virtual
source env/bin/activate

# 2. Configurar variables de entorno
export AWS_REGION=us-east-1
export S3_BUCKET=proyecto-ra2-aws-s3-streamlit
export S3_KEY=data/sensores/iabd08_sensores.json

# 3. Lanzamiento en segundo plano con nohup
PYTHONPATH=. nohup streamlit run app/dashboard.py --server.port 8501 > streamlit.log 2>&1 &

Estructura del repositorio

    app/ → Dashboard principal y lógica de componentes.

    app/services/ → Servicios de carga desde S3 y limpieza de datos (Pandas).

    notebooks/ → Aquí debe residir el script de carga de datos a S3.

    streamlit.log → Archivo de registro generado por el proceso nohup.

    requirements.txt → Librerías necesarias: streamlit, pandas, plotly, boto3.