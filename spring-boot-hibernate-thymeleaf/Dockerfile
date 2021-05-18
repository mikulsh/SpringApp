FROM openjdk:8-jdk-alpine as builder
ENV JAVA_OPTIONS "-Djava.net.preferIPv4Stack=true"
COPY ./target/demo-0.0.1-SNAPSHOT.jar /app/spring-petclinic.jar
WORKDIR /app
CMD ["java", "-jar", "/app/spring-petclinic.jar"]

