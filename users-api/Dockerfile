# Build Stage
FROM maven:3.8.6-openjdk-11 AS build-stage
WORKDIR /app
COPY . .
RUN mvn package -DskipTests

# Runtime Stage
FROM openjdk:8-jre-slim
WORKDIR /app
COPY --from=build-stage /app/target/users-api-0.0.1-SNAPSHOT.jar ./users-api.jar
EXPOSE 8083  
CMD ["java", "-jar", "users-api.jar"]