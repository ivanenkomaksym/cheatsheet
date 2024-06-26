# Docker cheatsheet

Run MySQL container
```
docker run -d --name mysql-container -e MYSQL_ROOT_PASSWORD=my-secret-pw -e MYSQL_DATABASE=TweetsDb -e MYSQL_USER=myuser -e MYSQL_PASSWORD=mypassword -p 3306:3306 mysql:latest
```

Run Mongo
```
docker run -d -p 27017:27017 --name mongo mongo:latest
````

Run Redis
```
docker run -d --name redis-stack -p 6379:6379 -p 8001:8001 redis/redis-stack:latest
```

Run NATS
```
docker run -d --name nats-streaming -p 4222:4222 nats-streaming:latest
```

Run RabbitMQ
```
docker run -d --hostname rabbitmq --name rabbitmq -p 5672:5672 -p 15672:15672 rabbitmq:3.13.0-management
```

Run Jaeger
```
docker run -d -p 4317:4317 -p 16686:16686 jaegertracing/all-in-one:latest
```

Build docker images with override and run containers
```
docker-compose -f docker-compose.yml -f docker-compose.override.yml up -d
```

Update the specific container under docker-compose, specify the --no-deps like below
```
docker-compose up -d --no-deps --build servicename
```

docker compose build single container
```
docker-compose build customerapi1
```

check docker image content
```
docker run -u root -it search /bin/bash
```

Log in into docker container
```
docker exec -u 0 -it a87eb386f3a5 bash
```

docker rebuild without cache
```
docker build --no-cache -t [name] .
```
