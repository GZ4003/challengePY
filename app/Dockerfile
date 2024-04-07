# Stage 1: Build stage
FROM python:3.9 as builder

WORKDIR /app

# Copiamos requirements.txt al contenedor
COPY requirements.txt .
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

# Copy the installed dependencies from the previous stage
COPY --from=builder /usr/local/lib/python3.9/site-packages /usr/local/lib/python3.9/site-packages

# Copy the application source code from the previous stage
COPY --from=builder /app/* .

# Expose port 5000
EXPOSE 6969

CMD ["gunicorn","--bind","0.0.0.0:6969","app:app"]




