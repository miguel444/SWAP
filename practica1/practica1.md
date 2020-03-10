# **PRÁCTICA 1**
    
## *Preparación de las máquinas virtuales*
Para esta práctica inicialmente debemos crear dos máquinas virtuales llamadas M1 y M2 , las cuáles dispondrán de 512 MB de memoria RAM y un disco duro dinámico de 10GB.

La siguiente imagen representa como se ha creado una de las máquinas virtuales pero el proceso se ha realizado sombre ambas máquinas.


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

Una vez tenemos el sistema operativo en las dos máquinas vamos a instalar el servicio LAMP, ya que no nos  aparecido la opción durante la instalación vamos a proceder a instalarlo manualmente de la siguiente forma :

- `sudo apt-get install apache2 mysql-server mysql-client`

![img](https://github.com/miguel444/SWAP/blob/master/practica1/images/Instalar%20LAMP.png)



