# Red Empresarial con Servicios de Seguridad y Administración

## 📄 Resumen

La infraestructura de red propuesta corresponde a una red empresarial de pequeña escala diseñada con criterios de segmentación, seguridad y administración centralizada. La topología se compone de un router perimetral encargado de proporcionar conectividad con el proveedor de servicios de Internet (ISP), además de realizar la traducción de direcciones mediante NAT/PAT para permitir el acceso a Internet de los equipos de la red interna.

El router se conecta a un switch de Capa 3, el cual constituye el núcleo de la red y es responsable del enrutamiento entre VLAN mediante interfaces virtuales (SVI). La segmentación lógica contempla cinco VLAN: una destinada al departamento de Finanzas, otra al departamento de Recursos Humanos, una tercera para el departamento de Tecnología (IT), una VLAN dedicada a la administración de la infraestructura de red y una VLAN nativa configurada con un identificador distinto al valor predeterminado, con el objetivo de reforzar la seguridad de los enlaces troncales.

Desde el switch de Capa 3 se establecen conexiones hacia switches de Capa 2 que proporcionan acceso a los dispositivos finales. Los departamentos de Finanzas, Recursos Humanos y Tecnología disponen de estaciones de trabajo conectadas a sus respectivas VLAN, mientras que un switch de acceso adicional aloja los servidores de infraestructura, entre ellos un servidor RADIUS para la autenticación centralizada de administradores, y un servidor Syslog destinado a la recopilación y almacenamiento centralizado de los registros generados por los dispositivos de red.

Como parte de las medidas de seguridad implementadas, la administración remota de los equipos de interconexión se realiza exclusivamente mediante el protocolo SSH, garantizando la confidencialidad e integridad de las sesiones de administración. La combinación de segmentación por VLAN, enrutamiento inter-VLAN, autenticación centralizada, registro de eventos y acceso remoto seguro proporciona una infraestructura organizada, escalable y alineada con las buenas prácticas de administración y seguridad en redes empresariales.


---------


## 🚧 EN PROCESO

⚠️ **Este proyecto se encuentra actualmente en etapa de desarrollo.**  
Se están realizando configuraciones, pruebas y ajustes de seguridad antes de su implementación final.