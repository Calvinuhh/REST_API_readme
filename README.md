# Guia para arrancar el proyecto localmente

### Tecnologias implementadas:

`Node.js, React, Tailwind CSS, Express.js, MongoDB, Mongoose, JWT, Bcrypt, TypeScript, MailTrap, Nodemailer`

Repositorio de Frontend - https://github.com/Calvinuhh/REST_API_client

Repositorio de Backend - https://github.com/Calvinuhh/REST_API_server

La version de `Node` utilizada para la prueba es la version `22.12.0`, en caso de no contar con esa version se puede hacer uso de `Nvm` (Node Version Manager) para instalar la version correspondiente.

Este proyecto tiene separacion de **_Frontend y Backend_** por lo que se tendra que descargar ambos repositorios por separado.

Se recomienda tener a la mano las variables de entorno para trabajar con **_Mailtrap_**, que vendrian siendo las siguientes: `MAIL_HOST`, `MAIL_PORT`, `MAIL_USER` y `MAIL_PASSWORD` de **Mailtrap**.

Primeramente de descargaran los 2 repositorios en una carpeta que sera la carpeta raiz.

### Repositorio de Frontend:

```
git clone https://github.com/Calvinuhh/REST_API_client
```

### Repositorio de Backend:

```
git clone https://github.com/Calvinuhh/REST_API_server
```

Obtendremos 2 carpetas: **_REST_API_client_** y **_REST_API_server_**

La primera accion que se realizara sera instalar las dependencias de ambos proyectos, en cada carpeta se escribira el comando `npm install` para instalar las dependencias.

## REST_API_client

```powershell
cd REST_API_client
npm install
```

## REST_API_server

```powershell
cd REST_API_server
npm install
```

# Variables de entorno

Una vez instaladas las dependencias cambiaremos el archivo `.env.demo` a `.env` en ambas carpetas, tanto de **_REST_API_client_** como **_REST_API_server_**

Ahora bien ya cambiamos el nombre del archivo de las variables de entorno ahora la siguiente accion sera reemplazar las variables de entorno por las correspondientes, se mostrara a continuacion que variables de entorno contiene cada carpeta.

### REST_API_client

```powershell
VITE_SERVER_URL=(URL del Server)
```

### REST_API_server

```powershell
PORT=(Puerto del server)
SERVER_URL=(URL del client)
CLIENT_URL=(URL del server)

DB_URI=(URI de la base de datos de MongoDB)


JWT_SECRET=(Secreto para JWT)


MAIL_HOST=(Host de correo)
MAIL_PORT=(Port de correo)
MAIL_USER=(User de correo)
MAIL_PASSWORD=(Password de correo)
```

Reemplazar las variables de entorno con los valores necesarios para levantar los proyectos en desarrollo.

Tener en cuenta que en la variable de entorno `VITE_SERVER_URL` de **_REST_API_client_** hace referencia a la URL donde esta levantado el servidor, por lo que si por ejemlo el servidor es: `http://localhost:3000` ese sera el valor que se le asignara a la variable `VITE_SERVER_URL`.

El `SERVER_URL` hace referencia al la _URL_ del propio servidor.

Este proyecto utiliza un cluster de **_Mongo Atlas_**, por lo que la variable `DB_URI` debe hacer referencia al _string_ de conexion de la instancia del cluster de Mongo Atlas, en caso de no implementar un cluster de **_Mongo Atlas_** normalmente el valor de **_DB_URI_** seria el siguiente: `mongodb://localhost:27017/{db_name}` para realizar una conexion local con MongoDB

Si no funciona con _localhost_ se puede intentar con un string basado en una conexion **IPv4**

por ejemplo: `mongodb://127.0.0.1:27017/{db_name}`

Como se puede observar el **_ultimo_** parametro del string seria el nombre de como se quiera nombrar a la nueva base de datos.

Como se menciono anteriormente si no se quiere implementar **_Mongo Atlas_** se puede probar con una base de datos localmente y para esto se levantara el servidor de la base de datos de **Mongo** con el siguiente comando:

```powershell
mongod
```

Una vez levantado el servidor de la base de datos, se procedera a levantar el servidor del proyecto.

## REST_API_server

Para esto en la carpeta devtree_server se implementara el comando `npm run`:

```powershell
  start
    node dist/index.js
available via `npm run-script`:
  dev
    nodemon src/index.ts
  build
    tsc
```

Al implementar el comando `npm run dev` en la consola se mostraran unas alertas como estas:

```powershell
> server@1.0.0 dev
> nodemon src/index.ts

[nodemon] 3.1.9
[nodemon] to restart at any time, enter `rs`
[nodemon] watching path(s): *.*
[nodemon] watching extensions: ts,json
[nodemon] starting `ts-node src/index.ts`
Conexión exitosa a la base de datos
Servidor escuchando en el puerto 3000, node version: 22.12
```

Una vez el servidor levantado en la carpeta de **_REST_API_client_** levantaremos el proyecto del _frontend_

## REST_API_client

```powershell
npm run dev
```

```powershell
> client@0.0.0 dev
> vite


  VITE v6.0.3  ready in 408 ms

  ➜  Local:   http://localhost:5173/
  ➜  Network: use --host to expose
  ➜  press h + enter to show help
```

Con el servidor y el cliente levantados y si reemplazamos las variables de entorno correctamente podremos ver el proyecto funcionando en la _URL_ del Front.
