# Helidon MicroProfile [![Build Status](https://travis-ci.org/daggerok/java-mp-helidon-example.svg?branch=master)](https://travis-ci.org/daggerok/java-mp-helidon-example)

This example implements a simple Hello World REST service using MicroProfile

## Run using maven

```bash
./mvnw exec:java

http :8080/greet/health
http :8080/greet/metrics

http :8080/greet
http :8080/greet/max
http put :8080/greet/greeting greeting=Привед
http :8080/greet/Максимко
```

## Build and run jar

```bash
./mvnw package
ava -jar ./target/*.jar

http :8080/greet
http :8080/greet/max
http put :8080/greet/greeting greeting=Привед
http :8080/greet/Максимко
```

## Build and run docker

```bash
docker build -t helidon-quickstart-mp .
docker run --rm -d -p 8080:8080 helidon-quickstart-mp:latest

http :8080/greet
http :8080/greet/max
http put :8080/greet/greeting greeting=Привед
http :8080/greet/Максимко
```

## Check versions update

```bash
./mvnw versions:display-property-updates
```

## Generate maven project

```bash
mvn archetype:generate -DinteractiveMode=false \                                24:00 
    -DarchetypeGroupId=io.helidon.archetypes \
    -DarchetypeArtifactId=helidon-quickstart-mp \
    -DarchetypeVersion=1.2.0 \
    -DgroupId=com.github.daggerok.helidon \
    -DartifactId=java-mp-helidon-example \
    -Dpackage=com.github.daggerok.helidon

cd java-mp-helidon-example
mvn -N io.takari:maven:0.7.6:wrapper -Dmaven=3.6.1
./mvnw 
```

<!--

## Prerequisites

1. Maven 3.5 or newer
2. Java SE 8 or newer
3. Docker 17 or newer (if you want to build and run docker images)
4. Kubernetes minikube v0.24 or newer (if you want to deploy to Kubernetes)
   or access to a Kubernetes 1.7.4 or newer cluster
5. Kubectl 1.7.4 or newer for deploying to Kubernetes

Verify prerequisites
```
java -version
mvn --version
docker --version
minikube version
kubectl version --short
```

## Build

```
mvn package
```

## Start the application

```
java -jar target/java-mp-helidon-example.jar
```

## Exercise the application

```
curl -X GET http://localhost:8080/greet
{"message":"Hello World!"}

curl -X GET http://localhost:8080/greet/Joe
{"message":"Hello Joe!"}

curl -X PUT -H "Content-Type: application/json" -d '{"greeting" : "Hola"}' http://localhost:8080/greet/greeting

curl -X GET http://localhost:8080/greet/Jose
{"message":"Hola Jose!"}
```

## Try health and metrics

```
curl -s -X GET http://localhost:8080/health
{"outcome":"UP",...
. . .

# Prometheus Format
curl -s -X GET http://localhost:8080/metrics
# TYPE base:gc_g1_young_generation_count gauge
. . .

# JSON Format
curl -H 'Accept: application/json' -X GET http://localhost:8080/metrics
{"base":...
. . .

```

## Build the Docker Image

```
docker build -t java-mp-helidon-example .
```

## Start the application with Docker

```
docker run --rm -p 8080:8080 java-mp-helidon-example:latest
```

Exercise the application as described above

## Deploy the application to Kubernetes

```
kubectl cluster-info                         # Verify which cluster
kubectl get pods                             # Verify connectivity to cluster
kubectl create -f app.yaml               # Deploy application
kubectl get service java-mp-helidon-example  # Verify deployed service
```

-->
