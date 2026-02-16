# Evidencias · RA2 SBD (rellenar por el alumnado)

> Completa este documento con capturas/salidas. No incluyas secretos.
> Indica si has usado **Variante A (IAM Role)** o **Variante B (aws configure)**.

## 0) Identificación
- Alumno/a: Iñaki Elustondo Arbide
- Grupo:iabd08
- Variante usada (A/B): A
- Región AWS: Estados Unidos (Norte de Virginia)
- Bucket S3: proyecto-ra2-aws-s3-streamlit

---

## 1) S3 privado
- [ ] Captura del bucket (nombre y región) <img width="1008" height="87" alt="imagen" src="https://github.com/user-attachments/assets/2fa530ad-bf80-489d-8615-ebce31e419f1" />

- [ ] Captura/confirmación de que **no es público** (Block Public Access o permisos) <img width="1895" height="636" alt="imagen" src="https://github.com/user-attachments/assets/e8743402-1037-4237-91ff-1279a615a927" />

- [ ] Captura del objeto JSON en `data/sensores/`<img width="1919" height="606" alt="imagen" src="https://github.com/user-attachments/assets/62acb1d3-de51-428f-bce6-60b84e83cf4e" />


**Notas:**
- Key usada (S3_KEY):

---

## 2) Notebook / Script de subida
- [ ] Captura de la ejecución del notebook/script subiendo a S3
- [ ] Enlace o ruta del archivo en el repo (`notebooks/...`)![Bucket creado y archivo subido mediante el boton de cargar](image.png)

---

## 3) EC2 y red
- [ ] Captura de la instancia EC2 (Ubuntu 22.04)![Instancia EC2 creada con Ubuntu 22.04](image-1.png)
- [ ] Captura del Security Group con puerto 8501 abierto (según reglas del lab)![Security Group con puerto 8501](image-2.png)
- [ ] Salida de `ssh` conectando (sin mostrar claves)![Salida de ssh estando conectado](image-3.png)

---

## 4) Acceso a S3 desde EC2 (sin secretos)
Ejecuta en EC2:

```bash
aws sts get-caller-identity
aws s3 ls s3://<BUCKET>/data/sensores/
```

- [ ] Captura/salida de ambos comandos![Salida de ambos comandos en consola de git bash](image-4.png)

---

## 5) Streamlit en EC2
- [ ] Captura de `streamlit hello` funcionando (o `python -c "import streamlit"`)![Captura de "streamlit hello" funcionando](image-5.png)
- [ ] Captura de instalación de dependencias (`pip install -r requirements.txt`)![Captura de la instalacion de dependencias (Demasiado grande para entrar el comando entero en una sola imagen, no ha dado fallos al finalizar)](image-6.png)

---

## 6) Dashboard (funcionalidad)
Incluye capturas donde se vea:

- [ ] Filtro por `sensor_state` ![Flitro por el sensor state](image-10.png)
- [ ] Slider de temperatura![Slider de temperatura](image-9.png)
- [ ] Tabla filtrada ![Tabla filtrada](image-7.png)
- [ ] Gráfica línea (temperatura vs tiempo)![Grafica de linea de temperatura vs tiempo](image-11.png)
- [ ] Gráfica barras (CO₂ por sensor)![Grafica de barras de CO2 por sensor](image-12.png)
- [ ] Mapa con sensores ![mapa de sensores](image-8.png)

---

## 7) Despliegue final
- [ ] Comando usado para arrancar en segundo plano (ej. `nohup` o script)![Comando para arrancar en segundo plano](image-13.png)
- [ ] Captura del log (`tail -n 50 streamlit.log` o similar)![Captura del log](image-14.png)
- [ ] URL final:

**URL:** `http://13.220.108.238:8501`

- [ ] Captura en navegador accediendo a la URL![Accediendo a la url puesta anteriormente](image-15.png)

---

## 8) Observaciones (opcional)
- Problemas encontrados y solución:
