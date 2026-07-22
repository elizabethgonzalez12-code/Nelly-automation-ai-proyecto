# Automatización Inteligente para Seguimiento de Entregas Pendientes

## Descripción

Este proyecto fue desarrollado como trabajo final del curso de AI Automation.

El objetivo es automatizar el seguimiento de órdenes de compra pendientes mediante la integración de Airtable, Gmail y n8n, incorporando reglas de negocio, clasificación de prioridades y validación humana para casos críticos.

La solución permite identificar automáticamente entregas pendientes, clasificarlas según su nivel de criticidad y ejecutar acciones de seguimiento de forma automatizada.

---

## 🎥 Video Demo

El funcionamiento completo de la automatización puede visualizarse en el siguiente enlace:

**Video demostrativo:**

https://drive.google.com/drive/folders/1AhEOz438s0OOKsphpa-aPg3IlL5zV34n?usp=sharing

---

## Problema de Negocio

El área de abastecimiento necesita monitorear órdenes de compra pendientes y detectar retrasos que puedan impactar la disponibilidad de productos.

Realizar este control manualmente consume tiempo y dificulta la priorización de los casos más urgentes.

La automatización permite:

- Detectar órdenes pendientes.
- Clasificar prioridades.
- Notificar automáticamente a los responsables.
- Mantener trazabilidad de las acciones realizadas.
- Incorporar validación humana en situaciones críticas.

---

## Tecnologías Utilizadas

- n8n
- Airtable
- Gmail
- Webhooks
- GitHub
- Google Drive (Video Demo)

---

## Arquitectura de la Solución

**Webhook → Airtable → Switch → Gestión según prioridad → Actualización de estado**

### Flujo General

1. El proceso inicia mediante un Webhook.
2. Se consultan los registros pendientes en Airtable.
3. Un nodo Switch clasifica los registros según la prioridad.
4. Se ejecutan acciones específicas para cada nivel:

   - CRÍTICA
   - MEDIA
   - BAJA
   - OK

5. Se envían notificaciones por correo electrónico.
6. Se actualizan los registros correspondientes en Airtable.

---

## Human In The Loop (HITL)

Las órdenes clasificadas como **CRÍTICAS** requieren validación humana antes de continuar el proceso.

Para ello se implementó un nodo **Wait** configurado con **Webhook Call**, permitiendo que la ejecución quede pausada hasta recibir una aprobación manual desde el correo electrónico.

Este mecanismo evita acciones automáticas sobre situaciones sensibles y proporciona mayor control operativo.

---

## Manejo de Prioridades

### CRÍTICA

- Envío de alerta por correo electrónico.
- Espera de validación humana (HITL).
- Actualización del estado en Airtable.

### MEDIA

- Envío de notificación por correo electrónico.
- Actualización del estado en Airtable.

### BAJA

- Envío de notificación por correo electrónico.
- Actualización del estado en Airtable.

### OK

- Registro informativo.
- Actualización del estado en Airtable.

---

## Base de Datos

Airtable se utiliza como repositorio central para almacenar:

- Órdenes de compra.
- Proveedores.
- Fechas compromiso.
- Días de atraso.
- Prioridad.
- Estado del seguimiento.

---

## Acceso a Airtable

Base de datos utilizada durante el desarrollo y pruebas del proyecto:

https://airtable.com/app51KuQa8TpNIkuu/shrJDq90i685I0M33

La base contiene los registros de órdenes de compra pendientes, clasificación de prioridades, estados de seguimiento y datos utilizados por la automatización.

---

## Evidencias

Las evidencias del funcionamiento incluyen:

- Video demostrativo del funcionamiento completo.
- Workflow desarrollado en n8n.
- Integración con Airtable.
- Integración con Gmail.
- Implementación de Human-In-The-Loop (HITL) mediante nodo Wait.
- Actualización automática de registros.
- Clasificación por prioridad (CRÍTICA, MEDIA, BAJA y OK).
- Capturas de pantalla del workflow y de las pruebas realizadas.

---

## Autor

**Elizabeth González**

Trabajo Final – AI Automation
