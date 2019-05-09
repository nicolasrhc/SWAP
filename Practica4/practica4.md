    Nicolás Rodríguez Hernández-Carrilo SWAP 
# Practica 4. Asegurar la granja web
---
### Instalar un certificado SSL autofirmado para configurar el acceso por HTTPS
Activamos el modulo SSL de Apache para generar el certificado SSL autofirmado mediante el siguiente comando y reiniciamos Apache
>a2enmod ssl

![Captura 1](https://github.com/nicolasrhc/SWAP/blob/master/Practica4/Imagenes/1.png)
Captura 1

![Captura 2](https://github.com/nicolasrhc/SWAP/blob/master/Practica4/Imagenes/2.png)
Captura 2

Generamos los certificados y les especificamos la ruta con el siguiente comando, y a continuación completamos la información que se pide:
>openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt

![Captura 3](https://github.com/nicolasrhc/SWAP/blob/master/Practica4/Imagenes/3.png)
Captura 3

Editamos el archivo /etc/apache2/sites-available/default-ssl.conf y añadimos las siguientes lineas:
>SSLCertificateFile /etc/apache2/ssl/apache.crt 
>SSLCertificateKeyFile /etc/apache2/ssl/apache.key

![Captura 4](https://github.com/nicolasrhc/SWAP/blob/master/Practica4/Imagenes/4.png)
Captura 4

Activamos el sitio default-ssl y reiniciamos apache:
>a2ensite default-ssl


![Captura 5](https://github.com/nicolasrhc/SWAP/blob/master/Practica4/Imagenes/5.png)
Captura 5

![Captura 6](https://github.com/nicolasrhc/SWAP/blob/master/Practica4/Imagenes/6.png)
Captura 6

Para finalizar vamos a hacer peticiones por HTTPS utilizando la herramienta curl:
>curl -k https://ipmaquina1/index.html


![Captura 7](https://github.com/nicolasrhc/SWAP/blob/master/Practica4/Imagenes/7.png)
Captura 7

### Configuración del cortafuegos
Primero bloqueamos todo el trafico, lo permitimos por medio de localhost y comprobamos con curl que no ocurre nada

![Captura 10](https://github.com/nicolasrhc/SWAP/blob/master/Practica4/Imagenes/10.png)
Captura 10

A continuación hacemos que funcione por medio de SSH y HTTP y lo comprobamos con curl

![Captura 11](https://github.com/nicolasrhc/SWAP/blob/master/Practica4/Imagenes/11.png)
Captura 11

Por ultimo hacemos que funcione en HTTPS y comprobamos

![Captura 12](https://github.com/nicolasrhc/SWAP/blob/master/Practica4/Imagenes/12.png)
Captura 12

Ponemos todas las reglas anteriores en un script:

![Captura 13](https://github.com/nicolasrhc/SWAP/blob/master/Practica4/Imagenes/13.png)
Captura 13

Y lo añadimos a /etc/rc.local para que se ejecute al iniciarse el equipo:
![Captura 14](https://github.com/nicolasrhc/SWAP/blob/master/Practica4/Imagenes/14.png)
Captura 14
