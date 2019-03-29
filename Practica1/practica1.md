    Nicolás Rodríguez Hernández-Carrilo SWAP 
# Practica 1. Presentación de las prácticas y preparación de las herramientas
---
### Conectarse a una maquina remota mediante ssh
Tras haber hecho la instalación por defecto de ubuntu server, añadiendo la pila lamp, tenemos que instalar en las maquinas open ssh, en una el servidor y en la otra el cliente. Eso lo hacemos con los comandos
>sudo apt-get install openssh-server
sudo apt-get install openssh-client

Con open ssh ya instalado, podemos conectarnos
![Captura 1](https://github.com/nicolasrhc/SWAP/blob/master/Practica1/Imagenes/1.png)
Captura 1

### Acceder mediante Curl
Instalamos curl usando
> sudo apt-get install curl

Una vez instalado crearemos un archivo html en /var/www/html y nos disponemos a conectarnos mediante
> curl http://direccionIPdelservidor/hola.html

![Captura 2](https://github.com/nicolasrhc/SWAP/blob/master/Practica1/Imagenes/2.png)
Captura 2
