# SPEC.md — Proyecto 2, Grupo 8

**Asignatura:** TDFI103 — Bases de Datos  
**Caso:** Sistema Integral de Gestión de Reparación de Equipos Electrónicos  
**Estado:** Borrador pendiente de validación del equipo  
**Fuentes:** Informe Fase 1 y enunciado oficial Fase 2, Proyecto Semestral 2026.

## 1. Propósito

Desarrollar una base de datos MySQL y un Producto Mínimo Viable (PMV) web para gestionar información de clientes, equipos electrónicos, sucursales, órdenes de reparación, diagnósticos, intervenciones técnicas, repuestos, trabajadores y evaluaciones del servicio.

El proyecto continuará el modelo de la Fase 1, incorporando las correcciones necesarias para cumplir con los requisitos de la Fase 2.

## 2. Alcance

### Incluido

- Corrección y documentación del MERE.
- Modelo relacional definitivo en MySQL Workbench.
- Base de datos MySQL con claves y restricciones.
- Generación de datos sintéticos.
- Seis vistas y seis procedimientos almacenados.
- Aplicación Streamlit conectada a MySQL.
- Formulario para registrar órdenes de reparación.
- CRUD de al menos dos tablas básicas.
- Inicio de sesión con dos o más roles diferenciados.
- Dashboard con cuatro preguntas de negocio.
- Despliegue con Docker y Docker Compose.
- Pruebas, documentación y evidencias.

### Fuera del alcance obligatorio

No se contempla implementar funciones avanzadas de seguridad ni integrar las seis vistas y seis procedimientos evaluados directamente al PMV.

Cualquier funcionalidad adicional requiere aprobación del equipo.

## 3. Actores

**Actores identificados en el caso:**

- Cliente: entrega equipos y puede evaluar el servicio.
- Trabajador administrativo: realiza funciones administrativas.
- Técnico electrónico: participa en reparaciones.
- Especialista en software: participa en trabajos especializados.
- Supervisor: desempeña funciones de supervisión.

**Pendiente:** definir cuáles de estos actores tendrán cuentas de acceso y qué acciones podrá realizar cada rol dentro del PMV.

## 4. Casos de uso

### CU01 — Registrar orden de reparación

Un usuario autorizado selecciona un cliente, equipo y sucursal existentes, registra el problema informado y las fechas necesarias y guarda la orden.

**Resultado:** la nueva orden queda almacenada en MySQL con sus relaciones válidas.

### CU02 — Administrar equipos

Un usuario autorizado consulta, registra, modifica y elimina o desactiva equipos, según las restricciones de integridad.

### CU03 — Administrar repuestos

Un usuario autorizado consulta, registra, modifica y elimina o desactiva repuestos.

### CU04 — Iniciar sesión

Un usuario registrado ingresa sus credenciales. El sistema comprueba su acceso y muestra únicamente las funcionalidades autorizadas.

### CU05 — Consultar dashboard

Un usuario autorizado visualiza las cuatro preguntas de negocio mediante gráficos, tablas y filtros pertinentes.

## 5. Modelo de datos

El modelo definitivo debe representar las siguientes áreas:

- Clientes y equipos.
- Especialización de EQUIPO en COMPUTADOR, TELEFONO_MOVIL y TABLET.
- Sucursales y órdenes de reparación.
- Diagnósticos y evaluaciones dependientes de órdenes.
- Intervenciones técnicas y tipos de trabajo.
- Repuestos y sus detalles de utilización.
- Trabajadores y funciones.
- Usuarios, roles y permisos.

Las tablas y sus relaciones se validarán en MySQL Workbench antes de crear el script SQL.

### Reglas de integridad

- Todas las tablas tendrán una clave primaria.
- Las relaciones se implementarán mediante claves foráneas.
- Se aplicarán restricciones NOT NULL, UNIQUE y CHECK cuando correspondan.
- Se mantendrá la especialización parcial y disyunta de EQUIPO.
- Los diagnósticos y evaluaciones conservarán su numeración por orden.
- Las cantidades utilizadas de repuestos deberán ser positivas.
- Los costos y duraciones no podrán ser negativos.
- Los datos deberán respetar la coherencia entre cliente, equipo, orden y sucursal.

## 6. Requerimientos SQL

Implementar exactamente los objetos solicitados en la sección 7 del enunciado oficial:

**Vistas:** R2, R3, R5, R6, R7 y R8.

**Procedimientos almacenados:** R1, R4, R9, R10, R11 y R12.

Cada objeto debe contar con su sentencia de creación, ejecución, resultado real e interpretación en el informe.

## 7. Arquitectura

### Capa de presentación

Streamlit proporciona formularios, navegación, controles de acceso y dashboard.

### Capa de aplicación

Python 3.12+ gestiona validaciones, reglas de negocio y operaciones de la aplicación.

### Capa de datos

MySQL 8.x almacena la información. SQLAlchemy y PyMySQL permiten la comunicación desde Python.

Pandas y Plotly se utilizan para preparar y visualizar los resultados del dashboard.

### Despliegue

Docker y Docker Compose permiten ejecutar la aplicación y sus servicios.

## 8. Datos de prueba

Generar información sintética, coherente y reproducible utilizando Faker o una herramienta equivalente.

Los datos deben permitir ejecutar las doce consultas y producir visualizaciones significativas.

Los volúmenes orientativos se tomarán de la sección 6 del enunciado oficial.

## 9. Pruebas

- **P01:** reconstruir la base de datos desde cero con el script integral.
- **P02:** comprobar las relaciones y restricciones de integridad.
- **P03:** verificar que los datos sintéticos respeten las reglas del negocio.
- **P04:** ejecutar las seis vistas y los seis procedimientos almacenados.
- **P05:** registrar una orden válida desde Streamlit y verificar su persistencia.
- **P06:** intentar registrar una orden con referencias inválidas y comprobar que sea rechazada.
- **P07:** ejecutar las operaciones CRUD de las dos tablas seleccionadas.
- **P08:** comprobar que los roles tengan accesos diferenciados.
- **P09:** verificar las cuatro visualizaciones y sus filtros.
- **P10:** iniciar el sistema mediante Docker Compose y comprobar su funcionamiento.

## 10. Criterios de aceptación

El proyecto se considerará listo para revisión cuando:

- El MERE y el modelo relacional sean coherentes.
- El script reconstruya correctamente la base de datos.
- Las doce consultas funcionen y tengan evidencias.
- El PMV utilice la misma base de datos MySQL.
- El formulario transaccional funcione.
- Existan dos CRUD operativos.
- El inicio de sesión aplique permisos reales.
- El dashboard responda las cuatro preguntas.
- Docker permita ejecutar el PMV.
- El informe, las bitácoras y la matriz de responsabilidades estén completos.

## 11. Decisiones pendientes

- Aprobar las claves definitivas de DIAGNOSTICO y EVALUACION.
- Definir cómo se validará la capacitación de trabajadores.
- Definir los roles y permisos concretos del PMV.
- Seleccionar las dos tablas del CRUD.
- Formular y justificar la cuarta pregunta del dashboard.
- Establecer el tratamiento de equipos sin clasificar.
- Definir el criterio de cálculo de costos y evaluaciones promedio.
- Asignar responsables principales y colaboradores.
- Consultar al docente cómo cumplir la exigencia de cuatro responsables principales distintos para las cuatro funciones del PMV si el grupo sigue compuesto por dos integrantes.

## 12. Validación y uso de IA

La IA podrá ayudar a revisar modelos, generar propuestas y corregir errores.

Todo SQL, código Python, configuración Docker y decisión de diseño deberá ser comprendido, ejecutado y validado por el equipo antes de su entrega.

Las modificaciones importantes se registrarán en el informe y las bitácoras individuales.

---

**Nota:** Este documento es un borrador de especificación. Los casos de uso CU02 y CU03 proponen EQUIPO y REPUESTO como tablas para el CRUD; deben confirmarse con el equipo. No se ha generado código de implementación.
