# Tarea 5 SXE

## Realizar la Tarea 4 pero utilizando Docker Compose

<details>

  <summary>Pasos para crear el Docker File</summary>
<br>
  Primero creamos una carpeta nueva para trabajar en ella y accedemos a ella desde la terminal

  ```bash
cd SXE/ComposeWP
```

  A continuación creamos el archivo .yaml
  
```bash
nano docker-compose.yaml
```

</details>
  
<details>

<summary>Modificar el DockerFile y crear los contenedores</summary>
<br>
Una vez creado el archivo lo modificamos de la siguiente manera para crear los dos contenedores con lo necesario:

```bash
name: SXETarea5

services:
  db:
    image: mariadb:latest
    restart: always
    environment:
      MYSQL_DATABASE: wordpress
      MYSQL_USER: sergio
      MYSQL_PASSWORD: password
      MYSQL_ROOT_PASSWORD: password
    volumes:
      - db_data:/var/lib/mysql

  wp:
    depends_on:
      - db
    image: wordpress:latest
    restart: always
    ports:
      - 8000:80
    environment:
      WORDPRESS_DB_HOST: db
      WORDPRESS_DB_USER: sergio
      WORDPRESS_DB_PASSWORD: password
      WORDPRESS_DB_NAME: wordpress

volumes:
  db_data:
```

Después de guardarlo lo ejecutamos con el siguiente comando:
```bash
docker compose up -d
```
Tras un tiempo de instalación:

![compose](https://github.com/user-attachments/assets/27090caf-84ac-4aeb-a874-afdfafef67f2)

Debería aparecer esto:

![compose2](https://github.com/user-attachments/assets/3ccb4ecc-6c65-45f2-bc17-83daad43cb4f)

Para ver que se crearon los contenedores y están activos:
```bash
docker ps
```
Después entramos con nuestra IP al puerto asignado a los contenedores y se siguen los datos siguiendo los pasos hasta llegar a la página final:

![wdfinal](https://github.com/user-attachments/assets/7dda5bbe-991b-4a7f-bd19-95556ffa8016)

</details>
