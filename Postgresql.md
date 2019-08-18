# Comandos De Postgres

### Crear una base de datos
    CREATE DATABASE practica;

### Creamos la tabla usuarios
    create table usuarios (
        nombre varchar(30),
        clave varchar(10)
    );

### Mostramos la estructura de la tabla usuarios
    select *
    from information_schema.columns 
    where table_name = 'usuarios';
