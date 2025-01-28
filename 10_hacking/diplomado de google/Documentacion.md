nos pidieron crear una base de datos para una tienda.
lo primero que debemos hacer es la consulta para crear una base de datos usando sql
primero 

   ```sql
  CREATE database tienda_pepito;
   ```

Luego tenemos que crear el diagrama de las tablas 
![[Pasted image 20231220124751.png]]
Agregamos las tablas y empezamos a crear las tablas de acuerdo al diagrama.
primero la tabla clientes
```sql
CREATE TABLE clientes(
N°_cliente INT AUTO_INCREMENT PRIMARY KEY,
nombre VARCHAR(60),
correo VARCHAR(60),
NIE VARCHAR(9),
direccion VARCHAR(200)
);
```

en este caso la clave primaria es N°_cliente, esto es importante por que va a ser nuestra llave primaria la que va a estar relacionada con las otras tablas.
ahora creamos la tabla productos.
```sql
CREATE TABLE productos(
id INT,
nombre VARCHAR(45),
precio DECIMAL(5,2),
categoria VARCHAR(45),
descripcion TEXT(1000),
stock INT,
favorito BIT
);
```
ahora la tabla Reseñas que va a estar relacionada con nuestra tabla clientes. en este caso es una relación de uno a muchos por que un cliente puede hacer varias reseñas.
```sql
CREATE TABLE Reseñas (
N°_resena INT ,
N°_cliente INT,
comentario text(400);
fecha DATE,
puntuacion DECIMAL(2,1)
FOREIGN KEY (N°_cliente) REFERENCES clientes(N°_cliente)
);```
en este caso se realizo la relación, de la tabla reseña a la tabla clientes. en la ultima parte  <h5>FOREIGN KEY (N°_cliente) REFERENCES clientes(N°_cliente)</h5>
creamos la tabla pedidos para posteriormente relacionarlo con la tabla pedidos
```sql
CREATE TABLE pedidos(
id INT,
fecha_pedido DATETIME,
N°_cliente INT,
FOREIGN KEY (N°_cliente) REFERENCES clientes(N°_cliente)
)
```
ahora vamos a crear la tabla Envios
```sql
CREATE TABLE Envios(
id INT,
fehca_pedido DATETIME,
fecha_entrega DATETIME,
N°_cliente INT,
N°_pedido INT,
estado VARCHAR(45)
FOREIGN KEY (N°_cliente) REFERENCES clientes(N°_cliente),
FOREIGN KEY (N°_pedido) REFERENCES pedidos(N°_pedido)
);
```
las líneas donde se especifica FOREIGN KEY  hace referencia a una llave "foránea" esto quiere decir que es la llave de otra tabla en este caso hay dos llaves foráneas, una de la tabla clientes y otra de la tabla pedidos.

Finalmente relacionamos la tabla Pedidos_has_productos que es la tabla intermedia entre productos y pedidos.
```sql
CREATE TABLE pedidos_has_productos(
pedidos_id INT,
productos_id INT,
cantidad_producto INT
FOREIGN KEY (N°_cliente) REFERENCES clientes(N°_cliente),
FOREIGN KEY (N°_pedidos) REFERENCES pedidos(id));
```
con esto ya estaría lista nuestra base de datos para empezar a cargar los datos.