# test-manager-library-3239188-infra

Contenedores, red, volúmenes y motor de base de datos de *Manager Library*. Prueba técnica SDD · Ficha ADSO 3239188.

## Papel en el spec

Levanta el entorno con un solo comando (RNF-5, tarea T-20). Según el ADR-001 y el artículo V de la constitución, este repositorio crea **solo el motor vacío**: usuario, volumen y red. **No contiene ninguna sentencia de creación de tablas**; todo el esquema vive en las migraciones del repo `api`.

## Qué debe levantar

| Servicio | Descripción |
|---|---|
| Base de datos | PostgreSQL 16, vacía, con volumen persistente |
| API | Backend Laravel del repo `api` |
| Frontend | App React del repo `app` |

## Variables de entorno

| Variable | Obligatoria | Uso |
|---|---|---|
| `DATABASE_URL` | sí | Conexión de la API al motor |
| `JWT_SECRET` | sí | Clave de firma del token (HS256, 8 horas) |
| `ADMIN_USERNAME` / `ADMIN_PASSWORD` | sí | Administrador inicial que crea el arranque de la API |
| `CORS_ORIGIN` | sí | Origen permitido del frontend |
| `COVERS_DIR` | no | Carpeta de portadas |

Regla del artículo IX: el `.env` real nunca se versiona; solo se publica un `.env.example` con valores de ejemplo.

## Criterio de terminado (T-20)

Un solo comando levanta motor, API y frontend, y la base arranca **sin tablas** hasta correr las migraciones.

## Estado

| Elemento | Estado |
|---|---|
| Diseño y alcance | Hecho (este documento) |
| Implementación de contenedores | Pendiente |

> Este README describe el diseño previsto. No afirma que la implementación exista.