# STAGE 1 - BUILD
FROM maven:3.9.9-eclipse-temurin-21-alpine as build
WORKDIR /build 
COPY . .
RUN ["mvn", "clean", "package"]

# STAGE 2 - APPLICATION
FROM eclipse-temurin:21.0.6_7-jre-alpine-3.21 as final
WORKDIR /opt/app
EXPOSE 8888
COPY --from=build /build/target/*.jar /opt/app/*.jar
ENTRYPOINT ["java", "-jar", "/opt/app/*.jar"]