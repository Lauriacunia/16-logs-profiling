### 馃寛 Consigna 馃寛

#### 馃敟 1 - Pasar un par谩metro por consola que permita ejecutar al servidor en modo fork o cluster (crear un if en el codigo). De no pasarlo, el servidor iniciar谩 en modo fork.

- ver en punto 3)

- Linea 10 del archivo server.js

#### 馃敟 2 - Agregar en la vista info, el n煤mero de procesadores presentes en el servidor (con os).

```
import os from "os"; // es propia de node para obtener informacion del sistema
const nroCPUs = os.cpus().length;
```

#### 馃敟 3 - Ejecutar el servidor (modos FORK y CLUSTER) con nodemon verificando el n煤mero de procesos tomados por node. (en el package json)

```
 "cluster": "MODO='cluster' nodemon server.js",
 "fork": "MODO='fork' nodemon server.js"
```

#### 馃敟 4 - Ejecutar el servidor (con los par谩metros adecuados) utilizando Forever, verificando su correcta operaci贸n. Listar los procesos por Forever y por sistema operativo 馃挬

#### 馃敟 5 - Ejecutar el servidor (con los par谩metros adecuados: modo FORK) utilizando PM2 en sus modos modo fork y cluster. Listar los procesos por PM2 y por sistema operativo.

- modo fork. No envio PORT asi que toma el default

```
> pm2 start server.js  --name="serverFork" --watch
```

- modo cluster. Con 4 cpus de las disponibles

```
> pm2 start server.js --name="serverCluster" --watch -i 4

```

> pm2 list

#### 馃敟 6 - Tanto en Forever como en PM2 permitir el modo escucha, para que la actualizaci贸n del c贸digo del servidor se vea reflejado inmediatamente en todos los procesos.

> --watch

#### 馃敟 7 - Hacer pruebas de finalizaci贸n de procesos fork y cluster en los casos que corresponda.

> pm2 stop all
> pm2 delete all

### Configurar NGINX

#### 馃敟 8 - Redirigir todas las consultas a /api/randoms a un cluster de servidores escuchando en el puerto 8081. El cluster ser谩 creado desde node utilizando el m贸dulo nativo cluster. El resto de las consultas, redirigirlas a un servidor individual escuchando en el puerto 8080.

#### 馃敟 9 - Luego, modificar la configuraci贸n para que todas las consultas a /api/randoms sean redirigidas a un cluster de servidores gestionado desde nginx, reparti茅ndolas equitativamente entre 4 instancias escuchando en los puertos 8082, 8083, 8084 y 8085 respectivamente.

- Tomo prestado el archivo de configuraci贸n de Leandro Wagner. Ver en carpeta

### Incluir en la entrega:

- Archivo de configuraci贸n de NGINX
- Documentaci贸n con los comandos a ejecutar en la terminal.
