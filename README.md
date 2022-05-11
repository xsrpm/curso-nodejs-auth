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

## Pasos llevados a cabo en el desarrollo del proyecto
https://api.escuelajs.co/docs/

- 1-step - setup inicial del proyecto
- 2-step - check api key (middleware de verificación)
- 3-step - implement hash (scripts de hash y compare con bcrypt)
- 4-step - implementando hashing para usuarios
- 5-step - Implementando login con Passport.js
  https://www.npmjs.com/package/passport
  https://www.passportjs.org/packages/passport-local/
- 6-step - firmar y verificar token
  https://datatracker.ietf.org/doc/html/rfc7519#section-4
- 7-step - Generar JWT en el servicio
- 8-step - Protección de rutas - Status Code 401
- e2b35eb7703bd7a8549881c2b7c0ceac274590a8 - Control de roles - Status Code 403
- 9-step - Obteniendo data filtrada por rol
- 10-step - Como enviar emails en nodejs
- 11-step - Implementando el envío de emails

## Consideraciones para el frontend
Al hacer un login en la API nos da la información del usuario, pero también envían el token. Lo más importante es guardar el token porque debe enviarse en todas las peticiones.

En el cliente deberíamos tener un estado de login, es decir, una vez hecho un login exitoso se debería guardar un estado de sesión iniciada en el frontend.
Deberíamos guardar el estado (el token) en algún lugar, se recomienda una cookie. También se puede en LocalStorage, pero no es la mejor practica.
Cada vez que se envíe una petición (request) se debería enviar el token. Si se manejan librerías para hacer requests (ej. axios), hay formas de interceptar la petición y poner el token en el header.
El token debería tener una expiración, se recomienda que expire en 15-20 minutos, se puede implementar una técnica de refresh token. La API nos puede dar un access token y otro token aparte (refresh token) que nos servirá para generar un nuevo token cuando el access token ya expiró. Se recomienda estar haciendo requests continuamente para no salir de la sesión.
Se pueden validar permisos, con el token se puede preguntar al backend qué tipo de perfil es, aunque para más seguridad sería mejor hacer un request para obtener el perfil del usuario para no guardar nada en algún lugar.


## Envío de emails
Para el envío de emails se necesita 3 variables de entorno consultables en el archivo .env.example
El correo que envía los email debe estar registrado como usuario en la base de datos de postgres.
