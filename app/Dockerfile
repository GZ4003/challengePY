# Etapa 1: La contrucción de la imagen
FROM python:3.9 as builder
WORKDIR /app

# Copiamos requirements.txt al contenedor
COPY /app/requirements.txt .
RUN pip install --upgrade pip
RUN pip install --upgrade setuptools wheel

# Instalación de Dependencias
RUN pip install --no-cache-dir --upgrade -r requirements.txt

# Copiando el codigo funte aplicación al directorio seleccionado
COPY . .
RUN rm requirements.txt

# Etapa 2: Producción
FROM builder

WORKDIR /app

# Copiando las dependencias instaladas desde la etapa anterior
COPY --from=builder /usr/local/lib/python3.9/site-packages /usr/local/lib/python3.9/site-packages

# Copiando el codigo funte aplicación desde la etapa previa
COPY --from=builder /app/* .

# Exponemos el Puerto 6969
EXPOSE 6969

# Ejecutamos la aplicación
CMD ["gunicorn","--bind","0.0.0.0:6969","app:app"]




