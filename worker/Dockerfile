FROM maven:latest AS builder

COPY src /usr/src/app/src  

COPY pom.xml /usr/src/app  

CMD mvn -f /usr/src/app/ -X clean package

FROM openjdk:16-jdk-alpine3.13

WORKDIR /worker-app

COPY --from=builder ./target/worker-jar-with-dependencies.jar .

CMD ["java", "-jar", "./app.jar"]
