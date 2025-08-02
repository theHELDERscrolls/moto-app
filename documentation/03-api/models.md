# Modelos de Datos

## Usuario (`User`)

Representa a un motero registrado en la plataforma.

```ts
interface User {
  _id: string;           // Identificador único (generado por MongoDB)
  email: string;         // Email único para login
  password: string;      // Contraseña encriptada (bcrypt)
  username: string;      // Nombre público (ej: "MoteroX")
  avatar?: string;       // URL de la imagen de perfil (opcional)
  role: 'user' | 'admin'; // Roles básicos
  createdAt: Date;       // Fecha de registro
  updatedAt: Date;       // Última actualización
  // Potenciales extensiones:
  // - favoriteRoutes: string[] (IDs de rutas favoritas)
  // - bikeType: 'street' | 'offroad' | 'both'
}
```

**Relaciones**:

- Un `User` puede tener múltiples `Route` (relación 1:N)
---
## Ruta (`Route`)

Representa una ruta motera compartida por un usuario.

```ts
interface Route {
  _id: string;
  title: string;         // Nombre de la ruta (ej: "Curvas del Tajo")
  description: string;   // Detalles (max 500 caracteres)
  difficulty: 'easy' | 'medium' | 'hard' | 'extreme';
  distance: number;      // Kilómetros (calculado al subir el track)
  duration?: number;     // Minutos estimados (opcional)
  coordinates: {        // Array de puntos GPS
    lat: number;
    lng: number;
    elevation?: number;  // Altitud (opcional)
  }[];
  userId: string;       // ID del usuario creador (relación)
  images?: string[];    // URLs de imágenes (max 5)
  rating?: {           // Sistema de valoración
    average: number;   // Puntuación media (1-5)
    count: number;     // Total de valoraciones
  };
  createdAt: Date;
  updatedAt: Date;
  // Campos para futuras extensiones:
  // - tags: string[] (ej: ['montaña', 'asfalto'])
  // - isPublic: boolean
}
```

**Relaciones**:

- Pertenece a un `User` (campo `userId`).
- Puede tener múltiples valoraciones (implícito en `rating.count`).
---
## Consideraciones para Evolución

### Usuario

1. **Perfil extendido**.

```ts
// Futura ampliación:
interface User {
  socialMedia?: {
    instagram?: string;
    youtube?: string;
  };
  ridingSince?: number; // Año inicio en moto
}
```
### Ruta

2. **Track avanzado**.

```ts
coordinates: {
  lat: number;
  lng: number;
  timestamp?: Date;  // Para grabación en tiempo real
  waypoint?: boolean // Puntos de interés
}[];
```

3. Clubes (futuro).

```ts
interface Route {
  clubId?: string; // Relación opcional con club organizador
}
```