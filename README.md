# Desafío: Análisis completo de performance
### >> Consigna:

Realizar el análisis completo de performance del servidor con el que venimos trabajando.

Vamos a trabajar sobre la ruta './info', en modo fork, agregando ó extrayendo un console.log de la información colectada antes de devolverla al cliente. Además desactivaremos el child_process de la ruta '/randoms'

Para ambas condiciones (con o sin console.log) en la ruta '/info' OBTENER:

1) El perfilamiento del servidor, realizando el test con --prof de node.js. Analizar los resultados obtenidos luego de procesarlos con --prof-process.

Utilizaremos como test de carga Artillery en línea de comandos, emulando 50 conexiones concurrentes con 20 request por cada una. Extraer un reporte con los resultados en archivo de texto.

Luego utilizaremos Autocannon en línea de comandos, emulando 100 conexiones concurrentes realizadas en un tiempo de 20 segundos. Extraer un reporte con los resultados (puede ser un print screen de la consola)

2) El perfilamiento del servidor con el modo inspector de node.js --inspect. Revisar el tiempo de los procesos menos performantes sobre el archivo fuente de inspección.

3) El diagrama de flama con 0x, emulando la carga con Autocannon con los mismos parámetros anteriores.
Realizar un informe en formato pdf sobre las pruebas realizadas incluyendo los resultados de todos los test (texto e imágenes).

👉 Al final incluir la conclusión obtenida a partir del análisis de los datos.

# Resultado:

### 1)

(con y sin console.log)
```
node --prof src/server.js 8080
```

(con y sin console.log)
```
artillery quick -c 50 -n 20 "http://localhost:8080/info" > artillery_prof_fork.txt
```

(print screen consola, con y sin console.log)
```
autocannon -d 20 -c 100 "http://localhost:8080/info"
```
(con y sin console.log)
```
node --prof-process fork-v8.log > prof_fork.txt 
```

### 2)
(con y sin console.log)
```
node --inspect src/server.js 8080
```

(con y sin console.log)
```
artillery quick -c 50 -n 20 "http://localhost:8080/info" > artillery_inspect_fork.txt
```
(print screen consola, con y sin console.log)
```
autocannon -d 20 -c 100 "http://localhost:8080/info"
```

chrome://inspect (con y sin console.log)

### 3)
(print screen consola, con y sin console.log)
```
0x src/server.js 8080
autocannon -d 20 -c 100 "http://localhost:8080/info"
```
