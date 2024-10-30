# Tarea6_SXE
Tarea 6 en Windows

Primero instalamos docker en Windows

Depsués creamos una carpeta con el nombre de Tarea6 para localizar todo ahí
 ```
mkdir Tarea06
```
Creamos un archivo de docker compose, un archivo del tipo .yml 
 ```
 echo $null > docker-compose.yml
```
 Y editamos ese archivo con notepad

 ![image](https://github.com/user-attachments/assets/909e076a-5c1e-4478-9d19-7869a45743e5)

 Añadimos este contenido 
 ```
 services:
  mysql:
    container_name: some-mysql
    image: mysql:5.7
    restart: unless-stopped
    environment:
      MYSQL_ROOT_PASSWORD: admin
      MYSQL_DATABASE: prestashop
    networks:
      - prestashop_network
  prestashop:
    container_name: prestashop
    image: prestashop/prestashop:latest .
    restart: unless-stopped
    depends_on:
      - mysql
    ports:
      - 8080:80
    environment:
      DB_SERVER: some-mysql
      DB_NAME: prestashop
      DB_USER: root
      DB_PASSWD: admin
    networks:
      - prestashop_network
networks:
    prestashop_network:
 ```
  
Guardamos el archivo y ejecutamos el archivo docker-compose

 ```
    docker-compose up -d
```
  
    Podemos comprobar si se han ejecutado los contenedores con el comando 
 
docker ps
 
![image](https://github.com/user-attachments/assets/f05881e5-b958-48b7-8642-01b8a1181317)

Ahora como no estamos dentro de la maquina virtual podemos utilizar local host pero en el caso qeu quisieramos saber la ip en windows podriamos utilizar
 ```
ipconfig
 ```
Pero como estamos utilizando el odernador basta con http://localhost:8080/

![image](https://github.com/user-attachments/assets/d4e6c375-e346-4d27-ba8c-c0cb8cd0ab30)

Ahora conectamos la base de datos sql con la informacion que hemos colocado en el archivo .yml 

![image](https://github.com/user-attachments/assets/d01e9d2c-a583-4f97-a2ef-71fa9fe3d57f)

Dejamos que cargue la información, al acabar de cargar nos aparecerá esto: 

![image](https://github.com/user-attachments/assets/172fc0d1-043c-45fc-9d1c-72d38d5db39e)

Podemos entrar en nuestra interfaz de usuario

![image](https://github.com/user-attachments/assets/896c2685-11a3-4570-80e2-a9fe9e2c3ac5)


Ahora podemos entrar en la interfazdeadministración pero nos da este error

![image](https://github.com/user-attachments/assets/322f97b9-6c2c-4bef-b990-ed056a7d38ca)

Para arreglarlo accedemos a la terminal del contenedor

![image](https://github.com/user-attachments/assets/f086ed7b-1296-4786-8cd5-c567b6eede3e)

Eliminamos la carpeta install 
 ```
 rm -rf install
 ```
Y modificamos el nombre de la carpeta
 ```
mv admin admin343knwezglbery3dpq6
 ```
Probamos ahora y finalmente ya podemos acceder con nuestro correo y contraseña 

![image](https://github.com/user-attachments/assets/4814e3d2-afdf-4ba2-84cc-14f5d57be8f2)





    
