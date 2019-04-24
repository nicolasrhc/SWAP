    Nicolás Rodríguez Hernández-Carrilo SWAP 
# Practica 3. Balanceo de carga
---
### Servidor web nginx
Instalamos nginx mediante el comando 
>sudo apt-get install nginx

![Captura 1](https://github.com/nicolasrhc/SWAP/blob/master/Practica3/Imagenes/1.png)
Captura 1

Añadimos el fichero de configuración /etc/nginx/conf.d/default.conf con la información de los dos servidores apache
![Captura 2](https://github.com/nicolasrhc/SWAP/blob/master/Practica3/Imagenes/2.png)
Captura 2

Modificamos el archivo /etc/nginx/nginx.conf comentando la linea
>include /etc/nginx/sites-enabled/*;

![Captura 3](https://github.com/nicolasrhc/SWAP/blob/master/Practica3/Imagenes/3.png)
Captura 3

Desde la maquina cliente ejecutamos el siguiente comando repetidas veces para comprobar que se está realizando el balanceo correctamente
>curl http://192.168.1.103

![Captura 4](https://github.com/nicolasrhc/SWAP/blob/master/Practica3/Imagenes/4.png)
Captura 4

### Balanceo de carga con haproxy
Instalamos haproxy mediante el comando 
>sudo apt-get install haproxy

![Captura 5](https://github.com/nicolasrhc/SWAP/blob/master/Practica3/Imagenes/5.png)
Captura 5

Modificamos el archivo /etc/haproxy/haproxy.cfg para añadir los servidores correspondientes con la siguiente información

![Captura 6](https://github.com/nicolasrhc/SWAP/blob/master/Practica3/Imagenes/6.png)
Captura 6

Desde la maquina cliente ejecutamos el siguiente comando repetidas veces para comprobar que se está realizando el balanceo correctamente
>curl http://192.168.1.104

![Captura 7](https://github.com/nicolasrhc/SWAP/blob/master/Practica3/Imagenes/7.png)
Captura 7

### Someter a una alta carga el servidor balanceado
Utilizaremos Apache Benchmark para sobrecargar el servidor. El comando es el siguiente
> ab -n 10000 -c 10 http://ip/index.html 

Donde -n es el numero de peticiones que se van a realizar, -c la concurrencia de esas peticiones, y la ip, el servidor al que haremos las peticiones. 
En la captura 8 tenemos los resultados al utilizar haproxy y en la 9 los de nginx 

![Captura 8](https://github.com/nicolasrhc/SWAP/blob/master/Practica3/Imagenes/8.png)
Captura 8

![Captura 9](https://github.com/nicolasrhc/SWAP/blob/master/Practica3/Imagenes/9.png)
Captura 9
