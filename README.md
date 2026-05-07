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
<img width="395" height="155" alt="Captura de pantalla 2026-05-07 090103" src="https://github.com/user-attachments/assets/424438c1-1e84-44c5-9af5-fe21e5d7d5f2" />


Clicamos en el engranaje e importamos registros, subimos el archivo CSV y antes de importarlo deberemos realizar un Test para validar que el tipo de dato coincide con la base de datos. Si todo está correcto clicamos “Importar”

<img width="820" height="600" alt="Captura de pantalla 2026-05-07 090147" src="https://github.com/user-attachments/assets/fecd68f4-4466-4830-83f2-1f85c66c5f6c" />


3. **El ciclo de negocio**.  
   Entraremos con el usuario “Comercial01” para crear un presupuesto para un nuevo cliente.  
* Producto de tipo almacenable (Ejemplo de nombre: “Monitor 24””)  
  Creamos el presupuesto y hacemos clic en confirmar para que pase de ‘Presupuesto’ a ‘Pedido en venta’. Arriba aparecerá un icono de un camión que nos indica que hay “1 Entrega”.<img width="942" height="806" alt="Captura de pantalla 2026-05-05 102253" src="https://github.com/user-attachments/assets/c6a74e6f-bb5a-4793-a5c4-3fdc1b901600" />
 
  Si realizamos clic en el camión veremos que el producto estará en estado “Reservado”. Ahora validaremos la entrega. Si volvemos al pedido original podremos utilizar el botón “Crear Factura” ya que hemos validado la entrega. A partir de ello crearemos una factura y se confirmará.
# Fase 2: Elaboración de Informes

1. **El Peligro de Modificar el *Core* y la Solución**.  
   1. Nunca de debe modificar el código fuente original (*core*), para ello se puede realizar de la siguiente manera  
   2. Activaremos el modo desarrollador y siguiendo la siguiente ruta: *Ajustes \> Técnico \> Interfaz de Usuario \> Vistas* (*Views*).  
2. Buscaremos utilizando un filtro por **Clave(Key)** y buscaremos *sale.report\_saleorder\_document*.  
3. **Modificación del XML mediante Herencia (Práctica directa)**:  
   1. Abriremos el registro.  
   2. Locazaremos la seccion final buscando el cierre del \<div class=”page”\>.  
   3. En la línea de arriba del cierre \</div\> copia y pega el siguiente bloque de marcado HTML/XML.  
       \<div class\="row mt32 mb32" id\="legal\_warning"\>  
          \<div class\="col-12"\>  
              \<p style\="color: red; font-weight: bold; border-top: 1px solid black; padding-top: 10px;"\>  
                  Atención: Este documento vinculante está sujeto a las condiciones generales de venta de DAM/DAW S.L. (CIF: B-12345678).  
              \</p\>  
              \<p class\="text-muted" style\="font-size: 10px; text-align: justify;"\>  
                  Protección de datos: En cumplimiento de la Ley Orgánica 3/2018 y el RGPD europeo, le informamos que sus datos serán tratados de forma estrictamente confidencial. Puede ejercer sus derechos ARCO dirigiéndose a nuestro DPO.  
              \</p\>  
          \</div\>  
        \</div\>  
   4. Guardamos los cambios en la vista  
   5. Validamos el renderizado: volveremos a Ventas y abriremos el pedido que creamos. Clicamos en la tuerca y descargaremos el Presupuesto.  
      <img width="922" height="869" alt="image" src="https://github.com/user-attachments/assets/d35416de-9217-4a3d-bacd-9c60096007ec" />


<img width="625" height="400" alt="Captura de pantalla 2026-05-05 102328" src="https://github.com/user-attachments/assets/ddf0e6ac-1158-4f19-89c2-3b0b852e1bda" />

# Fase 3: Exportación de Información

1. Nos dirigimos a los clientes mediante la siguiente ruta: *Facturación \> Clientes \> Clientes*.  
2. Seleccionamos todos los clientes  
3. Una vez seleccionados seleccionamos la opción “Exportar”  
   1. Seleccionamos "Exportar datos compatibles con importación".  
   2. Formato CSV  
   3. Y seleccionamos Nombre, Correo electrónico, teléfono y Nombre del país   
4. Clicamos en “Exportar” y se descargara el archivo  
5. Abrimos el archivo .csv en VS Code
<img width="640" height="261" alt="Captura de pantalla 2026-05-05 102353" src="https://github.com/user-attachments/assets/c1fc84df-d28c-4a72-b526-40e3f893ed10" />
