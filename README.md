# Catálogo Mayorista con Armado de Pedidos

> Solución de ingeniería Full Stack para distribuidores mayoristas: catálogo digital móvil, motor transaccional de importación masiva de planillas (CSV/Excel) y generador de pedidos vía WhatsApp y correo electrónico con congelamiento de precios históricos.

## 📌 Visión del Proyecto
Este repositorio contiene la arquitectura, especificaciones de diseño, modelos de datos y estructura organizativa para una plataforma web B2B de comercio mayorista. Resuelve la fricción de distribuidores que operan con listas en PDF desactualizadas, permitiendo actualizar miles de artículos en minutos y dotando al cliente minorista de una experiencia ágil para armar y repetir pedidos con precios vigentes.

## 🧱 Arquitectura del Repositorio (Monorepo)
```text
catalogo-mayorista/
├── .github/                      # Automatización CI/CD (ci.yml, deploy.yml)
├── apps/                         # Aplicaciones ejecutables
│   ├── api/                      # Backend REST API (Node.js, Fastify, TypeScript)
│   └── web/                      # Frontend PWA (React, Vite, Tailwind CSS, Radix UI)
├── packages/                     # Librerías y paquetes compartidos
│   ├── core-importer/            # Motor de importación masiva (funciones puras)
│   ├── database/                 # Prisma ORM, esquemas relacionales, migraciones y seeds
│   ├── shared/                   # Tipos TypeScript compartidos y esquemas Zod
│   └── tsconfig/                 # Configuraciones base de TypeScript
├── infra/                        # Infraestructura como código y contenedores (Docker Compose)
├── tests/                        # Pruebas integradas (Playwright E2E y fixtures CSV/XLSX)
└── docs/                         # Documentación de ingeniería, ADRs y especificaciones
    ├── architecture/             # Architecture Decision Records (ADRs)
    ├── api-specs/                # Especificación OpenAPI / REST
    └── fullstack-manifesto.md    # Fundamentos de la arquitectura Full Stack
```

## 🛠️ Stack Tecnológico
- **Frontend:** React 18+, TypeScript, Vite, Tailwind CSS, Radix UI. PWA con persistencia en localStorage (Zustand).
- **Aceleración Gráfica (WebGL):** Three.js / React Three Fiber (Visor 3D del bulto) y regl (Mapa de impacto de precios de 10.000 celdas).
- **Backend:** Node.js 20+, Fastify, TypeScript, Zod, sesiones con cookies HttpOnly y hash argon2.
- **Base de Datos:** PostgreSQL 16+, Prisma ORM, extensiones pg_trgm para búsqueda difusa rápida.
- **Parseo & Documentos:** PapaParse, SheetJS, pdf-lib, Resend.
- **Testing & DevOps:** Vitest, Playwright, Docker multi-etapa, GitHub Actions.
