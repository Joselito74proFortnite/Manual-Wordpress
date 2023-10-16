# Manual-Wordpress

Crea una carpeta 

## Vagrant

**Creamos vagrant con este comando:**

[usuario@elpuig example]$ vagrant init ubuntu/jammy64

**Continuamos elevando las infraestructuras gracias a el siguientge comando:**

[usuario@elpuig example]$ vagrant up --provider=virtualbox

**Y con estos pasos podemos hacer ssh a vagrant:**

[usuario@elpuig example]$ vagrant ssh

**Podemos mirar los permisos y directorios con:**

vagrant@ubuntu-jammy:~$ ll /vagrant

# Apache2

**1.Actualizacion**

apt update

**2.Instalacion de apache2**

apt install -y apache2

**3.Instalacion de la base de datos mysql-server**

apt install -y mysql-server

**4.Instalacion de librerias php**

apt install -y php libapache2-mod-php

apt install -y php-fpm php-common php-mbstring php-xmlrpc php-soap php-gd php-xml php-intl php-mysql php-cli php-ldap php-zip php-curl

**5.Reinicio de apache2**

systemctl restart apache2

## MySQL

**Consola MySQL

En la terminal de forma root ponemos el siguiente comando:**

root@elpuig:~$ mysql

**Creacion de la base de datos:

Dentro de mysql cramos la base con nombre: bbdd**

CREATE DATABASE bbdd;

**Creacion del usuario

Tingueu en compte que s'haurà d'identificar la IP des de la qual s'accedirà a la base de dades, en aquest cas, localhost.**

CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

**Dar permisos:**

GRANT ALL ON bbdd.* to 'usuario'@'localhost';

**Salir de bbdd:**

exit

**Comprobar la conexion**

alumne@elpuig:~$ mysql -u usuario -p

