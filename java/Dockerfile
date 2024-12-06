FROM maven:3.9-eclipse-temurin-8 AS builder

WORKDIR /app

COPY . .

RUN mvn clean package -DskipTests


FROM eclipse-temurin:8-jre

WORKDIR /app

COPY --from=builder /app/target/java-*.jar app.jar

LABEL maintainer="noel"

EXPOSE 8448

CMD ["java", "-jar", "app.jar"]