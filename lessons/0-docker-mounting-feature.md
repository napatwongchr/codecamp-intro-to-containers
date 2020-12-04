## Bind mount

1. ทำการ run คำสั่ง docker

```
docker run -dit -p 3001:3001 --mount type=bind,src="$(pwd)",target=/app --rm --name my-node-app my-node-app
```

Note: Bind mount ใน docker-compose

```
version: "3"
services:
  node_app:
      container_name: "my_node_app"
      build: ./backend
      ports:
        - "3001:3001"
      volumes:
        - type: bind
          source: ./backend
          target: /app
      environment:
        MONGO_CONNECTION_STRING: mongodb://localhost:27017
```

## Volume mount

1. ทำการ run คำสั่ง docker

```
docker run -dit -p 3306:3306 -e MYSQL_ROOT_PASSWORD="123456789" --mount type=volume,src=mysql_data,target=/var/lib/mysql --rm --name mysql_db mysql
```

Note: Volume mount in docker-compose (in short syntax)

```
version: "3"
services:
  db_sql:
    container_name: "mysql_db"
    image: mysql
    command: --default-authentication-plugin=mysql_native_password
    restart: always
    volumes:
      - "mysql_data:/var/lib/mysql"
    environment:
      MYSQL_ROOT_PASSWORD: "123456789"
    ports:
      - "3306:3306"
    cap_add:
      - SYS_NICE
volumes:
  mysql_data:

```
