# 🌱 EcoVerde Antioquia S.A.S.

<div align="center">

![EcoVerde](https://img.shields.io/badge/EcoVerde-Antioquia-success?style=flat-square&logo=leaf)
![Docker](https://img.shields.io/badge/Docker-Enabled-blue?style=flat-square&logo=docker)
![HTML5](https://img.shields.io/badge/HTML5-ES2020-orange?style=flat-square&logo=html5)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Status](https://img.shields.io/badge/Status-Active-brightgreen?style=flat-square)

**Plataforma Institucional Moderna para Servicios de Espacios Verdes**

[Ver Demo](#demo) • [Requisitos](#requisitos) • [Instalación](#instalación) • [Documentación](#documentación)

</div>

---

## 📋 Tabla de Contenidos

- [Descripción](#descripción)
- [Características](#características)
- [Requisitos](#requisitos)
- [Instalación](#instalación)
- [Estructura del Proyecto](#estructura-del-proyecto)
- [Configuración](#configuración)
- [Uso](#uso)
- [Desarrollo](#desarrollo)
- [Troubleshooting](#troubleshooting)
- [Contribuir](#contribuir)
- [Contacto](#contacto)

---

## 📝 Descripción

**EcoVerde Antioquia S.A.S.** es una empresa dedicada al mantenimiento de zonas verdes, diseño de jardines y suministro de materiales para construcción. Este proyecto implementa una **plataforma web institucional moderna** utilizando tecnologías de containerización con Docker para garantizar portabilidad, escalabilidad y facilidad de despliegue.

### Objetivo Principal
Desarrollar una presencia digital de clase mundial que refleje los valores de sostenibilidad, innovación y excelencia de la empresa, proporcionando una experiencia de usuario excepcional a través de un sitio web responsivo y de alto rendimiento.

---

## ✨ Características

### 🎨 Diseño
- ✅ Interfaz moderna y profesional con glassmorphism
- ✅ Diseño completamente responsivo (Mobile-first)
- ✅ Animaciones suaves y efectos visuales sofisticados
- ✅ Paleta de colores coherente basada en temática ecológica
- ✅ Tipografía premium (Playfair Display + Poppins)

### ⚡ Rendimiento
- ✅ Página de carga rápida (~2KB CSS optimizado)
- ✅ Sin dependencias externas (vanilla JavaScript)
- ✅ Optimizado para SEO
- ✅ Compatible con todos los navegadores modernos

### 🔧 Infraestructura
- ✅ Containerizado con Docker para facilidad de despliegue
- ✅ Orquestación con Docker Compose
- ✅ Servidor Nginx de alta performance
- ✅ Volúmenes persistentes para datos
- ✅ Red Docker personalizada

### 📱 Funcionalidades
- ✅ Sección Hero con llamada a acción (CTA)
- ✅ Información de empresa (Quiénes Somos)
- ✅ Catálogo de servicios con tarjetas interactivas
- ✅ Sección de estadísticas de impacto
- ✅ Valores corporativos destacados
- ✅ Información de contacto con iconografía
- ✅ Footer con branding
- ✅ Animaciones en scroll con Intersection Observer

---

## 📦 Requisitos

### Requisitos Mínimos
- **Docker**: v20.10 o superior
- **Docker Compose**: v1.29 o superior
- **Git**: v2.30 o superior
- **Sistema Operativo**: Linux, macOS o Windows (WSL2)

### Verificar Instalación

```bash
# Verificar Docker
docker --version
# Docker version 24.x.x

# Verificar Docker Compose
docker compose version
# Docker Compose version 2.x.x

# Verificar Git
git --version
# git version 2.x.x
```

---

## 🚀 Instalación

### Opción 1: Instalación Rápida (Recomendado)

```bash
# 1. Clonar el repositorio
git clone https://github.com/tu-usuario/ecoverde-antioquia.git
cd ecoverde-antioquia

# 2. Construir la imagen Docker
docker build -t ecoverde-web:latest .

# 3. Iniciar los contenedores
docker compose up -d

# 4. Verificar el estado
docker compose ps

# 5. Abrir en navegador
# http://localhost:8080
```

### Opción 2: Instalación con Variables de Entorno

```bash
# Crear archivo .env
cat > .env << EOF
COMPOSE_PROJECT_NAME=ecoverde
NGINX_PORT=8080
VOLUME_PATH=./webdata
EOF

# Ejecutar con variables
docker compose --env-file .env up -d
```

### Opción 3: Instalación Paso a Paso

```bash
# Paso 1: Clonar repositorio
git clone https://github.com/tu-usuario/ecoverde-antioquia.git
cd ecoverde-antioquia

# Paso 2: Construir imagen
docker build -t ecoverde-web .

# Paso 3: Crear red Docker
docker network create ecoverde-net

# Paso 4: Crear volumen
docker volume create webdata

# Paso 5: Ejecutar contenedor
docker run -d \
  --name ecoverde-container \
  --network ecoverde-net \
  -p 8080:80 \
  -v webdata:/usr/share/nginx/html \
  ecoverde-web

# Paso 6: Verificar
docker logs ecoverde-container
```

---

<!-- ## 📂 Estructura del Proyecto

```
ecoverde-antioquia/
│
├── 📄 README.md                 # Este archivo
├── 📄 Dockerfile                # Definición de imagen Docker
├── 📄 compose.yml               # Orquestación Docker Compose
├── 📄 .dockerignore             # Archivos ignorados en build
├── 📄 .gitignore                # Archivos ignorados en Git
├── 📄 .env.example              # Variables de entorno de ejemplo
│
├── 📁 app/                      # Aplicación web
│   ├── 📄 index.html            # Página principal (HTML5)
│   ├── 📄 styles.css            # Estilos personalizados
│   └── 📁 assets/               # Recursos (imágenes, fuentes)
│       ├── 📁 images/
│       ├── 📁 fonts/
│       └── 📁 icons/
│
├── 📁 nginx/                    # Configuración Nginx
│   └── 📄 nginx.conf            # Archivo de configuración
│
├── 📁 docs/                     # Documentación adicional
│   ├── 📄 INSTALLATION.md       # Guía de instalación detallada
│   ├── 📄 DEPLOYMENT.md         # Guía de despliegue
│   ├── 📄 TROUBLESHOOTING.md    # Solución de problemas
│   └── 📄 API.md                # Documentación API (si aplica)
│
└── 📁 webdata/                  # Volumen persistente (generado)
``` -->

---

## ⚙️ Configuración

### Dockerfile

```dockerfile
FROM nginx:alpine

# Copiar archivos de la aplicación
COPY app/ /usr/share/nginx/html/

# Copiar configuración Nginx
COPY nginx/nginx.conf /etc/nginx/nginx.conf

# Exponer puerto
EXPOSE 80

# Healthcheck
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 \
    CMD wget --no-verbose --tries=1 --spider http://localhost/ || exit 1

CMD ["nginx", "-g", "daemon off;"]
```

### Docker Compose (compose.yml)

```yaml
version: '3.8'

services:
  ecoverde-web:
    build:
      context: .
      dockerfile: Dockerfile
    container_name: ecoverde-container
    ports:
      - "${NGINX_PORT:-8080}:80"
    volumes:
      - webdata:/usr/share/nginx/html
    networks:
      - ecoverde-net
    restart: unless-stopped
    environment:
      - TZ=America/Bogota

volumes:
  webdata:
    driver: local

networks:
  ecoverde-net:
    driver: bridge
```

### Variables de Entorno (.env)

```env
# Proyecto
COMPOSE_PROJECT_NAME=ecoverde
PROJECT_NAME=EcoVerde Antioquia

# Puertos
NGINX_PORT=8080
NGINX_PORT_SSL=8443

# Rutas
VOLUME_PATH=./webdata
APP_PATH=./app

# Zona Horaria
TZ=America/Bogota

# Ambiente
ENVIRONMENT=production
DEBUG=false
```

---

## 🎯 Uso

### Comandos Docker Básicos

```bash
# Iniciar servicios
docker compose up -d

# Ver logs en tiempo real
docker compose logs -f ecoverde-web

# Detener servicios
docker compose down

# Reconstruir imagen
docker compose up -d --build

# Ejecutar comando en contenedor
docker compose exec ecoverde-web sh

# Ver estado de contenedores
docker compose ps

# Estadísticas de recursos
docker stats ecoverde-container
```

### Acceso a la Aplicación

```
URL Principal:   http://localhost:8080
Health Check:    http://localhost:8080/health.html
```

### Modificar Contenido

```bash
# Copiar archivos al volumen
docker compose exec ecoverde-web cp /app/* /usr/share/nginx/html/

# O editar directamente en el volumen
nano webdata/index.html

# Recargar Nginx
docker compose exec ecoverde-web nginx -s reload
```

---

## 💻 Desarrollo

### Entorno Local sin Docker

```bash
# Instalar dependencias (si aplica)
npm install

# Ejecutar servidor local
python -m http.server 8080
# O usar Live Server en VS Code

# Acceder a http://localhost:8080
```

### Editar HTML/CSS/JavaScript

```bash
# Editar archivos en app/
nano app/index.html

# Los cambios se reflejan al recargar la página
```

### Build Personalizado

```bash
# Build con etiqueta personalizada
docker build -t ecoverde-web:v1.0.0 .

# Build sin caché
docker build --no-cache -t ecoverde-web:latest .

# Build con etiquetas múltiples
docker build -t ecoverde-web:latest -t ecoverde-web:v1 .
```

---

## 🔧 Troubleshooting

### Puerto 8080 en Uso

```bash
# Encontrar proceso usando puerto 8080
lsof -i :8080

# Cambiar puerto en compose.yml
ports:
  - "8081:80"  # Usar puerto 8081

# O usar variable de entorno
NGINX_PORT=8081 docker compose up -d
```

### Contenedor no Inicia

```bash
# Ver logs detallados
docker compose logs ecoverde-web

# Verificar configuración Nginx
docker compose exec ecoverde-web nginx -t

# Reiniciar contenedor
docker compose restart ecoverde-web
```

### Permisos de Archivos

```bash
# Ajustar permisos en volumen
docker compose exec ecoverde-web chmod -R 755 /usr/share/nginx/html

# Cambiar propietario
docker compose exec ecoverde-web chown -R nginx:nginx /usr/share/nginx/html
```

### Limpiar Completamente

```bash
# Detener y eliminar contenedores
docker compose down

# Eliminar volumen
docker volume rm webdata

# Eliminar imagen
docker rmi ecoverde-web

# Iniciar desde cero
docker compose up -d --build
```

---

## 📊 Monitoreo

### Ver Consumo de Recursos

```bash
# Monitoreo en vivo
docker stats ecoverde-container

# Historial
docker container stats --no-stream
```

### Logs

```bash
# Últimas 100 líneas
docker compose logs --tail=100 ecoverde-web

# Logs en tiempo real
docker compose logs -f

# Logs con timestamps
docker compose logs --timestamps
```

---

## 🚢 Despliegue en Producción

### Checklist Previo

- ✅ Actualizar `TZ` a zona horaria correcta
- ✅ Configurar certificado SSL/TLS
- ✅ Ajustar limites de recursos
- ✅ Configurar logs persistentes
- ✅ Hacer backup de datos
- ✅ Configurar CI/CD

### Despliegue en Servidor

```bash
# 1. SSH a servidor
ssh usuario@servidor.com

# 2. Clonar repositorio
git clone https://github.com/tu-usuario/ecoverde-antioquia.git
cd ecoverde-antioquia

# 3. Configurar variables
cp .env.example .env
nano .env  # Editar valores

# 4. Ejecutar
docker compose -f compose.yml up -d

# 5. Verificar
docker compose ps
curl http://localhost:8080
```

---

## 🔐 Seguridad

### Buenas Prácticas

1. **Actualizar regularmente**
   ```bash
   docker compose pull
   docker compose up -d
   ```

2. **Usar variables de entorno sensibles**
   ```bash
   # No commitear .env con datos sensibles
   echo ".env" >> .gitignore
   ```

3. **Limitar recursos**
   ```yaml
   services:
     ecoverde-web:
       deploy:
         resources:
           limits:
             cpus: '1'
             memory: 512M
   ```

4. **Network segura**
   ```yaml
   networks:
     ecoverde-net:
       driver: bridge
       ipam:
         config:
           - subnet: 172.20.0.0/16
   ```

---

## 📚 Documentación Adicional

- [Guía de Instalación Detallada](./docs/INSTALLATION.md)
- [Guía de Despliegue](./docs/DEPLOYMENT.md)
- [Solución de Problemas](./docs/TROUBLESHOOTING.md)
- [Documentación Nginx](https://nginx.org/en/docs/)
- [Documentación Docker](https://docs.docker.com/)

---

## 🤝 Contribuir

Las contribuciones son bienvenidas. Por favor:

1. **Fork** el proyecto
2. Crea una **rama** para tu feature (`git checkout -b feature/AmazingFeature`)
3. **Commit** tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. **Push** a la rama (`git push origin feature/AmazingFeature`)
5. Abre un **Pull Request**

### Estándares de Código

- Usar HTML5 semántico
- CSS organizado y comentado
- JavaScript vanilla sin dependencias
- Documentar cambios importantes

---

## 📄 Licencia

Este proyecto está bajo la Licencia MIT. Ver archivo [LICENSE](./LICENSE) para más detalles.

```
MIT License

Copyright (c) 2024 EcoVerde Antioquia S.A.S.

Permission is hereby granted, free of charge, to any person obtaining a copy...
```

---

## 👥 Autores

- **Aprendiz ADSO** - Desarrollo Web
- **EcoVerde Antioquia S.A.S.** - Empresa

---

## 📞 Contacto

<div align="center">

**EcoVerde Antioquia S.A.S.**

📧 Email: [contacto@ecoverde.com](mailto:contacto@ecoverde.com)

📱 Teléfono: [300 000 0000](tel:3000000000)

📍 Ubicación: Antioquia, Colombia

🌐 Web: [www.ecoverde.com](https://www.ecoverde.com)

</div>

---

## 🙏 Agradecimientos

- [Docker](https://www.docker.com/) - Containerización
- [Nginx](https://nginx.org/) - Servidor web
- [Google Fonts](https://fonts.google.com/) - Tipografía
- Comunidad Open Source

---

## 📈 Roadmap

- [ ] Integración con base de datos
- [ ] Sistema de formularios
- [ ] Panel de administración
- [ ] Blog/Noticias
- [ ] Galería de proyectos
- [ ] Certificado SSL/TLS
- [ ] PWA (Progressive Web App)
- [ ] API REST
- [ ] Multi-idioma (i18n)
- [ ] Analytics avanzado

---

<div align="center">

**Hecho con ❤️ por EcoVerde Antioquia**

⭐ Si este proyecto te fue útil, considera darle una estrella en GitHub

</div>