# backend-plus

Es un framework para desarrollar aplicaciones web basadas en base de datos PostgreSQL. Sus características destacadas son:

  1. Está basado en metadatos centralizados que definen:
     1. La estructura de datos (estructura de tablas y vistas, con restricciones y fk)
     2. La estructura de procesos (definición de parámetros, permisos, encoding)
     3. La estructura de menúes
  2. Controla que las operaciones se hagan dentro del contexto de una transacción sql
  3. Está basado en grillas editables (ordenables y filtrables), para editar en formato XLSX; con jerarquías maestro detalle
  4. Tiene anotaciones de tipos para poder usar desde Typescript
  5. Genera los .sql para crear las tablas en la base de datos antes de la instalación
  
