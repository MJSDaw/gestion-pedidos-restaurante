Objetivo General: Desarrollar una aplicación web para el Departamento de Pedidos de una cadena de restaurantes que permita gestionar pedidos de comida, bebida y materiales de manera eficiente.

Objetivos Específicos:

1. Implementar un sistema de carrito de compra para que los restaurantes puedan seleccionar productos antes de confirmar un pedido.

2. Crear una base de datos para almacenar información sobre restaurantes, productos, categorías y pedidos.

3. Generar un flujo de pantallas que facilite la navegación por la aplicación y las operaciones relacionadas con el pedido.

4. Desarrollar un sistema de autenticación para asegurar que solo usuarios autorizados puedan acceder a la aplicación.

Fases del Proyecto

mapa conceptual

1. Análisis de Requisitos* (*Detalles al final del documento) 

Se realizará un análisis detallado de las funcionalidades de la aplicación, que deberá incluir:

• Consulta de categorías y productos.

• Añadir productos al carrito.

• Visualización del carrito y gestión de productos en él.

• Realización y confirmación de pedidos mediante notificación por correo electrónico.

2. Diseño de la Aplicación

• Esquema ER: Un diagrama entidad-relación representará las relaciones entre las tablas de la base de datos, incluyendo entidades como Restaurantes, Pedidos, Productos, Categorías y tablas de relación correspondientes.

• Diagrama de flujo de pantallas: Se diseñará un flujo de pantallas que guiará al usuario desde el login hasta la confirmación del pedido, pasando por la selección de productos y revisión del carrito.

3. Implementación

• Base de Datos: Se implementará la base de datos en SQL según el diseño lógico y físico definido.

• Carrito de Compra: Desarrollo de la lógica de selección de productos y actualización del carrito.

• Control de Acceso: Implementación de autenticación para restringir el acceso a usuarios autorizados.

• Notificaciones por Correo: Envío de correos de confirmación de pedidos.

4. Pruebas y Validación

• Verificación del flujo de trabajo desde el inicio de sesión hasta la confirmación del pedido.

• Pruebas de funcionalidad del carrito, control de acceso y envío de correos.

Diagrama de flujo de pantallas
Flujo de ventanas

Ejemplo de resultado final:
Resultado final

Especificaciones Técnicas

1. Base de Datos

Tablas esenciales:

• Restaurantes: información del restaurante que realiza el pedido.

• Pedidos: detalles del pedido realizado.

• Productos: descripción de los productos disponibles.

• Categorías: clasificación de los productos.

• PedidosProductos: tabla de relación entre pedidos y productos con detalles de cantidad.

2. Limitaciones

• No permite autorregistro de usuarios.

• Caso base - No incluye un panel de administración para gestionar usuarios, categorías ni productos.

3. El carrito de la compra

La estructura de datos utilizada para el carrito de la compra es uno de los puntos más importantes de la aplicación. Para almacenarlo se utilizará una variable de sesión.

El carrito será un array asociativo en el que las claves de los elementos representan el código de un producto, y el valor, el número de unidades pedidas de este producto.

El array comienza vacío. Cuando se añade un producto al pedido, hay que comprobar si ya hay en el array algún elemento que tenga como clave el código del producto. Si no lo hay, se añade un nuevo elemento tomando como clave el código y como valor el número de unidades.

Por ejemplo, si el carrito está vacío y se añaden 2 unidades del producto con código 4, se creará un elemento del array con clave 4 y valor 2.

Si ya hay un elemento con ese código, se suman las unidades al valor actual del elemento.

4. Control de acceso

Cuando se realiza login con éxito, se crea una nueva sesión y dos variables de sesión:

Un array con dos campos. Uno para guardar el nombre del usuario (el correo del restaurante) y otro para su código, así no hay que buscarlo en la base de datos más adelante.
La variable para el carrito de la compra.
El resto de los ficheros de la aplicación comienza uniéndose a la sesión y comprobando que la primera de estas variables existe. Si no se han creado, es que el usuario no ha hecho login y por tanto no puede acceder. En ese caso se le redirige a la página de Login.

--------------------------------------------------------------------------------------------------------

Análisis de Requisitos*
La aplicación debe permitir:

Consultar las categorías.
Consultar los productos.
Añadir una o más unidades de un producto al pedido.
Consultar el pedido del carrito y eliminar productos de este.
Realizar el pedido, introduciéndolo en la base de datos y enviando correos de confirmación al restaurante que hace el pedido y al Departamento de Pedidos de la empresa.
Para acceder a la aplicación será necesario autentificarse. Se supone que en cada restaurante habrá un responsable de pedidos que es quien tiene el usuario y la clave para acceder a la aplicación.

De cada categoría se quiere almacenar su código, su nombre y su descripción. De los pro-ductos, su código, nombre, descripción, peso, cantidad en stock y la categoría a la que pertene-cen. Cada producto pertenece a una categoría.

De cada pedido interesa saber:

El restaurante que lo realizó.
Los productos que se pidieron, incluyendo la cantidad de unidades de cada producto.
Si ha sido enviado ya o no.
La fecha en la que se realizó el pedido.
Los pedidos se introducen en la base de datos como no enviados. Cuando se envíen el Departamento de Pedidos los marcará como enviados (directamente en la base de datos, la aplicación no se ocupa de esto).

De los restaurantes se guarda la siguiente información:

a) El código.

b) El correo electrónico. El correo es el nombre de usuario para acceder a la aplicación.

c) La clave.

d) País, dirección y código postal.