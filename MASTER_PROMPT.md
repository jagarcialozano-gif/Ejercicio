# Master Prompt — Plataforma de Seguimiento y Rastreo de Asesores Comerciales

## Rol del modelo
Actúa como un **arquitecto de software senior + product manager + diseñador UX/UI + tech lead full-stack** para construir una plataforma llamada **Ruta360** orientada al seguimiento en tiempo real de asesores comerciales en campo.

## Objetivo del producto
Diseñar e implementar una aplicación web + móvil para:
1. Monitorear ubicación en tiempo real de asesores comerciales.
2. Comparar el recorrido ejecutado vs recorrido planificado.
3. Detectar desviaciones de ruta y generar alertas automáticas.
4. Registrar visitas, evidencias y productividad comercial.
5. Brindar tablero de control para supervisores y gerencia.

## Entregables obligatorios
Genera la solución completa en fases, incluyendo:

### 1) Descubrimiento y alcance
- Problema a resolver.
- Usuarios objetivo.
- Alcance MVP y alcance futuro.
- Supuestos, restricciones y riesgos.

### 2) Requerimientos funcionales y no funcionales
- Catálogo de funcionalidades priorizadas (Must/Should/Could/Won’t).
- Reglas de negocio para desvío de recorridos.
- Requerimientos de seguridad, privacidad, disponibilidad y rendimiento.

### 3) Historias de usuario
- Historias por rol (Asesor, Supervisor, Administrador, Gerencia).
- Criterios de aceptación tipo Gherkin (Given/When/Then).
- Definición de DoR y DoD.

### 4) Diseño de interfaz
- Mapa de navegación (sitemap).
- Wireframes textuales por pantalla.
- Sistema de diseño base: tipografía, colores, componentes y estados.
- Buenas prácticas de accesibilidad (WCAG AA).

### 5) Arquitectura técnica
- Arquitectura de referencia (frontend, backend, BD, colas, mapas, notificaciones).
- Diseño de datos (entidades, relaciones, índices geo-espaciales).
- API REST/GraphQL (endpoints, payloads, códigos de respuesta).
- Servicios de geolocalización y cálculo de rutas.

### 6) Motor de alertas por desviación
Diseña el motor con:
- Geocercas dinámicas y tolerancia configurable (metros/minutos).
- Comparación de trayecto planificado vs real.
- Estados de alerta: *riesgo*, *desviación leve*, *desviación crítica*, *resuelta*.
- Reglas anti-ruido (histeresis, suavizado GPS, ventanas temporales).
- Escalamiento automático (push → supervisor → correo → bloqueo de nuevas visitas).
- Bitácora auditable de eventos.

### 7) Plan de implementación
- Roadmap por sprints (2 semanas).
- Dependencias técnicas y organizacionales.
- Estrategia de pruebas (unitarias, integración, E2E, campo).
- Plan de despliegue y observabilidad.

### 8) Métricas y analítica
- KPIs operativos y comerciales.
- Métricas del motor de alertas (precisión/recall, falsos positivos).
- Dashboard ejecutivo con objetivos y umbrales.

### 9) Seguridad y cumplimiento
- Gestión de identidad y accesos (RBAC).
- Cifrado en tránsito y reposo.
- Trazabilidad y auditoría.
- Políticas de retención y anonimización de datos sensibles.

### 10) Entrega de artefactos
Debes entregar en formato Markdown:
- `README` funcional del producto.
- Backlog inicial priorizado.
- Historias de usuario completas.
- Especificación de API.
- Esquema de base de datos.
- Plan de QA.
- Manual breve de operación para supervisor.

## Contexto del dominio
- Los asesores tienen rutas diarias con clientes planificados.
- El sistema debe funcionar con conectividad intermitente.
- Debe existir modo offline en móvil y sincronización diferida.
- Se requiere evidencia de visita: foto, comentario, checklist y geotag.

## Restricciones técnicas sugeridas
- Frontend web: React + TypeScript.
- App móvil: Flutter o React Native.
- Backend: Node.js (NestJS) o Python (FastAPI).
- Base de datos: PostgreSQL + PostGIS.
- Mensajería/eventos: Redis Streams o Kafka.
- Mapas: Google Maps Platform o Mapbox.
- Notificaciones: Firebase Cloud Messaging + correo transaccional.

## Reglas de calidad de la respuesta
- Escribe en español claro y profesional.
- Justifica decisiones técnicas con pros/contras.
- Incluye tablas donde aporte claridad.
- No dejes secciones “pendientes”.
- Entrega output accionable y listo para ejecución por un equipo de desarrollo.

## Criterios de éxito
La propuesta final se considera exitosa si:
1. Permite operar seguimiento en tiempo real con baja latencia.
2. Reduce desviaciones no justificadas mediante alertas oportunas.
3. Aumenta productividad y trazabilidad del trabajo en campo.
4. Es escalable, segura y mantenible.
