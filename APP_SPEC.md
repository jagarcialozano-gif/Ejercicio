# Ruta360 — Definición de la Aplicación

## 1) Alcance de la solución

### Alcance MVP (primer release)
- Seguimiento GPS en tiempo real de asesores desde app móvil.
- Planificación de rutas diarias por supervisor.
- Visualización en mapa de ruta planificada vs ruta recorrida.
- Detección de desviación con alertas automáticas.
- Registro de visitas con evidencia (foto, nota, checklist, hora de llegada/salida).
- Panel web para supervisión operativa y productividad básica.
- Modo offline con sincronización al recuperar conectividad.

### Alcance fase 2 (evolutivo)
- Recomendación automática de mejor secuencia de visitas.
- Predicción de riesgo de desviación por zona/horario.
- Integración con CRM/ERP.
- Gamificación y ranking de cumplimiento de rutas.
- Motor de reglas avanzado por tipo de cliente, SLA y región.

### Fuera de alcance (por ahora)
- Nómina y liquidación de comisiones.
- Gestión financiera/contable.
- Optimización logística de flotas de reparto pesado.

---

## 2) Funcionalidades principales

### A. Gestión de usuarios y roles
- Roles: Asesor, Supervisor, Administrador, Gerencia.
- Inicio de sesión seguro (MFA opcional).
- Permisos por rol (RBAC).

### B. Planificación y asignación
- Creación de rutas por día, zona y prioridad.
- Asignación de cartera de clientes por asesor.
- Horarios objetivo por visita.

### C. Seguimiento en tiempo real
- Actualización de ubicación cada X segundos (configurable).
- Mapa en vivo con estado del asesor (en ruta, en visita, inactivo).
- Línea comparativa entre ruta planificada y ruta real.

### D. Alertas de desviación de recorridos
- Regla base por distancia: alerta si el asesor se aleja más de N metros del trayecto planificado.
- Regla base por tiempo: alerta si permanece fuera de ruta más de M minutos.
- Niveles de alerta:
  - Informativa
  - Leve
  - Crítica
- Escalamiento:
  - Push al asesor.
  - Notificación al supervisor.
  - Registro de incidente para auditoría.

### E. Gestión de visitas
- Check-in/check-out con geolocalización.
- Evidencias: foto, comentarios, checklist.
- Resultado de visita (exitosa, no efectiva, reprogramada).

### F. Analítica y reporting
- KPIs por asesor, zona y periodo.
- Índice de cumplimiento de ruta.
- Tiempo promedio entre visitas.
- Tasa de desvío y reincidencia.

### G. Auditoría y cumplimiento
- Bitácora de eventos (login, cambios de ruta, alertas, cierres).
- Exportación de reportes (CSV/PDF).
- Trazabilidad por usuario y timestamp.

---

## 3) Historias de usuario (resumen)

### Como Asesor Comercial
1. **Ver mi ruta del día** para saber qué clientes visitar y en qué orden.
2. **Registrar inicio de jornada** para habilitar el seguimiento GPS.
3. **Registrar visita con evidencia** para respaldar la ejecución en campo.
4. **Recibir alertas de desvío** para corregir el recorrido de forma oportuna.
5. **Operar en modo offline** para no perder registros cuando no haya señal.

### Como Supervisor
6. **Visualizar asesores en mapa en tiempo real** para monitorear avance.
7. **Configurar umbrales de desviación** por zona o tipo de ruta.
8. **Recibir alertas críticas** para tomar acción rápida.
9. **Reasignar visitas** cuando exista contingencia.
10. **Consultar indicadores diarios** para evaluar desempeño del equipo.

### Como Administrador
11. **Gestionar usuarios, roles y permisos** para asegurar gobernanza.
12. **Configurar catálogos** (zonas, clientes, motivos de visita, reglas).
13. **Auditar actividad del sistema** para cumplir políticas internas.

### Como Gerencia
14. **Ver dashboard ejecutivo** para identificar productividad y riesgos.
15. **Comparar cumplimiento entre regiones** para decisiones estratégicas.

---

## 4) Interfaz propuesta

## 4.1 Aplicación móvil (Asesor)
1. **Login**
   - Campos: usuario, contraseña, OTP (opcional).
   - Estado de conectividad visible.

2. **Inicio / Ruta del día**
   - Tarjeta resumen: visitas programadas, visitas completadas, atrasos.
   - Botón “Iniciar jornada”.
   - Acceso rápido al mapa.

3. **Mapa de recorrido**
   - Ruta planificada (línea azul).
   - Ruta real (línea verde).
   - Desviación (tramo rojo).
   - Clientes pendientes/completados con iconos.

4. **Detalle de visita**
   - Datos del cliente.
   - Check-in / Check-out.
   - Formulario de evidencia (foto, notas, checklist).

5. **Alertas**
   - Lista cronológica de alertas.
   - Estado (activa/resuelta).
   - Acciones sugeridas.

## 4.2 Portal web (Supervisor / Gerencia)
1. **Dashboard operativo**
   - Mapa con todos los asesores.
   - Filtros por zona, estado y severidad.
   - Widget de alertas en tiempo real.

2. **Módulo de planificación**
   - Agenda de rutas por día/semana.
   - Drag & drop de clientes por asesor.

3. **Módulo de alertas**
   - Bandeja de incidentes.
   - SLA de respuesta.
   - Estado de gestión del incidente.

4. **Reportes y analítica**
   - KPIs de cumplimiento.
   - Tasa de desviación por asesor y zona.
   - Exportación y envío programado.

---

## 5) Reglas del sistema de alertas de desviación

- **Umbral de distancia:** generar prealerta si la distancia al corredor de ruta supera 150 m.
- **Umbral de tiempo:** escalar a alerta leve si el desvío persiste > 5 min.
- **Alerta crítica:** desvío > 500 m o > 15 min fuera de ruta.
- **Exclusiones:** zonas sin cobertura GPS estable y desvíos autorizados por supervisor.
- **Anti-falsos positivos:** media móvil de posiciones + validación de 3 lecturas consecutivas.
- **Cierre de alerta:** retorno al corredor de ruta durante al menos 2 min continuos.

---

## 6) Requerimientos no funcionales

- Disponibilidad objetivo: 99.5%.
- Latencia de actualización en tiempo real: < 5 segundos promedio.
- Seguridad: cifrado TLS 1.2+ y datos sensibles cifrados en reposo.
- Escalabilidad: arquitectura preparada para crecimiento por regiones.
- Trazabilidad: toda acción crítica queda auditada.
- Accesibilidad: interfaz web con lineamientos WCAG AA.

---

## 7) MVP listo para implementación

Para iniciar desarrollo inmediato:
1. Definir diseño detallado de API y modelo de datos.
2. Construir app móvil con tracking + registro de visitas.
3. Construir portal supervisor con mapa y bandeja de alertas.
4. Implementar motor de reglas de desviación y notificaciones.
5. Cerrar con piloto de campo de 2 semanas y ajuste de umbrales.
