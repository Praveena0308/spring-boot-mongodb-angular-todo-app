# Stage 1: Build the application using Maven
FROM maven:3.8.7-eclipse-temurin-17 AS build
WORKDIR /home/to-do-app/

# Copy the pom.xml and source code
COPY pom.xml .
COPY src/ ./src/

# Build the application (skip tests to speed up the build if not needed)
RUN mvn clean package -DskipTests

# Stage 2: Run the Spring Boot application
FROM openjdk:17-jdk-slim
WORKDIR /home/to-do-app/

# Copy the built JAR file from the build stage
COPY --from=build /home/to-do-app/target/todoapp-0.0.1-SNAPSHOT.jar /home/to-do-app/todoapp.jar

# Expose the application port
EXPOSE 8080

# Run the Spring Boot application
CMD ["java", "-jar", "todoapp.jar"]
