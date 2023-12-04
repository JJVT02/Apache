# Apache
## 01. Instalación de Apache y ficheros de configuración
Para instalar Apache2 haz lo siguiente ( como administrador ):

apt-get update
apt-get install apache2
![](/img/1.png)

Los ficheros de configuración se encuentan en /etc/apache2

Para trabajar con el servicio:
```
service apache2 start  --> para arrancar

service apache2 stop  --> para pararlo

service apache2 restart --> reinicia ( equivalente a hacer stop y luego start )

service apache2 reload --> recargar la configuración

service apache2 status --> comprobamos el estado del servicio
```
La ruta de publicación por defecto se encuentra en /var/www/html

Para comprobar si existen errores de sintaxis en los ficheros de configuración:
```
apache2ctl -t
```
Para evitar el mensaje de advertencia al ejecutar el comando anterior hay que añadir un ServerName en el fichero /etc/apache2/apache2.conf. Por ejemplo: ServerName www.iescamp.es

![](/img/apache2.png)

## 02. Creación de un sitio virtual
Pasos:
- Si no se dispone de un servidor público en Internet y dominios públicos tenemos que editar el fichero /etc/hosts del servidor y añadir entradas para cada dominio
![](/img/2.png)
- Creamos una carpeta para poner los ficheros del dominio dentro de /var/www
![](/img/3.png)
- Vamos a la carpeta /etc/apache2/sites-available

- Copiamos la "plantilla" del sitio por defecto. Por ejemplo: cp 000-default.conf sitio1.conf Tenemos que asegurarnos que los ficheros de configuración de los sitios virtuales acaban en .conf
![](/img/4.png)
- Editamos el fichero de configuración del sitio virtual

- Descomentamos y cambiamos la directiva ServerName y ponemos el nombre del dominio. Por ejemplo ServerName www.sitio1.com

- Cambiarmos la directiva DocumentRoot para que apunte a la carpeta de publicación del dominio

- Activamos el sitio. Por ejemplo a2ensite sitio1

- Recargamos Apache con service apache2 reload