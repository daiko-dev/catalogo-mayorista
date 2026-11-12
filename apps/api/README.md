# Backend REST API (apps/api)
API construida con Node.js, Fastify y TypeScript.
- Arquitectura modular por dominios: auth (argon2 y cookies httpOnly), catalog (búsqueda pg_trgm), orders (PDF con pdf-lib y emails con Resend), imports (orquestador transaccional) y settings.
- Validación perimetral con esquemas Zod compartidos y rate limiting en endpoints públicos.
