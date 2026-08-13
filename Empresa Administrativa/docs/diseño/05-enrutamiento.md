🏠 [Volver al inicio](../../README.md#-índice-de-documentación)

# Diseño de enrutamiento

El enrutamiento de la infraestructura se centralizó en el router perimetral R-EDGE-01, el cual desempeña dos funciones principales: proporcionar el enrutamiento inter-VLAN entre las redes internas y actuar como puerta de enlace hacia redes externas mediante el enlace WAN.

Para implementar el enrutamiento inter-VLAN, se utilizó la técnica Router-on-a-Stick, configurando subinterfaces sobre la interfaz física conectada al switch de acceso SW-ACC-01 mediante un enlace troncal IEEE 802.1Q. Cada subinterfaz se asoció a una VLAN específica y se configuró con una dirección IP que funciona como puerta de enlace predeterminada para los dispositivos pertenecientes a esa red.

Las subinterfaces configuradas fueron las siguientes:

| Subinterfaz | VLAN | Red | Dirección IP (Gateway) | Función | 
|:--:|:--:|:--:|:--:|:--:|
| GigabitEthernet0/0.10 | 10 | 192.168.10.0/24 | 192.168.10.1 | Puerta de enlace para la red del área administrativa. | 
| GigabitEthernet0/0.20 | 20 | 192.168.20.0/24 | 192.168.20.1 | Puerta de enlace para la red del área de ventas. | 
| GigabitEthernet0/0.30 | 30 | 192.168.30.0/24 | 192.168.30.1 | Puerta de enlace para la red del área de tecnología. | 


Esta configuración permite que los equipos ubicados en diferentes VLAN puedan intercambiar información de manera controlada, manteniendo la segmentación lógica de la red y reduciendo los dominios de difusión. El router recibe las tramas etiquetadas desde el switch, identifica la VLAN correspondiente mediante el protocolo IEEE 802.1Q y realiza el enrutamiento entre las distintas redes cuando el tráfico así lo requiere.

Para el acceso a redes externas, se implementó un esquema de enrutamiento estático, seleccionado debido a la simplicidad de la topología y a la existencia de un único enlace de salida hacia el proveedor de servicios de Internet (ISP). En este escenario no resulta necesario emplear protocolos de enrutamiento dinámico, ya que únicamente existe una ruta disponible para alcanzar redes externas.

Con este propósito, se configuró una ruta estática por defecto (0.0.0.0/0), la cual redirige todo el tráfico cuyo destino no pertenece a las redes internas hacia el siguiente salto correspondiente al ISP simulado (200.1.1.1). De esta forma, cualquier paquete destinado a redes externas es enviado automáticamente a través del enlace WAN.


### Tabla resumen

| Elemento de diseño | Implementación | 
|--|--|
| Dispositivo de Capa 3 | Router perimetral R-EDGE-01 | 
| Función principal | Enrutamiento inter-VLAN y comunicación con redes externas | 
| Método de enrutamiento interno | Router-on-a-Stick mediante subinterfaces IEEE 802.1Q | 
| Segmentos internos gestionados | VLAN 10 (ADMIN), VLAN 20 (VEN) y VLAN 30 (IT) | 
| Subinterfaces configuradas | G0/0.10, G0/0.20 y G0/0.30 | 
| Puertas de enlace | 192.168.10.1, 192.168.20.1 y 192.168.30.1 | 
| Método de salida externa | Ruta estática por defecto | 
| Red de destino externa | 0.0.0.0/0 | 
| Próximo salto | 200.1.1.1 (ISP simulado) | 
| Administración de rutas | Configuración manual |  

<br>
<br> 

⬅️ Anterior: [***Diseño de servicio DHCP***](./04-DHCP.md)

➡️ Siguiente: [***Diseño de seguridad***](./06-seguridad.md)