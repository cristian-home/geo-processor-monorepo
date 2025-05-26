# Geo Processor Monorepo

Este monorepo contiene la aplicación completa del Geo Processor, utilizando Git submodules para gestionar cada servicio de forma independiente.

## Servicios

- **Frontend** (geo-processor-frontend): Aplicación Next.js - Puerto 3001
- **API Gateway** (geo-processor-api-gateway): NestJS Gateway - Puerto 3000
- **Backend** (geo-processor-api-backend): API Python/FastAPI - Puerto 8000

## Desarrollo

### Prerrequisitos

- Docker y Docker Compose
- Git con gitflow
- Git submodules

### Configuración inicial

1. Clonar el repositorio con submódulos:

```bash
git clone --recursive <url-del-repo>
```

O si ya clonaste el repo:

```bash
git submodule init
git submodule update
```

2. Ejecutar los servicios:

```bash
docker compose up --build
```

### Arquitectura

```
Frontend (3001) → API Gateway (3000) → Backend (8000)
```

### Submódulos

Este proyecto utiliza Git submodules. Para más información sobre gestión de submódulos, consulta [SUBMODULES.md](./SUBMODULES.md).

### Gitflow

Este proyecto utiliza gitflow para la gestión de ramas:

- `main`: Rama principal con código estable
- `develop`: Rama de desarrollo
- `feature/*`: Ramas de características
- `release/*`: Ramas de releases
- `hotfix/*`: Ramas de hotfixes

### URLs de acceso

- Frontend: http://localhost:3001
- API Gateway: http://localhost:3000
- Backend: http://localhost:8000
