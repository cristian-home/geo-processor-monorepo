# Submodules Management

Este repositorio utiliza Git submodules para gestionar los diferentes servicios del proyecto.

## Inicialización después de clonar

Cuando clones este repositorio, necesitas inicializar los submódulos:

```bash
git clone <url-del-repo>
cd <nombre-del-repo>
git submodule init
git submodule update
```

O en un solo comando:

```bash
git clone --recursive <url-del-repo>
```

## Submódulos incluidos

### geo-processor-api-backend

- **URL**: https://github.com/cristian-home/geo-processor-api-backend.git
- **Descripción**: Backend API desarrollada en Python con FastAPI
- **Puerto**: 8000

### geo-processor-api-gateway

- **URL**: https://github.com/cristian-home/geo-processor-api-gateway.git
- **Descripción**: API Gateway desarrollado en NestJS
- **Puerto**: 3000

### geo-processor-frontend

- **URL**: https://github.com/cristian-home/geo-processor-frontend.git
- **Descripción**: Aplicación frontend desarrollada en Next.js
- **Puerto**: 3001

## Comandos útiles

### Actualizar todos los submódulos

```bash
git submodule update --remote
```

### Actualizar un submódulo específico

```bash
git submodule update --remote geo-processor-api-backend
```

### Ver el estado de los submódulos

```bash
git submodule status
```

### Trabajar en un submódulo

```bash
cd geo-processor-api-backend
# Hacer cambios...
git add .
git commit -m "Cambios en backend"
git push origin main

# Volver al repo principal y actualizar la referencia
cd ..
git add geo-processor-api-backend
git commit -m "Update backend submodule"
```

## Docker Compose

El archivo `docker-compose.yml` en la raíz está configurado para construir y ejecutar todos los servicios:

```bash
docker-compose up --build
```

## Flujo de trabajo recomendado

1. **Desarrollo en submódulos**: Trabaja directamente en cada submódulo
2. **Commit en submódulo**: Haz commit de tus cambios en el submódulo
3. **Push en submódulo**: Sube los cambios al repositorio del submódulo
4. **Actualizar en principal**: Actualiza la referencia en el repo principal
5. **Commit en principal**: Haz commit de la nueva referencia del submódulo
