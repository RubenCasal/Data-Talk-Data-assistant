# Usa una imagen de Python ligera
FROM python:3.9-slim

# Establece el directorio de trabajo en el contenedor
WORKDIR /app

# Copia el archivo de requerimientos y el código de la aplicación
COPY requirements.txt .
COPY . .

# Instala las dependencias de Python
RUN pip install --no-cache-dir --upgrade pip
RUN pip install --no-cache-dir -r requirements.txt

# Instala Chromium y chromium-driver
RUN apt-get update && \
    apt-get install -y chromium chromium-driver && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Establece la ruta de Chromium como variable de entorno para dataframe_image
ENV CHROME_PATH=/usr/bin/chromium

# Expone el puerto que usará Uvicorn
EXPOSE 8000

# Comando para iniciar la aplicación con Uvicorn
CMD ["uvicorn", "api:app", "--host", "0.0.0.0", "--port", "8000"]
