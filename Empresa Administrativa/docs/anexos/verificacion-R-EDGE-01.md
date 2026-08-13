🏠 [Volver al inicio](../../README.md#-índice-de-documentación)

# Verificación de la configuración implementada

## Configuración en ejecución

El siguiente archivo contienen la configuración activa obtenida mediante el comando `show running-config`, utilizada para verificar el estado final de los dispositivos.

- [Configuración en ejecución del router R-EDGE-01](../../verificaciones/router/R-EDGE-01-running-config.txt) 

  
## Estado de interfaces  
  
El siguiente archivo contiene la salida del comando `show ip interface brief` ejecutado en el router, donde se verifica el estado operativo de las interfaces y sus direcciones IP configuradas.  
  
- [Estado de interfaces del router R-EDGE-01](../../verificaciones/router/R-EDGE-01-show-ip-interface-brief.txt)  
  
  
## Tabla de enrutamiento  
  
El siguiente archivo contiene la salida del comando `show ip route` del router, donde se muestran las rutas conocidas por el dispositivo y la ruta por defecto configurada hacia la red WAN.  
  
- [Tabla de enrutamiento del router R-EDGE-01](../../verificaciones/router/R-EDGE-01-show-ip-route.txt)  


## Servicio DHCP

El siguiente archivo contiene la verificación del funcionamiento del servicio DHCP, realizada mediante los comandos de diagnóstico correspondientes. En él se muestran las asignaciones de direcciones IP realizadas por el servidor DHCP `show ip dhcp binding` y el estado de los grupos de direcciones configurados `show ip dhcp pool`.

- [Verificación de DHCP del router R-EDGE-01](../../verificaciones/router/R-EDGE-01-show-ip-dhcp.txt)
  
  
## Traducción de direcciones NAT  
  
El siguiente archivo contiene la verificación del funcionamiento de NAT/PAT mediante los comandos de diagnóstico correspondientes, mostrando las traducciones realizadas entre direcciones privadas y la dirección pública configurada.  
  
- [Verificación de NAT del router R-EDGE-01](../../verificaciones/router/R-EDGE-01-show-ip-nat.txt)


<br>
<br> 

⬅️ Anterior: [***Plan de validación***](../validacion/README.md)

➡️ Siguiente: [***Verificación de la configuración implementada en SW-ACC-01***](./verificacion-SW-ACC-01.md)