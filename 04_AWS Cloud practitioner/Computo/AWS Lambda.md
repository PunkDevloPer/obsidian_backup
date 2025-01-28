Lambda es un servicio de computación sin servidor proporcionado por Amazon Web Services (AWS). Permite ejecutar código sin servidores. En lugar de tener que configurar la infraestructura para ejecutar tu aplicación, puedes simplemente cargar tu código a Lambda y dejar que AWS se encargue del resto. es importante mencionar que el tiempo de ejecución máximo de lambda es de 15 minutos por consulta.

Algunas características:

### [[Computación sin Servidor]]

AWS Lambda sigue una arquitectura sin servidor, lo que permite a los desarrolladores centrarse en escribir código sin la necesidad de gestionar la infraestructura subyacente. Los usuarios cargan su código y Lambda maneja automáticamente la ejecución, escalado y mantenimiento de recursos.

### [[Ejecución Basada en Eventos]]

Las funciones de Lambda son desencadenadas por varios servicios o eventos de AWS. Los desencadenadores pueden ser eventos de servicios como Amazon S3, Amazon DynamoDB, Amazon API Gateway, AWS CloudWatch, y más. Cuando se produce un desencadenador, Lambda ejecuta la función asociada.

### [[Modelo de Pago por Uso]]

AWS Lambda opera bajo un modelo de precios de pago por uso. Los usuarios son cobrados en función del número de solicitudes para sus funciones y el tiempo que su código se ejecuta. No hay cargos cuando el código no está en ejecución.

### [[Lenguajes Admitidos]]

Lambda admite varios lenguajes de programación como Node.js, Python, Java, Ruby, Go, .NET Core y runtimes personalizados utilizando imágenes de contenedor.

### [[Beneficios]]

- **Escalabilidad:** Las funciones se escalan automáticamente en respuesta al tráfico entrante o eventos.
- **Administración Cero:** No es necesario aprovisionar o gestionar servidores.
- **Eficiencia de Costos:** Paga solo por el tiempo de computación consumido por su código.
- **Flexibilidad:** Admite una variedad de lenguajes de programación.
- **Integración:** Se integra sin problemas con otros servicios de AWS.

### [[Casos de Uso]]

- **Procesamiento de Archivos en Tiempo Real:** Procesar archivos cargados en Amazon S3.
- **Backend Basado en Eventos:** Responder a eventos de Amazon DynamoDB, SNS o IoT.
- **Backend de API:** Construir APIs sin servidor con API Gateway.
- **Procesamiento de Datos:** Manejar tareas de transformación y procesamiento de datos.
- **Tareas Programadas:** Ejecutar código en un horario utilizando CloudWatch Events.