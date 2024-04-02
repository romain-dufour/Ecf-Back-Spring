FROM maven:3.6 as builder

WORKDIR /app

COPY server/authentication-service/pom.xml .
RUN mvn dependency:go-offline

COPY server/authentication-service/src ./src
RUN mvn package -DskipTests

FROM openjdk:11

WORKDIR /app

# Copie de l'artifact JAR depuis l'étape précédente
COPY --from=builder /app/target/authentication-service-0.0.1-SNAPSHOT.jar .

# Exposition du port 8080
EXPOSE 8080

# Exécution de l'application Spring Boot
ENTRYPOINT ["java", "-jar", "authentication-service-0.0.1-SNAPSHOT.jar"]


# <artifactId>authentication-service</artifactId>
  #    <version>0.0.1-SNAPSHOT</version>

