# Stage 1: Build with Maven
FROM maven:3.9.6-eclipse-temurin-17 AS build

WORKDIR /app

# Copy pom.xml और dependencies पहले ताकि cache बने
COPY pom.xml .
COPY src ./src

# Maven build (tests skip कर सकते हैं अगर चाहें)
RUN mvn clean install -DskipTests

# Stage 2: Run the JAR
FROM eclipse-temurin:17-jdk

WORKDIR /app

# Build stage से jar copy करें
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8089

ENTRYPOINT ["java", "-jar", "app.jar"]
