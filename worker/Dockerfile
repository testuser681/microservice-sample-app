FROM openjdk:16-jdk-alpine3.13

WORKDIR /worker-app

ADD ./target/worker.jar ./app.jar

CMD ["java", "-jar", "./app.jar"]
