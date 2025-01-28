- **Inicio de Conexión**: Cuando un dispositivo quiere iniciar una conexión con otro dispositivo, envía un paquete con la bandera SYN (synchronize). Este paquete es parte del proceso de "three-way handshake" (apretón de manos de tres vías) que establece una conexión TCP.
    
- **Three-Way Handshake**:
    
    - **SYN**: El primer dispositivo (cliente) envía un paquete SYN al servidor para iniciar la conexión.
    - **SYN-ACK**: El servidor responde con un paquete que tiene las banderas SYN y ACK (acknowledgment) activadas, indicando que ha recibido el paquete SYN y está dispuesto a establecer la conexión.
    - **ACK**: Finalmente, el cliente envía un paquete con la bandera ACK activada para confirmar que ha recibido el paquete SYN-ACK del servidor.
- **Establecimiento de Conexión**: Una vez que estos tres pasos se han completado, la conexión TCP está establecida, y los dos dispositivos pueden comenzar a intercambiar datos.