

# Creacion de entorno virutal 

El tutorial que hemos seguido para esto se encuentra en el siguiente enlace: https://docs.python.org/es/3/tutorial/venv.html

Creamos una carpeta que para hostear entornos virutlaes en nuestro ordenador: 

```
mkdir entornos
```

Nos posicionamos en ella, creamos un entorno virtual 

```
python3 -m venv <nombre_entorno>
```

Si estamos en Windows ejecutamos: 

```
<nombre_entorno>\Scripts\activate.bat
```
Y en linux o macos

```
source <nombre_entorno>/bin/activate
```

# Docker: 

Nos posicionamos en la terminal dentro de la carpeta que va a tener el Docker file, en nuestro caso, a la altura 
de la carpeta de 'app'. 

Rellenamos el Dockerfile y creamos la imagen de Docker con el siguiente comando 

```
docker build -t <nombre_imagen> .
```

En mi caso, ejecuto lo siguiente en la CMD en la terminadonde estaba siguiendo este tutorial

```
docker build -t mi_primera_api_docker .
```

Me fijo que en Docker si la imagen esta creada. Bien. 


## Dockerhub

Si quiero subir la imagen a DockerHub, me creo una cuenta y lo posiciono en modo publico. Luego: 

```
docker login
```

Y entro a la cuenta desde la consola. 

Si quiero subo la imagen a dockerhub, primero lo etiqueto: 

```
docker tag <nombre_imagen> <usuario_dockerhub>/<nuevo_tag>
```
En mi caso seria algo como : 


```
docker tag mi_primera_api_docker <usuario_dockerhub>/api_docker
```

Y finalmente lo subo si quiero a dockerhub
```
docker push <usuario_dockerhub>/<nuevo_tag>
```

En mi caso seria algo como : 

```
docker push <usuario_dockerhub>/api_docker
```

## Local-host

Seguimos en local: 

Lo corremos


```
docker run -d --name  <nombre_container> -p 80:80 <nombre_imagen>

```

En mi caso: 

```
docker run -d --name mi_api_docker  -p 80:80 mi_primera_api_docker	

```

Podremos acceder al contenido mediante: 

```

http://127.0.0.1/docs

```

Si queremos pararlo

```
docker stop <id_container>
```

Verificamos que se ha parado con: 

```
docker ps -a
```

