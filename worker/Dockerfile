FROM openjdk:16-jdk-alpine3.13

WORKDIR /worker-app

COPY ./target/worker-jar-with-dependencies.jar ./app.jar

CMD ["java", "-jar", "./app.jar"]
