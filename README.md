# mi_web – Gestor de tareas (To‑Do) con usuarios

Aplicación web sencilla para gestionar tareas personales con cuentas de usuario. Permite registrarse, iniciar sesión y realizar operaciones CRUD sobre tareas propias, además de filtrar por título y ver el conteo de pendientes.

## Funcionalidades
- Autenticación de usuarios: registro, login y logout
- CRUD de tareas: crear, listar, ver detalle, editar y eliminar
- Búsqueda por título en la lista de tareas (`area-buscar`)
- Indicador de tareas incompletas (pendientes)
- Separación por usuario: cada persona ve solo sus tareas

## Tecnologías
- Python 3.13
- Django 4.1.5
- Base de datos: SQLite (desarrollo)

## Arquitectura rápida
- App principal: `base`
- Modelo central: `Tarea` (`base/models.py`)
  - Campos: `usuario`, `titulo`, `descripcion`, `completo`, `creado`
- Vistas basadas en clases (`base/views.py`): `ListaPendientes`, `DetalleTarea`, `CrearTarea`, `EditarTarea`, `EliminarTarea`, `Logueo`, `PaginaRegistro`
- Rutas (`base/urls.py`):
  - `/` lista de tareas
  - `/login/`, `/registro/`, `/logout/`
  - `/tarea/<pk>`, `/crear-tarea/`, `/editar-tarea/<pk>`, `/eliminar-tarea/<pk>`
- Templates: `base/templates/base/`
- Configuración relevante (`proyecto/settings.py`):
  - `LANGUAGE_CODE = 'es-ar'`
  - `ALLOWED_HOSTS = ['*']` en desarrollo
  - `TEMPLATES['DIRS'] = BASE_DIR / 'base' / 'templates'`

## Puesta en marcha (Windows PowerShell)
Desde este directorio (`mi_web/src/proyecto`):
```powershell
python -m venv ..\..\..\.venv
..\..\..\.venv\Scripts\Activate.ps1
pip install -r ..\..\..\requirements.txt
python manage.py migrate
python manage.py runserver 0.0.0.0:8000
```

- Navegá a `http://127.0.0.1:8000`
- Registro: `http://127.0.0.1:8000/registro/`
- Login: `http://127.0.0.1:8000/login/`

Crear superusuario (opcional):
```powershell
python manage.py createsuperuser
```

## Estructura (resumen)
```
mi_web/src/proyecto/
├─ base/
│  ├─ migrations/
│  ├─ templates/base/
│  ├─ models.py
│  ├─ views.py
│  └─ urls.py
├─ proyecto/
│  ├─ settings.py
│  ├─ urls.py
│  └─ wsgi.py
├─ manage.py
└─ db.sqlite3 (ignorado en git)
```

## Configuración
- `ALLOWED_HOSTS`: en desarrollo se usa `['*']` para facilitar pruebas locales y en LAN.
- `TIME_ZONE`, `LANGUAGE_CODE`: ajustar según preferencia.
- Base de datos: por defecto `SQLite` (`db.sqlite3`). Para producción, cambiar a Postgres u otro motor.

## Contraseñas
Se aplican validadores por defecto de Django:
- Longitud mínima (8),
- No ser muy común,
- No ser demasiado parecida al usuario,
- No ser solo numérica.

## Rutas útiles
- `/` lista de tareas
- `/registro/` y `/login/`
- `/crear-tarea/`

## Roadmap / Mejoras posibles
- Tareas
  - Vencimiento (fecha límite) y recordatorios
  - Prioridad y orden manual (drag & drop)
  - Repetición (diaria/semanal/mensual) y tareas recurrentes
  - Categorías/etiquetas y colores
  - Adjuntos (archivos) y notas/comentarios por tarea
  - Estados adicionales (en progreso, bloqueada, etc.)
- UX/UI
  - Diseño con Tailwind/Bootstrap
  - Modo oscuro, accesibilidad (a11y) y i18n
  - Paginación y filtros avanzados
- Integraciones y API
  - API REST (Django REST Framework)
  - Webhooks/notificaciones (email, Telegram, etc.)
  - Importar/Exportar CSV/Excel
- Seguridad
  - Políticas de contraseña configurables
  - 2FA (TOTP) opcional
  - Auditoría de cambios
- Calidad y CI/CD
  - Tests unitarios e integración (pytest)
  - Lint/format (ruff, black) y pre-commit hooks
  - GitHub Actions (test + build)
- Despliegue
  - Docker y docker-compose
  - Deploy en Render/Railway/Fly.io/CapRover
  - Configuración para Postgres y variables de entorno
- Rendimiento
  - Índices en DB, select_related/prefetch_related
  - Cache y CDN de estáticos

## Licencia
A definir.

## Enlaces
- Repo: `https://github.com/ExeDevCentral/proyectopython01.git`
