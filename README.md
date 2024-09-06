# Proyecto de Base de Datos para un BAZAR

Este archivo README proporciona una descripción completa de cómo se creó la base de datos, las tablas y los datos de prueba cargados.

## Índice

1. [Introducción]
2. [Diseño de la Base de Datos]
3. [Diseño de Ventanas]

   
## Introducción

Este proyecto tiene como objetivo gestionar un sistema de ventas para una tienda, utilizando una base de datos relacional para almacenar
información sobre los clientes, el inventario y las ventas. La base de datos está estructurada para permitir una gestión eficiente de la
información y realizar consultas efectivas.

## Diseño de la Base de Datos

La base de datos está diseñada con cuatro tablas principales:

1. **Clientes**: Almacena información sobre los clientes de la tienda.
2. **Categorias**: Son los distintos tipos de productos que ofrece la tienda.
3. **Inventario**: Contiene detalles sobre los productos disponibles en la tienda.
4. **Ventas**: Registra las transacciones realizadas, incluyendo la información del cliente, el producto vendido y el método de pago.

## Diseño de Ventanas

Codigo SQL
===========================================================================================================================

## Se crea la base de datos llamada bazar.

CREATE DATABASE bazar;

## Se crean las tablas de clientes, inventario, categorias y ventas.

CREATE TABLE bazar.clientes (
    id_cliente INT PRIMARY KEY AUTO_INCREMENT,
    nombre_cliente VARCHAR(50) NOT NULL,
    direccion_cliente VARCHAR(255),
    telefono_cliente VARCHAR(20),
    email_cliente VARCHAR(100)
);

CREATE TABLE bazar.categorias (
    id_categoria INT PRIMARY KEY AUTO_INCREMENT,
    nombre_categoria VARCHAR(50) NOT NULL
);

CREATE TABLE bazar.inventario (
    codigo_producto VARCHAR(50) PRIMARY KEY,
    nombre_producto VARCHAR(255) NOT NULL,
    descripcion TEXT,
    precio DECIMAL(10, 2) NOT NULL,
    id_categoria INT NOT NULL,
    cantidad INT NOT NULL,
    FOREIGN KEY (id_categoria) REFERENCES bazar.categorias(id_categoria)
);

CREATE TABLE bazar.ventas (
    id_venta VARCHAR(20)PRIMARY KEY,
    id_cliente INT NOT NULL,
    fecha_venta DATE NOT NULL,
    descripcion_venta VARCHAR(255) NOT NULL,
    total_venta DECIMAL(10, 2) NOT NULL,
    met_pago ENUM('Crédito', 'Débito', 'Efectivo', 'Transferencia') NOT NULL,
    FOREIGN KEY (id_cliente) REFERENCES bazar.clientes(id_cliente)
);

============================================================================================================================

## Se inserta la informacion a las tablas.

##  Tabla CLIENTES

INSERT INTO bazar.clientes (id_cliente, nombre_cliente, direccion_cliente, telefono_cliente, email_cliente) VALUES
(1, 'Juan Pérez', 'Av. Corrientes 1234, Buenos Aires, Argentina', '+54 11 1234-5678', 'juanperez@gmail.com'),
(2, 'María Gómez', 'Calle Florida 456, Buenos Aires, Argentina', '+54 11 2345-6789', 'mariagomez@gmail.com'),
(3, 'Carlos López', 'Av. de Mayo 789, Buenos Aires, Argentina', '+54 11 3456-7890', 'carloslopez@gmail.com'),
(4, 'Ana Martínez', 'Calle Santa Fe 321, Buenos Aires, Argentina', '+54 11 4567-8901', 'anamartinez@gmail.com'),
(5, 'Pedro Sánchez', 'Plaza Italia 654, Buenos Aires, Argentina', '+54 11 5678-9012', 'pedrosanchez@gmail.com'),
(6, 'Laura Fernández', 'Av. Libertador 987, Buenos Aires, Argentina', '+54 11 6789-0123', 'laurafernandez@gmail.com'),
(7, 'Jorge Romero', 'Calle Tucumán 432, Córdoba, Argentina', '+54 351 1234-5678', 'jorgeromero@gmail.com'),
(8, 'Marta Ruiz', 'Av. Colón 876, Córdoba, Argentina', '+54 351 2345-6789', 'martaruiz@gmail.com'),
(9, 'Andrés Díaz', 'Calle Viamonte 543, Rosario, Argentina', '+54 341 3456-7890', 'andresdiaz@gmail.com'),
(10, 'Isabel Torres', 'Av. Pellegrini 678, Rosario, Argentina', '+54 341 4567-8901', 'isabeltorres@gmail.com'),
(11, 'Francisco Moya', 'Calle San Martín 210, Mendoza, Argentina', '+54 261 5678-9012', 'franciscomoya@gmail.com'),
(12, 'Beatriz Silva', 'Av. Emilio Civit 543, Mendoza, Argentina', '+54 261 6789-0123', 'beatrizsilva@gmail.com'),
(13, 'Rafael Castro', 'Calle Las Heras 654, San Juan, Argentina', '+54 264 7890-1234', 'rafaelcastro@gmail.com'),
(14, 'Silvia Gómez', 'Av. Libertador 789, San Juan, Argentina', '+54 264 8901-2345', 'silviagomez@gmail.com'),
(15, 'Manuel Ortega', 'Calle Alem 432, San Luis, Argentina', '+54 266 9012-3456', 'manuelortega@gmail.com'),
(16, 'Patricia Ríos', 'Av. Sarmiento 321, San Luis, Argentina', '+54 266 0123-4567', 'patriciarios@gmail.com'),
(17, 'Sergio Vargas', 'Calle Balcarce 876, La Plata, Argentina', '+54 221 1234-5678', 'sergiovargas@gmail.com'),
(18, 'Elena Cruz', 'Av. 19 de Noviembre 987, La Plata, Argentina', '+54 221 2345-6789', 'elenacruz@gmail.com'),
(19, 'Gustavo Romero', 'Calle 43 543, La Plata, Argentina', '+54 221 3456-7890', 'gustavoromero@gmail.com'),
(20, 'Marta Delgado', 'Paseo del Bosque 654, Mar del Plata, Argentina', '+54 223 4567-8901', 'martadelgado@gmail.com'),
(21, 'Víctor Herrera', 'Calle Güemes 432, Mar del Plata, Argentina', '+54 223 5678-9012', 'victorherrera@gmail.com'),
(22, 'Clara Morales', 'Av. Luro 321, Mar del Plata, Argentina', '+54 223 6789-0123', 'claramorales@gmail.com'),
(23, 'Joaquín Núñez', 'Calle Belgrano 210, Bahía Blanca, Argentina', '+54 291 7890-1234', 'joaquinnunez@gmail.com'),
(24, 'Laura Moreno', 'Av. Alem 987, Bahía Blanca, Argentina', '+54 291 8901-2345', 'lauramoreno@gmail.com'),
(25, 'Luis Castro', 'Calle Moreno 543, Neuquén, Argentina', '+54 299 9012-3456', 'luiscastro@gmail.com'),
(26, 'Gabriela Soto', 'Av. Argentina 876, Neuquén, Argentina', '+54 387 1234-5678', 'gabrielasoto@gmail.com'),
(27, 'Ricardo Morales', 'Calle Rawson 321, Neuquén, Argentina', '+54 387 2345-6789', 'ricardomorales@gmail.com'),
(28, 'Claudia López', 'Paseo del Parque 654, Salta, Argentina', '+54 387 3456-7890', 'claudiolopez@gmail.com'),
(29, 'Manuel Paredes', 'Calle 20 de Febrero 987, Salta, Argentina', '+54 387 4567-8901', 'manuelparedes@gmail.com'),
(30, 'Natalia Díaz', 'Av. Belgrano 876, Salta, Argentina', '+54 299 0123-4567', 'natalia.diaz@gmail.com');


## Tabla CATEGORIAS

INSERT INTO categorias (id_categoria, nombre_categoria) VALUES 
(1, 'Juguetería'),
(2, 'Ropa'),
(3, 'Escolar'),
(4, 'Cotillón'),
(5, 'Cocina'),
(6, 'Decoración'),
(7, 'Herramientas');

## Tabla INVENTARIO

INSERT INTO bazar.inventario (codigo_producto, nombre_producto, descripcion, precio, id_categoria, cantidad) VALUES

-- JUGUETERIA
('J101', 'Pelota de Playa', 'Pelota de playa colorida', 10.99, 1, 100),
('J202', 'Muñeca', 'Muñeca con accesorios', 25.50, 1, 50),
('J305', 'Construcción de Bloques', 'Juego de bloques para construir', 15.75, 1, 75),
('J408', 'Tren Eléctrico', 'Tren eléctrico con vías', 45.00, 1, 30),
('J519', 'Rompecabezas', 'Rompecabezas de 500 piezas', 12.25, 1, 60),

-- ROPA
('R134', 'Camisa Casual', 'Camisa de algodón para hombre', 22.00, 2, 200),
('R289', 'Pantalones Jeans', 'Pantalones jeans de mezclilla', 30.00, 2, 150),
('R374', 'Vestido de Verano', 'Vestido ligero para verano', 35.00, 2, 120),
('R485', 'Chaqueta de Cuero', 'Chaqueta de cuero para invierno', 85.00, 2, 80),
('R592', 'Zapatos Deportivos', 'Zapatos deportivos para correr', 55.00, 2, 90),

-- ESCOLAR
('E133', 'Cuaderno A4', 'Cuaderno de tamaño A4 con 100 hojas', 3.50, 3, 500),
('E147', 'Lápices de Colores', 'Set de 12 lápices de colores', 4.75, 3, 300),
('E158', 'Calculadora Científica', 'Calculadora científica con funciones avanzadas', 12.00, 3, 150),
('E169', 'Mochila Escolar', 'Mochila con compartimentos múltiples', 28.00, 3, 75),
('E185', 'Bolígrafos', 'Paquete de 10 bolígrafos', 2.50, 3, 400),

-- COTILLON
('C222', 'Globos', 'Paquete de 50 globos de colores', 6.00, 4, 200),
('C239', 'Serpentina', 'Serpentina para decoraciones', 5.00, 4, 180),
('C304', 'Confeti', 'Paquete de confeti multicolor', 4.00, 4, 250),
('C411', 'Gorra de Fiesta', 'Gorra de fiesta con estampado', 3.50, 4, 300),
('C520', 'Pañuelos de Papel', 'Pañuelos de papel para fiestas', 7.00, 4, 220),

-- COCINA
('K101', 'Cuchillo Chef', 'Cuchillo de cocina profesional', 25.00, 5, 40),
('K215', 'Sartén Antiadherente', 'Sartén antiadherente de 28 cm', 30.00, 5, 35),
('K326', 'Tetera de Acero', 'Tetera de acero inoxidable', 22.00, 5, 50),
('K439', 'Set de Utensilios', 'Set de utensilios de cocina', 18.00, 5, 60),
('K548', 'Platos de Cerámica', 'Juego de 6 platos de cerámica', 35.00, 5, 45),

-- DECORACION
('D102', 'Cuadro Moderno', 'Cuadro con diseño moderno', 50.00, 6, 25),
('D213', 'Lámpara de Mesa', 'Lámpara de mesa con base de madera', 40.00, 6, 30),
('D327', 'Cojín Decorativo', 'Cojín decorativo para sofá', 15.00, 6, 75),
('D438', 'Vaso de Vidrio', 'Vaso decorativo de vidrio', 10.00, 6, 100),
('D547', 'Espejo Decorativo', 'Espejo con marco decorativo', 60.00, 6, 20),

-- HERRAMIENTAS
('H102', 'Taladro Eléctrico', 'Taladro eléctrico de 500W', 75.00, 7, 20),
('H215', 'Juego de Destornilladores', 'Juego de 10 destornilladores', 20.00, 7, 40),
('H334', 'Sierra Circular', 'Sierra circular para madera', 95.00, 7, 15),
('H445', 'Martillo', 'Martillo de acero con mango de madera', 15.00, 7, 60),
('H559', 'Cinta Métrica', 'Cinta métrica de 5 metros', 8.00, 7, 100);


# Tabla VENTAS

INSERT INTO bazar.ventas (id_venta, id_cliente, fecha_venta, descripcion_venta, total_venta, met_pago) VALUES
('V0001', 1, '2024-01-15', 'Compra de Pelota de Playa y Muñeca', 36.49, 'Crédito'),
('V0002', 2, '2024-02-20', 'Compra de Camisa Casual y Pantalones Jeans', 52.00, 'Débito'),
('V0003', 3, '2024-03-05', 'Compra de Cuaderno A4 y Lápices de Colores', 8.25, 'Efectivo'),
('V0004', 4, '2024-04-10', 'Compra de Rompecabezas y Tren Eléctrico', 57.75, 'Transferencia'),
('V0005', 5, '2024-05-15', 'Compra de Sartén Antiadherente y Cuchillo Chef', 55.00, 'Crédito'),
('V0006', 6, '2024-06-20', 'Compra de Mochila Escolar y Bolígrafos', 30.50, 'Débito'),
('V0007', 7, '2024-07-25', 'Compra de Cuadro Moderno y Lámpara de Mesa', 90.00, 'Efectivo'),
('V0008', 8, '2024-08-30', 'Compra de Set de Utensilios y Platos de Cerámica', 53.00, 'Transferencia'),
('V0009', 9, '2024-01-05', 'Compra de Globos y Serpentina', 11.00, 'Crédito'),
('V0010', 10, '2024-02-15', 'Compra de Confeti y Pañuelos de Papel', 11.00, 'Débito'),
('V0011', 11, '2024-03-20', 'Compra de Lámpara de Mesa y Cojín Decorativo', 55.00, 'Efectivo'),
('V0012', 12, '2024-04-15', 'Compra de Zapatos Deportivos y Vestido de Verano', 57.00, 'Transferencia'),
('V0013', 13, '2024-05-30', 'Compra de Calculadora Científica y Cuaderno A4', 15.50, 'Crédito'),
('V0014', 14, '2024-06-10', 'Compra de Camisa Casual y Pantalones Jeans', 52.00, 'Débito'),
('V0015', 15, '2024-07-20', 'Compra de Rompecabezas y Tren Eléctrico', 57.75, 'Efectivo'),
('V0016', 16, '2024-08-15', 'Compra de Sartén Antiadherente y Cuchillo Chef', 55.00, 'Transferencia'),
('V0017', 17, '2024-01-25', 'Compra de Cuadro Moderno y Vaso de Vidrio', 60.00, 'Crédito'),
('V0018', 18, '2024-02-28', 'Compra de Taladro Eléctrico y Cinta Métrica', 83.00, 'Débito'),
('V0019', 19, '2024-03-15', 'Compra de Globos y Serpentina', 11.00, 'Efectivo'),
('V0020', 20, '2024-04-05', 'Compra de Set de Utensilios y Platos de Cerámica', 53.00, 'Transferencia'),
('V0021', 21, '2024-05-20', 'Compra de Lámpara de Mesa y Cojín Decorativo', 55.00, 'Crédito'),
('V0022', 22, '2024-06-15', 'Compra de Zapatos Deportivos y Vestido de Verano', 92.00, 'Débito'),
('V0023', 23, '2024-07-10', 'Compra de Cuaderno A4 y Lápices de Colores', 8.25, 'Efectivo'),
('V0024', 24, '2024-08-20', 'Compra de Calculadora Científica y Mochila Escolar', 40.50, 'Transferencia'),
('V0025', 25, '2024-01-10', 'Compra de Sartén Antiadherente y Cuchillo Chef', 55.00, 'Crédito'),
('V0026', 26, '2024-02-25', 'Compra de Cuadro Moderno y Lámpara de Mesa', 90.00, 'Débito'),
('V0027', 27, '2024-03-30', 'Compra de Taladro Eléctrico y Juego de Destornilladores', 95.00, 'Efectivo'),
('V0028', 28, '2024-04-20', 'Compra de Rompecabezas y Tren Eléctrico', 57.75, 'Transferencia'),
('V0029', 29, '2024-05-25', 'Compra de Confeti y Pañuelos de Papel', 11.00, 'Crédito'),
('V0030', 30, '2024-06-10', 'Compra de Platos de Cerámica y Set de Utensilios', 53.00, 'Débito');


============================================================================================================================




































































