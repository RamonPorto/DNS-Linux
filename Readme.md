# Práctica 1.2 - DNS Linux

## 1. Primer paso

El primer paso de la práctica es instalar bind9 en la máquina virtual de Ubuntu. Para ello utilizaremos el siguiente comando:

~~~
sudo apt install bind9
~~~

## 2. Segundo paso

El segundo paso de la práctica sería comrpobar el estado de nuestro servicio. Para ello usamos el comando:

~~~
sudo systemctl status bind9
~~~

El resultado se mostrará de la siguiente manera

``` console
● named.service - BIND Domain Name Server
     Loaded: loaded (/lib/systemd/system/named.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2023-11-07 15:42:15 CET; 1h 5min ago
       Docs: man:named(8)
    Process: 694 ExecStart=/usr/sbin/named $OPTIONS (code=exited, status=0/SUCCESS)
   Main PID: 716 (named)
      Tasks: 6 (limit: 4484)
     Memory: 11.5M
        CPU: 105ms
     CGroup: /system.slice/named.service
             └─716 /usr/sbin/named -u bind

nov 07 16:14:59 usuario-VirtualBox named[716]: none:99: 'max-cache-size 90%' - setting to 3430MB (out of 3811MB)
nov 07 16:14:59 usuario-VirtualBox named[716]: obtaining root key for view _default from '/etc/bind/bind.keys'
nov 07 16:14:59 usuario-VirtualBox named[716]: configuring command channel from '/etc/bind/rndc.key'
nov 07 16:14:59 usuario-VirtualBox named[716]: configuring command channel from '/etc/bind/rndc.key'
nov 07 16:14:59 usuario-VirtualBox named[716]: managed-keys-zone: Unable to fetch DNSKEY set '.': operation canceled
nov 07 16:14:59 usuario-VirtualBox named[716]: reloading configuration succeeded
nov 07 16:15:00 usuario-VirtualBox named[716]: scheduled loading new zones
nov 07 16:15:00 usuario-VirtualBox named[716]: any newly configured zones are now loaded
nov 07 16:15:00 usuario-VirtualBox named[716]: running
nov 07 16:15:00 usuario-VirtualBox named[716]: managed-keys-zone: Key 20326 for zone . is now trusted (acceptance timer complete)



```

## 3. Tercer paso

El siguiente paso es copiar los ficheros de configuración de la anterior práctica a esta. En este caso copiaremos los 3 ficheros *named.conf* en el directorio ***/etc/bind*** y el archivo *db.asircastelao.int* en el directorio ***/var/lib/bind***

## 4. Cuarto paso

El último paso es comprobar mediante el comando dig que nuestro servicio dns funciona correctamente.

_Sintaxis del comando:_

~~~
dig @10.0.2.15 www.asircastelao.int
~~~

**Siendo 10.0.2.15 la ip de la máquina virtual que actua como servidor de DNS.*

## 5. Quinto paso

Ahora comprobaremos que funciona correctamente comprobando desde el host, fuera de la máquina virtual. Para ello debemos acceder a los adaptadores de red de la máquina virtual y añadir uno nuevo en modo *adaptador de red*

Una vez hecho esto debemos iniciar la máquina y averiguamos la ip del nuevo adaptador. Una vez la conocemos probaremos con el comando dig en el equipo local:

~~~
dig @10.0.9.133 www.asircastelao.int
~~~

En este caso la IP que fue asignada es la 10.0.9.133. 
