
FROM maven:3.8.7-eclipse-temurin-17 AS build
WORKDIR /home/to-do-app/

COPY pom.xml .
COPY src/ ./src/

RUN mvn clean package -DskipTests

FROM openjdk:17-jdk-slim
WORKDIR /home/to-do-app/

COPY --from=build /home/to-do-app/target/todoapp-0.0.1-SNAPSHOT.jar /home/to-do-app/todoapp.jar

EXPOSE 8081

CMD ["java", "-jar", "todoapp.jar"]
