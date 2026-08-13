🏠 [Volver al inicio](../../README.md#-índice-de-documentación)

# Servicio DHCP

Con el objetivo de automatizar la asignación de direcciones IP a los equipos de la red, se implementó el servicio DHCP (Dynamic Host Configuration Protocol) en el router R-EDGE-01, el cual actúa como servidor DHCP para todas las VLAN de usuarios.

Se configuró un pool DHCP para cada VLAN. Cada pool contiene la información necesaria para que los clientes obtengan automáticamente una dirección IP válida, junto con los parámetros de red correspondientes.


| Pool DHCP | VLAN | Red | Máscara | Gateway | Rango excluido | Rango asignable | 
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| DHCP-ADMIN | 10 | 192.168.10.0 | 255.255.255.0 | .1 | .1 - .20 | .21 - .254 | 
| DHCP-VEN | 20 | 192.168.20.0 | 255.255.255.0 | .1 | .1 - .20 | .21 - .254 |
| DHCP-IT | 30 | 192.168.30.0 | 255.255.255.0 | .1 | .1 - 20 | .21 - .254 |

> Nota: Las direcciones abreviadas corresponden al último octeto de la red indicada.

<br>
<br> 

⬅️ Anterior: [***Diseño de direccionamiento IP***](./direccionamiento-IP.md)

➡️ Siguiente: [***Diseño de enrutamiento***](./enrutamiento.md)