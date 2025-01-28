1. **Inicio de la Conexión**: El escáner envía un paquete SYN (synchronize) a un puerto específico en el sistema de destino. Este paquete es una solicitud para iniciar una conexión TCP, siguiendo el proceso del "three-way handshake".
    
2. **Respuesta del Sistema de Destino**:
    
    - **Puerto Abierto**: Si el puerto está abierto y aceptando conexiones, el sistema de destino responderá con un paquete SYN-ACK (synchronize-acknowledge). Esto indica que el puerto está dispuesto a establecer una conexión. El escáner, a continuación, completa el "three-way handshake" enviando un paquete ACK (acknowledge), estableciendo así una conexión completa.
    - **Puerto Cerrado**: Si el puerto está cerrado, el sistema de destino responderá con un paquete RST (reset). Esto indica que no hay servicio escuchando en ese puerto y que la conexión no se puede establecer.
3. **Cierre de la Conexión**: En un escaneo TCP Connect, el escáner completa la conexión enviando un paquete FIN (finish) para cerrar la conexión después de recibir la respuesta del sistema de destino. Esto asegura que la conexión se cierre correctamente y que no queden conexiones abiertas innecesarias.
    

### Características del Escaneo TCP Connect

- **Completo y Preciso**: Dado que el escaneo TCP Connect establece una conexión real, proporciona información precisa sobre qué puertos están abiertos y aceptan conexiones.
    
- **Detección de Firewall/IDS**: Este tipo de escaneo puede ser fácilmente detectado por sistemas de detección de intrusiones (IDS) o firewalls, ya que genera tráfico TCP completo y estableciendo conexiones, lo que puede alertar a los administradores de red sobre posibles actividades de escaneo.
    
- **Lento y Evidente**: Debido a que establece conexiones reales, el escaneo TCP Connect puede ser más lento y menos discreto que otros métodos de escaneo, como el escaneo SYN (también conocido como escaneo "half-open").
    
- **Uso en Auditorías**: Es comúnmente utilizado en auditorías de seguridad y pruebas de penetración para mapear redes y descubrir puertos abiertos en sistemas objetivo.



