# ----------- STAGE 1: Build ------------
    FROM maven:3.8.8-eclipse-temurin-11 AS build

    WORKDIR /build
    


    COPY eureka-service/ ./eureka-service/
    

    
    # Compiler le microservice
    RUN mvn -f eureka-service/pom.xml clean package -DskipTests
    
    # ----------- STAGE 2: Run --------------
    FROM eclipse-temurin:11-jre
    
    WORKDIR /app
    
    # Copier le JAR du service compilé
    COPY --from=build /build/eureka-service/target/*.jar app.jar
    
    EXPOSE 8080
    ENTRYPOINT ["java", "-jar", "/app/app.jar"]
    