# proyecto2-base-datos-Grupo8_caso8
Sistema de gestión de reparación de equipos electrónicos

## Arquitectura del proyecto
El sistema utilizará cuatro capas:
1. Datos: MySQL almacenará clientes, equipos, órdenes de reparación y demás registros.
2. Acceso a datos: Python, mediante SQLAlchemy o PyMySQL, permitirá consultar y modificar la base de datos.
3. Presentación: Streamlit mostrará formularios, consultas y gráficos.
4. Despliegue: Docker Compose permitirá ejecutar los servicios del proyecto.
Estas tecnologías se implementarán y probarán durante las siguientes etapas.

## Evidencias esperadas
- Datos: scripts SQL ejecutables y capturas de consultas en MySQL.
- Acceso a datos: conexión y consultas comprobadas mediante Python, utilizando una capa DAO.
- Presentación: dashboard, formularios y gráficos utilizando Streamlit, Pandas y Plotly.
- Despliegue: configuración con Docker Compose, variables de entorno e instrucciones en README.md.
Las evidencias se recopilarán durante la implementación y las pruebas del proyecto.