🏠 [Volver al inicio](../../README.md#-índice-de-documentación)

# Diseño de VLAN

La arquitectura de la red fue segmentada mediante VLAN (Virtual Local Area Networks) con el propósito de establecer dominios de broadcast independientes y separar lógicamente el tráfico de cada área funcional de la organización. Esta segmentación mejora la seguridad, optimiza el rendimiento de la red y simplifica la administración de las políticas de comunicación entre departamentos.

Adicionalmente, se implementa una VLAN nativa independiente para el enlace troncal entre dispositivos de red, evitando el uso de la VLAN 1 predeterminada y aplicando una medida adicional de seguridad en la comunicación entre equipos.

La distribución de VLAN definida es la siguiente:

| VLAN | Nombre | Propósito | 
|:--:|:--:|:--:|
| 10 | ADMIN | Segmento destinado a los equipos del departamento de Administración. | 
| 20 | VEN | Segmento destinado a los equipos del departamento de Ventas. | 
| 30 | IT | Segmento destinado a los equipos del departamento de Tecnología. | 
| 99 | NATIVE | VLAN utilizada como nativa en enlaces troncales, sin dispositivos finales asociados. |

<br>
<br> 

⬅️ Anterior: [***Arquitectura de la red***](./arquitectura-red.md)

➡️ Siguiente: [***Diseño de direccionamiento IP***](./direccionamiento-IP.md)