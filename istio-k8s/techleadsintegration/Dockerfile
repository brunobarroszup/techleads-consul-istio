FROM maven:3.6.0-jdk-11-slim AS build
COPY src /home/app/src
COPY pom.xml /home/app
RUN mvn -f /home/app/pom.xml clean install

FROM openjdk:11-jre-slim
COPY --from=build /home/app/target/*.jar /app.jar
EXPOSE 8081
CMD ["java", "-jar", "/app.jar"]