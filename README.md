# Taller práctico 03: Laboratorio: Ecosistema Odoo

# Fase 1: Integración de Módulos

1. **Instalación y Alteración del Esquema**.  
   Primero entraremos en odoo y en el menú principal deberemos entrar en la aplicación **Aplicaciones** y buscar e instalar los módulos **Inventario** y **Facturación**.  
2. **Nuestros clientes**.  
   Para la práctica debemos tener un archivo de datos (en este caso en formato CSV).  
   Copia estos datos y crea un archivo llamado *clientes\_mock.csv*

   Nombre,Correo electrónico,Teléfono,Ciudad,País,Es una compañía  
   Tech Solutions Ibérica,info@techsolutions.es,\+34 611 222 333,Sevilla,España,True  
   María Fernández,maria.fernandez@ejemplo.com,\+34 644 555 666,Madrid,España,False  
   Distribuciones del Sur,ventas@delsur.es,\+34 677 888 999,Málaga,España,True  
   Carlos Ruiz,cruiz.dev@ejemplo.com,\+34 699 111 222,Valencia,España,False  
   Global Logistics S.L.,logistica@global.es,\+34 622 333 444,Barcelona,España,True  
   Laura Gómez,laura.gomez@ejemplo.com,\+34 655 444 333,Bilbao,España,False  
   Sistemas Avanzados,contacto@sistemas.es,\+34 688 777 666,Zaragoza,España,True  
   Pedro Sánchez,psanchez@ejemplo.com,\+34 612 345 678,Murcia,España,False  
   Innovaciones Web,dev@innovaciones.es,\+34 698 765 432,Granada,España,True  
   Elena Torres,etorres.design@ejemplo.com,\+34 633 222 111,Alicante,España,False

     
   

Instalamos en VS Code la extensión Rainbow CSV.

**Ruta en Odoo**: Navega a la aplicación de **Ventas \> Pedidos \> Clientes**.

![][image1]

Clicamos en el engranaje e importamos registros, subimos el archivo CSV y antes de importarlo deberemos realizar un Test para validar que el tipo de dato coincide con la base de datos. Si todo está correcto clicamos “Importar”

![][image2]

3. **El ciclo de negocio**.  
   Entraremos con el usuario “Comercial01” para crear un presupuesto para un nuevo cliente.  
* Producto de tipo almacenable (Ejemplo de nombre: “Monitor 24””)  
  Creamos el presupuesto y hacemos clic en confirmar para que pase de ‘Presupuesto’ a ‘Pedido en venta’. Arriba aparecerá un icono de un camión que nos indica que hay “1 Entrega”.![][image3]  
  Si realizamos clic en el camión veremos que el producto estará en estado “Reservado”. Ahora validaremos la entrega. Si volvemos al pedido original podremos utilizar el botón “Crear Factura” ya que hemos validado la entrega. A partir de ello crearemos una factura y se confirmará.
