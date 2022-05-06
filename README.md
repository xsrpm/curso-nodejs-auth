## Pasos para levantar el proyecto

### Crear carpeta mirror de base de datos en al raiz del proyecto:
mkdir postgres_data

### Iniciar contenedores
    docker-compose up -d postgres
    docker-compose up -d pgadmin

### Ingresar a pgadmin y conectar con el servidor de postgres
- Entrar a `pgadmin`(localhost:5050) 
- Iniciar sesión en pgadmin:
    - username: admin@mail.com
    - password: root

- Conectar con la base de datos de postgres

  - Object > Register > Server
  - General.Name: MySERVER
  - Connection.Host: postgres
  - Connection.Maintenance database: my_store
  - Connection.Username: nico
  - Connection.Password: admin123

### Realizar migraciones de tablas y data
    npm run migrations:run

### Levantar el proyecto en entorno de desarrollo
    npm run dev


https://api.escuelajs.co/docs/
