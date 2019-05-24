# WindowsServer
## Organización de la empresa
La empresa está organizada en tres departamentos los cuales son: Dirección, Almacén y Marketing. Cada departamento tiene un equipo y dos empleados que solo podrán entrar al equipo que está en su departamento.

En la empresa solo hay una impresora para todos.

Los usuarios solo podrán entrar al sistema de 15:00 a 22:00 de lunes a viernes.

Todo el sistema está en la red 192.168.5.0/24.

## Cambio de la IP y del Nombre al Servidor
Antes de hacer nada en el servidor tenemos que hacer unas configuraciones básicas. Lo primero que haremos es cambiar el nombre del equipo a uno distintivo. También hay que cambiar la IP del servidor a una estática para que el servidor siempre esté accesible y no haya problemas de acceso desde los clientes.

![imagen](./img/CAMBIARIP.PNG)
![imagen](./img/CAMBIARNOMBRE.PNG)

## Instalación de Active Directory
Para que nuestro equipo empiece a funcionar como servidor necesitamos un servicio. Los servicioes se agregan desde el enlace Administrar > Agregar Roles. Desde ahí siguiendo los pasos instalaremos el rol de Active Directory.

![imagen](./img/SELECCIONARAD.PNG)

Una vez lo tenemos seleccionado solo tenemos que darle a siguiente hasta que nos de la opción de instalar.

![imagen](./img/ADINSTALADO.PNG)

Una vez se haya instalado nos aparecerá un mensaje en el que nos dirá que el rol ya ha sido instalado, pero eso no es todo, Ahora tendremos que configurarlo promoviendolo como controlador de dominio.

Lo primero que tenemos que configurar es la implementación que en nuestro caso escogeremos un nuebo bosque y además le daremos un nuevo nombre de dominio a nuestro servidor. Aquí nos pedirá el nombre del nuevo dominio, y la contraseña del Administrador del mismo. Una vex promovido, se reiniciará el sistema, ya conectado dentro del nuevo dominio.

![imagen](./img/CREARBOSQUE.PNG)
![imagen](./img/AD%20INICIADO.PNG)

## Creación de las Unidades Organizativas de la Empresa
Nuestra empresa tiene tres departamentos en los que hay un equipo y dos empleados en cada uno. Lo primero que tenemos que hacer es crear la unidad organizativa para cada departamento, para ello hacemos clic en herramientas y nos vamos a la gestión de Active Directory. Desde ahí hacemos clic derecho sobre servidor(local) y seleccionamos crear una nueva unidad organizativa a la que le daremos el nombre deseado.

![imagen](./img/CREARUO1.PNG)
![imagen](./img/CREARUO2.PNG)

Una vez la tenemos creada accedemos a ella con un doble clic y dentro de ella creamos los correspondientes Equipos y Usuarios realizando los mismos pasos: Botón derecho > Nuevo > Equipo|Usuario.

![imagen](./img/CREARUSUARIO.PNG)
![imagen](./img/CREAREQUIPO.PNG)

Una vez creado todo, nos debería quedar algo así:

![imagen](./img/rs.PNG)

Ahora lo que tenemos que hacer es configurar los usuario. Para ello pondremos que los usuarios solo puedan entrar al equipo del departamento al que pertenecen.

![imagen](./img/RESTREQUIPO.PNG)

Ahora vamos a limitar las horas en las que los usuario pueden iniciar sesión en el sistema.

![imagen](./img/RESHORAS.PNG)

## Impresora
Por último tenemos que agregar la impresora y para ello tenemos que agregar el rol al servidor.

![imagen](./img/impresora.PNG)

Una vez instalado tenemos que configurarla y añadir la impresora.

![imagen](./img/impresora2.PNG)
![imagen](./img/impresora3.PNG)

## DHCP
Lo siguiente que vamos a hacer es agregar un nuevo rol a nuestro servidor de DHCP. Esto lo hacemos de la misma forma en la que hemos añadido el Active Directory.

![imagen](./img/SERVERDHCPINS.PNG)
![imagen](./img/SERVERDHCPINS2.PNG)

Después de añadirlo necesitamos configurarlo para que de el rango de IPs que nosotros queramos, y agregar a la resolución DNS la IP del Servidor. Para ello lo que tenemos que hacer es agregar un nuevo ámbito.

![imagen](./img/RANGO.PNG)

Una vez configurado ya está listo para que reparta IPs a los equipos de la red.

## Comprobaciones
### Conexión
Lo que necesitamos hacer es cambiar el nombre del equipo a uno que tengamos en el servidor creado. Una vez tengamos eso tenemos que cambiar el grupo de trabajo por el dominio de nuestro servidor. Una vez hecho eso nos pedirá la contraseña del administrador del sistema del servidor y ya se tendra acceso con los usuarios utilizados después de reiniciar el equipo.

![imagen](./img/NOMBREWIN7.PNG)
![imagen](./img/DOMINIO.PNG)

Una vez que hemos establecido la conexión vamos a intentar conectarnoS. Para ello necesitamos hacerlo por primera vez con el usuario Administrador:

![imagen](./img/ADMINLOGIN.PNG)
![imagen](./img/ADMINLOGEADO.PNG)

Después de esto, comprobaremos a acceder con un usuario, el cual no pueda acceder por la restricción horaria:

![imagen](./img/ERROR_HORARIO.PNG)

### DHCP
La comprobación la hacemos desde un cliente en la misma red física y cofigurándolo como DHCP y comprobar que tiene una IP dentro de nuestro rango, y que ha asignado bien el servidor DNS y la puerta de enlace.

![imagen](./img/dhcpcom.PNG)


# RAFAEL SALMERÓN MARTOS
