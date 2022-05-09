## Pasos para levantar el proyecto

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

1-step - setup inicial del proyecto
2-step - check api key (middleware de verificación)
3-step - implement hash (scripts de hash y compare con bcrypt)
4-step - implementando hashing para usuarios
5-step - Implementando login con Passport.js
  https://www.npmjs.com/package/passport
  https://www.passportjs.org/packages/passport-local/
6-step - firmar y verificar token
  https://datatracker.ietf.org/doc/html/rfc7519#section-4
7-step - Generar JWT en el servicio
