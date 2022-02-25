# Lectura línea a líena del archivo proto utilizado

Indicamos que usaremos la sintaxis del lenguaje proto en su versión tres.
También indicamos que nuestro paquete contenedor para solución es grpc.
````protobuf 
syntax = "proto3";
package grpc;
````
Para utilizar el transpilado que resulta de nuestro archivo proto necesitamos colocarlo en un sitio accesible para instalarlo como móulo en nuestra aplicación GO.
En éste ejemplo publicamos el código en repositorio indicado por la ruta de abajo.
```protobuf
option go_package = "github.com/JorgeAmbrocio/GRPC-TEST/ProtoCliente";
```

Los bloques **message** son el equivalente a los modelos en un lengaje robusto. En éstos se describe la estructura que tendrán los mensajes request y response. Se pueden anidar las estructuras.
En el ejemplo actual el mensaje **PedidoRequest** crea una lista del tipo mensaje **Descripcion**. 
````protobuf
message Descripcion {
    int32 idProducto = 1;
    string descripcion = 2;
    int32 cantidad = 3;
};

message PedidoRequest {
    repeated Descripcion descripciones = 1;
};

message idPedido {
    int32 id = 1;
}
````

Un servicio es el equivalente de un controllador en dot net. Para describir las funciones que vamos a implementar como "endpoints" lo haremos indicado el nombre de la función, entre paréntesis el tipo del mensaje request que solicitamos como input y por último en el **return** necesitamos indicar el tipo de mensaje response con el que responderemos en la función.
````protobuf
service PedidosService {
    rpc PostPedido(PedidoRequest) returns (Pedido);
    rpc GetRepartidor(idPedido) returns (Pedido);
    rpc GetRestaurante(idPedido) returns (Pedido);
}
````

Nota: Si nuestra función recibirá únicamente parámetros por query, también se debe crear un mensaje indicando el tipo y el nombre del mismo. Como **idPedido** en el ejemplo.