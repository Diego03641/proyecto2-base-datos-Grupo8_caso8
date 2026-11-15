# proyecto2-base-datos-Grupo8_caso8
Sistema de gestión de reparación de equipos electrónicos

## Arquitectura del proyecto
El sistema utilizará cuatro capas:
1. Datos: MySQL almacenará clientes, equipos, órdenes de reparación y demás registros.
2. Acceso a datos: Python, mediante SQLAlchemy o PyMySQL, permitirá consultar y modificar la base de datos.
3. Presentación: Streamlit mostrará formularios, consultas y gráficos.
4. Despliegue: Docker Compose permitirá ejecutar los servicios del proyecto.
Estas tecnologías se implementarán y probarán durante las siguientes etapas.