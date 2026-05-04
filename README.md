# Reto Nequi — Chat App

Aplicación de chat full-stack compuesta por un backend en **FastAPI** y un frontend en **Angular**, orquestados con **Docker Compose**.

---

## Clonar el repositorio

> **Importante:** el proyecto usa submódulos de Git. Usa el siguiente comando para clonar todo correctamente:

```bash
git clone --recurse-submodules https://github.com/Jesus-Rojas/reto-nequi
cd reto-nequi
```

Si ya clonaste el repo sin `--recurse-submodules`, ejecuta:

```bash
git submodule update --init --recursive
```

---

## Levantar con Docker Compose

La forma más rápida de correr el proyecto completo es con Docker:

```bash
docker compose up --build
```

| Servicio  | URL                          |
|-----------|------------------------------|
| Frontend  | http://localhost:8080        |
| Backend   | http://localhost:8000        |
| Swagger   | http://localhost:8000/docs   |

---

## Estructura del proyecto

```
reto-nequi/
├── docker-compose.yml
├── backend/          # FastAPI + SQLAlchemy + SQLite
└── frontend/         # Angular 21
```

---

## Backend — desarrollo local

```bash
cd backend
python -m venv .venv

# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate

pip install -r requirements.txt
uvicorn app.main:app --reload
```

### Ejecutar pruebas

```bash
pytest
```

El reporte de cobertura se muestra automáticamente en consola (configurado en `pytest.ini`).  
Para generar un reporte HTML:

```bash
pytest --cov=app --cov-report=html
# Resultado en: backend/htmlcov/index.html
```

---

## Frontend — desarrollo local

```bash
cd frontend
npm install
ng serve
```

La app estará disponible en http://localhost:4200.

### Ejecutar pruebas unitarias

```bash
ng test
```

Para ver el porcentaje de cobertura:

```bash
ng test --coverage
# Resultado en: frontend/coverage/index.html
```

---

## Stack

| Capa       | Tecnología                              |
|------------|-----------------------------------------|
| Backend    | FastAPI 0.115, SQLAlchemy 2.0, SQLite   |
| Frontend   | Angular 21, TypeScript                  |
| Contenedor | Docker + Docker Compose                 |
| Pruebas    | Pytest + HTTPX                          |
