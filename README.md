# Docker cheatsheet

Run MySQL container
```
docker run -d --name mysql-container -e MYSQL_ROOT_PASSWORD=my-secret-pw -e MYSQL_DATABASE=AspNetAzureSample -e MYSQL_USER=myuser -e MYSQL_PASSWORD=mypassword -p 3306:3306 mysql:latest
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

Rebuild the images without starting the containers
```
docker-compose build
```

Run docker images defined in `compose.yaml`
```
docker-compose up
```

To ensure that new Docker images are built from your project when running docker-compose up
```
docker-compose up --build
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

# Kubernetes cheatsheet

List all k8s pods
```
kubectl get pods
```

List all k8s services
```
kubectl get services
```

View deployments
```
kubectl get deployments
```

Restart pod
```
kubectl rollout restart deployment [name]
```

Show pod lods
```
kubectl logs [pod]
```

Get pod details
```
kubectl describe pod [name]
```

Make deployment to update image
```
kubectl rollout restart deployment orderapi-pod
```

Update deployment configuration in runtime
```
kubectl edit deploy [name]
```

Get inside the container which is contained inside the pod and start a shell
```
kubectl exec -it [pod] -c [container] -- /bin/bash
```

Install and use curl
```
apt-get update
apt-get install curl
curl http://customerapi/api/Customer
curl http://localhost/gateway/discounts
```

Install curl on Alpine Linux
```
apk update && apk add --no-cache curl
```

Install curl on Debian
```
apt-get -y update; apt-get -y install curl
```

Install telnet and dnsutils
```
apt install telnet
apt install dnsutils
```

In case hostname isn't resolved by the microservice (https://kubernetes.io/docs/tasks/administer-cluster/dns-debugging-resolution/)
1. Create dnsutils pod
```
kubectl apply -f https://k8s.io/examples/admin/dns/dnsutils.yaml
```
2. Verify its status
```
kubectl get pods dnsutils
```
3. Try to look up the hostname
```
kubectl exec -i -t dnsutils -- nslookup helmapp-rabbitmq
```

```
Server:		10.96.0.10
Address:	10.96.0.10#53

Name:	myapp-rabbitmq.default.svc.cluster.local
Address: 10.107.88.226
```

Open minikube WEB dashboard
```
minikube dashboard
```

Enable metrics
```
minikube addons enable metrics-server
```

Expose service
```
minikube service webui --url
```

```
http://192.168.99.100:31167
```