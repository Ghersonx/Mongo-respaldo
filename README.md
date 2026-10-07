# Bottle Traceability

Aplicación de trazabilidad de botellas con blockchain local, autenticación por roles y mini interfaz web.

## Stack

- Python 3.13
- FastAPI
- SQLAlchemy
- SQLite
- Docker

## Requisitos locales

- Python 3.13
- pip
- Docker Desktop (opcional para ejecutar en contenedor)

## Ejecutar localmente

```powershell
cd "c:\Users\Camilo\Documents\ING- INF\SISTEMAS DISTRIBUIDOS\blockchain"
python -m pip install -r requirements.txt
python seed.py
python -m uvicorn app.main:app --host 127.0.0.1 --port 8001
```

Abrir en el navegador:

```text
http://127.0.0.1:8001
```

## Usuarios de prueba

- manufacturer / manufacturer123
- distributor / distributor123
- consumer / consumer123

## Ejecutar con Docker

```powershell
cd "c:\Users\Camilo\Documents\ING- INF\SISTEMAS DISTRIBUIDOS\blockchain"

Construir docker
docker compose up --build

Construir docker
docker compose up

```

Abrir:

```text
http://localhost:8001
```

## Flujo de prueba

1. Iniciar sesión como `manufacturer`
2. Registrar una botella
3. Cerrar sesión
4. Iniciar sesión como `distributor`
5. Distribuir la botella
6. Cerrar sesión
7. Iniciar sesión como `consumer`
8. Consumir la botella
9. Revisar la validación de la cadena blockchain

## Estructura

- `database.py`: modelos SQLAlchemy
- `blockchain.py`: cadena persistida (hash, minería y validación)
- `app/auth.py`: autenticación, JWT y roles
- `app/main.py`: entrada principal de FastAPI
- `app/services/bottle_service.py`: registro, distribución, consumo y listado
- `app/static/index.html`: interfaz web (escritorio fabricante, móvil distribuidor/consumidor)
- `seed.py`: carga de usuarios de prueba
- `tests/test_blockchain_flow.py`: pruebas de validación

## Nota

Esta implementación usa blockchain local dentro de la aplicación para integridad de datos, no una red distribuida de nodos.
#
