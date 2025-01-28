### Proceso de un Escaneo UDP

1. **Envio de Paquetes UDP**: El escáner envía un paquete UDP a un puerto específico en el sistema de destino. Este paquete puede ser un datagrama UDP vacío o un datagrama con datos específicos diseñados para provocar una respuesta del servicio que se ejecuta en el puerto.
    
2. **Respuestas del Sistema de Destino**:
    
    - **Puerto Abierto**: Si el puerto UDP está abierto y hay un servicio escuchando en ese puerto, el sistema de destino puede no responder de inmediato, ya que UDP no tiene un mecanismo de confirmación de recepción. Sin embargo, algunos servicios UDP pueden responder con un mensaje específico o realizar alguna acción que indique que el puerto está en uso.
    - **Puerto Cerrado**: Si el puerto UDP está cerrado, el sistema de destino suele responder con un paquete ICMP (Internet Control Message Protocol) de tipo "Destination Unreachable" (Destino Inalcanzable) con el código "Port Unreachable" (Puerto Inalcanzable). Este mensaje indica que no hay servicio en ese puerto y que el paquete UDP no puede ser entregado.
    - **Filtrado**: Si el puerto UDP está filtrado por un firewall o un dispositivo de seguridad, el sistema de destino puede no responder en absoluto al paquete UDP, o puede enviar un mensaje ICMP de "Destination Unreachable" con el código "Administratively Prohibited" (Prohibido Administrativamente). Este caso puede hacer que el puerto aparezca como filtrado, ya que no hay respuesta clara sobre si está abierto o cerrado.
3. **Análisis de Respuestas**: El escáner analiza las respuestas recibidas (o la falta de ellas) para determinar el estado del puerto:
    
    - **Sin Respuesta**: La ausencia de una respuesta puede indicar que el puerto está abierto, filtrado, o que el servicio UDP está simplemente inactivo.
    - **Respuesta ICMP**: La recepción de un mensaje ICMP de "Port Unreachable" indica que el puerto está cerrado.