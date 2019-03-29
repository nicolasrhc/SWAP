    Nicolás Rodríguez Hernández-Carrilo SWAP 
# Practica 2. Clonar la información de un sitio web
---
### Crear un tar con ficheros locales en un equipo remoto
Creamos un archivo directamente en el equipo de destino mediante el comando 
>tar czf - directorio | ssh equipodestino 'cat > ~/tar.tgz'

![Captura 1](https://github.com/nicolasrhc/SWAP/blob/master/Practica2/Imagenes/1.png)
Captura 1

Comprobamos que el archivo está en el equipo remoto
![Captura 2](https://github.com/nicolasrhc/SWAP/blob/master/Practica2/Imagenes/2.png)
Captura 2

### Instalar la herramienta rsync
Instalamos rsync con el comando
> sudo apt-get install rsync

![Captura 3](https://github.com/nicolasrhc/SWAP/blob/master/Practica2/Imagenes/3.png)
Captura 3

Hacemos que el usuario sea el dueño del directorio con los archivos que hay en el espacio web
![Captura 4](https://github.com/nicolasrhc/SWAP/blob/master/Practica2/Imagenes/4.png)
Captura 4

Y probamos el funcionamiento clonando la carpeta /var/www/ con el comando
> rsync -avz -e ssh ipmaquina1:/var/www/ /var/www/

![Captura 4](https://github.com/nicolasrhc/SWAP/blob/master/Practica2/Imagenes/5.png)
Captura 5

### Acceso sin contraseña para ssh
Creamos la llave publica mediante el comando
> ssh-keygen -b 4096 -t rsa

![Captura 6](https://github.com/nicolasrhc/SWAP/blob/master/Practica2/Imagenes/6.png)
Captura 6

Copiamos la llave publica y la añadimos al fichero de llaves autorizadas para poder acceder sin contraseña utilizando los comandos
> ssh-copy-id maquina1
chmod 600 ~/.ssh/authorized_keys

![Captura 7](https://github.com/nicolasrhc/SWAP/blob/master/Practica2/Imagenes/7.png)
Captura 7

Por ultimo accedemos a la maquina sin contraseña
![Captura 8](https://github.com/nicolasrhc/SWAP/blob/master/Practica2/Imagenes/8.png)
Captura 8

### Programar tareas con crontab
Modificamos el archivo etc/crontab añadiendo la ultima linea que indica que a 
cada hora se actualicen los directorios /var/www/
![Captura 9](https://github.com/nicolasrhc/SWAP/blob/master/Practica2/Imagenes/9.png)
Captura 9
