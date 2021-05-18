FROM openjdk:8-jdk-alpine as builder
COPY ./target/demo-0.0.1-SNAPSHOT.jar /app/demo.jar
WORKDIR /app
CMD ["java", "-jar", "/app/demo.jar"]