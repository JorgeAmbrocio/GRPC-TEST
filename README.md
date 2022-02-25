# GRPC-TEST
Creación de microservicios para simular un servicio de crowdsourcing de comida a domicilio.

# Tecnologías a utilizar
- GRPC
- GOLANG

# Descripción simple de servicios
- Cliente
    - Solicitar pedido al restaurante
    - Verificar estado del pedido al restaurante
     Verificar estado del pedido al repartidor
- Restaurante
    - Recibir pedido del cliente
    - Informar estado del pedido al cliente
    - Avisar al repartidor que ya está listo el pedido
- Repartidor
    - Recibir pedido del restaurante
    - Informar estado del pedido al cliente
    - Marcar como entregado

[Lectura del archivo proto](./notasnoob/ExplicacionProto.md)
[Comandos para transpilar e instalar módulo generado](./notasnoob//Comandos.md)