# Comandos para compilación

Comando para transpilar archivo .proto
Este comando generará archivos .go que colocaremos en el reposotorio de la ruta indicada en la opción de opcoines del archivo proto. 
````bash
protoc --go_out=. --go_opt=paths=source_relative --go-grpc_out=. --go-grpc_opt=paths=source_relative cliente.proto
````
- **--go_out** indica la carpeta en la que se generarán los archivos transpilados
- **--go_opt** indica las opciones con las que se ejecutará la transpilación
    - **paths** indica el tipo de rutas que se utilizarán
        - **source_relative** indica que todo se ejecutará en la carpeta actual
- **--go_grpc_out** indica la carpeta de en la que se generarán los archivos transpilados a igual que el parámetro **go_out**
- **--go_grp_opt** indica las opciones con las que se ejecutará la transpilación al igual que el parámetro **go_opt**
    - **paths** indica el tipo de rutas que se utilizarán
        - **source_relative** indica que todo se ejecutará en la carpeta actual
- **archivo.proto** archivo con la definición proto que se utilizará como base para la transpilación.

# Crear tag
Al tener los archivos generados en el repositorio, debemos crear un tag release para tener como base al momento de obtener nuestro proyecto.

# Descargar el transpilado como módulo de go
````bash
go get github.com/JorgeAmbrocio/GRPC-TEST/ProtoCliente
````

# Instalar módulo de go en proyecto final
En el proyecto en el que implementaremos la transpilación de proto a golang debemos iniciar los módulos.
````bash
go mod init
````
Luego debemos instalar todas las dependencias para nuestro proyecto.
````bash
go mod tidy
````