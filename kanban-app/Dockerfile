FROM maven:3.6.1-jdk-8-slim AS build
WORKDIR /app
COPY pom.xml ./
COPY . .
RUN mvn clean package -DskipTests


FROM openjdk:8-jdk-alpine

WORKDIR /app

COPY --from=build /app/target/*.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","app.jar"]