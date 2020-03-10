# **PRÁCTICA 1 : Preparación de las herramientas**

- **AUTOR : MIGUEL ÁNGEL PÉREZ DÍAZ**
- **ASIGNATURA : SERVIDORES WEB DE ALTAS PRESTACIONES**

    
## *Preparación de las máquinas virtuales*
Para esta práctica inicialmente debemos crear dos máquinas virtuales llamadas M1 y M2 , las cuáles dispondrán de 512 MB de memoria RAM y un disco duro dinámico de 10GB.

La siguiente imagen representa como se ha creado una de las máquinas virtuales pero el proceso se ha realizado sobre ambas máquinas.


Se nombra a la máquina virtual y se asigna tipo de sistema operativo y versión:

- Nombre de la máquina virtual : M2 (M1 en el otro caso)
- Tipo : Linux
- Versión: Ubuntu (64 bits)
  
---

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/Nombre%20y%20SO.png)

---

A continuación vamos a asignar a cada máquina la memoria RAM y el espacio de disco duro mencionados anteriormente. De esta manera seleccionamos ambos valores :

- Asignación memoria RAM:

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/Asignar%20RAM.png)

---

- Asignación espacio disco duro:

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/Asignar%20espacio.png)

---

## *Configuración de los adaptadores de red de las máquinas virtuales*
Para poder comunicar máquinas entre un mismo anfitrión y entre ellas, y éstas tener
conexión a internet, es necesario añadir a cada máquina dos adaptadores un adaptador
de red en modo NAT y otro adaptador en solo-anfitrión para crear una red local entre
las máquinas virtuales y el anfitrión.

A continuación se va a configurar los adaptadores de red : uno en modo NAT (viene por defecto) y habilitamos el adaptador de host-only : 

- Adaptador de red en modo NAT

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/NAT.png)

---

- Adaptador de red en modo Host-Only


![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/Solo-Anfitrion.png)

---

## *Instalación Ubuntu Server 18.04 y puesta a punto*

En esta sección se va a completar la instalación de Ubuntu Server para las dos máquinas virtuales, de esta forma obtendremos las máquinas totalmente configuradas para los ejercicios que se piden para esta práctica. 

Seleccionamos todas las opciones por defecto y las correspondiente a nuestra franja horaria, y finalmente creamos nuestro usuario. Antes de crear el usuario en cada máquina virtual seleccionamos que se instale el servicio SSH en el proceso de instalación.

- Selección servicio SSH:
  
![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/SSH.png)

---

- Creación de usuario
    - User : miguel444 (usuario de Github)
    - Password: Swap1234

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/Crear%20Usuario.png)

---

Una vez tenemos el sistema operativo en las dos máquinas vamos a instalar el servicio LAMP, ya que no nos ha aparecido la opción durante la instalación vamos a proceder a instalarlo manualmente de la siguiente forma :

- `sudo apt-get install apache2 mysql-server mysql-client`

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/Instalar%20LAMP.png)

También, y de cara a las siguientes prácticas, podemos activar la cuenta de root. De esta forma, luego podremos acceder como superusuario, copiar contenidos con todos los permisos, etc, sin necesidad de andar usando sudo. Para eso, podéis ejecutar en todas las máquinas el siguiente comando:

- `sudo passwd root`

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/Activar%20Cuenta%20Root.png)


Finalmente antes de ponerse manos a la obra y realizar las tareas correspondiente a esta práctica, vamos a comprobar que los servicios instalados anteriormente de LAMP y SSH se encuentran activos. De esta forma:

- Para comprobar el estado del servicio Apache2   
    - `sudo service apache2 status`
    - `apache2 -v`

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/Apache2%20funciona.png)

- Para comprobar el estado del servicio SSH   `sudo systemctl status ssh`

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/SSH-funciona.png)

---

## *Cuestiones a resolver*
En esta práctica el objetivo es **configurar las máquinas virtuales** (al menos dos) para
trabajar en prácticas posteriores, **asegurando la conectividad entre dichas máquinas**

Específicamente, hay que llevar a cabo las siguientes tareas:

1. Acceder por SSH de una máquina a otra
2. Acceder mediante la herramienta curl desde una máquina a la otra


Antes de realizar cualquiera de las tareas vamos a comprobar si una vez configurados los adaptadores de red obtenemos conectividad entre ambas máquinas. De este modo vamos a realizar `ping` de una máquina a otra y vicerversa.

- Ping de M1 a M2 

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/Ping%20m1-m2.png)

- Ping de M2 a M1

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/Ping%20m2-m1.png)

---

Una vez comprobada la conectividad vamos a proceder a crear el fichero *ejemplo.html* en la ruta *var/www/html* en M1 :

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/ejemplo-html.png)

De esta forma vamos a ejecutar el siguiente comando en M2 : `curl http://192.168.56.12/ejemplo.html` para obtener y mostrar el fichero creado anteriormente en M1. Obteniendo así la siguiente respuesta :

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/CURL%20HTML.png)

---

Como última tarea vamos a proceder a realizar SSH desde la máquina M2 a M1, para ello debemos ejecutar lo siguiente : 
`ssh 192.168.56.12` (siendo ésta la dirección IP de M1). 

Una vez establecida la conexión nos pedirá confirmación y la contraseña de la dirección destino , en este caso la contraseña de M1 que como sabemos sería Swap1234.

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/Conexion%20SSH.png)


