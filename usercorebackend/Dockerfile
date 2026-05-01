# ./usercorebackend/Dockerfile
FROM eclipse-temurin:17-jdk AS build

WORKDIR /app

# Maven wrapper और source code copy करें
COPY . .

# Maven build चलाएँ (अगर gradle है तो gradle command दें)
RUN ./mvnw clean package -DskipTests

# Final image
FROM eclipse-temurin:17-jdk

WORKDIR /app

# Build stage से jar copy करें
COPY --from=build /app/target/*.jar app.jar

EXPOSE 8089

ENTRYPOINT ["java", "-jar", "app.jar"]
