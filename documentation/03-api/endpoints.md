# Endpoints API

## Autenticación (`/api/auth`)

| Método | Endpoint          | Descripción                          | Acceso       |
|--------|-------------------|--------------------------------------|-------------|
| POST   | `/auth/signup`    | Registro de nuevo usuario            | Público      |
| POST   | `/auth/login`     | Inicio de sesión                     | Público      |
| GET    | `/auth/me`        | Obtener datos del usuario actual     | Privado (JWT)|

## Usuarios (`/api/users`)

| Método | Endpoint          | Descripción                          | Acceso       |
|--------|-------------------|--------------------------------------|-------------|
| GET    | `/users`          | Listar todos los usuarios            | Privado (Admin)|
| GET    | `/users/:id`      | Obtener perfil de usuario específico | Público      |
| GET    | `/users/:id/routes`| Listar rutas de un usuario           | Público      |

## Rutas (`/api/routes`)

| Método | Endpoint          | Descripción                          | Acceso       |
|--------|-------------------|--------------------------------------|-------------|
| POST   | `/routes`         | Crear nueva ruta                     | Privado (JWT)|
| GET    | `/routes`         | Listar todas las rutas (con filtros) | Público      |
| GET    | `/routes/:id`     | Obtener detalles de ruta específica  | Público      |
| PATCH  | `/routes/:id`     | Actualizar ruta                      | Privado (Dueño)|
| DELETE | `/routes/:id`     | Eliminar ruta                        | Privado (Dueño)|

## Páginas SPA

| Ruta                | Componente          | Acceso       |
|---------------------|---------------------|-------------|
| `/`                | HomePage            | Público      |
| `/auth`            | AuthPage            | No autenticado|
| `/routes`          | RouteListPage       | Público      |
| `/routes/new`      | NewRoutePage        | Privado      |
| `/routes/:id`      | RouteDetailPage     | Público      |
| `/users/:id`       | UserProfilePage     | Público      |

---

### Notas:
1. **Privado (JWT)**: Requiere header `Authorization: Bearer <token>`
2. **Privado (Dueño)**: Solo el creador del recurso puede acceder
3. **Filtros disponibles** en `/routes`:
   - `?difficulty=easy|medium|hard`
   - `?userId=<id>` (filtrar por usuario)
   - `?minRating=4` (rutas con rating mínimo)

### Futuras Extensiones:
- `/api/comments` para comentarios en rutas
- `/api/clubs` para gestión de clubes moteros