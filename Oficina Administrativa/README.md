# Empresa administrativa
 
## 📄 Resumen

Este proyecto presenta el diseño e implementación de una infraestructura de red para una pequeña empresa administrativa, con el propósito de proporcionar una conectividad segura, eficiente y fácil de administrar entre sus diferentes departamentos. La solución fue diseñada para satisfacer las necesidades actuales de la organización y permitir futuras ampliaciones sin requerir cambios significativos en la arquitectura de red.

La infraestructura se basa en la segmentación lógica mediante VLANs, separando los departamentos de Administración, Ventas e IT para mejorar la seguridad, optimizar el rendimiento de la red y facilitar su administración. La comunicación entre las distintas VLANs se realiza mediante la técnica Router-on-a-Stick, utilizando un enlace troncal entre el switch de acceso (SW-ACC-01) y el router perimetral (R-EDGE-01).

Asimismo, el router perimetral proporciona el servicio DHCP, automatizando la asignación de direcciones IP para cada segmento de red, y se implementa NAT/PAT para permitir que todos los equipos accedan a Internet utilizando una única dirección IP pública.

Como parte de las políticas de seguridad, se aplican Listas de Control de Acceso (ACLs) que restringen el acceso del departamento de Ventas hacia Administración, mientras que el departamento de IT dispone de acceso completo a todas las redes para realizar tareas de administración y soporte.

Una vez finalizada la implementación de la red, se realizaron distintas pruebas para verificar el correcto funcionamiento de la infraestructura y comprobar el cumplimiento de los requerimientos establecidos por el cliente.


------------------


## 📚 Índice de documentación

### Requerimientos

* [Requerimientos funcionales](./docs/requerimientos/requerimientos.md)

### Diseño de la red

* [Arquitectura de la red](./docs/diseño/01-arquitectura-red.md)
* [Diseño de VLAN](./docs/diseño/02-VLAN.md)
* [Diseño de direccionamiento IP](./docs/diseño/03-direccionamiento-IP.md)
* [Diseño de servicio DHCP](./docs/diseño/04-DHCP.md)
* [Diseño de enrutamiento](./docs/diseño/05-enrutamiento.md) 
* [Diseño de seguridad](./docs/diseño/06-seguridad.md) 

### Implementación

* [Secuencia de configuración Cisco IOS](./docs/implementacion/config-cisco-ios.md)

### Validación

* [Pruebas de funcionamiento](./docs/validacion/README.md)

### Anexos
 
* [Verificación de la configuración implementada en R-EDGE-01](./docs/anexos/verificacion-R-EDGE-01.md)
* [Verificación de la configuración implementada en SW-ACC-01](./docs/anexos/verificacion-SW-ACC-01.md)


------------------


## 📁 Organización del repositorio

```text
configuraciones/
├── router/
└── switch/ 

diagramas/
├── fisico/
└── logico/ 

docs/ 
├── anexos/
├── diseño/
├── implementacion/
├── validacion/
└── requerimientos/ 

packet-tracer/ 
screenshots/

verificaciones/
├── router/
└── switch/
```


------------------


## 📂 Recursos del proyecto

* **Configuraciones Cisco:** carpeta `configuraciones/`
* **Diagramas:** carpeta `diagramas/`
* **Documentación:** carpeta `docs/`
* **Proyecto Packet Tracer:** carpeta `packet-tracer/`
* **Capturas y evidencias:** carpeta `screenshots/`
* **Comprobación de configuraciones:** carpeta `verificaciones/`


------------------


## ⚙️ Tecnologías utilizadas

* Cisco IOS
* Cisco Packet Tracer 


------------------


## ℹ️ Acerca de

Este repositorio tiene como finalidad la documentación técnica.