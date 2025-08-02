# User Stories

## Épica 1: Autenticación y Perfil

### US-01: Registro de usuario
**Como** motero no registrado,
**Quiero** crear una cuenta con email, contraseña y nombre
**Para** acceder a todas las funcionalidades de la app.

**Criterios de aceptación**:
- Formulario con: email, password (6+ caracteres), nombre
- Validación email único y formato válido
- Encriptación password con bcrypt
- Email de confirmación (opcional para MVP)

---

### US-02: Inicio de sesión
**Como** motero registrado,
**Quiero** iniciar sesión de forma segura
**Para** gestionar mis rutas y perfil.

**Criterios**:
- Login con email + password
- Generación JWT con expiración 24h
- Protección contra ataques de fuerza bruta (máximo 5 intentos)

---

## Épica 2: Gestión de Rutas

### US-03: Creación de rutas
**Como** motero autenticado,
**Quiero** crear rutas con detalles técnicos
**Para** compartir mis recorridos.

**Criterios**:
- Campos obligatorios:
  - Título (50 caracteres máximo)
  - Descripción (200 caracteres máximo)
  - Dificultad (Fácil/Media/Difícil/Extrema)
  - Track GPS (GPX/KML o trazado manual)
- Campos opcionales:
  - Imagen portada (5MB máximo, JPG/PNG)
  - Recomendaciones (equipamiento, época del año)

---

### US-04: Visualización de ruta
**Como** usuario (con/sin autenticación),
**Quiero** ver el detalle completo de cada ruta
**Para** valorar si hacerla.

**Criterios**:
- Mapa interactivo con:
  - Track completo (Polyline)
  - Puntos de interés (curvas peligrosas, vistas)
- Sección técnica:
  - Distancia total
  - Desnivel acumulado
  - Tipo de terreno (asfalto/trial)
- Sistema de rating (1-5 estrellas)

---

### US-05: Edición de rutas
**Como** creador de una ruta,
**Quiero** modificar los detalles
**Para** corregir errores o añadir información.

**Criterios**:
- Solo el creador puede editar
- Historial de cambios (opcional para fase 2)
- Notificar a usuarios que guardaron la ruta

---

### US-06: Eliminación de rutas
**Como** creador de una ruta,
**Quiero** eliminar rutas
**Para** gestionar mi contenido.

**Criterios**:
- Confirmación modal "¿Estás seguro?"
- Eliminación en cascada de ratings asociados
- Backup automático por 30 días (opcional)

---

## Épica 3: Sistema de Rating

### US-07: Valorar rutas
**Como** usuario registrado,
**Quiero** puntuar rutas (1-5 estrellas)
**Para** ayudar a otros moteros.

**Criterios**:
- Solo 1 voto por usuario/ruta
- Poder modificar mi voto
- Mostrar:
  - Media aritmética (ej: 4.2)
  - Total de votos (ej: 15 valoraciones)

---

### US-08: Filtrado avanzado
**Como** motero,
**Quiero** filtrar rutas por rating/dificultad
**Para** encontrar las mejores opciones.

**Criterios**:
- Filtros combinables:
  - Rating (mínimo 3/4/5 estrellas)
  - Dificultad (1+ opciones)
  - Distancia (rango en km)
- Ordenación por:
  - Mejor valoradas
  - Más recientes

---

## Prioridades

### MVP Fase 1 (Core)
- US-01 a US-04 (Auth + CRUD básico)
- US-07 (Rating básico)

### Fase 2 (Mejoras)
- US-05 a US-06 (Gestión avanzada)
- US-08 (Filtros)
- Notificaciones (US-05)

### Fase 3 (Social)
- Comentarios en rutas
- Compartir en redes
- Retos mensuales