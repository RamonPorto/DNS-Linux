# Práctica 1.2 - DNS Linux

# 1. Primer paso

El primer paso de la práctica es instalar bind9 en la máquina virtual de Ubuntu. Para ello utilizaremos el siguiente comando:

~~~
sudo apt install bind9
~~~

# 2. Segundo paso

El segundo paso de la práctica sería comrpobar el estado de nuestro servicio. Para ello usamos el comando:

~~~
sudo systemctl status bind9
~~~

# 3. Tercer paso

El siguiente paso es copiar los ficheros de configuración de la anterior práctica a esta. En este caso copiaremos los 3 ficheros *named.conf* en el directorio ***/etc/bind*** y el archivo *db.asircastelao.int* en el directorio ***/var/lib/bind***

# 4. Cuarto paso

El último paso es comprobar mediante el comando dig que nuestro servicio dns funciona correctamente.

_Sintaxis del comando:_

~~~
dig @10.0.2.15 www.asircastelao.int
~~~

**Siendo 10.0.2.15 la ip de la máquina virtual que actua como servidor de DNS.*