# Kine – Replicación académica de la base de datos de Nequi  
**Bases de Datos II · Semestre 2025‑I**

**Autores**
- José Jesús Céspedes Rivera - 20211020118  
- Sofía Lozano Martínez - 20211020088  

Este repositorio reúne los **tres workshops** desarrollados durante el semestre para construir y evolucionar el núcleo de datos de **Kine**, una versión académica de la plataforma financiera Nequi. Cada taller aborda un conjunto distinto de retos: modelado conceptual y de negocio, diseño lógico y físico, y finalmente concurrencia y distribución.

---

## 📁 Estructura del repositorio


---

## 1 · Workshop 1 – Modelo de negocio y modelo de datos inicial

- Propuesta de valor y segmentos de usuario definidos mediante Value Proposition Canvas y modelo CANVAS.
- Requerimientos funcionales y no funcionales enfocados en disponibilidad, usabilidad móvil y métricas de crecimiento.
- Modelo ER inicial (PlantUML) con entidades clave como Usuario, Cuenta, Movimiento, Producto, etc.
- Evaluación de tecnologías y justificación de un stack híbrido PostgreSQL + MongoDB (SQL para OLTP, Mongo para auditoría y logs).

---

## 2 · Workshop 2 – Diseño lógico/físico y consultas

- Script DDL en PostgreSQL definiendo los requerimientos de informacion.
- Modelo de colecciones en MongoDB para soporte y trazabilidad
- Conjunto de queries optimizadas e indexadas para operaciones típicas del sistema.
- Mejoras al modelo conceptual a partir de retroalimentación obtenida en Workshop 1.

---

## 3 · Workshop 3 – Concurrencia, BD distribuida y rendimiento

- Análisis de concurrencia: escenarios críticos como transferencias simultáneas, accesos paralelos y conflictos de actualización.
- Soluciones implementadas: MVCC, bloqueo 2-fase, niveles de aislamiento, control optimista, uso de Redis para locks distribuidos.
- Diseño distribuido multirregional: PostgreSQL activo + almacenamiento histórico en la nube.
- Estrategias de rendimiento (por el compañero de equipo): fragmentación, replicación geográfica, ejecución paralela, reducción de latencia.

---


