# 32- Logs & Profiling

### 1- Incorporar al proyecto de servidor de trabajo la compresión gzip.

- instalat gzip

```
>npm i compression
```

- inspeccionar en navegador rutas /info vs /info-gzip

### 2- Implementar loggueo

```
>npm i winston
```

- ver archivo de configuracion en utils/logger.js

# PERFORMANCE

- Levantar servidor con --prof

```
>node --prof server.js
```

- análisis con artillery

```
>artillery quick --count 5 --num 10 --output resultados.txt http://localhost:3000/info
```

- Comparar performance en ambos casos . con y sin console.log(info)
- Pasar log de profiler a txt

```
> node --prof-process  isolate-0x5911610-66286-v8.log > result-prof-debug.txt
```

### Autocannon -> Misma funcionalidad que Artillery

- levantar servidor

```
>node --prof server.js
```

- correr análisis con autocannon (muy pareccido a artillery):

```
>autocannon -d 5 -c 10 "http://localhost:3000/info"
```

### 0x . Gráfico de flama (ohhh 🔥🔥🔥)

- Levantar server con 0x

```
>0x server.js
```

- Correr análisis con autocannon o artillery

```
>autocannon -d 5 -c 10 "http://localhost:3000/info"
```
