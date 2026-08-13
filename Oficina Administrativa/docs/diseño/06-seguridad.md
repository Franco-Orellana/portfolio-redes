🏠 [Volver al inicio](../../README.md#-índice-de-documentación)

# Diseño de seguridad

El diseño de seguridad de la infraestructura tiene como objetivo proteger la información y los recursos de la organización mediante la segmentación de la red y el control del acceso entre departamentos. Para ello, se implementó una estrategia basada en la separación lógica mediante VLAN, el control del tráfico a través de Listas de Control de Acceso (ACL) y la administración centralizada de las políticas de seguridad en el router perimetral R-EDGE-01.

Esta arquitectura permite que cada departamento acceda únicamente a los recursos necesarios para el desarrollo de sus actividades, reduciendo el riesgo de accesos no autorizados y facilitando la administración de la red.

## Segmentación de la red

Como primera medida de seguridad, la infraestructura se dividió en tres VLAN, asignando una red independiente a cada departamento de la organización.

| VLAN | Nombre | Departamento | Red |
|:--:|:--:|:--:|:--:|
|  10  | ADMIN | Administración | 192.168.10.0/24 |
|  20  | VEN | Ventas | 192.168.20.0/24 |
|  30  | IT | Tecnología | 192.168.30.0/24 |

La segmentación mediante VLAN permite aislar el tráfico de cada departamento, reducir los dominios de broadcast y evitar que los equipos pertenecientes a distintas áreas se comuniquen directamente a nivel de Capa 2.

Toda comunicación entre VLAN debe atravesar el router R-EDGE-01, donde se aplican las políticas de seguridad definidas mediante ACL. Este diseño cumple con el requisito RF-02, que establece la separación de los departamentos de Administración, Ventas y Tecnología.

## Política de acceso entre departamentos

Las políticas de acceso fueron definidas considerando las funciones que desempeña cada área dentro de la organización y el nivel de acceso requerido para el desarrollo de sus actividades.

El departamento de Administración procesa documentación, información financiera y otros recursos de carácter interno, por lo que constituye uno de los segmentos con mayor nivel de protección. En consecuencia, se restringe el acceso desde aquellos departamentos que no requieren interactuar con estos recursos.

Por su parte, el departamento de Ventas utiliza únicamente los recursos propios de su área y los servicios externos necesarios para su operación, sin necesidad de acceder a la información administrativa.

Finalmente, el departamento de Tecnología es responsable de la administración, mantenimiento y soporte de toda la infraestructura, motivo por el cual dispone de acceso a todos los segmentos de la red.

La política de acceso definida es la siguiente:

### Acceso entre departamentos

| Origen | Destino | Acceso |
|:--:|:--:|:--:|
| Administración | Tecnología | ✗ Denegado |
| Administración | Ventas | ✗ Denegado |
| Ventas | Administración | ✗ Denegado |
| Ventas | Tecnología | ✗ Denegado |
| Tecnología | Administración | ✓ Permitido |
| Tecnología | Ventas | ✓ Permitido |

### Acceso a Internet

| Departamento | Acceso |
|:--:|:--:|
| Administración | ✓ Permitido |
| Ventas | ✓ Permitido |
| Tecnología | ✓ Permitido |


Las reglas anteriores permiten satisfacer los requisitos funcionales definidos para la infraestructura:

* Se mantiene el aislamiento lógico entre los departamentos mediante la segmentación de la red utilizando VLAN (RF-02).
* El personal del departamento de Ventas no pueden acceder a los recursos de los departamentos de Administración ni de Tecnología, garantizando la restricción de acceso establecida para este segmento (RF-03).
* El personal del departamento de Administración no pueden acceder a los recursos de los departamentos de Ventas ni de Tecnología, manteniendo las restricciones de comunicación definidas entre los distintos segmentos (RF-04).
* El personal de IT dispone de acceso a todos los segmentos de la red para realizar tareas de soporte, mantenimiento y administración (RF-05).
* Todos los departamentos conservan el acceso a Internet necesario para el desarrollo de sus actividades (RF-01).

<br>

> Nota: La implementación constituye una aproximación a una política stateful. Las ACL permiten tráfico TCP de retorno mediante la palabra clave established y tráfico ICMP de respuesta, permitiendo así que la VLAN IT pueda realizar tareas de administración sobre las VLAN ADMIN y VENTAS. Sin embargo, debido a que las ACL son stateless, no es posible garantizar que dichos paquetes correspondan exclusivamente a conexiones iniciadas por IT. Asimismo, la técnica established no proporciona seguimiento de sesiones UDP ni el comportamiento completo de un firewall stateful. Para cumplir estrictamente el requisito sería necesario implementar CBAC o Zone-Based Firewall.



## Administración centralizada de la seguridad

La aplicación de las políticas de seguridad se centralizó en el router R-EDGE-01, encargado del enrutamiento entre VLAN y de la ejecución de las ACL.

Centralizar estas funciones en un único dispositivo simplifica la administración de la infraestructura, facilita la incorporación de nuevas políticas de acceso y permite ampliar la red sin afectar el funcionamiento de los segmentos existentes, dando cumplimiento al requisito RF-06.

## Resumen del diseño de seguridad

| Elemento de diseño | Implementación |
|--|--| 
| Segmentación lógica | VLAN independientes para Administración, Ventas e IT |
| Método de aislamiento | Separación mediante VLAN y enrutamiento inter-VLAN |
| Control de acceso | ACL extendidas aplicadas en el router R-EDGE-01 |
| Protección de la información administrativa | Acceso denegado desde la VLAN de Ventas |
| Acceso de administración de red | IT posee acceso a todas las VLAN |
| Acceso a Internet | Habilitado para todos los departamentos mediante NAT/PAT |
| Punto de aplicación de políticas | Router perimetral R-EDGE-01 |
| Escalabilidad | Incorporación de nuevas VLAN y políticas de acceso sin modificar la arquitectura existente |


<br>
<br>


⬅️ Anterior: [***Diseño de enrutamiento***](./enrutamiento.md)

➡️ Siguiente: [***Secuencia de configuración Cisco IOS***](../implementacion/config-cisco-ios.md)