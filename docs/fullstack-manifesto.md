# Manifiesto Full Stack: Las 10 Dimensiones de Ingeniería

Este documento establece los principios y pilares fundamentales de arquitectura e ingeniería para la plataforma B2B de catálogo mayorista.

## 1. Arquitectura Monorepo
Unificación de aplicaciones (`apps/api`, `apps/web`) y paquetes compartidos (`packages/core-importer`, `packages/database`, `packages/shared`, `packages/tsconfig`) bajo un mismo repositorio gobernado por `pnpm`. Permite compartición de tipos de extremo a extremo, refactorización atómica y gestión coherente de dependencias.

## 2. Dominio Puro
Aislamiento de la lógica de negocio nuclear en librerías independientes y desacopladas de frameworks de UI o controladores HTTP. `core-importer` opera como un conjunto de funciones puras e idempotentes para el procesamiento, normalización y validación de datos.

## 3. Frontend Mobile-First / PWA
Experiencia de usuario optimizada primordialmente para dispositivos móviles de clientes minoristas. Soporte PWA para capacidades offline parciales, almacenamiento persistente local mediante Zustand/localStorage y carga ultrarrápida.

## 4. WebGL Progressive Enhancement
Uso de aceleración gráfica vía WebGL con Three.js / React Three Fiber para visualización 3D interactiva de dimensiones de bultos y `regl` para la renderización de alto rendimiento de mapas de impacto de precios de 10.000 celdas sin degradar la respuesta de la UI.

## 5. Backend Fastify
Servidor HTTP de alto rendimiento impulsado por Fastify y TypeScript. Validaciones estrictas con esquemas Zod, bajo overhead de CPU y memoria, y arquitectura basada en plugins para modularidad limpia.

## 6. Modelado Relacional PostgreSQL / pg_trgm / ACID
Modelado robusto en PostgreSQL 16+ gestionado vía Prisma ORM. Garantía de integridad transaccional ACID para congelamiento de precios e importaciones masivas, e índice `pg_trgm` para búsquedas de texto completo y difusas de SKUs y productos.

## 7. Seguridad en Profundidad
Protección multicapa que incluye autenticación segura mediante hash Argon2, gestión de sesiones con cookies HttpOnly/SameSite, validación rigurosa de entradas en frontend y backend, y principio de menor privilegio.

## 8. Infraestructura Docker / IaC
Contenerización estandarizada mediante Docker multi-etapa para entornos de desarrollo y producción consistentes. Infraestructura como código con Docker Compose para orquestación local de servicios (App, API, DB).

## 9. CI/CD Automatizado
Flujos de trabajo automatizados con GitHub Actions para integración y despliegue continuos (linting, type-checking, ejecución de suites de prueba unitarias e integradas, y construcción de imágenes Docker).

## 10. Estrategia de Testing
Enfoque de pruebas piramidal que abarca pruebas unitarias ultrarrápidas con Vitest para lógica de dominio e importación, y pruebas de extremo a extremo (E2E) con Playwright validando flujos críticos de usuario e importación de archivos CSV/XLSX.
