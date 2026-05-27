# MapTuu — Documentación del proyecto (2º DAM)

**Centro:** CPIFP Alan Turing (Málaga) · **Ciclo:** DAM · **Curso:** 2025/2026  
**Exposición:** 5 de junio de 2026 · **Orden en planning:** 7 (10:30–10:45)

**Repositorio guía del equipo** según [exposiciones_proyecto_intermodular_25_26_2DAM_M](https://github.com/CPIFPAlanTuring/exposiciones_proyecto_intermodular_25_26_2DAM_M).

---

## Índice de contenidos

1. [Personas del equipo](#1-personas-del-equipo)
2. [Explicación del proyecto](#2-explicación-del-proyecto)
3. [Capturas e imágenes del producto](#3-capturas-e-imágenes-del-producto)
4. [Qué aporta el proyecto en cada módulo](#4-qué-aporta-el-proyecto-en-cada-módulo)
5. [Enlaces a repositorios de código](#5-enlaces-a-repositorios-de-código)
6. [Enlace al artefacto en producción](#6-enlace-al-artefacto-en-producción)
7. [Documentación unificada del proyecto (PDF)](#7-documentación-unificada-del-proyecto-pdf)
8. [Resumen de la gestión en Jira (PDF)](#8-resumen-de-la-gestión-en-jira-pdf)
9. [Documentación de código (Compodoc)](#9-documentación-de-código-compodoc)
10. [Documentación técnica (Confluence) — complemento](#10-documentación-técnica-confluence--complemento)
11. [Detalle ampliado por módulo](#11-detalle-ampliado-por-módulo)
12. [Pendientes y limitaciones conocidas](#12-pendientes-y-limitaciones-conocidas)

---

## 1. Personas del equipo

| Nombre | Correo educaAnd | Rol en el proyecto |
|--------|-----------------|-------------------|
| Ezequiel Vargas Berrocal | evarber0103@g.educaand.es | Frontend, integración Firebase, IA, documentación, Confluence |
| José Antonio Domínguez González | jdomgon334@g.educaand.es | Backend API, Android, despliegue, arquitectura |

Organización GitHub del código: [Jose-AntonioT8](https://github.com/Jose-AntonioT8).

---

## 2. Explicación del proyecto

**MapTuu** es una plataforma para **descubrir, crear y compartir actividades** y **planes** (itinerarios geolocalizados): turismo y ocio cotidiano en web, con **API REST**, **app Android** (visor) y **exportación de datos** para informes (Power BI).

### Problema que aborda

Centralizar en un solo lugar el descubrimiento de actividades, la planificación en itinerarios y la interacción de la comunidad (valoraciones, favoritos, reportes de contenido).

### Funcionalidades principales (producto)

| Área | Descripción |
|------|-------------|
| Explorar | Listados y **mapa** (Leaflet en web, Google Maps en Android) |
| Crear | Actividades y planes que agrupan varias actividades |
| Personalizar | Favoritos, perfil, edición de contenido propio |
| Valorar | Reseñas y puntuaciones |
| Buscar | Búsqueda global (usuarios registrados, web) |
| Asistente | Pantalla `/ia` en web (usuarios autenticados) |
| Moderación | Panel admin: tipos de actividad, cola de reportes |
| Móvil | App Android en modo **visor** del mismo catálogo vía API |
| Analítica | Script Python → CSV → Power BI (offline) |

Guía orientada a usuarios no técnicos en Confluence: [MapTuu — Guía de la aplicación](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/24248485).

### Diagrama de arquitectura (alto nivel)

![Diagrama de arquitectura MapTuu](docs/img/00-diagrama-arquitectura.png)

> Pendiente de añadir/actualizar `docs/img/00-diagrama-arquitectura.png` con la versión final del diagrama.

Patrón de datos (web + API): **lecturas** en cliente con Firestore; **escrituras y reglas de dominio** vía HTTP a la API con token Firebase.

Las **capturas de pantalla** del producto (requisito de la guía del centro) están en la [sección 3](#3-capturas-e-imágenes-del-producto), **antes** de la aportación por módulo.

---

## 3. Capturas e imágenes del producto

Capturas de la aplicación (guía del centro: imágenes embebidas directamente en el repo).

### Landing / listado actividades

![Landing / listado actividades](docs/img/01-landing.png)

### Mapa (web)

Pendiente de subir `docs/img/02-mapa-web.png`.

### Detalle de actividad + mapa

Pendiente de subir `docs/img/03-detalle-actividad-mapa.png`.

### Panel admin / reportes

Pendiente de subir `docs/img/04-panel-admin-reportes.png`.

### App Android

Pendiente de subir `docs/img/05-app-android.png`.

Instrucciones: [docs/img/README.md](docs/img/README.md).

---

## 4. Qué aporta el proyecto en cada módulo

Resumen de aportación por módulo para evaluación. El desarrollo detallado con evidencias está en la [sección 11](#11-detalle-ampliado-por-módulo).

| Módulo (profesorado) | Aportación en MapTuu |
|---|---|
| Acceso a datos — Juan Antonio García Gómez | Firestore, autenticación Firebase y exportación de datos |
| Programación multimedia y dispositivos móviles — David Hormigo Ramírez | App Android (visor) con Compose, Room, Retrofit y mapas |
| Programación de servicios y procesos — David Hormigo Ramírez | API REST, scripts de proceso y flujo de exportación Python |
| Desarrollo de interfaces — Carmen Campos Fernández | SPA Angular responsive, i18n, mapas, flujo de usuario |
| Servidores y APIs — Juan Antonio García Gómez | Despliegue Vercel, Swagger, seguridad y CORS |
| Empresa e iniciativa emprendedora II — Rosa Carmen Alcázar Rosal | Propuesta de valor, páginas informativas y enfoque de producto |
| Sistemas de gestión empresarial — Miguel Ángel Ronda Carracao | Exportación CSV para análisis e integración con Power BI |

Para revisión de arquitectura por capas/repositorios: [Anexo de Confluence](#10-documentación-técnica-confluence--complemento).

---

## 5. Enlaces a repositorios de código

| Repositorio | Enlace | Visibilidad | Notas |
|-------------|--------|-------------|-------|
| **Frontend Angular** | https://github.com/Jose-AntonioT8/vercelAngularMappTuu | Privado | Rama producción: `frontend` |
| **Backend Node** | https://github.com/Jose-AntonioT8/vercelNodeMappTuu | Privado | Rama: `main` |
| **Android** | https://github.com/Jose-AntonioT8/androidMappTuu | **Público** | Incluye `MappTuu.apk` en raíz |
| **Python / Power BI** | https://github.com/Jose-AntonioT8/PythonMappTuu | Privado | `export_firestore_to_powerbi.py` |

Este repositorio (**Proyecto-Intermodular-MappTuu**) es solo documentación de exposición; el código vive en los cuatro repos anteriores.

---

## 6. Enlace al artefacto en producción

| Artefacto | URL | Notas |
|-----------|-----|-------|
| **Web (producción)** | https://vercel-angular-mapp-tuu.vercel.app/ | SPA Angular en Vercel |
| **API REST** | https://vercel-node-mapp-tuu.vercel.app/api | Base path `/api` |
| **Swagger / OpenAPI** | https://vercel-node-mapp-tuu.vercel.app/api-docs/ | Documentación interactiva de la API |
| **APK Android** | [MappTuu.apk en GitHub](https://github.com/Jose-AntonioT8/androidMappTuu/blob/main/MappTuu.apk) | ~48 MB; build de referencia en repo (mayo 2026) |

### Acceso para evaluación

- La **web** y la **API** son públicas en las URLs anteriores.
- Para probar flujos con sesión (crear actividad, favoritos, `/ia`, admin), hay que **registrarse** en la aplicación o solicitar al equipo credenciales de prueba si las hubiera configuradas en el entorno — **no se documentan aquí usuarios/contraseñas** por seguridad.
- Repos **privados**: el tribunal puede solicitar acceso invitado a la organización `Jose-AntonioT8` si necesita revisar código en GitHub.

### Comandos rápidos (desarrollo)

Ver [06 - Comandos y entornos](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/23724045) en Confluence.

```bash
# Frontend
git clone https://github.com/Jose-AntonioT8/vercelAngularMappTuu.git
cd vercelAngularMappTuu && git checkout frontend
npm install && cp .env.example .env && npm start

# Backend
git clone https://github.com/Jose-AntonioT8/vercelNodeMappTuu.git
cd vercelNodeMappTuu && npm install && npm run dev

# Android (público)
git clone https://github.com/Jose-AntonioT8/androidMappTuu.git

# Python
git clone https://github.com/Jose-AntonioT8/PythonMappTuu.git
pip install -r requirements.txt && python export_firestore_to_powerbi.py
```

## 7. Documentación unificada del proyecto (PDF)

| Entregable | Estado | Enlace / notas |
|------------|--------|----------------|
| **PDF unificado (Confluence)** | **Pendiente en este repo** | Exportar manualmente el espacio MAP desde Confluence (PDF) y subirlo a `docs/pdf/` — ver [docs/PENDIENTES.md](docs/PENDIENTES.md) |

---

## 8. Resumen de la gestión en Jira (PDF)

| Entregable | Estado | Enlace / notas |
|------------|--------|----------------|
| **Resumen Jira (PDF)** | **Pendiente en este repo** | Proyecto gestionado en https://maptuu.atlassian.net (Jira). Falta exportar estadísticas del tablero y añadir `docs/pdf/jira-resumen.pdf` |

---

## 9. Documentación de código (Compodoc)

| | |
|---|---|
| **Generación** | En `vercelAngularMappTuu`: `npm run docs` / `npm run docs:build` |
| **Publicación en producción** | https://vercel-angular-mapp-tuu.vercel.app/documentation/ |
| **Configuración Vercel** | `vercel.json` ejecuta `docs:build` en el build; salida en `dist/map-tuu/browser/documentation` |

Compodoc documenta componentes, servicios, guards y pipes del frontend Angular a partir de JSDoc en el código.

**Nota:** la API Node no usa Compodoc; su referencia es **Swagger** en la URL de producción indicada arriba.

---

## 10. Documentación técnica (Confluence) — complemento

Espacio del proyecto: **https://maptuu.atlassian.net/wiki/spaces/MAP**

| Documento | Enlace |
|-----------|--------|
| Home / índice | [MappTuu (overview)](https://maptuu.atlassian.net/wiki/spaces/MAP/overview) |
| Guía para personas | [MapTuu — Guía de la aplicación](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/24248485) |
| Repositorios GitHub | [08 - Repositorios GitHub](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/27000833) |
| Arquitectura | [01 - Arquitectura general](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/24150017) |
| Frontend inicio | [Frontend MapPTuu - Inicio](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/2981889) |
| Backend inicio | [Backend MapPTuu - Inicio](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/3014658) |
| Rutas y guards | [Frontend - 2. Rutas y Guards](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/2916353) |
| Modelo Firestore | [Backend - 3. BBDD](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/3112962) |
| API REST | [Backend - 2. API](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/3080193) |
| Android | [09 - Android MappTuu](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/27197450) |
| Python / Power BI | [10 - Python MappTuu](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/27426817) |
| Riesgos técnicos | [07 - Riesgos técnicos](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/24117249) |

Índice ampliado en este repo: [docs/confluence-indice.md](docs/confluence-indice.md).

---

## 11. Detalle ampliado por módulo

Plantilla según el repositorio del centro. Donde no hay evidencia en el repositorio, se indica explícitamente.

### Acceso a datos — Juan Antonio García Gómez

**Objetivos cubiertos:** persistencia en **Cloud Firestore**, autenticación Firebase, exportación de datos para análisis.

**Evidencias:**

| Evidencia | Enlace |
|-----------|--------|
| Modelo Firestore (colecciones, campos, relaciones) | [Confluence — Backend BBDD](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/3112962) |
| Lecturas `onSnapshot` en Angular | `src/app/core/services/activity.service.ts`, `plan.service.ts` (repo frontend) |
| Escrituras vía API + Admin SDK | Repo `vercelNodeMappTuu` — módulos `activities`, `plans`, `users`, `activitytypes`, `reports` |
| Export CSV Power BI | Repo `PythonMappTuu` — `export_firestore_to_powerbi.py` → `output/*.csv` |
| Cuenta de servicio / env | `FIREBASE_SERVICE_ACCOUNT` o `FIREBASE_SERVICE_ACCOUNT_PATH` en Python y Node |

**Limitaciones:** integridad referencial manual en borrados; campos legacy (`IdTypeActivity` vs `activityTypeId`) documentados en [07 - Riesgos](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/24117249).

---

### Programación multimedia y dispositivos móviles — David Hormigo Ramírez

**Objetivos cubiertos:** aplicación **Android** nativa (visor), sensores/permisos (cámara, notificaciones), mapas en móvil.

**Evidencias:**

| Evidencia | Enlace |
|-----------|--------|
| Repositorio Android (público) | https://github.com/Jose-AntonioT8/androidMappTuu |
| Documentación Confluence | [09 - Android MappTuu](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/27197450) |
| Stack | Kotlin, Jetpack Compose, Hilt, Room, Retrofit, Firebase Auth, Google Maps |
| APK de referencia | [MappTuu.apk](https://github.com/Jose-AntonioT8/androidMappTuu/blob/main/MappTuu.apk) |
| Pantallas | `ActivityList`, `PlanList`, `Map`, `Profile`, `Login` — ver README del repo Android |

**Limitaciones:** app principalmente **visor**; creación/edición completa de contenido está centrada en la web.

---

### Programación de servicios y procesos — David Hormigo Ramírez

**Objetivos cubiertos:** API REST, procesos de moderación, scripts de mantenimiento, exportación batch (Python).

**Evidencias:**

| Evidencia | Enlace |
|-----------|--------|
| API Express 5 + TypeScript | https://github.com/Jose-AntonioT8/vercelNodeMappTuu |
| Swagger producción | https://vercel-node-mapp-tuu.vercel.app/api-docs/ |
| Scripts npm | `seed:firestore`, `migrate:activity-moderation`, `test`, `test:coverage` (ver `package.json` del backend) |
| Export offline | `PythonMappTuu` — proceso ETL Firestore → CSV |

**Limitaciones:** el README largo del repo Node incluye material formativo de una API genérica PostgreSQL/Prisma; el **código de producción MapTuu** usa **Firestore** como almacén principal de dominio (ver módulos en `src/modules/`).

---

### Desarrollo de interfaces — Carmen Campos Fernández

**Objetivos cubiertos:** SPA responsive, UX de listados/mapas/formularios, i18n, accesibilidad básica (cabeceras, feedback).

**Evidencias:**

| Evidencia | Enlace |
|-----------|--------|
| Frontend Angular 19 + Tailwind | https://github.com/Jose-AntonioT8/vercelAngularMappTuu (rama `frontend`) |
| Producción | https://vercel-angular-mapp-tuu.vercel.app/ |
| i18n | `src/assets/i18n/` (es, en, de) |
| Mapa detalle actividad (layout) | Merge PR #11 — componente `activity-detail` |
| Rutas y flujos | [Frontend - 2. Rutas y Guards](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/2916353) |
| Seguridad cliente (CSP, headers) | [Frontend - 3. Seguridad](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/2949122) |

**Limitaciones:** no hay auditoría WCAG formal documentada en el repo.

---

### Servidores y APIs — Juan Antonio García Gómez

**Objetivos cubiertos:** despliegue en **Vercel**, API REST documentada, CORS, seguridad HTTP.

**Evidencias:**

| Evidencia | Enlace |
|-----------|--------|
| API en Vercel | https://vercel-node-mapp-tuu.vercel.app/api |
| Swagger UI | https://vercel-node-mapp-tuu.vercel.app/api-docs/ |
| Frontend Vercel | `vercel.json` en repo Angular; build `dist/map-tuu/browser` |
| CORS hacia front de producción | Documentado en Confluence [08 - Repositorios](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/27000833) (mayo 2026) |
| Módulos API | `auth`, `users`, `activities`, `activitytypes`, `plans`, `reports` |

**Limitaciones:** algunos endpoints documentados en riesgos (p. ej. valoración de planes sin auth) — ver [07 - Riesgos](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/24117249).

---

### Empresa e iniciativa emprendedora II — Rosa Carmen Alcázar Rosal

**Objetivos cubiertos (desde el producto documentado):** propuesta de valor de una plataforma de ocio/turismo colaborativa; secciones **Acerca de** y **Contacto** en la web.

**Evidencias:**

| Evidencia | Enlace |
|-----------|--------|
| Descripción de producto y usuarios | [Guía Confluence](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/24248485) |
| Rutas `about`, `contact` | `src/app/app.routes.ts` (lazy load) en repo Angular |
| Landing pública | https://vercel-angular-mapp-tuu.vercel.app/ → `landingPage` |

**Limitaciones:** **no hay** en este repositorio un plan de negocio, estudio de mercado ni análisis financiero en PDF. Si el módulo exige entregables específicos de EIE, deben añadirse por el equipo en `docs/modulos/eie/` (pendiente).

---

### Sistemas de gestión empresarial — Miguel Ángel Ronda Carracao

**Objetivos cubiertos:** exportación de datos de negocio para **informes y dashboards** (Power BI).

**Evidencias:**

| Evidencia | Enlace |
|-----------|--------|
| Script Python | https://github.com/Jose-AntonioT8/PythonMappTuu |
| Tablas CSV | `users`, `activityTypes`, `activities`, `plans`, `activity_reviews`, `plan_reviews`, `plan_activity_links` |
| Documentación | [10 - Python MappTuu](https://maptuu.atlassian.net/wiki/spaces/MAP/pages/27426817) |
| Relaciones Power BI | Por `id`, `activityId`, `planId`, `userId`, `activityTypeId` (README del repo Python) |

**Limitaciones:** no hay capturas de informes Power BI versionadas en el repo; el equipo puede añadirlas en `docs/img/powerbi/` (pendiente).

---

## 12. Pendientes y limitaciones conocidas

Lista detallada: **[docs/PENDIENTES.md](docs/PENDIENTES.md)**

Resumen:

- [ ] PDF exportado de Confluence en `docs/pdf/`
- [ ] PDF resumen Jira en `docs/pdf/`
- [ ] Capturas de pantalla en `docs/img/`
- [ ] URL de este repo en la [tabla del centro](https://github.com/CPIFPAlanTuring/exposiciones_proyecto_intermodular_25_26_2DAM_M#tabla-de-proyectos-participantes-y-url-del-repositorio) (sustituir `PENDIENTE` en orden 7)
- [ ] Entregables específicos de EIE si el profesorado los requiere aparte de la descripción de producto
- [ ] Re-evaluar merge del `feat(ia)` filtrado por pregunta (revertido en `frontend`)

---

## Referencia rápida — exposición

| Dato | Valor |
|------|-------|
| Fecha | 5 junio 2026, 9:00–13:00 |
| Franja equipo MapTuu | **10:30 – 10:45** (orden 7) |
| Duración máxima | 15 minutos (demo incluida) |
| Repo centro (tabla) | https://github.com/Ezequielvb/Proyecto-Intermodular-MappTuu |

---

*Documentación generada a partir de Confluence (espacio MAP), repos Jose-AntonioT8 y plantilla CPIFP Alan Turing. Última revisión: mayo 2026.*