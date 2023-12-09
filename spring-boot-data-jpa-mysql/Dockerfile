FROM maven AS build

WORKDIR /app/spring-app

COPY . .

RUN mvn install package

FROM eclipse-temurin:21-jre-ubi9-minimal

WORKDIR /app

EXPOSE 8080

COPY --from=build /app/spring-app/target/spring-boot-app.jar spring-app.jar

ENTRYPOINT ["java", "-jar", "spring-app.jar"]