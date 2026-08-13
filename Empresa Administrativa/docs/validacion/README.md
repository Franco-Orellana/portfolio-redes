🏠 [Volver al inicio](../../README.md#-índice-de-documentación)

# Plan de validación

Con el propósito de validar el cumplimiento de los requisitos funcionales definidos para la infraestructura, se estableció un conjunto de pruebas orientadas a verificar el funcionamiento de los principales servicios de red, las políticas de seguridad implementadas y la conectividad entre los distintos segmentos.

La siguiente tabla presenta las pruebas realizadas y los requisitos funcionales que cada una permite verificar.

| Código | Prueba | Descripción | Requisito(s) verificado(s) | Resultado |
|--|--|--|--|--|
| PV-01 | Asignación automática de direcciones IP (DHCP) | Verifica que los equipos obtengan automáticamente una dirección IP, máscara de subred y puerta de enlace correspondientes a su VLAN. | **RF-06** | ✅ Correcto |
| PV-02 | Segmentación y aislamiento entre VLAN | Comprueba que los departamentos de Administración, Ventas e IT se encuentren separados mediante VLAN y que cada equipo pertenezca al segmento de red correspondiente. | **RF-02** | ✅ Correcto |
| PV-03 | Restricción de acceso desde Ventas | Verifica que las ACL impidan el acceso desde la VLAN de Ventas hacia las VLAN de Administración y Tecnología, conforme a la política de seguridad establecida. | **RF-03** | ✅ Correcto |
| PV-04 | Restricción de acceso desde Administración | Verifica que las ACL impidan el acceso desde la VLAN de Administración hacia las VLAN de Ventas y Tecnología, conforme a la política de seguridad establecida. | **RF-04** | ✅ Correcto |
| PV-05 | Acceso del departamento de IT a los segmentos internos | Comprueba que los equipos del departamento de IT puedan acceder a los segmentos de Administración y Ventas para realizar tareas de administración y soporte. | **RF-05** | ✅ Correcto |
| PV-06 | Acceso a Internet desde las VLAN internas | Verifica que los usuarios de Administración, Ventas e IT puedan acceder a Internet mediante la infraestructura de enrutamiento y la traducción de direcciones (NAT/PAT). | **RF-01** | ❌ No hay prueba. Ver **Nota al final**. |
| PV-07 | Incorporación de nuevos usuarios y servicios | Verifica que la infraestructura permita incorporar nuevos usuarios, departamentos o servicios sin afectar el funcionamiento de los segmentos y servicios existentes. | **RF-07** | ⚠️ Se cumple por diseño, pero no se verifica. |


> **Nota**: El requisito RF-01 no fue validado mediante una prueba de conectividad directa debido a que la simulación no cuenta con un dispositivo externo o una red ISP que permita comprobar el acceso hacia Internet. No obstante, su cumplimiento se considera contemplado dentro del diseño de la infraestructura mediante la configuración de la ruta por defecto hacia la red externa y la implementación de NAT/PAT en el router perimetral R-EDGE-01. La correcta validación de la conectividad interna, el funcionamiento del enrutamiento inter-VLAN y la configuración de la traducción de direcciones permiten confirmar que la infraestructura se encuentra preparada para proporcionar acceso externo una vez conectado el enlace WAN correspondiente.

<br>

# Verificación de la infraestructura

Los siguientes apartados contienen las pruebas realizadas para verificar el funcionamiento de los servicios implementados, la conectividad entre VLAN y las políticas de seguridad configuradas.

* [PV-01 - Asignación automática de direcciones IP (DHCP)](./PV-01-asignacion-DHCP.md)
* [PV-02 - Segmentación y aislamiento entre VLAN](./PV-02-segmentacion-vlan.md)
* [PV-03 - Restricción de acceso desde Ventas](./PV-03-restriccion-vlan-ventas.md)
* [PV-04 - Restricción de acceso desde Administración](./PV-04-restriccion-vlan-admin.md)
* [PV-05 - Acceso del departamento de IT a los segmentos internos](./PV-05-acceso-it.md) 


<br>
<br> 

⬅️ Anterior: [***Secuencia de configuración Cisco IOS***](../implementacion/config-cisco-ios.md)

➡️ Siguiente: [***Verificación de la configuración implementada en R-EDGE-01***](../anexos/verificacion-R-EDGE-01.md)