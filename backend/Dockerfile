FROM gradle:9.7.1-jdk17-alpine as build
COPY build.gradle settings.gradle gradlew ./
COPY gradle/ ./gradle
COPY src/ ./src
RUN chmod +x gradlew
RUN ./gradlew clean build

FROM eclipse-temurin-17-jre-alpine as run
COPY --from=build /app/build/libs/*.jar /app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
EXPOSE 8081