# Usa una imagen oficial de Node.js como base
FROM node:18-alpine as build
#miau
# Crea el directorio de trabajo dentro del contenedor
WORKDIR /var/lib/jenkins/workspace/Dev-Ops/CN_api_bk


# Copia los archivos package.json y package-lock.json (si existe)
COPY package*.json ./

# Instala las dependencias de Node.js
RUN npm install

# Copia el resto del código fuente al contenedor
COPY . .

# Expone el puerto en el que tu API estará corriendo (por ejemplo, 3000)
EXPOSE 3000

# Comando por defecto para iniciar la aplicación
CMD ["npm", "start"]

