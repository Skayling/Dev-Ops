# Usa una imagen oficial de Node.js como base
FROM node:18-alpine AS build

# Crea el directorio donde se almacenará el proyecto dentro del contenedor
WORKDIR /var/lib/jenkins/workspace/Dev-Ops/CN_React

# Copia los archivos package.json y package-lock.json (si existe)
COPY package*.json ./

# Instala las dependencias de Node.js
RUN npm install

# Copia el resto del código fuente al contenedor
COPY . .

# Expone el puerto 3000 para acceder a la API
EXPOSE 3000

# Comando por defecto para iniciar la aplicación
CMD ["npm", "start"]

FROM nginx:stable-alpine AS prod
# Expone el puerto 80 para el servidor Nginx
EXPOSE 80

# Inicia Nginx
CMD ["nginx", "-g", "daemon off;"]
