🏠 [Volver al inicio](../../README.md#-índice-de-documentación)

# Diseño de direccionamiento IP

El esquema de direccionamiento se diseñó asignando una subred IPv4 exclusiva a cada VLAN, utilizando una máscara /24 (255.255.255.0). Esta estrategia permite mantener independencia entre los segmentos de red y simplifica las tareas de administración, identificación y resolución de incidencias.

En todas las subredes se adoptó un criterio uniforme de asignación de direcciones:

* La primera dirección utilizable se reserva como puerta de enlace predeterminada (Default Gateway).
* Un bloque inicial de direcciones se destina a dispositivos con direccionamiento estático, tales como equipos de infraestructura, servidores, impresoras y elementos de gestión.
* El resto de las direcciones se asigna dinámicamente mediante el servicio DHCP a los equipos cliente.

Este esquema estandarizado reduce la complejidad operativa, facilita la administración del direccionamiento y permite mantener un crecimiento ordenado de la infraestructura.

Finalmente, el diseño contempla la implementación de una VLAN nativa dedicada para los enlaces troncales entre los dispositivos de la infraestructura. Al estar destinada exclusivamente al tráfico nativo de los enlaces troncales, esta VLAN no se utiliza para usuarios ni para la prestación de servicios, por lo que no requiere gateway, direccionamiento para hosts ni servicio DHCP.
 
### Tabla resumen

| VLAN | Nombre | Uso | Red | Máscara | Gateway | Reservadas | Asignables | Broadcast | 
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| 10 | ADMIN | Usuarios | 192.168.10.0/24 | 255.255.255.0 | .1 | .2 - .20 | .21 - .254 | .255 |
| 20 | VEN | Usuarios | 192.168.20.0/24 | 255.255.255.0 | .1 | .2 - .20 | .21 - .254 | .255 |
| 30 | IT | Usuarios | 192.168.30.0/24 | 255.255.255.0 | .1 | .2 - .20 | .21 - .254 | .255 |
| 999 | NATIVE | Nativa |  192.168.254.0/24 | 255.255.255.0 | No aplica | No aplica | No aplica | .255 |   

> Nota: Las direcciones abreviadas corresponden al último octeto de la red indicada.

<br>
<br> 

⬅️ Anterior: [***Diseño de VLAN***](./VLAN.md)

➡️ Siguiente: [***Diseño de servicio DHCP***](./DHCP.md)