# Tech Stack

## Frontend

### Core
- **Framework**: [React](https://react.dev/) (v18+) con TypeScript
- **Bundler**: [Vite](https://vitejs.dev/) (v4+)
- **Estilos**: [Tailwind CSS](https://tailwindcss.com/) (v3+)
- **Routing**: [React Router DOM](https://reactrouter.com/) (v6+)

### State Management
- **Local State**: Context API + useReducer
- **Server State**: [SWR](https://swr.vercel.app/) (opcional para caching avanzado)

### Formularios
- [React Hook Form](https://react-hook-form.com/) (v7+)
- [Zod](https://zod.dev/) para validación de esquemas

### Testing
- [Vitest](https://vitest.dev/) (Unit Testing)
- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
- [MSW](https://mswjs.io/) (Mock API)

### HTTP Client
- [Axios](https://axios-http.com/) (v1+)

### Configuración
- **Aliases**: Configuración de `@/` en `vite.config.ts`
- **Environment**: Variables con `.env`

---

## Backend

### Core
- **Runtime**: [Node.js](https://nodejs.org/) (v18+ LTS)
- **Framework**: [Express](https://expressjs.com/) (v4+)
- **Database**: [MongoDB](https://www.mongodb.com/) (v6+)

### Librerías Clave (Por Definir)
| Categoría          | Opciones a Evaluar                     |
|--------------------|----------------------------------------|
| ORM/ODM           | Mongoose, Prisma (MongoDB)             |
| Autenticación     | JWT, Passport.js                       |
| Validación        | Zod, Joi                               |
| Seguridad         | Helmet, rate-limiter                   |
| Logging           | Winston, Morgan                        |

---

## Infraestructura (Futuro)

### Deployment
- **Frontend**: Vercel/Netlify
- **Backend**: Render/AWS EC2
- **Database**: MongoDB Atlas

### Monitoring
- **Frontend**: Sentry
- **Backend**: New Relic

---

## Justificación de Elecciones

### Frontend
- **Vite**: Mayor velocidad que Webpack para desarrollo
- **Tailwind**: Facilita prototipado rápido sin salir de JSX
- **Zod + RHF**: Combinación óptima para forms type-safe

### Backend (Consideraciones Iniciales)
- **Express**: Más fácil de aprender para juniors vs Nest.js
- **MongoDB**: Flexibilidad con datos de rutas GPS (schemaless)

---

## Próximos Pasos
1. Definir stack de testing backend (Jest/Mocha)
2. Evaluar solución para uploads de imágenes (Cloudinary vs S3)
3. Configurar CI/CD básico (GitHub Actions)