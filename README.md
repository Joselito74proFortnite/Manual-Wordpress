# Manual-Wordpress

Crea una carpeta 

## Vagrant

**Creamos vagrant con este comando:**

vagrant init ubuntu/jammy64

**Continuamos elevando las infraestructuras gracias a el siguientge comando:**

vagrant up --provider=virtualbox

**Y con estos pasos podemos hacer ssh a vagrant:**

vagrant ssh

**Podemos mirar los permisos y directorios con:**

ll /vagrant

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

### Consola MySQL

**En la terminal de forma root ponemos el siguiente comando:**

mysql

### Creacion de la base de datos:

**Dentro de mysql cramos la base con nombre: bbdd**

CREATE DATABASE bbdd;

### Creacion del usuario

**Tingueu en compte que s'haurà d'identificar la IP des de la qual s'accedirà a la base de dades, en aquest cas, localhost.**

CREATE USER 'usuario'@'localhost' IDENTIFIED WITH mysql_native_password BY 'password';

**Dar permisos:**

GRANT ALL ON bbdd.* to 'usuario'@'localhost';

***Salir de bbdd:**

exit

**Comprobar la conexion**

mysql -u usuario -p

## Archivo ZIP



### Pasar el archivo zip

**Descargamos el ZIPY lo metemos en el directorio /vagrant/ y lo movemos a /var/www/html/:**

mv /vagrant/arxiu.zip /var/www/html/

### Descomprimir el Zip

**Instalamos el zip:**

apt install zip

**Utilizamos unzip para descomprimirlo**

**Eliminamos el index**

rm index.html

**Entramos a el directorio y lo copiamos**

cd nextcloud
cp -R * ..

**Volvemos a el directorio anterior y eliminamos el archivo y wordpress**

cd ..
rm arxiu.zip
rm -r nextcloud

### Permisos per la web

**Per evitar errors deberiem copiar el zip amb cp -r si esta també amb un altre directori i eliminar el director amb rm -r. Per donar permisos anirem al directori /var/www/html i posarem les següents comandes:**

cd /var/www/html

chmod -R 775 .
chown -R root:www-data .

systemctl restart apache2

exit

## Red pública

**Para hacer nuesta red publica tendremos que ir a vagrantfile y marcamos los siguentes comandos:**

config.vm.network "forwarded_port", guest: 80, host: 8080

config.vm.network "public_network"
