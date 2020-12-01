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
